---
title: Pick oldest batch on a mobile device
description: Learn how you set up and apply the options to pick the oldest batch from a mobile device with an outline on setting up the configuration for pick oldest batch.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/26/2017
ms.reviewer: kamaybac
ms.search.form:  WHSRFMenuItem
---

# Pick oldest batch on a mobile device

[!include [banner](../includes/banner.md)]

You can access the configuration **Pick oldest batch** via a mobile device menu and it allows you to force or warn warehouse workers to pick the oldest batch in their current location.  

## Where it applies
Pick oldest batch is configured on mobile device menu items and effects the pick for batch below items.

## How to set up the configuration for Pick oldest batch 
For items that are set to use existing work, **Pick oldest batch** can be set to **None**, **Warn**, or **Force** from a mobile device menu.

**None**: Workers will not receive any messages and they will be allowed to pick any batch in their location.

**Warn** and **Force**:  A list of the batch(es) with the oldest expiration date will be displayed above the batch control when the worker selects a batch. If the location is license plate controlled, a list of license plates that have the oldest batch will be displayed above the license plate control. 
-	**Warn**: If a worker chooses a license plate or batch that is not on the shown list, the control will be blanked and a warning will be shown that there is an older batch to select. To be allowed to continue the work, the worker can select the same license plate or batch again.  
-	**Force**: Workers will continue to receive the message that there is an older batch to pick.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]