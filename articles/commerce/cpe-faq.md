---
# required metadata

title: Dynamics 365 Commerce evaluation environment FAQ
description: This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce evaluation environment.
author: v-chgri
manager: annbe
ms.date: 07/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: v-chgri
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
---

# Dynamics 365 Commerce evaluation environment FAQ

[!include [banner](includes/banner.md)]

This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce evaluation environment.

**Can we use the Commerce evaluation environment as an e-Commerce storefront for customers that currently implement Retail?**

No. The Commerce evaluation environment is only for evaluation. If you require an environment for a customer that implements Retail, contact Microsoft.

**Can the Commerce evaluation environment be used to provision the e-Commerce features on top of an existing application/environment that implements Retail?**

No. The Commerce evaluation environment is currently only available in new environments.

**What costs are involved in deploying the Commerce evaluation environment on Microsoft Azure via Microsoft Lifecycle Services (LCS)?**

Commerce is the only component that is hosted in your subscription. Other components such as Commerce Scale Unit and Commerce will be hosted in Microsoft subscriptions. You can use the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/) to estimate this cost.

**Which Azure geographies are currently supported for the Commerce evaluation environment?**

The Commerce evaluation environment can be deployed only in the North America geography.

**Is there a downloadable virtual hard disk (VHD) that has the complete OneBox virtual machine (VM) option?**

Dynamics 365 Commerce and Commerce Scale Unit are completely software as a service (SaaS) and must be cloud-hosted.

**How long can the Commerce evaluation environment be used?**

The Commerce evaluation environment has a 30-day time limit from the date of provisioning Commerce.

**Can I extend the time limit for my Commerce evaluation environment?**

This is considered on case by case basis. Please reach out to your Microsoft partner contact for assistance.

## Additional resources

[Dynamics 365 Commerce evaluation environment overview](cpe-overview.md)

[Provision a Dynamics 365 Commerce evaluation environment](provisioning-guide.md)

[Configure a Dynamics 365 Commerce evaluation environment](cpe-post-provisioning.md)

[Configure optional features for a Dynamics 365 Commerce evaluation environment](cpe-optional-features.md)
