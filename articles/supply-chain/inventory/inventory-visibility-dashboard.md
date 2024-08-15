---
title: Inventory Visibility Power BI dashboard
description: Learn how to download a sample Microsoft Power BI dashboard file and connect to your Inventory Visibility instance and other data sources.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 07/31/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Inventory Visibility Power BI dashboard

[!include [banner](../includes/banner.md)]

Microsoft provides a sample Microsoft Power BI dashboard file that you can download and connect to your Inventory Visibility instance and other data sources. In this way, you can visualize your inventory levels across regions, entities, and channels. Use the dashboard to track inventory movement, compare supply and demand portions, view the most popular and least popular products, and drive decisions about inventory risk mitigation.

The dashboard lets you perform the following tasks:

- Filter on inventory dimensions, so that you can focus on the regions and products that you most care about.
- Identify out-of-stock, understocked, and overstocked products for timely inventory replenishment or reduction.
- View inventory key performance indicators (KPIs), such as on-hand quantity, supply, and demand, to quickly monitor your inventory status.
- Tailor the sample dashboard to your organization's business needs.

## License requirements

Because the dashboard is a standard Power BI file (.pbix file), you must have a Power BI license to use it. Learn more in [Power Bi licensing guide](https://powerbi.microsoft.com/pricing/).

## Download the dashboard and connect it to Inventory Visibility

1. Download the Inventory Visibility dashboard file from [Inventory Visibility samples folder on GitHub](https://github.com/microsoft/Inventory-Visibility-Add-in-Examples/tree/main/powerbi).
1. For all the data that you plan to view by using the Power BI dashboard, configure *preloaded on-hand queries* in Inventory Visibility. For instructions, see [Preload a streamlined on-hand query](inventory-visibility-preload-on-hand.md).
1. Connect the power BI report to your Dataverse environment by following these steps:

    1. Open the downloaded report in [Power BI desktop](https://powerbi.microsoft.com/downloads).
    1. Expand the **Data** pane. Select and hold (or right-click) the **Query Preload Results** table, and then select **Edit query** to open the Power Query editor.
    1. Replace the value of the `EnvironmentURL` parameter with the base URL of your Dataverse environment (for example, `example.crm.dynamics.com`).
    1. Refresh the query to update the results.

1. To load data from your entities, create a new data source, and name it *pbi* to indicate that it's your Power BI data source. (Learn more in [Configure Inventory Visibility](inventory-visibility-configuration.md).) To reduce the size of the response body, information from this data source is excluded from results.

## Default KPIs

To use the visuals and KPIs that are provided in the sample dashboard, you must define the following calculated measures in the `pbi` data source. Add the relevant physical measures from your data sources to these calculated measures.

- `Totalonhand` – The total physical inventory stock that you have in your warehouses.
- `Totalavailablephysical` – The total available physical inventory quantities.
- `Totalavailable` – The total quantities that are available. This total includes both available physical inventory and available ordered inventory, minus the on-order quantity that hasn't been promised.
- `Totalordered` – The total quantity that has been purchased or produced, or that's otherwise inbound.
- `totalonorder` – The total quantities that are on order.
- `Hardreserved` The total hard-reserved quantities. This total includes both reserve physical quantities and reserve ordered quantities.
- `Returned` – The total returned quantities. Make sure that one of your data sources includes a physical measure for returns, and that this physical measure is added to the `Returned` calculated measure.
- `Totalsold` – The total quantities that have been sold.
- `Othersupply` – Supply quantities from other user-specified sources that aren't included in the previously mentioned measures.
- `Otherdemand` – Demand quantities from other user-specified sources that aren't included in the previously mentioned measures.
- `Totalsoftreserved` – The total soft-reserved quantities.
- `Received` – The total inventory quantity that has been received into your warehouses.

These sample calculated measures are included in the following formulas on the Power BI report:

- On the **Supply by Product** dashboard: *Total supply* = `Totalonhand` &plus; `Totalordered` &plus; `Othersupply`
- On the **Demand by Product** dashboard: *Total demand* = `Totalonorder` &plus; `Totalsoftreserved` &plus; `Totalreserved` &plus; `Otherdemand`

## Customize the dashboard

You can customize the sample dashboard by directly editing the visuals. You can also edit the query to show different measures from different data sources.

To add a new data source, follow these steps.

1. Open the dashboard in Power BI desktop, and expand the **Data** pane. Select and hold (or right-click) the **Query Preload Results** table, and then select **Edit query** to open the Power Query editor.
1. On the ribbon of the Power Query editor, on the **Home** tab, select **Refresh Preview**.
1. In the **Query Settings** pane, in the **Applied Steps** section, select and hold (or right-click) the **Expanded is\_quantities** step, and then select **Edit settings**.
1. Search for or select the data source that you want to add to the report.

To add, modify, or delete a column for an existing data source, follow these steps.

1. Open the dashboard in Power BI desktop, and expand the **Data** pane. Select and hold (or right-click) the **Query Preload Results** table. and then select **Edit query** to open the Power Query editor.
1. On the ribbon of the Power Query editor, on the **Home** tab, select **Refresh Preview**.
1. In the **Query Settings** pane, in the **Applied Steps** section, find the **Expanded is\_quantities.\<data-source\>** step, where **\<data-source\>** is the data source that the new column belongs to.
1. Select and hold (or right-click) the step, and then select **Edit settings**.
1. Search for or select the name of the column that you want to add to the report.

You can also define new columns, based on the retrieved entity. In the sample report, the columns for total supply and total demand are calculated columns that are defined in Power BI.

If you're familiar with [Power Query](https://powerquery.microsoft.com), you can directly edit the query by using the Power Query language. On the ribbon of the Power Query editor, on the **Home** tab, select **Advanced Editor** to open the advanced editor.
