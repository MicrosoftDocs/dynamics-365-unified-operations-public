---
# required metadata

title: Save for Next Payment option doesn't appear
description: This topic provides troubleshooting guidance for when "Save for next payment" doesn't appear under the payment methods options on an e-commerce site checkout page. 
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

# "Save for Next Payment" option doesn't appear

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance for when "Save for next payment" doesn't appear under the payment methods options on an e-commerce site checkout page.

## Description

The **Save for next payment** option doesn't appear on the an e-commerce site's checkout page under **Payment method**, as shown in the example image below.

![Payment module save for next payment checkbox](media/payment-module-save-payment.jpg)

## Resolution

### Check that the Dynamics 365 Payment Connector for Adyen is configured correctly in Commerce headquarters

To check that the Dynamics 365 Payment Connector for Adyen is configured correctly in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Online Stores**.
1. Select the online store.
1. On the **Payment accounts** FastTab, ensure that the **Allow saving payment information in e-commerce** value is set to **True**.

![Payment connector save for next payment checkbox](media/payment-connector-save-payment.jpg)

## Additional resources

[Payment module](../payment-module.md)

[Saving online payment instruments with the Adyen connector](../adyen-connector-listpi.md)


