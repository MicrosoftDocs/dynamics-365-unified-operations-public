---
# required metadata

title: Save for Next Payment option doesn't appear
description: This topic provides how to troubleshoot when "Save for next payment" doesn't appear under the payment methods options on an e-commerce site. 
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

# "Save for Next Payment" option doesn't appear

[!include [banner](../../includes/banner.md)]

## Description
The **Save for next payment** option doesn't appear on the **Checkout** page under **Payment method**.

## Resolution

### Make sure the Dynamics 365 Payment Connector for Adyen is configured correctly

1. Go to Commerce headquarters.

1. Go to **Retail and Commerce > Channels > Online Stores**.

1. Select the online store that you want to configure the Adyen connector for.

1. On the **Online stores** page, on the **Payent accounts** tab, make sure the **Allow saving payment information in e-commerce** field is set to **True**.













