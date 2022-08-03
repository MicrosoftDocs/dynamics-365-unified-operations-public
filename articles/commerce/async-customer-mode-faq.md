---
# required metadata

title: Asynchronous customer frequently asked questions. 
description: This article answers frequently asked questions about asynchronous mode of customer management in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 08/03/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin

ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
---

# Frequently asked questions - Async customer management

This article answers frequently asked questions about asynchronous mode of customer management in Microsoft Dynamics 365 Commerce.

### Why can't I enable the feature "Enable editing customers in asynchronous mode"?

**Enable editing customers in asynchronous mode** needs the following features to be enabled first: 

- Performance improvements for customer orders and customer transactions.
- Enable enhanced async customer creation
- Enable asynchronous creation for customer addresses

### Why am I still observing real-time service calls being made to the Headquarters, though "Enable editing customers in asynchronous mode" is enabled?

This happens when the CDX jobs have not been executed to ensure that the Feature State and other channel metadata are synchronized with the channel. Ensure that the below CDX jobs are executed before re-attempting the scenario:
- 1110 (Global configuration)
- 1010 (Customers)
- 1070 (Channel configuration)

This data can be cached in CSU and may not immediately reflect after the CDX jobs have been executed.

### Why doesn't Commerce headquarters not reflect customer creation or updates from POS or e-commerce channel?

Ensure that the following actions have been performed in the exact sequence below:

- Execute the CDX P-job in headquarters, which will ensure that async customer data stored in the **RETAILASYNCCUSTOMERV2**, **RETAILASYNCADDRESSV2**, **RETAILASYNCCUSTOMERCONTACT**, **RETAILASYNCCUSTOMERAFFILIATION**, and **RETAILASYNCCUSTOMERATTRIBUTEV2** tables are available in headquarters. 
- Execute the "Synchronize customers and channel requests" batch job in the Headquarters. Upon successful execution of this batch job, all records that have been successfully processed from the tables mentioned above will have the **OnlineOperationCompleted** field marked as **1**.
