---
# required metadata

title: Asynchronous customer creation mode FAQ
description: This article provides answers to frequently asked questions about asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 01/15/2026
ms.topic: faq
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-12-17
ms.custom: 
  - bap-template
---

# Asynchronous customer creation mode FAQ

[!include [banner](includes/banner.md)]

This article provides answers to frequently asked questions about asynchronous (async) customer creation mode in Microsoft Dynamics 365 Commerce.

### Why can't I enable the "Enable editing customers in asynchronous mode" feature?

Before you enable the **Enable editing customers in asynchronous mode** feature, you must enable the following features:

- Performance improvements for customer orders and customer transactions
- Enable enhanced async customer creation
- Enable asynchronous creation for customer addresses

### Why do I still see real-time service calls made to Commerce headquarters after the "Enable editing customers in asynchronous mode" feature is enabled?

This issue occurs when Commerce Data Exchange (CDX) jobs aren't run to ensure the feature state and other channel metadata are synchronized with the channel. Before you retry the scenario, ensure the following CDX jobs are run in Commerce headquarters:

- 1110 (Global configuration)
- 1010 (Customers)
- 1070 (Channel configuration)

Data that is cached in Commerce Scale Unit (CSU) might not be immediately reflected in Commerce headquarters after the CDX jobs are run.

### Why doesn't Commerce headquarters show customer creation or updates from the point of sale (POS) or e-commerce channel?

Ensure the following actions are performed in the order that they're listed in here.

1. Run the CDX P-job in Commerce headquarters to ensure async customer data is stored in the **RETAILASYNCCUSTOMERV2**, **RETAILASYNCADDRESSV2**, **RETAILASYNCCUSTOMERCONTACT**, **RETAILASYNCCUSTOMERAFFILIATION**, and **RETAILASYNCCUSTOMERATTRIBUTEV2** tables.
1. Run the **Synchronize customers and channel requests** batch job in Commerce headquarters. After successful execution of the batch job, all records that are successfully processed from the previously mentioned tables will have the **OnlineOperationCompleted** field set to **1**.

### How do I know which customer management in asynchronous mode operation failed, and how do I make changes if they're required?

To view all asynchronous mode operations and their synchronization status, in Commerce headquarters go to **Commerce and Retail \> Customers \> Customer synchronization status**. To make changes, edit a specific operation, update the fields, select **Save**, and then select **Synchronize** to sync the changes.

[!INCLUDE[footer-include](../includes/footer-banner.md)]