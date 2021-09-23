---
# required metadata

title: Address setup
description: This topic describes setting up address formats for the global address book.
author: jaredha
ms.date: 09/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DirPartyTable, DirPartyTableRoles
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jaredha
ms.search.validFrom: 2021-09-23
ms.dyn365.ops.version: AX 7.0.0

---

# Address setup

[!include [banner](../includes/banner.md)]

Global regions in which you organization operates may have different address format types. Your organization must have the flexibility to adjust to the appropriate address format when displaying a postal address for each region. You can use the **Address setup** form to set up the postal address formats required for your organization.

## Define address parameters

## Set up address formats
Use this section of the form to enter and set up address component information and formatting. As you enter address information for a selected address type, the **Preview** field in the upper-right pane displays how the address will appear.

1. In the **Address setup** form, select **Address format** in the left pane.
2. In the action ribbon of the pane, select **New** to add a new address format type.
3. Enter the address format type name and a brief description. For example, you might enter "NO" in the **Address format** field and enter "Norway" in the **Description** field.
4. In the lower pane, click **New** to configure a new address component for the address format type that is selected in the upper pane.
5. In the **Address application object** field, select the first object that must appear when an address for this format is displayed. For example, **Street**.
6. In the **Separator** field, enter the character that should separate this object from the next object when the address is displayed. For example, a comma.
7. Select the check boxes to indicate the following:
  - **New line** - Display this object on a new line.
  - **Data entry only** - Display this object only when entering the address. If this check box is selected, the object will not be displayed when the address is printed.
  - **Not active** - Do not use this object in an address for the selected format type.
  - **Expand** - Display the name of the country/region, state, or county instead of the assigned code.
  - **Special** - Indicates that the field countains the same separator characters.
