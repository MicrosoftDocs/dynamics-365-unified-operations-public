---
title: Track commissions in the point of sale (POS) by using sales groups
description: This article describes how to track commissions in the point of sale (POS) by using sales groups in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 08/02/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anvenkat
ms.search.validFrom: 2016-11-30
ms.assetid: 7cd68ecc-cc09-48ab-8cb8-48d5c304effa
ms.custom: 
  - bap-template
---

# Track commissions in the point of sale (POS) by using sales groups

[!include [banner](includes/banner.md)]

This article describes how to track commissions in the point of sale (POS) by using sales groups in Microsoft Dynamics 365 Commerce.

It's a common retail practice to track sales by the associate who worked with the customer by—providing assistance, up-selling, cross-selling, and processing the transaction.

Tracking sales by sales representative is a measure of the associates selling abilities, while sales by cashier is a measure of speed and efficiency. Sales tracked by sales representative are also often used to calculate commissions or other incentives.

## Configuring a worker to be a sales representative in POS

When a worker is added to a sales group, they become eligible for commission and can be identified as a sales representative in the system. A worker who isn't in a sales group isn't eligible for commission and isn't listed as a sales representative in the point of sale (POS) application. In POS, the list of sales representatives is derived from all sales groups that contain at least one worker assigned to the store. The list is shown in POS as a combination of sales group ID and name (ID = name). A default sales group can be assigned to workers to support scenarios where the retailer chooses to set the sales representative on POS lines automatically. Users can select from any sales group that the worker is a member of.

## Functionality profile settings

There are numerous functionality profile settings for a store that determine the flow and process in POS that involve sales representatives.

<table>
<thead>
<tr>
<th>Profile</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Default to cashier when available</td>
<td>If this option is enabled, POS automatically populates transaction lines with the current cashier's default sales group. If a cashier doesn't have a default sales group specified, the value isn't be set. A user can still manually set the sales group by using a POS button grid button.</td>
</tr>
<tr>
<td>Prompt for sales representative</td>
<td>This option has three possible values:
<ul>
<li><strong>No</strong> – If this option is selected, the user isn't be prompted to select a sales group. The value could still be set by using a cashier's default sales group or manually by using a POS button grid button.</li>
<li><strong>Start of transaction</strong> – If this option is selected, and either the <strong>Default to cashier</strong> option isn't enabled or the current cashier doesn't have a default sales group, the user is prompted to select a sales group at the beginning of each transaction. Selecting a sales group from this prompt defaults all subsequent lines to the selected sales group. A user ccan still manually set the sales group by using a POS button grid button.</li>
<li><strong>For each line</strong> – If this option is selected, and either the <strong>Default to cashier</strong> option isn't enabled or the current cashier doesn't have a default sales group, the user is prompted to select a sales group after adding each line. A user can still manually set the sales group by using a POS button grid button.</li>
</ul>
</td>
</tr>
<tr>
<td>Require</td>
<td>This option is only applicable when POS is configured to prompt for a sales representative. If enabled, the user is required to choose a sales group before continuing. Otherwise, the user is prompted, but can cancel and continue without making a selection. After the line is added, a user with sufficient permissions can still remove the sales group from the line. "Require sales representative" isn't enforced in this situation.</td>
</tr>
</tbody>
</table>

## Displaying the Sales representative information on the POS transactions screen

The POS transaction screen layout and contents are configurable using the screen layout designer and assigned screen layouts to stores, registers, or workers. The **Sales representative** field can be added to the **Lines** tab of the **Receipt** pane. This action displays the ID of the specified sales group for each line on the transaction screen.

## Adding Sales representative operations to POS button grids

POS allows users to configure button grids, which are included in screen layouts to provide access to POS operations. The following POS operations can be assigned to button grid buttons that pertain to Sales representatives.

| Operation                                 | Description |
|-------------------------------------------|-------------|
| Set sales representative on line          | This POS operation displays a list of eligible sales groups (ID : Name) for the store. Selecting a sales group from this list sets the value on the current transaction line. |
| Clear sales representative on line        | This POS operation removes the current sales group value from the current transaction line. |
| Set sales representative on transaction   | This POS operation displays a list of eligible sales groups (ID : Name) for the store. Selecting a sales group from this list sets the default value on the current transaction. Any existing lines without a sales group assigned are set, along with any subsequently added lines. |
| Clear sales representative on transaction | This POS operation removes the current default sales group value from the current transaction. It doesn't impact any lines already existing in the transaction. |

## Calculating commissions

Commission is calculated for the workers in the specified sales groups at the time of statement posting or sales order posting. The commission amount is determined based on the worker's commission share, as defined in the sales group and the associated commission calculation settings for the customer and/or products on the transaction.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
