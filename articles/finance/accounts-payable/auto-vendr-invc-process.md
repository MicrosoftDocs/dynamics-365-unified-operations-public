---
# required metadata

title: Vendor payments workspace
description: Accounts payable vendor invoicing processes, such as submitting imported vendor invoices to workflow and matching posted product receipt lines to pending vendor invoice lines can be automated. 
author: abruer
manager: AnnBe
ms.date: 08/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations
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
[!include [preview banner](../includes/preview-banner.md)]

Automating vendor invoices processes helps accounts payable clerks and managers process vendor invoices more efficiently, while reducing the errors and inefficiencies that arise when information is entered and processed manually. Automated vendor invoices comprises a set of features that are be enabled through Feature management. The feature set applies to Vendor invoices; not invoices that are processed through the **Invoice journal** or **Invoice register journal** pages.

Organizations often work with third-parties to process paper invoices using an optical character recognition (OCR) service provider. The service providers return receive machine-readable invoice metadata. To help with automation, the Accounts payable automation features let you consume these artifacts from within Accounts payable.

Accounts payable vendor invoicing processes, such as submitting imported vendor invoices to workflow and matching posted product receipt lines to pending vendor invoice lines can be automated. The functionality displays information about the progress of a vendor invoice as it moves through each of the processes. Enabling the feature helps accounts payable clerks and managers process vendor invoices more efficiently, while reducing the errors and inefficiencies that arise when information is entered and processed manually. 

The automation processes can be used to perform these tasks:
-	Submit imported invoices to workflow automatically
-	Match product receipts to pending vendor invoice lines
-	Simulate posting prior to posting a vendor invoice
-	View workflow history in an efficient, speedy manner
-	View and analyze the results of automating your vendor invoice processing

## Vendor invoice automation – Submit imported vendor invoices to workflow

As part of a touchless accounts payable invoicing process, you can choose to have the system automatically submit an imported invoice to workflow. The submit-to-workflow process will run as a background process, using a frequency that you can specify, either hourly or daily. The ability to automatically submit imported invoices to workflow requires that your process begins with an imported invoice. To ensure that the invoice can be processed straight-through, without manual intervention, an automated posting task must be included in the workflow configuration. Invoices that are related to purchase orders and invoices that contain non-PO procurement category, and non-stocked lines, can be submitted to workflow automatically. Manually entered invoices and invoices created via the **Vendor collaboration invoicing** workspace must be manually submitted to workflow.
The automation feature provides a flexible framework that lets you define company-specific rules for submitting imported vendor invoices to workflow and matching posted product receipt lines to pending vendor invoice lines.

## Vendor invoice automation – Match product receipts to invoice lines that have a three-way matching policy
The system can automatically match posted product receipts to invoice lines that a three-way matching policy has been defined for. The process will run until the matched product receipt quantity is equal to the invoice quantity.  As part of this process, you can indicate the maximum number of times the system should try to match product receipts to an invoice line before concluding that the process failed. The process will run in the background, using a frequency of either hourly or daily. You can run the automated matching process as part of the process for submitting invoices to workflow, or as a stand-alone process.

## Vendor invoice automation – Pre-validate vendor invoice posting
Simulation of posting completes the validation steps that are done during the posting process for vendor invoices, without updating any accounts. You can select a single invoice or multiple invoices on the **Pending vendor invoices** page to run the process.  

## Vendor invoice automation – Enhanced workflow historical information experience for vendor invoices
An easy-to-read view of vendor invoice workflow history is provided. Vendor invoice workflow history can be accessed directly from the vendor invoice, reducing the number of clicks that are needed to find that information. 

## Vendor invoice automation – Analytics and metrics
The Vendor invoice entry workspace lets you focus on vendor invoices that didn’t make it through the automated process. Tiles on the workspace list information about vendor invoices that weren’t successfully submitted to workflow, imported, or matched to product receipts. PowerBI metrics are also provided to give accounts payable managers insight into the efficiencies of vendor invoice automation. 

