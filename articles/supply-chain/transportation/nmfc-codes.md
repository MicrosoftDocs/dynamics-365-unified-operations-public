---
# required metadata

title: Create a new NMFC code
description: This topic describes how to create a new NMFC code in Dynamics 365 Supply Chain Management. 
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

# NMFC codes

[!include [banner](../includes/banner.md)]

The NMFC code stands for National Motor Freight Classification and enables classifying the items that can be shipped. The NMFC code is a designation of grouping commodities that allows transport companies to evaluate goods for shipment like fitting into truck, difficulties to load, item handling, perishability etc. Commodities are grouped into one of 18 classes - ranging from 50 to 500 - based on an evaluation of four transportation characteristics: density, stowability, handling and liability. Together, these characteristics establish a commodity's transportability.

Each LTL (Less than truck load) shipping item has an NMFC code associated with it. For example, a laptop may be assigned NMFC which classes at 2.5, whereas electric cords may be assigned NMFC which classes at 65.

This feature can help workers classify the LTL shipping items through an NMFC code. Here are some examples:

- If your company include freight description on the BOL, the carrier will have an idea what the freight is. Freight is an important classification because many transportation companies base their entire business model off of the types of freight they ship.

- This classification is essential for your company for determining the cost of a given load.

- Your company can identify the profitability of an LTL logistics and transportation company.

This topic describes how to create an NMFC code in Dynamics 365 Supply Chain management.

## **Prerequisites**

Before you can create an NMFC code, you might need to follow these steps to make sure that the prerequisites are in place. 

1. Go to **Warehouse management**  \>  **Setup**  \>  **Inventory**  \>  **LTL classes**.
1. Create an LTL class. For more information, see LTL class.

## **Create an NMFC code**

To create an NMFC code, follow these steps:

1. Go to  **Warehouse management**  \>  **Setup**  \>  **Inventory**  \>  **NMFC codes**.  
   *–or–*  
   Go to  **Transportation management**  \>  **Setup**  \>  **Transportation standards**  \>  **NMFC codes**.

2. Select **New** to create a new NMFC code and specify the details as described below.

    -  **NMFC code** - Enter the NMFC code identifier (ID) for commodity type. 
    -   **Name** - Enter a name for the NMFC code. 
    -   **LTL class** - Select the LTL class that is associated with the NMFC code. LTL class number is assigned by NMFC for proper rating. 
    -   **BOL handling unit** - Define the default handling type for the shipment 

## **Example: Different NMFC codes**

The products sold by your organization may come in variants differentiated by NMFC codes as following:

1. Go to **Warehouse management**  \>  **Setup**  \>  **Inventory**  \>  **NMFC codes**.
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

## **Related tasks**

[Create a bill of landing](https://docs.microsoft.com/en-us/dynamics365/supply-chain/transportation/create-bill-of-lading)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]