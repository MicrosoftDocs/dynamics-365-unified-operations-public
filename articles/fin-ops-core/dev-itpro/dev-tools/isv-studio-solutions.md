---
title: Link X++ modules from ISV packages by using ISV Studio
description: This article describes linking X++ packages by using ISV Studio.
author: gianugo
ms.date: 04/08/2021
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 90ae4ae6-f19a-4ea5-8bd9-1d45729b0636
---

# Link X++ modules from ISV packages by using ISV Studio

Independent software vendors (ISVs) can link their X++ modules to their registered products and solutions by using [Microsoft Power Platform ISV Studio](/powerapps/developer/data-platform/isv-app-management). Linking enables ISV's to monitor the success and usage of their applications in finance and operations apps.

> [!NOTE]
> For the link from X++ into ISV Studio to work correctly, customers need to have deployed ISV packages with the correct solution ID in all the ISV models. The customer's environment also has to be version 10.0.16 or higher.

## Find the product ID in Microsoft Partner Center

Sign in to Partner Center and open the **Offer overview** page for your product. From the browser's URL bar, locate the product ID globally unique identifier (GUID), as shown in the following example.

```HTTP
https://partner.microsoft.com/dashboard/commercial-marketplace/offers/<product-ID-GUID>/overview
```

> [!NOTE]
> The product ID does not necessarily match the offer code of your product, although they may be similar. Using the offer code in your descriptors will not correctly identify your X++ modules to ISV Studio.

## Update your X++ model descriptors

For all models that make up your solution, locate the descriptor XML files. For every descriptor that belongs to a solution, update the `SolutionId` tag with the product ID from Partner Center. The order of the elements must match the following example to get the expected results.

:::code language="xml" source="code/descriptor.xml" highlight="19,20":::

After you recompile, the X++ binaries will contain the product ID and will link to ISV Studio after they are deployed to a Tier 2+ sandbox or production environment.

