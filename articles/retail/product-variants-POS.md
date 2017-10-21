## Inventory look up on POS - 


Inventory look-up on POS helps Retailers achieve real-time operational excellence and insights by connecting the stores, POS and the back office. It provides an accurate real time view of products inventory across various stores & distribution centers. It helps Retailers drive additional efficiencies & cost savings through improved inventory planning in real-time. 

An accurate real-time inventory view across organization, helps store-associates provide an elevated customer service at right moment. As the moment that matters most is the time when customer is ready to make a purchase decision & with real-time inventory information, at fingertips of cashiers in-store, empowers them to be able to promise product delivery/pick up accurately. 

On Retail Point-of-sale from home-page you can launch the 'Inventory look-up' and you shall be navigated to this view.

![POS home page](media/POSHomepage.png)

Upon being navigated to this view, user enters a product on the Number pad to view quantity on hand for multiple stores and warehouses on the Inventory lookup page. 

![Standard inventory look up](media/InventoryLookUp.png)

On inventory look-up page Along with quantity on-hand, you shall also notice there are the values shown for **Reserved** and **Ordered** for each location. 

**Reserved quantity** refers to *'Physical reserved'* value from back-office for an entered product number at the given location.

**Ordered quantity** refers to *'Ordered in total'* value from back-office for an entered product number at the given location. 

**What’s the nature of locations for which inventory availability information is shown? **

The locations list comprises of two types of entities - **Retail stores** & **Distribution centers**. 

**Retail stores** are configured using **store-locator group**. That means, it shows only store locations that are part of a store-locator group of the current store. 

And of various types of **Distribution centers** that are configurable in Dynamics 365 for Retail - we show inventory availability information only for the **Standard/Default type** of Distribution centers. *(Note - We do not show inventory availability information in POS for Transit, Quarantine & GoodsInRoute_RU type of warehouses.)*

On inventory look up page, in addition to the *current quantity on hand, reserved & ordered*, the future **available to promise (ATP) quantities** can be viewed for each individual store. To do so, select the store that you want to view the ATP for and then click **Show store availability**.

![ATP](media/ATP.png)

**How to navigate to 'Dimension based matrix view' showing all variants availability information?

There are two ways to navigate to **'Dimension based matrix view'** and on following two pages 
	1. Product details page and
	2. Inventory look up page

You would notice a new control available on the app-bar titled as **'View all variants'**. And this button is active/available only for an item **(Product master)** with product variants. (*Note - 'View all variants' button in app-bar is inactive/ not-available for standard standalone products or kits.*)

![StandardViewToMatrix](media/StandardToMatrix.png)

Upon clicking **'View all variants'** from *'Product details page'* of a **product master** or from *'Inventory look up page* without selecting a location' user shall be navigated to **'Dimension based matrix view'** showcasing inventory availability information for all variants of an entered product for *current store*.

![InventoryDimensionMatrixView](media/Matrix.png)
(*Note - The display order of dimensions is alphabetic - that's because the display order for the dimensions on this product were not configured)*

And as you may notice, there are various kind of variant tiles 

| Variant Tile On-hand value | Description                                                                                                                                                                                                               |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Numeric (>0)               | It indicates that a particular variant is released to the selected location, and user can interact with that individual cell to perform additional actions.                                                               |
| Numeric (= 0)              | It indicates that a particular variant is released to the selected location, and there's no availability of that item in selected location but user can interact with that individual cell to perform additional actions. |
| n/a or dead cell           | It indicates that a particular variant is not released to the selected location, and user cannot interact with that individual cell to perform any additional actions.                                                    |


User can swiftly **change the pivot** for dimensions by choosing the dimension they would like to swap.

![ChangingPivot](media/ChangePivot.png)
*(Note: The display order of dimensions for this product is custom [non-alphabetic], it's as per the dimension display order set in back office on product)*

![PivotChanged](media/PivotChanged.png)



