---
title: Automated vendor invoicing processes overview
description: Learn about the capability for automating your vendor invoice processing and the benefits of using an automated process. 
author: twheeloc
ms.author: shpandey
ms.topic: overview
ms.date: 04/29/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-08-30
ms.dyn365.ops.version: 10.0.14
---

# Automated vendor invoicing processes overview

[!include [banner](../includes/banner.md)]

This article describes the capability for automating your vendor invoice processing and the benefits of using an automated process. This capability consists of features that are turned on in Feature management. These features apply **only to vendor invoices**, not to invoices that are processed using the **Invoice journal** or **Invoice register journal** page.

Organizations often work with third parties or **Invoice capture** to process paper invoices by using an optical character recognition (OCR) service provider. The service provider returns machine-readable invoice metadata. To help with automation, the Accounts payable automation features let you consume these artifacts from Accounts payable.

You can automate some Accounts Payable vendor invoicing processes by using vendor invoice automation. The vendor invoice automation processing includes various tasks based on the Accounts Payable automation settings. The automated process shows information about the progress of a vendor invoice as it moves through each of the processes. This capability can help Accounts Payable clerks and managers process vendor invoices more efficiently. It also helps reduce the errors and inefficiencies that can occur when information is manually entered and processed.

The automation processes can be used to perform these tasks:

- Automatically apply prepayments to vendor invoices
- Match product receipts to pending vendor invoice lines.
- Automatically submit imported invoices to the workflow system.
- Simulate posting before a vendor invoice is posted.
- Quickly and efficiently view workflow and automation history.
- View and analyze the results of automating vendor invoice processing.
- Resume automated processing for multiple invoices.

## Submit vendor invoices to vendor invoice automation

When one of the parameters **"Automatically submit invoice to workflow"** and **"Automatically match product receipts to invoice lines"** under Accounts payable parameters >> Vendor invoice automation is enabled, all the imported invoice will be automacially submitted into vendor invoice automation and will wait for the automation background job to process them. For manually created invoices, you can submit them into vendor invoice automation by enabling the toggle **"Include in automated processing"** on the invoice header. The toggle is only visible when one the automation features is enabled. All invoices included in automated processing are not editable. If you want to edit the invoice, you need to exclude the invoice from automated processing by disabling the toggle **"Include in automated processing"**.

## Match product receipts to invoice lines that have a three-way matching policy

Posted product receipts can be automatically matched to invoice lines that a three-way matching policy is defined for. The process will run until the matched product receipt quantity equals the invoice quantity. As part of this process, you can specify the maximum number of times that the system should try to match product receipts to an invoice line before it concludes that the process failed. The process will run in the background, either hourly or daily. You can define your own repeats interval **Process automation >> Choose "Background processes"" >> Select "Match vendor invoice lines with product receipts" and click button "Edit"**.

The feature is controlled by the parameter "Matching product receipt to invoice lines". When it is enabled, the field "Automated receipt match status" will be displayed in the pending vendor invoice list form. The initial value will be set to "Not yet run" for invoices imported from external sources. When automatic invoice receipt matching is executed, the status will be updated based on different conditions:

- **Not applicable**: No 3-way matching line is found. The matching policy is defined in "Setup" tab under the connected purchase line.
- **Complete**: The invoice line's quantity has completely matched against the product receipt line's quantity.
- **Failed**: The matched product receipt line's quantity is less than the invoice line's quantity and the maximum trial has been reached.
- **Waiting**: The matched product receipt line's quantity is less than the invoice line's quantity and the maximum trial hasn't yet been reached.

## Submit imported vendor invoices to the workflow system

As part of a touchless Accounts payable invoice process, the invoice shall be able to be automatically submitted to the workflow. The feature is controlled by the parameter **"Automatically submit invoice to workflow"** is enabled. The capability to automatically submit the invoices to the workflow system requires that the invoice has completed the task **"Automatically match product receipts to invoice lines"** and still in auotmated processing. The process runs in the background by the processing job **"Submit vendor invoices to workflow"**. You can define your own repeats interval under Process automation >> Choose "Background processes"" >> Select the job and click button "Edit". 

The parameter **Check Match product receipt status before workflow submission** is designated to check the value **""Automated receipt match status"** first and then to decide whether or not to allow the invoice to be submitted to workflow. When it is enabled, the invoice can be submitted into workflow when the status of "Match product receipt" is "Complete" or "Not applicable". When it is OFF, the invoice can be submitted into workflow even if the "Match product receipt" is "Failed". 

The invoices that are created using the **Vendor collaboration invoicing** workspace must be manually submitted to the workflow system. 

## Automatically apply prepayment application

When the parameter **"Automatically apply prepayment for imported invoices"** is enabled, the prepayment is automatically applied at the time the invoice is imported into the vendor invoice when it exists. The parameter **"Block follow-up automation process in case of prepayment application failure"** determines whether the vendor invoice automation processing should continue if the prepayment application fails.

## Pre-validate vendor invoice posting

Posting simulation completes the validation steps that are done during the posting process for vendor invoices, but no accounts are updated. To run the process, you can select either a single invoice or multiple invoices on the **Pending vendor invoices** page.

## Enhanced experience for viewing workflow and automation historical information for vendor invoices

An easy-to-read view of vendor invoice workflow history is provided. Vendor invoice workflow history can be accessed directly from the vendor invoice. Therefore, fewer clicks are required to find that information. If your organization has enabled the ability to automatically submit imported vendor invoices to workflow, the automation history is provided for the imported invoices. The automation history helps you identify the current process step, as well as the steps that have already been completed. When a step is unsuccessful, detailed information will be provided to help you understand the reason for the failure.

## Analytics and metrics

The **Vendor invoice center** workspace lets you focus on vendor invoices that didn't make it through the automated process. Tiles on the workspace list information about vendor invoices that weren't successfully submitted to the workflow system, imported, or matched to product receipts. Microsoft Power BI metrics are also provided to give Accounts payable managers insight into the efficiencies of vendor invoice automation.


## Resume automation processing for multiple invoices

When an imported invoice isn't successfully submitted to workflow using the automated process, the system will remove it from further automated processing. An accounts payable clerk can review and edit the invoice before the automated process resubmits it to workflow. When a failure reason can be resolved by the same fix for multiple invoices, you can restart the automated process on the **Resume automated invoice processing** page. 

## Tracking the Invoice received date value

The **Invoice received date** value indicates the date when the company received the invoice from the vendor. It provides a starting point for tracking the invoice's progress through the automation processes. This value can be included in the imported data for a vendor invoice. For invoices that were manually created, you can specify the date. If no value is entered, the current date is used by default.

## Tracking the Imported invoice amount and Imported sales tax amount values

The **Imported invoice amount** and **Imported sales tax amount** values for vendor invoices can be provided in the vendor invoices import file. Typically, these values are from an invoice that was scanned by an outside provider and included in the import file. As the invoice is processed in Accounts payable, the values will be calculated based on the invoice data. The invoice can be posted only if the imported values match the calculated values. When the workflow is enabled, it will apply the validation before the workflow submission. Matching values ensure that the invoice accurately reflects the amount that is due to the vendor. If your organization allows imported invoices to be submitted to the workflow system automatically, you can optionally require that the imported totals match the calculated totals before the invoice can be submitted to the workflow system. The feature is controlled by the parameter **"Require the calculated totals to equal the imported totals for workflow submission"**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
