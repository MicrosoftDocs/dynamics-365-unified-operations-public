--- 
title: Mixed license plate receiving doesn't work for all disposition codes 
description: When the Action field for a disposition code is set to Credit or Scrap, you can use only the Mixed license plate receiving menu item to process returned items. 
author: perlynne 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: perlynne 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 

--- 

# Mixed license plate receiving doesn't work for any disposition code but Credit

## Symptoms

When the **Action** field for a disposition code is set to *Credit* or *Scrap*, you can use only the [Mixed license plate receiving](/dynamics365/supply-chain/warehousing/mixed-license-plate-receiving) menu item to process returned items.

## Resolution

Microsoft has evaluated this issue and has determined that it's a feature limitation. Currently, only [disposition codes](/dynamics365/supply-chain/service-management/set-up-disposition-codes) where the **Action** field is set to *Credit* or *Scrap* are supported for mixed license plate receiving.
