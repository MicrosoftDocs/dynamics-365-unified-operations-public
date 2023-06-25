---
# required metadata

title: Asynchronous customer creation mode
description: This article describes the asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 10/18/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2021-12-17

---

# Asynchronous customer creation mode

[!include [banner](includes/banner.md)]

This article describes the asynchronous customer creation mode in Microsoft Dynamics 365 Commerce.

In Commerce, there are two modes of customer creation: synchronous (or sync) and asynchronous (or async). By default, customers are created synchronously. In other words, they're created in Commerce headquarters in real time. The sync customer creation mode is beneficial because new customers are immediately searchable across channels. However, it also has a drawback. Because it generates [Commerce Data Exchange: Real-time Service](dev-itpro/define-retail-channel-communications-cdx.md#realtime-service) calls to Commerce headquarters, performance can be affected if many concurrent customer creation calls are made.

If the **Create customer in async mode** option is set to **Yes** in the store's functionality profile (**Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**), Real-time Service calls aren't used to create customer records in the channel database. The async customer creation mode doesn't affect the performance of Commerce headquarters. A temporary globally unique identifier (GUID) is assigned to every new async customer record and used as the customer account ID. This GUID isn't shown to point of sale (POS) users. Instead, those users will see **Pending sync** as the customer account ID.

> [!IMPORTANT]
> Whenever the POS goes offline, the system automatically creates customers asynchronously, even if the async customer creation mode is disabled. Similarly, the system automatically creates customers asynchronously when an RTS call fails with a communication exception. Therefore, regardless of your selection between sync and async customer creation, Commerce headquarters administrators must create and schedule a recurring batch job for the **P-job**, the **Synchronize customers and business partners from async mode** job, and the **1010** job, so that any async customers are converted to sync customers in Commerce headquarters.

## Async customer limitations

The async customer functionality currently has the following limitation:

- Loyalty cards can't be issued to async customers unless the new customer account ID has been synced back to the channel.

## Async customer enhancements

To help organizations use async customer creation mode to manage customers, and to help reduce real-time communications with Commerce headquarters, the following enhancements have been rolled out to bring parity between sync and async modes in channels. 

| Feature enhancement | Commerce version | Feature details |
|---|---|---|
| Performance improvements when customer information is retrieved from the channel database | 10.0.20 and later | To help improve performance, the customer entity is split into smaller entities. The system then retrieves only the required information from the channel database. |
| Ability to create address asynchronously during checkout | 10.0.22 and later | <p>Feature switch: **Enable asynchronous creation for customer addresses**</p><p>Feature details:</p><ul><li>Ability to add addresses without making real-time service calls to Commerce headquarters</li><li>Ability to uniquely identify addresses in the channel database without using a record ID (**RecId** value)</li><li>Tracking timestamps for address creation</li><li>Synchronization of addresses in Commerce headquarters</li></ul><p>This feature affects both sync customers and async customers. To edit addresses asynchronously in addition to creating them asynchronously, you must enable the **Editing customers in asynchronous mode** feature.</p> |
| Enable parity between synchronous and asynchronous customer creation. | 10.0.24 and later | <p>Feature switch: **Enable enhanced async customer creation**</p><p>Feature details: Ability to capture additional information, such as the title, affiliations from the default customer, and secondary contact information (phone number and email address), while you create customers asynchronously</p> |
| User-friendly error messages | 10.0.28 and later | These enhancements help improve user-friendly error messages if a user can't immediately edit information while synchronization is in process. You enable these enhancements by using the **Allow certain UI elements to be unmodifiable by an async customer** setting at **Site settings \> Extensions** in Commerce site builder. |
| Ability to edit customer information asynchronously | 10.0.29 and later | <p>Feature switch: **Enable editing customers in asynchronous mode**</p><p>Feature details: Ability to edit customer data asynchronously</p><p>For answers to common questions about issues that are related to editing customer information asynchronously, see [Asynchronous customer creation mode FAQ](async-customer-mode-faq.md).</p> |
| Ability to audit synchronization of customer management operations | 10.0.31 and later | This enhancement lets users audit the synchronization of customer management operations in Commerce headquarters. It also lets users make changes if they are needed and synchronize the data. |

### Feature switch hierarchy

Because of the hierarchy of feature switches, before you enable the **Enable editing customers in asynchronous mode** feature, you must enable the following features: 

- **Performance improvements for customer orders and customer transactions** – This feature has been mandatory since the Commerce version 10.0.28 release. 
- **Enable enhanced async customer creation**
- **Enable asynchronous creation for customer addresses**

After the feature's enabled, run the **Channel configuration scheduler** job (by default, the **1070** scheduler job).

For answers to common troubleshooting questions, see [Asynchronous customer creation mode FAQ](async-customer-mode-faq.md). 

After you enable the previously mentioned features, you must schedule a recurring batch job for the **P-job**, the **Synchronize customers and channel requests** job, and the **1010** job, so that any async customers are converted to sync customers in Commerce headquarters.

### Customer creation in POS offline mode

As was mentioned earlier, whenever the POS goes offline, the system automatically creates customers asynchronously, even if the async customer creation mode is disabled. Therefore, Commerce headquarters administrators must create and schedule a recurring batch job for the **P-job**, the **Synchronize customers and channel requests** job, and the **1010** job, so that any async customers are converted to sync customers in Commerce headquarters.

> [!NOTE]
> If the **Filter shared customer data tables** option is set to **Yes** on the **Commerce channel schema** page (**Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group**), customer records aren't created in POS offline mode. For more information, see [Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion).

## Additional resources

[Customer management in stores](customer-mgmt-stores.md)

[Convert asynchronous customers to synchronous customers](convert-async-to-sync.md)

[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
