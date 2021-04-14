---
title: Create a new LTL class
description: This topic describes how to create a new LTL class in Dynamics 365 Supply Chain Management. 
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

# Set up an LTL class

[!include [banner](../includes/banner.md)]

A less thant truckload (LTL) class is a freight shipping class used to classify items that can be shipped. Generally, every type of product or commodity has a National Motor Freight Classification (NMFC), which corresponds to a specific freight class number for LTL shipments. The LTL freight class represents a category of items while NMFC codes relate to specific commodities within each of the 18 freight classes.

This feature can help you to:

- Establish the LTL freight classes in use at your company.
- Determine packing requirements for each class, ensuring that your products are well protected and shipped safely. <!-- KFM: How can we do this? Maybe we should mention it (for example, by providing the name of the page where we make this association). -->
- Accurately assess the LTL class of each product. <!-- KFM: assess and assign? -->
- Get accurate shipping estimates by knowing the freight class for each of your products.

This topic describes how to create LTL classes in Dynamics 365 Supply Chain management.

## Create an LTL class

To create an LTL class, follow these steps:

1. Do one of the following:
    - Go to  **Warehouse management \> Setup \> Inventory \> LTL classes**.
    - Go to  **Transportation management \> Setup \> Transportation standards \> LTL classes**.

2. Select **New** to create a new LTL class and specify the following details:

    - **LTL class** – Enter the LTL class identifier (ID) for commodity type.
    - **Name** – Enter a name for the LTL class. <!-- KFM: "Enter a descriptive name that will help you and other users select the correct class for each product"?  -->
    - **Class** – Enter the LTL class that is associated with a LTL class. <!-- KFM: The difference between **LTL class** and **Class** isn't clear. In the examples they are always the same. Might one be NMFC?  -->

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