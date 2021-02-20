---
# required metadata

title: Payments are automatically settled before orders are invoiced or shipped
description: This topic provides a resolution for when an order is placed and is immediately settled in the Adyen portal despite whether the sales order isn't invoiced or shipped. 
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

# Payments are automatically settled before orders are invoiced or shipped

[!include [banner](../../includes/banner.md)]

## Description
Once an order is placed, the payment is immediately settled in the Adyen porta,l even when the sales order is not yet invoiced or shipped.

## Resolution

### Configure manual capture for e-commerce payments in the Adyen portal

1. Go to the Adyen portal and sign in.

1. On the top right corner, select your merchant account for the e-commerce channel.

1. On the top navigation, select **Account** and then select **Settings**.

1. In the **Capture delay** field, select **Manual**.

## Additional Resources
- [Adyen payment capture](https://docs.adyen.com/point-of-sale/capturing-payments)
- [Dynamics 365 Payment Connector for Adyen](../dev-itpro/adyen-connector.md)
- [Set up the Adyen payment connector for Dynamics 365](https://docs.adyen.com/plugins/microsoft-dynamics)










