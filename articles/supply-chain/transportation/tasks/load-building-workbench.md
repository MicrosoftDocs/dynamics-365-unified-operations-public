--- 
# required metadata 
 
title: Load building workbench
description: This procedure shows how to work with the Load building workbench. 
author: Henrikan
manager:  
ms.date: 10/30/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSLoadBuildWorkbench,TMSLoadBuildTemplateCreate,TMSLoadBuildStrategy
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: henrikan
ms.search.validFrom: 2020-10-30
ms.dyn365.ops.version: 10.0.15
---
## Load building workbench

The load building workbench allows you to apply load building strategies when creating loads.

### Create a Load building strategy

Use load building strategies automatically build loads, which can be beneficial in the following situations:

- When you ship a certain set of products regularly, using a load strategies saves time because you won't have to build the same load every time.
- When you want to maximize efficiency by avoiding half full loads, load strategies can help fill each load as much as possible.

A load building strategy class called `TMSLoadBuildingVolumeStrategy` provides a load building strategy called the *Volume-based load building strategy*. This strategy lets you use the maximum values that are specified for height and weight in the load template, or you can override the settings by entering new values.
<!-- KFM: Should we mention other classes here? I see just one other, which is TMSLoadBuildUTestStrategy, but is that for real? Might there be custom options here? -->
To use this strategy, select it in the **Load building strategy** field on the **Transportation management &gt; Planning &gt; Load building workbench** page.

To create a load building strategy, follow these steps:

1. Go to **Transportation management &gt; Setup &gt; Load Building &gt; Load building strategies**.
1. On the Action Pane, select **New**.
1. Enter a unique **Name**, select the **Load building strategy class**, and enter a **Description** for the strategy.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Parameters**.
1. The **Load building strategy parameters** page opens. Enter the value for **Volume** and the value for capacity to be applied for the newly created load building strategy. The value that you enter will be applied as a percentage of the total volume and capacity for the load. <!-- KFM: For me, these values are read-only for some reason. What has to happen to make them active? I don't see a setting for "Capacity", but I do see additional settings that we should probably explain (Name, Data type, Attribute type). -->
1. Close the **Load building strategy parameters** page.
1. Close the **Load building strategy** page.

You can now assign the load building strategy to a load building template, or use it directly in the load planning workbench.

### Use load building strategy in the load building workbench

To use a load building strategy in the load building workbench, follow these steps:

1. Open **Transportation management &gt; Planning &gt; Load building workbench**.
1. Do one of the following:
    - To choose a strategy directly, select it from the **Load building strategy** drop-down list.
    - Alternatively, if you have defined a load building template and assigned the load building strategy to the template, on the Action Pane, open the **Manage templates** tab and select Apply template to open the **Apply load building template** drop-down dialog box. Then select a template from the **Load building template name** drop-down list.
1. On the **Load templates sequence** FastTab, select one or more [load templates](load-template.md). <!-- KFM: This appears to be required to get to the next step. Also, would be nice to say a few words about what this means, and how to use the other FastTabs and settings on this page. -->
1. On the Action Pane, select **Propose loads**.
1. Review the proposed loads and proposed load lines.
1. On the Action Pane, select **Create loads**, to create loads based on the source document lines shown on the **Proposed load lines** FastTab.
1. Close the **Load building workbench** page.