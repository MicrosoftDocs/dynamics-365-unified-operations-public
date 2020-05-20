# Zone threshold replenishment

Zone based replenishment uses a min/max [replenishment](replenishment.md) strategy, but evaluates entire warehouse zones instead of just individual locations. This helps make it faster for warehouse managers to find out when additional inventory is needed within a picking zone.

The set up for this feature is similar to the setup for location-based replenishment, except that when you are setting up a template for min/max replenishment, you can now also make a setting that specifies whether the threshold should be evaluated per location or per zone. When setting up an evaluation based on zone, you must add specific zones to the zone selection query.

As with location-based min/max replenishment, zone-based min/max replenishment is based on setting up a minimum threshold of inventory that triggers the creation of replenishment work for selected items and item variants. This replenishment work will increase inventory up to the configured maximum threshold for the zone.

Unlike location-based min/max replenishment, zone replenishment does not require fixed locations to evaluate whether locations should store a certain item or not. Zone-based replenishment therefore allows you to use min/max replenishment without fixed locations for each item or item variant within the warehouse. When a quantity in the zone falls below the specified minimum, replenishment will be created, and location directives will determine which specific location to put the inventory into.

## Enable the Zone threshold replenishment feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) page to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Zone threshold replenishment*

<a name="setup"></a>

## Set up zone-based replenishment

To set up zone-based replenishment, you must configure several parts of the system. This section introduces those various settings and provides demo-data values that you can enter if you would like to work through the demo-data example given at the end of this topic.

### Set up your directive codes

[Directive codes](control-warehouse-location-directives.md) enable you to be more specific when defining which location template to use in a work template. Each code establishes a common value that you can refer to when configuring each type of template.

#### View and edit directive codes

To view or edit your directive codes, go to **Warehouse management > Setup > Directive codes**.

#### Prepare sample-data directive codes

Here is an example for how to prepare a directive code. If you're planning to work through the example at the end of this topic, then use the sample-data values provided here. Otherwise, use your own values.

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management > Setup > Directive codes**.
1. Select **New** on the Action Pane to add a new row to the table and enter the following values for it:
    - **Directive code** – _Zone replen_
    - **Directive description** – _Zone replenishment_
1. Select **Save** to save the new code.

### Set up your replenishment templates

[Min/Max replenishment templates](tasks/set-up-min-max-replenishment-process.md) are the primary mechanism for maintaining optimal levels in picking locations. This is where you must set up the rules by which you will replenish inventory in the warehouse, including for zone-based replenishment.

#### View and edit replenishment templates

Replenishment template is a set of rules that control when and how to replenish a location. Select the template to use for controlling when and how to replenish.

#### Prepare a sample-data replenishment template

Here is an example for how to prepare a replenishment template. If you're planning to work through the example at the end of this topic, then use the sample-data values provided here. Otherwise, use your own values.

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management > Setup > Replenishment > Replenishment templates**.
1. Select **Edit** to put the page in edit mode.
1. Select **New** on the Action Pane to add a new row to the **Overview** table and enter the following values for it:
    - **Replenish template** – _Zone min/max replen_
    - **Description** – _Zone min/max replenishment_
    - **Replenishment type** – _Minimum or maximum_
    - Accept remaining defaults
    - Select **Save**
1. With the new row still selected in the **Overview** table, select **New** in the **Replenishment Template details** action pane to add a new row to *Replenishment Template Details* associated with the replenishment template **Zone Min/Max replen** just created. Make the following settings for the new row:
    - **Sequence number** - Enter _1_.
    - **Description** – Enter _Pick zone replenishment_
    - **Replenishment unit** – Select _ea_.
    - **Request type** - Leave empty
    - **Directive code** – This will link this replenishment template with a location directive. Select the sample-data directive code that you just created: _Zone replen_.
    - **Work template** - Leave empty
    - **Minimum quantity** – This sets the quantity at which replenishment will be triggered. Enter _50_.
    - **Maximum quantity** – This sets the maximum quantity of an item that can be present in a zone. Generated replenishment work will increase inventory to this quantity. Enter _150_.
    - **Unit** – Sets the unit for the min and max values. Select _ea_.
    - **Demand increment** – Select _Round up_.
    - **Replenish empty fixed locations** – Select this check box.
    - **Replenish only fixed locations** –  Deselect this check box.
    - **Product query mode** – Select _Product query_.
    - **Replenishment threshold scope** – Sets whether the template should evaluate by zone or by specific location. Select _Zone_.
    - **Warehouse** - Select _61_.
1. In the **Replenishment Template Details** action pane, select the menu option **Select products**. This opens the **Product query** flyout. Select **Add** in the **Range** tab to add a row with the following values:
    - **Table** - _Items_
    - **Derived table** - _Items_
    - **Field** - _Item number_
    - **Criteria** - _A0001_
1. Select **OK** to save your query and close the pane.
1. Select **Select zones to replenish** from the **Replenishment template details** action pane to open the **Zone query** flyout. Add a row with the following values to the **Range** table:
    - **Table** - _Warehouse zone_
    - **Derived table** - _Warehouse zone_
    - **Field** - _Zone ID_
    - **Criteria** - _FLOOR_
1. Select **OK** to save your query and close the pane.

### Set up your location directives

Unlike location-based min/max replenishment, zone-based replenishment requires you to set up both pick-location and put-location directives because the system evaluates the whole zone instead of just the outbound work pick location.

#### View and edit location directives

See the next section of examples of how to use the settings here to create the required pick-location and put-location directives.

#### Prepare sample-data location directives

To prepare demo data for use with the scenario given at the end of this topic, you need two location directives, one for pick and one for put.

##### Create a replenishment pick directive

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management > Setup > Location directives**.
1. In the left pane, set **Work order type** to _Replenishment_.
1. Select **New** on the Action Pane to create a new directive and make the following settings:
    - **Sequence number** - Accept default
    - **Name** – Enter _Zone pick_
    - **Work type** – Select _Pick_
    - **Site** - Select _6_
    - **Warehouse** - Select _61_
    - **Directive code** – leave empty
    - **Multi SKU** – Set to _No_
1. Select **Save** to create a directive with your settings so far.
1. In the **Lines** FastTab, select **New** to add a new line to the table and then make the following settings for it:
    - **Sequence number** – Enter _1_
    - **From quantity** – Enter _0_
    - **To quantity** – Enter _10000000_
    - **Unit** - Leave blank
    - **Locate quantity** – Select _None_
    - **Restrict by unit** - Unselect this check box (no)
    - **Round up to unit** - Unselect this check box (no)
    - **Locate packing quantity** - Unselect this check box (no)
    - **Allow split** – Select this check box (yes)
1. Select **Save** to save the new line.
1. With your new line still selected in the **Lines** table, select **New** on the **Location directive actions** FastTab to add a new action to the table and then make the following settings for it:
    - **Sequence number** – Enter _1_
    - **Name** – Enter _Pick from bulk_
    - **Fixed location usage** – Select _Fixed and non-fixed locations_
    - **Allow negative inventory** -  Unselect this check box (no)
    - **Batch enabled** - Unselect this check box (no)
    - **Strategy** – Select _None_
1. Select **Save** to save the new action.
1. With your action still selected in the **Location directive actions** table, select **Edit query** on the **Location Directive Actions** action pane.
1. A query flyout opens, which lets you select the locations you want to replenish from. Select **Add** on the **Range** tab to add a new row to the table here and then make the following settings for the new row:
    - **Table** - _Locations_
    - **Derived table** - _Locations_
    - **Field** - _Zone ID_
    - **Criteria** - _BULK_
1. Select **OK** to save your query and close the pane.
1. Select **Save** to save your location directive.

##### Create a replenishment put directive

1. Continue working on the **Location directives** page and in the left pane, make sure **Work order type** is still to _Replenishment_.
1. Select **New** on the Action Pane to create another new directive and make the following settings:
    - **Sequence number** - Accept default
    - **Name** – Enter _Zone put_
    - **Work order type** – Select _Put_
    - **Site** - Select _6_
    - **Warehouse** - Select _61_
    - **Directive code** – Select _Zone replen_. This will link this location directive with the replenishment template we created earlier using the code we also created earlier.
    - **Multi SKU** – Set to _No_
1. Select **Save** to create a directive with your settings so far.
1. In the **Lines** FastTab, select **New** to add a new line to the table and then make the following settings for it:
    - **Sequence number** – Enter _1_
    - **From quantity** – Enter _0_
    - **To quantity** – Enter _10000000_
    - **Unit** - Leave blank
    - **Locate quantity** – Select _None_
    - **Restrict by unit** - Unselect this check box (no)
    - **Round up to unit** - Unselect this check box (no)
    - **Locate packing quantity** - Unselect this check box (no)
    - **Allow split** – Select this check box (yes)
1. Select **Save** to save the new line.
1. With your new line still selected in the **Lines** table, select **New** on the **Location Directive Actions** FastTab to add a new action to the table and then make the following settings for it:
    - **Sequence number** – Enter _1_
    - **Name** – Enter _Zone put_
    - **Fixed location usage** – Select _Fixed and non-fixed locations_
    - **Allow negative inventory** -  Unselect this check box (no)
    - **Batch enabled** - Unselect this check box (no)
    - **Strategy** – Select _Consolidate_
1. Select **Save** to save the new action.
1. With your action still selected in the **Location Directive Actions** table, select **Edit query** on the **Location Directive Actions** action pane.
1. A query flyout opens, which lets you select the zone you want to replenish to. This should be the same as Zone specified on the Replenishment template. Select **Add** on the **Range** tab to add a new row to the table here and then make the following settings for the new row:
    - **Table** - _Locations_
    - **Derived table** - _Locations_
    - **Field** - _Zone ID_
    - **Criteria** - _FLOOR_
1. Select **OK** to save your query and close the pane.
1. Select **Save** to save your location directive.

## Scenario

This section provides a sample scenario that illustrates how to work with this feature.

### Prepare the sample data required for this sample scenario

Before you start working through the scenario, you must activate sample data and set up the feature as described in this section and in the previous sections of this topic.

#### Use the USMF legal entity

To work through this sample scenario using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

#### Prepare additional sample data

After you have selected the **USMF** legal entity, add the additional required sample data as described in [Set up zone-based replenishment](#setup).

#### Check your on-hand inventory

Do the following to make sure your system includes enough inventory to support the sample scenario:

1. Ensure there is on-hand inventory for item A0001 at two different locations within the ***pick zone*** specified on the replenishment template (**FLOOR**), but still less total inventory than required by the **Minimum quantity** (**50**) specified on the replenishment template. This is to simulate how the calculation occurs for the whole zone, instead of only for a single location. ***Use any of the warehouse processes to adjust inventory if needed.***
1. Ensure there is enough inventory for item A0001 at a ***bulk location*** specified on the zone pick location directive where the replenishment work should pick the items from ***Zone ID*** (**BULK**) . The total inventory must be greater than the quantity required by the **Maximum quantity** (**150**) specified on the replenishment template.
1. Suggested action: Create an Inventory adjustment journal
1. Go to **Inventory management > Journal entries > Items > Inventory adjustment**

    - Select **New**
    - On **Create inventory journal** flyout select **Warehouse** -*61*
    - Select **OK**
    - On the **Journal lines** fast tab, select **New** in the action pane
    - Enter the following data (you will create 3 lines)
    - ***Line 1***
        - **Item number** - *A0001*
        - **Site** - *6*
        - **Warehouse** - *61*
        - **Location** - *02A01R1S1B*
        - **License plate** - *Select existing license plate from list or create a new one*
        - **Quantity** - *1000*
        - Select **Save**
    - ***Line 2***
        - **Item number** - *A0001*
        - **Site** - *6*
        - **Warehouse** - *61*
        - **Location** - *07A01R2S1B*
        - **License plate** - *Select existing license plate from list or create a new one*
        - **Quantity** - *15*
        - Select **Save**
    - ***Line 3***
        - **Item number** - *A0001*
        - **Site** - *6*
        - **Warehouse** - *61*
        - **Location** - *07A01R1S1B*
        - **License plate** - *Select existing license plate from list or create a new one*
        - **Quantity** - *10*
        - Select **Save**
    - In the **Inventory adjustment** action pane, select **Validate**, address any errors before posting
    - In the **Inventory adjustment** action pane, select **Post** to post the inventory to the warehouse

### Sample scenario: Run zone min/max replenishment

Once you have all the prerequisite sample data in place, you can trigger a replenishment by doing the following:

1. Go to **Warehouse management > Replenishment > Replenishments**.
1. The **Replenishment** pane opens. In the **Records to include** FastTab, select **Filter**.
1. The **Inquiry** pane opens. On the **Range** tab, edit the default table row provided as follows:
    - **Table** - Select _Replenishment templates_.
    - **Derived table** - Select _Replenishment templates_.
    - **Field** - Select _Replenishment template_.
    - **Criteria** - Select _Zone min/max replen_. This is the replenishment template that you should have created while preparing the demo data for this scenario.
1. Select **OK** to save the query and go back to the **Replenishment** pane.
1. Select **OK** on the **Replenishment** pane to run the Replenishment template.

Replenishment work will now be created to pick inventory from the BULK zone and replenish it to the FLOOR zone.

## Notes and tips

Here are a few notes and tips for working with this feature:

- To set up replenishment work that goes to the desired zone, you can link the replenishment template lines and location directives in either of the following ways:
  - Edit the location directive header query and filter the selected replenishment template lines.
  - Use a directive code on the replenishment template line and match it to the put location directive.
- If you are using dynamic locations, replenishment work will be created for the first available location, or for a location that already contains inventory, if the location directive action is setup to use the **Consolidate** strategy.
- If you are using fixed locations instead of zones, you should use [standard min/max replenishment](tasks/set-up-min-max-replenishment-process.md).
