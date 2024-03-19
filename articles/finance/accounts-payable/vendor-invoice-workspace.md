---
# required metadata

title: Vendor invoice center workspace overview
description: This article provides information about the Vendor invoice center workspace.
author: leizi2015
ms.date: 3/19/2024
ms.topic: overview

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

# Vendor invoice center overview

[!include [banner](../includes/banner.md)]

This article explains how to enable the Vendor invoice center workspace in Dynamics 365 Finance. The vendor invoice center workspace offers a view of the overall processing status of vendor invoices at
various stages. This functionality helps Accounts Payable (AP) Managers or AP Clerks with decision making and more efficient exception handling. 

## Overview: 

Using the **Vendor invoice center**, users can:
 - manage vendor invoices
 - import invoices
 - apply prepayments
 - match receipts
 - submit to workflow
 - approve workflow
 - post invoices

Drill-down lists provide detailed invoice information and help manage invoices more efficiently. 

The **Vendor invoice center** is available when the **(Preview) New vendor invoice center** feature is enabled in Feature management. It can't exist together with the old workspace Vendor invoice automation.  

### Vendor invoice center workspace 

The workspace is made up of following: 
 - Global filter for legal entity - Accounts Payable clerks can switch between different legal entities to check the overall invoice processing status. The invoice number and pending vendor invoice list displays the respective counts or lists based on the chosen legal entity.
 - Invoice processing tiles - The vendor invoice process tiles display different stages of invoices:
     - Capture and import
     - Manual entry
     - Automation
     - Workflow
     - To post 

Each stage has various status's that help the AP clerks check the detailed list of the invoices. Quick actions are available based on invoice status to accelerate their vendor invoice processing time.

### Capture and import stage 
Invoices in the Capture and import stage can have the following status:
- **Imported failed** - The invoice is being imported using the data entity, and it fails to be persisted in the pending vendor invoice. The subtile navigates to the **Vendor invoices that failed import** page to correct.
  
### Manual entry stage
Invoices in the **Manual entry** stage can have the following status:
- **Without errors** - Invoices that are created manually and aren't complete are in this status. The **Include in automation** action allows users to manually include the selected invoices in automation. The processing automation job automatically picks up the invoices and execute the corresponding jobs. The action button is visible when either the **Automatically submit invoice to workflow** or **Automatically match product receipts to invoice lines** parameters are enabled.   
 - **With validation errors** - The manually created invoice contains matching errors, caused by discrepancies during the two-way or three-way matching process. The **Accept price discrepancy** is available when it's required to resolve these discrepancies before proceeding with the vendor invoice process. This is controlled by the **Post invoice with discrepancies** parameter.
 - **With other errors**  - The invoice is generated manually, but it may contain errors. These errors require correction of the invoice details before submitting it to vendor invoice automation.


### Automation stage 

Invoice in the **Automation** stage can have the following status's:
- **In process** - Invoices are in automation processing and can't be edited. If additional changes are needed, the invoices can be manually excluded from automation process by clicking **Exclude from automation**.
 - **Apply prepayment error** - During the vendor invoice import process, the prepayment application is triggered if an existing prepayment is identified. An error may occur if the prepayment amount exceeds the invoice amount. The user needs to manually adjust the prepayment amount before applying for it or skip the prepayment application completely.
 - **Receipt match error** - The invoices are received prior to the product receipts. The invoices aren't completely matched with product receipts, but the receipt matching automation job has reached the maximum trials. The error displays a detailed list.
 - **Workflow submission error** - During invoice submission into the workflow, various validations are applied to ensure the invoice's completeness and accuracy. The detailed list view displays validation errors, which can help AP clerks to understand which action to be taken.
 - **Others** - The invoices that are included in automation but are temporarily paused due to additional corrections or adjustments needed without automation-related error. This feature enables the resumption of automation, allowing the invoices to be included in the process. 


### Workflow stage

Invoices in the workflow stage can have the following status:
 - **In process** - The invoices that are waiting for approval are displayed. Additional fields are available for the pending invoices that shows which person needs to approve the invoice, the pending time, and the due date for the approval. 
 - **Workflow failed** - The invoice was successfully submitted into the workflow, but an error occurred during the process due to additional validations within the workflow. This requires the invoice or settings to be updated before resubmitting the invoice into the workflow.
 - **Workflow rejected** - The invoice has been submitted for approval but was rejected due to specific reasons. The list provides the rejection reason given by the approver.
 - **For my approvals** - The invoice was submitted for approval within the workflow and is awaiting review. This process applies specifically to invoices configured with Vendor invoice workflow settings. 

### To post
Invoices in the To post stage can have the following status:
 - **Complete not posted** - The invoice has completed the workflow approval process and is waiting final posting. 

 

#### Documents not invoiced 

Most of the functions are inherited from the previous version. The pending vendor invoice is displayed as the default option in this section. **Edit all** is available to navigate to a list page for pending vendor invoices. 

