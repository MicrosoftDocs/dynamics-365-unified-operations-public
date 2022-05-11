---
# required metadata

title: Commerce posting parameters
description: This topic describes the parameters that are specific to the posting of financial and physical transactions in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 04/27/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: analpert
ms.search.validFrom: 2022-04-12
---

# Commerce posting parameters

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes the parameters that are specific to the posting of financial and physical transactions in Microsoft Dynamics 365 Commerce. Commerce posting parameters are located in Commerce headquarters at **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters \> Posting**.

## Periodic discount parameters

The following table lists the periodic discount parameters that are specific to the posting of financial and physical transactions.

| Parameter | Description |
|-----------|-------------|
| Post periodic discount | This option controls whether periodic offers are posted to the ledger accounts. Periodic discounts include mix and match discounts, quantity discounts, and discount offers. When this parameter is enabled, additional fields can be set in the **Periodic discounts** section. |
| Ledger account type | <p>Select the type of account that is used to post periodic discounts:</p><ul><li>**Standard** – The system doesn't use the discount-related fields on this page. Instead, it uses the accounts that are defined on the **Posting** page in Commerce headquarters (**Inventory management \> Setup \> Posting \> Posting forms**).</li><li>**Periodic** – The system uses the Commerce discount accounts that are specified by the discount-related fields on this page. If you select this option, you must specify the general ledger (GL) account for each type of offer (discount, mix and match, quantity, and threshold). When you set up each discount, you can define an account. When the discount account posting feature is used on the discount setup page, an additional debit entry and credit entry are made to reclassify the discount posting from the Commerce discount GL account to the discount GL account. For more information, see [Retail discounts](retail-discounts-overview.md).</li></ul> |
| Post info code discount | This option is no longer used in the standard Commerce solution and will be deprecated. |
| Post periodic discount for orders | This option controls whether retail periodic discounts are posted to the ledger for customer order and call center orders. |

## Inventory update parameters

The following table lists the inventory update parameters that are specific to the posting of financial and physical transactions.

| Parameter | Description |
|-----------|-------------|
| Use default batch ID when batch numbers are not found | This option controls whether a default batch ID is used for batch-enabled items if batch numbers aren't found and negative inventory is allowed. |
| Default batch ID | The batch number to use if batch numbers for items aren't found and the **Use default batch ID when batch numbers are not found** parameter is enabled. |

## Aggregation parameters

The following table lists the aggregation parameters that are specific to the posting of financial and physical transactions.

| Parameter | Description |
|-----------|-------------|
| Safe drop | Enable this parameter to aggregate all transactions during statement posting and create a single line in the journal for posting instead of a separate line for each drop. |
| Bank drop | Enable this parameter to aggregate all transactions during statement posting and create a single line in the journal for posting instead of a separate line for each drop. |
| Sales transactions | Enable this parameter to consolidate the transactions as part of the transaction statement posting process. We recommend that you enable this parameter. It was previously named **Voucher transactions**. |
| Do not aggregate returns | If this option is selected, each return transaction will be posted as a separate sales order when a retail statement is posted. |

## Batch processing parameters

The following table lists the batch processing parameters that are specific to the posting of financial and physical transactions.

| Parameter | Description |
|-----------|-------------|
| Maximum number of parallel statements | This field defines the number of batch tasks that are used to post multiple statements. |
| Max thread for order processing per statement | This field represents the maximum number of threads that the statement posting batch job uses to create and invoice sales orders for a single statement. The total number of threads that the statement posting process uses is calculated by multiplying the value of this parameter by the value of the **Maximum number of parallel statement posting** parameter. If the value of this parameter is too high, it can negatively affect the performance of the statement posting process. |
| Max transaction lines included in aggregation | This field defines the number of transaction lines that are included in a single aggregated transaction before a new transaction is created. Aggregated transactions are created based on different aggregation criteria, such as the customer, the business date, or financial dimensions. Note that the lines from a single transaction won't be split across different aggregated transactions. Therefore, the number of lines in an aggregated transaction might be slightly higher or lower, based on factors such as the number of distinct products. |
| Maximum number of threads to validate store transactions | This field defines the maximum number of threads that are used to validate transactions. Validation of transactions is a required step that must occur before the transactions can be pulled into the statements. You must also define a gift card product on the **Gift card** FastTab on the **Posting** tab of the **Commerce parameters** page, even if the organization doesn't use gift cards. |

The following table lists the recommended values for the parameters in the preceding table. These values should be tested and tailored to the deployment configuration and available infrastructure. Values that exceed the recommended values can adversely affect other batch processing and should be validated.

| Parameter | Recommended value | Details |
|-----------|-------------------|---------|
| Maximum number of parallel statement posting | <p>Set this parameter to the number of batch tasks that are available for the batch group that is running the **Statement** job.</p><p>**General rule:** Multiply the number of Application Object Server (AOS) virtual servers by the number of batch tasks that are available per AOS virtual server.</p> | This parameter isn't applicable when the **Retail statements - Trickle feed** feature is enabled. |
| Max thread for order processing per statement | Start to test values at **4**. Typically, the value should not exceed **8**. | This parameter defines the number of threads that are used to create and post sales orders. It represents the number of threads that are available for posting per statement. |
| Max transaction lines included in aggregation | Start to test values at **1000**. Depending on the Commerce headquarters configuration, smaller orders might be more beneficial to performance. | This parameter defines the number of lines that are included on each sales order during statement posting. After this number is reached, lines will be split into a new order. The number of sales lines won't exactly equal the number that you specify, because the split occurs at the sales order level. Nevertheless, the number will be close to the number that is set. This parameter is used to generate sales orders for retail transactions that don't have a named customer. |
| Maximum number of threads to validate store transactions | We recommend that you set this parameter to **4**, and that you increase it only if you don't achieve acceptable performance. The number of threads that this process uses can't exceed the number of processors that are available to the batch server. If the number of threads is too high, other batch processing might be affected. | This parameter controls the number of transactions that can be validated at the same time for a given store. |

> [!NOTE]
> All settings and parameters that are related to statement postings, and that are defined on stores and on the **Commerce parameters** page, are applicable to the improved statement posting feature.

## Invoice parameters

The following table lists the invoice parameters that are specific to the posting of financial and physical transactions.

| Parameter | Description |
|-----------|-------------|
| Journal name | The payment journal name that is used when customer payment journals for sales order payments are created. This setting applies to all order payments that are posted for point of sale (POS), call center, and e-commerce channel orders. |
| Account name | The payment account name. |
| Prioritize dimensions from payment method | When this flag is enabled, payment journals prioritize dimensions from the payment method instead of dimensions from the store. |
| Tax calculation behavior | This parameter specifies the behavior when sales orders that are created during statement posting are invoiced:<ul><li>**Recalculate** – Calculate taxes again.</li><li> **Don't recalculate** – Use the tax amounts that are calculated in POS.</li></ul> |
| Journal name | The journal name that is used when a customer payment journal for refunds is created. This setting applies to all order payments that are posted for POS, call center, and e-commerce channel orders. |

## Statement parameters

The following table lists the statement parameters that are specific to the posting of financial and physical transactions.

| Parameter | Description |
|-----------|-------------|
| Reserve inventory during calculation | When this parameter is enabled, statement calculation temporarily reserves inventory until the statement is posted. This parameter is disabled by default to help improve the performance of statement calculation. Updated inventory information can be calculated by using the **Post inventory** batch job. Note that the **Post** inventory batch job is no longer used when [trickle feed](trickle-feed.md)–based order creation for retail store transactions is enabled. |
| Disable counting required | This flag disables the counting during posting in Commerce headquarters. |
| Recalculate financial dimensions on error | When this parameter is enabled, financial dimensions can be reevaluated on subsequent statement postings if statement posting fails. |
| Use financial dimensions from the return store | When this parameter is enabled, linked return sales orders can be created that use the financial dimensions of the store instead of the financial dimensions from the original transaction. |
| Unlink returns | When this parameter is enabled, the statement can create returns of unposted sales as blind returns. This parameter is disabled by default, and we recommend that you keep it disabled. |
| Disable posting of rounding difference | This parameter disables posting of the rounding difference between a transaction payment and the gross amount during payments processing. |
| Auto settle customer deposits | When this parameter is enabled, customer deposits that are posted during retail statement posting are settled against customer open transactions. |
| Enable and use cash management reconciliation from POS | When this parameter is enabled, cash management reconciliation is done in POS, and the values are passed through to retail financial statement posting to create statement lines. |
| Ledger voucher detail level | This parameter defines the level of detail that is included in the ledger voucher for selected transactions that originate from POS. Transaction types include income, expenses, and discounts. For discounts, this parameter is considered only when the account number for a periodic discount and the account number for a regular discount aren't the same. Unless details are required, **Summary** is the recommended value for these postings. When summary-level posting is defined, **TransactionDiscountTrans.RecID** won't be filled in. In the Commerce 10.0.27 version release, this flag was renamed and moved. It was previously named **Detail level** and was in the **Inventory update** section. |
