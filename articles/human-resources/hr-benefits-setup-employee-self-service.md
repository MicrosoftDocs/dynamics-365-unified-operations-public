---
# required metadata

title: Configure Employee self service
description: In Microsoft Dynamics 365 Human Resources, you can configure tiles for top-level navigation in Employee self service.
author: twheeloc
ms.date: 05/14/2026
ms.topic: how-to
# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure employee self service

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

In Microsoft Dynamics 365 Human Resources, you can configure tiles for top-level navigation in **Employee self service**. Benefit plan tiles direct users to benefit plans that they're eligible for.

## Set up a benefit plans tile

1. In the **Benefits management** workspace, under **Setup**, select **Employee self service parameters**.

2. Select the **Benefit plans tile setup** tab, and then select **New**.

3. Specify values for the following fields.

   | Field | Description |
   | --- | --- |
   | **Plan type code** | The plan type that appears when users select this tile in **Benefits self service**. |
   | **Tile ID** | The unique identifier for the tile. |
   | **Tile label text** | The text that appears for the tile in **Benefits self service**. |
   | **Description** | A description of the tile. |
   | **Tile background image** | The URL of the image to use for the tile (optional). |
   | **Track open enrollment** | Select this option to track the open enrollment progress for this plan type. For example, you might have plans created where **Plan type = Other**. These plans might be optional plans that you don't want to track enrollment progress for. If you don't select this plan type, the system ignores this type of plan when tracking enrollment progress or enrollment completion on the **Open enrollment** tab. This setting applies to the plan type that you select for all periods and legal entities. |

4. Select **Save**.

## Set up a flex credit plan tile

1. In the **Benefits management** workspace, under **Setup**, select **Employee self service parameters**.
1. Select the **Flex credit plan tile setup** tab, and then select **New**.
1. Specify values for the following fields.

   | Field | Description |
   | --- | --- |
   | **Benefit credit ID** | The flex credit program plans that appear when you select this tile in **Benefits self service**. |
   | **Tile ID** | The unique identifier for the tile. |
   | **Tile label text** | The text that appears for the tile in **Benefits self service**. |
   | **Description** | A description of the tile. |
   | **Tile background image** | The URL of the image to use for the tile (optional). |
   | **Track open enrollment** | Select this option to track the open enrollment progress for this plan type. For example, you might have plans created where **Plan type = Other**. These plans might be optional plans that you don't want to track enrollment progress for. If you don't select this plan type, the system ignores this type of plan when tracking enrollment progress or enrollment completion on the **Open enrollment** tab. This setting applies to the plan type that you select for all periods and legal entities. |

1. Select **Save**.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
