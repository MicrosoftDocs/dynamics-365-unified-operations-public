---
title: Plan based on quotations and RFQs
description: This topic describes how to set up master planning to take quotations and requests for quotation (RFQs) into consideration when generating planned orders.
author: t-benebo
ms.date: 09/20/2022
ms.topic: article
ms.search.form: SalesQuotationListPage, ReqPlanSched, SalesQuotationTable, smmOpportunityTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-09-20
ms.dyn365.ops.version: 10.0.30
---

# Plan based on quotations and RFQs

[!include [banner](../../includes/banner.md)]

Quotations and requests for quotations (RFQs) represent possible or even likely future orders. Therefore, it makes sense to take these into consideration during master planning to plan extra supply based on existing RFQs and how likely each quotation is to become an actual order. This topic describes how to set up master planning to take quotations and RFQs into consideration when generating planned orders.

## Set up master planning to consider sales quotations and/or RFQs

Use the following procedure to set up master planning to consider sales quotations and/or RFQs.

1. Go to **Master Planning \> Setup \> Plans \> Master plans**.
1. Select an existing plan from the list pane or select **New** on the Action Pane to create a new one.
1. Expand the **General** FastTab, and make the following settings:
    - **Include sales quotations** – Set to *Yes* to consider sales quotations when running the current plan. Set to *No* to ignore them.
    - **Probability %** – Set the minimum level of confidence required for a quotation to be included in master planning. The master planning calculation will include all quotations that were created from opportunities that have this probability percentage or higher (see also the following section). Set this to zero to include all quotations, including quotations that have no probably assigned or opportunity associated with them.
    - **Include requests for quotations** – Set to *Yes* to consider RFQs when running the current plan. Set to *No* to ignore them. If you choose to consider RFQs, then the system will create planned purchase orders for them (which may affect the quantities of other planned orders), but won't specify the vendor until the RFQ is resolved.
1. Continue setting up your master plan as usual.

## Assign and view probabilities for quotations

As mentioned in the previous section, a master plan will only consider quotations that meet or exceed the probability threshold established for the plan (if any). However, the probability isn't set directly on each quotation. Instead, it is inherited from the opportunity used to generate the quotation. That means that quotations created directly on the **All quotations** page won't have a probability or opportunity associated with them, and therefore won't ever be considered by master planning (other than for plans that have **Probability %** set to zero). For a quotation to have a probability associated with it, it must be generated from an opportunity.

### Create a quotation from an opportunity

Use the following procedure to assign a probability to an opportunity and then create a quotation from that opportunity.

1. Go to **Sales and marketing \> Relationships \> Opportunities \> All opportunities**.
1. Select an existing opportunity or select **New** on the Action Pane to create a new one.
1. Fill out the opportunity page however you like to identify the opportunity, but be sure to set **Probably** to an appropriate value. Only master plans set to look for properties of this value or lower will consider quotations generated from this opportunity.
1. Select **Save** on the Action Pane.
1. On the Action Pane, open the **Opportunity** tab and, from the **New** group, select **Sales quotation** or **Project quotation**, depending on which type of quotation you want to make.
1. The **Create quotation** dialog opens. Set options as needed and then select **OK**.
1. A new quotation is created and opened. Oon the **Lines** FastTab toolbar, define the content of the quotation by adding sales lines or project lines as needed.
1. On the Action Pane, select **Save** and then close the quotation.

### View opportunities associated with a quotation

The only way to view the probably associated with a quotation is to go to the open the opportunity used to create that quotation, as described in the following procedure.

1. **Sales and marketing \> Sales quotations \> All quotations**
1. If the **Opportunity ID** column isn't shown (it's hidden in a default installation), then do the following steps to show it temporarily (or create a [saved view](../../fin-ops-core/fin-ops/get-started/saved-views.md?toc=/dynamics365/supply-chain/toc.json) that includes the **Opportunity ID** column to keep it available):
    1. Right-click on the grid and select **Insert columns...** from the context menu.
    1. The **Insert columns** dialog opens. Find the row where **Field** is *Opportunity* and select the **Select** checkbox for that row.
    1. Select **Update** to add the selected column to the **All quotations** page.
1. Find the relevant quotation in the grid and, for that row, select the value in the **Opportunity ID** column. (If you're looking for a project quotation, you may need to select the **Quotation type** column header and clear its filter, which is set to show only *Sales quotations* in a default installation.)
1. The related opportunity opens, where you can view and edit the **Probability** value as needed.
