> **Live API:** [Run Peppol BIS Billing Preflight Validator on Apify](https://apify.com/kamerozkan/peppol-bis-preflight-validator)

# Peppol BIS Billing 3.0 Validator API: Samples and JSON Schema

[![Apify Actor](https://img.shields.io/badge/Apify-Run%20Actor-00c7b7?logo=apify)](https://apify.com/kamerozkan/peppol-bis-preflight-validator)
![Active rules](https://img.shields.io/badge/Peppol_BIS-3.0.20-005EA8)
![Preview rules](https://img.shields.io/badge/Preview-3.0.21_on_2026--08--17-F59E0B)
![Validation](https://img.shields.io/badge/scope-OFFLINE__PREFLIGHT-137333)
![Latest build](https://img.shields.io/badge/latest_build-0.0.7%20SUCCEEDED-2f855a)
![Samples](https://img.shields.io/badge/samples-3%20verified%20live%20rows-2f855a)
![License](https://img.shields.io/badge/license-MIT-blue)

Validate Peppol BIS Billing UBL invoices before network submission. One run returns the active 3.0.20 decision and a separate 3.0.21 preview decision for the rules effective on 17 August 2026.

> `ACCEPTED` is a deterministic technical preflight result under the pinned rules. It is not proof of legal or tax validity, Peppol participant capability, AS4 delivery, or recipient acceptance.

## Verified repository contents

| File | Meaning |
|---|---|
| [`01_accepted_input.json`](01_accepted_input.json) | Runnable input for the accepted official fixture |
| [`02_rejected_input.json`](02_rejected_input.json) | Runnable input for the empty-invoice-ID mutation |
| [`03_not_evaluated_input.json`](03_not_evaluated_input.json) | Runnable input for the source-policy boundary |
| [`01_live_accepted_output.json`](01_live_accepted_output.json) | Real accepted UBL Invoice result |
| [`02_live_rejected_output.json`](02_live_rejected_output.json) | Real rejected result with active and preview findings |
| [`03_live_not_evaluated_output.json`](03_live_not_evaluated_output.json) | Real source failure, no technical decision |
| [`dataset_record.schema.json`](dataset_record.schema.json) | JSON Schema 2020-12 contract for one dataset row |
| [`DATA_NOTICE.md`](DATA_NOTICE.md) | Provenance, privacy, and interpretation limits |

All three JSON rows came from successful Actor run `Szb49L6dL3IkFBapm`, build `0.0.3` (`RSEHb1OfMZGbVGlsj`), dataset `HXEpY6XKMF7SiyYKw`, on 2026-07-29. The run evaluated two documents and billed exactly two `invoice-validated` events. The `NOT_EVALUATED` source failure was not billed.

Latest hosted build `0.0.7` was verified `SUCCEEDED` on 2026-07-30. The three real rows remain attributed to build `0.0.3`. Both evaluated fixture SHA-256 values match their output rows exactly.

## Stable decision contract

- `ACCEPTED`: processing completed and no required active-rule failure was found.
- `REJECTED`: processing completed and at least one required active-rule failure was found.
- `NOT_EVALUATED`: a source or engine failure prevented a technical decision.
- `previewConformanceStatus`: the separate Peppol BIS Billing 3.0.21 decision.
- `externalStateStatus`: participant, network, delivery, and recipient state remain outside offline preflight.
- `versions.activeRuleset` and `versions.previewRuleset`: machine-readable rule identity and effective date.
- `sha256`: digest of every document that was successfully loaded.

## Real output examples

<details>
<summary><strong>01. ACCEPTED</strong> - active 3.0.20 and preview 3.0.21 both accept the document</summary>

[`01_live_accepted_output.json`](01_live_accepted_output.json)

```json
{
  "inputIndex": 0,
  "documentId": "official-valid",
  "fileName": "base-example.xml",
  "processingStatus": "SUCCEEDED",
  "conformanceStatus": "ACCEPTED",
  "previewConformanceStatus": "ACCEPTED",
  "validationScope": "OFFLINE_PREFLIGHT",
  "externalStateStatus": "NOT_EVALUATED_EXTERNAL_STATE",
  "rulesetEffectiveAt": "2026-02-23",
  "sourceFormat": "XML",
  "validationFamily": "PEPPOL_BIS_BILLING",
  "syntax": "UBL_INVOICE",
  "profile": "PEPPOL_BIS_BILLING_3",
  "scenario": "Peppol BIS Billing 3 UBL Invoice",
  "versions": {
    "ubl": "2.1",
    "cenSchematronActive": "1.3.15",
    "cenSchematronPreview": "1.3.16",
    "peppolBisActive": "3.0.20",
    "peppolBisPreview": "3.0.21",
    "saxonHe": "10.9",
    "schematronSkeleton": "02f3707b194ce5792bf77b14a66d782c060abba3",
    "activeRuleset": {
      "name": "Peppol BIS Billing 3.0.20",
      "effectiveAt": "2026-02-23"
    },
    "previewRuleset": {
      "name": "Peppol BIS Billing 3.0.21",
      "effectiveAt": "2026-08-17"
    },
    "artifactManifestSha256": "ce0b34ba52412ea870785a58f316990d578d91717c3b1b396ed0f2e9f3fd5ef2"
  },
  "counts": {
    "fatal": 0,
    "error": 0,
    "warning": 0,
    "information": 0
  },
  "findings": [],
  "findingsTruncated": false,
  "previewCounts": {
    "fatal": 0,
    "error": 0,
    "warning": 0,
    "information": 0
  },
  "previewFindings": [],
  "previewFindingsTruncated": false,
  "sha256": "1b7cc3ff1834c8963f2c93f30f171b58002cbf0b2c52dc8765e7e83aebb9f7c9",
  "embeddedXmlSha256": null,
  "container": null,
  "checkedAt": "2026-07-29T11:51:09.618197Z",
  "reports": {},
  "error": null
}
```

</details>

<details>
<summary><strong>02. REJECTED</strong> - empty invoice ID fails active and preview business rules</summary>

[`02_live_rejected_output.json`](02_live_rejected_output.json)

```json
{
  "inputIndex": 1,
  "documentId": "mutated-empty-invoice-id",
  "fileName": "mutated-empty-invoice-id.xml",
  "processingStatus": "SUCCEEDED",
  "conformanceStatus": "REJECTED",
  "previewConformanceStatus": "REJECTED",
  "validationScope": "OFFLINE_PREFLIGHT",
  "externalStateStatus": "NOT_EVALUATED_EXTERNAL_STATE",
  "rulesetEffectiveAt": "2026-02-23",
  "sourceFormat": "XML",
  "validationFamily": "PEPPOL_BIS_BILLING",
  "syntax": "UBL_INVOICE",
  "profile": "PEPPOL_BIS_BILLING_3",
  "scenario": "Peppol BIS Billing 3 UBL Invoice",
  "versions": {
    "ubl": "2.1",
    "cenSchematronActive": "1.3.15",
    "cenSchematronPreview": "1.3.16",
    "peppolBisActive": "3.0.20",
    "peppolBisPreview": "3.0.21",
    "saxonHe": "10.9",
    "schematronSkeleton": "02f3707b194ce5792bf77b14a66d782c060abba3",
    "activeRuleset": {
      "name": "Peppol BIS Billing 3.0.20",
      "effectiveAt": "2026-02-23"
    },
    "previewRuleset": {
      "name": "Peppol BIS Billing 3.0.21",
      "effectiveAt": "2026-08-17"
    },
    "artifactManifestSha256": "ce0b34ba52412ea870785a58f316990d578d91717c3b1b396ed0f2e9f3fd5ef2"
  },
  "counts": {
    "fatal": 2,
    "error": 0,
    "warning": 0,
    "information": 0
  },
  "findings": [
    {
      "severity": "FATAL",
      "stage": "BUSINESS_RULE",
      "ruleId": "BR-02",
      "message": "[BR-02]-An Invoice shall have an Invoice number (BT-1).",
      "location": "/*:Invoice[namespace-uri()='urn:oasis:names:specification:ubl:schema:xsd:Invoice-2'][1]",
      "test": "normalize-space(cbc:ID) != ''",
      "ruleset": "EN16931-1.3.15"
    },
    {
      "severity": "FATAL",
      "stage": "BUSINESS_RULE",
      "ruleId": "PEPPOL-EN16931-R008",
      "message": "Document MUST not contain empty elements.",
      "location": "/*:Invoice[namespace-uri()='urn:oasis:names:specification:ubl:schema:xsd:Invoice-2'][1]/*:ID[namespace-uri()='urn:oasis:names:specification:ubl:schema:xsd:CommonBasicComponents-2'][1]",
      "test": "false()",
      "ruleset": "PEPPOL-BIS-3.0.20"
    }
  ],
  "findingsTruncated": false,
  "previewCounts": {
    "fatal": 2,
    "error": 0,
    "warning": 0,
    "information": 0
  },
  "previewFindings": [
    {
      "severity": "FATAL",
      "stage": "BUSINESS_RULE",
      "ruleId": "BR-02",
      "message": "[BR-02]-An Invoice shall have an Invoice number (BT-1).",
      "location": "/*:Invoice[namespace-uri()='urn:oasis:names:specification:ubl:schema:xsd:Invoice-2'][1]",
      "test": "normalize-space(cbc:ID) != ''",
      "ruleset": "EN16931-1.3.16-PREVIEW"
    },
    {
      "severity": "FATAL",
      "stage": "BUSINESS_RULE",
      "ruleId": "PEPPOL-EN16931-R008",
      "message": "[PEPPOL-EN16931-R008]-Document MUST not contain empty elements.",
      "location": "/*:Invoice[namespace-uri()='urn:oasis:names:specification:ubl:schema:xsd:Invoice-2'][1]/*:ID[namespace-uri()='urn:oasis:names:specification:ubl:schema:xsd:CommonBasicComponents-2'][1]",
      "test": "false()",
      "ruleset": "PEPPOL-BIS-3.0.21-PREVIEW"
    }
  ],
  "previewFindingsTruncated": false,
  "sha256": "96c9ed30f12c85489ca66091e8e045cf76cd284970c048b03ce6dd2ed753ba85",
  "embeddedXmlSha256": null,
  "container": null,
  "checkedAt": "2026-07-29T11:52:37.720171Z",
  "reports": {},
  "error": null
}
```

</details>

<details>
<summary><strong>03. NOT_EVALUATED</strong> - source policy stopped evaluation</summary>

[`03_live_not_evaluated_output.json`](03_live_not_evaluated_output.json)

```json
{
  "inputIndex": 2,
  "documentId": "source-error",
  "fileName": "blocked.xml",
  "processingStatus": "FAILED",
  "conformanceStatus": "NOT_EVALUATED",
  "previewConformanceStatus": "NOT_EVALUATED",
  "validationScope": "OFFLINE_PREFLIGHT",
  "externalStateStatus": "NOT_EVALUATED_EXTERNAL_STATE",
  "rulesetEffectiveAt": "2026-02-23",
  "sourceFormat": "UNKNOWN",
  "validationFamily": "UNKNOWN",
  "syntax": "UNKNOWN",
  "profile": "UNKNOWN",
  "scenario": null,
  "versions": {
    "ubl": "2.1",
    "cenSchematronActive": "1.3.15",
    "cenSchematronPreview": "1.3.16",
    "peppolBisActive": "3.0.20",
    "peppolBisPreview": "3.0.21",
    "saxonHe": "10.9",
    "schematronSkeleton": "02f3707b194ce5792bf77b14a66d782c060abba3",
    "activeRuleset": {
      "name": "Peppol BIS Billing 3.0.20",
      "effectiveAt": "2026-02-23"
    },
    "previewRuleset": {
      "name": "Peppol BIS Billing 3.0.21",
      "effectiveAt": "2026-08-17"
    },
    "artifactManifestSha256": "ce0b34ba52412ea870785a58f316990d578d91717c3b1b396ed0f2e9f3fd5ef2"
  },
  "counts": {
    "fatal": 0,
    "error": 0,
    "warning": 0,
    "information": 0
  },
  "findings": [],
  "findingsTruncated": false,
  "previewCounts": {
    "fatal": 0,
    "error": 0,
    "warning": 0,
    "information": 0
  },
  "previewFindings": [],
  "previewFindingsTruncated": false,
  "sha256": null,
  "embeddedXmlSha256": null,
  "container": null,
  "checkedAt": "2026-07-29T11:52:37.783264Z",
  "reports": {},
  "error": {
    "code": "SOURCE_FETCH_FAILED",
    "message": "Only HTTPS source URLs are allowed"
  }
}
```

</details>

## Production notes

- Input sources: Console upload, HTTPS URL with SSRF controls, inline XML, base64 XML, or Apify key-value store record.
- The rule packages and their SHA-256 checks are pinned at build time. Runtime validation does not download rules.
- One bad document does not stop the remaining batch.
- Evaluated `ACCEPTED` and `REJECTED` documents cost $0.004 each. `NOT_EVALUATED` is free.
- Source XML is not copied into dataset results.

Use [`dataset_record.schema.json`](dataset_record.schema.json) to validate webhook, Make, n8n, MCP, SDK, and warehouse ingestion. See [`DATA_NOTICE.md`](DATA_NOTICE.md) before publishing real invoice data.

For custom access-point integration or high-volume support, contact the owner through the [Apify Actor page](https://apify.com/kamerozkan/peppol-bis-preflight-validator).

## E-Invoice Automation Suite

This repository is part of a 16-product invoice automation family. Public Actor links are runnable Store listings. Private labels are release-state disclosures, not public availability claims.

- Public validators: [`xrechnung-xml-batch-validator-api`](https://apify.com/kamerozkan/xrechnung-xml-batch-validator-api) ([`xrechnung-xml-batch-validator-api-sample`](https://github.com/kamerozkan/xrechnung-xml-batch-validator-api-sample)), [`france-einvoice-validator`](https://apify.com/kamerozkan/france-einvoice-validator) ([`france-einvoice-validator-sample`](https://github.com/kamerozkan/france-einvoice-validator-sample)), [`italy-fatturapa-validator`](https://apify.com/kamerozkan/italy-fatturapa-validator) ([`italy-fatturapa-validator-sample`](https://github.com/kamerozkan/italy-fatturapa-validator-sample)), [`peppol-bis-preflight-validator`](https://apify.com/kamerozkan/peppol-bis-preflight-validator) ([`peppol-bis-preflight-validator-sample`](https://github.com/kamerozkan/peppol-bis-preflight-validator-sample)), and [`poland-ksef-preflight-validator`](https://apify.com/kamerozkan/poland-ksef-preflight-validator) ([`poland-ksef-preflight-validator-sample`](https://github.com/kamerozkan/poland-ksef-preflight-validator-sample)).
- Private validator preview: `romania-efactura-validator` ([`romania-efactura-validator-sample`](https://github.com/kamerozkan/romania-efactura-validator-sample)), private release preview with a successful hosted build.
- Private generators with successful hosted builds: `xrechnung-invoice-generator` ([`xrechnung-invoice-generator-sample`](https://github.com/kamerozkan/xrechnung-invoice-generator-sample)), `peppol-ubl-invoice-generator` ([`peppol-ubl-invoice-generator-sample`](https://github.com/kamerozkan/peppol-ubl-invoice-generator-sample)), `zugferd-facturx-pdf-generator` ([`zugferd-facturx-pdf-generator-sample`](https://github.com/kamerozkan/zugferd-facturx-pdf-generator-sample)), `fatturapa-invoice-generator` ([`fatturapa-invoice-generator-sample`](https://github.com/kamerozkan/fatturapa-invoice-generator-sample)), and `ksef-fa-invoice-generator` ([`ksef-fa-invoice-generator-sample`](https://github.com/kamerozkan/ksef-fa-invoice-generator-sample)).
- Parsers and converters: public [`zugferd-facturx-pdf-to-json`](https://apify.com/kamerozkan/zugferd-facturx-pdf-to-json) ([`zugferd-facturx-pdf-to-json-sample`](https://github.com/kamerozkan/zugferd-facturx-pdf-to-json-sample)); private release-ready `xrechnung-to-json-parser` ([`xrechnung-to-json-parser-sample`](https://github.com/kamerozkan/xrechnung-to-json-parser-sample)); private hosted-build-ready `peppol-ubl-to-json-parser` ([`peppol-ubl-to-json-parser-sample`](https://github.com/kamerozkan/peppol-ubl-to-json-parser-sample)), `zugferd-to-xrechnung-converter` ([`zugferd-to-xrechnung-converter-sample`](https://github.com/kamerozkan/zugferd-to-xrechnung-converter-sample)), and `ubl-cii-format-converter` ([`ubl-cii-format-converter-sample`](https://github.com/kamerozkan/ubl-cii-format-converter-sample)).
