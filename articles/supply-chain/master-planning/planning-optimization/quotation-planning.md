---
title: Plan based on quotations
description: This topic describes how to set up master planning to take sales quotations and RFQs into consideration when generating planned orders.
author: t-benebo
ms.date: 09/20/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-09-20
ms.dyn365.ops.version: 10.0.30
---

# Plan based on quotations

[!include [banner](../../includes/banner.md)]

Sales quotations and requests for quotations (RFQs) represent possible or even likely future sales orders. Therefore, it makes sense to take these into consideration during master planning to plan extra supply based on how likely each quotation or RFQ is to become an actual order. This topic describes how to set up master planning to take sales quotations and RFQs into consideration when generating planned orders.

<!-- KFM: Does this require PO, or does the legacy engine also support this? Is any FM needed? -->

## Set up master planning to consider sales quotations and/or RFQs

Use the following procedure to set up master planning to consider sales quotations and/or RFQs.

1. Go to **Master Planning \> Setup \> Plans \> Master plans**.
1. Select an existing plan from the list pane or select **New** on the Action Pane to create a new one.
1. Expand the **General** FastTab, and make the following settings:
    - **Include sales quotations** – Set to *Yes* to consider sales quotations when running the current plan. Set to *No* to ignore them.
    - **Probability %** – Set the minimum level of confidence required for a quotation to be included in master planning. The master planning calculation will include all project or sales orders of the Quotation type that have the same probability percentage or higher. <!--KFM: This sentence isn't clear. What do we mean by "project"? Is "quotation" a type of sales order, or are we talking about sales quotation records of a specific type? Is a probability also set on the quotation or sales order or project, or whatever it is we are looking at here?  -->
    - **Include requests for quotations** – Set to *Yes* to consider RFQs when running the current plan. Set to *No* to ignore them. <!--KFM: What does it mean to consider RFQs? Do we generate planned orders to cover all of them? Does the Probability % apply for these too?  -->
1. Continue setting up your master plan as usual.

## Example scenario: Run master planning supplying for a sales quotation

This example shows a typical scenario where a sales person sets up an opportunity and converts it to a sales quotation, which the system is set up to then consider during master planning.

1. To work through this scenario using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.
1. Go to **Master Planning \> Setup \> Plans \> Master plans**.
1. Create or edit a master plan so that includes the following options:

    - **Include sales quotations:** *Yes*
    - **Probability %:** *50*
    - **Include requests for quotations:** *Yes* <!-- KFM: Is this needed for this example? -->

1. Go to **Sales and marketing \> Relationships \> Opportunities**.
1. Create a new opportunity <!-- KFM: continue here. -->

Create an opportunity on the **All opportunities** page (Sales and marketing \> Relationships \> Opportunities). Fill in the opportunity related fields. Fill in the **Probability** field to 75. <!--KFM: Why are we talking about opportunities now? How are they related to sales quotations and RFQs? Is this the usual way to create a quotation? If so, we should mention this sooner.  -->

To create a sales quotation from the opportunity, click on Opportunity \> New \> Sales quotation on the upper pane. Click OK.

On the created sales quotation, fill in the desired lines – which products will be part of the quotation. The probability associated with the sales quotation is the probability from the related opportunity. It is possible to view the opportunity associated with the quotation by adding the field Opportunity ID on the **All quotations** page. For example, add a line for item D0001 site 1 warehouse 11 quantity 100.

If a quotation does not have an opportunity associated (for example, by creating it directly from the Quotations page, its probability is 0.

Run master planning.

Notice that for item D0001 master planning will have created supply for the item D0001 site 1 warehouse 11, for example by checking on net requirements page of the item, as its probability was higher than what was on the defined master plans.
