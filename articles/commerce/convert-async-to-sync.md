---
# required metadata

title: Convert asynchronous customers to synchronous customers
description: This topic explains how to convert asynchronous customers to synchronous customers in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 12/07/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
---

# Convert asynchronous customers to synchronous customers

[!include [banner](includes/banner.md)]

This topic explains how to convert asynchronous customers to synchronous customers in Microsoft Dynamics 365 Commerce.

To convert asynchronous customers to synchronous customers, follow these steps.

1. In Commerce headquarters, run the **P-job** to send the asynchronous customers to headquarters. 
1. Run the **Synchronize customers and business partners from async mode** job (formerly named the **Synchronize customers and business partners from async mode** job) to create customer account IDs.
1. Run the **1010** job to sync the new customer account IDs to the channels.

If an order is referenced to an asynchronous customer or address not synchronized to headquarters yet, the customer or address will be synchronized as part of the **Synchronize orders** batch job. If a cash and carry transaction references an asynchronous customer or address, the customer or address will be synchronized before EOD posting.

## Additional resources

[Customer management in stores](/customer-mgmt-stores.md)

[Synchronous and asynchronous customer](/synchronous-and-asynchronous-customers.md)

[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
