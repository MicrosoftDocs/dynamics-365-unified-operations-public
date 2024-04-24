---
title: Vendor invoice center workspace overview
description: Learn about the Vendor invoice center workspace, including outlines on manual entry stages, automation stages, and workflow stages.
author: leizi2015
ms.author: zezhangzhao
ms.topic: overview
ms.date: 3/19/2024
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Vendor invoice center workspace overview

[!include [banner](../includes/banner.md)]

This article provides information about the **Vendor invoice center** workspace in Microsoft Dynamics 365 Finance. This workspace offers a view of the overall processing status of vendor invoices at different stages. It helps Accounts payable (AP) managers or AP clerks make decisions and handle exceptions more efficiently.

From the **Vendor invoice center** workspace, users can complete the following tasks:

- Manage vendor invoices.
- Import invoices.
- Apply prepayments.
- Match receipts.
- Submit invoices to the workflow.
- Approve the workflow.
- Post invoices.

Drill-down lists provide detailed invoice information and help manage invoices more efficiently.

The **Vendor invoice center** workspace is available when the **(Preview) New vendor invoice center** feature is enabled in Feature management. It can't exist together with the old **Vendor invoice automation** workspace.

### Vendor invoice center workspace

The **Vendor invoice center** workspace consists of following elements:

- **Global filter for legal entity** – AP clerks can switch between legal entities to review the overall invoice processing status. The invoice number and pending vendor invoice list shows the appropriate counts or lists, based on the selected legal entity.
- **Invoice processing tiles** – These tiles show the different stages of invoices:

    - Capture and import
    - Manual entry
    - Automation
    - Workflow
    - To post

    Each stage has one or more statuses that help AP clerks review the detailed list of the invoices. For each invoice status, quick actions are available to help accelerate vendor invoice processing.

### Capture and import stage

Invoices in the **Capture and import** stage can have the following status:

- **Imported failed** – The invoice is being imported by using the data entity, but it fails to be persisted in the pending vendor invoice. The sub-tile goes to the **Vendor invoices that failed import** page, where users can make corrections.

### Manual entry stage

Invoices in the **Manual entry** stage can have the following statuses:

- **Without errors** – The invoice was manually created and isn't complete. The **Include in automation** action lets users manually include selected invoices that have this status in automation processing. The processing automation job automatically picks up the invoices and runs the corresponding jobs. The action button is visible when either the **Automatically submit invoice to workflow** parameter or the **Automatically match product receipts to invoice lines** parameter is enabled.
- **With validation errors** – The invoice was manually created and contains matching errors that are caused by discrepancies during the two-way or three-way matching process. The **Accept price discrepancy** action lets users fix these discrepancies before they continue with the vendor invoice process. The action button is controlled by the **Post invoice with discrepancies** parameter.
- **With other errors** – The invoice was manually created and might contain errors. These errors require correction of the invoice details before the invoice can be submitted to vendor invoice automation.

### Automation stage 

Invoices in the **Automation** stage can have the following statuses:

- **In process** – The invoice is in automation processing and can't be edited. If changes are required, the **Exclude from automation** action lets users manually exclude the invoice from automation processing.
- **Apply prepayment error** – During the vendor invoice import process, prepayment application is triggered if an existing prepayment is identified. An error might occur if the prepayment amount exceeds the invoice amount. Users must manually adjust the prepayment amount before they apply it, or they must completely skip prepayment application.
- **Receipt match error** – The invoice was received before the product receipts. The invoice wasn't completely matched with product receipts, but the receipt matching automation job reached the maximum number of attempts. The error shows a detailed list.
- **Workflow submission error** – During invoice submission to the workflow, different validations are applied to ensure the invoice's completeness and accuracy. The detailed list view shows validation errors and can help AP clerks understand what action they must take.
- **Others** – The invoice was included in automation processing but is temporarily paused because additional corrections or adjustments are required without automation-related errors. The feature enables the resumption of automation processing, so that the invoice can be included in the process.

### Workflow stage

Invoices in the **Workflow** stage can have the following statuses:

- **In process** – The invoice is waiting for approval. Additional fields that are available for pending invoices show the person who must approve each invoice, the pending time, and the due date for the approval.
- **Workflow failed** – The invoice was successfully submitted to the workflow, but an error occurred during the process because of additional validations in the workflow. This error requires that users update the invoice or settings before they resubmit the invoice to the workflow.
- **Workflow rejected** – The invoice was submitted for approval, but it was rejected for specific reasons. The list provides the rejection reason that the approver provided.
- **For my approvals** – The invoice was submitted for approval in the workflow and is awaiting review. This process applies specifically to invoices that are configured with vendor invoice workflow settings.

### To post stage

Invoices in the **To post** stage can have the following status:

- **Complete not posted** – The invoice completed the workflow approval process and is awaiting final posting.

#### Documents not invoiced 

Most of the functions are inherited from the previous version. The pending vendor invoice is shown as the default option in this section. The **Edit all** action lets users open a list page for pending vendor invoices.
