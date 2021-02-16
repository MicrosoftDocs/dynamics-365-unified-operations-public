---
# required metadata

title: Customer management in stores
description: This document explains how the retailers can enable the customer management capabilities in the Point of Sale
author: josaw1
manager: AnnBe
ms.date: 01/20/2021
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


This document explains how the retailers can enable the customer management capabilities in the Point of Sale (aka. POS). The ability to create and edit customers is important for a store associate so that they can capture any updates to the customer information such as email, phone number, address etc. This information is helpful in the downstream systems such as Marketing because their effectiveness depends on the accuracy of the customer data.

The sales associates can trigger the customer creation workflow through two entry points i.e. either using a button on the POS which is mapped to the "Customer add" operation, or from the search results page by clicking on the "Create customer" button on the app bar. This opens up the "New customer" form where the sales associate can capture the required details about the customer such name, email, phone number, address, and any other information that is relevant to the business. This additional data can be captured using the customer attributes associated to the customer. To learn more about customer attributes, please use the link: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/customer-attributes

The associates can also capture secondary email and phone numbers along with the customer's intent to receive marketing information on any of these emails or phone numbers. To enable this capability, the retailers must turn on the feature titled "Capture multiple emails and phone numbers and consent for marketing on these contacts" from the Feature management workspace.

## Default customer properties

The "All stores" form in the headquarter (HQ) application allows the retailers to associate a default customer to each store. The system uses the properties defined on this default customer to copy on the newly created customers. For e.g. the customer create form displays properties such as Customer type, Customer group, receipt preference, currency and language which get defaulted from the default customer associated to the store. Additionally, the affiliations also get copied from this default customer. However, the financial dimensions are copied from the Customer group associated to the default customer and not from the default customer itself. 

The sales associates can capture multiple addresses for the customer and the customer's name and phone number get defaulted on the contact information associated with the address. The address form displays a field as "Purpose" which can be modified by the sales associate. This can support values such as Home, office, postbox etc. This is defaulted to "Home" if the customer is of type "Person" and "Business" if the customer is of type "Organization". Additionally, the address form shows a field "Country" which is defaulted from the primary address of the Operating unit (Operating unit form in HQ)

## Sync vs Async customers

There are two modes of customer creation i.e. Synchronous customer (aka Sync) and 'Asynchronous (aka Async) customer. By default, we create the customer synchronously i.e. the customers get created in the HQ in real time. This is functionally great because the newly created customer is searchable across the channels immediately. However, the drawback of this approach is that it makes a Real Time Service (RTS) call to the HQ, so large number of concurrent customer creation calls can impact the HQ performance. 

If the Async customer creation is enabled the "Create customer in async mode" configuration on functionality profile of the store is turned on, the customers are created only in the channel database and does not make a RTS call. Thus, the store customer creation activities does not impact HQ performance. This newly created customer gets a temporary GUID as the account ID which is not shown to the POS users. Instead, the POS shows "Pending sync" as the customer ID. Please note that this configuration only forces the customer creation in Async mode, but the customer edits are always done synchronously.

### Steps to convert Async customer to HQ customer

The async customer is sent to HQ using the 'P-Job' while the customer account ID is created by running the 'Synchronize customers and business partners from async mode" job. This newly created customer account ID is synced to the channels by running the 1010 - Customer job.

### Async customer limitations
The Async customer has the following limitations. But this will be removed in the future releases.

- The Async customer cannot be edited, unless the customer is created in HQ and the new customer ID is synced back to the channel
- Affiliations cannot be associated to the Async customers, thus the newly created Async customers do not get the affiliations associated from the default customer
- Loyalty card cannot be issued to the Async customers, unless the new customer account id is synced back to the channel
- Secondary emails and phone numbers cannot be captured for the Async customer


### Customer creation in POS offline mode

If the POS goes offline, and the Sync customer creation flow is enabled, then the system automatically switches to the Async customer creation. If the Async customer is enabled, and the POS goes offline, then the customer gets created in the Async mode. Since there could be some customers who get created asynchronously, even if the Async customer creation is not enabled, thus the admins need to ensure that they have created a recurring batch job scheduled for P-job, 'Synchronize customers and business partners from async mode' and '1010' jobs to convert these async customers to HQ customers.

> [!NOTE]
> The customer is not created in POS offline mode only if 'Filter shared customer data tables' configuration is enabled. You can read more about this configuration here: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/implementation-considerations-cdx#offline-data-exclusion
