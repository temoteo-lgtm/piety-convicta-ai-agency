# Lovable Implementation Prompt: PIETY Audio Quote

Use this prompt in the PIETY site project when implementing the audio quotation feature.

## Prompt

Implement the PIETY audio quotation feature end-to-end. The business goal is: the customer clicks the audio quote option, speaks the plan/profile information, and receives a prepared quotation result or a short prompt for missing information inside the site.

Do not use WhatsApp as the main audio quote solution. WhatsApp can only be a last-resort human support fallback. The automated feature must process the audio inside the site.

### Required UX

In the quote card, show an audio section with:
- Title: `Cotar por audio`
- Primary button: `Cotar falando agora`
- Fallback button: `Usar audio gravado no aparelho`
- Recording state with timer, `Parar`, and `Cancelar`
- Upload/processing state: `Analisando seu audio...`
- Success state showing extracted information and the prepared quotation result or next step
- Missing-data state asking only the missing information

The browser must not open video recording when the customer expects audio. If inline recording is unavailable or fails, show the audio file picker fallback and continue the same AI quotation pipeline.

### Required Technical Flow

1. Capture or receive an audio file.
2. Send audio to backend endpoint `POST /api/audio-quote` as `multipart/form-data`.
3. Backend transcribes the audio.
4. Backend extracts structured quotation fields using AI.
5. Backend validates required fields.
6. Frontend fills known form state and asks only missing fields.
7. Frontend shows quote result, quote summary, or clear next step.

### Endpoint Contract

Request:
- `audio`: audio file/blob
- `source`: `browser-recorder`, `file-picker`, or `recorder-page`
- optional existing form/session state

Response:
```json
{
  "status": "completed | needs_more_info | failed",
  "transcript": "",
  "extracted_fields": {},
  "missing_fields": [],
  "quote_summary": null,
  "quote_payload": null,
  "user_message": "",
  "debug_id": ""
}
```

### Extraction Schema

Use the structure from `config/audio-quote.schema.json` in the agency repo. Required output fields:
- `city`
- `state`
- `modality`
- `company_type`
- `lives_count`
- `ages`
- `has_cnpj`
- `current_plan`
- `desired_coverage`
- `contact_name`
- `phone`
- `missing_fields`
- `confidence`
- `transcript`

### Validation Rules

For health plan quotation, require at minimum:
- city
- state
- modality
- lives_count
- ages

For PME/company quotation, also require:
- whether the customer has CNPJ
- company type when relevant

If fields are missing, ask only for those fields. Do not reset the full form.

### Accepted Audio Formats

Accept at least:
- `.m4a`
- `.aac`
- `.mp3`
- `.wav`
- `.webm`
- `.ogg`

Normalize server-side if needed before transcription.

### Error Handling

Handle:
- microphone denied
- unsupported recorder
- mobile Safari recording limitation
- interrupted upload
- oversized file
- unsupported codec
- transcription failure
- low confidence extraction
- backend/API timeout

Each failure must show a fast recovery path. The fallback audio upload still needs to run through the same AI quote pipeline.

### Acceptance Tests

The feature is only complete when these pass:
- Desktop Chrome: record audio and receive quote result or missing-data prompt.
- Android Chrome: record audio and receive quote result or missing-data prompt.
- iPhone Safari: inline recording or audio file fallback reaches the same quote pipeline.
- Microphone denied: user can recover without losing progress.
- Unsupported recorder: user can upload audio and continue.
- Missing fields: site asks only missing details.
- Backend failure: site shows helpful retry message with safe debug id.

Do not mark the task as complete if only the button, recorder UI, or transcription exists. Completion requires the customer-visible quotation journey.
