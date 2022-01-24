---
# required metadata

title: Asynchronous customer creation mode
description: This topic describes the asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 12/10/2021
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.scope: Retail, Core, Operations
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
---

# Asynchronous customer creation mode

[!include [banner](includes/banner.md)]

This topic describes the asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.

In Commerce, there are two modes of customer creation: synchronous (or sync) and asynchronous (or async). By default, customers are created synchronously. In other words, they are created in Commerce headquarters in real time. The sync customer creation mode is beneficial because new customers are immediately searchable across channels. However, it also has a drawback. Because it generates [Commerce Data Exchange: Real-time Service](dev-itpro/define-retail-channel-communications-cdx.md#realtime-service) calls to Commerce headquarters, performance can be affected if many concurrent customer creation calls are made.

If the **Create customer in async mode** option is set to **Yes** in the store's functionality profile (**Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**), Real-time Service calls aren't used to create customer records in the channel database. The async customer creation mode doesn't affect the performance of Commerce headquarters. A temporary globally unique identifier (GUID) is assigned to every new async customer record and used as the customer account ID. This GUID isn't shown to point of sale (POS) users. Instead, those users will see **Pending sync** as the customer account ID.

> [!IMPORTANT]
> Whenever the POS goes offline, the system automatically creates customers asynchronously, even if the async customer creation mode is disabled. Therefore, regardless of your selection between sync and async customer creation, Commerce headquarters administrators must create and schedule a recurring batch job for the **P-job**, the **Synchronize customers and business partners from async mode** job (formerly named **Synchronize customers and business partners from async mode**), and the **1010** job, so that any async customers are converted to sync customers in Commerce headquarters.

## Async customer limitations

The async customer functionality currently has the following limitations:

- Async customer records can't be edited unless the customer has been created in Commerce headquarters and the new customer account ID has been synced back to the channel.
- Loyalty cards can't be issued to async customers unless the new customer account ID has been synced back to the channel.

## Async customer enhancements

As of the Commerce version 10.0.24 release, you can enable the **Enable enhanced async customer creation** feature in the **Feature management** workspace. This feature bridges the gap between async and sync customer creation modes in POS and e-commerce in the following ways:

- Affiliations can be associated with async customers.
- Titles can be added to async customers.
- Secondary email addresses and phone numbers can be captured for async customers.

As of the Commerce version 10.0.22 release, you can enable the **Enable the asynchronous creation for customer addresses** feature in the **Feature management** workspace. This feature enables newly created customer addresses to be saved asynchronously for both sync customers and async customers.

After you enable the previously mentioned features, you must schedule a recurring batch job for the **P-job**, the **Synchronize customers and business partners from async mode** job, and the **1010** job, so that any async customers are converted to sync customers in Commerce headquarters.

### Customer creation in POS offline mode

As was mentioned earlier, whenever the POS goes offline, the system automatically creates customers asynchronously, even if the async customer creation mode is disabled. Therefore, Commerce headquarters administrators must create and schedule a recurring batch job for the **P-job**, the **Synchronize customers and business partners from async mode** job, and the **1010** job, so that any async customers are converted to sync customers in Commerce headquarters.

> [!NOTE]
> If the **Filter shared customer data tables** option is set to **Yes** on the **Commerce channel schema** page (**Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group**), customer records aren't created in POS offline mode. For more information, see [Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion).

## Additional resources

[Customer management in stores](customer-mgmt-stores.md)

[Convert asynchronous customers to synchronous customers](convert-async-to-sync.md)

[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
