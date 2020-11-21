---
# required metadata

title: What's new or changed in dual-write
description: This topic provides links to the release plans, major announcements, and documentation for dual-write.
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

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between customer engagement apps in Microsoft Dynamics 365 and Finance and Operations apps. To get started with dual-write, see the [Dual-write home page](dual-write-home-page.md).

Check out the latest information about dual-write features and changes in the [release plans](https://go.microsoft.com/fwlink/?linkid=2010158).

+ [Data in Common Data Service – Phase 1](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/data-common-data-service-phase-1)
+ [Data in Common Data Service – phase 1 & 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/finance-operations-crossapp-capabilities/data-common-data-service-phase-1-2)
+ [Finance and Operations data in Common Data Service – Phase 3](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/finance-operations-data-common-data-service-phase-3)

## September 2020 release

The September 2020 release of the [Dual-write application orchestration solution version 2.0.777.493](https://appsource.microsoft.com/product/dynamics-365/mscrm.finance-and-operations-with-common-data-service) is based on [Dual-write core solution version 10.0.21](https://appsource.microsoft.com/product/dynamics-365/mscrm.msft-d365-dual-write).  

The September 2020 release contains the features and bug fixes listed in the following table.

| Feature | Description |Status |
|------|---------|-------|
| Lead qualification process in Sales is now company striped | Dynamics 365 Sales users can create a lead, qualify the lead to an opportunity, convert an opportunity into a quote, activate a quote, and create an order. This process was broken in dual-write due to lack of company striping on the **Lead** entity. We implemented company striping on the **Lead** entity, which cascades the company to the underlying **Account** and **Opportunity** entities. Thus the application behavior is restored to support the process. During the **Lead** qualification process, the **Contact** entity isn't company striped. This design supports the **Party** entity model that is due in October 2020. To learn about the **Party** and **GlobalAddressBook** model for dual-write, join the [dual-write Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=66052096&view=all). | General availability |
| [Map state transitions from **Order** to **SalesOrder**](sales-status-map.md) | The **Order** form in Dynamics 365 Sales is always set to **Active**. To create state transitions from **Order** in Dynamics 365 Sales to **SalesOrder** in Dynamics 365 Supply Chain Management, we introduced the **ProcessingStatus** field. |   General availability   |  
| [Money to decimal data type conversion](currrency-decimal-places.md) |  Common Data Service environments are limited to 4 decimal places for currency and 10 decimal places for exchange rates. Finance and Operations apps support more decimal places than Common Data Service. You can now opt in to extend the decimal support in Common Data Service to help ensure there's no loss of decimal place data when using dual-write. | General availability |
| Security role for company and currency exchange | Company and currency exchange entities are global in nature and all dual-write users require read access to these 2 entities. To simplify the experience, we've added a new security role named **dual-write app user**. Each dual-write user must be added to this security role.   | General availability |
| Security role for setup | Adds the **Dual-write Runtime User** security role. This role allows non-administrator users to create records that are set up for dual-write. This feature is part of Dual-write core solution 10.0.21. | General availability |
| Tracing | Internal field added for use in tracing. This feature is part of Dual-write core solution 10.0.21. | General availability |
| Bug fix | Fixes issues where dual-write fails because of a mismatch between the plugin and the destination environments. This fix is part of Dual-write core solution 10.0.21. | General availability |
| Bug fix | Support to ensure that unused plugins are deleted. This fix is part of Dual-write core solution 10.0.21. | General availability |

## August 2020 release

The August 2020 release of the dual-write orchestration package contains the features and bug fixes listed in the following table.

| Feature | Description |Status |
|------|---------|-------|
| Manage multiple entity maps | As part of day-to-day operations, you might need to bulk handle entity maps. For example, you might want to simultaneously enable or pause a set of entity maps. Instead of doing this one-by-one, which is cumbersome and time consuming, you can now enable, pause, resume, or stop more than one entity map at the same time in the dual-write list page. | General availability |
| Bug fix | Fixes issues where records would be skipped in certain cases during project execution. This fix is part of Dual-write core solution version 10.0.19.  | General availability |

## June 2020 release

The June 2020 release of the dual-write orchestration package contains the features and bug fixes listed in the following table.

| Feature | Description |Status |
|------|---------|-------|
| Edit legal entity after setup | The company or legal entity list isn't static and is constantly changing. You might need to add new companies, for example, during a phased rollout or acquisition. Previously, you couldn't add a company or legal entity without system downtime. During this downtime, you would have to unlink and relink your environment. That can be expensive, especially if you have pre-existing data. With this feature, you can add a company in a live environment without having to unlink and relink. | General availability |


## May 2020 release

The May 2020 release of the dual-write orchestration package (version 2.0.777.353) contains the features and bug fixes listed in the following table.

| Feature | Description |Status |
|------|---------|-------|
| Look up on-hand inventory | Ability to look up on-hand inventory and available-to-promise dates on forms in customer engagement apps. | General availability |
| Unit conversions | 	When unit conversions occur in a Finance and Operations app at the quote line and order line, the customer engagement app honors the unit conversions and reflects the respective changes to unit and price in the customer engagement app quote detail and order detail. | General availability |
| Currency change restriction | When you try to change the currency in a Finance and Operations app for an existing quote or order, the change fails.   | General availability |
| Parity in **Account** and **Contact** forms | Bring attribute parity in **Account** and **Contact** forms in customer engagement apps for B2B and B2C customers.  | General availability |
| No address duplication | Don’t duplicate an address in a Finance and Operations app when there's a create or update action on a customer engagement app quote or order.  | General availability |
| **SalesTaxGroup** support | Support for **SalesTaxGroup** in **Account** and **Contact** forms for business-to-business (B2B) and business-to-consumer (B2C) customers. | General availability |
| Create sellable contacts | Allow creation of a sellable contact using the **Quick Create: Contact** form in customer engagement apps. | General availability |
| Quote and order creation | Enable quote and order creation for B2C customers. | General availability |
| Removal of tenant admin-level consent requirement | Until now, before you could enable dual-write, a tenant admin needed to explicitly give consent to the applications. This wasn't always practical and required additional approval, which can be time consuming. With this feature, we removed this prerequisite and the need for explicitly giving consent to the applications. | General availability |
| Force unlink dual-write environment | Previously, while testing dual-write, you had to disable all the entity maps before unlinking a dual-write environment. This seemed cumbersome and sometimes not possible if one of the environments wasn't available. This new feature provides a quick way to unlink your test and trial environments. | General availability |


