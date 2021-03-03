---
# required metadata

title: Order synchronization error related to default payment service
description: This topic provides troubleshooting guidance on how to fix an error that is displayed when synchronizing an online order.
author: Reza-Assadi
manager: AnnBe
ms.date: 02/24/2021
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

# Order synchronization error related to default payment service

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance on how to fix an error that is displayed when synchronizing an online order.

## Description

When synchronizing an online order, the following error message is displayed as highlighted in the example image below: "There must be a default payment service to process credit card transactions."

![Default payment service missing error](media/default-payment-method-error.jpg)

## Resolution

### Confirm or set the default payment service in Dynamics 365 Commerce headquarters

To confirm or set the default payment service in Dynamics 365 Commerce headquarters

1. Go to **Accounts receivable \> Payment setup \> Payment services**.
1. Confirm that one payment service has the **Default processor for new credit cards** option is set to **Yes**. If not, set the option to **Yes** for one payment service.

## Additional resources

[Credit card setup, authorization, and capture](https://docs.microsoft.com/dynamics365/finance/accounts-receivable/credit-card-authorizations)
