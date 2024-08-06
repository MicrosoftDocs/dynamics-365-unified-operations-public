---
title: Plans based on quotations and RFQs
description: Learn how to set up master planning to consider quotations and requests for quotation (RFQs) when it generates planned orders.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 09/20/2022
ms.reviewer: kamaybac
ms.search.form: SalesQuotationListPage, ReqPlanSched, SalesQuotationTable, smmOpportunityTable
---

# Plan based on quotations and RFQs

[!include [banner](../../includes/banner.md)]

Quotations and requests for quotations (RFQs) represent possible or even likely future orders. Therefore, it makes sense to consider them during master planning, so that extra supply can be planned based on existing RFQs and the likelihood that each quotation will become an actual order. This article describes how to set up master planning to consider quotations and RFQs when it generates planned orders.

## Set up master planning to consider sales quotations and/or RFQs

Use the following procedure to set up master planning to consider sales quotations and/or RFQs.

1. Go to **Master Planning \> Setup \> Plans \> Master plans**.
1. Select an existing plan in the list pane, or select **New** on the Action Pane to create a new one.
1. On the **General** FastTab, set the following fields:

    - **Include sales quotations** – Set this option to *Yes* to consider sales quotations when the current plan is run. Set it to *No* to ignore them.
    - **Probability %** – Set the minimum level of confidence that is required for a quotation to be included in master planning. The master planning calculation will include all quotations that were created from opportunities that have this probability percentage or higher. To include all quotations, including quotations that have no probability assigned to them or no opportunity associated with them, set this field to *0* (zero). For more information about probabilities for quotations, see the next section.
    - **Include requests for quotations** – Set this option to *Yes* to consider RFQs when the current plan is run. Set it to *No* to ignore them. If you choose to consider RFQs, the system will create planned purchase orders for them, but it won't specify the vendor until the RFQ is resolved. Planned purchase orders that are created for the RFQs might affect the quantities of other planned orders.

1. Continue to set up your master plan in the usual way.

## Assign and view probabilities for quotations

As was mentioned in the previous section, a master plan will consider only quotations that meet or exceed the probability threshold that is defined for the plan (if a threshold is defined). However, the probability isn't set directly on each quotation. Instead, it's inherited from the opportunity that was used to generate the quotation. Therefore, quotations that are created directly on the **All quotations** page won't have a probability assigned to them or an opportunity associated with them, and they won't ever be considered by master planning (unless the **Probability %** field is set to *0* \[zero\]). To have a probability assigned to it, a quotation must be generated from an opportunity.

### Create a quotation from an opportunity

Use the following procedure to assign a probability to an opportunity and then create a quotation from that opportunity.

1. Go to **Sales and marketing \> Relationships \> Opportunities \> All opportunities**.
1. Select an existing opportunity, or select **New** on the Action Pane to create a new one.
1. Fill in the opportunity page to identify the opportunity as you want. Be sure to set the **Probability** field to an appropriate value. Only master plans that are set up to look for probabilities of this value or higher will consider quotations that are generated from this opportunity.
1. On the Action Pane, select **Save**.
1. On the Action Pane, on the **Opportunity** tab, in the **New** group, select **Sales quotation** or **Project quotation**, depending on the type of quotation that you want to create.
1. In the **Create quotation** dialog box, set the fields as you require, and then select **OK**.
1. A new quotation is created and opened. On the **Lines** FastTab, use the toolbar to add sales lines or project lines as required to define the content of the quotation.
1. On the Action Pane, select **Save**. Then close the quotation.

### View the probability that is assigned to a quotation

The only way to view the probability that is assigned to a quotation is to open the opportunity that was used to create that quotation, as described in the following procedure.

1. Go to **Sales and marketing \> Sales quotations \> All quotations**.
1. If the **Opportunity ID** column isn't shown (it's hidden in a default installation), follow these steps to temporarily show it. (Alternatively, to keep the **Opportunity ID** column available, create a [saved view](../../../fin-ops-core/fin-ops/get-started/saved-views.md?toc=/dynamics365/supply-chain/toc.json) that includes it.)

    1. Select and hold (or right-click) in the grid, and then select **Insert columns**.
    1. In the **Insert columns** dialog box, find the row where the **Field** field is set to *Opportunity*, and select the **Select** checkbox for that row.
    1. Select **Update** to add the selected column to the **All quotations** page.

1. In the grid, find the row for the relevant quotation. Then, in the **Opportunity ID** column, select the value for that row.

    > [!NOTE]
    > If you're looking for a project quotation, you might have to select the **Quotation type** column header and clear its filter. In a default installation, this filter is set so that only sales quotations are shown.

1. The related opportunity is opened. You can now view and edit the **Probability** value as you require.
