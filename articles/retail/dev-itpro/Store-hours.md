---
# required metadata

title: Create and update store hours
description: This topic describes how to create and update store hours in Retail HQ.
author: josaw1
manager: AnnBe
ms.date: 7/30/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application users
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rapraj
ms.search.validFrom: 2019-07-30
ms.dyn365.ops.version: Retail 10.0.1 update

---



# Create and update store hours

[!include [banner](../../includes/banner.md)]

## Overview
Retailers can create, maintain, and manage the store hours for different stores across geographies from a single point. Retailers can showcase the store hours in point of sale (POS) terminals, letting the cashiers share store hours to customers and assist shoppers while looking for inventory in different stores. Customers also can see the new store hours printed on their receipts in case they wish to return to the store. 

Multiple store hours can be configured across different channels, such as brick and mortar store, call center, mobile, and e-Commerce.

If a customer has a pickup order for a different store, the cashier can select dates when the pickup will be available in that store. The store lookup will provide a reference to the dates and store times. The cashier will choose a date and location, and can print a pickup receipt with the store hours. 

## Configure store hours
This functionality is available in Dynamics 365 for Retail versions 8.1.2 and later.

1. To configure store hours, go to **Retail** > **Channel Setup** > **Store hours**.
2. Create a new **Store hours template** or choose an existing one. To create a new template, click **New**. To use an existing template, choose the template from the left pane.  

![Store Hours Template](../dev-itpro/media/Storehours1.png "Store hours template")  

3. Next, define the period of the date range, the store hours, and holidays (if anneeded).
  - If store hours are constant and do not change, select **Never ends** in the **End date** field. 
  - If the store hours are for a specific month/week/day, set the appropriate dates in the **Start Date** and **End date** fields.
  
  > [!NOTE]
  > You can create mutliple templates with overlapping start and end dates, for example, to define store hours for stores in different time-zones. 

4. Next, you need to associate the **Store hours template** to the stores. Use the **Organization heirarchy** table to select the stores, regions, and organizations that you want the template to be associated with. 
  - Each store can have only one store hours template associated to it. 
  - Use the arrow keys to select the stores, region, organization. 
The calendar will now be available to the store or store groups, and will become visible in the point of sale (POS) for reference.

![Save Store Hours Template](../dev-itpro/media/Storehours2.png "Save Store hours template") 

5. Run the **1070** and **1090** jobs in **Distribution Schedule** for the store hours to be available to POS.


## Add store hours to printed receipts

To add store hours to the printed POS receipts, do the following.
1. Open **Receipt Designer**.
1. Select **Footer** tab in the receipt template.
1. Drag the **Store hours** tab from the left navigation pane to the bottom of the receipt template in the footer. 
1. If you need to change the label, edit the default label names in the **Store hours** tab of the receipt designer. 
1. Save the receipt and exit **Receipt designer**.
1. Run the **1070** and **1090** jobs in **Distribution Schedule**.
1. Log into POS. 
1. Complete a sale and select printed receipt.

POS receipts will now include store hours. If any holidays were included in the template, they will also be visible on the receipt.


![Receipt Template](../dev-itpro/media/Storehours3.png "Receipt template") 

