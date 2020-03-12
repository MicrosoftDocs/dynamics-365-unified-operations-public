---
# required metadata

title: Customer loyalty cards and reward points
description: This topic describes the integration of tax data between Finance and Operations apps and Common Data Service.
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 03/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-10

---

# Customer loyalty cards and reward points

[!include [banner](../../includes/banner.md)]

[!include [preview banner](../../includes/preview-banner.md)]

Businesses classify customers and provide sophisticated services based on their shopping and spending patterns. Among the Dynamics 365 suite of applications, Dynamics 365 Commerce has the infrastructure and functions to facilitate and handle customer loyalty cards, reward points, loyalty-based pricing, and rewards-based shopping experience. When customer loyalty and reward points data from Dynamics 365 Commerce is synchronized to Common Data service, model-driven apps in Dynamics 365 can use that data. For example, Dynamics 365 Customer Service users can use the data to provide the same sophisticated service through the help desk.

## Templates

Finance and Operations apps | Model-driven apps in Dynamics 365 | Description
----------------------------|-----------------------------------|-------------
Loyalty card | msdyn_loyaltycards | This template synchronizes customer loyalty card information.
Loyalty reward points | msdyn_loyaltyrewardpoints | This template synchronizes customer reward points information.

[!include [banner](../../includes/dual-write-symbols.md)]

[!include [mapping loyalty card](includes/LoyaltyCard-msdyn-loyaltycards.md)]

[!include [mapping reward points](includes/LoyaltyRewardPoints-msdyn-loyaltyrewardpoints.md)]

