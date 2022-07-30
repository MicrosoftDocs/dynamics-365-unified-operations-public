---
# required metadata

title: Asynchronous customer frequently asked questions. 
description: This article answers frequently asked questions about asynchronous mode of customer management in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 07/15/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin

ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
---

# Frequently asked questions - Async customer management

**Q: Why can't I enable the feature "Enable editing customers in asynchronous mode"?**

A:  **Enable editing customers in asynchronous mode** needs the following features to be enabled first: 

	• Performance improvements for customer orders and customer transactions.
	• Enable enhanced async customer creation
	• Enable asynchronous creation for customer addresses


**Q: Why am I still observing real-time service calls being made to the Headquarters, though "Enable editing customers in asynchronous mode" is enabled?**

A: This happens when the CDX jobs have not been executed to ensure that the Feature State and other channel metadata are synchronized with the channel. Please ensure that the below CDX jobs are executed before re-attempting the scenario:
	• 1110 (Global configuration)
	• 1010 (Customers)
	• 1070 (Channel configuration)

Note that this data can be cached in CSU and may not immediately reflect after the CDX jobs have been executed.


**Q: Why Headquarter is not reflecting customer creation or updates from POS or e-Commerce channel? **

A: Please ensure that the following actions have been performed in the exact sequence below:
	• Execute the CDX P-job in the Headquarters which will ensure the async customer data stored in RETAILASYNCCUSTOMERV2, RETAILASYNCADDRESSV2, RETAILASYNCCUSTOMERCONTACT, RETAILASYNCCUSTOMERAFFILIATION, and RETAILASYNCCUSTOMERATTRIBUTEV2 tables is now available in Headquarters. 
	• Execute the "Synchronize customers and channel requests" batch job in the Headquarters. Upon successful execution of this batch job, all records which have been successfully processed from the tables mentioned above will have the OnlineOperationCompleted field marked as 1.
