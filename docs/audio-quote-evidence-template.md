# Audio Quote Evidence Template

Copy this template for each validation run of the PIETY audio quotation feature.

## Summary

- Date:
- Tester:
- Environment:
- Device:
- Browser/App:
- Site URL:
- Build/commit/version:
- Scenario:
- Status: `PASSED`, `FAILED`, or `NEEDS_WORK`

## Customer Journey Tested

Describe the journey in customer language. Example:

> Customer taps `Cotar falando agora`, records a health plan request for 3 lives in Brasilia/DF, stops recording, waits for processing, and receives a quote summary or missing-data prompt inside the site.

## Input Audio

- Source: `browser-recorder`, `file-picker`, or `recorder-page`
- File type/codec:
- Duration:
- Size:
- Audio content summary, without customer PII:

## Expected Result

- Audio uploads successfully.
- Audio is transcribed.
- Required fields are extracted.
- Missing fields are identified when applicable.
- Site shows quote result, quote summary, or focused next-step question.

## Actual Result

Document exactly what happened.

## Extracted Fields

```json
{
  "city": null,
  "state": null,
  "modality": null,
  "company_type": null,
  "lives_count": null,
  "ages": [],
  "has_cnpj": null,
  "current_plan": null,
  "desired_coverage": null,
  "contact_name": null,
  "phone": null,
  "missing_fields": [],
  "confidence": 0,
  "transcript": ""
}
```

## API / Debug Evidence

- Endpoint tested:
- HTTP status:
- Debug id:
- Relevant log summary, redacted:
- Error message shown to customer, if any:

## Visual Evidence

Attach or link:
- Screenshot before recording/upload.
- Screenshot during processing.
- Screenshot after result/missing-field prompt.
- Screen recording when useful.

## Decision

- Can this scenario be marked passed? `Yes/No`
- If no, what failed?
- Which agent/team owns the fix?
- Next action:

## Reality Checker Notes

Reality Checker must confirm:
- The site behavior matches the claimed result.
- Evidence covers the target environment.
- The user journey did not silently fall back to WhatsApp as the primary solution.
- The result is customer-visible inside the site.
