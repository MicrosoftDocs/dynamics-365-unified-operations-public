---
# required metadata

title: Sign in link redirects back to e-commerce site
description: This topic provides a fix for when a sign-in link redirects back to the e-commerce site instead of the sign-in page. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/17/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# "Sign in" link redirects back to e-commerce site

[!include [banner](../../includes/banner.md)]

## Description
After configuring a new AAD B2C tenant in site builder, selecting **Sign in** redirects back to the main e-commerce landing page without navigating to the sign-in page.

## Resolution
### Make sure the **Reply** URL on the AAD B2C is configured correctly 

1. Go to to the Azure Portal at: https://portal.azure.com](https://portal.azure.com/).

1. Select the AAD B2C application that you created for your site access.

1. Select the application you created earlier during the AAD B2C setup.

1. Under the list for **Reply URL**, make sure you have two entries for both site domain and e-commerce-generated URL.

> [!NOTE]
> These URLs must use a valid URK format without leading or trailing slashes.



