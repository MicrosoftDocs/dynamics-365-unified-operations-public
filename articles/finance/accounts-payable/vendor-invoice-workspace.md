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

This article explains how to enable the Vendor invoice center workspace in Dynamics 365 Finance. The vendor invoice center workspace offers an intuitive view of the overall processing status of vendor invoices at
various stages. This functionality assists with Accounts Payable (AP) Managers or AP Clerks in decision making and more efficient exceptions handling. 

## Overview: 

Vendor invoice center presents a new interface for managing vendor invoices, starting from capturing/importing invoices, through prepayment application, receipt matching, workflow submission, workflow approval, 
and ready for posting at the end. The drill-down lists provide detailed invoice information and offer quick actions to help manage invoices more efficiently. 

The **Vendor invoice center** is available when the **(Preview) New vendor invoice center** feature is enabled in Feature management. It can't exist together with the old workspace Vendor invoice automation.  

 

Components in the workspace: 

The workspace is mainly constructed by the following components: 

Global filter for legal entity: 

Accounts Payable clerks can switch between different legal entities to check the overall invoice processing status. The invoice number and pending vendor invoice list will display the respective counts or lists 
based on the chosen legal entity. 

Invoice processing tiles: 

A screenshot of a computer

Description automatically generated 

The vendor invoice process tiles present the invoices at different stages, which include: 

Capture and import 

Manual entry 

Automation 

Workflow 

To post 

Under each stage, it has various subtitles to let the AP clerks check the detailed list of the invoices, it offers quick actions based on the status of the invoices to accelerate their vendor invoice processing
time: 

Capture and import: 

Imported failed 

The invoice with this status happens when the invoice is trying to import via the data entity, and it fails to be persisted in the pending vendor invoice. The subtile will navigate the user to the form 
“Vendor invoices that failed import” to make the corresponding correction.  

 

Manual entry: 

Without errors 

Invoices which are created manually and not complete yet will be left in this status. The action “Include in automation” action will allow user to manually include the selected invoices in automation and the
processing automation job will automatically pick up the invoices and execute the corresponding jobs. The action button is only visible when one of the parameters “Automatically submit invoice to workflow” or 
“Automatically match product receipts to invoice lines” under Accounts payable parameters > Vendor invoice automation is enabled.  

With validation errors 

The manually created invoice contains matching errors, which are normally caused by discrepancies during the 2-way or 3-way matching process. The action button “Accept price discrepancy” is visible when it
required to resolve these discrepancies before proceeding with the vendor invoice process, which is controlled by the parameter “Post invoice with discrepancies” under Accounts payable parameters > Invoice 
validation.  

With other errors 

The invoice is generated manually, but it may contain post errors, which require the attention of the accounts payable (AP) clerk to manually correct the invoice details before submitting it for processing 
through the vendor invoice automation system. 

 

Automation 

In process 

This means that invoices are in automation processing and cannot be edited. If some additional changes need to be applied, AP clerks can manually exclude the invoices from automation process by clicking the
button “Exclude from automation”. 

Apply prepayment error 

During the vendor invoice import process, the prepayment application will be triggered if an existing prepayment is identified. An error may occur if the prepayment amount exceeds the invoice amount. In such 
cases, the user will need to manually adjust the prepayment amount before applying for it or skip the prepayment application completely. 

Receipt match error 

The invoices are received prior to the product receipts. However, the invoices are not completely matched with the product receipts, but the receipt matching automation job has reached the maximum trials. The
error will alert the accounts payable (AP) clerk and display a detailed list.  

Workflow submission error 

During invoice submission into the workflow, various validations are applied to ensure the invoice's completeness and accuracy. The detailed list view will column of validation error, which can help AP clerks to
understand which action shall be taken in the next.  

Others 

The invoices that have been included in automation but are temporarily paused due to the need for additional corrections or adjustments without automation-related error. This feature enables the resumption of
automation, allowing the invoices to be included in the process once more. 

Workflow 

In process 

The invoices which are waiting for someone’s approval will be counted. It will show the additional fields to understand the invoices pending for which person’s approval, the pending time, and the due date for 
the approval. There is no batch action.  

Workflow failed 

The invoice was successfully submitted into the workflow, but an error occurred during the process due to additional validations within the workflow. This requires the Accounts Payable (AP) clerk to amend the 
invoice or the settings before resubmitting the invoice into the workflow. 

Workflow rejected 

The invoice has been submitted for approval but was rejected due to specific reasons. The list provides the rejection reason given by the approver for Accounts Payable (AP) clerks' reference, helping them decide
the appropriate action for the next steps. 

For my approvals  

The invoice was submitted for approval within the workflow and is awaiting my review. This process applies specifically to invoices configured with the Vendor Invoice Workflow settings. 

Workflow 

Complete not posted 

The invoice has completed the workflow approval process and is now awaiting final posting. 

 

Documents not invoiced: 

The majority of the functions in this section are inherited from the previous version. The pending vendor invoice will be displayed as the default option in this section. An 'Edit all' button is introduced that
allows users to navigate to the list page for pending vendor invoices. 

