---
title: LTL classes
description: This topic describes what less thant truckload (LTL) classes are and how to set them up in Dynamics 365 Supply Chain Management. 
author: Henrikan
ms.date: 04/05/2021
ms.topic: article
ms.search.form: WHSLTLClass
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-04-05
ms.dyn365.ops.version: 10.0.8
---

# LTL classes

[!include [banner](../includes/banner.md)]

A less than truckload (LTL) class is a freight shipping class used to classify items that can be shipped. Generally, every type of product or commodity has a National Motor Freight Classification (NMFC), which corresponds to a specific freight class number for LTL shipments. The LTL freight class represents a category of items while NMFC codes relate to specific commodities within each of the 18 freight classes.

This feature enables you to use your system to:

- Establish the LTL freight classes in use at your company.
- Assign each LTL class to an NMFC code using the **NMFC Codes** page.
- Assign an NMFC code (and thereby its associated LTL code) to each product using the **Products** page.
- Accurately assess the LTL class of each product for which an NMFC code is assigned.
- Determine packing requirements for each class by checking the international LTL standards, thus ensuring that your products will be well protected and shipped safely.
- Get accurate shipping estimates based on the LTL freight class for each of your products.

This topic describes how to create LTL classes in Dynamics 365 Supply Chain management.

## Create an LTL class

To create an LTL class, follow these steps:

1. Do one of the following:
    - Go to  **Warehouse management \> Setup \> Inventory \> LTL classes**.
    - Go to  **Transportation management \> Setup \> Transportation standards \> LTL classes**.

2. Select **New** to create a new LTL class and specify the following details:

    - **LTL class** – Enter your company's internal LTL class identifier for this commodity type. Most companies use the international standard, which would then match the value set in the **Class** field. However, if your company has it's own standard, enter that value instead.
    - **Name** – Enter a descriptive name that will help you and other users select the correct class for each NMFC code.
    - **Class** – Enter the international standard LTL class identifier (ID) for this commodity type. The code entered here must match the  official standard.

## Example of how to set up LTL classes

The following example shows how to set up two different LTL classes to use with different types of products.

1. Go to **Warehouse management \> Setup \> Inventory \> LTL classes**.
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

- [Create a bill of lading](create-bill-of-lading.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]