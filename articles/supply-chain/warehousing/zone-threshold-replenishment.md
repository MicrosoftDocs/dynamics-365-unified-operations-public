---
title: Zone threshold replenishment
description: Zone-based replenishment uses a minimum/maximum (min/max) replenishment strategy, but it evaluates whole warehouse zones instead of just individual locations.required in a picking zone.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 07/01/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSReplenishmentTemplates, WHSLocDirHint, WHSLocDirTable, WHSRequestType
---

# Zone threshold replenishment

[!include [banner](../includes/banner.md)]

Zone-based replenishment uses a minimum/maximum (min/max) [replenishment](replenishment.md) strategy, but it evaluates whole warehouse zones instead of just individual locations. Therefore, warehouse managers can more quickly learn when additional inventory is required in a picking zone.

The setup for this feature resembles the setup for location-based replenishment. However, when you set up a template for min/max replenishment, you can also specify whether the threshold should be evaluated per location or per zone. If you set up evaluation that is based on zones, you must add specific zones to the zone selection query.

Like location-based min/max replenishment, zone-based min/max replenishment is based the setup of a minimum inventory threshold that triggers the creation of replenishment work for selected items. This replenishment work will increase inventory up to the specified maximum threshold for the zone.

> [!NOTE]
> Zone replenishment processes for product variants aren't supported in the current release.


Unlike location-based min/max replenishment, zone-based min/max replenishment doesn't require fixed locations to evaluate whether locations should store a specific item. Therefore, zone-based replenishment lets you use min/max replenishment even if you don't have fixed locations for each item or item variant in the warehouse. When a quantity in the zone falls below the specified minimum threshold, replenishment work is created. Location directives will determine which specific location the inventory should be put into.

## Turn on the Zone threshold replenishment feature

Before you can use the *Zone threshold replenishment* feature, it must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Zone threshold replenishment*

## <a name="setup"></a>Set up zone-based replenishment

To set up zone-based replenishment, you must configure several parts of the system. This section introduces the various settings and provides demo data values that you can enter if you want to work through the scenario at the end of this article.

### Set up directive codes

[Directive codes](control-warehouse-location-directives.md) let you be more specific when you define the location template that is used in a work template. Each code establishes a common value that you can refer to when you configure each type of template.

#### View and edit directive codes

To view or edit your directive codes, go to **Warehouse management \> Setup \> Directive codes**.

#### Prepare demo data directive codes

This example shows how to prepare a directive code. If you're planning to work through the scenario at the end of this article, use the demo data values that are provided here. Otherwise, use your own values.

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management \> Setup \> Directive codes**.
1. On the Action Pane, select **New** to add a row to the grid.
1. In the new row, set the following values:

    - **Directive code:** _Zone replen_
    - **Directive description:** _Zone replenishment_

1. Select **Save** to save the new code.

### Set up replenishment templates

[Min/max replenishment templates](tasks/set-up-min-max-replenishment-process.md) are the primary mechanism for maintaining optimal levels in picking locations. In these templates, you must set up the rules that will be used to replenish inventory in the warehouse. The replenishment that the templates can be used for includes zone-based replenishment.

#### View and edit replenishment templates

A replenishment template is a set of rules that control when and how a location is replenished. You select a template to control when and how replenishment is done. To view or edit your replenishment templates, go to **Warehouse management \> Setup \> Replenishment \> Replenishment templates**.

#### Prepare a demo data replenishment template

This example shows how to prepare a replenishment template. If you're planning to work through the scenario at the end of this article, use the demo data values that are provided here. Otherwise, use your own values.

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management \> Setup \> Replenishment \> Replenishment templates**.
1. Select **Edit** to put the page into edit mode.
1. On the Action Pane, select **New** to add a row to the **Overview** grid.
1. In the new row, set the following values. Accept the default values for all other fields.

    - **Replenish template:** _Zone min/max replen_
    - **Description:** _Zone min/max replenishment_
    - **Replenishment type:** _Minimum or maximum_

1. Select **Save**.
1. While the new row is still selected in the **Overview** grid, select **New** above the **Replenishment Template Details** grid to add a row that is associated with the *Zone Min/Max replen* replenishment template that you just created.
1. In the new row, set the following values:

    - **Sequence number:** Enter _1_.
    - **Description:** Enter _Pick zone replenishment_.
    - **Replenishment unit:** Select _ea_.
    - **Request type:** Leave this field blank.
    - **Directive code:** This field links the replenishment template with a location directive. Select the demo data directive code that you created earlier (_Zone replen_).
    - **Work template:** Leave this field blank.
    - **Minimum quantity:** This field sets the quantity that replenishment will be triggered at. Enter _50_.
    - **Maximum quantity:** This field sets the maximum quantity of an item that can be present in a zone. Generated replenishment work will increase inventory to this quantity. Enter _150_.
    - **Unit:** This field sets the unit for the minimum and maximum values. Select _ea_.
    - **Demand increment:** Select _Round up_.
    - **Replenish empty fixed locations:** Select this check box.
    - **Replenish only fixed locations:** Clear this check box.
    - **Product query mode:** Select _Product query_.
    - **Replenishment threshold scope:** This field defines whether the template should evaluate by zone or by specific location. Select _Zone_.
    - **Warehouse:** Select _61_.

1. Select **Select products** above the **Replenishment Template Details** grid.
1. In the **Product query** dialog box, on the **Range** tab, select **Add** to add a row to the grid.
1. In the new row, set the following values:

    - **Table:** _Items_
    - **Derived table:** _Items_
    - **Field:** _Item number_
    - **Criteria:** _A0001_

1. Select **OK** to save your query and close the dialog box.
1. Select **Select zones to replenish** above the **Replenishment Template Details** grid.
1. In the **Zone query** dialog box, on the **Range** tab, add a row to the grid.
1. In the new row, set the following values:

    - **Table:** _Warehouse zone_
    - **Derived table:** _Warehouse zone_
    - **Field:** _Zone ID_
    - **Criteria:** _FLOOR_

1. Select **OK** to save your query and close the dialog box.

### Set up location directives

Unlike location-based min/max replenishment, zone-based min/max replenishment requires that you set up both pick location directives and put location directives, because the system evaluates the whole zone instead of just the pick location for outbound work.

#### View and edit location directives

To view or edit your location directives, go to **Warehouse management \> Setup \> Location directives**.

For examples that show how to use the settings to create the required pick location directives and put location directives, see the next section.

#### Prepare demo data location directives

To prepare demo data so that it can be used in the scenario at the end of this article, you must create two location directives: one for pick and one for put.

##### Create a replenishment pick directive

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management \> Setup \> Location directives**.
1. In the left pane, set the **Work order type** field to _Replenishment_.
1. On the Action Pane, select **New** to create a new directive.
1. Set the following values:

    - **Sequence number:** Accept the default value.
    - **Name:** Enter _Zone pick_.
    - **Work type:** Select _Pick_.
    - **Site:** Select _6_.
    - **Warehouse:** Select _61_.
    - **Directive code:** Leave this field blank.
    - **Multi SKU:** Set this option to _No_.

1. Select **Save** to create a directive that has the settings that you've configured so far.
1. On the **Lines** FastTab, select **New** to add a line to the grid.
1. On the new line, set the following values:

    - **Sequence number:** Enter _1_.
    - **From quantity:** Enter _0_.
    - **To quantity:** Enter _10000000_.
    - **Unit:** Leave this field blank.
    - **Locate quantity:** Select _None_.
    - **Restrict by unit:** Clear this check box.
    - **Round up to unit:** Clear this check box.
    - **Locate packing quantity:** Clear this check box.
    - **Allow split:** Select this check box.

1. Select **Save** to save the new line.
1. While your new line is still selected in the **Lines** grid, select **New** on the **Location Directive Actions** FastTab to add a row to the grid.
1. In the new row, set the following values:

    - **Sequence number:** Enter _1_.
    - **Name:** Enter _Pick from bulk_.
    - **Fixed location usage:** Select _Fixed and non-fixed locations_.
    - **Allow negative inventory:** Clear this check box.
    - **Batch enabled:** Clear this check box.
    - **Strategy:** Select _None_.

1. Select **Save** to save the new action.
1. While your new action still selected, select **Edit query** above the **Location Directive Actions** grid.
1. A query dialog box appears, where you can select the locations to replenish from. On the **Range** tab, select **Add** to add a row to the grid.
1. In the new row, set the following values:

    - **Table:** _Locations_
    - **Derived table:** _Locations_
    - **Field:** _Zone ID_
    - **Criteria:** _BULK_

1. Select **OK** to save your query and close the dialog box.
1. Select **Save** to save your location directive.

##### Create a replenishment put directive

1. On the **Location directives** page, in the left pane, make sure that the **Work order type** field is still set to _Replenishment_.
1. On the Action Pane, select **New** to create another new directive.
1. Set the following values:

    - **Sequence number:** Accept the default value.
    - **Name:** Enter _Zone put_.
    - **Work order type:** Select _Put_.
    - **Site:** Select _6_.
    - **Warehouse:** Select _61_.
    - **Directive code:** Select _Zone replen_ to link this location directive with the replenishment template that you created earlier by using the code that you created earlier.
    - **Multi SKU:** Set this option to _No_.

1. Select **Save** to create a directive that has the settings that you've configured so far.
1. On the **Lines** FastTab, select **New** to add a line to the grid.
1. On the new line, set the following values:

    - **Sequence number:** Enter _1_.
    - **From quantity:** Enter _0_.
    - **To quantity:** Enter _10000000_.
    - **Unit:** Leave this field blank.
    - **Locate quantity:** Select _None_.
    - **Restrict by unit:** Clear this check box.
    - **Round up to unit:** Clear this check box.
    - **Locate packing quantity:** Clear this check box.
    - **Allow split:** Select this check box.

1. Select **Save** to save the new line.
1. While your new line is still selected in the **Lines** grid, select **New** on the **Location Directive Actions** FastTab to add a row to the grid.
1. In the new row, set the following values:

    - **Sequence number:** Enter _1_.
    - **Name:** Enter _Zone put_.
    - **Fixed location usage:** Select _Fixed and non-fixed locations_.
    - **Allow negative inventory:** Clear this check box.
    - **Batch enabled:** Clear this check box.
    - **Strategy:** Select _Consolidate_.

1. Select **Save** to save the new action.
1. While your new action is still selected, select **Edit query** above the **Location Directive Actions** grid.
1. A query dialog box appears, where you can select the zone to replenish to. This zone should be the same zone that is specified in the replenishment template. On the **Range** tab, select **Add** to add a row to the grid.
1. In the new row, set the following values:

    - **Table:** _Locations_
    - **Derived table:** _Locations_
    - **Field:** _Zone ID_
    - **Criteria:** _FLOOR_

1. Select **OK** to save your query and close the dialog box.
1. Select **Save** to save your location directive.

## Scenario

This section provides a sample scenario that shows how to work with the feature.

### Prepare the sample data that is required for the sample scenario

Before you start to work through the scenario, you must activate sample data and set up the feature as described in this section and in the previous sections of this article.

#### Use the USMF legal entity

To work through the scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

#### Prepare additional sample data

After you've selected the **USMF** legal entity, add the additional sample data that is required, as described in the [Set up zone-based replenishment](#setup) section earlier in this article.

#### Check your on-hand inventory

Follow these steps to make sure that your system includes enough inventory to support the sample scenario.

1. Make sure that there is on-hand inventory for item *A0001* at two different locations in the pick zone (*FLOOR*) that is specified in the replenishment template. However, the total inventory should be less than the required minimum quantity (*50*) that is specified on the replenishment template. In this way, you can simulate how the calculation occurs for the whole zone instead of just for a single location. **Use any of the warehouse processes to adjust inventory as required.**
1. Make sure that there is enough inventory for item *A0001* at a bulk location that is specified in the zone pick location directive where the replenishment work should pick the items from zone ID *BULK*. The total inventory must be more than the required maximum quantity (*150*) that is specified in the replenishment template.
1. Optional but recommended: Follow these steps to create an inventory adjustment journal:

    1. Go to **Inventory management \> Journal entries \> Items \> Inventory adjustment**.
    1. Select **New**.
    1. In the **Create inventory journal** dialog box, in the **Warehouse** field, select *61*.
    1. Select **OK**.
    1. On the **Journal lines** FastTab, use the **New** button to add three lines to the grid, and set the following values. After you've finished setting up each line, select **Save**.

        - **Line 1:**

            - **Item number:** *A0001*
            - **Site:** *6*
            - **Warehouse:** *61*
            - **Location:** *02A01R1S1B*
            - **License plate:** Select an existing license plate in the list, or create a new license plate.
            - **Quantity:** *1000*

        - **Line 2:**

            - **Item number:** *A0001*
            - **Site:** *6*
            - **Warehouse:** *61*
            - **Location:** *07A01R2S1B*
            - **License plate:** Select an existing license plate in the list, or create a new license plate.
            - **Quantity:** *15*

        - **Line 3:**

            - **Item number:** *A0001*
            - **Site:** *6*
            - **Warehouse:** *61*
            - **Location:** *07A01R1S1B*
            - **License plate:** Select an existing license plate in the list, or create a new license plate.
            - **Quantity:** *10*

    1. On the Action Pane, select **Validate**. Address any errors that are found before you move on to the next step.
    1. On the Action Pane, select **Post** to post the inventory to the warehouse.

### Sample scenario: Run zone-based min/max replenishment

After all the prerequisite sample data is in place, you can trigger replenishment by following these steps.

1. Go to **Warehouse management \> Replenishment \> Replenishments**.
1. In the **Replenishment** dialog box, on the **Records to include** FastTab, select **Filter**.
1. In the **Inquiry** dialog box, on the **Range** tab, edit the default table row in the following way:

    - **Table:** Select _Replenishment templates_.
    - **Derived table:** Select _Replenishment templates_.
    - **Field:** Select _Replenishment template_.
    - **Criteria:** Select _Zone min/max replen_. This replenishment template is the replenishment template that you created while you were preparing the demo data for this scenario.

1. Select **OK** to save the query and go back to the **Replenishment** dialog box.
1. Select **OK** to run the replenishment template.

Replenishment work is now created to pick inventory from the *BULK* zone and replenish it to the *FLOOR* zone.

## Notes and tips

Here are a few notes and tips for working with the feature:

- To set up replenishment work that goes to the desired zone, you can link the replenishment template lines and location directives in either of the following ways:

    - Edit the location directive header query, and filter the selected replenishment template lines.
    - Use a directive code on the replenishment template line, and match it to the put location directive.

- If you're using dynamic locations, replenishment work will be created either for the first available location or for a location that already contains inventory, if the location directive action is set up to use the **Consolidate** strategy.
- If you're using fixed locations instead of zones, you should use [standard min/max replenishment](tasks/set-up-min-max-replenishment-process.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]