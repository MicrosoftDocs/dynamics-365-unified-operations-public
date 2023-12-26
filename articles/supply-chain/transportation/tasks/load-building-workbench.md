--- 
# required metadata 
 
title: Load building workbench
description: This article describes how to work with the load building workbench.
author: Weijiesa
ms.date: 10/30/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSLoadBuildWorkbench,TMSLoadBuildTemplateCreate,TMSLoadBuildStrategy,TMSLoadBuildTemplateApply
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2020-10-30
ms.dyn365.ops.version: 10.0.15
---
# Load building workbench

[!include [banner](../../includes/banner.md)]

The load building workbench lets you apply load building strategies when you create loads.

## Create a load building strategy

You use load building strategies to automatically build loads. This capability can be beneficial in the following situations:

- If you regularly ship a specific set of products, load strategies help save time, because you don't have to build the same load every time.
- If you want to avoid half-full loads to maximize efficiency, load strategies can help fill each load as much as possible.

A load building strategy class that is named `TMSLoadBuildingVolumeStrategy` provides a load building strategy that is named *Volume-based load building strategy*. This strategy lets you use the maximum values that are specified for height and weight in the load template, or you can override the settings by entering new values. This strategy is the only strategy that is included out of the box. (However, you might have some custom strategies.)

To use the out-of-box *Volume-based load building strategy* strategy, select it in the **Load building strategy** field on the **Load building workbench** page (**Transportation management &gt; Planning &gt; Load building workbench**).

To create a load building strategy, follow these steps.

1. Go to **Transportation management &gt; Setup &gt; Load building &gt; Load building strategies**.
1. On the Action Pane, select **Generate class list** to make sure that you have the latest versions of all available classes.
1. On the Action Pane, select **New**.
1. Enter a unique name for the strategy, select the load building strategy class for it, and enter a description.
1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Parameters**.
1. On the **Load building strategy parameters** page, select **Volume capacity** in the list, and then, in the **Value** field, enter the percentage of the load's total volume capacity that should be applied for the new load building strategy.
1. Select **Weight capacity** in the list, and then, in the **Value** field, enter the percentage of the load's total weight capacity that should be applied for the new load building strategy.
1. Close the **Load building strategy parameters** page.
1. Close the **Load building strategies** page.

You can now assign the load building strategy to a load building template. Alternatively, you can use it directly in the load planning workbench.

## Use a load building strategy in the load building workbench

1. Go to **Transportation management &gt; Planning &gt; Load building workbench**.
1. Follow one of these steps:

    - Select a strategy in the **Load building strategy** field.
    - If you've defined a load building template and assigned the load building strategy to it, on the Action Pane, on the **Manage templates** tab, select **Apply template**. Then, in the **Apply load building template** drop-down dialog box, select a template in the **Load building template name** field.

1. On the **Load templates sequence** FastTab, select one or more [load templates](load-template.md). The workbench will try to fit the load into these types of containers, in the sequence that is specified here. Typically, you should put the smallest containers at the top of the list to ensure that the smallest possible container is selected first.
1. On the Action Pane, select **Propose loads**.
1. Review the proposed loads and proposed load lines.
1. On the Action Pane, select **Create loads** to create loads that are based on the source document lines on the **Proposed load lines** FastTab.
1. Close the **Load building workbench** page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]