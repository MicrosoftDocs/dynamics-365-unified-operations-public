---
# required metadata

title: Customer management in stores
description: This topic explains how retailers can enable customer management capabilities at the point of sale (POS) in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 03/05/2021
ms.topic: article
ms.prod: 
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

[!include [banner](includes/banner.md)]

This topic explains how retailers can enable customer management capabilities at the point of sale (POS) in Microsoft Dynamics 365 Commerce.

It's important that store associates can create and edit customer records at the POS. In that way, they can capture any updates to customer information such as the email address, phone number, and address. This information is helpful in downstream systems such as marketing, because the effectiveness of those systems depends on the accuracy of their customer data.

Sales associates can trigger the customer creation workflow from two POS entry points. They can select a button that is mapped to the **Customer add** operation, or they can select **Create customer** on the app bar on the search results page. In both cases, the **New customer** dialog box appears, where sales associates can enter required customer details, such as the customer's name, email address, phone number, address, and any additional information that is relevant to the business. That additional information can be captured by using the customer attributes that are associated with the customer. For more information about customer attributes, see [Customer attributes](dev-itpro/customer-attributes.md).

Sales associates can also capture secondary email addresses and phone numbers. Additionally, they can capture the customer's preference about receiving marketing information via any of those secondary email addresses or phone numbers. To enable this capability, retailers must turn on the **Capture multiple emails and phone numbers and consent for marketing on these contacts** feature in the **Feature management** workspace in Commerce headquarters (**Systems administration \> Workspaces \> Feature management**).

## Default customer properties

Retailers can use the **All stores** page in Commerce headquarters (**Retail and Commerce \> Channels \> Stores**) to associate a default customer with each store. Commerce then copies the properties that are defined for the default customer to all new customer records that are created. For example, the **Create customer** dialog box shows properties that are inherited from the default customer that is associated with the store. Those properties include the customer type, customer group, receipt preference, currency, and language. Any affiliations (groupings of customers) are also inherited from the default customer. However, financial dimensions are inherited from the customer group that is associated with the default customer, not from the default customer itself.

Sales associates can capture multiple addresses for a customer. The customer's name and phone number are inherited from the contact information that is associated with each address. The **Addresses** FastTab of a customer record includes a **Purpose** field that sales associates can edit. If the customer type is **Person**, the default value is **Home**. If the customer type is **Organization**, the default value is **Business**. Other values that this field supports include **Home**, **Office**, and **Post box**. The value of the **Country** field for an address is inherited from the primary address that is specified on the **Operating unit** page in Commerce headquarters at **Organization administration \> Organizations \> Operating units**.

## Sync customers and Async customers

In Commerce, there are two modes of customer creation: Synchronous (or Sync) and Asynchronous (or Async). By default, customers are created synchronously. In other words, they are created in Commerce headquarters in real time. The Sync customer creation mode is beneficial because new customers are immediately searchable across channels. However, it also has a drawback. Because it generates [Commerce Data Exchange: Real-time Service](dev-itpro/define-retail-channel-communications-cdx.md#realtime-service) calls to Commerce headquarters, performance can be affected if many concurrent customer creation calls are made.

If the **Create customer in async mode** option is set to **Yes** in the store's functionality profile (**Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**), Real-time Service calls aren't used to create customer records in the channel database. The Async customer creation mode doesn't affect the performance of Commerce headquarters. A temporary globally unique identifier (GUID) is assigned to every new Async customer record and used as the customer account ID. This GUID isn't shown to POS users. Instead, those users will see **Pending sync** as the customer account ID. Although this configuration forces customers to be created asynchronously, note that edits to customer records are always done synchronously.

### Convert Async customers to Sync customers

To convert Async customers to Sync customers, you must first run the P-job to send the Async customers to Commerce headquarters. Then run the **Synchronize customers and business partners from async mode** job to create customer account IDs. Finally, run the **1010** job to sync the new customer account IDs to the channels.

### Async customer limitations

The Async customer functionality currently has the following limitations:

- Async customer records can't be edited unless the customer has been created in Commerce headquarters and the new customer account ID has been synced back to the channel.
- Affiliations can't be associated with Async customers. Therefore, new Async customers don't inherit affiliations from the default customer.
- Loyalty cards can't be issued to Async customers unless the new customer account ID has been synced back to the channel.
- Secondary email addresses and phone numbers can't be captured for Async customers.

### Customer creation in POS offline mode

If the POS goes offline while the Async customer creation mode is enabled, new customer records are created asynchronously. If the POS goes offline while the Async customer creation mode is disabled, the system automatically switches to the Async customer creation mode. In other words, customer records might be created asynchronously even if the Async customer creation mode is disabled. Therefore, Commerce headquarters administrators must create and schedule a recurring batch job for the P-job, the **Synchronize customers and business partners from async mode** job, and the **1010** job, so that any Async customers are converted to Sync customers in Commerce headquarters.

> [!NOTE]
> If the **Filter shared customer data tables** option is set to **Yes** on the **Commerce channel schema** page (**Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Channel database group**), customer records aren't created in POS offline mode. For more information, see [Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion).

## Additional resources

[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
