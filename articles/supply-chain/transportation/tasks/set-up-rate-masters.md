---
title: Set up rate masters, rate bases, and break masters
description: Learn how to set up a rate master, including a step-by-step process for setting up break masters. 
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSBreakMaster,TMSRateMaster,TMSRateMasterBase,TMSRateBaseType, TMSRouteWorkbench
ms.topic: how-to
ms.date: 05/15/2025
ms.custom: 
  - bap-template
---

# Set up rate masters, rate bases, and break masters

[!include [banner](../../includes/banner.md)]

This article explains how to set up rates that are returned when using the rate route workbench as part of load planning or building. Rate engines use the configuration of rating profiles, rate masters, rate base assignments, rate bases, and break masters to determine the query structure. The logistics manager usually sets up these options based on the contracts signed with the carriers.

Because of the relationships between each of these rating elements, they must be configured in the following order:

1. Set up rating metadata. Learn more in [How is metadata used in transportation management engines?](../transportation-management-engines.md#use-metadata).
1. Set up a break master.
1. Set up a rate master and associate it to one rating metadata ID. For each rate master, you must do the following:
    - Set up one or multiple rate bases, each based on one break master.
    - Set up one or multiple rate base assignments.

After this, you must set up a rating profile, which is unique to a shipping carrier and is associated with one rate master. Learn more in [Rating profiles](setup-a-rating-profile.md).

The following illustration shows the relationship between and the hierarchy of elements that make up rating in transportation management. You must configure rating from the bottom up.

:::image type="content" source="../media/rate-master-diagram.svg" alt-text="Screeenshot of the relationships between the different elements of the rating engine." lightbox="../media/rate-master-diagram.svg":::

> [!NOTE]
> The descriptions in this article relate to standard engines and might not fully apply to custom engines.

## Set up a break master

Break masters define a pricing structure and its breakpoints. The pricing structure uses tiered pricing that is based on the break unit used by the engine. If the shipping carrier charges a certain rate per unit of distance or weight, for example, the break master can reflect this in the rate base.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Break master**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Break master**: Enter a unique identifier for break master.
    - **Name**: Enter a descriptive name for the break master.
1. Enter the following values on the **General** FastTab.
    - **Data type**: Select the data type used to define the breakpoints (*string*, *integer, or *real*).
    - **Comparison**: Enter the operator used when evaluating the breakpoints (typically *&lt;*, for *less than*, but you can enter any comparison operator in this field).
    - **Break unit**: Enter the unit or measure used to define the breakpoints (for example kgs/lbs or kms/miles). Ideally, the break unit should match the unit of the engine.
1. On the **Details** FastTab, create as many breaks as are needed for your pricing structure. For each row, enter a **Value** using the **Data type** and **Break unit** you specified on the **General** FastTab.
1. Select **Save**.

> [!NOTE]
> The **Comparison** and **Break unit** fields don't affect the standard engine behavior. They're only provided for informational purposes.

## Set up a rate master

Rate masters represent carrier rates. Each rate master can be associated with only one rating metadata ID but can have multiple rate bases and rate base assignments.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Rate master**: Enter a unique identifier for rate master.
    - **Name**: Enter a descriptive name for the rate master.
1. On the **Overview** FastTab, set **Rating metadata ID** to the rating metadata ID record that applies for this rate master. The rating metadata ID determines the data needed for the rate master. It defines the metadata expected by the transportation management engine using this rate master. Learn more in [How do I configure metadata for a transportation management engine?](../transportation-management-engines.md#config-metadata).

### Set up a rate base

The rate base defines the prices charged by the carrier at each breakpoint defined in an associated break master. You can set up one or multiple rate bases for each rate master to reflect the carrier pricing structure based on factors such as mileage and/or weight.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. Select the rate master that you want to add a rate base to.
1. On the Action Pane, select **Rate base**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Rate base**: Enter a unique identifier for rate base.
    - **Name**: Enter a descriptive name for the rate base.
1. Make the following settings on the **General** FastTab.
    - **Rate master**: Shows the rate master record that you selected previously. This is the master you're creating a rate base for. You can change this value to move a selected rate base to another rate master if needed.
    - **Break master**: Select the break master that defines the pricing structure and breakpoints for this rate base.
    - **Minimum charge**: Specify the lowest amount that can be charged for a shipment, regardless of the calculated rate based on other criteria such as distance, weight, or volume. This ensures that the carrier receives a minimum payment for their services, even if the calculated rate would otherwise be lower. The minimum charge defined here on the **General** FastTab applies if a minimum charge hasn't been set on the **Details** FastTab for a given line.
    - **Maximum charge**: Set an upper limit on the amount that can be charged for a shipment for the rate base. This ensures that the cost for shipping doesn't exceed a specified threshold, regardless of the calculated rate based on other criteria such as distance, weight, or volume. The maximum charge defined here on the **General** FastTab applies if a maximum charge isn't set on the **Details** FastTab for a given line.
    - **Currency**: If a currency different from the accounting currency is to be used for the rate base, then select that currency here.
1. On the **Details** FastTab, you can specify a pricing structure for the price break points defined in the break master. The columns available here depend on how the break master and rating metadata for the rate base are configured. For example, if the break master is set to *mileage*, you can set up one rate for less than 100 miles, and another for less than 200, and so on. Select **New** to add a new row to the grid. Then enter values for the following settings for the new row to define the price that applies at each breakpoint. The following are standard columns available in all rate bases, irrespective of the break master and rating metadata configuration:
    - **Minimum charge**: Specify the lowest amount that can be charged for a shipment for the specific rate base line. If a minimum charge is defined here on the **Details** FastTab, it applies even if a different minimum charge is defined on the **General** FastTab.
    - **Maximum charge**: Set an upper limit on the amount that can be charged for a shipment for the rate base. If a maximum charge is defined here on the **Details** FastTab, it applies even if a different maximum charge is defined on the **General** FastTab.
    - **Effective start date and time**: Set the first date and time where the rate applies.
    - **Effective end date and time**: Set the last date and time where the rate applies.

        > [!IMPORTANT]
        > Avoid setting up rate bases with overlapping effective dates and times for matching detail lines.

1. Fill out the remaining fields in the new row to define the rate that applies at each break point.
1. The **Search** FastTab shows information from the **Details** FastTab. Select a line in the **Search** table to view matching values from the **Details** FastTab.
1. On the Action Pane, select **Save**.

### Set up rate base assignments

Rate base assignments allow you to create several different price points for each carrier depending on destinations, services, or different rate bases. Rate base assignments define which rate base to apply. Use the **Rate base assignments** FastTab to define the rate base assignment for each rate master.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. On the **Rate base assignments** FastTab toolbar, select **New** to add a new row to the grid. Then enter values for the following settings for the new row. The columns available here depend on the setup of the rate base assignment metadata, as selected in the **Rating metadata ID** field. The following are standard columns that are always provided.
    - **Name**: Specify a unique identifier for the rate base assignment.
    - **Rate base**: Define the basis on which the rates are calculated.
    - **Service**: Specify the type of service associated with the rate base assignment. It could refer to different levels of service such as standard, expedited, or overnight delivery. The services listed are based on how your [shipping carrier services](set-up-shipping-carriers.md#create-carrier-services) are configured.
    - **Effective start date and time**: Specify the date and time when the rate base assignment becomes active. This setting ensures that the rates are applied correctly from the specified start time.
    - **Effective end date and time**: Specify the date and time when the rate base assignment expires. This setting helps you manage the validity period of the rates and ensures that outdated rates aren't applied.

        > [!IMPORTANT]
        > Avoid setting up rate bases with overlapping effective dates and times for matching detail lines.

1. On the Action Pane, select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
