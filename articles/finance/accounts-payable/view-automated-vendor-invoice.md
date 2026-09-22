---
title: View vendor invoice automation results 
description: Learn about how to view the status of vendor invoices that are in the automated submit-to-workflow process, including overviews of various statuses.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 08/20/2026
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-09-08
ms.search.form:
ms.dyn365.ops.version: 10.0.14
---

# View vendor invoice automation results

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to view the status of vendor invoices that are in the automated submit-to-workflow process. Each imported vendor invoice has a detailed automation history. Depending on the business processes that you automated, the **Pending vendor invoices** page shows **Automated receipt match status** and **Automated submit to workflow status** values. You can view the details and focus on the invoices that failed an automated step. After you correct the issue, you can resume the automated process for the imported invoice.

Before you can edit an invoice that you submitted, pause the automated processing. If an invoice in the automated submit-to-workflow process must be paused, set the **Include in Automated processing** field to **No** on the **Vendor invoices** page. Automation doesn't run until you set **Include in Automated processing** to **Yes**. You can pause an invoice from further automation if it isn't yet in the workflow system and the automated process doesn't use it.

If an imported invoice is subject to the submit-to-workflow process, you can view its **Automation status** value on the **Vendor invoices** page. The system tracks the following statuses:

- **Included** – The automated processes that you define on the **Accounts payable parameters** page are running correctly but didn't complete yet.
- **Paused** – The automated processes that you define on the **Accounts payable parameters** page ran, but at least one step in the process failed. The system also applies the **Paused** status if you set the **Include in automated processing** field to **No**. Select **View most recent results** to view the failures.
- **In workflow** – The imported invoice is submitted to the workflow system by the automated submit-to-workflow process or manually.
- **Workflow complete** – The workflow process is complete for the imported invoice.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
