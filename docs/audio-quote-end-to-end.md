# Audio Quote End-to-End Blueprint

This document defines the intended PIETY audio quotation journey. It is non-confidential and must not contain credentials, private pricing rules, customer data, or insurer secrets.

## Product Goal
A customer arrives on the PIETY site, starts an audio quote, speaks the plan/profile information, and receives a prepared quotation result or a clear next-step request for missing data.

WhatsApp is not the primary solution for this feature. It may exist only as an emergency contact fallback, not as the audio quotation pipeline.

## Target User Journey
1. Customer taps `Cotar por audio` or `Cotar falando agora`.
2. Site opens the simplest available recording path for the device.
3. Customer records up to 2 minutes of audio.
4. Site uploads the audio to the backend.
5. Backend transcribes the audio.
6. AI extracts structured quotation fields from the transcript.
7. System validates required fields.
8. If data is sufficient, the quote flow is filled/prepared and the customer sees the quotation result or standard quote summary.
9. If data is missing, the site asks only the missing questions, not the full form again.
10. All failures give a fast recovery path without losing the customer.

## Required Data Contract
The extraction layer should return a structured object, not free text.

Minimum fields for health quotation workflows:
- `city`
- `state`
- `modality`: `pessoa_fisica`, `empresa_pme`, or `adesao`
- `company_type`, when modality is company/PME
- `lives_count`
- `ages`
- `has_cnpj`, when relevant
- `current_plan`, if mentioned
- `desired_coverage`, if mentioned
- `contact_name`, if mentioned
- `phone`, if mentioned
- `missing_fields`
- `confidence`
- `transcript`

The UI must treat low-confidence or missing required fields as a normal recovery state, not as a system failure.

## Device Strategy
The product must support a layered capture strategy because mobile browsers vary, especially iOS Safari.

Preferred path:
- Use browser microphone capture when `navigator.mediaDevices.getUserMedia` and `MediaRecorder` are available.
- Show a clear recording state: recording timer, stop button, cancel button, and upload/progress feedback.

Fallback path:
- Provide a direct audio file picker for devices where inline recording fails.
- The file picker must accept audio formats such as `audio/*`, `.m4a`, `.mp3`, `.wav`, `.webm`, `.ogg`, `.aac`.
- The fallback still uploads to the same AI quotation pipeline.

Last-resort contact path:
- WhatsApp may be shown only after capture and upload paths fail.
- WhatsApp must be labeled as human support, not as the automated audio quote feature.

## Backend Contract
The backend endpoint should accept `multipart/form-data` with:
- `audio`: uploaded audio file/blob
- `source`: browser, file-picker, or recorder-page
- optional `session_id`
- optional existing form state

The backend response should include:
- `status`: `completed`, `needs_more_info`, or `failed`
- `transcript`
- `extracted_fields`
- `missing_fields`
- `quote_summary` or `quote_payload`, when available
- `user_message`
- `debug_id` for support, without exposing sensitive logs

## AI Pipeline
The AI pipeline should be explicit:
1. Normalize audio format where needed.
2. Transcribe audio.
3. Extract fields into the schema.
4. Validate required fields deterministically.
5. Prepare quotation request or standard quotation summary.
6. Return missing questions when required.

Do not declare the feature complete when only transcription works. Completion requires the customer-visible quotation journey.

## UX Acceptance Criteria
The feature is only acceptable when:
- A new customer can start the audio flow from the visible quote card.
- Recording works on supported browsers without opening the camera/video recorder by mistake.
- If inline recording fails, choosing an audio file still continues the same quote flow.
- Upload progress and processing state are visible.
- Extracted fields populate the form or quote state.
- Missing information is requested in a short, focused way.
- The customer receives a quote result, prepared quote summary, or clear next step.
- Error states do not push the customer to repeat everything from zero.

## Evidence Required Before DONE
Record evidence for at least these cases:
- Desktop Chrome successful recording to quote result.
- Android Chrome successful recording to quote result.
- iPhone Safari successful path, either inline recording or audio file fallback, to quote result.
- Microphone denied recovery path.
- Unsupported recorder recovery path.
- Low-quality audio recovery path.
- Missing fields recovery path.
- Backend failure message with debug id.

Each evidence entry should include environment, test input, expected result, actual result, and implementation reference.
