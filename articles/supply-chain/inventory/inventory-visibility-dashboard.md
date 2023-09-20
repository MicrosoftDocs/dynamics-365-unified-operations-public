---
title: Inventory Visibility Power BI dashboard
description: This topic describes how to download a sample Power BI dashboard file and connect to your Inventory Visibility instance and other data sources to visualize your inventory levels across regions, entities, and channels.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inventory Visibility Power BI dashboard

[!include [banner](../includes/banner.md)]

Microsoft provides a sample Microsoft Power BI dashboard file that you can download and connect to your Inventory Visibility instance and other data sources to visualize your inventory levels across regions, entities, and channels. Use it to track inventory movement, compare supply and demand portions, view most and least popular products, and drive inventory risk mitigation decisions.

The dashboard enables you to do the following:

- Filter on inventory dimensions to focus on the regions and products you care about most.
- Identify out-of-stock, understocked, and overstocked products for timely inventory replenishment or reduction.
- View inventory key performance indicators (KPIs) (such as on-hand quantity, supply, and demand) to quickly monitor your inventory status.
- Tailor the sample dashboard to accommodate your organization's business needs.

## License requirements

Because the dashboard is a standard Power BI file (.pbix), you must have a Power BI license to use it. For details, see [Power Bi licensing guide](https://powerbi.microsoft.com/pricing/).

## Download the dashboard and connect it to Inventory Visibility

1. Download the Inventory Visibility dashboard file from the Inventory Visibility Teams channel or [Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=46697168896). To access the file, you must be a member of the Inventory Visibility Teams channel or Yammer group. If you need help with accessing the file, contact the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com).
1. Configure *preloaded on-hand queries* in Inventory Visibility for all of the data that you plan to view using the Power BI dashboard. For instructions about how to set these up, see [Turn on and configure preloaded on-hand queries](inventory-visibility-configuration.md#query-preload-configuration).
1. Connect the power BI report to your Dataverse environment by following these steps:
    1. Open the downloaded report in [Power BI desktop](https://powerbi.microsoft.com/downloads).
    1. Expand the **Data** pane. Right-click the **Query Preload Results** table and select **Edit query** to open the Power Query editor.
    1. Replace value for the `EnvironmentURL` parameter with the base URL of your Dataverse environment (for example,  `example.crm.dynamics.com`).
    1. Refresh the query to update the results.
1. To load data from your entities, create a new data source and name it `pbi` to indicate that it's your Power BI data source (see also [Configure Inventory Visibility](inventory-visibility-configuration.md)). To reduce the size of the response body, information from this data source isn't included in results.

## Default KPIs

If you'd like to use the visuals and KPIs provided in the example dashboard, you must define the following calculated measures in `pbi` data source, and add the relevant physical measures from your data sources to the calculated measures.

- `Totalonhand` – Total physical inventory stock you have in your warehouses.
- `Totalavailablephysical` – Total available physical inventory quantities.
- `Totalavailable` – Total quantities that are available (including both available physical and available ordered inventory, minus the on-order quantity that hasn't been promised).
- `Totalordered` – Total quantity that has been purchased, produced, or otherwise inbound.
- `totalonorder` – Total quantities that are on order.
- `Hardreserved` Total hard-reserved quantities (including reserve physical and reserve ordered quantities).
- `Returned` – Total returned quantities. Make sure that one of your data sources includes a physical measure for returns and that this physical measure is added to the returned calculated measure.
- `Totalsold` – Total quantities sold.
- `Othersupply` – Supply quantities from other user-specified sources that aren't included in the measures already mentioned.
- `Otherdemand` – Demand quantities from other user-specified sources that aren't included in the measures already mentioned.
- `Totalsoftreserved` – Total soft reserved quantities.
- `Received` – Total inventory quantity received into your warehouses.

These sample calculated measures are included in the following formulas in the Power BI report:

- On the **Supply by Product** dashboard: Total supply = `Totalonhand` &plus; `Totalordered` &plus; `Othersupply`
- On the **Demand by Product** dashboard: Total demand = `Totalonorder` &plus; `Totalsoftreserved` &plus; `Totalreserved` &plus; `Otherdemand`

## Customize the dashboard

You can customize the sample dashboard by editing the visuals directly. You can also edit the query to display different measures from different data sources.

To add a new data source, follow these steps:

1. With the dashboard open in Power BI desktop, expand the **Data** pane. Right-click on the **Query Preload Results** table and select **Edit query** to open the Power Query editor.
1. On the ribbon of the Power Query editor, open the **Home** tab and then select **Refresh Preview**.
1. On **Query Settings** pane, go to the **Applied Steps** section. Right-click the **Expanded is_quantities** step and select **Edit settings**.
1. Search for or select the new data source that you want to add to the report.

To add, modify or delete a column for an existing data source, follow these steps:

1. With the dashboard open in Power BI desktop, expand the **Data** pane. Right-click on the **Query Preload Results** table and select **Edit query** to open the Power Query editor.
1. On the ribbon of the Power Query editor, open the **Home** tab and then select **Refresh Preview**.
1. In **Query Settings** pane, go to the **Applied Steps** section. Find the **Expanded is_quantities.\<data-source\>** step, where **\<data-source\>** is the data source that the new column belongs to.
1. Right-click on the step you found and select **Edit settings**.  Search for or select the new column name that you want to add to the report.

You can also define new columns based on the retrieved entity. In the example report, total supply and total demand are calculated columns defined inside Power BI.

If you're familiar with [Power Query](https://powerquery.microsoft.com), then you can edit the query directly using the Power Query language.  To do so, open the **Home** tab on the ribbon of the Power Query editor and then select **Advanced Editor** to open the advanced editor.
