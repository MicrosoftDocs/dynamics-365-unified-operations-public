---
title: Workload insights with Copilot in the Warehouse Management mobile app
description: Learn about how the Warehouse Management mobile app can show AI-generated insights to warehouse workers to help them better plan their shift.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 08/19/2024
ms.custom: 
  - bap-template
---

# Workload insights with Copilot in the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

The Warehouse Management mobile app provides a *workload* page that shows work summaries and AI-generated insights to help warehouse workers better plan their shift. The information can include the following details:

- The number of pick and receive work headers or work lines.
- The number of active warehouse mobile app sessions in the warehouse.
- Insights into the available work types.
- The current workload. This information can be shown either as work headers or work lines.
- Details of the available work per work type.
- More information about the available work. Microsoft Copilot generates this information in natural language.

Workers can use the insights on the workload page to get an overview of their workday and optimize the way that they engage with their daily tasks. Detailed information about available tasks helps enhance operational efficiency, reduce the time that is spent on information retrieval, and optimize resource allocation across the warehouse floor.

The workload page offers insights into relevant warehouse operations, such as the number of active warehouse mobile sessions that are working in the same warehouse. This information fosters a more connected and efficient workplace by promoting awareness and coordination among workers.

The following illustration shows an example of the workload page. When workers first open the page, it shows an overview of unstarted tasks that are scheduled for the current warehouse, together with a natural-language summary that Copilot generates (left). Workers can then tap any tile to view detailed information about open work by type (right). This information helps them quickly grasp their objectives for the day. To close the workload page and open the **Main menu**, workers select the check mark button.

:::image type="content" source="media/wma-insights-worklines.png" alt-text="Screenshots of the initial and detailed views of unstarted work lines scheduled for the current warehouse." lightbox="media/wma-insights-worklines.png":::

## Prerequisites

Before you can get workload insights with Copilot in the Warehouse Management mobile app, your system must meet the following requirements:

- You must be running Dynamics 365 Supply Chain Management version 10.0.39 or later.
- You must be running Warehouse Management mobile app version 2.3.2.0 or later.
- The feature that is named *Context-aware worker summary screen in WMA* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). (As of Supply Chain Management version 10.0.39, the feature is turned on by default.)

## Worker preferences and options

### Choose whether the workload page is shown after sign-in

Workers can specify whether they want the workload page to be shown each time they sign in to the app. To set this preference, follow these steps.

1. From the **Main menu**, open the **Settings** menu.
1. Select the **Show copilot on startup** entry.

    :::image type="content" source="media/wma-insights-startup.png" alt-text="Screenshot that shows the Show copilot on startup entry on the Settings menu." lightbox="media/wma-insights-startup.png":::

1. Select one of the following options:

    - *Yes*: Show the workload page each time you sign in (default setting).
    - *No*: Go straight to the **Main menu** each time you sign in, without showing the workload page.

### Choose whether workload data is shown as headers or lines

Workers can specify whether they want summaries to be based on work headers or work lines. The choice depends on how the workers prefer to think about their daily workload. For example, if all your orders typically contain just a few items, workers might prefer to think about their work in terms of whole orders (headers). However, if quantities vary greatly from order to order, workers might prefer to think about their work in terms of individual items (lines).

To set this preference, follow these steps.

1. From the **Main menu**, open the **Settings** menu.
1. Select the **Show copilot data as** entry.

    :::image type="content" source="media/wma-insights-data-option.png" alt-text="Screenshot that shows the Show copilot data as entry on the Settings menu." lightbox="media/wma-insights-data-option.png":::

1. Select one of the following options:

    - *Work lines*: Show the workload data as lines (default setting).
    - *Work headers*: Show the workload data as headers.

## Open the workload page

Even if workers specify that the workload page should not be shown after sign-in, they can open the page at any time by following these steps.

1. On the **Main menu**.
1. Select the **Workload** button at the top of the page.

    :::image type="content" source="media/wma-insights-workload-button.png" alt-text="Screenshot that shows the Workload button at the top of the Main menu." lightbox="media/wma-insights-workload-button.png":::

## Related information

- [Responsible AI FAQ for Workload insights with Copilot](../faq-wma-copilot.md)
