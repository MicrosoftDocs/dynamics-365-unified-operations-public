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

Dual-write provides ...

To get started with dual-write, see the [Dual-write home page](dual-write-home-page.md).

> [!IMPORTANT]
> Dual-write features and changes are not announced via blog posts. Descriptions of dual-write features are provided in the [release plans](https://go.microsoft.com/fwlink/?linkid=2010158). 

The following sections list the features that are included in dual-write releases.

## July 2020 - wave 1

The July 2020 release of the dual-write orchestration package is based on dual-write core version 10.0.18 and it contains the following application functions:

| Area | Feature |Status |
|------|---------|-------|
|      | 	1. Lead qualification process in Sales is new company striped. As a D365 Sales user, you can create a lead, qualify the lead to an opportunity, convert an opportunity in to a quote, activate a quote and create an order. This end to end process was broken in dual-write due to lack of company striping on Lead record. With this release, we are introducing the company striping on the lead record, which upon qualify, cascades the company to the underlying Account and Opportunity records. Thus the application behavior is restored to support the end to end process flow. Note: During the lead qualification process, the contact record is not company striped. This design will support the party model which is due in Sep'20. If you are interested in learning about the Party & Global Address Book model for dual-write, please join the dual-write Yammer group. | |
|         | 	2. Map the state and sub-state transitions between Sales\Order and SCM\SalesOrder. The Order form in Sales app was set to be in Active state always. In order to restore the Order life cycle and correctly reflect the state and sub-state transitions, we have mapped the Order status between Sales app and Supply Chain app. This release contains the respective changes to reflect correct status on both applications. For details, please refer <here - link to Dasani's page> |      |  
|  | 	3. Money to decimal data type conversion (aka Extended Decimal Support in CDS to support Dual-Write). Standard CDS deployments are limited to 4 decimal places for currency and 10 decimal places for exchange rates. Users who are dual writing from F&O may currently be using more decimal places with their data. Users may now opt-in to extend the decimal support in CDS to help ensure there is no loss of decimal place data when dual writing between the two environments. Documentation is available to describe the change and help users request this extension.  |  |
|  | 	4. Security role for company and currency exchange. Company and currency exchange entities are global in nature and all dual-write users require read access to these 2 entities. In order to simplify the experience, we have releasing a new security role called "". Each dual-write user must be added to this security role.   |  |

If you are using Dual-write core version 1.0.16, you should upgrade to 10.0.18. 

## May 2020 - wave 1

The May 2020 release of dual-write orchestration package (version 2.0.777.353) contains the following features and bug fixes: 

| Area | Feature |Status |
|------|---------|-------|
|  | 	Ability to lookup on-hand inventory and Available to promise dates on CE forms. |  |
|  | 	When unit conversions take place in F&O at the quote line and order line, CE honors the unit conversions and reflect the respective changes (unit & price) in CE quote detail and order detail. |  |
|  | 	When user tries to change the currency in F&O for an existing quote or order, restrict the change and don’t succeed.   |  |
|  | 	Bring attribute parity in CE Account and Contact forms for B2B and B2C customers.  |  |
|  | 	Don’t duplicate an address in F&O when there is a create/update action on CE quote/order.  |  |
|  | 	Support for Sales Tax Group in Account and Contact forms for B2B and B2C customers. |  |
|  | 	Allow creation of a sellable contact through “Quick Create: Contact” form in CE. |  |
|  | Enable Quote and Order creation for B2C customers. |  |

## Dual-write releases before ...

For information about dual-write releases that occurred before ..., see the blog posts at ...
