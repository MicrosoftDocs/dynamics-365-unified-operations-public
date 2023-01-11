---
title: Less than truckload (LTL) classes
description: This article explains what less than truckload (LTL) classes are and describes how to set them up in Microsoft Dynamics 365 Supply Chain Management.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: WHSLTLClass
ms.topic: how-to
ms.date: 01/05/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Less than truckload (LTL) classes

[!include [banner](../includes/banner.md)]

A less than truckload (LTL) class is a freight shipping class that is used to classify items that can be shipped. Generally, every type of product or commodity has a National Motor Freight Classification (NMFC) code that corresponds to a specific freight class number for LTL shipments. LTL freight classes represent categories of items, whereas NMFC codes are related to specific commodities in each of the 18 freight classes.

This feature lets you use your system to perform the following tasks:

- Define the LTL freight classes that are used at your company.
- Assign each LTL class to an NMFC code on the **NMFC Codes** page. For more information, see [National Motor Freight Classification (NMFC) codes](nmfc-codes.md).
- Assign an NMFC code (and therefore its associated LTL code) to each product on the **Products** page.
- Accurately assess the LTL class of each product that an NMFC code is assigned to.
- Determine packing requirements for each LTL class by checking the international LTL standards. In this way, you ensure that your products will be well protected and safely shipped.
- Get accurate shipping estimates, based on the LTL freight class for each product.

This article describes how to create LTL classes in Microsoft Dynamics 365 Supply Chain Management.

## Create an LTL class

To create an LTL class, follow these steps.

1. Follow one of these steps:

    - Go to **Warehouse management \> Setup \> Inventory \> LTL classes**.
    - Go to **Transportation management \> Setup \> Transportation standards \> LTL classes**.

2. On the Action Pane, select **New** to create an LTL class. Then set the following fields:

    - **LTL class** – Enter your company's internal LTL class identifier (ID) for the commodity type. Most companies use the international standard. In that case, the value of this field will match the value of the **Class** field. However, if your company uses its own standard, enter a code that conforms to that standard.
    - **Name** – Enter a descriptive name that will help you and other users select the correct LTL class for each NMFC code.
    - **Class** – Enter the international standard LTL class ID for the commodity type. The code that you enter here must conform to the official standard.

## Example: Set up LTL classes

The following example shows how to set up two different LTL classes that you can use with different types of products.

1. Go to **Warehouse management \> Setup \> Inventory \> LTL classes** or **Transportation management \> Setup \> Transportation standards \> LTL classes**.
1. On the Action Pane, select **New**.
1. On the new line, set the following values:

    - **LTL class:** *92.5*
    - **Name:** *Computers, monitors, refrigerators*
    - **Class:** *92.5*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **New**.
1. On the new line, set the following values:

    - **LTL class:** *125*
    - **Name:** *Small household appliances*
    - **Class:** *125*

1. On the Action Pane, select **Save**.

## Additional resources

- [National Motor Freight Classification (NMFC) codes](nmfc-codes.md)
- [Create a bill of lading](create-bill-of-lading.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
