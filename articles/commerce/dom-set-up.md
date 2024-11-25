---
title: Set up DOM
description: This article describes how to set up distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.
author: rickwyang
ms.date: 08/23/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2023-11-07
ms.custom: 
  - bap-template
---

# Set up DOM

[!include [banner](includes/banner.md)]

This article describes how to set up distributed order management (DOM) functionality in Microsoft Dynamics 365 Commerce.

> [!IMPORTANT]
> Bing Maps for Enterprise is deprecated and will be retired. Customers with an enterprise license can continue to use Bing Maps for Enterprise until **June 30th, 2028**, and customers on the free and basic license for Bing Maps for Enterprise can continue to use Bing Maps for Enterprise until **June 30th, 2025**. However, if you don't already have a Bing Maps key, you can no longer get one and must build your own customization to bring in longitude and latitude address data for DOM to work. You also need to disable Bing Maps usage for DOM when you configure DOM parameters as described in this article.

## Enable the DOM configuration key

To enable the DOM configuration key, follow these steps.

1. In Commerce headquarters, go to **System administration \> Setup \> License configuration**.
1. On the **Configuration keys** tab, expand the **Commerce** node, and then select the **Distributed Order Management** checkbox.

## Configure DOM parameters

To configure DOM parameters, follow these steps.

1. In headquarters, go to **Retail and Commerce \> Distributed order management \> Setup \> DOM parameters**.
1. On the **General** tab, set the following values:

    - **Enable distributed order management** – Set this option to **Yes**.
    - **Confirm Bing Maps usage for DOM** – Set this option to **Yes**. When this option is enabled, DOM depends on Bing Maps to determine accurate latitude and longitude values based on address, city, and postal code information. When this option is disabled, the latitude and longitude values on the warehouse setting or customer's delivery address are used. The latitude and longitude values are used for distance calculation in the DOM processing.

        > [!NOTE]
        > - You can set this option to **Yes** only if the **Enable Bing Maps** option on the **Bing Maps** tab of the headquarters **Commerce shared parameters** page (**Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**) is also set to **Yes**, and if a valid key is entered in the **Bing Maps key** field.
        > - The [Bing Maps Dev Center](https://www.bingmapsportal.com/) portal allows you to restrict access on your Bing Maps API keys to a set of domains that you specify. With this feature, customers can define a strict set of referrer values or IP address ranges that the key will be validated against. Requests originating from your allow list will process normally, while requests from outside of your list will return an access denied response. Adding domain security to your API key is optional and keys left as-is will continue to function. The allow list for a key is independent from all of your other keys, enabling you to have distinct rules for each of your keys. Distributed Order Management does not support the setting up of domain-referred properties.
    - **Disable road distance calculation** - If this option is **Yes**, aerial distance is calculated for latitude and longitude values of the warehouse and the customer address. Set this option to **No** if you want to use Bing Maps API to calculate road distance, in this case, **Confirm Bing Maps usage for DOM** option is required to be **Yes**.
    - **Do not process accepted store orders during order optimization** - Set this option to **Yes** if you don't want DOM to process sales orders that have been accepted by retail stores.
    - **Update Financial Dimensions on Sales Order Line based on Site** - Set this option to **Yes** if you want to update financial dimensions on sales order lines based on the site.
        > [!NOTE]
        > The financial dimensions might fail to update on sales order lines if the financial dimension link to the site is locked or deactivated. For more information, see [Configure and manage financial dimension links to sites](/dynamicsax-2012/appuser-itpro/configure-and-manage-financial-dimension-links-to-sites).
    - **Fulfillment data retention period (in days)** – Specify how long the fulfillment plans that DOM runs generate are kept in the system. The **DOM fulfillment data deletion job setup** batch deletes any fulfillment plan that is older than the number of days that you specify here.
    - **DOM logs retention period (in days)** - Specify how long the DOM logs that DOM runs generate are kept in the system. The **DOM fulfillment data deletion job setup** batch job deletes any DOM logs that are older than the number of days that you specify here.
    - **Rejection period (in days)** – Specify how much time must pass before a rejected order line can be assigned to the same location.
    - **Thread utilization (percentage)** - When fulfillment plans are generated and **Auto apply result** is enabled in the fulfillment profile, DOM creates fulfillment plan tasks to automatically apply fulfillment plans in parallel. Specify how many thread resources DOM should use to create tasks. A higher number means that more tasks are created. If set to 0, only one fulfillment plan task is created.

1. On the **Solver** tab, set the following values:

    - **Max auto-fulfillment attempts** – Specify how many times the DOM engine attempts to broker an order line to a location. If the DOM engine can't broker an order line to a location in the specified number of attempts, it flags the order line as an exception. It will then skip that line in future runs until the status is manually reset.
    - **Local store region radius** – Enter a value. This field helps determine how locations are grouped and considered equal in terms of distance. For example, if you enter **100**, every store or distribution center within a 100-mile radius of the fulfillment address is considered equal in terms of distance.
    - **Solver type** – Select a value. Two solver types are released with Commerce: **Production Solver** and **Simplified Solver**. For all machines that run DOM (that is, all servers that are part of the DOMBatch group), **Production Solver** must be selected. The Production Solver requires the special license key that, by default, is licensed and deployed in production environments. In newer Tier 2+ environments, the Production Solver is already enabled.

      For nonproduction environments, this license key must be manually deployed. Due to the limitation of nonproduction environments, you must contact Microsoft support to get the latest **DOM license** file. After you obtain the license file, follow these steps:

        1. Start Microsoft Internet Information Services (IIS) Manager, right-click **AOSService website**, and then select **Explore**. A Windows Explorer window is opened at **\<AOS service root\>\\webroot**. Make a note of the \<AOS Service root\> path, because you'll use it in the next step.
        1. Copy the configuration file in the **\<AOS Service root\>\\PackagesLocalDirectory\\DOM\\bin** directory.
        1. In Commerce headquarters, go to the **DOM parameters** page. On the **Solver** tab, for **Solver type**, select **Production solver**, and then confirm that no error messages appear.

        > [!NOTE]
        > - The Simplified Solver is provided so that retailers can try out the DOM feature without having to deploy the special license. Organizations should not use the Simplified Solver in production environments.
        > - The Production Solver improves performance (such as the number of orders and order lines that can be handled in a run) and convergence of results (since a batch of orders might not yield the best result in some scenarios). The **Partial orders** rule requires Production Solver.
1. Go back to **Retail and Commerce \> Distributed order management \> Setup \> DOM parameters**.
1. On the **Number sequences** tab, assign the required number sequences to the various DOM entities.

    > [!NOTE]
    > Before the number sequences can be assigned to the entities, they must be defined on the **Number sequences** page (**Organization administration \> Number sequences \> Number sequences**).
## Configure fulfillment groups

The DOM feature supports the definition of various types of DOM rules, and organizations can configure multiple rules, depending on their business needs. DOM rules can be defined for a group of locations or individual locations, and for a specific product category, product, or variant. To create the grouping of locations that must be used for the DOM rules, follow these steps:

1. In headquarters, go to **Retail and Commerce \> Channel setup \> Fulfillment groups**.
1. Select **New**, and then enter a name and description for the new group.
1. Select **Save**.
1. Select **Add line** to add a single location to the group. Alternatively, select **Add lines** to add multiple locations.

> [!NOTE]
> - In Commerce version 10.0.12 and higher, the **Ability to specify locations as 'Shipping' or 'Pickup' enabled within Fulfillment group** feature must be enabled in the **Feature Management** workspace.
> - This feature adds new configurations on the **Fulfillment group** page so you can specify if the warehouse can be used for shipping or if the warehouse/store combination can be used for shipping, pickup, or both.
> - If you enable the feature, the options available for location selection when you create pickup or shipment orders in POS are updated.
> - Enabling the feature also results in updated pages in POS when the **Ship all** or **Ship selected** operations are selected.

## Configure DOM rules

To configure DOM rules, in headquarters, go to **Retail and Commerce \> Distributed order management \> Setup \> Manage rules**.

The following DOM rules are currently supported.

- Minimum inventory rule.
- Fulfillment location priority rule.
- Partial orders rule.
- Offline fulfillment location rule.
- Maximum rejects rule.
- Maximum distance rule.
- Maximum orders rule.

For more information, see [DOM rules](dom-rules.md).

## Set up and configure DOM fulfillment profiles

Fulfillment profiles are used to group a collection of rules, legal entities, sales order origins, and modes of delivery. Every DOM run is for a specific fulfillment profile. Organizations can define and run rules for a set of legal entities on orders that have specific sales order origins and modes of delivery. If different sets of rules must be run for different sets of sales order origins or modes of delivery, the fulfillment profiles can be defined accordingly.

To set up and configure DOM fulfillment profiles, follow these steps:

1. In headquarters, go to **Retail and Commerce \> Distributed order management \> Setup \> Fulfillment profiles**.
1. Select **New**.
1. Enter values for **Profile** and **Description**.
1. Set the **Auto apply result** option. If you set this option to **Yes**, the results of the DOM run for the profile are automatically applied to the sales order lines. If you set it to **No**, the results can only be viewed in the fulfillment plan, and aren't applied to the sales order lines.
1. If you want the DOM profile to be run for orders that have every sales order origin, including orders where the sales order origin is undefined, set the **Process orders with empty sales origin** option to **Yes**. To run the profile for only a few sales order origins, you can define them on the **Sales origins** page.
1. If you want to change how DOM break sales lines into different batches, set a value for **Maximum number of order lines per optimization**. For more information, see [Partition sales lines](dom-processing.md#partition-sales-lines).

    > [!NOTE]
    > - In Commerce version 10.0.12 and later, the **Ability to assign Fulfillment group to a Fulfillment Profile** feature must be enabled in the **Feature Management** workspace. This feature lets you specify a list of warehouses that DOM should consider when optimization is run with a fulfillment profile. If this list of warehouses isn't specified, DOM will look at all warehouses on legal entities that are defined in the profile.
    > - This feature adds a new configuration on the **Fulfillment profile** page that can be associated to a single fulfillment group.
    > - If you select the fulfillment group, the DOM rules for that fulfillment profile will efficiently run against the "shipping" warehouses included in the fulfillment group.
    > - To effectively use this feature, ensure that there is one fulfillment group that contains all the shipping warehouses, and then associate that fulfillment group to the fulfillment profile.
1. On the **Legal entities** FastTab, select **Add**, and then select a legal entity.
1. On the **Rules** FastTab, select **Add**, and then select the rule to link to the profile.
1. Repeat the previous two steps until all the required rules are associated with the profile.
1. Select **Save**.
1. On the Action Pane, on the **Setup** tab, select **Modes of delivery**.
1. On the **Modes of delivery** page, select **New**.
1. In the **Company** field, select the legal entity. The list of companies is limited to the legal entities that you added earlier.
1. In the **Mode of delivery** field, select the mode of delivery to associate with this profile. A mode of delivery can't be associated with multiple active profiles.
1. Repeat the previous two steps until all the required modes of delivery are associated with the profile.
1. Close the **Modes of delivery** page.
1. On the Action Pane, on the **Setup** tab, select **Sales order origins**.
1. On the **Sales origins** page, select **New**.
1. In the **Company** field, select the legal entity. The list of companies is limited to the legal entities that you added earlier.
1. In the **Sales origin** field, select the sales origin to associate with this profile. A sales origin can't be associated with multiple active profiles.
1. Repeat the previous two steps until all the required sales origins are associated with the profile.
1. Close the **Sales origins** page.
1. Set the **Enable profile** option to **Yes**. If there are any errors in the setup, a warning message appears.

## Additional resources

[DOM overview](dom.md)

[DOM rules](dom-rules.md)

[DOM cost configuration](dom-costs.md)

[DOM processing](dom-processing.md)

[Results of DOM runs](dom-runs-results.md)

[Clean up DOM fulfillment plans and logs](dom-clean-up.md)

[DOM extensibility](dom-extensibility.md)

[DOM limitations](dom-limitations.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
