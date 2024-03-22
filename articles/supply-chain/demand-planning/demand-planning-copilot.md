---
title: Analyze demand plans with Copilot (preview) 
description: The Demand planning app for Dynamics 365 Supply Chain Management can analyze your demand plans with Copilot. It lets you choose from a set of pre-defined questions and provides answers in real time using natural language.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 04/01/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
ms.collection:
  - bap-ai-copilot
---

# Analyze demand plans with Copilot (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]
<!--KFM: Preview until further notice -->

The Demand planning app for Dynamics 365 Supply Chain Management can analyze your demand plans with Copilot. It lets you choose from a set of pre-defined questions and provides answers in real time using natural language.

Using Copilot, you can quickly gain valuable insights across multiple dimensions. Using these insights, you can improve operational efficiency, increase profitability, and improve customer satisfaction.

For example, a demand planner might be interested in tracking down the most significant factors that contributed to a notable shift between two consecutive periods. The planner opens the relevant worksheet, chooses a point of interest on the graph, and then selects a predefined question to ask Copilot. Copilot's response could resemble the following answer:

> The top 10 most significant changes contributing to the change in demand are:<br><br>1. Car Audio Unit-500 in Distribution center increased by 31% or 208 units.<br>2. Car Audio Unit-65-Black in Distribution center increased by 31% or 173 units.<br>3. Car Audio Unit-65-Silver in Store 2 increased by 29% or 574 units.<br>4. Mid-Range Speaker in Store 1 increased by 29% or 509 units.<br>5. High End Speaker in Store 4 increased by 28% or 298 units.<br>6. High End Speaker in Store 1 increased by 28% or 351 units.<br>7. Car Audio Unit-65-Silver in Store 1 increased by 28% or 405 units.<br>8. High End Cabinet-Oak in Distribution center increased by 28% or 190 units.<br>9. Car Audio Unit-500 in Store 4 increased by 28% or 123 units.<br>10. Car Audio Unit-200 in Store 1 increased by 27% or 240 units.<br><br>AI-generated content may be incorrect.

[!INCLUDE [preview-note](includes/preview-note.md)]

## Prerequisites

To analyze demand plans with Copilot, you must be running the general availability (GA) version of Demand planning app for Dynamics 365 Supply Chain Management.

## Country/region availability and language support

The *Analyze demand plans with Copilot* feature is available in all regions.

The *Analyze demand plans with Copilot* feature is only available in English.

## Ask Copilot to analyze your data

To ask Copilot to analyze your data, follow these steps.

1. On the navigation pane, select **Worksheets**.
1. Open the worksheet you want to analyze.
1. In the **Timeline** section, select the point on the graph that represents the period you want to analyze.
1. The **Copilot** menu opens, displaying one or more questions that you can ask about your selected point. Select the question you want to ask. (See the next section for more information about the types of questions that can be shown.)
1. Copilot analyzes the data and provides its answer.

## Chat with Copilot

The following table provides a quick reference to predefined questions that you can choose from the **Copilot** menu.

| **Example question** | **Description** |
|--|--|
| Largest shifts from Apr 24 to May 24 | Compares two consecutive periods in the same year. The length of the period (day, week, or month) is based on how the times series in your worksheet are set up.</br></br>The specific example question shown here indicates that you selected a point that represents the one-month period of May 2024 and Copilot will compare that to the previous month (April 2024). |
| Largest shifts from May 23 to May 24 | Compare a selected period to the same period one year earlier. The length of the period (day, week, or month) is based on how the times series in your worksheet are set up.</br></br>The specific example question shown here indicates that you selected a point that represents the one-month period of May 2024 and Copilot will compare that to the one-month period of May 2023. |

## Turn the Analyze demand plans with Copilot feature on or off

The *Analyze demand plans with Copilot* feature is on by default. Follow these steps to turn the feature on or off for your system. These steps must be followed by a system administrator of the environment.

1. Sign in to [Power Apps Maker portal](https://make.powerapps.com/).
1. From the selector on the top right of the page, select the environment where you want to turn the Copilot feature on or off.
1. Go to **Solutions**.
1. Select the link in the **Default name** column for the *Default Solution* row.
1. From the **Objects** list, select **Settings**.
1. Select the link in the **Display name** column for the *Copilot for demand planning* row.
1. The **Edit Copilot for demand planning** dialog opens.
1. In teh **Setting environment value section**, select **Add existing value**.
1. A drop-down list opens. Select *Yes* to enable the feature for the current environment or *No* to disable it.
1. Select **Save**.

### See also

- [Responsible AI FAQ for Analyze demand plans with Copilot (preview)](../faq-demand-planning-copilot.md)
