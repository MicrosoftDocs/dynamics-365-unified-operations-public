---
# required metadata

title: Vendor data flow
description: 
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

## Integrated Vendor Master

*Vendor* refers to a supplier organization or a sole proprietor that is part of the supply chain process and supplies goods for the business. *Vendor* is an established concept in Finance and Operations. But in Customer Engagement, the *Vendor* concept does not exist. Some businesses overload the *Account* entity to store both customer and vendor information. Other uses a custom *Vendor* concept. Common Data Service (CDS) integration supports both these designs. You can choose to enable either of the designs based on your business scenario. Integrating the vendor data between Finance and Operations and Customer Engagement gives you the capability to multi-master vendor data. Regardless of where the vendor data originates, it is integrated behind the scenes across application boundaries and infrastructure differences. 

### Vendor data flow

If you want to use Customer Engagement for vendor-mastering and want to isolate vendor information from customers, then you can use the new vendor design.

![vendor data flow](media/dual-write-vendor-data-flow.png)

If you want to use Customer Engagement for vendor mastering and you want to continue to use the **Account** entity for storing vendor information, you can use the new extended vendor design. In this design, extended vendor information like vendor group and vendor post profile are stored in the **vendor detail**.

![extended vender design](media/dual-write-vendor-detail.png)

Vendor contact information is similar to the customer contact information. Behind the scenes the contact person information is stored and retrieved from same entities.

## Templates

Vendor data includes all information about the vendor like vendor group, addresses, contact information, payment profile, and invoice profile. A collection of entity maps works together in vendor data interaction as listed below.

Finance and Operations  | Customer Engagement Application
------------------------|---------------------------------
Vendor V2               | Account
Vendor V2               | Msdyn\_vendors
CDS Contacts V2         | Contact
Vendor groups           | Msdyn\_vendorgroups
Vendor Payment Method   | Msdyn\_vendorpaymentmethods
Payment Schedule        | Msdyn\_paymentschedules
Payment Schedule        | Msdyn\_paymentschedulelines
Payment day CDS         | Msdyn\_paymentdays
Payment day lines CDS   | Msdyn\_paymentdaylines
Terms of Payment        | Msdyn\_paymentterms
Name Affixes            | Msdyn\_nameaffixes

## Vendor V2 and Account 

Businesses using the **Account** entity to store vendor information can continue to use it in the same way and also take advantage of the explicit vendor functionality coming due to Finance and Operations integration.

## Vendor V2 and Msdyn\_vendors

Businesses using a custom solution for vendors can take advantage of the out-of-the-box vendor concept introduced in CDS due to Finance and Operations integration. 

![vendor mappings](media/dual-write-vendors-1.png)

![vendor mappings](media/dual-write-vendors-2.png)

![vendor mappings](media/dual-write-vendors-3.png)

## Contacts

Synchronizes all primary, secondary, and tertiary contact information of both customers and vendors between Finance and Operations and CE. For the entity map details, see [Integrated Customer Master](dual-write-customer.md#contacts).

## Vendor Groups

Synchronizes vendor group information between Finance and Operations and Customer Engagement.

![vendor groups mappings](media/dual-write-vendor-groups.png)

### Vendor Payment Method

Synchronizes vendor payment method information between Finance and Operations and Customer Engagement.

![vendor payment method mappings](media/dual-write-vendor-payment-method.png)
