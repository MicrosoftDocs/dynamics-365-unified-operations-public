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

# Production Dispensing

Three basic principles drive the design of Production dispensing – unidirectional flow of materials and personnel, segregation of hazardous and non-hazardous materials, separation of storage and manufacturing items and spaces. In the past, convenience dictated the placement of dispensing areas, traditionally located right near warehouses where the materials were stored. Today, the dispensing area is viewed as the entry point to manufacturing and the transition point for materials coming from the warehouse and entering process areas, so specific criteria will determine the best location. Some materials can be weighed into intermediate bulk containers, such as corn starch or lactose used as fillers and binders for the formation of tablets and the filling of capsules. Some materials need to be transferred to production in its original container and may need to be dedicated until dispensing has been completed.

## Setting up Production Dispensing

To activate Production Dispensing you must select the feature for the desired company or site. For that company or site, you can also configure a parameter to allow for the over-dispensing or over-picking of material and then have the remainder returned to inventory with an automatically generated pick list. The final selection allows the identification of a folder/directory on the server for the placement of ASCII files from weight scales.

If the Picking list is created at Release, the user will still have to go through the Start process on the batch or production orders. Upon Starting the order, the user will have to select the Dispensing ticket journal name and select Never as the Automatic BOM consumption; if not, the Picking journal will be created again.

## Using Production Dispensing

There are three modes of issuing materials that are supported by Production Dispensing. The first mode, the proposed quantity of the material is dispensed from the raw material warehouse. This proposed quantity is then added to the manufacturing batch for production.

The second mode, a planned transfer order is automatically generated when there is insufficient quantity of the material in the dispensing warehouse. The proposed amount is dispensed from the container in the dispensing warehouse and then added to the manufacturing batch for production. The remainder of the material in the dispensing warehouse is retained there for other batch or production orders.

The third mode, an amount is picked from the raw material warehouse and entered as the Consumption or picked amount. An amount within the tolerance of the proposed quantity is dispensed and then added to the manufacturing batch for production. The remainder (Dispensed quantity minus the Consumption quantity) is then returned to the raw material warehouse using an automatically generated reverse pick list (dispensing ticket).

Once you have released or started the batch or production order the ingredients will be added to pick lists. If the ingredient is configured as a dispensed item, then it will appear on a dispensing ticket and non-dispensed items will appear of a normal pick list. Once the batch or production order is released/started the user can tell whether there are open pick lists or dispensing tickets by viewing that information on the Production Order List Page.

On the View tab for the Production order list Page there are separate action buttons for the Picking list and Dispensing ticket. Use the Picking list to interact with non-dispensed ingredients and then post the journal. Use the Dispensing ticket to interact with dispensed ingredients.

When the dispensing ticket is selected, the warehouse worker can select 'Lines' and enter the quantity of material that is being picked for the batch or production order. If so configured, the warehouse worker may pick an entire container of material (e.g. 400 lb. in the example below) for the order and then allow the machine operator to dispense from that container. Once that is completed the remainder would be returned.

The machine operator would now select the Dispensing option on the Dispensing Ticket journal to display the Dispensing Ticket form.

The Dispensing Ticket production journal lines form contains a grid in the upper portion of the form that lists the dispensed ingredients. When selected, the grid in the lower portion of the form allows for entry of one or more dispensed weights that can be averaged and posted. Once the weights are entered, the procedure would be to click the 'Post dispensed' button, the Confirm menu button, optionally the Validate menu button, and finally the Post menu button.

| **Path: Production control** \> **Common** \> **All production orders** \> **Dispensing ticket** \> **Dispensing** |  |  |
|-------------------------|-------------------------|-------------------------|
| **Label Name** | **Description** | **Examples/Hints** |
| **Overview - Upper** |  |  |
| Dispensed item | <blockquote></br>The dispensed item from the dispensing ticket picking list</br></blockquote> | Select the dispensed item for which to enter dispensed weights |
| Proposal | <blockquote></br>The amount, in the BOM unit, that is expected to be consumed, based on the estimated production orders. The field displays a value only if you specified that the material consumption of the production must be entered manually for the item.</br></blockquote> |  |
| Consumption | <blockquote></br>Feedback about the actual consumption, in the BOM unit.</br></blockquote> |  |
| Dispensed | <blockquote></br>The amount that is being issued for production.</br></blockquote> | This will be the resultant value after you post the dispensed weight(s). |
| **Tabs** |  |  |
| Overview | <blockquote></br>View or enter the posting date for physical item picking, the production number, and the lot ID. The remaining fields provide an overview of the status of the lines in the picking list journal. This overview includes the item number that is used for production, the configuration, the warehouse where the item is stored, the proposal, and the unit. The overview can also indicate whether the item is finished.</br></blockquote> |  |
| General | <blockquote></br>View or enter general identifying information. This information includes the journal number, bill of material (BOM), inventory quantity, and information about scrap and end reporting for the selected journal line.</br></blockquote> |  |
| Reference | <blockquote></br>View related inventory references and BOM information for the selected journal line.</br></blockquote> |  |
| Financial dimensions | <blockquote></br>View information about financial dimensions, such as the default dimensions and where the dimensions are used in account structures and advanced rule structures.</br></blockquote> |  |
| Inventory dimensions | <blockquote></br>View the inventory dimensions for the selected journal line.</br></blockquote> |  |
| **Buttons** |  |  |
| Confirm | <blockquote></br>Check the dispensed – net amount for the journal line. Also updates the journal line "Dispensed" field with the posted dispensed quantity on the form.</br></blockquote> |  |
| Validate | <blockquote></br>Check the journal for required information before you post it.</br></blockquote> |  |
| Post | <blockquote></br>Check for errors and then post the journal.</br></blockquote> |  |
| Inventory | <blockquote></br>Check inventory information for the journal line. This information includes inventory transactions, the available inventory for the selected item, and reservations.</br></blockquote> |  |
| Print | <blockquote></br>Print the information that is on the journal line.</br></blockquote> |  |
| **Overview - Lower** |  |  |
| Dispensed – net | <blockquote></br>Enter the net amount that is being issued to production</br></blockquote> |  |
| Include in validation | <blockquote></br>Check to include the weight in the averaging calculation</br></blockquote> |  |
| Date and time | <blockquote></br>The current date and time when the weight was entered.</br></blockquote> |  |
| User ID | <blockquote></br>The User ID of the individual who is entering the weights.</br></blockquote> |  |
| Gross | <blockquote></br>The gross or total amount of weight being considered.</br></blockquote> |  |
| Tare | <blockquote></br>The tare or unladen weight being considered.</br></blockquote> |  |
| Scales | <blockquote></br>The Test Instrument that is used to identify the specific scale equipment related to the entered weight.</br></blockquote> |  |
| **Tabs** |  |  |
| General | <blockquote></br>View or enter general weight line information. This information includes the gross, tare, and net dispensed reporting for the selected journal line.</br></blockquote> |  |
| **Buttons** |  |  |
| Add | <blockquote></br>Allows additional weight lines to be entered for the journal line.</br></blockquote> |  |
| Remove | <blockquote></br>Removes the selected weight line from the journal.</br></blockquote> |  |
| Net weight from scales | <blockquote></br>Populates the Dispensed – net weight field from an ASCII text file in the server directory.</br></blockquote> |  |
| Gross weight from scales | <blockquote></br>Populates the Gross weight field from an ASCII text file in the server directory.</br></blockquote> |  |
| Tare weight from scales | <blockquote></br>Populates the Tare weight field from an ASCII text file in the server directory.</br></blockquote> |  |
| Post dispensed | <blockquote></br>Calculates the average weight of the lines marked with 'Include in validation'</br></blockquote> |  |

If the user had posted the form above, with the Consumption quantity greater than the Proposal quantity and the Dispensed quantity less than the Consumption quantity (and the item is configured to allow over-dispensing with reverse pick list) then the posting will automatically generate an adjustment picking list journal. The user can select the line that indicates the new journal number and then an 'Open the adjustment journal' button will appear.
