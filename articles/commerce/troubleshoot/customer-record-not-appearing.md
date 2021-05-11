---
# required metadata

title: Customer records don't appear in Commerce headquarters
description: This topic provides troubleshooting guidance that can help when customer records don't immediately appear in Commerce headquarters.
author: Reza-Assadi
ms.date: 03/11/2021
ms.topic: Troubleshooting
ms.prod: 
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

# Customer records don't appear in Commerce headquarters

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting guidance that can help when customer records don't immediately appear in Commerce headquarters.

## Description

When you create a new customer record by using the sign-up flow in the e-commerce storefront, the corresponding customer record doesn't immediately appear in Commerce headquarters.

## Resolution

### Disable customer creation in async mode

> [!IMPORTANT]
> If you disable asynchronous customer creation, system performance could be affected, because creation of each record will produce a real-time request to Commerce headquarters. In addition, if Commerce headquarters is down (for example, during servicing flows), any new customer creation flows will produce errors.

To disable customer creation in async mode in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Online store setup \> Functionality profiles**.
1. If you aren't already using a functionality profile for your online channel, create one.
1. Make sure that the **Create customer in async mode** option is set to **No**.
1. Go to **Retail and Commerce \> Channels \> Online stores**.
1. Select the online store to disable asynchronous customer creation for.
1. On the **General** tab, make sure that the **Functionality profile** field is set to the functionality profile that you're using for your online channel.

## Additional resources

[Setup a B2C tenant in Commerce](../set-up-b2c-tenant.md)
