---
title: Set up rate masters, rate bases, and break masters
description: Learn how to set up a rate master, including a step-by-step process for setting up break masters using the USMF demo data company. 
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSBreakMaster,TMSRateMaster,TMSRateMasterBase,TMSRateBaseType, TMSRouteWorkbench
ms.topic: how-to
ms.date: 04/04/2025
ms.custom: 
  - bap-template
---

# Set up rate masters, rate bases, and break masters

[!include [banner](../../includes/banner.md)]

This article explains how to set up rates that are returned when using the rate route workbench as part of load planning or building. Rate engines use the configuration of rating profiles, rate masters, rate base assignments, rate bases, and break masters to determine the query structure. The logistics manager usually sets these options up based on the contracts signed with the carriers.

Because of the relationships between each of these rating elements, they must be configured in the following order:

1. Set up rating metadata and break masters.
1. Set up a rate base, which must be associated with only one break master.
1. Set up a rate base assignment, which is associated with only one rate base.
1. Set up a rate master, which can be associated with one or more rate base assignments and only one rating metadata.
1. Set up a rating profile, which can be associated with only one rate master.

<!-- KFM: 

The above order of operations doesn't quite work because we need the rate master before we can create a rate base, and we need a rate base before we can set up the base/master association. We're also missing a couple of elements in the documentation. Here is what I think the order should be:

1. Set up rating metadata. (Description and new section needed)
2. Set up a break master. (Existing section)
3. Set up a rate master. (Split from existing section)
4. Add one or more rate bases to a rate master. (Existing section)
5. Set up rate base assignments for a break master. (Split from existing section)
6. Set up a rating profile (New section that briefly describe what this is for and link to [Rating profiles](setup-a-rating-profile.md), I think.)

 -->

The following illustration shows the relationships between the different elements of the rating engine. <!-- KFM: This is my guess. Please expand on this to explain more about this diagram and what we are showing here. -->

:::image type="content" source="../media/rate-master-diagram.svg" alt-text="Diagram of relationships between the different elements of the rating engine." lightbox="../media/rate-master-diagram.svg":::

## Set up a break master

Break masters define a pricing structure and its breakpoints. The pricing structure uses tiered pricing that is based on physical dimensions. If the shipping carrier charges a certain rate per unit of distance or weight, for example, the break master can reflect this in the rate base.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Break master**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Break master** – Enter a unique identifier for break master.
    - **Name** – Enter a descriptive name for the break master.
1. Enter the following values on the **General** FastTab.
    - **Data type** – Select the data type used to define the breakpoints.
    - **Comparison** – Enter the operator to use when evaluating the breakpoints (typically *\<*, for *less than*). <!-- KFM: we should explicitly list the valid values and what they mean. -->
    - **Break unit** – Enter the unit or measure used to define the breakpoints.
1. On the **Details** FastTab, create as many breaks as are needed for your pricing structure. For each row, enter a **Value** using the **Data type** and **Break unit** you specified on the General FastTab.
1. Select **Save**.

## Set up a rate base

The rate base defines the prices charged by the carrier at each breakpoint defined in an associated break master. <!-- KFM: Explain that we might have several of these for each break master and what that means. -->

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. Select the rate master that you want to add a rate base to.
1. On the Action Pane, select **Rate base**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Rate base** – Enter a unique identifier for rate base.
    - **Name** – Enter a descriptive name for the rate base.
1. Make the following settings on the **General** FastTab.
    - **Rate master** – Shows the rate master record that you selected previously. This is the master you are creating a rate base for. You can change this value to move a selected rate base to another rate master if needed.
    - **Break master** – Select the break master that defines the pricing structure and breakpoints for this rate base.
    - **Minimum charge** – <!-- KFM: Explain what this setting does and what to enter here. How do these settings in this FastTab interact with the settings of the same name in the Details FastTab? -->
    - **Maximum charge** – <!-- KFM: Explain what this setting does and what to enter here -->
    - **Currency** – Select the currency used to specify the **Minimum charge** and **Maximum charge**.
1. On the **Search** FastTab... <!-- KFM: Describe what this does and what to do here, or mention that we shouldn't do anything here. -->
1. On the **Details** FastTab toolbar, select **New** to add a new row to the grid. Then enter values for the following settings for the new row. <!-- KFM: here we should introduce the purpose of this FastTab. I think we are defining the price that applies at each breakpoint and the conditions under which each row applies. --> <!-- KFM: Your draft listed the following fields here, but I didn't see them. I think they vary based on what Break Master is selected, so we shouldn't list them here: **Drop-off Postal Code From**, **Drop-off Postal Code To**, **Drop-off Country Region**. The following seem to be the standard fields that aren't part of the Break master. -->
    - **Minimum charge** – <!-- KFM: Description needed -->
    - **Maximum charge** – <!-- KFM: Description needed -->
    - **Effective start date and time** – <!-- KFM: Description needed -->
    - **Effective end date and time** – <!-- KFM: Description needed -->
1. Fill out the remaining fields in the new row to define the rate that applies at each break point. The available columns vary based on what you selected in the **Break master** field. For example, if the break master is weight, the unit is pounds, and the break master has been set up at 5 pound intervals, then you're provided columns where you can define the rate for loads under 5 pounds, 10 pounds, 15 pounds, and so on.  
1. On the Action Pane, select **Save**.

## Set up rate master and assign rate bases

Rate masters represent carrier rates. Each rate master can have multiple rate base assignments, which define different price points for each carrier depending on destinations, services or different rate bases.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Rate master** – Enter a unique identifier for rate master.
    - **Name** – Enter a descriptive name for the rate master.
1. Make the following settings on the **Overview** FastTab.
    - **Rate base** – Shows the number of rate base records that are associated with this rate master. This field is read-only.
    - **Rate engine** – Select the rate engine that will be used to calculate the rates for this rate master. The rate engine is a service that calculates the rates based on the rate master and the rate base assignments.
    - **Rating metadata ID** – Select the rating metadata ID record that applies for this rate master. The rating metadata ID determines the data needed for the rate master. It defines the metadata expected by the transportation management engine using this rate master. <!-- KFM: We don't describe anywhere how to set up these **Rating metadata ID** records. We should probably have a topic or section about this. -->
1. On the **Rate base assignments** FastTab toolbar, select **New** to add a new row to the grid. Then enter values for the following settings for the new row. <!-- KFM: here we should introduce the purpose of this FastTab. I think it's the conditions for selecting a rate base, but I'm not sure. -->
    - **Name** – <!-- KFM: Description needed -->
    - **Rate base** – <!-- KFM: Description needed. This is also a required field! So we have a chicken/egg problem when it comes to defining rate masters and rate bases. We need to resolve this somehow. -->
    - **Service** – <!-- KFM: Description needed -->
    - **Effective start date and time** – <!-- KFM: Description needed -->
    - **Effective end date and time** – <!-- KFM: Description needed -->

1. Fill out the remaining fields in the new row to define <!-- KFM: ... whatever we are doing here... -->. The available columns vary based on what you selected in the **Rating metadata ID** field.
1. On the Action Pane, select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
