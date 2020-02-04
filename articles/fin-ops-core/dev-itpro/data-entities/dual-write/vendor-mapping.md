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

The term *vendor* refers to a supplier organization or a sole proprietor that is part of the supply chain process, and that supplies goods for the business. Although *vendor* is an established concept in Finance and Operations apps, a vendor concept doesn't exist in other Dynamics 365 apps. Instead, some businesses overload the Account entity to store both customer information and vendor information. Other businesses use a custom vendor concept. Common Data Service integration supports both these designs. Therefore, you can enable either of the designs, depending on your business scenario.

Integration of vendor data between Finance and Operations apps and other Dynamics 365 apps lets you multi-master the data. Regardless of where the vendor data originates, it's integrated behind the scenes across application boundaries and infrastructure differences. 

### Vendor data flow

If you want to use other Dynamics 365 apps for vendor mastering, and you want to isolate vendor information from customer information, you can use the new vendor design.

![Vendor data flow](media/dual-write-vendor-data-flow.png)

If you want to use other Dynamics 365 apps for vendor mastering, and you want to continue to use the Account entity to store vendor information, you can use the new extended vendor design. In this design, extended vendor information, such as the vendor group and vendor posting profile, are stored in the vendor detail.

![Extended vendor data flow](media/dual-write-vendor-detail.jpg)

Vendor contact information resembles customer contact information. Behind the scenes, the contact person's information is stored and retrieved from the same entities.

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
