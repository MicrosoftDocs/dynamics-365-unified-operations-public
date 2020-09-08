---
# required metadata

title: Submit invoice to workflow; match product receipt lines
description: This topic explains the process of submitting vendor invoices to workflow and posted product receipt lines are matched to vendor invoices automatically.
author: abruer
manager: AnnBe
ms.date: 09/08/2020
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
ms.search.validFrom: 2017-09-08
ms.dyn365.ops.version: 10.0.14

---

# Submit invoice to workflow; match product receipt lines
This topic explains the process of submitting vendor invoices to workflow and automatically matching posted product receipt lines to vendor invoices.  
[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

## Submitting imported vendor invoices to workflow and matching posted product receipt lines to pending vendor invoice lines 
As part of a touchless accounts payable invoicing process, you can choose to have the system automatically submit an imported invoice to workflow. You can configure the process of submitting imported invoices to workflow on the **Vendor invoice automation** tab of the **Accounts payable parameters** page (**Accounts payable > Setup > Accounts payable parameters**).  The submit-to-workflow process will run as a background process, using a frequency that you can specify as hourly or daily. 

You must begin with an imported invoice when automatically submitting imported invoices to workflow. To ensure that the invoice can be processed straight-through, without manual intervention, you must include an automated posting task in the workflow configuration. Invoices that are related to purchase orders and invoices that contain a non-PO procurement category, and non-stocked lines, can be submitted to workflow automatically. Invoices that are entered manually must be submitted to workflow manually.

The **Submitted by** value in workflow is the user ID that was entered on the Submit vendor invoices to workflow background task on the **Process automation** page. This user will be able to recall the invoice from workflow, if necessary.

## Matching posted product receipts to invoice lines that have a three-way matching policy
As part of a touchless accounts payable invoicing process, the system can automatically match posted product receipts to invoice lines. A three-way matching policy must be defined for this task. This feature is available if the **Automate vendor invoices** parameter on the **Feature management** page is enabled. 

The process will run until the matched product receipt quantity is equal to the invoice quantity. As part of this process, you can indicate the maximum number of times the system should try to match product receipts to an invoice line before concluding that the process failed. The process will run in the background, using a frequency of either hourly or daily. You can run the automated matching process as part of the process for submitting invoices to workflow, or as a stand-alone process. The settings for the Match product receipts to invoice lines process are configured on the **Vendor invoice automation** tab of the **Accounts payable parameters** page (**Accounts payable > Setup > Accounts payable parameters**).

Invoice lines that have a matching policy of three-way matching, where the matched receipt quantity is not equal to, or is greater than, the invoice quantity, will be included in the Match-to-product-receipt automated process. 

To view the **Last match** status for invoices that are not part of the Automatic-submit-to-workflow process, open the invoice from the **Vendor invoices** page. Viewing the invoice will update the matching validation information.

The following conditions will exclude an invoice line from the automated processing:

- Invoice lines whose **Automated receipt match status** is **Failed** are not included 
- Invoices that are in use are not included 
- Invoices that are in workflow are not included
