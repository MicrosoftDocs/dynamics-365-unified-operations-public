--- 
title: Production orders not shown on the Marking page 
description: Some production orders aren't shown on the Marking page. This topic explains the three product configurations that aren't available for marking. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Production orders aren't shown on the Marking page

## Symptoms

When working with discreet manufacturing, some production orders aren't shown on the **Marking** page.

## Resolution

Products that have the following configurations aren't available for marking. Therefore, they won't be shown on the **Marking** page:

- The products are defined as products of the *catch weight* type.
- They're enabled for the advanced warehouse processes.
- They're configured to be controlled by the *Standard cost* principle.
