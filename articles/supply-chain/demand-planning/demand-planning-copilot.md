---
title: Analyze demand plans with Copilot
description: Demand planning in Microsoft Dynamics 365 Supply Chain Management lets you use Copilot to analyze your demand plans, including prerequisites.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: overview
ms.date: 11/15/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.collection:
  - bap-ai-copilot
ms.search.form:
---

# Analyze demand plans with Copilot

[!include [banner](../includes/banner.md)]

Demand planning in Microsoft Dynamics 365 Supply Chain Management lets you use Copilot to analyze your demand plans. You can select from a set of predefined questions. The app then provides answers in real time by using natural language.

By using Copilot, you can quickly gain valuable insights across multiple dimensions. You can use these insights to improve operational efficiency, increase profitability, and improve customer satisfaction.

For example, a demand planner is interested in learning the most significant factors that contributed to a notable shift between two consecutive periods. The planner opens the relevant worksheet, selects a point of interest on the chart, and then selects a predefined question to ask Copilot. Copilot's response might resemble the following example.

:::image type="content" source="media/demand-plan-copilot-result.png" alt-text="Copilot results in Demand planning" lightbox="media/demand-plan-copilot-result.png":::

## Prerequisites

To use Copilot to analyze demand plans, you must be running the general availability (GA) version of Demand planning in Microsoft Dynamics 365 Supply Chain Management.

## Country/region availability and language support

The *Analyze demand plans with Copilot* feature is available in all regions.

The *Analyze demand plans with Copilot* feature is available only in English.

## Ask Copilot to analyze your data

To ask Copilot to analyze your data, follow these steps.

1. On the navigation pane, select **Worksheets**.
1. Open the worksheet that you want to analyze.
1. In the **Timeline** section, on the chart, select the point that represents the period that you want to analyze.
1. The **Copilot** menu shows one or more questions that you can ask about the selected point. Select the question that you want to ask. (For more information about the types of questions that can be shown, see the next section.)

    :::image type="content" source="media/demand-plan-copilot-questions.png" alt-text="Copilot questions in Demand planning" lightbox="media/demand-plan-copilot-questions.png":::

1. Copilot analyzes the data and provides its answer.

## Chat with Copilot

The following table provides a quick reference to the predefined questions that you can select on the **Copilot** menu.

| Example question | Description |
|--|--|
| Shifts from Apr '24 to May '24 | Compare two consecutive periods in the same year. The length of the period (day, week, or month) depends on the setup of the time series in your worksheet.</br></br>The example question that's shown here indicates that you selected a point that represents the one-month period of May 2024. Copilot will compare that period to the previous one-month period (April 2024). |
| Shifts from May '23 to May '24 | Compare a selected period to the same period one year earlier. The length of the period (day, week, or month) depends on the setup of the time series in your worksheet.</br></br>The example question that's shown here indicates that you selected a point that represents the one-month period of May 2024. Copilot will compare that period to the one-month period of May 2023. |
| Trends from Nov '23 to Apr '24 | Identify trends that occurred over the previous six time periods. The length of the period (day, week, or month) depends on the setup of the time series in your worksheet.</br></br>The example question that's shown here indicates that you selected a point that represents the one-month period of April 2024. Copilot will analyze data across all available dimensions for the previous six months (November 2023 to April 2024) and highlight the most significant trends. |
| Outliers from Jan '24 to Dec '24 | Analyze the full calendar year that includes the selected point and apply *interquartile range* (IQR) methodology to identify outlying values that occurred during that year.</br></br>The example question that's shown here indicates that you selected a point that represents a period from 2024. Copilot will analyze data across all available dimensions to find outliers that occurred in the selected time series during the calendar year 2024. |
| Deviations from Jan '24 to Dec '24 | Compare the selected time series to a second time series to identify the largest deviations that occurred between them during the selected calendar year. On choosing this question, Copilot asks you to choose a second time series included in the same worksheet. This question is only available if you're working with a worksheet that includes at least two time series.</br></br>Copilot applies *mean average percentage error* (MAPE) methodology to identify the largest deviations occurring between the two selected time series over the selected calendar year. |

## Turn the Analyze demand plans with Copilot feature on or off

The *Analyze demand plans with Copilot* feature is on by default. Follow these steps to turn the feature on or off for your system. A system administrator of the environment must complete this procedure.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/).
1. Use the selector in the upper right of the page to select the environment where you want to turn the feature on or off.
1. Go to **Solutions**.
1. In the *Default Solution* row, select the link in the **Default name** column.
1. In the **Objects** list, select **Settings**.
1. In the *Copilot for demand planning* row, select the link in the **Display name** column.
1. In the **Edit Copilot for demand planning** dialog box, in the **Setting environment value** section, select **Add existing value**.
1. In the dropdown list, select *Yes* to enable the feature for the current environment, or select *No* to disable it.
1. Select **Save**.

### Related information

- [Responsible AI FAQ for Analyze demand plans with Copilot](../faq-demand-planning-copilot.md)
