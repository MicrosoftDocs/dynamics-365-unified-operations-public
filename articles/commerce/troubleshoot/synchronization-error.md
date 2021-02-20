---
# required metadata

title: Order synchronization error related to default payment service
description: This topic provides a resolution for when an error is displayed when an online order is synchronized.
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

# Order synchronization error related to default payment service

[!include [banner](../../includes/banner.md)]

## Description
When synchronizing an online order, the following error message is displayed: "There must be a default payment service to process credit card transactions."

## Resolution

### Set the default payment service

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Accounts receivable > Payment setup > Payment services**.

1. Make sure one payment service is configured with the **Default processor for new credit cards** setting.

## Additional Resources
- [Credit card setup, authorization, and capture](https://docs.microsoft.com/en-us/dynamics365/finance/accounts-receivable/credit-card-authorizations)
