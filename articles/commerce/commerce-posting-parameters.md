---
# required metadata

title: Commerce posting parameters
description: This topic describes each of the parameters related to Commerce specific postings.
author: analpert
ms.date: 04/12/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RetailParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: ?
ms.assetid: ?
ms.search.region: Global
ms.search.industry: Retail
ms.author: analpert
ms.search.validFrom: 2022-04-12
ms.dyn365.ops.version: 10.0.27

---

# Commerce posting parameters

This article will describe the **Commerce parameters** specific for posting of financial and physical transactions. 

# Periodic discounts
| Parameter                         | Definition                                                                                                                                                                                                                                                                   |
|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Post periodic discount            | This option enables periodic offers to be posted to the ledger accounts. Periodic discounts include mix and match, quantity discounts, and discount offers. When this parameter is enabled additional fields within the periodic discount parameters section can be defined. |
| Ledger account type               | Test this value starting at 4 and typically not more than 8.                                                                                                                                                                                                                 |
| Post info code discount           | This field is not used in out of box Commerce functionality any longer and will be deprecated.                                                                                                                                                                               |
| Post periodic discount for orders | This parameter controls whether retail periodic discounts are posted to the ledger for Customer order and Call center orders.                                                                                                                                                |

# Inventory update
| Parameter                                             | Definition                                                                                                                              |
|-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Use default batch id when batch numbers are not found | Define a default batch id that will be used for batch enabled items when batch numbers are not found and negative inventory is allowed. |
| Default batch id                                      | Batch number to be used when batch numbers for items are not found and the parameter to use default batch numbers is enabled.           |

# Aggregation
| Parameter                | Definition                                                                                                                                                                                                          |
|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Safe drop                | Enabling this parameter will aggregate all transactions during statement posting and create a single line in the journal for posting vs individual lines for each drop.                                             |
| Bank drop                | Enabling this parameter will aggregate all transactions during statement posting and create a single line in the journal for posting vs individual lines for each drop.                                             |
| Sales transactions       | Enabling this parameter will consolidate the transactions as part of the transaction statement posting process. It is recommended to enable this parameter.   This field was formally titled 'Voucher transactions' |
| Do not aggregate returns | If this option is selected, each return transaction will be posted as a separate sales order when posting a retail statement.                                                                                       |

# Batch processing
| Parameter                                                | Definition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Maximum number of parallel statements                    | This field defines the number of batch tasks that will be used to post multiple statements.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Max thread for order processing per statement            | This field represents the maximum number of threads used by the statement posting batch job to create and invoice sales orders for a single statement. The total number of threads that will be used by the statement posting process will be computed based on the value in this parameter multiplied by the value in the Maximum number of parallel statement posting parameter. Setting the value of this parameter too high can negatively impact the performance of the statement posting process.                                                                                    |
| Max transaction lines included in aggregation            | This field defines the number of transaction lines that will be included in a single aggregated transaction before a new one is created. Aggregated transactions are created based on different aggregation criteria such as customer, business date, or financial dimensions. It is important to note that the lines from a single transaction will not be split across different aggregated transactions. This means that there is a possibility that the number of lines in an aggregated transaction is slightly higher or lower based on factors such as number of distinct products. |
| Maximum number of threads to validate store transactions | This field defines the number of threads that will be used to validate transactions. Validating transactions is a required step that needs to occur before the transactions can be pulled into the statements. You also need to define a Gift card product on the Gift card FastTab on the Posting tab of the Commerce parameters page. This needs to defined even if gift cards are not used by the organization.                                                                                                                                                                         |
