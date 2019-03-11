---
# required metadata

title: Linked Refunds: Refund of a previously approved and confirmed transaction
description: This topic describes how to enable and use 'Linked refunds' feature.
author: 
manager: AnnBe
ms.date: 3/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rapraj
ms.search.validFrom: 2019-03-28
ms.dyn365.ops.version: Retail 10.0.1 update

---

### Linked Refunds: Refund of a previously approved and confirmed transaction. 

[!include [banner](../../includes/banner.md)]

Returns are an integral operation for a Retailer. The ability to accept returns for sales and refund the payments to the customer allows the Retailer an option to service their customers’ needs and issues.

A Linked Refund is a refund of a previously approved and confirmed transaction. This can either be a full or partial refund of the previous transaction and cannot exceed the full amount of the original authorization. 
 
## FEATURE DESCRIPTION

With the current set of capability, Retailers can process refunds to Cards, but these must be manually specified by the cashier. Cashiers are not able to process the funds to the original mode of payment(s) unless provided by the customer. Call center orders do not have any traceability to the mode of payment made – Dynamics 365 does not store any information on the type of payment made from call centers and there is no way to validate what the customer specified as a mode of payment is valid as the one used for purchase. 

This new feature outlines the improvements that needs to be made to the ‘Returns’ function in Dynamics 365 for Retail application to have a better functionality and flexibility for the Retailers to use the original payment as the return payment mode. 
 
### In scope :
Cashiers can now process refund to card used during original transaction without the card being present for return.
- Linked refunds for cash and carry using credit/debit cards.
- Linked refunds for customer orders using credit/debit cards.
 
### Out of scope :
Linked refunds with gift cards.
Linked refunds with loyalty cards.
Exchange orders support.
Multiple return orders in the same transaction.
 
 
## Who uses this feature
This feature will be used by the customer developer or partner/ISV to use linked refunds via POS, center or e-Commerce channels.
 
### License Required
No
 
### Setup Required
If the customer is not using Adeyn Connector out of box implementation, they will have to set up the connector that supports tokenization of credit cards.

