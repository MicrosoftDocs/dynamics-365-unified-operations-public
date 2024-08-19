---
title: Warehouse Management mobile app insights
description: The Warehouse Management mobile app can show AI-generated insights to warehouse workers to help them better plan their shift.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/19/2024
ms.custom: 
  - bap-template
---

# Warehouse Management mobile app insights

[!include [banner](../includes/banner.md)]

<!--KFM: It's confusing that the settings menu calls this feature "copilot", the main menu calls it "Workload" and the documentation calls it "insights". -->

The Warehouse Management mobile app provides a *workload* page that shows AI-generated insights to warehouse workers to help them better plan their shift. Workers can choose to see the insights each time they sign in and can view them on-demand at any time by opening the workload page from the app menu. The information shown can include the following details:

- The number of pick and receive work headers or work lines.
- The number of active warehouse mobile app sessions in the warehouse.
- Insights into the available work types.
- The current workload, displayed either as work headers or work lines.
- Details of available work per work type.
- Additional information about available work.

Workers can use these AI-generated insights to get an overview of their workday and optimize the way they engage with their daily tasks. Detailed information about available tasks enhances operational efficiency, reduces time spent on information retrieval, and optimizes resource allocation across the warehouse floor.

The workload page offers insights into relevant warehouse operations, such as the number of active warehouse mobile sessions working in the same warehouse. This fosters a more connected and efficient workplace by promoting awareness and coordination among workers.

When workers first open the workload page, they're shown an overview of unstarted tasks scheduled for the current warehouse. The following illustration shows how it looks. First, the app shows an overview (left). The worker can then tap the screen to see detailed information about open work by type, which lets them quickly grasp their day's objectives (right). Select the check-mark button to... <!--KFM: What does it do? -->. <!--KFM: Please review this paragraph; is this what we mean to say? -->

:::image type="content" source="media/wma-insights-worklines.png" alt-text="Overview of un-started tasks scheduled for the current warehouse" lightbox="media/wma-insights-worklines.png":::

## Prerequisites

To use Warehouse Management mobile app insights, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.39 or later.
- You must be running Warehouse Management mobile app version 2.3.2.0 or later.

## Worker preferences and options

### Choose whether to show the workload page on sign-in

Workers can choose whether or not to see the workload page each time they sign in to the app. To set this preference, follow these steps:

1. Open the **Settings** menu. <!--KFM: How do we open this menu? -->
1. Select the **Show copilot on startup** entry.

    :::image type="content" source="media/wma-insights-startup.png" alt-text="The Show copilot on startup option in the settings menu" lightbox="media/wma-insights-startup.png":::

1. Choose one of the following options:
   - *Yes*: Display the workload page each time you sign in (default setting).
   - *No*: Don't display the workload page each time you sign in. <!--KFM: What will we see instead. -->

### Choose whether to show workload data as headers or lines

<!--KFM: We should better explain the difference between viewing headers and viewing lines and when each view is useful. Maybe include side-by-side screenshots. -->

Workers can choose whether to see workload data as headers or lines. To set this preference, follow these steps:

1. Open the **Settings** menu. <!--KFM: How do we open this menu? -->
1. Select the **Show copilot data as** entry.

    :::image type="content" source="media/wma-insights-data-option.png" alt-text="The Show copilot on startup option in the settings menu" lightbox="media/wma-insights-data-option.png":::

1. Choose one of the following options:
   - *Work lines*: Display the workload data as lines.
   - *Work headers*: Display the workload data as headers.

## Open the workload page

Regardless of whether a worker chooses to see the workload page at sign-in, they can also choose to open the workload page at any time by following these steps:

1. Open the **Main menu**. <!--KFM: How do we open this menu? -->
1. Select the **Workload** button at the top of the screen.

    :::image type="content" source="media/wma-insights-workload-button.png" alt-text="The Show copilot on startup option in the settings menu" lightbox="media/wma-insights-workload-button.png":::
