---
# required metadata

title: Configure Employee self service
description: In Microsoft Dynamics 365 Human Resources, you can configure tiles for top-level navigation in Employee self service.
author: twheeloc
ms.date: 12/06/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure employee self service


[!INCLUDE [PEAP](../includes/peap-2.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In Microsoft Dynamics 365 Human Resources, you can configure tiles for top-level navigation in **Employee self service**. Benefit plan tiles direct users to benefit plans that they're eligible for.

## Set up a benefit plans tile

1. In the **Benefits management** workspace, under **Setup**, select **Employee self service parameters**.

2. Select the **Benefit plans tile setup** tab, and then select **New**.

3. Specify values for the following fields.

   | Field | Description |
   | --- | --- |
   | **Plan type code** | The plan type that is displayed when this tile is selected in **Benefits self service**. |
   | **Tile ID** | The unique identifier for the tile. |
   | **Tile label text** | The text that will appear for the tile in **Benefits self service**. |
   | **Description** | A description of the tile. |
   | **Tile background image** | The URL of the image to use for the tile (optional). |
   | **Track open enrollment** | Select this option to track the open enrollment progress for this plan type. For example, you may have plans created where **Plan type = Other**. These plans might be optional plans that you don’t want to track enrollment progress for. If you do not select this plan type, this type of plan will be ignored when tracking enrollment progress or enrollment completion on the **Open enrollment** tab. This setting applies to the plan type that is selected for all periods and legal entities. |

4. Select **Save**.

## Set up a flex credit plan tile

1. In the **Benefits management** workspace, under **Setup**, select **Employee self service parameters**.

2. Select the **Flex credit plan tile setup** tab, and then select **New**.

3. Specify values for the following fields.

   | Field | Description |
   | --- | --- |
   | **Benefit credit ID** | The flex credit program plans that will be displayed when this tile is selected in **Benefits self service**. |
   | **Tile ID** | The unique identifier for the tile. |
   | **Tile label text** | The text that will appear for the tile in **Benefits self service**. |
   | **Description** | A description of the tile. |
   | **Tile background image** | The URL of the image to use for the tile (optional). |
   | **Track open enrollment** | Select this option to track the open enrollment progress for this plan type. For example, you may have plans created where **Plan type = Other**. These plans might be optional plans that you don’t want to track enrollment progress for. If you do not select this plan type, this type of plan will be ignored when tracking enrollment progress or enrollment completion on the **Open enrollment** tab. This setting applies to the plan type that is selected for all periods and legal entities. |

4. Select **Save**.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
