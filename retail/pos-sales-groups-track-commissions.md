---
# required metadata

title: Track commissions in POS using sales groups
description: It's a common retail practice to track sales by the associate who worked with the customer—providing assistance, up-selling, cross-selling, and processing the transaction.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 41
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 261234
ms.assetid: 7cd68ecc-cc09-48ab-8cb8-48d5c304effa
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Track commissions in POS using sales groups

[!include[banner](includes/banner.md)]


It's a common retail practice to track sales by the associate who worked with the customer—providing assistance, up-selling, cross-selling, and processing the transaction.

Tracking sales by sales representative is a measure of the associates selling abilities, while sales by cashier is a measure of speed and efficiency. Sales tracked by sales representative are also often used to calculate commissions or other incentives.

## Configuring a worker to be a sales representative in POS
When a worker is added to a sales group, they become eligible for commission and can be identified as a sales representative in the system. A worker who isn't in a sales group isn't eligible for commission and won't be listed as a sales representative in the point of sale (POS) application. In POS, the list of sales representatives is derived from all sales groups that contain at least one worker assigned to the store. The list is shown in POS as a combination of Sales group ID and Name (ID : Name). A default sales group can be assigned to workers to support scenarios where the retailer chooses to set the sales representative on POS lines automatically. Users can select from any sales group that the worker is a member of.

## Functionality profile settings
There are a number of functionality profile settings for a store that will determine the flow and process in POS that involve sales representatives.

|                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Profile**                           | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Default to cashier when available** | If this option is enabled, POS will automatically populate transaction lines with the current cashier’s default sales group. If a cashier doesn't have a default sales group specified, the value won't be set. A user could still manually set the sales group by using a POS button grid button.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **Prompt for sales representative**   | This option has three possible values: **No **- If this option is selected, the user won't be prompted to select a sales group. The value could still be set by using a cashier’s default Sales group or manually by using a POS button grid button. **Start of transaction** - If this option is selected, and either the **Default to cashier** option isn't enabled or the current cashier doesn't have a default sales group, the user will be prompted to select a sales group at the beginning of each transaction. Selecting a sales group from this prompt will default all subsequent lines to the selected sales group. A user could still manually set the sales group by using a POS button grid button. **For each line** - If this option is selected, and either the **Default to cashier** option isn't enabled or the current cashier doesn't have a default sales group, the user will be prompted to select a sales group after adding each line. A user could still manually set the Sales group by using a POS button grid button. |
| **Require**                           | This option is only applicable when POS is configured to prompt for a sales representative. If enabled, the user will be required to choose a sales group before continuing. Otherwise, the user will be prompted, but can cancel and continue without making a selection. After the line is added, a user with sufficient permissions could still remove the sales group from the line. “Require sales representative” is not enforced in this situation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

## Displaying the Sales representative information on the POS transactions screen
The POS transaction screen layout and contents are configurable using the screen layout designer and assigned screen layouts to stores, registers, or workers. The **Sales representative** field can be added to the Lines tab of the Receipt pane.  This will display the ID of the specified Sales group for each line on the transaction screen.

## Adding Sales representative operations to POS button grids
POS allows users to configure button grids, which are included in screen layouts to provide access to POS operations. The following POS operations can be assigned to button grid buttons that pertain to Sales representatives.

|                                           |                                                                                                                                                                                                                                                                                              |
|-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Operation**                             | **Description**                                                                                                                                                                                                                                                                              |
| Set sales representative on line          | This POS operation displays a list of eligible Sales groups (ID : Name) for the store. Selecting a Sales group from this list will set the value on the current transaction line.                                                                                                            |
| Clear sales representative on line        | This POS operation removes the current Sales group value from the current transaction line.                                                                                                                                                                                                  |
| Set sales representative on transaction   | This POS operation displays a list of eligible Sales groups (ID : Name) for the store. Selecting a Sales group from this list will set the default value on the current transaction. Any existing lines without a sales group assigned will be set, as well as any subsequently added lines. |
| Clear sales representative on transaction | This POS operation removes the current default Sales group value from the current transaction. It does not impact any lines already existing in the transaction.                                                                                                                             |

## Calculating commissions
Commission is calculated for the workers in the specified sales groups at the time of statement posting or sales order posting. The commission amount is determined based on the worker’s commission share, as defined in the sales group and the associated commission calculation settings for the customer and/or products on the transaction.



