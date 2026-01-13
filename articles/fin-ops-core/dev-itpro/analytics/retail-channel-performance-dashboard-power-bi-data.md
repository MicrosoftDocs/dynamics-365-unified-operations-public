---
title: Retail channel performance PowerBI.com solution
description: Learn about the Retail channel performance PowerBI.com solution for Dynamics AX 7.0 releases, including information on how to connect and modify reports.
author: ashishmsft
ms.author: asharchw
ms.topic: how-to
ms.date: 01/12/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: cb5aff3b-5b29-44f7-9c6f-6b055c043996
---

# Retail channel performance PowerBI.com solution

[!include [banner](../includes/banner.md)]

> [!NOTE]
> Microsoft deprecated this PowerBI.com solution. For more information, see [Power BI content packs available on Marketplace](../migration-upgrade/deprecated-features.md#power-bi-content-packs-available-on-marketplace).

This article provides information about the Retail channel performance PowerBI.com solution for Dynamics AX. By using this PowerBI.com solution, channel managers can quickly build channel performance analytics to predict trends and uncover insights, based on sales performance.

The Retail channel performance PowerBI.com solution helps you quickly build your channel performance analytics. The PowerBI.com solution is designed specifically for channel managers who focus on sales performance to predict trends and uncover insights. Its components draw directly from Retail and commerce data in the Dynamics AX database, and provide drill-down reports about organization-wide sales performance across global geography by employee, category, product, terminal, channel, and more. Power BI automatically creates reports and dashboards that give you a great starting point for exploring and analyzing your Retail and commerce data. This article includes the following information:

- Learn how to connect the Retail channel performance PowerBI.com solution to a Dynamics AX data source.
- View a list of reports that provide insights into retail channel performance.
- Learn how to modify an existing report in the PowerBI.com solution to make it self-authored.
- Get a glimpse of an actual data model that enables the whole experience in Power BI.

## Connect the Retail channel performance PowerBI.com solution to a Dynamics AX data source

1. Go to [https://www.powerbi.com](https://www.powerbi.com), and select **Sign in**. If you don't have an account, you can register to try the new Power BI Preview for free.
1. Enter a Microsoft 365 account that has a Power BI account to sign in.
1. If your workspace appears, select **Get Data** at the bottom of the left navigation pane.
1. In the **Services** section, select **Get**.
1. Scroll or search to find **Microsoft Dynamics AX Retail channel performance**, and then select **Get it now**.
1. Enter your Dynamics AX URL in the following format: `https://<tenant>.cloudax.dynamics.com` (for example, `https://YourAOSTenant.cloudax.dynamics.com`). Then select **Next** to pull data from Dynamics AX data storage into this Power BI dashboard.
1. Select **oAuth2** as the authentication method, and then select **Sign in**.
1. Enter a Microsoft 365 account that has permission to access your Dynamics AX environment.
1. After data is successfully pulled from Dynamics AX into Power BI, you can view your personal **Retail channel performance** dashboard in Power BI by selecting **Retail channel performance dashboard** in the left navigation pane.

    :::image type="content" source="./media/rcmpbidashboard.png" alt-text="Screenshot of Retail channel performance dashboard." lightbox="./media/rcmpbidashboard.png":::

1. You can then take advantage of the Q&A feature in Power BI to query your Dynamics AX sales data by using natural language.

    :::image type="content" source="./media/qnapbiretailchannelperformance.png" alt-text="Screenshot of Q&A feature in Power BI.":::

## View a list of reports

By clicking any of the pinned tiles on the dashboard, you can access the following list of reports that provide insights into retail channel performance:

- Geographical sales distribution
- Category sales performance
- Sales summary by Tender type or payment method
- Employee monthly performance
- Store monthly performance
- Product sales performance for the given category in the given store

For example, you might want to do a deeper analysis of geographical sales distribution.

:::image type="content" source="./media/slicendicegeographicalsalesdata.png" alt-text="Screenshot of Geographical sales distribution report." lightbox="./media/slicendicegeographicalsalesdata.png":::

## Modify an existing report in the PowerBI.com solution to make it self-authored

The following example shows how to modify an existing report in the PowerBI.com solution to make it self-authored. In this example, you modify an existing report named **Category & product performance** by adding **Category level 1** to the **Total amount by Month/Year** chart on that report.

1. Select the **CategoryProductPerformance** tab at the bottom of the window to open the **Category & product performance** report. Then, select **Edit report**.

    :::image type="content" source="./media/editreport.png" alt-text="Screenshot of Edit report." lightbox="./media/editreport.png":::

1. Select the chart named **Total amount by Month/Year**. Then, on the right side of the window, in the **Fields** pane, expand the **Default Retail Product Category Hierarchy** node.

    :::image type="content" source="./media/editreportstep2.png" alt-text="Screenshot of Default Retail Product Category Hierarchy node for the Total amount by Month/Year chart." lightbox="./media/editreportstep2.png":::

1. In the list of category levels for this hierarchy, select **Category Level 1**. The name of the chart changes to **Total amount by Month/Year and Category level 1**. The chart now shows the share of sales in each category for each month.

    :::image type="content" source="./media/editreportstep3.png" alt-text="Screenshot of Total amount by Month/Year and Category level 1 chart." lightbox="./media/editreportstep3.png":::

1. Finally, try to change the visualization itself. Select the **Total amount by Month/Year and Category level 1** chart. Then, in the **Visualizations** pane, select **Area chart** or **Stacked area chart**, and see the effect.

    :::image type="content" source="./media/editreportstep4.png" alt-text="Screenshot of changing the visualization of the Total amount by Month/Year and Category level 1 chart." lightbox="./media/editreportstep4.png":::

## Get a glimpse of the actual data model

The data model that the PowerBI.com solution includes for the Dynamics AX data entities and aggregated data entities lets you slice and dice across various measures by using different dimensions.

:::image type="content" source="./media/datamodeltomakeslicingndicingpossibleinrcm.png" alt-text="Screenshot of Data model." lightbox="./media/datamodeltomakeslicingndicingpossibleinrcm.png":::

## Additional resources

[Features and services available through Power BI integration](power-bi-integration.md)

[Configure Power BI integration for workspaces](configure-power-bi-integration.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
