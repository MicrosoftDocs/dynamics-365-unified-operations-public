---
# required metadata

title: Create a new LTL class
description: This topic describes how to create a new LTL class in Dynamics 365 Supply Chain Management. 
author: GalynaFedorova
ms.date: 04/05/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: v-gfedorova
ms.search.validFrom: 2021-04-05
ms.dyn365.ops.version: 10.0.8

---
# **Set up an LTL class**

[!include [banner](../includes/banner.md)]

The LTL class stands for less-than-truckload freight shipping class and enables classifying the items that can be shipped. Generally, every type of product or commodity has a National Motor Freight Classification (NMFC), which corresponds to a specific freight class number for LTL shipments. LTL freight class represents a category of items while NMFC codes relate to specific commodities within each of the 18 freight classes.

This feature can help workers determine a commodity’s freight class. Here are some examples:
-	Company can establish the commodity’s freight classes. It allows you to determine its packing requirements, ensuring that your goods are well protected and shipped safely.
-	Knowing the freight class of your goods will help you get an accurate shipping estimate. 
-	Company will be able to accurately assess a commodity’s class.

This topic describes how to create an LTL class in Dynamics 365 Supply Chain management.

## **Create an LTL class**

To create an LTL class, follow these steps:

1. Go to  **Warehouse management**  \>  **Setup**  \>  **Inventory**  \>  **LTL classes**.

   *–or–*

   Go to  **Transportation management**  \>  **Setup**  \>  **Transportation standards**  \>  **LTL classes**.

2. Select **New** to create a new LTL class and specify the details as described in the following table.

    - **LTL class** - Enter the LTL class identifier (ID) for commodity type. 
    - **Name** - Enter a name for the LTL class. 
    - **LTL class** - Enter the LTL class that is associated with a LTL class. 

## **Example: Different LTL classes**

The products sold by your organization may come in variants differentiated by LTL classes as following:

1. Go to **Warehouse management**  \>  **Setup**  \>  **Inventory**  \>  **LTL classes**.
1. On the Action Pane, select **New**.
1. On the new line, set the following values:

    - **LTL class:** *92.5*
    - **Name:** *Computers, monitors, refrigerators*
    - **LTL class:** *92.5*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **New**.
1. On the new line, set the following values:

     - **LTL class:** *125*
    - **Name:** *Small household appliances*
    - **LTL class:** *125*

1. On the Action Pane, select **Save**.

## **Related tasks**

[Create a bill of landing](https://docs.microsoft.com/en-us/dynamics365/supply-chain/transportation/create-bill-of-lading)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]