---
# required metadata

title: What's new or changed in dual-write
description:  
author: robinarh
manager: AnnBe
ms.date: 06/30/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang:
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2020-07-31
ms.dyn365.ops.version: 10.0.8

---

# What's new or changed in dual-write

[!include [banner](../../includes/banner.md)]

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between model-driven apps in Microsoft Dynamics 365 and Finance and Operations apps. To get started with dual-write, see the [Dual-write home page](dual-write-home-page.md).

The following sections list the features that are included in dual-write releases. Dual-write features and changes are announced in the [release plans](https://go.microsoft.com/fwlink/?linkid=2010158).

+ [Data in Common Data Service – Phase 1](https://docs.microsoft.com/en-us/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/data-common-data-service-phase-1)
+ [Data in Common Data Service – phase 1 & 2](https://docs.microsoft.com/en-us/dynamics365-release-plan/2020wave1/finance-operations-crossapp-capabilities/data-common-data-service-phase-1-2)
+ [Finance and Operations data in Common Data Service – Phase 3](https://docs.microsoft.com/en-us/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/finance-operations-data-common-data-service-phase-3)

## July 2020 release

The July 2020 release is based on [dual-write core version 10.0.18](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.msft-d365-dual-write?tab=Overview) and it contains the functions in the following table. If you are using dual-write core version 1.0.16, you should upgrade to 10.0.18. 

| Area | Feature |Status |
|------|---------|-------|
| Mapping | Lead qualification process in Sales is now company striped.<br>Dynamics 365 Sales users can create a lead, qualify the lead to an opportunity, convert an opportunity in to a quote, activate a quote, and create an order. This end-to-end process was broken in dual-write due to lack of company striping on the **Lead** entity. We implemented company striping on the **Lead** entity, which cascades the company to the underlying **Account** and **Opportunity** entities. Thus the application behavior is restored to support the end-to-end process. During the **Lead** qualification process, the **Contact** entity is not company striped. This design support the **Party** entity model which is due in Septemper 2020. If you are interested in learning about the **Party** and **GlobalAddressBook** model for dual-write, please join the dual-write Yammer group. | Preview |
| Mapping | [Map the state transitions between **Order** in Dynamics 365 Sales and **SalesOrder** in Dynamics 365 Supply Chain Management](sales-status-map.md).<br>The **Order** form in Dynamics 365 Sales is always set to **Active**. To create state transitions for Dynamics 365 Sales, we introduced the **ProcessingStatus** field. |   Preview   |  
| Data conversion | [Money to decimal data type conversion](currrency-decimal-places.md) provides extended decimal support in Common Data Service to support dual-write.<br>Common Data Service environments are limited to 4 decimal places for currency and 10 decimal places for exchange rates. Finance and Operations apps support more decimal places than Common Data Service. You can now opt-in to extend the decimal support in Common Data Service to help ensure there is no loss of decimal place data when using dual-write. | Preview |
| Security | Security role for company and currency exchange.<br>Company and currency exchange entities are global in nature and all dual-write users require read access to these 2 entities. In order to simplify the experience, we have releasing a new security role called "". Each dual-write user must be added to this security role.   | Preview |


## May 2020 release

The May 2020 release of dual-write orchestration package (version 2.0.777.353) contains the features and bug fixes listed in the following table.

| Area | Feature |Status |
|------|---------|-------|
| Mapping | Ability to lookup on-hand inventory and available-to-promise dates on forms in model-driven apps in Dynamics 365. | General availability |
| Data conversion | 	When unit conversions take place in Finance and Operations app at the quote line and order line, the model-driven app in Dynamics 365 honors the unit conversions and reflects the respective changes to unit and price in model-driven app quote detail and order detail. | General availability |
|  | 	When you try to change the currency in the Finance and Operations app for an existing quote or order, the change fails.   | General availability |
| Mapping | Bring attribute parity in **Account** and **Contact** forms in model-driven apps for B2B and B2C customers.  | General availability |
| Mapping | Don’t duplicate an address in the Finance and Operations app when there is a create or update action on model-driven app quote or order.  | General availability |
| Mapping | Support for **SalesTaxGroup** in **Account** and **Contact** forms for B2B and B2C customers. | General availability |
| Mapping | Allow creation of a sellable contact through **Quick Create: Contact** form in model-driven apps. | General availability |
| Mapping | Enable quote and order creation for B2C customers. | General availability |


