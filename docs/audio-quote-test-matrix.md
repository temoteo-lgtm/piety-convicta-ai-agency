# Audio Quote Test Matrix

Use this matrix before marking the PIETY audio quotation feature as VERIFIED or DONE.

## Test Environments

| Environment | Browser/App | Required Path | Status | Evidence Link/Notes |
|---|---|---|---|---|
| Desktop | Chrome | Inline recording | PLANNED |  |
| Desktop | Safari or Edge | Inline recording or fallback upload | PLANNED |  |
| Android | Chrome | Inline recording | PLANNED |  |
| iPhone | Safari | Inline recording or audio-file fallback | PLANNED |  |
| iPhone | In-app browser, if used by ads/social | Audio-file fallback at minimum | PLANNED |  |

## Functional Cases

| Case | Steps | Expected Result | Status | Evidence Link/Notes |
|---|---|---|---|---|
| Happy path with complete audio | Record customer quote audio with city, UF, modality, lives and ages | Site transcribes, extracts fields, validates and shows quote result/summary | PLANNED |  |
| Missing city/state | Record audio without location | Site asks only city/UF, not the whole form | PLANNED |  |
| Missing ages | Record audio with lives count but no ages | Site asks only ages | PLANNED |  |
| PME with missing CNPJ info | Record PME audio without CNPJ status | Site asks whether customer has CNPJ/company type | PLANNED |  |
| Microphone denied | Deny microphone permission | Site explains recovery and offers audio upload fallback | PLANNED |  |
| Unsupported recorder | Simulate missing MediaRecorder/getUserMedia | Site offers file fallback and continues same AI pipeline | PLANNED |  |
| Upload fallback | Select `.m4a` or `.mp3` file | Audio goes to backend and returns same extraction flow | PLANNED |  |
| Oversized file | Upload file over allowed limit | Site rejects with clear size guidance, no crash | PLANNED |  |
| Low-quality audio | Use noisy/unclear audio | Site asks for clarification or missing fields | PLANNED |  |
| Transcription timeout/failure | Simulate provider failure | Site shows retry message and safe debug id | PLANNED |  |
| Backend validation failure | Send malformed payload | API returns controlled error and frontend recovers | PLANNED |  |
| Quote unavailable | Extraction works but no quote data available | Site shows prepared summary and clear next step | PLANNED |  |

## Minimum Evidence Required

For each completed case, capture:
- Environment/device/browser.
- Test audio description, without customer PII.
- Expected result.
- Actual result.
- Screenshot or screen recording reference.
- API/debug id when applicable.
- Implementation commit/version.
- Final status: `PASSED`, `FAILED`, or `NEEDS_WORK`.

## DONE Rule

The feature cannot be DONE unless:
- At least one desktop path passes.
- At least one Android path passes.
- At least one iPhone path passes through inline recording or audio upload fallback.
- Missing-field recovery passes.
- Failure recovery passes.
- Customer-visible quote result, quote summary, or focused next step appears inside the site.
