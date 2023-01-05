---
title: National Motor Freight Classification (NMFC) codes
description: This article describes how to work with National Motor Freight Classification (NMFC) codes in Microsoft Dynamics 365 Supply Chain Management
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: WHSNMFC
ms.topic: how-to
ms.date: 01/05/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# National Motor Freight Classification (NMFC) codes

[!include [banner](../includes/banner.md)]

National Motor Freight Classification (NMFC) codes help you classify items that can be shipped. The NMFC code is a designation that is used to group commodities. It enables transport companies to evaluate goods for shipment by classifying items based on considerations such as truck fit, loading issues, handling issues, and perishability. Commodities are grouped into one of 18 freight classes by using a range of numbers from 50 to 500. The class that a commodity is grouped into is based on an evaluation of four transportation characteristics: density, stowability, handling, and liability. Together, these characteristics establish the commodity's transportability.

An NMFC code is associated with every less than truckload (LTL) shipping item. For example, a laptop might be assigned an NMFC that is classed at 2.5, whereas electrical cords might be assigned an NMFC that is classed at 65.

This feature can help workers use NMFC codes to classify LTL shipping items. Here are some examples:

- If your company includes a freight description on the bill of lading (BOL), the carrier will have some idea what the freight is. Freight is an important classification because many transportation companies base their whole business model on the types of freight that they ship.
- This classification might be essential to your company because it's used to determine the cost of a given load.
- Your company can identify the profitability of an LTL logistics and transportation company.

This article describes how to work with NMFC codes in Microsoft Dynamics 365 Supply Chain Management.

## Prerequisites

Before you can create NMFC codes, you must set up all the LTL freight classes that must be mapped to them. LTL freight classes represent categories of items, whereas NMFC codes are related to specific commodities in each of the 18 freight classes. For more information about how to work with LTL classes, see [Less than truckload (LTL) classes](ltl-class.md).

## Create an NMFC code

To create an NMFC code, follow these steps.

1. Follow one of these steps:

    - Go to **Warehouse management \> Setup \> Inventory \> NMFC codes**.
    - Go to **Transportation management \> Setup \> Transportation standards \> NMFC codes**.

1. Select **New** to create an NMFC code. Then set the following fields:

    - **NMFC code** – Enter the NMFC code for the commodity type.
    - **Name** – Enter a name for the NMFC code.
    - **LTL class** – Select the LTL class that is associated with the NMFC code.
    - **BOL handling unit** – Define the default handling type for the shipment.

## Example: Set up NMFC codes

The following example shows how to set up two different NMFC codes that can be used with different products.

1. Follow one of these steps:

    - Go to **Warehouse management \> Setup \> Inventory \> NMFC codes**.
    - Go to **Transportation management \> Setup \> Transportation standards \> NMFC codes**.

1. On the Action Pane, select **New**.
1. On the new line, set the following values:

    - **NMFC code:** *92.5*
    - **Name:** *Computers*
    - **LTL class:** *92.5*
    - **BOL handling unit:** *Unit*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **New**.
1. On the new line, set the following values:

    - **NMFC code:** *125*
    - **Name:** *Phones*
    - **LTL class:** *125*
    - **BOL handling unit:** *Unit*

1. On the Action Pane, select **Save**.

## Additional resources

- [Less than truckload (LTL) classes](ltl-class.md)
- [Create a bill of landing](create-bill-of-lading.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
