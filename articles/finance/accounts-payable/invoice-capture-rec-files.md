---
title: Invoice capture received files
description: Learn about how to collect invoice files from different sources in Invoice capture, including an outline on views in received files.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 08/09/2024
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

In Invoice capture, the **Received files** page is a central place where invoice files are received from different sources.

In most cases, the **Received files** process is automatic and doesn't require manual intervention. However, if there are exceptions or errors, the user must ensure that all invoice files have been correctly accounted, to help prevent omissions.

The **Manage file** filter can be used to apply different filter settings on the received invoice files. Invoice files that violate the filter rules won't be processed. On the **Received files** page, users can decide whether invoices can be included again when they're valid.

## Views in received files

The **Received file (pending)** page shows incoming files that violate filter rules.

- If an invoice isn't valid, you can mark it as **Voided** by selecting **Void**.
- If an invoice is valid, you can include it in the invoice process by selecting it and then selecting **Retry**.

The **Received file (voided)** page shows all files that are marked as **Voided**. If you select an invoice and then select **Delete**, it's permanently deleted from Microsoft Dataverse and can't be recovered.

The **Received file (captured)** page shows all files that have been successfully recognized and are in Dataverse.

- Select an invoice, and then select **View captured invoice** to view invoices in a side-by-side viewer, where users can review the invoice status and make corrections.
- Select **Download** to download the original invoice file.

## Received file statuses

| Status | Description | Action |
|---|---|---|
| Waiting | The invoice was captured by a Power Automate flow and is awaiting file validation. | No action is required. |
| In-process | File filter rules are being used to validate the invoice, or the invoice passed filter validation and is being recognized. | **Reset processing status** |
| Canceled | An exception occurred when a duplicate file was found, or file filter validation or the call to the recognitive service failed. | **Retry** or **Void** |
| Captured | The form recognizer result was moved to captured invoice staging. | **View captured invoice** |
| Voided | If the invoice isn't needed, select **Voided**. If an invoice has a status of **Voided**, you can permanently delete it from Dataverse by selecting **Obsoleted**. | **Obsolete** |

### Reset processing status

Occasionally, system issues might cause an invoice to become stuck in the **Processing** status. In this case, the business process might be blocked, because the user can't take further action. To prevent the disruptions that this issue can cause, a **Reset processing status** button appears on the Action Pane if an invoice remains stuck for more than five minutes. Users can use this option to reset the status and try to resubmit the invoice in the event of system failure.

### Duplicate file check

The duplicate file check uses the checksum method to determine whether the same file was previously received. If a file that has the same checksum result is detected, the invoice file status is set to **Cancelled**, and the reason is set to **Duplicate file found**. Users can still process the file further by selecting the entry and then selecting the **Retry** button.

> [!NOTE]
> The duplicate file check differs from validation that ensures that an invoice that has the same number wasn't previously received. Although such validation doesn't exist, it can be implemented via a custom extension during the invoice transfer in Dynamics 365 Finance.

## Upload invoice files

To upload invoice images, follow these steps.

1. Go to **Manage Invoices \> Received file**.
2. Select **Upload file**.
3. Select files by selecting the plus sign (**+**) frame.
4. Drag and drop the files. The selected files appear in the list.
5. Select **Upload**. The files immediately start to be uploaded.

    When the upload is completed, a success message is shown, and the uploaded files are removed from the list.

6. Close the pane. The **Received file** list is automatically refreshed.

## View history

Users can select an invoice and then select **View history** to view the processing details. Details include a description, the message type, and the processing time.
