---
title: Use France e-reporting in Dynamics 365 Finance to submit using EDICOM connection
description: Learn how to generate France e-reporting documents in Dynamics 365 Finance and submit them to the tax authorities through the EDICOM connection.
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

# How to use France e-reporting in Dynamics 365 Finance to submit using EDICOM connection

[!INCLUDE [banner](../../includes/banner.md)]

This article is a continuation of the [How to use France e-reporting in Dynamics 365 Finance](emea-fra-e-reporting-experience.md) article and explains how you can send the generated e-report directly to the French tax authorities through EDICOM and track the authority's response, without leaving Dynamics 365 Finance.

Complete the report generation described in the [How to use France e-reporting in Dynamics 365 Finance](emea-fra-e-reporting-experience.md) first. Then use the steps in this article to submit the report to EDICOM, request its processing status, and handle rejections and corrections.

The submission uses the **FR e-Reporting** electronic message processing. Each generated document is represented as one electronic message that contains the transactions and payments for a single reporting period and direction.

For information about how to set up the connection, see [Set up the EDICOM integration for France e-Reporting](emea-fra-e-reporting-edicom-integration-guide.md).

> [!NOTE]
> This article assumes that the France e-reporting feature and the EDICOM connection are already configured. If a document doesn't generate, or the EDICOM actions aren't available, verify the setup that's described in the preparation articles.

## Privacy notice

When you enable Finance to interoperate with EDICOM for e-Reporting, the system shares customer content with EDICOM to process and submit e-Reports. This content might include sales, purchase, and payment information, as well as e-Reporting status acknowledgement details. To learn more about the information required for e-Reporting submissions, review [EDICOM's documentation](https://go.microsoft.com/fwlink/?LinkId=2378296). A system administrator can disable the EDICOM interoperation in Finance by going to **Tax** > **Setup** > **Electronic Messages**. Your privacy is important to us. To learn more, read our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=521839).

## Submission lifecycle at a glance

A France e-reporting document moves through the following stages when you submit it through EDICOM:

1. **Collect data** – The **FR-eRep Populate Report Data** action collects the transactions and payments for the reporting period into message items.
1. **Generate the report** – The generation action produces the France e-reporting XML file and attaches it to the electronic message.
1. **Submit to EDICOM** – The **FR-eRep Submit to EDICOM** web service action sends the generated file to the EDICOM endpoint.
1. **Request the status** – The status-request action polls EDICOM for the processing result.
1. **Import the response** – The response-import action stores the EDICOM identifiers and the authority status on the message.
1. **Handle the outcome** – If the authority accepts the document, the message is complete. If it's rejected, you correct the data and submit corrected e-report.

## Open the FR e-Reporting processing

1. Ensure that you're working in the legal entity that reports for France.
1. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.
1. In the list of processing, select **FR e-Reporting**.

The **Electronic messages** page shows the messages for the processing and the actions that are available on the Action Pane. The available actions depend on the current status of the selected message.

## Generate the France e-reporting document

Before you submit an e-report to EDICOM, collect the data and generate (or regenerate) the France e-reporting document as described in the [How to use France e-reporting in Dynamics 365 Finance](emea-fra-e-reporting-experience.md) article. When you generate the e-report, the file is attached to the electronic message and the message reaches the generated status (**FR-eRep Report Generated**), which is the starting point for the EDICOM submission steps in the following section.

> [!TIP]
> You can submit a document only after the reporting period is complete. Items from an incomplete period remain ungenerated so that they're included in the correct period.

## Submit e-report to EDICOM

1. On the **Electronic messages** page, select the message that has the generated status.
1. On the Action Pane, select **Send report**, mark **Choose action** checkbox and select  **FR-eRep Submit to EDICOM** action in the **Action** field.

The **FR e-Reporting** processing runs a single sequence of actions that execute one after another. Each action starts only after the previous one completes successfully:

- **FR-eRep Submit Report File** – Sends the generated e-reporting file to EDICOM.
- **FR-eRep Get Report Status** – Requests the processing status of the submitted file from EDICOM. 
- **FR-eRep Import Report Status** – Imports the returned status into the electronic message.
- **FR-eRep Confirm Report Status** – Sends the confirmation for the received status back to EDICOM.
- **FR-eRep Import Status Confirmation** – Imports the confirmation response into the electronic message.

Because the actions run as one sequence, you don't run them individually. If any action in the sequence doesn't complete successfully, the sequence stops at that action. Review the **Action log** on the message to identify which action failed and why. Resolve the cause, and then select **Send report** again to rerun the sequence from where it's needed.

EDICOM validates the e-report and forwards it to the tax authority asynchronously. When the **FR-eRep Submit Report File** action succeeds, the following message is displayed:

> The e-Report has been successfully published to EDICOM.
>
> We will now attempt to retrieve the validation status of the submitted e-Report. This process might take up to **15 minutes**, depending on when the validation status becomes available in the EDICOM portal.
>
> Don't close or refresh this page while the operation is running, as this action terminates the current attempt.
>
> If the validation status isn't available within 15 minutes, or if you choose **Cancel**, you can retry later by clicking **Send report**.

You can repeat the status request until the document reaches a final status (**FR-eRep Report Submitted**).

## Review the submission result

For each message, you can review the full history of the exchange:

- The message status shows the current stage of the submission lifecycle.
- The action log records the user, date, and time of each submission and status request.
- The stored response attachments contain the EDICOM communication details and any error details that were returned.

Use this information to reconcile the reported data with EDICOM and to provide evidence of transmission.

## Correct a submitted period

If data changes after a period was submitted and accepted, you must send a rectifying transmission for that period instead of a new initial transmission.

1. Make the required corrections in the source transactions or payments.
1. Confirm that **FR-eRep TypeCode** additional field is set to the rectifying value (**RE – Rectificative**) rather than the initial value (**IN – Initiale**).
1. Regenerate the output file for the electronic message for the affected period using **FR-eRep Regenerate Report File** action so that the XML reflects the corrected data.
1. Submit the rectifying document to EDICOM by using the **FR-eRep Submit to EDICOM** action as you did for the initial submission.

> [!IMPORTANT]
> Changes that you make before a period is submitted don't require a rectifying transmission. Regenerate the document, and the initial type code is retained. Only changes to an already submitted period require a rectifying transmission.
