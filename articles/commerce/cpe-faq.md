---
# required metadata

title: Commerce preview environment FAQ
description: This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce preview environment.
author: v-chgri
manager: annbe
ms.date: 12/02/2019
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
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Commerce preview environment FAQ

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic provides answers to frequently asked questions about the Microsoft Dynamics 365 Commerce preview environment.

### I have received an invitation to Dynamics 365 Commerce preview environment on my account, but I want to set up the Commerce preview environment in another tenant (due to the fact that I'm not a global administrator for my company tenant). Is it possible to transfer the invitation to the other tenant instead?  
Yes. For invitation transfers, you can use the [Commerce preview transfer form](https://aka.ms/Dynamics365CommercePreviewTransferForm).
 
###  How long will the invitation transfer take? 
The transfer should take approximately 3-5 business days.
 
###  The Commerce preview environment does not work with Dynamics 365 for Finance and Operations projects? 
Correct, it only works with Dynamics 365 Retail projects.
 
###  What should we do if our customer is a Dynamics 365 for Finance and Operations customer who is also implementing Dynamics 365 Retail and needs an e-commerce storefront? 
This is the evaluation environment process. If you need an environment for an implementing customer, please reach out to us.
 
###  What do you consider as "Commerce preview"? Provisioning a pure Dynamics 365 Retail preview environment for a prospective customer? Or provisioning the e-commerce features that are in Commerce preview on top of an existing application/environment that is implementing Dynamics 365 Retail as well?
At this time, the Commerce preview environment is only available on new environments deployed on Dynamics 365 Retail SKU projects with demo data from version 10.0.6.
 
###  When we deploy the Commerce preview environment on Azure via Microsoft Lifecycle Services (LCS), what costs are involved? Only the CPU computing hours of the machine or are there also additional costs, for example Azure websites? 
Dynamics 365 Retail is the only component hosted in your subscription. The other components will be hosted in Microsoft subscriptions.
 
###  Is there a calculation option to estimate the monthly costs?
The [Azure pricing calculator](https://azure.microsoft.com/en-us/pricing/calculator/) can be used to estimate the cost. 
 
###  Which geographical regions are currently supported? 
The Commerce preview environment can only be deployed to the North America geographical region.
 
###  Why isn't there a downloadable virtual hard disk (VHD) with complete OneBox VM option? Setting this thing up is quite a pain... 
Retail Cloud Scale Unit (RCSU) and Commerce are completely software as a service (SaaS) and must be cloud hosted.
 
###  Is there a time limit on running the Commerce preview environment?
The time limit on running the Commerce preview environment is 30 days from provisioning e-Commerce.
 
###  Why is the Commerce preview environment only available for 30 days? 
If 30 days is not enough for evaluation, you should reach out to us using the [Commerce preview extension form] (https://aka.ms/Dynamics365CommercePreviewExtensionForm).

### Can we make multiple request for a preview? 
We grant quota of a single Commerce preview environment per accepted request. Should you need more than that, please reach out to us.

## Dynamics 365 Commerce preview environment contact information

To contact Microsoft with questions or requests regarding the Commerce preview environment, please visit the [Microsoft Dynamics 365 Commerce Preview Yammer group](https://aka.ms/Dynamics365CommercePreviewYammer) for assistance. 

If you are having issues accessing the Yammer group, you can also reach us via email at **Dynamics365Commerce@microsoft.com**. This email address is not actively monitored so expect a delay in response.
 
 ## Additional resources

[Commerce preview environment overview](cpe-overview.md)

[Provision a Commerce preview environment](provisioning-guide.md)

[Configure a Commerce preview environment](cpe-post-provisioning.md)

[Configure Commerce preview environment optional features](cpe-optional-features.md)


