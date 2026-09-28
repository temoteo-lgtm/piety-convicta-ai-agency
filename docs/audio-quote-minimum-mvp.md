# Audio Quote Minimum MVP

This is the smallest acceptable scope for launching PIETY audio quotation without pretending the full automation is finished too early.

## MVP Goal

A customer can provide quote information by voice, and the site uses AI to turn that audio into structured quote data and a customer-visible next step.

## Must Have

1. Audio entry point on the quote card.
2. Recording path where supported.
3. Audio-file fallback where recording fails.
4. Backend endpoint for audio upload.
5. Transcription.
6. Structured field extraction.
7. Validation of required fields.
8. Form/state population with extracted fields.
9. Missing-field prompt when needed.
10. Quote result, quote summary, or consultant-ready quote request shown inside the site.
11. Failure states with retry/fallback and debug id.
12. Evidence across desktop, Android, and iPhone.

## Can Be Later

- Perfect live pricing from every operator.
- Full CRM automation.
- Full insurer/operator API integration.
- Long-term audio storage.
- Advanced analytics dashboard.
- Multi-language audio.
- Automatic WhatsApp follow-up.

## Not Acceptable as MVP

- Button that only opens a recorder.
- Recorder that fails on iPhone without fallback.
- Audio upload that does not run through AI extraction.
- Transcription without structured quote data.
- WhatsApp as the primary path.
- Asking the customer to fill the full form again after speaking.
- Marking the feature done without evidence.

## MVP Output Options

Depending on current data availability, the first version may return one of these:

| Output | Acceptable? | Condition |
|---|---|---|
| Live quote result | Yes | If data/API is available and validated. |
| Ranked plan/options summary | Yes | If database supports it and prices are reliable. |
| Consultant-ready quote summary | Yes | If pricing must be finalized by a human, but extracted data is complete. |
| Missing-data questions | Yes | If required fields are absent. |
| WhatsApp redirect only | No | It does not complete the automated audio quote feature. |
