---
# required metadata

title: Asynchronous customer creation mode
description: This article describes the asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 08/02/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin

ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
---

# Asynchronous customer creation mode

[!include [banner](includes/banner.md)]

This article describes the asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.

In Commerce, there are two modes of customer creation: synchronous (or sync) and asynchronous (or async). By default, customers are created synchronously. In other words, they're created in Commerce headquarters in real time. The sync customer creation mode is beneficial because new customers are immediately searchable across channels. However, it also has a drawback. Because it generates [Commerce Data Exchange: Real-time Service](dev-itpro/define-retail-channel-communications-cdx.md#realtime-service) calls to Commerce headquarters, performance can be affected if many concurrent customer creation calls are made.

If the **Create customer in async mode** option is set to **Yes** in the store's functionality profile (**Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**), Real-time Service calls aren't used to create customer records in the channel database. The async customer creation mode doesn't affect the performance of Commerce headquarters. A temporary globally unique identifier (GUID) is assigned to every new async customer record and used as the customer account ID. This GUID isn't shown to point of sale (POS) users. Instead, those users will see **Pending sync** as the customer account ID.

> [!IMPORTANT]
> Whenever the POS goes offline, the system automatically creates customers asynchronously, even if the async customer creation mode is disabled. Therefore, regardless of your selection between sync and async customer creation, Commerce headquarters administrators must create and schedule a recurring batch job for the **P-job**, the **Synchronize customers and business partners from async mode** job, and the **1010** job, so that any async customers are converted to sync customers in Commerce headquarters.

## Async customer limitations

The async customer functionality currently has the following limitations:

- Loyalty cards can't be issued to async customers unless the new customer account ID has been synced back to the channel.

## Async customer enhancements

To help organizations in using asynchronous mode of customer management and reduce real-time communications with Headquarters, there have been numerous enhancements in bringing parity between synchronous and asynchronous mode of customer management in channels. 

To help organizations in using asynchronous mode of customer management and reduce real-time communications with Headquarters, there have been numerous enhancements in bringing parity between synchronous and asynchronous mode of customer management in channels. 

| Feature  Enhancement | Dynamics 365 Commerce Version   | Feature Details |
| ------------- | -------------- | -------------- |
|Performance improvements in retrieving customer information from channel database.  | 10.0.20 onwards |Customer entity is split into lightweight entities, and service retrieves only necessary information from channel database to improve performance.   |
|Ability to create address asynchronously during checkout.  |10.0.22 onwards  | <p>**Feature switch**: Enable asynchronous creation for customer addresses.</br></br>**Feature details**:<ul><li>Ability to add addresses without making real-time-service calls to headquarters.</li><li>Ability to identify addresses uniquely in Channel DB, without RECID.</li><li>Tracking timestamps for address creation.</li><li>Synchronize addresses in headquarters.</li></ul>This feature affects both sync and async customers. In addition to create addresses asynchronously, to also edit addresses asynchronously Editing customers in asynchronous mode feature must be enabled.</p> |
|Enable parity between synchronous and asynchronous customer creation.   |10.0.24 onwards  | <p>**Feature switch:** Enable enhanced async customer creation.</br></br>**Feature details:**<ul><li>Ability to capture additional info, such as title, affiliations from default customer, and second contact info (phone, email), while creating customers asynchronously.</li></ul></p>  |
|E-commerce user-friendly messages.  |10.0.28 onwards  | Enhancements to improve user friendly messages when user is unable to edit information immediately, while synchronization is in process. These enhancements can be enabled via the **Allow certain UI elements to be unmodifiable by an async customer** setting in site builder  at **Site settings \> Extensions**.    |
| Ability to edit customer information asynchronously. |10.0.29 onwards  | <p>**Feature switch**: Enable editing customers in asynchronous mode</br></br>**Feature details**:<ul><li>Ability to edit customers data asynchronously.</li></ul>For any issues faced in using editing customer information asynchronously, refer to [Async mode frequently asked questions](async-mode-faq.md).</p>|

### Feature switches hierarchy

As described above, there are multiple feature management switches to enable complete set of enhancements related to async customer. However, one particular feature, i.e. **Enable editing customers in asynchronous mode** needs the following features to be enabled first: 

- Performance improvements for customer orders and customer transactions. This feature has been made as mandatory since 10.0.28 release. 
- Enable enhanced async customer creation
- Enable asynchronous creation for customer addresses

Refer to **[Async mode frequently asked questions](/commerce/async-mode-faq.md)** for any questions related to troubleshooting. 

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
