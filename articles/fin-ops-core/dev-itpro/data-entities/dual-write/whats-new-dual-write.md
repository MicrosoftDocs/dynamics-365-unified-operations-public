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

Dual-write is an out-of-box infrastructure that provides near-real-time interaction between customer engagement apps in Microsoft Dynamics 365 and Finance and Operations apps. To get started with dual-write, see the [Dual-write home page](dual-write-home-page.md).

Check out the latest information about dual-write features and changes in the [release plans](https://go.microsoft.com/fwlink/?linkid=2010158).

+ [Data in Common Data Service – Phase 1](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/finance-operations-crossapp-capabilities/data-common-data-service-phase-1)
+ [Data in Common Data Service – phase 1 & 2](https://docs.microsoft.com/dynamics365-release-plan/2020wave1/finance-operations-crossapp-capabilities/data-common-data-service-phase-1-2)
+ [Finance and Operations data in Common Data Service – Phase 3](https://docs.microsoft.com/dynamics365-release-plan/2020wave2/finance-operations/finance-operations-crossapp-capabilities/finance-operations-data-common-data-service-phase-3)

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
| Parity in **Account** and **Contract** forms | Bring attribute parity in **Account** and **Contact** forms in customer engagement apps for B2B and B2C customers.  | General availability |
| No address duplication | Don’t duplicate an address in a Finance and Operations app when there's a create or update action on a customer engagement app quote or order.  | General availability |
| **SalesTaxGroup** support | Support for **SalesTaxGroup** in **Account** and **Contact** forms for business-to-business (B2B) and business-to-consumer (B2C) customers. | General availability |
| Create sellable contracts | Allow creation of a sellable contact using the **Quick Create: Contact** form in customer engagement apps. | General availability |
| Quote and order creation | Enable quote and order creation for B2C customers. | General availability |
| Removal of tenant admin-level consent requirement | Until now, before you could enable dual-write, a tenant admin needed to explicitly give consent to the applications. This wasn't always practical and required additional approval, which can be time consuming. With this feature, we removed this prerequisite and the need for explicitly giving consent to the applications. | General availability |
| Force unlink dual-write environment | Previously, while testing dual-write, you had to disable all the entity maps before unlinking a dual-write environment. This seemed cumbersome and sometimes not possible if one of the environments wasn't available. This new feature provides a quick way to unlink your test and trial environments. | General availability |


