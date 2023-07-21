---
# required metadata

title: Invoice capture received files
description: This article explains how to collect invoice files from different sources in Invoice capture.
author: sunfzam
ms.date: 07/19/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture received files

[!include [banner](../includes/banner.md)]

In Invoice capture, the **Received files** page is a central place where invoice files are received from different sources.

In most cases, the **Received files** process is automatic and doesn't require manual intervention. However, if there are exceptions or errors, the user must ensure that all invoice files have been correctly accounted, to help prevent omissions.

The **Manage file** filter can be used to apply different filter settings on the received invoice files. Invoice files that violate the filter rules won't be processed. On the **Received files** page, users can decide whether invoices can be included again when they're valid.

## View captured invoices

The **Received file (pending)** page shows incoming files that violate filter rules.

- If an invoice isn't valid, you can mark it as **Voided** by selecting **Void**.
- If an invoice is valid, you can include it in the invoice process by selecting it and then selecting **Retry**.

The **Received file (voided)** page shows all files that are marked as **Voided**. If you select an invoice and then select **Delete**, it's permanently deleted from Microsoft Dataverse and can't be recovered.

The **Received file (captured)** page shows all files that have been successfully recognized and are in Dataverse.

- Select an invoice, and then select **View captured invoice** to view invoices in a side-by-side viewer, where users can review the invoice status and make corrections.
- Select **Download** to download the original invoice file.

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
