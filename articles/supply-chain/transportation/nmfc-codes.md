---
title: NMFC codes
description: This topic describes how to work with NMFC codes in Dynamics 365 Supply Chain Management
author: Henrikan
ms.date: 04/22/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-04-22
ms.dyn365.ops.version: 10.0.8
---

# NMFC codes

[!include [banner](../includes/banner.md)]

National Motor Freight Classification (NMFC) codes help you to classify items that can be shipped. The NMFC code is a designation for grouping commodities that allows transport companies to evaluate goods for shipment, classifying items according to truck fit, loading issues, handling issues, perishability, and so on. Commodities are grouped into one of 18 classes&mdash;using numbers ranging from 50 to 500&mdash;based on an evaluation of four transportation characteristics: density, stowability, handling, and liability. Together, these characteristics establish a commodity's transportability.

Each LTL (Less than truck load) shipping item has an NMFC code associated with it. For example, a laptop may be assigned an NMFC that classes at 2.5, whereas electric cords may be assigned an NMFC that classes at 65.

This feature can help workers classify the LTL shipping items using NMFC codes. Here are some examples:

- If your company includes  freight description on the bill of lading (BOL), the carrier will have an idea what the freight is. Freight is an important classification because many transportation companies base their entire business model on the types of freight they ship.
- This classification may be essential to your company for determining the cost of a given load.
- Your company can identify the profitability of an LTL logistics and transportation company.

This topic describes how to work with NMFC codes in Dynamics 365 Supply Chain management.

## Prerequisites

Before you can create NMFC codes, you must set up all of the LTL classes required to map to them. LTL freight classes represent categories of items, whereas NMFC codes are related to specific commodities in each of the 18 freight classes. For details about how to work with LTL classes, see [Less than truckload (LTL) classes](ltl-class.md).

## Create an NMFC code

To create an NMFC code, follow these steps:

1. Follow one of these steps:
    - Go to  **Warehouse management** \> **Setup** \> **Inventory** \> **NMFC codes**.  
    - Go to  **Transportation management** \> **Setup** \> **Transportation standards** \> **NMFC codes**.

2. Select **New** to create a new NMFC code. Then set the following fields:

    - **NMFC code** – Enter the NMFC code identifier (ID) for commodity type.
    - **Name** – Enter a name for the NMFC code.
    - **LTL class** – Select the LTL class that is associated with the NMFC code.
    - **BOL handling unit** – Define the default handling type for the shipment.

## Example: Set up NMFC codes

The following example shows how to set up two different NMFC codes for use with different products.

1. Go to **Warehouse management** \> **Setup** \> **Inventory** \> **NMFC codes**.
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