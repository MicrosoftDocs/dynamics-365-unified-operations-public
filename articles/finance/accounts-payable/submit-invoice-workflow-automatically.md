---
title: Submit invoices to the workflow system and match product receipt lines
description: Learn about the process of submitting vendor invoices to the workflow system and automatically matching posted product receipt lines to vendor invoices.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 07/28/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2017-09-08
ms.search.form:  
ms.dyn365.ops.version: 10.0.14
---

# Submit invoices to the workflow system and match product receipt lines

[!include [banner](../includes/banner.md)]

This article explains the process of submitting vendor invoices to the workflow system and automatically matching posted product receipt lines to vendor invoices.

## Submitting imported vendor invoices to the workflow system and matching posted product receipt lines to pending vendor invoice lines

As part of a touchless Accounts payable invoicing process, you can automatically submit an imported invoice to the workflow system. Configure the process of submitting imported invoices to the workflow system on the **Vendor invoice automation** tab of the **Accounts payable parameters** page (**Accounts payable \> Setup \> Accounts payable parameters**). The submit-to-workflow process runs in the background, at a frequency that you specify (either hourly or daily).

When you automatically submit invoices to the workflow system, start with an imported invoice. To ensure that the invoice can be processed from start to finish without manual intervention, include an automated posting task in the workflow configuration. Invoices that are related to purchase orders (POs), and invoices that contain a non-PO procurement category and non-stocked lines, can automatically be submitted to the workflow system. You must manually submit invoices that are manually entered to the workflow system.

The **Submitted by** value in the workflow is the user ID that you enter for the **Submit vendor invoices to workflow** background task on the **Process automation** page. The user with that user ID can recall the invoice from the workflow system as required.

## Matching posted product receipts to invoice lines that have a three-way matching policy

As part of a touchless Accounts payable invoicing process, you can automatically match posted product receipts to invoice lines. You must define a three-way matching policy for this task. This feature is available if you enable the **Vendor invoice automation** feature on the **Feature management** page.

The matching process runs until the matched product receipt quantity equals the invoice quantity. However, if there are multiple product receipts for a single invoice line, you need to run the process multiple times to achieve the full quantity match. You can specify the maximum number of times that the system should try to match product receipts to an invoice line before it concludes that the process failed. The process runs in the background, either hourly or daily.

You can run the automated matching process as part of the process for submitting invoices to the workflow system. Alternatively, you can run it as a stand-alone process. You configure the settings for the match-product-receipts-to-invoice-lines process on the **Vendor invoice automation** tab of the **Accounts payable parameters** page (**Accounts payable \> Setup \> Accounts payable parameters**).

The automated match-to-product-receipt process includes invoice lines that have a three-way matching policy, where the matched receipt quantity is less than the invoice quantity.

To view the **Last match** status for invoices that aren't part of the automated submit-to-workflow process, open the invoice from the **Vendor invoices** page. When you view the invoice, the matching validation information is updated. The **Last match** status can be updated automatically by using the **Validate invoice matching** background task. You can configure the process of automatically updating the **Last match** status on the **Background processes** tab of the **Process automations** page (**System adminstration\> Setup\> Process automations**).

An invoice line is excluded from the automated processing if any of the following conditions are met:

- The **Automated receipt match status** value of the invoice line is **Failed**.
- The invoice is being used.
- The invoice is in the workflow system.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
