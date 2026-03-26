---
title: Automated vendor invoicing processes overview
description: Learn about the capability for automating your vendor invoice processing and the benefits of using an automated process. 
author: ShielaSogge
ms.author: shpandey
ms.topic: overview
ms.date: 02/10/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-08-30
ms.dyn365.ops.version: 10.0.14
---

# Automated vendor invoicing processes overview

[!include [banner](../includes/banner.md)]

This article describes the capability for automating your vendor invoice processing and the benefits of using an automated process. This capability consists of features that are turned on in Feature management. These features apply only to vendor invoices, not to invoices that are processed by using the **Invoice journal** or **Invoice register journal** page.

Organizations often work with third parties or **Invoice capture** to process paper invoices by using an optical character recognition (OCR) service provider. The service provider returns machine-readable invoice metadata. To help with automation, the Accounts payable automation features let you consume these artifacts from Accounts payable.

You can automate some Accounts payable vendor invoicing processes by using vendor invoice automation. The vendor invoice automation processing includes various tasks that are based on the Accounts payable automation settings. The automated process shows information about the progress of a vendor invoice as it moves through each of the processes. This capability can help Accounts payable clerks and managers process vendor invoices more efficiently. It also helps reduce the errors and inefficiencies that can occur when information is manually entered and processed.

Use the automation processes to perform these tasks:

- Automatically apply prepayments to vendor invoices.
- Match product receipts to pending vendor invoice lines.
- Automatically submit imported invoices to the workflow system.
- Simulate posting before a vendor invoice is posted.
- Quickly and efficiently view workflow and automation history.
- View and analyze the results of automating vendor invoice processing.
- Resume automated processing for multiple invoices.

## Submit vendor invoices to vendor invoice automation

When you enable either the **Automatically submit invoice to workflow** parameter or the **Automatically match product receipts to invoice lines** parameter, the system automatically submits all imported invoices to vendor invoice automation and waits for the automation background job to process them.

You can submit manually created invoices to vendor invoice automation by enabling the **Include in automated processing** option on the invoice header. This option is visible only when one of the automation features is enabled.

You can't edit invoices that are included in automated processing. If you want to edit an invoice, you must first exclude it from automated processing by disabling the **Include in automated processing** option.

## Match product receipts to invoice lines that have a three-way matching policy

You can automatically match posted product receipts to invoice lines when a three-way matching policy exists. The process continues until the matched product receipt quantity equals the invoice quantity. You can set the maximum number of times the system tries to match product receipts to an invoice line before it stops. The process runs in the background, either hourly or daily. To set your own interval, go to **Process automation** \> **Background processes** \> **Match vendor invoice lines with product receipts**, and select **Edit**.

The **Matching product receipt to invoice lines** parameter controls this feature. When you enable this parameter, the **Automated receipt match status** field appears on the **Pending vendor invoice list** page. For invoices imported from external sources, this field's initial value is **Not yet run**.

When you run automatic invoice receipt matching, the status updates based on different conditions:

- **Not applicable** – No three-way matching line is found. The matching policy is defined on the **Setup** tab under the connected purchase line.
- **Complete** – The invoice line's quantity was completely matched against the product receipt line's quantity.
- **Failed** – The matched product receipt line's quantity is less than the invoice line's quantity, and the maximum number of tries is reached.
- **Waiting** – The matched product receipt line's quantity is less than the invoice line's quantity, and the maximum number of tries isn't reached.

## Submit imported vendor invoices to the workflow system

As part of a touchless Accounts payable invoice process, invoices can be automatically submitted to the workflow system. The **Automatically submit invoice to workflow** parameter controls this feature. Only invoices that complete the **Automatically match product receipts to invoice lines** task and are still in automated processing can be automatically submitted to the workflow system. The **Submit vendor invoices to workflow** processing job runs the process in the background. To set the interval, go to **Process automation** \> **Background processes**, select the job, and then select **Edit**.

The **Check Match product receipt status before workflow submission** parameter first checks the **Automated receipt match status** value and determines whether the invoice should be submitted to the workflow system. When you enable the parameter, the invoice is submitted to the workflow system when the **Match product receipt** status is **Complete** or **Not applicable**. When you disable the parameter, the invoice can be submitted to the workflow system even if the **Match product receipt** status is **Failed**.

You must manually submit invoices created by using the **Vendor collaboration invoicing** workspace to the workflow system.

## Automatically apply prepayments

When you enable the **Automatically apply prepayment for imported invoices** parameter, the system automatically applies any existing prepayment when importing the invoice into the vendor invoice. The **Block follow-up automation process in case of prepayment application failure** parameter determines whether the vendor invoice automation processing should continue if prepayment application fails.

## Pre-validate vendor invoice posting

Posting simulation completes the validation steps that are done during the posting process for vendor invoices, but it doesn't update any accounts. To run the process, you can select either a single invoice or multiple invoices on the **Pending vendor invoices** page.

## Enhanced experience for viewing workflow and automation historical information for vendor invoices

You can view vendor invoice workflow history in an easy-to-read format. You can access vendor invoice workflow history directly from the vendor invoice, so you need fewer clicks to find that information. If your organization enables the ability to automatically submit imported vendor invoices to workflow, the automation history is provided for the imported invoices. The automation history helps you identify the current process step, as well as the steps that are already completed. When a step is unsuccessful, the system provides detailed information to help you understand the reason for the failure.

## Analytics and metrics

The **Vendor invoice center** workspace lets you focus on vendor invoices that didn't make it through the automated process. Tiles on the workspace list information about vendor invoices that weren't successfully submitted to the workflow system, imported, or matched to product receipts. Microsoft Power BI metrics are also provided to give Accounts payable managers insight into the efficiencies of vendor invoice automation.

## Resume automation processing for multiple invoices

When an imported invoice isn't successfully submitted to workflow by using the automated process, the system removes it from further automated processing. An accounts payable clerk can review and edit the invoice before the automated process resubmits it to workflow. When a failure reason can be resolved by the same fix for multiple invoices, you can restart the automated process on the **Resume automated invoice processing** page.

## Tracking the Invoice received date value

The **Invoice received date** value indicates the date when the company receives the invoice from the vendor. It provides a starting point for tracking the invoice's progress through the automation processes. You can include this value in the imported data for a vendor invoice. For invoices that you manually create, you can specify the date. If you don't enter a value, the current date is used by default.

## Tracking the Imported invoice amount and Imported sales tax amount values

You can include the **Imported invoice amount** and **Imported sales tax amount** values for vendor invoices in the vendor invoices import file. Typically, these values come from an invoice that an outside provider scanned and included in the import file. As Accounts payable processes the invoice, it calculates these values based on the invoice data. You can post the invoice only if the imported values match the calculated values, unless you opt to override the actual tax amount by using the imported tax amount on the **Vendor invoice automation parameters**. When you select the option to override the actual tax amount by using the imported tax amount, the imported (total) tax amount replaces the actual (total) sales tax amount on the **Sales tax** page. The actual amount automatically allocates to the linked sales tax codes. To configure this option, go to **Accounts Payable Parameters** > **Vendor invoice automation** tab. Expand **Tax import settings** and select **Override actual tax amount with imported tax amount for pending vendor invoice** and **Override actual tax amount with import tax amount for invoice journal**.

> [!NOTE]
> In Dynamics 365 Finance versions 10.0.45 and 10.0.46, a feature in feature management controls the override actual tax by using imported tax functionality. It's not a toggle on the **Account payable parameters** page.
> To enable this functionality, go to feature management and enable the following features:
>
> - Apply the imported sales tax for invoice register and invoice journal
> - Apply the imported sales tax for pending vendor invoice
> In Dynamics 365 Finance version 10.0.47 and later, the feature is available by default. Users must configure the feature in Account payable parameters as listed earlier. However, if the feature was previously enabled in Dynamics 365 Finance versions 10.0.45 and 10.0.46, these toggles are automatically enabled.  

When you turn off these options and enable the workflow, the validation is applied before workflow submission. Matching values ensure that the invoice accurately reflects the amount that's due to the vendor. If your organization allows imported invoices to be submitted to the workflow system automatically, you can optionally require that the imported totals match the calculated totals before the invoice can be submitted to the workflow system. The **Require the calculated totals to equal the imported totals for workflow submission** parameter controls the feature.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
