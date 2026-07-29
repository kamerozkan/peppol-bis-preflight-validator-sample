# Data Notice

## Purpose

This repository is a technical sample for the [Peppol BIS Billing Preflight Validator](https://apify.com/kamerozkan/peppol-bis-preflight-validator). It contains three real Actor output rows and a standalone JSON Schema.

This is an independent, unofficial product. It is not affiliated with, sponsored by, or endorsed by OpenPeppol, OASIS, CEN, any Peppol authority, access point, tax authority, or invoice recipient.

## Audit snapshot

| Item | Verified value |
|---|---|
| Actor | `kamerozkan/peppol-bis-preflight-validator` |
| Actor ID | `7hUmsUWO5wpNVeDOz` |
| Successful run | `fNx8cxIyntPOg1IDj` |
| Build | `0.0.1`, build ID `nveuIn6Ai1tEFsD2W` |
| Dataset | `XlAJMsaT0VBsSHHxq`, 3 records |
| Run time | 2026-07-29 |
| Charged validation events | 2 |

The run and dataset identifiers are included for owner-side provenance. This repository does not claim that either resource is publicly readable.

## Output provenance

- [`01_live_accepted_output.json`](01_live_accepted_output.json) is the verbatim accepted dataset row.
- [`02_live_rejected_output.json`](02_live_rejected_output.json) is the verbatim rejected dataset row, limited by the run input to three active and three preview findings.
- [`03_live_not_evaluated_output.json`](03_live_not_evaluated_output.json) is the verbatim source-policy failure row.

The records were generated from public or synthetic release-test inputs. No omitted value was inferred, reconstructed, or converted into a success claim.

## Privacy and security

This repository contains no customer invoice, raw XML, base64 payload, report body, access token, cookie, signed URL, webhook URL, email address, IBAN, customer account identifier, or private key.

Real invoice validation can process personal, financial, tax, and commercial data. Users remain responsible for lawful processing, access control, retention, deletion, and all applicable privacy, tax, accounting, database, and contractual requirements.

## Interpretation limits

- `ACCEPTED` means the submitted bytes passed the required active technical rules pinned in the result.
- `REJECTED` means processing completed and at least one required active technical rule failed.
- `NOT_EVALUATED` means no technical decision was possible.
- `previewConformanceStatus` is a separate future-rule assessment and does not replace the active decision before its effective date.
- A result does not prove legal or tax validity, participant capability, authenticity, authorization, delivery, payment, or recipient acceptance.
- A result does not guarantee acceptance by an access point, recipient, ERP, tax authority, or other downstream system.

Check the Actor page for the current rules, supported syntax, pricing, and limits before production use.

## License boundary

The MIT License applies only to the original documentation, output samples, and JSON Schema committed here. It does not relicense Peppol, UBL, EN 16931, validator software, specifications, test documents, third-party names, marks, or source data.
