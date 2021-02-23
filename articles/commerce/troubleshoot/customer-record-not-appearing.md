---
# required metadata

title: Customer records don't appear in Commerce headquarters
description: This topic provides troubleshooting for when customer records don't show up immediately in Commerce headquarters. 
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

# Customer records don't appear in Commerce headquarters

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting for when customer records don't show up immediately in Commerce headquarters

## Description

When creating a new customer record using the sign-up flow in the e-commerce storefront, the corresponding customer record doesn't immediately appear in Dynamics 365 Commerce headquarters.

## Resolution

### Disable customer creation in async mode 

> [!IMPORTANT]
> Disabling the asynchronous customer creation could have potential performance implications on the system because each record creation will result in a real time request to Commerce headquarters. Also, if Commerce headquarters is down (for example, during servicing flows), any new customer creation flows will result in errors. 

To disable customer creation in async mode in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**.
1. Create a new functionality profile (if you are not already using one for your online channel) and make sure the **Create customer in async mode** option is set to **No**.
1. Go to **Retail and Commerce \> Channels \> Online stores**.
1. Select the online store for which you want to disable customer creation in async mode.
1. On the **General** tab, ensure that the **Functionality profile** drop-down list option is set to the functionality profile you created in the previous step.

## Additional resources

- [Setup a B2C tenant in Commerce](../set-up-b2c-tenant.md)
