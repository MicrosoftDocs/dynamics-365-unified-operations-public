---
# required metadata

title: Cookie compliance
description: This topic describes considerations for cookie compliance and the default policies that are included in Microsoft Dynamics 365 Commerce.
author: BrianShook
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Cookie compliance

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes considerations for cookie compliance and the default policies that are included in Microsoft Dynamics 365 Commerce.

## Overview

Privacy is an important factor whenever any tracking technologies that affect e-Commerce customers are used. Because of privacy compliance standards such as the General Data Protection Regulation (GDPR) in the European Union (EU), electronic privacy guidelines must be considered for any site that is active today. Because many e-Commerce sites are globally accessible by default, it's important that you review the compliance standards for your e-Commerce site.

Here is what the GDPR directs site owners to do in the matter of cookies:

- Receive user consent before you use any cookies that aren't strictly necessary.
- Before consent is received, provide accurate and specific information, in plain language, about the data that each cookie tracks and the purpose of that data.
- Document and store the consent that is received from users.
- Allow users to access a service even if they refuse to allow some cookies to be used.
- Make it as easy for users to withdraw their consent as it was for them to give their consent.

(Source: [Cookies, the GDPR, and the ePrivacy Directive](https://gdpr.eu/cookies/))

By default, Dynamics 365 Commerce doesn't collect any customer cookies that aren't strictly necessary. Therefore, when sites that are built by using the e-Commerce authoring tools are published, they don't use nonessential cookies.

However, if any customization or extension that is done to your site adds cookies or tracking technologies, you must consider GDPR and cookie compliance, as required.

For more information about GDPR privacy standards, see [Complete guide to GDPR compliance](https://gdpr.eu/).
