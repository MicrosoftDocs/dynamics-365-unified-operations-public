---
title: Customer management in stores
description: This article explains how retailers can enable customer management capabilities at the point of sale (POS) in Microsoft Dynamics 365 Commerce.
author: gvrmohanreddy
ms.date: 12/10/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14
ms.search.industry: retail
ms.search.form: RetailOperations
---

# Customer management in stores

[!include [banner](includes/banner.md)]

This article explains how retailers can enable customer management capabilities at the point of sale (POS) in Microsoft Dynamics 365 Commerce.

It's important that store associates can create and edit customer records at the POS. In that way, they can capture any updates to customer information such as the email address, phone number, and address. This information is helpful in downstream systems such as marketing, because the effectiveness of those systems depends on the accuracy of their customer data.

Sales associates can trigger the customer creation workflow from two POS entry points. They can select a button that is mapped to the **Customer add** operation, or they can select **Create customer** on the app bar on the search results page. In both cases, the **New customer** dialog box appears, where sales associates can enter required customer details, such as the customer's name, email address, phone number, address, and any additional information that is relevant to the business. That additional information can be captured by using the customer attributes that are associated with the customer. For more information about customer attributes, see [Customer attributes](dev-itpro/customer-attributes.md).

Sales associates can also capture secondary email addresses and phone numbers. Additionally, they can capture the customer's preference about receiving marketing information via any of those secondary email addresses or phone numbers. To enable this capability, retailers must turn on the **Capture multiple emails and phone numbers and consent for marketing on these contacts** feature in the **Feature management** workspace in Commerce headquarters (**Systems administration \> Workspaces \> Feature management**).

## Default customer properties

Retailers can use the **All stores** page in Commerce headquarters (**Retail and Commerce \> Channels \> Stores**) to associate a default customer with each store. Commerce then copies the properties that are defined for the default customer to all new customer records that are created. For example, the **Create customer** dialog box shows properties that are inherited from the default customer that is associated with the store. Those properties include the **customer type**, **customer group**, **receipt option**, **receipt email**, **currency**, and **language**. Any **affiliations** (groupings of customers) are also inherited from the default customer. However, **financial dimensions** are inherited from the customer group that is associated with the default customer, not from the default customer itself.

> [!NOTE]
> The **receipt email** value gets copied from the default customer only if the receipt email ID is not provided for the newly created customers. This means that if the receipt email ID is present on the default customer, then all the customers created from the e-commerce site will get the same receipt email ID as there is no user interface to capture the receipt email ID from the customer. We recommend that you leave the **receipt email** field blank for the default customer of the store and use it only if you have a business process that depends on a receipt email address being present. 

Sales associates can capture multiple addresses for a customer. The customer's name and phone number are inherited from the contact information that is associated with each address. The **Addresses** FastTab of a customer record includes a **Purpose** field that sales associates can edit. If the customer type is **Person**, the default value is **Home**. If the customer type is **Organization**, the default value is **Business**. Other values that this field supports include **Home**, **Office**, and **Post box**. The value of the **Country** field for an address is inherited from the primary address that is specified on the **Operating unit** page in Commerce headquarters at **Organization administration \> Organizations \> Operating units**.

## Marketing Opt-in feature

The feature **Capture multiple emails and phone numbers and consent for marketing on these contacts** has been enabled by default in 10.0.36. This feature allows sales associates to capture multiple emails and phone numbers for customers on POS along with the consent for marketing information on these contacts.

> [!NOTE]
> This feature will cause UI change for customer creation or editing. Before enabling this feature, customer will only allow to have one email address and one phone number. After enabling this feature, customer can add multiple email addresses and phone numbers by clicking the **+ Add an email** or **+ Add a phone number** button. The UI display of existing email address and phone number will also change to list of tiles. Customer can edit the existing email address and phone number by clicking the tiles and edit in the pop-up dialog. For each contact, customer can determine whether to use it for marketing opt-in.

This feature **does not work for Async customers**. If the asynchronous customer creation functionality is enabled, these capabilities will not be available.

## Additional resources

[Asynchronous customer creation mode](async-customer-mode.md)

[Convert asynchronous customers to synchronous customers](convert-async-to-sync.md)

[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
