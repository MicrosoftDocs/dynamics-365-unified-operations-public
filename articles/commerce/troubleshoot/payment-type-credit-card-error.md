---
# required metadata

title: "Payment type must be credit card" error on Sales order page
description: This topic provides troubleshooting information for when an error message is displayed on the sales order page after synchronizing an order. 
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

# "Payment type must be credit card" error

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting information for when an error message is displayed on the sales order page after synchronizing an order. 

## Description

When navigating to the **Sales order** page after synchronizing an order, the following error message is displayed: "The payment type must be credit card, since the credit card number has been specified."

![Payment type must be credit card](media/payment-type-must-be-credit-card.jpg)

## Resolution

### Set the payment type in Commerce headquarters

1. Go to **Accounts receivable > Payment setup > Terms of payment**.
1. Select your term of payment from the navigation pane on the left.
1. For **Payment type**, ensure that **Credit card** is selected.

## Additional resources

[Posting of online sales and payments](../posting-online-sales-payments.md)
