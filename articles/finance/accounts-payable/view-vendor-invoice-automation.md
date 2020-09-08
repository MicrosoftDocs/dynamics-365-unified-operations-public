---
# required metadata

title: Vendor payments workspace
description: This topic provides information about the Vendor payments workspace. The Vendor payments workspace shows information that is related to the processing of vendor payments.
author: abruer
manager: AnnBe
ms.date: 07/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  VendPaymentWorkspace
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
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: July 2017 update

---

# View vendor invoice automation results
 
[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic explains how to view the status of vendor invoices that are in the automated submit-to-workflow process. The details of the automation history are maintained for each imported vendor invoice. The **Automated receipt match status** and the **Automated submit to workflow status** will be displayed on the **Pending vendor invoices** page, depending on which business processes you have chosen to automate.  You can view the details and make a plan to focus on the invoices that failed an automated step. After correcting the issue, the imported invoice can be placed back into the automated process. 

In order to edit an invoice, you must pause it from the automated processing. If an invoice needs to be paused from the submit-to-workflow automation process, unmark the **Include in Automated processing** setting on the **Vendor invoices** page. This will keep automation from running, until you mark the **Include in Automated processing** setting. An invoice can be paused from further automation when it’s not yet in workflow, and isn’t in use by an automated process.

You can view the **Automation status** on the **Vendor invoices** page for an imported invoice that’s subject to the submit-to-workflow process. The following statuses are tracked:

- **Included** – The automated processes are running properly and have not reached completion, based on the configuration that’s defined on the **Accounts payable parameters** page.
- **Paused** – The automated processes defined in the **Accounts payable parameters** page have run, but at least on of the steps in the process failed, or the **Include in automated processing** setting was cleared. You can view the failures by selecting the **View most recent results** button.
- **In workflow** – The imported invoice has been submitted to workflow, either by the submit-to-workflow automated process, or manually. 
- **Workflow complete** – The workflow process has been completed for the imported invoice.

