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

1. Set up rating metadata. See here for more information about rating metadata: ([How is metadata used in transportation management engines?](https://review.learn.microsoft.com/en-us/dynamics365/supply-chain/transportation/transportation-management-engines?branch=main#how-is-metadata-used-in-transportation-management-engines)).
1. Set up a break master.
1. Set up a rate master and associate it to one rating metadata ID. For this rate master:
        Set up one or multiple rate bases, each based on one break master.
        Set up one or multiple rate base assignments.
1. Set up a rating profile, which can be associated with only one rate master.

The following illustration shows the relationships between the different elements of the rating engine.

:::image type="content" source="../media/rate-master-diagram.svg" alt-text="Diagram of relationships between the different elements of the rating engine." lightbox="../media/rate-master-diagram.svg":::

Standard engines note -

## Set up a break master

Break masters define a pricing structure and its breakpoints. The pricing structure uses tiered pricing that is based on the break unit used by the engine. If the shipping carrier charges a certain rate per unit of distance or weight, for example, the break master can reflect this in the rate base.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Break master**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Break master** – Enter a unique identifier for break master.
    - **Name** – Enter a descriptive name for the break master.
1. Enter the following values on the **General** FastTab.
    - **Data type** – Select the data type used to define the breakpoints: *string*, *integer* or *real*.
    - **Comparison** – Enter the operator that reflects what the engine uses when evaluating the breakpoints (typically *\<*, for *less than*, but you can input anything in this field). 
    - **Break unit** – Enter the unit or measure used to define the breakpoints (for example kgs/lbs or kms/miles). Ideally, the break unit should match the unit of the engine. 
1. On the **Details** FastTab, create as many breaks as are needed for your pricing structure. For each row, enter a **Value** using the **Data type** and **Break unit** you specified on the General FastTab.
1. Select **Save**.

Note that both the **Comparison** and **Break unit** fields do not impact the standard engine behavior and are only used for visual purposes.

## Set up a rate master

Rate masters represent carrier rates. Each rate master can be associated with only one rating metadata ID, but have multiple rate bases and rate base assignments.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. On the Action Pane, select **New**.
1. Enter the following values in the header of the new record.
    - **Rate master** – Enter a unique identifier for rate master.
    - **Name** – Enter a descriptive name for the rate master.
1. Select the following setting on the **Overview** FastTab.
    - **Rating metadata ID** – Select the rating metadata ID record that applies for this rate master. The rating metadata ID determines the data needed for the rate master. It defines the metadata expected by the transportation management engine using this rate master. For more information, see [Configure metadata for a transportation management engine](dynamics365/supply-chain/transportation/transportation-management-engines?branch=main#how-do-i-configure-metadata-for-a-transportation-management-engine))

### Set up a rate base

The rate base defines the prices charged by the carrier at each breakpoint defined in an associated break master. You can set up one or multiple rate bases for each rate master to reflect carrier pricing structure by factors such as mileage and/or weight.

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
    - **Minimum charge** – This field is used to specify the lowest amount that can be charged for a shipment, regardless of the calculated rate based on other criteria such as distance, weight, or volume. This ensures that the carrier receives a minimum payment for their services, even if the calculated rate would otherwise be lower. The minimum charge defined here in the **General** Fasttab applies if a minimum charge has not been set on the **Details** FastTab for the given line.
    - **Maximum charge** – This field is used to set an upper limit on the amount that can be charged for a shipment for the rate base. This ensures that the cost for shipping does not exceed a specified threshold, regardless of the calculated rate based on other criteria such as distance, weight, or volume. The maximum charge defined here in the **General** Fasttab applies if a maximum charge has not been set on the **Details** FastTab for the given line.
    - **Currency** – Define here if a currency different from the accounting currency is to be used for the rate base. 
1. On the **Details** FastTab toolbar, you can specify a pricing structure for the price break points defined in the break master. The columns here will depend on how the breakmaster and rating metadata for the rate base have been configured. For example, if the break master has been set to mileage, you can set up one rate for less than 100 miles, and another for less than 200 and so on. Select **New** to add a new row to the grid. Then enter values for the following settings for the new row to define the price that applies at each breakpoint. The following are standard columns available in all rate bases, irrespective of the breakmaster and rating metadata configuration:
    - **Minimum charge** – This field is used to speficy the lowest amount that can be charged for a shipment for the specific rate base line. If a minimum charge is defined here in the **Details** Fasttab, it is applied even if a different minimum charge is defined on the **General** Fasttab.
    - **Maximum charge** – This field is used to set an upper limit on the amount that can be charged for a shipment for the rate base. If a maximum charge is defined here in the **Details** Fasttab, it is applied even if a different maximum charge is defined on the **General** Fasttab.
    - **Effective start date and time** – Specify if the rate is to only be applicable from a specified time and date onwards.
    - **Effective end date and time** – Specify if the rate is to only be applicable up to a specified time and date.
        > [!NOTE]
        > Avoid setting up multiple rate bases with overlapping effective dates and times for unique detail lines.
1. Fill out the remaining fields in the new row to define the rate that applies at each break point.   
1. The **Search** FastTab is populated with what is entered in the **Details** FastTab. Selecting a different line in the Search table will populate different values in the Details FastTab.
1. On the Action Pane, select **Save**.

### Set up rate base assignments

Rate base assignments allow you to create several different price points for each carrier depending on destinations, services, or different rate bases. Rate base assignments define which rate base to apply. You set them up under each rate master through the **Rate base assignments** Fasttab.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. On the **Rate base assignments** FastTab toolbar, select **New** to add a new row to the grid. Then enter values for the following settings for the new row. The columns here depend on the set-up of the rate base assignment metadata based on what you selected in the **Rating metadata ID** field. The following are standard columns that are always applicable.
    - **Name** – This field is used to specify a unique identifier for the rate base assignment. 
    - **Rate base** – The rate base field is used to define the basis on which the rates are calculated. 
    - **Service** – This field specifies the type of service associated with the rate base assignment. It could refer to different levels of service such as standard, expedited, or overnight delivery. This list of available services depends on the configuration of the [shipping carrier services](set-up-shipping-carriers?branch=main#create-the-necessary-services-for-the-shipping-carrier).
    - **Effective start date and time** – This field indicates the date and time when the rate base assignment becomes active. It ensures that the rates are applied correctly from the specified start time.
    - **Effective end date and time** – This field specifies the date and time when the rate base assignment expires. It helps in managing the validity period of the rates and ensures that outdated rates are not applied.
        > [!NOTE]
        > Avoid setting up multiple rate bases with overlapping effective dates and times for unique detail lines.
1. On the Action Pane, select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
