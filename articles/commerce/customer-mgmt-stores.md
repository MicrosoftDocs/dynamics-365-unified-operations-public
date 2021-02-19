---
# required metadata

title: Customer management in stores
description: This topic explains how retailers can enable customer management capabilities at the point of sale (POS) in Dynamics 365 Commerce.
author: josaw1
manager: AnnBe
ms.date: 02/23/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form: RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Customer management in stores

[!include [banner](../../includes/banner.md)]

This topic explains how retailers can enable customer management capabilities at the point of sale (POS) in Dynamics 365 Commerce.

It's important for store associates to have the ability to create and edit customer records that they can capture any updates to customer information such as email, phone number, and address. This information is helpful in downstream systems such as marketing because their effectiveness depends on the accuracy of their customer data.

Sales associates can trigger the customer creation workflow from two POS entry points: by selecting a button mapped to the "Customer add" operation, or from the search results page by selecting **Create customer** on the app bar. This opens a **New customer** form where a sales associate can enter required customer details such as name, email, phone number, address, and any other information that is relevant to the business. This additional data can be captured using the customer attributes associated to the customer. For more information about customer attributes, see [Customer attributes](dev-itpro/customer-attributes.md).

Sales associates can also capture secondary email and phone numbers along with the customer's intent to receive marketing information on any of these emails or phone numbers. To enable this capability, retailers must enable the **Capture multiple emails and phone numbers and consent for marketing on these contacts** feature in Commerce headquarters at **Systems administration \> Workspaces**.

## Default customer properties

The "all stores" form in Commerce headquarters (**Retail and Commerce \> Channels \> Stores**) allows retailers to associate a default customer with each store. Commerce then copies properties defined for the default customer to newly-created customer records. For example, the **Create customer** form displays properties such as customer type, customer group, receipt preference, currency, and language which are inherited from the default customer associated with the store. Any affiliations (groupings of customers) are also inherited from the default customer. However, financial dimensions are instead inherited from the customer group associated with the default customer, and not from the default customer record. 

A sales associates can capture multiple addresses for a customer and the customer's name and phone number get defaulted on the contact information associated with the address. The address form displays has a **Purpose** property that can be modified by a sales associate. This property supports values such as home, office, and post box. The default value is "Home" if the customer type is "Person," and "Business" if the customer type is "Organization." The value for the address form property **Country** is inherited from the primary address specified on the operating unit form in headquarters.

## Sync and Async customers

In Commerce, there are two modes of customer creation: Synchronous (also know as "Sync") and Asynchronous (also known as "Async"). By default, customers are created synchronously (in other words, created in Commerce headquarters in real time). This is functionally beneficial because a newly-created customer is immediately searchable across channels. However, there is a drawback to this approach since creating customers synchronously generates Real Time Service (RTS) calls to headquarters, which can impact performance if a large number of customer creation calls are made concurrently. 

If the **Create customer in async mode** setting is enabled on the functionality profile of the store (**Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**), customer records are only created in the channel database without RTS calls. So creating customers in Async mode does not impact headquarters performance. Each newly-created Async customer record get a temporary GUID that is used as the account ID. This ID is not shown to POS users, who will see instead "Pending sync" as the customer ID. Note that although this configuration forces Async mode customer creation, customer record edits are always done synchronously.

### Convert Async customers to Sync customers

To convert Async customers to Sync customers, the Async customer is sent to headquarters by running the **P-Job**, while the customer account ID is created by running the **Synchronize customers and business partners from async mode** job. Newly-created customer account IDs are synchronized to channels by running the **1010 - Customer job**.

### Async customer limitations

The Async customer functionality currently has the following limitations.

- The Async customer record cannot be edited unless the customer is created in headquarters and the new customer ID is synchronized back to the channel.
- Affiliations cannot be associated with Async customers, so newly-created Async customers do not inherit affiliations from the default customer.
- Loyalty cards cannot be issued to the Async customers unless the new customer account ID is synchronized back to the channel.
- Secondary emails and phone numbers cannot be captured for Async customers.

### Customer creation in POS offline mode

If the POS goes offline with the Sync customer creation mode enabled, the system then automatically switches to Async customer creation. If the POS goes offline with the Async customer creation mode enabled, the customer record is then created in Async mode. Since there may be customer records that get created asynchronously even if the Async customer creation mode is not enabled, headquarters administrators must ensure that they have created and scheduled a recurring batch job for **P-job**, **Synchronize customers and business partners from async mode**, and **1010 - Customer job** jobs to convert these Async customers to synchronized headquarters customers.

> [!NOTE]
> If the **Filter shared customer data tables** setting is enabled, customer records are not created in POS offline mode. For more information, see [Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion).

## Additional resources

[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
