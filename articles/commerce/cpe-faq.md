---
# required metadata

title: Dynamics 365 Commerce preview environment FAQ
description: This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce preview environment.
author: v-chgri
manager: annbe
ms.date: 12/10/2019
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

# Dynamics 365 Commerce preview environment FAQ

[!include [banner](includes/banner.md)]

This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce preview environment.

**Can I transfer my invitation for the Commerce preview environment to another tenant?**

Yes. For invitation transfers, you can use the [Commerce preview transfer form](https://aka.ms/Dynamics365CommercePreviewTransferForm).

**How long does the invitation transfer take?**

The transfer takes an average of approximately three to five business days. However, exceptions might apply.

**Does the Commerce preview environment work with Dynamics 365 Finance or Dynamics 365 Supply Chain projects?**

No. The Commerce preview environment works only with Dynamics 365 Retail projects.

**Can we use the Commerce preview environment as an e-commerce storefront for customers that currently implement Retail?**

No. The Commerce preview environment is just the evaluation environment. If you require an environment for a customer that implements Retail, contact Microsoft.

**Can the Commerce preview environment be used to provision the e-commerce features on top of an existing application/environment that implements Retail?**

No. The Commerce preview environment is currently available only in new environments that were deployed on Retail stock keeping unit (SKU) projects that have demo data from version 10.0.6.

**What costs are involved in deploying the Commerce preview environment on Microsoft Azure via Microsoft Dynamics Lifecycle Services (LCS)?**

Retail is the only component that is hosted in your subscription. Other components such as Retail Cloud Scale Unit (RCSU) and e-Commerce will be hosted in Microsoft subscriptions. You can use the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/) to estimate this cost.

**Which Azure geographies are currently supported for the Commerce preview environment?**

The Commerce preview environment can be deployed only in the North America geography.

**Is there a downloadable virtual hard disk (VHD) that has the complete OneBox virtual machine (VM) option?**

Dynamics 365 Retail Cloud Scale Unit (RCSU) and e-Commerce are completely software as a service (SaaS) and must be cloud-hosted.

**How long can the Commerce preview environment be used?**

The Commerce preview environment has a 30-day time limit from the date of provisioning e-Commerce.

**Can I extend the time limit for my Commerce preview environment?**

Yes. You can contact the support team by using the [Commerce preview extension form](https://aka.ms/Dynamics365CommercePreviewExtensionForm).

**Can we make multiple requests for a Commerce preview environment?**

We grant a quota of one Commerce preview environment for each request that is accepted. If you need more than one preview environment, contact Microsoft. For contact information, see the next section.

## Dynamics 365 Commerce preview environment contact information

To contact Microsoft if you have questions or requests that are related to the Commerce preview environment, visit the [Microsoft Dynamics 365 Commerce Preview Yammer group](https://aka.ms/Dynamics365CommercePreviewYammer) for help.

## Additional resources

[Dynamics 365 Commerce preview environment overview](cpe-overview.md)

[Provision a Dynamics 365 Commerce preview environment](provisioning-guide.md)

[Configure a Dynamics 365 Commerce preview environment](cpe-post-provisioning.md)

[Configure optional features for a Dynamics 365 Commerce preview environment](cpe-optional-features.md)
