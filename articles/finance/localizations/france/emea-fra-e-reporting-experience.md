--- 
title: France e-reporting (electronic reporting of transactions) experience
description: Learn how to report electronically transaction in France. 
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 07/28/2026
ms.custom:
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: France
ms.search.validFrom: 2026-06-30
ms.search.form: CustTable, VendTable, OMLegalEntity
ms.dyn365.ops.version: Version 7.0.0 
---

# How to use France e-reporting in Dynamics 365 Finance

[!include [banner](../../includes/banner.md)]

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
| FR-eRep Generate Transactions Report     | Generates a report containing only transaction data                         | Action type: Message execution level<br> Format mapping: e-Reporting XML (FR)<br> Executable class: FR-eRep GenerateReportFile<br>Show dialog: No<br>Hide action class parameters: Yes  | <li>FR-eRep Transaction Report Created</li><li>FR-eRep Transaction Report Pending</li> | <li>FR-eRep Report Generated (Successfully executed)</li><li>FR-eRep Report Generation Failed (Technical error)</li><li>FR-eRep Transaction Report Excluded (Cancel)</li><li>FR-eRep Transaction Report Pending (Business error)</li> |
| FR-eRep Generate Payments Report         | Generates a report containing only payment data                             | Action type: Message execution level<br> Format mapping: e-Reporting XML (FR)<br> Executable class: FR-eRep GenerateReportFile<br>Show dialog: No<br>Hide action class parameters: Yes  | <li>FR-eRep Payment Report Created</li><li>FR-eRep Payment Report Pending</li> | <li>FR-eRep Report Generated (Successfully executed)</li><li>FR-eRep Report Generation Failed (Technical error)</li><li>FR-eRep Payment Report Excluded (Cancel)</li><li>FR-eRep Payment Report Pending (Business error)</li> |
| FR-eRep Generate Full Report             | Generates a complete report including both transactions and payments        | Action type: Message execution level<br> Format mapping: e-Reporting XML (FR)<br> Executable class: FR-eRep GenerateReportFile<br>Show dialog: No<br>Hide action class parameters: Yes  | <li>FR-eRep Transaction Report Created</li><li>FR-eRep Transaction Report Pending</li><li>FR-eRep Payment Report Created</li><li>FR-eRep Payment Report Pending</li> | <li>FR-eRep Report Generated (Successfully executed)</li><li>FR-eRep Report Generation Failed (Technical error)</li><li>FR-eRep Transaction Report Excluded (Cancel)</li><li>FR-eRep Transaction Report Pending (Business error)</li><li>FR-eRep Payment Report Excluded (Cancel)</li><li>FR-eRep Payment Report Pending (Business error)</li> |
| FR-eRep Regenerate Report File           | Regenerates the report after data changes or corrections                    | Action type: Electronic reporting export message<br>Format mapping: e-Reporting XML (FR)<br>Show dialog: No | <li>FR-eRep Report Generated</li><li>FR-eRep Report Generation Failed</li><li>FR-eRep Report Submitted</li> | <li> FR-eRep Report Generated (Successfully executed) </li><li> FR-eRep Report Generation Failed (Technical error)</li> |
| FR-eRep Mark Report as Submitted         | Marks the report as submitted after completion of the reporting process     | Action type: Message level user processing | <li>FR-eRep Report Generated | <li>FR-eRep Report Submitted |

## Action flow details

To report France e-reporting data, follow these steps.

### Populate data

To populate data, follow these steps:

1. In Finance, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic message items**.
1. On the Action Pane, select **Run processing**.
1. In the dialog, in the **Processing** field, select **FR e-Reporting**.
1. Select the **Choose action** checkbox, and then, in the **Action** field, select the **FR-eRep Populate Report Data** action.
1. Expand the **Run in the background** FastTab and specify the **Recurrence** settings for the **FR-eRep Populate Report Data** action. For example, if you want the system to collect data for e-reporting on a daily basis, define the recurrence pattern as every weekday.
1. Mark the **Batch processing** checkbox to execute the **FR-eRep Populate Report Data** action in the background according to defined recurrence settings.

### Review e-reporting entries

After data is populated, you can control which records are included in the report output:

- Use **FR-eRep Exclude Transaction Entry** or **FR-eRep Exclude Payment Entry** actions to remove entries from the report or postpone their reporting.
- Use **FR-eRep Reactivate Transaction Entry** or **FR-eRep Reactivate Payment Entry** to include entries again in the report to be generated.

To review e-reporting entries, follow these steps:

1. In Finance, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic message items**.
1. On the Action Pane, select **Update status**.
1. In the dialog, in the **Processing** field, select **FR e-Reporting**.
1. In the **Action** field, select relevant action.
1. In the **New status** field, select the status to apply to the selected message items.

This step ensures that only relevant data is included in the final report.

### Generate reports

You can generate different report outputs depending on your reporting needs:

- FR-eRep Generate Transactions Report – transactions only
- FR-eRep Generate Payments Report – payments only
- FR-eRep Generate Full Report – combined report

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

1. In Finance, go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic messages**.
1. For the **FR e-Reporting** processing, find and select the electronic message that you previously submitted.
1. Expand the **Additional fields** FastTab and select the **FR-eRep TypeCode** additional field. Select **RE** value (Rectificative) for the **FR-eRep TypeCode** additional field.
1. Select **Generate report** button on the **Messages** FastTab to regenerate the report.

When you generate an XML file for the FR e-Reporting, you attach it to the electronic message. To view the file, select the electronic message, and select the **Attachments** button (paper clip symbol) in the upper-right corner of the page. On the **Attachments for Message** page, select the attachment, and then, on the Action Pane, select **Open**.

### Finalize reporting

Use **FR-eRep Mark Report as Submitted** to complete the process. This action changes the electronic message status to **FR-eRep Report Submitted**, indicating that the report is successfully submitted to the French tax authorities through an approved intermediary platform.

To finalize reporting, follow these steps:

1. In Finance, go to **Tax > Inquiries and reports > Electronic messages > Electronic message**.
1. On the Action Pane, select **Update status**.
1. In the dialog, in the **Processing** field, select **FR e-Reporting**.
1. In the **Action** field, select the **FR-eRep Mark Report as Submitted** action.
1. In the **New status** field, select the **FR-eRep Report Submitted** status to apply to the selected message.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
