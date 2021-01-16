---
# required metadata

title: Automated vendor invoicing processes overview
description: This topic describes the capability for automating your vendor invoice processing and the benefits of using an automated process. 
author: abruer
manager: AnnBe
ms.date: 11/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-08-30
ms.dyn365.ops.version: 10.0.14

---

# Automated vendor invoicing processes overview

[!include [banner](../includes/banner.md)]

This topic describes the capability for automating your vendor invoice processing and the benefits of using an automated process. This capability consists of features that are turned on in Feature management. These features apply only to vendor invoices, not to invoices that are processed through the **Invoice journal** or **Invoice register journal** page.

Organizations often work with third parties to process paper invoices by using an optical character recognition (OCR) service provider. The service provider returns machine-readable invoice metadata. To help with automation, the Accounts payable automation features let you consume these artifacts from Accounts payable.

You can automate some Accounts payable vendor invoicing processes. These processes include submitting imported vendor invoices to the workflow system and matching posted product receipt lines to pending vendor invoice lines. The automated process shows information about the progress of a vendor invoice as it moves through each of the processes. This capability can help Accounts payable clerks and managers process vendor invoices more efficiently. It also helps reduce the errors and inefficiencies that can occur when information is manually entered and processed.

The automation processes can be used to perform these tasks:

- Automatically submit imported invoices to the workflow system.
- Match product receipts to pending vendor invoice lines.
- Simulate posting before a vendor invoice is posted.
- Quickly and efficiently view workflow and automation history.
- View and analyze the results of automating vendor invoice processing.
- Resume automated processing for multiple invoices.

## Vendor invoice automation – Submit imported vendor invoices to the workflow system

As part of a touchless Accounts payable invoicing process, you can have the system automatically submit an imported invoice to the workflow system. The process will run in the background, at a frequency that you specify (either hourly or daily). The capability to automatically submit imported invoices to the workflow system requires that your process begin with an imported invoice. To ensure that the invoice can be processed from start to finish without manual intervention, an automated posting task must be included in the workflow configuration.

'Invoices that are related to purchase orders (POs), and invoices that contain a non-PO procurement category and non-stocked lines, can automatically be submitted to the workflow system. Invoices that are manually entered and invoices that are created via the **Vendor collaboration invoicing** workspace must be manually submitted to the workflow system.

The automation feature provides a flexible framework that lets you define company-specific rules for submitting imported vendor invoices to the workflow system and matching posted product receipt lines to pending vendor invoice lines.

## Vendor invoice automation – Match product receipts to invoice lines that have a three-way matching policy

The system can automatically match posted product receipts to invoice lines that a three-way matching policy is defined for. The process will run until the matched product receipt quantity equals the invoice quantity. As part of this process, you can specify the maximum number of times that the system should try to match product receipts to an invoice line before it concludes that the process failed. The process will run in the background, either hourly or daily. You can run the automated matching process as part of the process for submitting invoices to the workflow system. Alternatively, you can run it as a standalone process.

## Vendor invoice automation – Pre-validate vendor invoice posting

Posting simulation completes the validation steps that are done during the posting process for vendor invoices, but no accounts are updated. To run the process, you can select either a single invoice or multiple invoices on the **Pending vendor invoices** page.

## Vendor invoice automation – Enhanced experience for viewing workflow and automation historical information for vendor invoices

An easy-to-read view of vendor invoice workflow history is provided. Vendor invoice workflow history can be accessed directly from the vendor invoice. Therefore, fewer clicks are required to find that information. If your organization has enabled the ability to automatically submit imported vendor invoices to workflow, the automation history is provided for the imported invoices. The automation history helps you identify the current process step, as well as the steps that have already been completed. When a step is unsuccessful, the system provides detailed information to help you understand the reason for the failure.

## Vendor invoice automation – Analytics and metrics

The **Vendor invoice entry** workspace lets you focus on vendor invoices that didn't make it through the automated process. Tiles on the workspace list information about vendor invoices that weren't successfully submitted to the workflow system, imported, or matched to product receipts. Microsoft Power BI metrics are also provided to give Accounts payable managers insight into the efficiencies of vendor invoice automation.

## Vendor invoice automation - Resume automation processing for multiple invoices
When an imported invoice isn’t submitted successfully to workflow through the automated process, the system will remove it from further automated processing. An accounts payable clerk can review and edit the invoice before the automated process resubmits it to workflow. When a failure reason can be resolved by the same fix for multiple invoices, you can restart the automated process on the **Resume automated invoice processing** page. 
