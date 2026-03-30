---
title: Track commissions in the point of sale (POS) by using sales groups
description: Learn how to track commissions using sales groups in Microsoft Dynamics 365 Commerce point of sale (POS).
author: josaw1
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2016-11-30
ms.assetid: 7cd68ecc-cc09-48ab-8cb8-48d5c304effa
ms.custom: 
  - bap-template
---

# Track commissions in the point of sale (POS) by using sales groups

[!include [banner](includes/banner.md)]

This article describes how to track commissions by using sales groups in Microsoft Dynamics 365 Commerce point of sale (POS).

It's a common retail practice to track sales by the associate who worked with the customer by providing assistance, up-selling, cross-selling, and processing the transaction.

Tracking sales by sales representative is a measure of the associate's selling abilities, while tracking sales by cashier is a measure of speed and efficiency. Retailers often use sales tracked by sales representative to calculate commissions or other incentives.

## Configure a worker as a sales representative in POS

When you add a worker to a sales group, they become eligible for commission and can be identified as a sales representative in the system. A worker who isn't in a sales group isn't eligible for commission and isn't listed as a sales representative in the point of sale (POS) application. In POS, the list of sales representatives comes from all sales groups that contain at least one worker assigned to the store. The list shows as a combination of sales group ID and name (ID = name). Assign a default sales group to workers to support scenarios where the retailer chooses to set the sales representative on POS lines automatically. Users can select from any sales group that the worker is a member of.

## Functionality profile settings

Numerous functionality profile settings for a store determine the flow and process in POS that involve sales representatives.

| Profile | Description |
|---------|-------------|
| Default to cashier when available | If you enable this option, POS automatically populates transaction lines with the current cashier's default sales group. If a cashier doesn't have a default sales group specified, the value isn't set. A user can still manually set the sales group by using a POS button grid button. |
| Prompt for sales representative | This option has three possible values: <ul><li>**No** – If you select this option, the user isn't prompted to select a sales group. The value could still be set by using a cashier's default sales group or manually by using a POS button grid button.</li><li>**Start of transaction** – If you select this option, and either the **Default to cashier** option isn't enabled or the current cashier doesn't have a default sales group, the user is prompted to select a sales group at the beginning of each transaction. Selecting a sales group from this prompt defaults all subsequent lines to the selected sales group. A user can still manually set the sales group by using a POS button grid button.</li><li>**For each line** – If you select this option, and either the **Default to cashier** option isn't enabled or the current cashier doesn't have a default sales group, the user is prompted to select a sales group after adding each line. A user can still manually set the sales group by using a POS button grid button.</li></ul> |
| Require | This option is only applicable when POS is configured to prompt for a sales representative. If enabled, the user is required to choose a sales group before continuing. Otherwise, the user is prompted, but can cancel and continue without making a selection. After the line is added, a user with sufficient permissions can still remove the sales group from the line. "Require sales representative" isn't enforced in this situation. |

## Display the sales representative information on the POS transactions screen

You can configure the POS transaction screen layout and contents by using the screen layout designer. You can assign screen layouts to stores, registers, or workers. Add the **Sales representative** field to the **Lines** tab of the **Receipt** pane. This action displays the ID of the specified sales group for each line on the transaction screen.

## Add sales representative operations to POS button grids

POS users can configure button grids. Include these grids in screen layouts to provide access to POS operations. Assign the following POS operations to button grid buttons that pertain to sales representatives.

| Operation | Description |
|-----------|-------------|
| Set sales representative on line | This POS operation displays a list of eligible sales groups (ID : Name) for the store. Selecting a sales group from this list sets the value on the current transaction line. |
| Clear sales representative on line | This POS operation removes the current sales group value from the current transaction line. |
| Set sales representative on transaction | This POS operation displays a list of eligible sales groups (ID : Name) for the store. Selecting a sales group from this list sets the default value on the current transaction. Any existing lines without a sales group assigned are set, along with any subsequently added lines. |
| Clear sales representative on transaction | This POS operation removes the current default sales group value from the current transaction. It doesn't affect any lines already existing in the transaction. |

## Calculate commissions

Calculate commission for the workers in the specified sales groups at the time of statement posting or sales order posting. Determine the commission amount based on the worker's commission share, as defined in the sales group and the associated commission calculation settings for the customer and products on the transaction.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
