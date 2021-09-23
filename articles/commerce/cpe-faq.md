---
# required metadata

title: Dynamics 365 Commerce evaluation environment FAQ
description: This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce evaluation environment.
author: v-chgri
ms.date: 07/16/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
---

# Dynamics 365 Commerce evaluation environment FAQ

[!include [banner](includes/banner.md)]

This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce evaluation environment.

## Can we use the Commerce evaluation environment as an e-Commerce storefront for customers that currently implement Retail?

No. The Commerce evaluation environment is only for evaluation. If you require an environment for a customer that implements Retail, contact Microsoft.

## Can the Commerce evaluation environment be used to provision the e-Commerce features on top of an existing application/environment that implements Retail?

No (mostly). The Commerce evaluation components are available only to environments that match the configurations that are specified in the prerequisites and provisioning guide. Additionally, the required base demo data won't be available in environments that were deployed with an initial release that is earlier than 10.0.8. 

## What costs are involved in deploying the Commerce evaluation environment on Microsoft Azure via Microsoft Dynamics Lifecycle Services (LCS)?

A traditional Dynamics 365 Finance/Dynamics 365 Supply Chain Management/Dynamics 365 Commerce headquarters demo environment (virtual machine \[VM\]) will be hosted in your Azure subscription. You can use the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/) to estimate this cost.

Other components such as Commerce Scale Unit, Commerce site builder, and your e-Commerce site will be available as software as a service (SaaS) and hosted by Microsoft.

## Which Azure geographies are currently supported for the Commerce evaluation environment?

The Commerce evaluation environment can be deployed only in the North America geography.

## Is there a downloadable virtual hard disk (VHD) that has the complete OneBox virtual machine (VM) option?

Dynamics 365 Commerce and Commerce Scale Unit are completely software as a service (SaaS) and must be cloud-hosted.

## How long can the Commerce evaluation environment be used?

The Commerce evaluation environment has a 30-day time limit from the date when SaaS components such as Commerce Scale Unit, Commerce site builder, and your e-Commerce site are provisioned.

## Can I extend the time limit for my Commerce evaluation environment?

Extension of the time limit is an exception to the norm and is considered on a case-by-case basis. You should reach out to your Microsoft partner contact for assistance.

## Additional resources

[Dynamics 365 Commerce evaluation environment overview](cpe-overview.md)

[Provision a Dynamics 365 Commerce evaluation environment](provisioning-guide.md)

[Configure a Dynamics 365 Commerce evaluation environment](cpe-post-provisioning.md)

[Configure BOPIS in a Dynamics 365 Commerce evaluation environment](cpe-bopis.md)

[Configure optional features for a Dynamics 365 Commerce evaluation environment](cpe-optional-features.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
