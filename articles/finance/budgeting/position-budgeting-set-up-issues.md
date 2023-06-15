---
# required metadata

title: Position budgeting troubleshooting
description: This article provides answers to questions that you might have when you configure position budgeting. It addresses frequently asked questions about how to create budget cost elements, compensation groups, and compensation grids. 
author: panolte
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmBudgetPurposeType, HcmPositionForecast
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: c44df01b-8700-4022-b4c6-c4b1cb84d31d
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Position budgeting troubleshooting

[!include [banner](../includes/banner.md)]

This article provides answers to questions that you might have when you configure position budgeting. It addresses frequently asked questions about how to create budget cost elements, compensation groups, and compensation grids. 

## Why can’t I find the forecast position page in Human resources?

Forecast positions have been moved to Budgeting.

## Why can’t I delete a budget cost element?
You can’t delete a budget cost element that is assigned to a forecast position. Before you can delete a budget cost element, you must remove it from all forecast positions. **Tip:** To find all the positions that a budget cost element is assigned to, select the cost element on the **Budget cost elements** page, and then click **Update positions**. The positions that use the cost element are listed in the upper grid.

## How can I remove a cost element from multiple forecast positions without opening each one?
You can’t remove a cost element. However, if you change the start and end dates so that they are outside the budget planning cycle dates, the cost element will no longer be assigned to the forecast positions in that budget planning cycle. To make this change, open the budget cost element, and then, on the **Cost calculation** FastTab, click **Change dates**, and change the effective date or expiration date. Then click **OK** to automatically update all forecast positions that the cost element is assigned to. **Tip:** If you use this method, be aware that it removes the budget cost element from **all** forecast positions where the start and end dates are no longer within the appropriate range. If this effect isn't what you intend, you must open each forecast position that you want to remove the budget cost element from and manually make the change.

## Why can’t I enter an annual amount on the Cost calculation FastTab for the budget cost element?
You can’t enter an annual amount if there are budget cost elements on the **Calculation basis** FastTab, because the system requires a percentage in order to calculate the value. To change the value, remove all budget cost elements from the **Calculation basis** FastTab.

## Why can’t I change the budget cost type from earning to another budget cost type?
Some budget cost elements use the earning cost element as a calculation basis. To change the **Budget cost type** field, remove the earning cost element from the **Calculation basis** FastTab of all budget cost elements.

## Why can’t I change the date on budget cost element lines for a budget cost element?
You can’t change the date on the budget cost element line when a budget cost element is used by a forecast position. This limitation helps guarantee that the forecast positions are always within the guidelines of the budget cost element. To change the date, on the **Cost calculation** FastTab, click **Change dates**, and enter the new dates. Then click **OK** to update the positions that the cost element is assigned to.

## Why can’t I change the costs for a budget cost element on the Compensation group page?
You can create and change budget cost elements only on the **Budget cost elements** page.

## Why do I receive an error message when I change the dates for a cost element on a forecast position?
The dates on the forecast position cost element line must be within the following ranges:

-   The activation and retirement dates of the position.
-   The activation and expiration dates of the budget cost element.
-   The start and end dates of the budget cycle that is associated with the budget planning process of the forecast position.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
