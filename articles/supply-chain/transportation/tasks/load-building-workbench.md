--- 
# required metadata 
 
title: Load building workbench
description: This procedure shows how to work with the Load building workbench. 
author: kamaybac
manager:  
ms.date: 10/16/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSLoadBuildWorkbench   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: 
ms.search.validFrom: 2020-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
## Load building workbench

The load building workbench allows you to apply load building strategies when creating loads.

Using load building strategies to automatically build loads can be beneficial when you &gt;

-   Ship a certain set of products regularly. Rather than building loads every time, you can apply load building strategies.

-   Want to maximize efficiency by avoiding half full loads.

A load building strategy class called TMSLoadBuildingVolumeStrategy is provided giving access to a load building strategy called the Volume-based load building strategy. This strategy lets you use the maximum values that are specified for height and weight in the load template, or you can override the settings by entering new values.

To use this strategy, select it in the Load building strategy field on the Transportation management &gt; Planning &gt; Load building workbench page.

### Create a Load building strategy

To create a load building strategy, follow these steps:

1.  Open Transportation management &gt; Setup &gt; Load Building &gt; Load building strategies.

2.  Select New.

3.  Enter a unique Name, select the Load building strategy class, and a description for the strategy.

4.  Click on Save.

5.  Click on Parameters.

6.  In the Load building strategy parameters page, enter the value for Volume and the value for capacity to be applied for the newly created load building strategy. The value that you enter will be applied as a % (percentage) of the total volume and capacity for the load.

7.  Close the Load building strategy parameters page.

8.  Close the Load building strategy page.

You can now assign the load building strategy to a load building template, or use it directly in the load planning workbench.

### Use load building strategy in the load building workbench

In the Load building workbench follow these steps:

1.  Open Transportation management&gt;Planning&gt;Load building workbench.

2.  In the field Load building strategy select the load building strategy. Alternatively, if you have defined a load building template and assigned the load building strategy to the template, then select the action Manage templates&gt;Apply load building template, and select the load building template.

3.  Select the action Propose loads.

4.  Review the proposed loads and proposed load lines.

5.  Select the action Create loads, to create loads based on the source document lines visible in the Proposed load lines section.

6.  Close the Load building workbench page.


