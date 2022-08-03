---
# required metadata

title: Asynchronous customer creation mode FAQ
description: This article provides answers to frequently asked questions about asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 08/03/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
---

# Asynchronous customer creation mode FAQ

This article provides answers to frequently asked questions about asynchronous (async) customer creation mode in Microsoft Dynamics 365 Commerce.

### Why can't I enable the "Enable editing customers in asynchronous mode" feature?

Before enabling the **Enable editing customers in asynchronous mode** feature, you must first enable the following features: 

- **Performance improvements for customer orders and customer transactions**
- **Enable enhanced async customer creation**
- **Enable asynchronous creation for customer addresses**

### Why am I still observing real-time service calls being made to Commerce headquarters after the "Enable editing customers in asynchronous mode" feature is enabled?

This issue occurs when Commerce Data Exchange (CDX) jobs haven't been executed to ensure that the feature state and other channel metadata are synchronized with the channel. Ensure that the following CDX jobs are executed in headquarters before reattempting the scenario:
- 1110 (Global configuration)
- 1010 (Customers)
- 1070 (Channel configuration)

Data cached in Commerce Scale Unit (CSU) may not be immediately reflected in headquarters after the CDX jobs have been executed.

### Why doesn't Commerce headquarters show customer creation or updates from the point of sale (POS) or e-commerce channel?

Ensure that the following actions have been performed in the exact sequence below:

1. Execute the CDX P-job in headquarters, which will ensure that async customer data stored in the **RETAILASYNCCUSTOMERV2**, **RETAILASYNCADDRESSV2**, **RETAILASYNCCUSTOMERCONTACT**, **RETAILASYNCCUSTOMERAFFILIATION**, and **RETAILASYNCCUSTOMERATTRIBUTEV2** tables are available in headquarters. 
1. Execute the **Synchronize customers and channel requests** batch job in Commerce headquarters. After successful execution of the batch job, all records that have been successfully processed from the tables mentioned above will have the **OnlineOperationCompleted** field marked as **1**.
