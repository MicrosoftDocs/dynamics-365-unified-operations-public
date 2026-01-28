---
title: Set up, create, and manage absorption costs
description: This article describes how to set up, create, and manage absorption costs for Brazil with Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
---

# Set up, create, and manage absorption costs 

[!include [banner](../../includes/banner.md)]

This article describes how to set up, create, and manage absorption costs for Brazil with Microsoft Dynamics 365 Finance.

You can calculate and post the direct and indirect costs that are incurred in the production orders for a fiscal period. The final manufacturing costs are registered in the ledger at the end of the fiscal period. You can calculate the absorption costs by allocating the total manufacturing costs to the products that are manufactured during a fiscal period.

## Set up a number sequence for absorption costs

To set up the number sequence code for cost absorption journals, follow these steps:

1. In Dynamics 365 Finance, go to **Production control** \> **Setup** \> **Absorption costs** \> **Parameters**.
1. In the **Number sequence code** field, select the number sequence code to use for the cost absorption journal.

## Set up a cost center for absorption costs

You can use the **Cost center** page to set up cost centers for absorption costs. 

To set up a cost type for a cost center, follow these steps:

1. In Dynamics 365 Finance, go to **Production control** \> **Setup** \> **Absorption costs** \> **Cost centers**.
1. Select the cost center to use to post absorption costs.
1. In the **Cost type** field, select the type of cost for the cost center.

## Set up journal names for absorption costs

To set up journal names for absorption costs, follow these steps:

1. In Dynamics 365 Finance, go to **Production control** \> **Setup** \> **Absorption costs** \> **Journal names**.
1. Select Ctrl+N to create a record.
1. In the **Name** field, enter a name for the journal.  

    > [!NOTE]
    > The **Journal type** field is updated with the default journal type that is used for absorption costs. The default journal type is "Indirect costs".

1. In the **Description** field, enter a brief description for the journal.
1. In the **Voucher series** field, select the number sequence code to use for the journal.
1. In the **Selection by** field, indicate if a new voucher is selected either during entry or after posting.
1. In the **Detail level** field, select the method to use to summarize the details of the journal.

## Create the cost absorption journal

To create and post a cost absorption journal, follow these steps:

1. In Dynamics 365 Finance, go to **Production control** \> **Periodic** \> **Absorption costs** \> **Cost absorption journal**.
1. Select Ctrl+N to create a journal.
1. On the **Overview** tab, in the **Name** field, select the name of the cost absorption journal.
1. In the **Month/Year to close** field, select the month and year that the costs are posted for.
1. Select **Lines** to open the **Journal lines** page, and then enter values in the following fields:   
      - **Date** – The date on which to post the journal line.
      - **Ledger account** – The ledger account number for which to post the journal line.
      - **Cost center** – The cost center number to use to post the journal line.
      - **Cost amount** – The cost amount for the journal line.
1. Select **Post** \> **OK** to post the journal line.

> [!NOTE]
> On the **Absorbed costs** page, you can view the type of absorbed cost that is posted to a work center, the corresponding cost center that the work center is associated with, the hourly rate, and the planned capacity for the work center details.

## Close absorption costs

You can post the absorption costs for a specific month and year to the ledger. You can specify the transfer account and transfer offset account in the **Accounts - WIP** and **Accounts - costing** fields on the **Resources** page. 

To close absorption costs, follow these steps:

1. In Dynamics 365 Finance, go to **Production control** \> **Periodic** \> **Absorption costs** \> **Absorption costs - monthly closing**.
1. In the **Month/Year to close** field, select the month and year for which to post the absorbed costs.
1. Select **OK** to post the absorption costs for the selected month and year.

## Cancel absorbed costs

You can't cancel the absorbed costs after the monthly closing is completed.

To cancel the absorbed costs that are not posted to the ledger for a specific month and year, follow these steps:

1. In Dynamics 365 Finance, go to **Production control** \> **Periodic** \> **Absorption costs** \> **Absorbed costs cancellation**.
1. In the **Month/Year to cancel** field, select the month and year for which to cancel the absorbed costs.
1. Select **OK** to cancel the absorbed costs for the selected month and year.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
