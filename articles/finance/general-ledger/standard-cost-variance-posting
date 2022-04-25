---
# required metadata

title: Standard cost variance posting
description: A detailed look at the standard cost tab in the inventory posting profile. 
author: raprofit
ms.date: 04/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventPosting, InventItemGroup
# ROBOTS: 
audience: Application User
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit

---

# Standard cost variance posting

When you use standard costing for one or more products in your organization, you need to configure the [Prerequisites for standard costing](/supply-chain/cost-management/prerequisites-standard-costs.md). This section documents how to configure the posting accounts that are needed for step three in the prerequisite for standard costing page.

There are a variety of types of variances that can occur for purchases and production orders. For examples of production variances, refer to [Common sources of production variances](/supply-chain/cost-management/common-sources-of-production-variances.md). Purchase order price variances happen when you use standard cost for a purchased item and there is a difference between the standard cost established for the product and the amount that is invoiced on the purchase order.

## Sample posting profile configuration

The following table shows examples of the default posting types with sample main accounts and descriptions. The Debit/Credit column indicates if the transaction typically Debit or Credits or in some cases can post either. The Clearing account column indicates the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted. The P/F column indicates P for physical posting and F for financial posting. The Follow column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicates the posting type that is typically followed.

> [!NOTE]
> The suggested main accounts and main account names are only suggestions, we recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type                     | Main account example | Main account name example        | Account type | Debit/ Credit? | Clearing account | Physical or Financial | Follow | Description                                                                                                                                                                                                       |
|----------------------------------|----------------------|----------------------------------|--------------|----------------|------------------|-----------------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Purchase price variance          | 510310               | Purchase Price Variance          | Expense      | Both           | No               | F                     | N/A    | This account is used when there is a variance between the purchase price and standard cost on a purchase order.                                                                                                   |
| Inventory cost revaluation       | 510330               | Inventory Cost Revaluation       | Expense      | Both           | No               | F                     | N/A    | This account is used when a new costing version is activated for a standard cost item to revalue the on-hand inventory.                                                                                           |
| Cost change variance             | 510320               | Cost Change Variance             | Expense      | Both           | No               | F                     | N/A    | This account is used when there is a difference in standard costs between sites or when an item is returned and there is a change between the original standard cost and the current standard cost for a product. |
| Production lot size variance     | 510370               | Production Lot Size Variance     | Expense      | Both           | No               | F                     | N/A    | This account is used when there are differences between the BOM calculation basis and the actual quantity for the production order cost calculation.                                                              |
| Production price variance        | 510340               | Production Price Variance        | Expense      | Both           | No               | F                     | N/A    | This account is used when there are price differences between the estimated cost and actual cost for a production order.                                                                                          |
| Production quantity variance     | 510350               | Production Quantity Variance     | Expense      | Both           | No               | F                     | N/A    | This account is used when there are quantity differences between the estimated cost and actual costs for a production order.                                                                                      |
| Production substitution variance | 510360               | Production Substitution Variance | Expense      | Both           | No               | F                     | N/A    | This account is used when there is unexpected consumption on a production order.                                                                                                                                  |
| Rounding variance                | 618160               | Rounding Difference              | Expense      | Both           | No               | F                     | N/A    | This account is used when there is a rounding difference when calculating the production costs from the standard costs.                                                                                           |
