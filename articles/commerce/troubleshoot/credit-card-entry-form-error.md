---
# required metadata

title: Credit card entry page displays error on checkout
description: This topic provides troubleshooting information for when the "Payment method" section doesn't load and throws an error. 
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

# Credit card entry page displays error on checkout

[!include [banner](../../includes/banner.md)]

## Description
When navigating to the **Checkout** page, the **Payment method** section doesn't load and throws the following error: "Something went wrong. Please try again later."

## Resolution

### Wait for Cloud Scale Unit cache to expire
The payment service settings on the **Online store** page, including changes to the **Merchant account ID** or **Cloud API** key, and various configuration settings relating to payment method, are cached on the Commerce Scale Unit and can take up to 15 minutes to appear on the e-commerce site.









