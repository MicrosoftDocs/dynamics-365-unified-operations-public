---
title: Pin Power BI content
description: Learn about how you can pin full-page Power BI reports to workspaces to give your users an interactive data exploration experience.
author: MilindaV2
ms.author: johnmichalak
ms.date: 01/15/2026
ms.topic: article
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.assetid: a0011a12-a1eb-46bd-8d28-e532fec14e09
---

# Pin Power BI content

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Finance uses Power BI for data exploration. This article explains how you can pin full-page Power BI reports to workspaces to give your users an interactive data exploration experience.

This article assumes that you're familiar with the feature that lets you pin Microsoft Power BI tiles to a workspace. For more information, see [Features and services available through Power BI integration](power-bi-integration.md). If you're a developer who is creating a workspace, to let users pin Power BI tiles to the workspace, embed the Power BI tile control.

## Pin Power BI reports to workspaces

Microsoft Dynamics AX platform update 1 (May 2016) introduced the capability to pin Power BI reports to workspaces. Power BI reports can be added to any workspace that contains a **Links** section. In other words, the reports can be added to most of the out-of-box workspaces that are included in the product. To enable Power BI reports and tiles, you must configure Power BI to work with the application. This one-time operation must be completed by an administrator of the environment. For instructions, see [Configure Power BI integration for workspaces](configure-power-bi-integration.md). After you've configured Power BI to work with the application, open the **Ledger budgets and forecasts** workspace in the client. In the workspace, select the **Options** tab. Notice that this tab contains buttons to open the (Power BI) tile catalog and the (Power BI) report catalog. Select **Open report catalog**. A dialog box that contains a list of reports appears. The list of reports comes from the reports that you have in your Power BI account. If you open PowerBI.com in a browser, you'll see that the same list of reports is used across your Power BI dashboards. Select some reports, as shown in the following illustration, and then select **OK** to continue.

:::image type="content" source="./media/ledger-budgets-workspace-list-of-reports-chosen.jpg" alt-text="Screenshot of Open report catalog dialog box." lightbox="./media/ledger-budgets-workspace-list-of-reports-chosen.jpg":::

Next, scroll to the bottom of the **Links** section in the workspace. A new section for Power BI reports is added to your links.

:::image type="content" source="./media/ledger-budgets-workspace-reports-in-links-section.jpg" alt-text="Screenshot of Power BI Reports section in the Links section." lightbox="./media/ledger-budgets-workspace-reports-in-links-section.jpg":::

## Full-page Power BI reports in the client

You can open and run Power BI reports in the client. The functionality resembles the functionality for running Microsoft SQL Server Reporting Services (SSRS) reports. To run a Power BI report, in the **Links** section, select the link for one of the Power BI reports. For this example, select the **Retail Analysis Sample** link. The Power BI report opens in the client in a full-page view, as shown in the following illustration. This report is interactive. As you select regions of the report, the remaining visuals react to your selection.

:::image type="content" source="./media/retail-analysis-report-full-page-no-filters.jpg" alt-text="Screenshot of Analysis Sample report." lightbox="./media/retail-analysis-report-full-page-no-filters.jpg":::

You can filter the data on the report by using the filter pane. The following illustration shows the report after filters have been applied.

:::image type="content" source="./media/retail-analysis-report-full-page-filtered-view-1.jpg" alt-text="Screenshot of filtered Analysis Sample report." lightbox="./media/retail-analysis-report-full-page-filtered-view-1.jpg":::

You can also open this report on PowerBI.com and make changes. You can then save the modified report as another copy that has a different name, and even pin the new report to the workspace.

## Power BI in user-created workspaces

So far, you learned how to add Power BI tiles and reports to **developer-created** workspaces. Developer-created workspaces are workspaces that Microsoft (that is, they're built into the product), your independent software vendor (ISV) or partner, or in-house developers create. However, in Microsoft Dynamics AX platform update 1 (May 2016), users can create new workspaces by using the personalization capabilities of the client. To create a new workspace, on the home page (or the dashboard), right-click the tile for a workspace, and then select **Add a workspace**. A new workspace is created. New workspaces are named **My Workspace 1**, **My Workspace 2**, and so on. You can change the name later. Select the workspace that you created. You can now add Power BI tiles and reports by using the same options that we discussed earlier. The following illustration shows an example.

:::image type="content" source="./media/my-workspace-with-tiles-and-reports.jpg" alt-text="Screenshot of Power BI report in a user-created workspace." lightbox="./media/my-workspace-with-tiles-and-reports.jpg":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
