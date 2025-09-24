---
title: Report a production order as finished
description: Learn how to report a production order as finished, including a step-by-step process for reporting finished production orders.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdTableListPage, ProdParmReportFinished, ProdJournalTransProd, ProdSetupReportFinished
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Report a production order as finished

[!include [banner](../../includes/banner.md)]

This procedure shows how to report a production order as finished. This is the sixth procedure out of seven which explains the production order lifecycle.

## Report a production order as finished

1. Go to **Production control** \> **Production orders** \> **All production orders**.
1. Select a production order that has the *Started* status.
1. On the Action Pane, select **Production order**.
1. Select **Report as finished**. On this page, you can confirm the quantity of the finished product to be reported as finished.  
1. Open the **General** tab and make the following settings:
    - **Good quantity** – Enter the quantity of usable items produced.
    - **Error quantity** – Enter the quantity of unusable items produced.
    - **Error cause** – Select the cause of the error for unusable items (for example, *Material*).
    - **End job** – Set as needed.
    - **Accept error** – Set as needed.

1. Select **OK**.

## Verify the Report as finished journal

1. On the Action Pane, select **View**.
1. Select **Reported as finished**.
1. In the list, mark the selected row.
1. In the list, select the link in the selected row.
1. The report as finished journal is posted. If you want to make adjustments to the journal, manually create a new journal where you can make changes.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
