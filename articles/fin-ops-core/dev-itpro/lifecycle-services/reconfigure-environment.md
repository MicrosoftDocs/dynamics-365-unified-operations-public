---
# required metadata

title: Reconfigure environments to take a new platform or topology
description: This topic provides information about how to reconfigure your environment with a new platform or topology and how to update the configuration of your existing environment.
author: PeterRFriis
manager: AnnBe
ms.date: 12/05/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perahlff
ms.search.validFrom: 2017-12-05
ms.dyn365.ops.version: 7.3

---
# Reconfigure environments to take a new platform or topology

[!include [banner](../includes/banner.md)]

This topic provides information about how to reconfigure your environment with a new platform or topology and how to update the configuration of your existing environment.  

## Prerequisites
Before you complete the steps in this topic, you must update your local agent. For more information, see the topic, [Update the local agent](update-local-agent.md). The procedure in this topic will only work with local agents that are on or above version 1.1.0. 

## Reconfigure your environment

1. In Lifecycle Services (LCS), navigate to your on-premises project and open the **Environments** blade. 

2. Do one of the following based on whether you are going to reconfigure or take a new deployment.

- If you need to reconfigure your environment, click **Reconfigure**.
- If you need to take a new deployment or topology, select the new topology for your platform and enter the environment name. You can use the same name or enter a new one. 
  
3. Click **Advanced Settings** to update your configuration. The configuration from your previous deployment will be saved. 
