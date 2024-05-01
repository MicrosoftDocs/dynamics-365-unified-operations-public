---
title: View vendor invoice automation results 
description: Learn about how to view the status of vendor invoices that are in the automated submit-to-workflow process, including overviews of various statuses.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 10/16/2020
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-09-08
ms.search.form:
ms.dyn365.ops.version: 10.0.14
---

# View vendor invoice automation results

[!include [banner](../includes/banner.md)]

This article explains how to view the status of vendor invoices that are in the automated submit-to-workflow process. Details of the automation history are maintained for each imported vendor invoice. Depending on the business processes that you've automated, the **Pending vendor invoices** page shows **Automated receipt match status** and **Automated submit to workflow status** values. You can view the details and make a plan to focus on the invoices that failed an automated step. Then, after you correct the issue, you can resume the automated process for the imported invoice.

Before you can edit an invoice that has been submitted, you must pause the automated processing. If an invoice in the automated submit-to-workflow process must be paused, set the **Include in Automated processing** field to **No** on the **Vendor invoices** page. Automation then won't run until **Include in Automated processing** is set to **Yes**. An invoice can be paused from further automation if it isn't yet in the workflow system and isn't used by the automated process.

If an imported invoice is subject to the submit-to-workflow process, you can view its **Automation status** value on the **Vendor invoices** page. The following statuses are tracked:

- **Included** – The automated processes that are defined on the **Accounts payable parameters** page are running correctly but haven't yet been completed.
- **Paused** – The automated processes that are defined on the **Accounts payable parameters** page have run, but at least one step in the process failed. The **Paused** status is also applied if the **Include in automated processing** field is set to **No**. You can view the failures by selecting **View most recent results**.
- **In workflow** – The imported invoice has been submitted to the workflow system, either by the automated submit-to-workflow process or manually.
- **Workflow complete** – The workflow process has been completed for the imported invoice.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
