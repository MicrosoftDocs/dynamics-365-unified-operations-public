---
title: Invoice capture received files
description: Learn about how to collect invoice files from different sources in Invoice capture, including an outline on views in received files.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 07/28/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Invoice capture received files

[!include [banner](../includes/banner.md)]

In Invoice capture, the **Received files** page is a central place where you receive invoice files from different sources.

In most cases, the **Received files** process is automatic and doesn't require manual intervention. However, if there are exceptions or errors, you must ensure that all invoice files are correctly accounted for to help prevent omissions.

Use the **Manage file** filter to apply different filter settings on the received invoice files. Invoice files that violate the filter rules aren't processed. On the **Received files** page, you can decide whether to include invoices again when they're valid.

## Views in received files

The **Received file (pending)** page shows incoming files that violate filter rules.

- If an invoice isn't valid, select **Void** to mark it as **Voided**.
- If an invoice is valid, include it in the invoice process by selecting it and then selecting **Retry**.

The **Received file (voided)** page shows all files that are marked as **Voided**. If you select an invoice and then select **Delete**, you permanently delete it from Microsoft Dataverse and can't recover it.

The **Received file (captured)** page shows all files that are successfully recognized and are in Dataverse.

- Select an invoice, and then select **View captured invoice** to view invoices in a side-by-side viewer, where you can review the invoice status and make corrections.
- Select **Download** to download the original invoice file.

## Received file statuses

| Status | Description | Action |
|---|---|---|
| Waiting | A Power Automate flow captured the invoice and is waiting for file validation. | No action required. |
| In-process | File filter rules validate the invoice, or the invoice passes filter validation and is recognized. | **Reset processing status** |
| Canceled | An exception occurs when a duplicate file is found, or file filter validation or the call to the recognitive service fails. | **Retry** or **Void** |
| Captured | The form recognizer result moves to captured invoice staging. | **View captured invoice** |
| Voided | If you don't need the invoice, select **Voided**. If an invoice has a status of **Voided**, you can permanently delete it from Dataverse by selecting **Obsoleted**. | **Obsolete** |

### Reset processing status

Occasionally, system issues cause an invoice to get stuck in the **Processing** status. In this case, the business process might be blocked, because the user can't take further action. To prevent the disruptions that this issue can cause, a **Reset processing status** button appears on the Action Pane if an invoice remains stuck for more than five minutes. Users can use this option to reset the status and try to resubmit the invoice in the event of system failure.

### Duplicate file check

The duplicate file check uses the checksum method to determine whether the same file was previously received. If a file with the same checksum result is detected, the invoice file status is set to **Cancelled**, and the reason is set to **Duplicate file found**. Users can still process the file further by selecting the entry and then selecting the **Retry** button.

> [!NOTE]
> The duplicate file check differs from validation that ensures that an invoice with the same number wasn't previously received. Although such validation doesn't exist, you can implement it through a custom extension during the invoice transfer in Dynamics 365 Finance.

## Upload invoice files

To upload invoice images, follow these steps:

1. Go to **Manage Invoices > Received file**.
1. Select **Upload file**.
1. Select the plus sign (**+**) to choose files.
1. Drag and drop the files. The selected files appear in the list.
1. Select **Upload**. The files immediately start to upload.

    When the upload finishes, a success message appears, and the uploaded files are removed from the list.

1. Close the pane. The **Received file** list automatically refreshes.

## View history

Select an invoice and then select **View history** to view the processing details. The details include a description, the message type, and the processing time.
