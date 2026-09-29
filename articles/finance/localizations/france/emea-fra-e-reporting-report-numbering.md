---
title: France e-reporting report numbering and identifiers in Dynamics 365 Finance
description: Learn about France e-reporting report numbering and identifiers in Dynamics 365 Finance
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 09/28/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2026-04-24
ms.dyn365.ops.version: AX 10.0.48
---

# France e-reporting report numbering and identifiers in Dynamics 365 Finance

[!INCLUDE [banner](../../includes/banner.md)]

A France e-reporting submission is traced through its lifecycle by a small set of identifiers. Some of these identifiers are created and owned by Dynamics 365 Finance, and others are received from the partner platform (PDP) and stored on the electronic message for reference. This article focuses on the Finance side: which identifiers Finance generates, how it builds the report number, where each identifier is stored, and how Finance uses these identifiers when it publishes a report and requests its status.

> [!NOTE]
> This article describes the identifiers from the Finance perspective. The identifiers that the PDP (EDICOM) and the tax authority assign are covered only to the extent that Finance stores and reuses them.
> For the end-to-end submission flow, see [Use France e-reporting in Dynamics 365 Finance to submit using EDICOM connection](emea-fra-e-reporting-edicom-submission.md).

## Identifiers at a glance

| Identifier | Scope | Where it's stored in Finance | How Finance uses it |
| --- | --- | --- | --- |
| **Message ID** | Uniquely identifies the e-report for a **reporting period** + **document type** + **document direction**. | The electronic message record. | Anchors the report to a single period and direction, and serves as the base for the document number. |
| **Document number** | Identifies the specific transmission of the e-report on the authority side. | Not stored as a separate value; embedded in the generated report file in `/Report/ReportDocument/Id` element of e-report. | Numbers each generated file so that a transmission can be traced by the authority. |
| **Publishing GUID** | Correlates a single publish operation with its later status request. | The electronic message: `ElectronicMessages.UID` <br> The action log: `ElectronicMessagesLog.UID` | Used on the status request so that the response is paired with the original submission. |

## Message ID

The **Message ID** is the primary identifier that Finance assigns to an e-reporting electronic message. It uniquely identifies the e-report for a combination of:

- **Reporting period** – the period that the report covers (for example, a ten-day transaction period or a monthly payment period, depending on the VAT regime).
- **Document type** – the report type that's being produced (transactions or payments).
- **Document direction** – the reporting direction (for example, sales or purchases).

Because the Message ID is bound to this combination, all transmissions for the same period, type, and direction — including a rectifying transmission that replaces an already-submitted period — share the same Message ID. 
Finance stores the Message ID on the electronic message and uses it as the stable anchor for the report throughout the lifecycle.

The **Message ID** is implemented in the way that's described here regardless of how you submit the report — whether you use the [direct submission to EDICOM](emea-fra-e-reporting-edicom-submission.md) or you only generate the report file and transmit it by your own means, this identifier is built and used the same way.

## Document number

The **Document number** identifies the specific transmission of the e-report that Finance produces at generation time. Finance builds it by combining the Message ID with the moment of generation:

```
Document number = Message ID + generation date-time stamp (yyyyMMddHHmmss)
```

Key characteristics of the document number:

- Finance generates it when producing the report file, so it captures the exact date and time (`yyyyMMddHHmmss`) that the file was generated in the `/Report/ReportDocument/Id` element of the e-report.
- Because the timestamp changes on every generation, each regeneration of the same period produces a new, distinct document number, even though the underlying Message ID stays the same. This characteristic distinguishes an initial transmission from a rectifying transmission of the same period.
- The generated report file contains the embedded document number, and the authority uses it to identify the received e-report.

Regardless of how you submit the report, implement the **Document number** as described in this section. Whether you use the [direct submission to EDICOM](emea-fra-e-reporting-edicom-submission.md) or you only generate the report file and transmit it by your own means, you build and use this identifier in the same way.

## Publishing GUID

The **Publishing GUID** correlates a publish operation with the status request that follows it. When Finance publishes (submits) the generated report, it generates a Publishing GUID for that publish operation. Finance stores the GUID and then reuses the same value when it sends the status request, so that the PDP can pair the status request with the original submission and return the correct result.

Because Finance reuses the same GUID for the status request, it uses the Publishing GUID to retrieve the status of a specific submission instead of any other outstanding transmission.

Use the **Publishing GUID** only when you submit the report through the [built-in EDICOM integration](emea-fra-e-reporting-edicom-submission.md). If you only generate the report file and don't use the direct submission, this identifier doesn't apply.
