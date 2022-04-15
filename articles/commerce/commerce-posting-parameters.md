---
# required metadata

title: Commerce posting parameters
description: This topic describes each of the parameters specific to the posting of financial and physical transactions in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 04/22/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgriffin
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: analpert
ms.search.validFrom: 2022-04-12
ms.dyn365.ops.version: 10.0.27
---

# Commerce posting parameters

[!include [banner](includes/banner.md)]

This topic describes each of the parameters specific to the posting of financial and physical transactions in Microsoft Dynamics 365 Commerce.

## Periodic discount parameters

The following table lists the periodic discount parameters specific to the posting of financial and physical transactions.

| Parameter                         | Definition   |
|-----------------------------------|------------|
| Post periodic discount            | This option enables periodic offers to be posted to the ledger accounts. Periodic discounts include mix and match, quantity discounts, and discount offers. When this parameter is enabled additional fields within the periodic discount parameters section can be defined.  |
| Ledger account type               | <p>Select the type of account to be used to post periodic discounts:</p><p><ul><li><b>Standard</b> - The system will not use the discount-related fields on this page, but will use the accounts defined in headquarters on the <b>Posting</b> form located at <b>Inventory management > Setup > Posting > Posting forms</b>.</li><li><b>Periodic</b> - The system will use the discount-related fields on this page as the Commerce discount accounts. If you select the **Periodic** option, you must specify the general ledger account for each type of offer (discount, mix and match, quantity, and threshold). When you set up a discount, the discount form allows you to define an account during the individual discount setup. When the discount account posting feature is used on the discount setup form, then an additional debit entry and credit entry are made to reclassify the discount posting out of the Commerce discount general ledger (GL) account and into the discount GL account. For more information, see [Retail discounts](retail-discounts-overview.md).</li></ul></p> |
| Post info code discount           | This field is no longer used in the standard Commerce solution and will be deprecated.  |
| Post periodic discount for orders | This parameter controls whether retail periodic discounts are posted to the ledger for customer order and call center orders. |

## Inventory update parameters

The following table lists the inventory update parameters specific to the posting of financial and physical transactions.

| Parameter  | Definition  |                                                                                                                         
|------------|-------------|
| Use default batch ID when batch numbers are not found | Defines a default batch ID that will be used for batch-enabled items when batch numbers are not found and negative inventory is allowed. |
| Default batch ID   | Batch number to be used when batch numbers for items are not found and the parameter to use default batch numbers is enabled.           |

## Aggregation parameters

The following table lists the aggregation parameters specific to the posting of financial and physical transactions.

| Parameter                | Definition    |
|--------------------------|---------------|
| Safe drop                | Enabling this parameter will aggregate all transactions during statement posting and create a single line in the journal for posting instead of individual lines for each drop.                                             |
| Bank drop                | Enabling this parameter will aggregate all transactions during statement posting and create a single line in the journal for posting instead of individual lines for each drop.                                             |
| Sales transactions       | Enabling this parameter will consolidate the transactions as part of the transaction statement posting process. It is recommended that you enable this parameter. This field was previously titled "Voucher transactions". |
| Do not aggregate returns | If this option is selected, each return transaction will be posted as a separate sales order when posting a retail statement.  |

## Batch processing parameters

The following table lists the batch processing parameters specific to the posting of financial and physical transactions.

| Parameter   | Definition  |
|-------------|-------------|
| Maximum number of parallel statements | This field defines the number of batch tasks that will be used to post multiple statements.   |
| Max thread for order processing per statement  | This field represents the maximum number of threads used by the statement posting batch job to create and invoice sales orders for a single statement. The total number of threads that will be used by the statement posting process will be computed based on the value in this parameter multiplied by the value in the **Maximum number of parallel statement posting** parameter. Setting the value of this parameter too high can negatively impact the performance of the statement posting process.   |
| Max transaction lines included in aggregation  | This field defines the number of transaction lines that will be included in a single aggregated transaction before a new one is created. Aggregated transactions are created based on different aggregation criteria such as customer, business date, or financial dimensions. It is important to note that the lines from a single transaction will not be split across different aggregated transactions. This means that there is a possibility that the number of lines in an aggregated transaction is slightly higher or lower based on factors such as the number of distinct products. |
| Maximum number of threads to validate store transactions | This field defines the maximum number of threads that will be used to validate transactions. Validating transactions is a required step that must occur before the transactions can be pulled into the statements. You must also define a gift card product on the **Gift card** FastTab of the **Posting** tab of the **Commerce parameters** page. This must be defined even if gift cards are not used by the organization. |

The following table lists the recommended values for the parameters in the preceding table. These values should be tested and tailored to the deployment configuration and available infrastructure. Any increase in the recommended values can adversely affect other batch processing and should be validated.

| Parameter | Recommended value | Details |
|-----------|-------------------|---------|
| Maximum number of parallel statement posting | <p>Set this parameter to the number of batch tasks that are available for the batch group that is running the **Statement** job.</p><p>**General rule:** Multiply the number of Application Object Server (AOS) virtual servers by the number of batch tasks that are available per AOS virtual server.</p> | This parameter isn't applicable when the **Retail statements - Trickle feed** feature is enabled. |
| Max thread for order processing per statement | Start to test values at **4**. Typically, the value should not exceed **8**. | This parameter specifies the number of threads that are used to create and post sales orders. It represents the number of threads that are available for posting per statement. |
| Max transaction lines included in aggregation | Start to test values at **1000**. Depending on the headquarters configuration, smaller orders may be more beneficial to performance. | This parameter determines the number of lines that will be included in each sales order during statement posting. After this number is reached, lines will be split into a new order. Although the number of sales lines won't be exact, because the split occurs at the sales order level, it will be close to the number that is set. This parameter is used to generate sales orders for retail transactions that don't have a named customer. |
| Maximum number of threads to validate store transactions | It is recommended that you set this parameter to **4**, and that you increase it only if you don't attain acceptable performance. The number of threads that this process uses can't exceed the number of processors that are available to the batch server. If you assign too many threads here it might affect other batch processing. | This parameter controls the number of transactions that can be validated at the same time for a given store. |

> [!NOTE]
> All settings and parameters that are related to statement postings and that are defined on stores and on the **Commerce parameters** page are applicable to the improved statement posting feature.

## Invoice parameters

The following table lists the invoice parameters specific to the posting of financial and physical transactions.

| Parameter  | Definition  |
|------------|-------------|
| Journal name   | Payment journal name that will be used when creating customer payment journals for sales order payments. This applies to all order payments posted for point of sale (POS), call center, and e-commerce channel orders. |
| Account name  | Payment account name.  |
| Prioritize dimensions from payment method | When this flag is enabled, payment journals will use prioritized from the payment method instead of the store.               |
| Taxes \| Tax calculation behavior   | <p><ul><li>Recalculate: Calculate taxes again at time of invoicing sales orders created during statement posting.</li><li> Don't recalculate: Use the tax amounts calculated in POS when invoicing sales orders created during statement posting.</li></ul></p> |
| Refund \| Journal name   | Journal name that will be used when creating a customer payment journal for refunds. This setting will apply to all order payments posted for POS, call center, and e-commerce channel orders.                                    |

## Statement parameters

The following table lists the statement parameters specific to the posting of financial and physical transactions.

| Parameter      | Definition   |
|----------------|---------------------|
| Reserve inventory during calculation  | When this parameter is enabled, statement calculation will temporarily reserve inventory until the statement is posted. This is disabled by default to improve the performance of statement calculation. Updated inventory information can be calculated by using the **Post inventory** batch job. Note that the **Post** inventory batch job is no longer used when [trickle feed](trickle-feed.md)-based order creation for retail store transactions is enabled.  |
| Disable counting required  | This flag disables the counting during posting in headquarters.  |
| Recalculate financial dimensions on error  | Enabling this parameter allows for financial dimensions to be reevaluated on subsequent statement postings when statement posting fails.  |
| Use financial dimensions from the return store | Enabling this parameter allows linked return sales orders to be created with the financial dimensions of the store instead of using the financial dimensions from the original transaction.  |
| Unlink returns   | Enabling this parameter causes the statement to create returns of unposted sales as blind returns. This setting is disabled by default, and it is recommended to keep it disabled.  |
| Disable posting of rounding difference  | Disables posting of the rounding difference between a transaction payment and the gross amount during payments processing.   |
| Auto settle customer deposits    | Enabling this parameter specifies that customer deposits posted during retail statement posting should be settled against customer open transactions.   |
| Enable and use cash management reconciliation from POS | If enabled, cash management reconciliation will be completed at POS and the values will be passed through to retail financial statement posting to create statement lines.  |
| Ledger voucher detail level | Determines what level of detail will be included in the ledger voucher for select transactions originating from the POS. Transaction types include income, expenses, and discounts. For discounts, this parameter is only considered when the account number for a periodic discount and a regular discount are not the same. Summary is the recommended value for these postings unless the detail is required. When summary level posting is defined, **TransactionDiscountTrans.RecID** will not be populated. As of the Commerce 10.0.27 version release this flag was renamed and moved. It was previously named **Detail level** and was located under the **Inventory update section**. |
