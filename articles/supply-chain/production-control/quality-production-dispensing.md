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

Production Dispensing ensures compliance with regulated and controlled standards for dispensing ingredients and materials in production processes, particularly in industries such as life sciences and pharmaceuticals. Its main capabilities include:

- Establishing a process that separates material picking activities from product dispensing.
- Identifying and configuring products for the dispensing process.
- Restricting dispensing activities to authorized personnel and option to require a digital signature for verifying dispensed products.

Follow the these steps to enable and configure the feature

## Set up a dispense pick journal

You need to set up a journal for dispensing materials to production and batch orders. Follow these steps to set up a journal. 

1. Go to **Production control > Setup > Production journal names**
1. Select **New** to create a new journal name for dispensing.
1. Enter **Name** and **Description**.
1. Leave the all other settings at their default values.

## Authorized users for production dispensing

You can control access to the production dispensing process by assigning the **Production dispenser** security role to designated users. To assign the role, use the following steps

1. Go to **System administration > Users > Users**
1. Open the user you want to enable for the **Production dispensing**
1. In the **Users's roles** section select **Assign roles**
1. From the list, select the role **Production dispenser** and select **OK**

## Enable Electronic signature for production dispensing

To enable **Electronic signature** for posting the production picking list journal for dispensed and non-dispensed products, use the following steps

1. Go to **Organization administration > Setup > Electronic signature > Electronic signature requirements**
1. Select the the name of the following **Electronic signature requirements** 
    - **Post dispensing ticket production journal**
    - **Post picking list production journal (non-dispensing)**
1. Set the field **Signature required** to *true* for both requirements.

## Set up a measuring device

To set up a **Measuring device** follow theses steps.

1. Go to **Inventory management > Setup > Quality control > Measuring devices**
1. Select **New** and fill out following information
    - **Measuring device** - Identification of the measuring device used in the dispensing process.
    - **Description**- Description of the device.
    - **Test instrument tag** - Select a tag define for the test instrument. Read more about **Test instrument tags** and **Test instrument calibration** here: <!-- TO-DO: JOHANHO Insert link to instrument calibration- :  -->

[!NOTE] - The **Measuring device** you define only serves as information about the name of the device you will be using in the dispense process. 


## Required set up in the production control parameters

1. Go to **Production control > Setup > Production control parameters** 
1. Open the **Standard update** tab
1. Make the following settings:
    - **Enable dispensing for production** - Set to *Yes* to enable using production dispensing in a production flow.
    - **Allow over-dispensing with reverse pick** - Set to *Yes* to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list.
1. Open the **Journals** tab and make the following setting
    - **Dispensing ticket** - Select the journal name you created. This will be the default journal for dispensed products.
1. Open the **General** tab to make the following setting
    - **Default measuring device** - In the drop down, select the measuring device that should be defaulted in the **Dispense ticket** page.
 
## Set up a product for the dispensing process

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
   
## Set up on BOM and Formula lines for the dispensing process 

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

In a normal production run, workers use the **Production picking list journal** to register the amount of materials consumed for the production order. For order that have materials configured for dispensing, workers use the **Dispensing ticket** journal to register the dispensed amounts prior to consumption. For orders using the dispensing process, the **Dispensing ticket** and the **Production picking list journal** can be configured to be created when the order is **Released**, instead as for normal production run when the order is **Started**. The dispensing process also offers an option to return remaining material that was staged to the production area for dispensing. You enable this option in the production control parameters and on the product configured for dispensing. 

The following procedure provides an example of using **Production dispensing** where the **Picking list journal** for non-dispensed products and the **Dispensing ticket** for dispensed products are created as production order release. After completing the dispensing ticket a picking list journal for the remaining material that was staged for the dispensing process is created.

1. Make sure the required setting for using **Production dispensing** is set up as described in the previous sections. 
1. Go to **Production control > Setup > Production control parameters** 
1. Open the **Standard update** tab and make the following setting
    - **Allow over-dispensing with reverse pick** - Set to *true*
1. Go to **Product information management > Products > Released products** and create a finished good with a bill of material that contains at least one product enabled for dispensing and one product that is not enabled for dispensing. 
1. For the product enabled for dispensing, make the following settings
    - **Allow over-dispensing with reverse pick** - Set to *true*
    - **Overdispense** - Set to *10* percent. 
    - **Underdispense** - Set to *10* percent.
1. Go to **Production control > Production orders > All production orders** 
1. Select **New production order** or **New batch order** to create a new order for the finished product defined in the previous step.
1. In the toolbar, select **Estimate** to bring the order in the estimated state.
1. In the toolbar, select **Release** and make the following selection in the dialog
    - **Picking list** - Select a picking list from the drop down.
    - **Dispensing ticket** - Select a dispensing ticket from the drop down.
 [!NOTE] - You can set up the journals names to default in **Default values** dialog.   
1. Select **OK** in the release dialog to confirm the release step for the order.
1. Back on the **All production orders** list page, notice the value in the two columns
    - **Picking list status** = *Open*.
    - **Dispensing ticket status** = *Open*.
    These two fields indicates that an un-posted **Picking list journal** and **Dispensing ticket** exist. 
1. In the toolbar under the **View** tab, select the **Dispensing pick journal**
1. Open the journal, and change the quantity in the **Consumption** field to a value that is greater then the value in the **Proposal** field. The quantity in the **Consumption** field represents the amount of material you have staged to the process.
1. Close the **Dispensing pick journal** and open the **Dispensing ticket** which is also located under the **View** tab.
1. In the **Dispensing details** section, select **New** to create a new line for the dispensed quantity for the product. You can create multiple lines, which will then represents multiple measurements for the same dispensed amount. 
1. Select **Post dispensed** to complete the registered values for dispensing. This process will calculate the average of registered values and update it in the field **Dispensed** for the product in the **Journal lines** section. Notice, that you will get an error in this process, if the dispensed a quantity exceeds the thresholds defined on the product.
1. When you have completed all the lines in the **Dispensing ticket**, select **Confirm** from the toolbar. This action will update the calculated value in the **Dispensed** field in the **Dispensing pick journal**.
1. After confirming the dispensed quantities, select **Post** which will post the **Dispensing pick list** journal with the dispensed quantities. This action will also create a **Dispensing adjustment** journal with a proposal to return a quantity that equals the difference between the quantity that has been staged to the production order and the quantity that has been dispensed. 
1. 

