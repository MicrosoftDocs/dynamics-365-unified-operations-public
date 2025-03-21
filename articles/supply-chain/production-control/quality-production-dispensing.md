---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Production dispensing

Production dispensing meets regulated and controlled requirements for dispensing ingredients and materials in production processes commonly found in industries such as life sciences and pharmaceuticals. It includes support for

- Identifying products with special dispensing requirements.
- Ensuring secure separation between material picking activities and product dispensing, as dispensing often needs to occur in highly regulated and restricted areas, such as clean rooms.
- Restricting dispensing activities to authorized personnel.
- Setting up rules for dispensed products, including thresholds for over- and under-dispensing.
- Configuring confirmation of dispensing activities with an electronic signature.

## Set up a dispense pick journal

A journal is used for dispensing materials to production and batch orders. You must set up at least one journal for this purpose. 

1. Go to **Production control > Setup > Production journal names**
1. Select **New** to create a new journal name for dispensing.
1. Enter **Name** and **Description**.
1. Leave the all other settings at their default values.


## Enable and configure production dispensing

You must turn on the feature and make basic configuration. 

### Set up workers who are authorized for production dispensing

To restrict the dispensing process to specific workers follow these steps

1. 

### Set up a measuring device

To set up a **Measuring device** follow theses steps.

1. Go to **Inventory management > Setup > Quality control > Measuring devices**
1. Select **New** and fill out following information
    - **Measuring device** - Identification of the measuring device used in the dispensing process.
    - **Description**- Description of the device.
    - **Test instrument tag** - Select a tag define for the test instrument. Read more about **Test instrument tags** and **Test instrument calibration** here: <!-- TO-DO: JOHANHO Insert link to instrument calibration- :  -->

[!NOTE] - The **Measuring device** you define only serves as information about the name of the device you will be using in the dispense process. 


### Required set up in the production control parameters

1. Go to **Production control > Setup > Production control parameters** 
1. Open the **Standard update** tab
1. Make the following settings:
    - **Enable dispensing for production** - Set to *Yes* to enable using production dispensing in a production flow.
    - **Allow over-dispensing with reverse pick** - Set to *Yes* to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list.
1. Open the **Journals** tab and make the following setting
    - **Dispensing ticket** - Select the journal name you created. This will be the default journal for dispensed products.
1. Open the **General** tab to make the following setting
    - **Default measuring device** - In the drop down, select the measuring device that should be defaulted in the **Dispense ticket** page.
 
### Set up a product for the dispensing process

To use a dispensing process, you must configure dispensing options for each relevant product. 

[!NOTE] - Only products enabled for the advanced processes can enabled for the dispensing process.

1. Go to **Product information management > Products > Released products**
1. Open a product that you want to set up for dispensing.
1. Expand the **Manage inventory** FastTab.
1. From the **Dispensing**Field group make the following settings: 
    - **Dispensing control** - Select this option to enable dispensing control for the product.
    - **Under dispensing** - The percentage by which the dispensed quantity is allowed to be less than the proposed quantity.
    - **Over dispensing** - The percentage by which the dispensed quantity is allowed to be larger than the proposed quantity.
    - **Authorized personnel** - Indication that only authorized personnel can do production dispensing.
   
### Set up on BOM and Formula lines for the dispensing process 

On BOM and Formula lines you can override the thresholds for over- and under dispensing from the product.

1. Go to **Product information management > Products > Released products**
1. Select a product that is defined for batch production.
1. In the toolbar under the **Engineering** tab, select the **Formula versions**.
1. In the **Formula versions** page, under the **Formulas** tab select **Formula** to open the **Formula** page.
1. Expand the **Lines details** FastTab and select the tab **Setup**.
1. Under the **Dispensing** field group find the following parameters
    - **Allow over-dispensing with reverse pick** - ??
    - **Overdispense** - The percentage by which the dispensed quantity is allowed to be larger than the proposed quantity. The value will override the value specified in the same field on the release products. 
    - **Underdispense** - The percentage by which the dispensed quantity is allowed to be less than the proposed quantity. The value will override the value specified in the same field on the release products.


If the Picking list is created at Release, the user will still have to go through the Start process on the batch or production orders. Upon Starting the order, the user will have to select the Dispensing ticket journal name and select Never as the Automatic BOM consumption; if not, the Picking journal will be created again.

## Using Production Dispensing



Use the following procedure to create a production or batch order where the dispensing process is used.

1. Go to **Production control > Production orders > All production orders** 
1. To create a new order select **New production order** or **New batch order** from the toolbar. 
1. In the dialog, select a product with a BOM or Formula that has at least on product enabled for dispensing.
1. Select **Create** to confirm the creation of the order and then select **Estimate** to bring the order in the estimated state.
1. In the toolbar, select **Estimate** and confirm the dialog.
1. In the toolbar, select **Release**. 
1. In the **Release dialog** select the **General** tab.
1. In the **Picking list journal section** make the following selections
    - **Picking list** - Select a picking list from the drop down.
    - **Dispensing ticket** - Select a dispensing ticket from the drop down.
 [!NOTE] - You can set up the journals names to default in **Default values** dialog.   
1. Select **OK** in the release dialog to confirm the release step for the order.
1. Back on the **All production orders** list page, notice the value in the two columns
    - **Picking list status** = *Open*.
    - **Dispensing ticket status** = *Open*.
    These two fields indicates that an un-posted **Picking list journal** and **Dispensing ticket** exist. The **Picking list journal** contains all the **BOM** and **Formula** lines for products not enabled for dispensing. The **Dispensing ticket** is a journal, much similar to the production picking list journal, with the items on the BOM or Formula which are enabled for dispensing.
1. To manage the dispensing process, select **Dispensing ticket** under the **View** tab. 
1. 

    1. select the **View** tab in the toolbar.
1. In the **Journals** section, you have following two options to manage the dispensing process
    - **Dispensing pick journal** - 



There are three modes of issuing materials that are supported by Production Dispensing. The first mode, the proposed quantity of the material is dispensed from the raw material warehouse. This proposed quantity is then added to the manufacturing batch for production.

:::image type="content" source="media/Dispensing - Image 1.png" alt-text="":::

The second mode, a planned transfer order is automatically generated when there is insufficient quantity of the material in the dispensing warehouse. The proposed amount is dispensed from the container in the dispensing warehouse and then added to the manufacturing batch for production. The remainder of the material in the dispensing warehouse is retained there for other batch or production orders.

:::image type="content" source="media/Dispensing - Image 2.png" alt-text="":::

The third mode, an amount is picked from the raw material warehouse and entered as the Consumption or picked amount. An amount within the tolerance of the proposed quantity is dispensed and then added to the manufacturing batch for production. The remainder (Dispensed quantity minus the Consumption quantity) is then returned to the raw material warehouse using an automatically generated reverse pick list (dispensing ticket).

:::image type="content" source="media/Dispensing - Image 3.png" alt-text="":::


Once you have released or started the batch or production order the ingredients will be added to pick lists. If the ingredient is configured as a dispensed item, then it will appear on a dispensing ticket and non-dispensed items will appear of a normal pick list. Once the batch or production order is released/started the user can tell whether there are open pick lists or dispensing tickets by viewing that information on the Production Order List Page.

On the View tab for the Production order list Page there are separate action buttons for the Picking list and Dispensing ticket. Use the Picking list to interact with non-dispensed ingredients and then post the journal. Use the Dispensing ticket to interact with dispensed ingredients.

When the dispensing ticket is selected, the warehouse worker can select 'Lines' and enter the quantity of material that is being picked for the batch or production order. If so configured, the warehouse worker may pick an entire container of material (e.g. 400 lb. in the example below) for the order and then allow the machine operator to dispense from that container. Once that is completed the remainder would be returned.

The machine operator would now select the Dispensing option on the Dispensing Ticket journal to display the Dispensing Ticket form.

The Dispensing Ticket production journal lines form contains a grid in the upper portion of the form that lists the dispensed ingredients. When selected, the grid in the lower portion of the form allows for entry of one or more dispensed weights that can be averaged and posted. Once the weights are entered, the procedure would be to click the 'Post dispensed' button, the Confirm menu button, optionally the Validate menu button, and finally the Post menu button.

- **Path: Production control > Common > All production orders > Dispensing ticket > Dispensing**
- **Label Name** – **Description** – **Examples/Hints**
- **Overview - Upper**
  - **Dispensed item** – The dispensed item from the dispensing ticket picking list – Select the dispensed item for which to enter dispensed weights
  - **Proposal** – The amount, in the BOM unit, that is expected to be consumed, based on the estimated production orders. The field displays a value only if you specified that the material consumption of the production must be entered manually for the item.
  - **Consumption** – Feedback about the actual consumption, in the BOM unit.
  - **Dispensed** – The amount that is being issued for production. – This will be the resultant value after you post the dispensed weight(s).
- **Tabs**
  - **Overview** – View or enter the posting date for physical item picking, the production number, and the lot ID. The remaining fields provide an overview of the status of the lines in the picking list journal. This overview includes the item number that is used for production, the configuration, the warehouse where the item is stored, the proposal, and the unit. The overview can also indicate whether the item is finished.
  - **General** – View or enter general identifying information. This information includes the journal number, bill of material (BOM), inventory quantity, and information about scrap and end reporting for the selected journal line.
  - **Reference** – View related inventory references and BOM information for the selected journal line.
  - **Financial dimensions** – View information about financial dimensions, such as the default dimensions and where the dimensions are used in account structures and advanced rule structures.
  - **Inventory dimensions** – View the inventory dimensions for the selected journal line.
- **Buttons**
  - **Confirm** – Check the dispensed – net amount for the journal line. Also updates the journal line "Dispensed" field with the posted dispensed quantity on the form.
  - **Validate** – Check the journal for required information before you post it.
  - **Post** – Check for errors and then post the journal.
  - **Inventory** – Check inventory information for the journal line. This information includes inventory transactions, the available inventory for the selected item, and reservations.
  - **Print** – Print the information that is on the journal line.
- **Overview - Lower**
  - **Dispensed – net** – Enter the net amount that is being issued to production
  - **Include in validation** – Check to include the weight in the averaging calculation
  - **Date and time** – The current date and time when the weight was entered.
  - **User ID** – The User ID of the individual who is entering the weights.
  - **Gross** – The gross or total amount of weight being considered.
  - **Tare** – The tare or unladen weight being considered.
  - **Scales** – The Test Instrument that is used to identify the specific scale equipment related to the entered weight.
- **Tabs**
  - **General** – View or enter general weight line information. This information includes the gross, tare, and net dispensed reporting for the selected journal line.
- **Buttons**
  - **Add** – Allows additional weight lines to be entered for the journal line.
  - **Remove** – Removes the selected weight line from the journal.
  - **Net weight from scales** – Populates the Dispensed – net weight field from an ASCII text file in the server directory.
  - **Gross weight from scales** – Populates the Gross weight field from an ASCII text file in the server directory.
  - **Tare weight from scales** – Populates the Tare weight field from an ASCII text file in the server directory.
  - **Post dispensed** – Calculates the average weight of the lines marked with 'Include in validation'

If the user had posted the form above, with the Consumption quantity greater than the Proposal quantity and the Dispensed quantity less than the Consumption quantity (and the item is configured to allow over-dispensing with reverse pick list) then the posting will automatically generate an adjustment picking list journal. The user can select the line that indicates the new journal number and then an 'Open the adjustment journal' button will appear.
