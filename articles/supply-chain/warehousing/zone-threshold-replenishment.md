# Zone threshold replenishment

Zone based replenishment uses a min/max [replenishment](replenishment.md) strategy, but evaluates entire warehouse zones instead of just individual locations. This helps make it faster for warehouse managers to find out when additional inventory is needed within a picking zone.

The set up for this feature is similar to the setup for location-based replenishment, except that when you are setting up a template for min/max replenishment, you can now also make a setting that specifies whether the threshold should be evaluated per location or per zone. When setting up an evaluation based on zone, you must add specific zones to the zone selection query.

As with location-based min/max replenishment, zone-based min/max replenishment is based on setting up a minimum threshold of inventory that triggers the creation of replenishment work for selected items and item variants. This replenishment work will increase inventory up to the configured maximum threshold for the zone.

Unlike location-based min/max replenishment, zone replenishment does not require fixed locations to evaluate whether locations should store a certain item or not. Zone-based replenishment therefore allows you to use min/max replenishment without fixed locations for each item or item variant within the warehouse. When a quantity in the zone falls below the specified minimum, replenishment will be created, and location directives will determine which specific location to put the inventory into.

<!-- KAMAYBAC: It seems like this feature isn't under Feature Management. Is that right? -->

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
    - **Directive code** – "Zone replen"
    - **Directive description** – "Zone replenishment"
1. Select **Save** to save the new code.

### Set up your replenishment templates

[Min/Max replenishment templates](tasks/set-up-min-max-replenishment-process.md) are the primary mechanism for maintaining optimal levels in picking locations. This is where you must set up the rules by which you will replenish inventory in the warehouse, including for zone-based replenishment.

#### View and edit replenishment templates

To view or edit your replenishment templates, go to **Warehouse management > Setup > Replenishment > Replenishment > templates**.

#### Prepare a sample-data replenishment template

Here is an example for how to prepare a replenishment template. If you're planning to work through the example at the end of this topic, then use the sample-data values provided here. Otherwise, use your own values.

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management > Setup > Replenishment > Replenishment > templates**.
1. Select **Edit** to put the page in edit mode.
1. Select **New** on the Action Pane to add a new row to the **Overview** table and enter the following values for it:
    - **Replenish template** – "Zone min/max replen"
    - **Description** – "Zone min/max replenishment"
    - **Replenishment type** – "Minimum or maximum"
1. With the new row still selected in the **Overview** table, select **New** above the **Replenishment template details** table to add a new row to that table. Make the following settings for the new row:
    - **Sequence number** - Enter "1".
    - **Description** – Enter "Pick zone replenishment"
    - **Replenishment unit** – Select "ea".
    - **Directive code** – This will link this replenishment template with a location directive. Select the sample-data directive code that you just created: "Zone replen".
    - **Minimum quantity** – This sets the quantity at which replenishment will be triggered. Enter "50".
    - **Maximum quantity** – This sets the maximum quantity of an item that can be present in a zone. Generated replenishment work will increase inventory to this quantity. Enter "150".
    - **Unit** – Sets the unit for the min and max values. Select "ea".
    - **Demand increment** – Select "Round up".
    - **Replenish empty fixed locations** – Select this check box.
    - **Replenish only fixed locations** –  Deselect this check box.
    - **Product query mode** – Select "Product query".
    - **Replenishment threshold scope** – Sets whether the template should evaluate by zone or by specific location. Select "Zone".
    - **Warehouse** - Select "61".
1. Select **Select products** above the **Replenishment template details** table to open the **Product query** pane. Add a row with the following values to the **Range** table:
    - **Table** - "Items"
    - **Derived table** - "Items"
    - **Field** - "Item number"
    - **Criteria** - "A0001"
1. Select **OK** to save your query and close the pane.
1. Select **Select zones to replenish** above the **Replenishment template details** table to open the **Zone query** pane. Add a row with the following values to the **Range** table:
    - **Table** - "Warehouse zone"
    - **Derived table** - "Warehouse zone"
    - **Field** - "Zone ID"
    - **Criteria** - "FLOOR"

### Set up your location directives

Unlike location-based min/max replenishment, zone-based replenishment requires you to set up both pick-location and put-location directives because the system evaluates the whole zone instead of just the outbound work pick location.

#### View and edit location directives

To view or edit your replenishment templates, go to **Warehouse management > Setup > Location directives**. See the next section of examples of how to use the settings here to create the required pick-location and put-location directives.

#### Prepare sample-data location directives

To prepare demo data for use with the example given at the end of this topic, you need two location directives, one for pick and one for put.

##### Create a replenishment pick directive

1. Select the **USMF** legal entity to work with the demo data.
1. Go to **Warehouse management > Setup > Location directives**.
1. In the left pane, set **Work order type** to "Replenishment".
1. Select **New** on the Action Pane to create a new directive and make the following settings:
    - **Name** – Enter "Zone pick"
    - **Work type** – Select "Pick"
    - **Site** - Select "6"
    - **Warehouse** - Select "61"
    - **Directive code** – leave empty
    - **Multi SKU** – Set to "No"
1. Select **Save** to create a directive with your settings so far.
1. In the **Lines** FastTab, select **New** to add a new line to the table and then make the following settings for it:
    - **Sequence number** – Enter "1"
    - **From quantity** – Enter "0"
    - **To quantity** – Enter "10000000"
    - **Locate quantity** – Select "None"
    - **Allow split** – Select this check box (yes)
1. Select **Save** to save the new line.
1. With your new line still selected in the **Lines** table, select **New** on the **Location directive actions** FastTab to add a new action to the table and then make the following settings for it:
    - **Sequence number** – Enter "1"
    - **Name** – Enter "Pick from bulk"
    - **Fixed location usage** – Select "Fixed and non-fixed locations"
    - **Strategy** – Select "None"
1. Select **Save** to save the new action.
1. With your action still selected in the **Location directive actions** table, select **Edit query** on the **Location directive actions** FastTab.
1. A query pane opens, which lets you select the locations you want to replenish from. Select **Add** on the **Range** tab to add a new row to the table here and then make the following settings for the new row:
    - **Table** - "Locations"
    - **Derived table** - "Locations"
    - **Field** - "Zone ID"
    - **Criteria** - "BULK"
1. Select **OK** to save your query and close the pane.
1. Select **Save** to save your location directive.

##### Create a replenishment put directive

1. Continue working on the **Location directives** page and in the left pane, make sure **Work order type** is still to "Replenishment".
1. Select **New** on the Action Pane to create another new directive and make the following settings:
    - **Name** – Enter "Zone put"
    - **Work order type** – Select "Put"
    - **Site** - Select "6"
    - **Warehouse** - Select "61"
    - **Directive code** – Select "Zone replen". This will link this location directive with the replenishment template we created earlier using the code we also created earlier.
    - **Multi SKU** – Set to "No"
1. Select **Save** to create a directive with your settings so far.
1. In the **Lines** FastTab, select **New** to add a new line to the table and then make the following settings for it:
    - **Sequence number** – Enter "1"
    - **From quantity** – Enter "0"
    - **To quantity** – Enter "10000000"
    - **Locate quantity** – Select "None"
    - **Allow split** – Select this check box (yes)
1. Select **Save** to save the new line.
1. With your new line still selected in the **Lines** table, select **New** on the **Location directive actions** FastTab to add a new action to the table and then make the following settings for it:
    - **Sequence number** – Enter "1"
    - **Name** – Enter "Zone put"
    - **Fixed location usage** – Select "Fixed and non-fixed locations"
    - **Strategy** – Select "Consolidate"
1. Select **Save** to save the new action.
1. With your action still selected in the **Location directive actions** table, select **Edit query** on the **Location directive actions** FastTab.
1. A query pane opens, which lets you select the zone you want to replenish to. This should be the same as Zone specified on the Replenishment template. Select **Add** on the **Range** tab to add a new row to the table here and then make the following settings for the new row:
    - **Table** - "Locations"
    - **Derived table** - "Locations"
    - **Field** - "Zone ID"
    - **Criteria** - "FLOOR"
1. Select **OK** to save your query and close the pane.
1. Select **Save** to save your location directive.

## Try out the feature

This section provides a sample scenario that illustrates how to work with this feature.

### Prepare the sample data required for this sample scenario

Before you start working through the scenario, you must activate sample data and set up the feature as described in this section and in the previous sections of this topic.

#### Use the USMF legal entity

To work through this sample scenario using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

#### Prepare additional sample data

After you have selected the **USMF** legal entity, add the additional required sample data as described in [Set up zone-based replenishment](#setup).

#### Check your on-hand inventory

Do the following to make sure your system includes enough inventory to support the sample scenario:

1. Ensure there is on-hand inventory for item A0001 at two different locations within the pick zone specified on the replenishment template, but still less total inventory than required by the **Minimum quantity** specified on the replenishment template. This is to simulate how the calculation occurs for the whole zone, instead of only for a single location. Use any of the warehouse processes to adjust inventory if needed.
2. Ensure there is enough inventory for item A0001 at the bulk location where the replenishment work should pick the items from. The total inventory must be greater than the quantity required by the **Maximum quantity** specified on the replenishment template.

<!-- KAMAYBAC: Can we give links for how to do these things? -->

### Sample scenario: Run zone min/max replenishment

Once you have all the prerequisite sample data in place, you can trigger a replenishment by doing the following:

1. Go to **Warehouse management > Replenishment > Replenishments**.
1. The **Replenishment** pane opens. In the **Records to include** FastTab, select **Filter**.
1. The **Inquiry** pane opens. On the **Range** tab, edit the default table row provided as follows:
    - **Table** - Select "Replenishment templates".
    - **Derived table** - Select "Replenishment templates".
    - **Field** - Select "Replenishment template".
    - **Criteria** - Select "Zone min/max replen". This is the replenishment template that you should have created while preparing the demo data for this scenario.
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
