---
# required metadata

title: Customer management in asynchronous mode
description: This topic explains how retailers can enable customer management capabilities in asynchronous mode at the point of sale (POS) or e-Commerce channel in Microsoft Dynamics 365 Commerce.
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 11/24/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
ms.dyn365.ops.version: 10.0.24
---


# Sync customers and Async customers

[!include [banner](includes/banner.md)]

This topic explains how retailers can enable customer management capabilities in asynchronous mode, for both point of sale (POS) and e-Commerce channels in Microsoft Dynamics 365 Commerce.

In Commerce, there are two modes of customer creation: Synchronous (or Sync) and Asynchronous (or Async). By default, customers are created synchronously. In other words, they are created in Commerce headquarters in real time. The Sync customer creation mode is beneficial because new customers are immediately searchable across channels. However, it also has a drawback. Because it generates [Commerce Data Exchange: Real-time Service](dev-itpro/define-retail-channel-communications-cdx.md#realtime-service) calls to Commerce headquarters, performance can be affected if many concurrent customer creation calls are made.

If the **Create customer in async mode** option is set to **Yes** in the store's functionality profile (**Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**), Real-time Service calls aren't used to create customer records in the channel database. The Async customer creation mode doesn't affect the performance of Commerce headquarters. A temporary globally unique identifier (GUID) is assigned to every new Async customer record and used as the customer account ID. This GUID isn't shown to POS users. Instead, those users will see **Pending sync** as the customer account ID. 



## Async customer limitations

The Async customer functionality currently has the following limitations:

- Async customer records can't be edited unless the customer has been created in Commerce headquarters and the new customer account ID has been synced back to the channel. Therefore, the address can't be saved for an Async customer until that customer is synced to Commerce headquarters, because the addition of a customer address is internally implemented as an edit operation on the customer profile. However, if the **Enable the asynchronous creation for customer addresses** feature is enabled, the customer addresses can also be saved for Async customers.

- Loyalty cards can't be issued to Async customers unless the new customer account ID has been synced back to the channel.

## Async customer enhancements

In earlier versions of Commerce there were some limitation prevented you to choose **creating customers in async mode**, and the Commerce team has been working to make the Async customer capabilities more closely to match with Sync customer capabilities. 

As of **Commerce version 10.0.24**, you can enable **Enable enhanced async customer creation** feature in the **Feature management** workspace so that the following limitations will be addressed to bridge the gap between asynchronous and synchronous modes of customer creation in POS and e-Commerce: 

- Affiliations can be associated with Async customers. 
- Secondary email addresses and phone numbers can be captured for Async customers.


As of the **Commerce version 10.0.22** release, you can enable **Enable the asynchronous creation for customer addresses** feature that in the **Feature management** workspace so that newly created customer addresses can be saved asynchronously for both Sync customers and Async customers. 

After enabling above features under Feature management workspace, you must schedule a recurring batch job for the **P-job**, the **Synchronize customers and business partners from async mode** job, and the **1010** job, so that any Async customers are converted to Sync customers in Commerce headquarters.




## Additional resources

[Customer management in stores](dev-itpro/customer-mgmt-stores.md)

[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)

