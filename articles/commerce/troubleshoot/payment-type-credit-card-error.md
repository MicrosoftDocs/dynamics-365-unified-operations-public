---
# required metadata

title: Payment type must be credit card error
description: This topic provides a resolution if an error message is displayed when the user goes to the sales order page after synchronizing an order. 
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

# "Payment type must be credit card" error

[!include [banner](../../includes/banner.md)]

## Description
When navigating to the **Sales order** page after synchronizing an order, the following error message is displayed: "The
payment type must be credit card, since the credit card number has been specified."

## Resolution

### Set the payment type on the terms of payment 

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Accounts receivable > Payment setup > Terms of payment**.

1. Select your term of payment from the navigtion on the left.

1. Make sure **Credit card** is selected in the **Payment type** field.
