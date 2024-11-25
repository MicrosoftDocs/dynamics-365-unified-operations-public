---
title: Submit invoices to the workflow system and match product receipt lines
description: Learn about the process of submitting vendor invoices to the workflow system and automatically matching posted product receipt lines to vendor invoices.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 02/11/2022
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

As part of a touchless Accounts payable invoicing process, an imported invoice can be automatically submitted to the workflow system. You can configure the process of submitting imported invoices to the workflow system on the **Vendor invoice automation** tab of the **Accounts payable parameters** page (**Accounts payable \> Setup \> Accounts payable parameters**). The submit-to-workflow process will run in the background, at a frequency that you specify (either hourly or daily).

When you automatically submit invoices to the workflow system, you must begin with an imported invoice. To ensure that the invoice can be processed from start to finish without manual intervention, you must include an automated posting task in the workflow configuration. Invoices that are related to purchase orders (POs), and invoices that contain a non-PO procurement category and non-stocked lines, can automatically be submitted to the workflow system. Invoices that are manually entered must be manually submitted to the workflow system.

The **Submitted by** value in the workflow is the user ID that was entered for the **Submit vendor invoices to workflow** background task on the **Process automation** page. The user who has that user ID will be able to recall the invoice from the workflow system as required.

## Matching posted product receipts to invoice lines that have a three-way matching policy

As part of a touchless Accounts payable invoicing process, posted product receipts can be automatically matched to invoice lines. A three-way matching policy must be defined for this task. This feature is available if the **Vendor invoice automation** feature has been enabled on the **Feature management** page.

The matching process will run until the matched product receipt quantity equals the invoice quantity. However, if there are multiple product receipts for a single invoice line, you’ll need to run the process multiple times to achieve the full quantity match. You can specify the maximum number of times that the system should try to match product receipts to an invoice line before it concludes that the process failed. The process will run in the background, either hourly or daily. 

You can run the automated matching process as part of the process for submitting invoices to the workflow system. Alternatively, you can run it as a stand-alone process. The settings for the match-product-receipts-to-invoice-lines process are configured on the **Vendor invoice automation** tab of the **Accounts payable parameters** page (**Accounts payable \> Setup \> Accounts payable parameters**).

Invoice lines that have a three-way matching policy, where the matched receipt quantity is less than the invoice quantity, will be included in the automated match-to-product-receipt process.

To view the **Last match** status for invoices that aren't part of the automated submit-to-workflow process, open the invoice from the **Vendor invoices** page. When you view the invoice, the matching validation information is updated. The **Last match** status can be updated automatically using the **Validate invoice matching** background task. You can configure the process of automatically updating the **Last match** status on the **Background processes** tab of the **Process automations** page (**System adminstration\> Setup\> Process automations**).

An invoice line will be excluded from the automated processing if any of the following conditions are met:

- The **Automated receipt match status** value of the invoice line is **Failed**.
- The invoice is being used.
- The invoice is in the workflow system.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
