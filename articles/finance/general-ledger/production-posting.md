---
title: Production order posting
description: Learn about different types of production order posting, including outlines on material consumption and reporting finished goods and error quantities.
author: rachelprofitt
ms.author: raprofit
ms.topic: overview
ms.date: 04/25/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: InventPosting, InventItemGroup, ProdGroup, WrkCtrTable, WrkCtrResourceGroup, ProjCategory, CostSheetDesigner
---

# Production postings

This article provides information about different types of posting in the production order process.


## Material consumption

Materials are registered as consumed during production when the production picking list journal is posted. This creates transactions that deduct the on-hand inventory. In the **Production parameters**, you can specify whether the value of raw materials that are in progress (called WIP), should be posted in the ledger.

The value of raw materials that are in progress (WIP) is posted to the **Estimated cost of materials consumed** and **Estimated cost of materials consumed, WIP** accounts. The picking list process for the production order is a physical update to the inventory transactions related to the production order. When a production order is registered as ended, the physical transactions are reversed and the related inventory transactions are financially updated. When the ending journal is posted, the **Cost of materials consumed** and **Cost of materials consumed, WIP** posting types are used.

The **Production** tab on the **Inventory posting profiles** page controls how production orders post to the general ledger. This is used when the **Ledger posting** field is set to either **Item and resource** or **Item and category** on the **Production control parameters** page. 

For a picking list journal to post to the general ledger for a production order, the following conditions must be met:

-   The **Post picking list in ledger** checkbox must be selected on the **Production control parameters** page. This setting can be overridden for a specific site on the **Production control parameters by site** page.
-   The **Post physical inventory** checkbox must be selected on the **Item model groups** page for the item selected on the purchase order line.
-   The main accounts must be specified on the **Inventory posting profile** page for the following posting types:
    -   **Estimated cost of materials consumed**
    -   **Estimated cost of materials consumed, WIP**

## Time consumption

The time that workers spend on production jobs is recorded in the **Route card journal** or the **Job card journal**. When these journals are posted, the ledger posting to a dedicated account for resources that are in progress (WIP) is processed. This posting represents the value of the time that is spent on the production order. After the production order is registered as ended, the WIP accounts are settled.

There are three possible ways to post time consumption depending on the option selected in the **Ledger posting** field on the **Production control parameters** page.

## Reporting finished goods and error quantities

When a production order is **Reported as finished**, the finished goods that have been completed are updated in inventory through the **Report as finished** journal. If you're using WIP accounting, a ledger journal is posted to reduce the WIP accounts and increase the inventory of the finished goods. The journal uses the standard cost that has been defined for the product. If the **Use estimated cost price** option is selected on the **Production control parameters** page, the estimated cost from the production order will be used.

The value of raw materials that are in progress (WIP) is posted to the **Estimated manufactured cost** and **Estimated manufactured cost, WIP** accounts. The **Report as finished** process for the production order is a physical update to the inventory transactions related to the production order. When a production order is ended, the physical transactions are reversed and the related inventory transactions are financially updated. When the ending journal is posted, the **Manufactured cost** and **Manufactured cost, WIP** posting types are used.

The **Production** tab on the **Inventory posting profiles** page is used to control how production orders will post to the general ledger. This is used when the **Ledger posting** field is set to either **Item and resource** or **Item and category** on the **Production control parameters** page. The **Ledger-items** FastTab on the **Production groups** page can also be used to control posting for production orders when the field is set to **Production groups**.

For a **Report as finished** journal to post to the general ledger for a production order, the following conditions must be met:
-   The **Post report as finished in ledger** checkbox must be selected in the **Production control parameters** page. This setting can be overridden for a specific site on the **Production control parameters by site** page.
-   The **Post physical inventory** checkbox must be selected on the **Item model groups** page for the item selected on the purchase order line.
-   The main accounts must be specified in the **Inventory posting profile** page for the following posting types:
    -   **Estimated manufactured cost**
    -   **Estimated manufactured cost, WIP**

## Ending the production order

Before a production order is ended, actual costs are calculated for the produced quantity. All estimated costs of material, labor, and overhead are reversed and replaced with actual costs. The overall cost of the finished item is debited from the **Manufactured cost** account and credited to the **Manufactured cost, WIP** account. The materials that were consumed during the production order are credited to the **Cost of materials consumed** and debited to the **Cost of materials, WIP** account.

If you select the **End job** checkbox when you run the cost calculation, the status of the production order is changed to **Ended**. This status prevents any additional costs from being unintentionally posted to a completed production order. You can specify that the value of error quantities that are reported as finished should be allocated to the good quantities that are reported as finished. Alternatively, you can specify that the value of error quantities be posted to a dedicated scrap account. 

To specify a specific scrap account, follow these steps:
1.  Go to **Production control** > **Setup** > **Production control parameters**.
2.  Select the **Standard update** tab.
3.  In the **Scrap method** field, select **Scrap account**.
4.  In the **Scrap account** field, select the main account where the scrap for error quantity should be posted when the production order is ended. For example, select an Expense account such as 510380: Production Scrap.

For the end journal to post to the general ledger for a production order, the following conditions must be met:
-   The main accounts must be specified in the **Inventory posting profile** or **Production groups** page for the following posting types:
    -   **Cost of materials consumed**
    -   **Cost of materials consumed, WIP**
    -   **Manufactured cost**
    -   **Manufactured cost, WIP**
-   The main accounts must be specified in the **Cost categories**, **Resources**, or **Resource groups** page for the following types:
    -   **Manufactured cost absorbed**
    -   **Cost of manufacturing consumed, WIP**

## Indirect costs for production orders

When you process transactions for a production order, you can configure indirect costs to capture overhead costs or additional fees in your general ledger. Physical transactions for indirect costs are recognized in inventory when you post a picking list journal or report as finished journal. Financial transactions for indirect costs are recognized in inventory when you post the end journal.

You can recognize indirect costs on your time consumption related to **Route card** journals or **Job card** journals. These transactions are reversed and posted into the financial accounts when you end the production order. For more information, go to [Costing sheets](../../supply-chain/cost-management/costing-sheets.md).

## Controlling the level of ledger posting

On the **Production control parameters** page, you can use the **Ledger posting** field to set the level of ledger posting for production processes. 

The following fields are available:

### Item and resource

When you select the **Item and resource** option in the **Ledger posting** field, the posting accounts come from the resource or resource group on operation in the route. Accounts on the specific resource will be the first posting option. If an account isn't specified, the accounts specified on the resource group will be used. Each operation line in a route can have one resource specified as the **Costing resource**. This resource is used for determining the account to be used. This option is commonly used when an organization assigns operating costs to the resources. Costs are often higher for the resources and are used to help make "make versus buy" decisions. This is the most detailed posting configuration, and allows the most granular control of the postings and very detailed analytics of the production process.

### Item and category

When you select the **Item and category** option in the **Ledger posting** field, the posting accounts will come from the **Cost category** page related to each line in the route. Each operation line in the route can have three cost categories: **Setup** time, **Run** time, and the **Quantity**. This option is commonly used when your organization's main focus is on process efficiency and activity duration. This option is a more summarized way of posting, and still provides a way to group costs into categories.

### Production group

When you select the **Production groups** option in the **Ledger posting** field, the posting accounts come from the **Production groups** page. **Production groups** are typically used when more than one production line runs similar products or has similar equipment. You can use this option to compare the costs between two different production groups.  
  
> [!NOTE]
> If the standard method for calculating the cost of the finished item is used, the final transactions will reflect this. If actual costs and the costs that are calculated by using the standard method differ, the differences are posted to the account that shows profit or loss.

### Route groups and ledger posting

Each operation line in a route has a **Route group** specified. The **Setup time**, **Run time**, and **Quantity** fields on the **Route group** in the **Estimation and costing** group are used to control whether the time will be used for costing when posting a **Job card** or **Route card journal** on the production order. If the options are disabled, a voucher won't be created in the general ledger for the time consumption.

For a **Route card** or **Job card journal** to post to the general ledger for a production order, the following conditions must be met:

-   The **Setup time**, **Run time** or **Quantity** field must be selected in the **Estimation and costing** group on the **Route group** page.
-   The main accounts must be specified in either the **Cost category**, **Route**, **Route group**, or **Production groups** page for the following posting types:
    -   Estimated manufacturing cost absorbed
    -   Estimated cost of manufacturing consumed, WIP

The following diagram shows the relationship of the route group to the calculation of the total cost for each operation (route line) in a given route. Each route line has one route group. The route group controls parameters for setup time, run time, and quantity. The **Cost category** tab has three options for **Setup**, **Run**, and **Quantity** that are enabled based on the route groups setting. The **Timings** FastTab has three fields that are based on the route group.

The formula that's used is based on whether the option is enabled in the route group. The cost from the selected cost category is multiplied by the quantity that was entered in the timings to calculate the total cost.

:::image type="complex" source="media/RouteGroupRelationship.png" alt-text="The relationship of route groups to the total calculated cost.":::
The relationship of route groups to the total calculated cost. Each route line has one route group. The route group controls parameters for setup time, run time and quantity. The cost category tab has three options for the Setup, Run, and Quantity that are enabled based on the route groups setting. The Timings FastTab has three fields that are enabled and costed based on the route group. The formula that is used is based on if the option is enabled in the route group. The cost from the selected cost category is multiplied by the quantity that is entered in the timings to calculate the total cost.
:::image-end:::

## Sample posting profile configuration

The following table shows examples of the default posting types with sample main accounts and descriptions. 

 - The **Debit/Credit** column indicates whether the transaction typically Debit or Credits, or in some cases it can post either. 
 - The **Clearing account** column indicates whether the posting type is a clearing account. The amount posted in this account is automatically reversed when a later transaction is posted. 
 - The **P/F** column indicates **P** for physical posting and **F** for financial posting. 
 - The **Follow** column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicates the posting type that's typically followed.

> [!NOTE]
> The suggested main accounts and main account names are suggestions. We recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type  | Main account example | Main account name example| Account type | Debit/ Credit? | Clearing account | Physical or Financial | Follow | Description |
|---------------|----------------------|--------------------------|--------------|----------------|------------------|-----------------------|--------|------------|
| Estimated cost of materials consumed      | 140100               | Materials Inventory        | Asset        | Credit         | Y                | P                     | Cost of materials consumed                | This account is used when you post a picking list journal for a production order. The offset to this account is the Estimated cost of materials, WIP. The amount in this account is automatically reversed when the production order is ended. This account represents the inventory account in the balance sheet.       |
| Estimated cost of materials consumed, WIP | 150150               | Production WIP – Materials | Asset        | Debit          | Y                | P                     | Estimated manufactured cost, WIP          | This account is used when you post a picking list journal for a production order. The offset to this account is the Estimated cost of materials consumed. The amount in this account is automatically reversed when a production order is ended. This account represents the WIP in your balance sheet.                  |
| Estimated manufactured cost               | 140200               | Finished Goods Inventory   | Asset        | Debit          | Y                | P                     | Manufactured cost                         | This account is used when you post a report as finished journal for a production order. The offset to this account is the Estimated manufactured cost, WIP. The amount in this account is automatically reversed when the production order is ended. This account represents the inventory account in the balance sheet. |
| Estimated manufactured cost, WIP          | 150150               | Production WIP – Materials | Asset        | Credit         | Y                | P                     | Manufactured cost, WIP                    | This account is used when you post a report as finished journal for a production order. The offset to this account is the Estimated manufactured cost. The amount in this account is automatically reversed when a production order is ended. This account represents the WIP in your balance sheet.                     |
| Cost of materials consumed                | 140100               | Materials Inventory        | Asset        | Credit         | N                 | F                     | Estimated cost of materials consumed      | This account is used to recognize the materials that are consumed in the production order during the ending process. The offset to this account is the Cost of materials consumed, WIP.                                                                                                    |
| Cost of materials consumed, WIP           | 150150               | Production WIP – Materials | Asset        | Debit          | N                 | F                     | Estimated cost of materials consumed, WIP | This account is used to recognize the materials in WIP that are consumed in the production order during the ending process. The offset to this account is the Cost of materials consumed.                                                |
| Manufactured cost                         | 140200               | Finished Goods Inventory   | Asset        | Debit          | N                 | F                     | Estimated manufactured cost               | This account is used to recognize the cost of the finished good that is produced by a production order when you end the production order. The offset to this account is the Manufactured cost, WIP account.                                                                  |
| Manufactured cost, WIP                    | 150150               | Production WIP – Materials | Asset        | Credit         | N                 | F                     | Estimated manufactured cost, WIP          | This account is used to recognize the cost of the finished good in WIP that is produced by a production order when you end the production order. The offset to this account is the Manufactured cost account.                                     |

> [!NOTE]
> The **Lean service WIP receipt** and **Lean service WIP clearing account** are used with backflush costing for lean manufacturing. For more information, go to [Backflush costing](../../supply-chain/cost-management/backflush-costing.md).