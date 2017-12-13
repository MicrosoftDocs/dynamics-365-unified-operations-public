
## Inventory lookup on POS 


Inventory lookup on POS helps retailers achieve real-time operational excellence and insights by connecting stores, POS, and the back office. It provides an accurate real-time view of products inventory across stores and distribution centers. It also helps retailers drive additional efficiencies and cost savings by improving inventory planning in real time. 

An accurate real-time inventory view across an organization helps store-associates to provide timely, elevated customer service. The moment that matters most is when the customer is ready to make a purchase decision. It's important for real-time inventory information to be at the fingertips of cashiers in the store, to empower cashiers to be able to accurately promise product delivery and pick up. 

Go to the **Retail Modern POS** workspace or **Retail Cloud** POS workspace to open the **Inventory lookup** page.

![POS home page](media/POSHomepage.png)

The **Inventory lookup** page allows you to enter a product on the numeric keypad so you can view quantity on hand for multiple stores and warehouses. 

![Standard inventory look up](media/InventoryLookUp.png)

There are also values shown for **Reserved** and **Ordered** for each location. 

 - **Reserved quantity** - Refers to the Physical reserved value from back office for a product number at the given location.

 - **Ordered quantity** - Refers to the Ordered in total value from back office for a product number at the given location. 

### Locations for which inventory availability information is shown

The locations list is comprised of two types of entities:

 - **Retail stores** - This is the list of stores that are configured using the **Store-locator group** for the current store in the headquarters. 

- **Distribution centers** - These types are configurable in Dynamics 365 for Retail but we show inventory availability information only for the **Standard/Default type** of Distribution centers. 
> [!NOTE]
> Inventory availability information is not displayed for POS for Transit, Quarantine, and Goods in Route type of warehouses.

On the **Inventory lookup** page, in addition to the current quantity on hand, reserved, and ordered, future available to promise (ATP) quantities can be viewed for each store. To do view this information, select the store that you want to view the ATP for and then click **Show store availability**.

![ATP](media/ATP.png)

### Open the **Dimension based matrix view** to show all variants

There are two ways to navigate to the **Dimension based matrix** view from the following pages: 
   - **Product details** page
   - **Inventory lookup** page

The **View all variants** button on the app bar is available only for an item product master with product variants. 
> [!NOTE]
> The **View all variants** button on the app bar is not available for stand-alone products or kits.

![StandardViewToMatrix](media/StandardToMatrix.png)

Click **View all variants** on the **Product details** page of a product master or from the **Inventory lookup** page, without selecting a location, go to the **Dimension based matrix** view to view the inventory availability information for all variants of a product for the current store.

![InventoryDimensionMatrixView](media/Matrix.png)
> [!NOTE]
> The display order of dimensions is alphabetic because the display order for the dimensions on this product were not configured.

There are various kind of variant tiles, as noted in the following table. 

| **Variant tile on-hand value** | **Description**                                                                                                                                                                                                               |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Numeric (>0)               | Indicates that a variant is released to the selected location, and you can perform additional actions in that individual cell.                                                               |
| Numeric (= 0)              | Indicates that a variant is released to the selected location, and the item is not available in selected location, but you can perform additional actions in that cell. |
| n/a or dead cell           | Indicates that a variant is not released to the selected location, and you cannot perform additional actions in that cell.                                                    |


You can also change the pivot for dimensions by selecting the dimension that you would like to swap.

![ChangingPivot](media/ChangePivot.png)
> [!NOTE]
> The display order of dimensions for this product is custom (non-alphabetic). It's based on the dimension display order that is set in the back office.

![PivotChanged](media/PivotChanged.png)

Additionally, to boost a store associate's productivity there are additional actions that can be performed from a product-dimension based matrix form of inventory lookup. For example, you can do the following: 
 
- Change the store location to look up inventory availability of all product variants at other locations. This include other stores in the store-locator group as well as standard/default types from the distribution center.
- Sell an individual product variant to a customer using cash and carry, pick up at store, and ship to address. 
- Provide the customer with available-to-promise information for an individual product variant at a specific location. 

![VariantTileActions](media/VariantActions.png)
> [!NOTE]
> The display order of dimensions is alphabetic because the display order for the dimensions on this product were not configured. 

| **Actions**              | **Description**                                                                                                                                                                                                          |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Sell now             | Adds the selected item variant to the transaction and re-directs the user to the transaction screen. (Not available when the selected location is of type distribution center.)                                             |
| Pick up in store     | Creates a customer order for that product variant to be picked up from the selected location and re-directs the user to the transaction screen. (Not available when the selected location is of type distribution center.)     |
| Ship product         | Creates a customer order for the product variant to be shipped from the selected location and re-directs the user to the transaction screen.                                                                              |
| Availability         | Shows the available to promise information (ATP) for the selected variant combination for the selected location.                                                                                                     |
| Show all locations      | Switches the user to standard inventory look up view, highlighting inventory availability information for that item variant across all stores in the store-locator group and standard/default distribution centers. |
| View product details | Re-directs the user to the product details page of the associated product master.                                                                                                                                        |
