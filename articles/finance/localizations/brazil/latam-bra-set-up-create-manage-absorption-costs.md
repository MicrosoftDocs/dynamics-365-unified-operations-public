---
title: Set up, create, and manage absorption costs
description: Learn how to set up, create, and manage absorption costs for Brazil, including overviews for setting up a number sequence for absorption costs and cost centers.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/10/2024
ms.reviewer: johnmichalak
ms.search.region: Brazil
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
---

# Set up, create, and manage absorption costs 

[!include [banner](../../includes/banner.md)]

You can calculate and post the direct and indirect costs that are incurred in the production orders for a fiscal period. The final manufacturing costs are registered in the ledger at the end of the fiscal period. You can calculate the absorption costs by allocating the total manufacturing costs to the products that are manufactured during a fiscal period.

## Set up a number sequence for absorption costs

Use this procedure to set up the number sequence code for cost absorption journals.

1.  Click **Production control** \> **Setup** \> **Absorption costs** \> **Parameters**.

2.  In the **Number sequence code** field, select the number sequence code to use for the cost absorption journal.

## Set up a cost center for absorption costs

Use this procedure to set up a cost type for a cost center. You can use the **Cost center** page to set up cost centers for absorption costs. 

1.  Click **Production control** \> **Setup** \> **Absorption costs** \> **Cost centers**.

2.  Select the cost center to use to post absorption costs.

3.  In the **Cost type** field, select the type of cost for the cost center.

## Set up journal names for absorption costs

Use this procedure to set up journal names for absorption costs.

1.  Click **Production control** \> **Setup** \> **Absorption costs** \> **Journal names**.

2.  Press CTRL+N to create a record.

3.  In the **Name** field, enter a name for the journal.  

    > [!NOTE]
    > The <STRONG>Journal type</STRONG> field is updated with the default journal type that is used for absorption costs. The default journal type is <STRONG>Indirect costs</STRONG>.

4.  In the **Description** field, enter a brief description for the journal.

5.  In the **Voucher series** field, select the number sequence code to use for the journal.

6.  In the **Selection by** field, indicate whether a new voucher is selected during entry or after posting.

7.  In the **Detail level** field, select the method to use to summarize the details of the journal.

## Create the cost absorption journal

Use this procedure to create and post a cost absorption journal.

1.  Click **Production control** \> **Periodic** \> **Absorption costs** \> **Cost absorption journal**.

2.  Press CTRL+N to create a journal.

3.  On the **Overview** tab, in the **Name** field, select the name of the cost absorption journal.

4.  In the **Month/Year to close** field, select the month and year that the costs are posted for.

5.  Click **Lines** to open the **Journal lines** page, and then specify values in the following fields:
    
      - **Date** – The date on which to post the journal line.
      - **Ledger account** – The ledger account number to post the journal line to.
      - **Cost center** – The cost center number to use to post the journal line.
      - **Cost amount** – The cost amount for the journal line.

6.  Click **Post** \> **OK** to post the journal line.

    > [!NOTE]
    > You can view the type of absorbed cost that is posted to a work center, the corresponding cost center that the work center is associated with, the hourly rate, and the planned capacity for the work center details on the <STRONG>Absorbed costs</STRONG> page.

## Close absorption costs

You can post the absorption costs for a specific month and year to the ledger. You can specify the transfer account and transfer offset account in the **Accounts - WIP** and **Accounts - costing** fields on the **Resources** page. 

1.  Click **Production control** \> **Periodic** \> **Absorption costs** \> **Absorption costs - monthly closing**.

2.  In the **Month/Year to close** field, select the month and year to post the absorbed costs for.

3.  Click **OK** to post the absorption costs for the selected month and year.

## Cancel absorbed costs

Use this procedure to cancel the absorbed costs that are not posted to the ledger for a specific month and year. You cannot cancel the absorbed costs after the monthly closing is completed.

1.  Click **Production control** \> **Periodic** \> **Absorption costs** \> **Absorbed costs cancellation**.

2.  In the **Month/Year to cancel** field, select the month and year to cancel the absorbed costs for.

3.  Click **OK** to cancel the absorbed costs for the selected month and year.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
