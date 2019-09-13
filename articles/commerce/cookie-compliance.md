---
# required metadata

title: Cookie compliance
description: This topic reviews considerations for cookie compliance and the default policies included within Dynamics 365 Commerce. tooling.
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

# Cookie Compliance

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic reviews considerations for cookie compliance and the default policies included within Dynamics 365 Commerce.

## Overview

Privacy is an important factor when working with any tracking technologies that would affect an e-Commerce customer. With privacy compliance standards such as the General Data Protection Regulation (GDPR) in the EU, e-Privacy guidelines must be considered for any site that is active today. Many e-Commerce sites are globally accessible by default. For this reason, it is important to review compliance standards for your e-Commerce site.

The EU GDPR for cookies directs site owners to:

- Receive users' consent before using any cookies except strictly necessary cookies.
- Provide accurate and specific information about the data each cookie tracks and its purpose in plain language before consent is received.
- Document and store consent received from users.
- Allow users to access a service even if they refuse to allow the use of certain cookies.
- Make it as easy for users to withdraw their consent as it was for them to give their consent in the first place.

  ​	(Source https://gdpr.eu/cookies/)

By default, Commerce does not collect any customer cookies that are not strictly necessary. This ensures that sites built using the e-Commerce authoring tools will not be published with non-essential cookies.

However, note that any customizations or extensibility added to your site which may add cookies or tracking technologies will need to take GDPR and cookie compliance into account as necessary.

Additional information regarding GDPR Privacy standards can be found at https://gdpr.eu.

