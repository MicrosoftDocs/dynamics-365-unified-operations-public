---
# required metadata

title: Integrated vendor master
description: This topic describes vendor data integration between Finance and Operations apps and Common Data Service.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 07/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2019-07-15

---

# Integrated vendor master

[!include [banner](../../includes/banner.md)]

[!include [preview-banner](../../includes/preview-banner.md)]

The term vendor refers to a supplier organization or a sole proprietor who supplies goods or services to the business. Vendor is an established concept in D365 Supply Chain. But Customer Engagement applications doesn’t have an explicit vendor concept and so, Account/Contact entity is overloaded to store vendor information. With integrated vendor master, an explicit vendor concept  is introduced in customer engagement applications. Businesses can either choose the new vendor concept or use Account/Contact entity for vendors. Dual-write supports both these designs. Therefore, you can enable either of the designs, depending on your business scenario.
With both designs, the vendor data is integrated between Supply chain, Sales, Field Service and Power Portal applications and becomes available for Supply chain workflows like purchase requisition, purchase orders etc. 


### Vendor data flow

If you want to isolate the vendor information from Account or contact entities in Common Data Service, then you can use the *new vendor model*.

![Vendor data flow](media/dual-write-vendor-data-flow.png)

If you want to continue to use the Account and contact entity for storing vendor information, then you can use the extended vendor design. But for that you need to configure the vendor workflows coming from dual-write application orchestration solution package. See how to [switch between vendor designs](vendor-switching)

![Extended vendor data flow](media/dual-write-vendor-detail.jpg)

**Tip**

If you are using power portals for self-serving vendors, the vendor information can directly flow to Finance and operations applications. 

## Templates

Vendor data includes all information about the vendor, such as the vendor group, addresses, contact information, payment profile, and invoice profile. A collection of entity maps work together during vendor data interaction, as shown in the following table.

Finance and Operations apps | Other Dynamics 365 apps         | Description
----------------------------|---------------------------------|------------
Vendor V2               | Account | Businesses that use the Account entity to store vendor information can continue to use it in the same way. They can also take advantage of the explicit vendor functionality that is coming because of Finance and Operations apps integration.
Vendor V2               | Msdyn\_vendors | Businesses that use a custom solution for vendors can take advantage of the out-of-box vendor concept that is being introduced in Common Data Service because of Finance and Operations apps integration. 
Vendor groups | msdyn_vendorgroups | This template synchronizes vendor group information.
Vendor payment method | msdyn_vendorpaymentmethods | This template synchronizes vendor payment method information.
CDS Contacts V2             | contacts                        | The [contacts](customer-mapping.md#cds-contacts-v2-to-contacts) template synchronizes all primary, secondary, and tertiary contact information, for both customers and vendors.
Payment schedule lines      | msdyn_paymentschedulelines      | The [payment schedule lines](customer-mapping.md#payment-schedule-lines-to-msdyn_paymentschedulelines) template synchronizes reference data for customers and vendors.
Payment schedule            | msdyn_paymentschedules          | The [payment schedules](customer-mapping.md#payment-schedule-to-msdyn_paymentschedules) template synchronizes payment schedule reference data, for both customers and vendors.
Payment day lines CDS V2    | msdyn_paymentdaylines           | The [payment day lines](customer-mapping.md#payment-day-lines-cds-v2-to-msdyn_paymentdaylines) template synchronizes payment day lines reference data for customers and vendors.
Payment days CDS            | msdyn_paymentdays               | The [payment days](customer-mapping.md#payment-days-cds-to-msdyn_paymentdays) template synchronizes payment days reference data, for both customers and vendors.
Terms of payment            | msdyn_paymentterms              | The [terms of payment](customer-mapping.md#terms-of-payment-to-msdyn_paymentterms) template synchronizes payment terms reference data, for both customers and vendors.
Name affixes                | msdyn_nameaffixes               | The [name affixes](customer-mapping.md#name-affixes-to-msdyn_nameaffixes) template synchronizes name affixes reference data, for both customers and vendors.

[!include [symbols](../../includes/dual-write-symbols.md)]

[!include [Vendors](includes/VendorsV2-msdyn-vendors.md)]

[!include [Vendor groups](includes/VendVendorGroup-msdyn-vendorgroups.md)]

[!include [Vendor payment methods](includes/VendorPaymentMethod-msdyn-vendorpaymentmethods.md)]
