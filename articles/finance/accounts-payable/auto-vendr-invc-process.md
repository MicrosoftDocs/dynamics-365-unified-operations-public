---
# required metadata

title: Automated vendor invoicing processes overview
description: This article describes the capability for automating your vendor invoice processing and the benefits of using an automated process. 
author: abruer
ms.date: 02/12/2021
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-08-30
ms.dyn365.ops.version: 10.0.14

---

# Automated vendor invoicing processes overview

[!include [banner](../includes/banner.md)]

This article describes the capability for automating your vendor invoice processing and the benefits of using an automated process. This capability consists of features that are turned on in Feature management. These features apply only to vendor invoices, not to invoices that are processed using the **Invoice journal** or **Invoice register journal** page.

Organizations often work with third parties to process paper invoices by using an optical character recognition (OCR) service provider. The service provider returns machine-readable invoice metadata. To help with automation, the Accounts payable automation features let you consume these artifacts from Accounts payable.

You can automate some Accounts payable vendor invoicing processes. These processes include submitting imported vendor invoices to the workflow system and matching posted product receipt lines to pending vendor invoice lines. The automated process shows information about the progress of a vendor invoice as it moves through each of the processes. This capability can help Accounts payable clerks and managers process vendor invoices more efficiently. It also helps reduce the errors and inefficiencies that can occur when information is manually entered and processed.

The automation processes can be used to perform these tasks:

- Automatically apply prepayments to vendor invoices
- Automatically submit imported invoices to the workflow system.
- Match product receipts to pending vendor invoice lines.
- Simulate posting before a vendor invoice is posted.
- Quickly and efficiently view workflow and automation history.
- View and analyze the results of automating vendor invoice processing.
- Resume automated processing for multiple invoices.

## Submit imported vendor invoices to the workflow system

As part of a touchless Accounts payable invoicing process, an imported invoice can automatically be submitted to the workflow system. The process will run in the background, at a frequency that you specify (either hourly or daily). The capability to automatically submit imported invoices to the workflow system requires that your process begin with an imported invoice. To ensure that the invoice can be processed from start to finish without manual intervention, an automated posting task must be included in the workflow configuration.


Invoices that are related to purchase orders (POs), and invoices that contain a non-PO procurement category and non-stocked lines, can automatically be submitted to the workflow system. Invoices that are manually entered and invoices that are created using the **Vendor collaboration invoicing** workspace must be manually submitted to the workflow system. Prepayment application processing must be performed manually for imported invoices. You can manually apply prepayments before or after posting the imported invoice. You can manually apply prepayments to unposted standard invoices using the **Vendor invoices** page. After posting, the settled prepayment will be available to manually apply to other invoices from this vendor on the **Vendors** page (**Accounts payable \> Common \> Vendors \> All vendors \> Invoice tab \> Apply**).

The automation feature provides a flexible framework that lets you define company-specific rules for submitting imported vendor invoices to the workflow system and matching posted product receipt lines to pending vendor invoice lines.

## Match product receipts to invoice lines that have a three-way matching policy

Posted product receipts can be automatically matched to invoice lines that a three-way matching policy is defined for. The process will run until the matched product receipt quantity equals the invoice quantity. As part of this process, you can specify the maximum number of times that the system should try to match product receipts to an invoice line before it concludes that the process failed. The process will run in the background, either hourly or daily. You can run the automated matching process as part of the process for submitting invoices to the workflow system. Alternatively, you can run it as a standalone process.

## Pre-validate vendor invoice posting

Posting simulation completes the validation steps that are done during the posting process for vendor invoices, but no accounts are updated. To run the process, you can select either a single invoice or multiple invoices on the **Pending vendor invoices** page.

## Enhanced experience for viewing workflow and automation historical information for vendor invoices

An easy-to-read view of vendor invoice workflow history is provided. Vendor invoice workflow history can be accessed directly from the vendor invoice. Therefore, fewer clicks are required to find that information. If your organization has enabled the ability to automatically submit imported vendor invoices to workflow, the automation history is provided for the imported invoices. The automation history helps you identify the current process step, as well as the steps that have already been completed. When a step is unsuccessful, detailed information will be provided to help you understand the reason for the failure.

## Analytics and metrics

The **Vendor invoice entry** workspace lets you focus on vendor invoices that didn't make it through the automated process. Tiles on the workspace list information about vendor invoices that weren't successfully submitted to the workflow system, imported, or matched to product receipts. Microsoft Power BI metrics are also provided to give Accounts payable managers insight into the efficiencies of vendor invoice automation.


## Resume automation processing for multiple invoices

When an imported invoice isn't successfully submitted to workflow using the automated process, the system will remove it from further automated processing. An accounts payable clerk can review and edit the invoice before the automated process resubmits it to workflow. When a failure reason can be resolved by the same fix for multiple invoices, you can restart the automated process on the **Resume automated invoice processing** page. 

## Tracking the Invoice received date value

The **Invoice received date** value indicates the date when the company received the invoice from the vendor. It provides a starting point for tracking the invoice's progress through the automation processes. This value can be included in the imported data for a vendor invoice. For invoices that were manually created, you can specify the date. If no value is entered, the current date is used by default.


## Tracking the Imported invoice amount and Imported sales tax amount values

The **Imported invoice amount** and **Imported sales tax amount** values for vendor invoices can be provided in the vendor invoices import file. Typically, these values are from an invoice that was scanned by an outside provider and included in the import file. As the invoice is processed in Accounts payable, the values will be calculated based on the invoice data. The invoice can be posted only if the imported values match the calculated values. Matching values ensure that the invoice accurately reflects the amount that is due to the vendor. If your organization allows imported invoices to be submitted to the workflow system automatically, you can optionally require that the imported totals match the calculated totals before the invoice can be submitted to the workflow system.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
