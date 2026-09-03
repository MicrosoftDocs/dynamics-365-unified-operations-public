--- 
title: France e-reporting (electronic reporting of transactions) experience
description: Learn how to report electronically transaction in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 09/02/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# How to use France e-reporting in Dynamics 365 Finance

[!INCLUDE [banner](../../includes/banner.md)]

You run the France e‑reporting process through the [Electronic messages](../../general-ledger/electronic-messaging-setup.md) framework. This process is a sequence of actions that you can use to:

- Collect and prepare reporting data
- Review transactions and payments to report
- Generate the reporting output in XML format
- Manage corrections and reprocessing
- Finalize the reporting process

## Process overview

The preceding diagram shows the overall process flow.

:::image type="content" source="../media/emea-fra-e-reporting-em-processing.png" alt-text="Screenshot of France e-reporting processing.":::

The reporting process typically follows these steps:

1. Populate message items by collecting transaction and payment data.
1. Optionally exclude or reactivate specific entries.
1. Generate the report (transactions, payments, or full report).
1. Optionally regenerate the report if corrections are required.
1. Mark the report as submitted after final validation.

> [!NOTE]
> The France e‑reporting process supports reporting for multiple VAT registrations that use the same Electronic Messages (EM) processing flow as described in this section.
> No additional processing actions are required. The difference lies in how data is selected during the execution of the **FR‑eRep PopulateMessageItems** executable class. For more information, see the [Set up FR e-Reporting to report in multiple VAT registrations legal entity](emea-fra-e-reporting-preparation.md#set-up-multi-tax).

The following actions are available in the France e‑reporting process:

| Action name                              | Description                                                                 | Parameters | Initial statuses | Result statuses |
|------------------------------------------|-----------------------------------------------------------------------------|------------|------|------------|
| FR-eRep Populate Report Data             | Collects transaction and payment data and creates message items             | Action type: Message item execution level<br> Executable class: FR-eRep PopulateMessageItems | - | <li>FR-eRep Payment Entry Created</li><li>FR-eRep Transaction Entry Created</li> |
| FR-eRep Exclude Transaction Entry        | Excludes a transaction entry from the reporting process                     | Action type: User processing | <li>FR-eRep Transaction Entry Created</li><li>FR-eRep Transaction Entry Pending</li>| <li>FR-eRep Transaction Entry Excluded</li> |
| FR-eRep Exclude Payment Entry            | Excludes a payment entry from the reporting process                         | Action type: User processing | <li>FR-eRep Payment Entry Created</li><li>FR-eRep Payment Entry Pending</li>| <li>FR-eRep Payment Entry Excluded</li> |
| FR-eRep Reactivate Transaction Entry     | Restores a previously excluded transaction entry                            | Action type: User processing | <li>FR-eRep Transaction Entry Excluded</li>| <li>FR-eRep Transaction Entry Created</li> |
| FR-eRep Reactivate Payment Entry         | Restores a previously excluded payment entry                                | Action type: User processing | <li>FR-eRep Payment Entry Excluded</li>| <li>FR-eRep Payment Entry Created</li> |
| FR-eRep Generate Transactions Report     | Generates a report containing only transaction data                         | Action type: Message execution level<br> Format mapping: e-Reporting XML (FR)<br> Executable class: FR-eRep GenerateReportFile<br>Show dialog: No<br>Hide action class parameters: Yes  | <li>FR-eRep Transaction Report Created</li><li>FR-eRep Transaction Report Pending</li><li>FR-eRep Report Generated</li><li>FR-eRep Report Submitted</li> | <li>FR-eRep Report Generated (Successfully executed)</li><li>FR-eRep Report Generation Failed (Technical error)</li><li>FR-eRep Transaction Report Excluded (Cancel)</li><li>FR-eRep Transaction Report Pending (Business error)</li> |
| FR-eRep Generate Payments Report         | Generates a report containing only payment data                             | Action type: Message execution level<br> Format mapping: e-Reporting XML (FR)<br> Executable class: FR-eRep GenerateReportFile<br>Show dialog: No<br>Hide action class parameters: Yes  | <li>FR-eRep Payment Report Created</li><li>FR-eRep Payment Report Pending</li><li>FR-eRep Report Generated</li><li>FR-eRep Report Submitted</li> | <li>FR-eRep Report Generated (Successfully executed)</li><li>FR-eRep Report Generation Failed (Technical error)</li><li>FR-eRep Payment Report Excluded (Cancel)</li><li>FR-eRep Payment Report Pending (Business error)</li> |
| FR-eRep Generate Full Report             | Generates a complete report including both transactions and payments        | Action type: Message execution level<br> Format mapping: e-Reporting XML (FR)<br> Executable class: FR-eRep GenerateReportFile<br>Show dialog: No<br>Hide action class parameters: Yes  | <li>FR-eRep Transaction Report Created</li><li>FR-eRep Transaction Report Pending</li><li>FR-eRep Payment Report Created</li><li>FR-eRep Payment Report Pending</li><li>FR-eRep Report Generated</li><li>FR-eRep Report Submitted</li> | <li>FR-eRep Report Generated (Successfully executed)</li><li>FR-eRep Report Generation Failed (Technical error)</li><li>FR-eRep Transaction Report Excluded (Cancel)</li><li>FR-eRep Transaction Report Pending (Business error)</li><li>FR-eRep Payment Report Excluded (Cancel)</li><li>FR-eRep Payment Report Pending (Business error)</li> |
| FR-eRep Regenerate Report File           | Regenerates the report after data changes or corrections                    | Action type: Electronic reporting export message<br>Format mapping: e-Reporting XML (FR)<br>Show dialog: No | <li>FR-eRep Report Generated</li><li>FR-eRep Report Generation Failed</li><li>FR-eRep Report Submitted</li> | <li> FR-eRep Report Generated (Successfully executed) </li><li> FR-eRep Report Generation Failed (Technical error)</li> |
| FR-eRep Mark Report as Submitted         | Marks the report as submitted after completion of the reporting process     | Action type: Message level user processing | <li>FR-eRep Report Generated | <li>FR-eRep Report Submitted |

## Action flow details

To report France e-reporting data, follow these steps.

### Populate data

To populate data, follow these steps:

1. In Finance, go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic message items**.
1. On the Action Pane, select **Run processing**.
1. In the dialog, in the **Processing** field, select **FR e-Reporting**.
1. Select the **Choose action** checkbox, and then, in the **Action** field, select the **FR-eRep Populate Report Data** action.
1. Expand the **Run in the background** FastTab and specify the **Recurrence** settings for the **FR-eRep Populate Report Data** action. For example, if you want the system to collect data for e-reporting on a daily basis, define the recurrence pattern as every weekday.
1. Select the **Batch processing** checkbox to execute the **FR-eRep Populate Report Data** action in the background according to the defined recurrence settings.

### Review e-reporting entries

After data is populated, you can control which records are included in the report output:

- Use **FR-eRep Exclude Transaction Entry** or **FR-eRep Exclude Payment Entry** actions to remove entries from the report or postpone their reporting.
- Use **FR-eRep Reactivate Transaction Entry** or **FR-eRep Reactivate Payment Entry** to include entries again in the report to be generated.

To review e-reporting entries, follow these steps:

1. In Finance, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic message items**.
1. On the **Action** pane, select **Update status**.
1. In the dialog, in the **Processing** field, select **FR e-Reporting**.
1. In the **Action** field, select relevant action.
1. In the **New status** field, select the status to apply to the selected message items.

This step ensures that only relevant data is included in the final report.

### Generate reports

You can generate different report outputs depending on your reporting needs. The following actions are available:

- **FR-eRep Generate Transactions Report** – transactions only
- **FR-eRep Generate Payments Report** – payments only
- **FR-eRep Generate Full Report** – combined report

The action that you select determines which data type is included in the run, according to your company's business needs. Choose **FR-eRep Generate Full Report** to let the system process all collected message items and decide automatically how to distribute them, or choose **FR-eRep Generate Transactions Report** or **FR-eRep Generate Payments Report** to restrict the run to a single data type.

Regardless of which action you select, the system automatically distributes the collected message items into one or several electronic messages and output files, so that each file contains only records that belong together for reporting. An output file is created for each unique combination of the following criteria:

- **Data type** – transaction data and payment data are always reported in separate files.
- **Document direction** – outgoing documents (customer sales) and incoming documents (vendor reverse charge, that is, purchases self-assessed by the declarant) are reported in separate files.
- **Reporting period** – records are separated by the reporting period that's derived from the **VAT regime** parameter of the **FR-eRep GenerateReportFile** executable class, together with the operation date (transaction data) or the collection date (payment data) and report generation date. Each file covers a single reporting period.

As a result, a single generation run can create multiple electronic messages and files attached to them. For example, when you run **FR-eRep Generate Full Report** for a declarant on the **Standard VAT regime - Monthly regime**, the system can produce separate files for outgoing and incoming transaction data for each ten-day period, and separate files for outgoing and incoming payment data for each month, based on the records that were collected. When you run **FR-eRep Generate Transactions Report** or **FR-eRep Generate Payments Report**, the same split applies but is limited to the selected data type.

Each generated file carries a transmission-type tag whose value the system populates from the **FR-eRep TypeCode** additional field of the electronic message (**IN** – Initiale for an initial transmission or **RE** – Rectificative for a rectifying transmission). For more information about how the reporting period and the VAT regime are configured, see [How to prepare your Dynamics 365 Finance for French e-Reporting](emea-fra-e-reporting-preparation.md).

The system includes message items in a generated file only when their reporting period is complete. A reporting period is considered complete after its last day has passed. Items that belong to a period that's still open—that is, a period whose end date hasn't yet been reached—aren't included in any file. They remain in the system and are picked up automatically for generation after the period is complete. This behavior ensures that a period is reported only once its data is final, and that a file is never transmitted for a period that's still in progress.

>[!TIP]
>**Example**
>
>A declarant uses the **Standard VAT regime - Monthly** VAT regime, so transaction data is reported in ten-day periods (1–10, 11–20, and 21–end of month). The following invoices have been collected as message items:
>
>- Invoice A, dated 5 September – belongs to the 1–10 September period.
>- Invoice B, dated 15 September – belongs to the 11–20 September period.
>- Invoice C, dated 25 September – belongs to the 21–30 September period.
>
>  The 1–10 September period was already generated and submitted. The current date is 26 September. When report generation runs on 26 September, the outcome is as follows:
>
>- 1–10 September – The period is complete and was already submitted. If its data changed, the system regenerates the file for this period as a rectifying transmission (**RE** – Rectificative), which cancels and replaces the previously submitted aggregate. Invoice A is reported in this rectifying file. If you use the EDICOM integration provided by Microsoft, the **FR-eRep TypeCode** additional field is set to **RE** automatically upon receipt of the authority's confirmation of a successful submission. If you don't use the EDICOM integration, you must update the **FR-eRep TypeCode** additional field to **RE** manually before you regenerate the file for this period.
>- 11–20 September – The period is complete but hasn't been reported yet. The system generates a new electronic message for the initial transmission (**IN** – Initiale) for this period. Invoice B is reported in this new file.
>- 21–30 September – The period is still open on 26 September, because its last day hasn't passed. Invoice C isn't included in any file and remains untouched. It's picked up automatically for generation after 30 September, once the period is complete.

To generate reports, follow these steps:

1. In Finance, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic message items**.
1. On the Action Pane, select **Run processing**.
1. In the dialog, in the **Processing** field, select **FR e-Reporting**.
1. Select the **Choose action** checkbox, and then, in the **Action** field, select one of the actions: **FR-eRep Generate Full Report**, **FR-eRep Generate Transactions Report**, or **FR-eRep Generate Payments Report**.
1. Expand the **Run in the background** FastTab and specify the **Recurrence** settings for the selected action. For example, if you want the system to generate a report once every 10 days, define the recurrence pattern as every 10 days.
1. Mark the **Batch processing** checkbox to execute the selected action in the background according to defined recurrence settings.

The action log related to the electronic message log information about the user who generated the **FR e-Reporting** and performed other actions with the electronic message.

When you generate an XML file for the FR e-Reporting, you attach it to the electronic message. To view the file, select the electronic message, and select the **Attachments** button (paper clip symbol) in the upper-right corner of the page. On the **Attachments for Message** page, select the attachment, and then, on the Action Pane, select **Open**.

### Regenerate reports

Use **FR-eRep Regenerate Report File** if you need to submit a corrected report after you already submitted the original report.

To regenerate reports, follow these steps:

1. In Finance, go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.
1. For the **FR e-Reporting** processing, find and select the electronic message that you previously submitted.
1. Expand the **Additional fields** FastTab and select the **FR-eRep TypeCode** additional field. Select **RE** value (Rectificative) for the **FR-eRep TypeCode** additional field.
1. Select **Generate report** button on the **Messages** FastTab to regenerate the report.

When you generate an XML file for the FR e-Reporting, you attach it to the electronic message. To view the file, select the electronic message, and select the **Attachments** button (paper clip symbol) in the upper-right corner of the page. On the **Attachments for Message** page, select the attachment, and then, on the Action Pane, select **Open**.

### Finalize reporting

Use **FR-eRep Mark Report as Submitted** to complete the process. This action changes the electronic message status to **FR-eRep Report Submitted**, indicating that the report is successfully submitted to the French tax authorities through an approved intermediary platform.

To finalize reporting, follow these steps:

1. In Finance, go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic message**.
1. On the Action Pane, select **Update status**.
1. In the dialog, in the **Processing** field, select **FR e-Reporting**.
1. In the **Action** field, select the **FR-eRep Mark Report as Submitted** action.
1. In the **New status** field, select the **FR-eRep Report Submitted** status to apply to the selected message.
1. Set the value of the **FR-eRep TypeCode** additional field to **RE** so that any subsequent regeneration of the report for this period is generated as a rectifying transmission.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
