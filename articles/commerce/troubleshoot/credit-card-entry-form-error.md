---
# required metadata

title: Credit card entry page displays error on checkout
description: This topic provides troubleshooting information for when the "Payment method" section doesn't load and displays an error. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/23/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
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

This topic provides troubleshooting information for when the "Payment method" section doesn't load and displays an error.

## Description

When navigating to the checkout page of an online store, the **Payment method** section doesn't load and displays the following error as shown in the following example image: "Something went wrong. Please try again later."

![Payment module error](media/payment-module-error.jpg)

## Resolution

### Wait for Commerce Scale Unit cache to expire

The payment service settings on the online store checkout page are cached on the Commerce Scale Unit and can take up to 15 minutes to appear on the e-commerce site. Such payment service settings include changes to the merchant account ID, cloud API key, and various configuration settings relating to payment method. 

## Additional Resources

[Set up an online channel](../channel-setup-online.md)
