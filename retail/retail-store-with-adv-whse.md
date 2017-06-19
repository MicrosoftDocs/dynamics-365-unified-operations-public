---
# required metadata

title: Retail store Advanced Warehouse setup
description: This topic how to configure a warehouse to work as a retail warehouse as well as an advanced warehouse.
author: rubencdelgado
manager: AnnBe
ms.date: 06/17/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: AX 7.0.0, Operations, Core, Retail
# ms.tgt_pltfrm: 
ms.custom: 
s.assetid:  
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.2

---

# Retail store Advanced Warehouse setup

[!include[banner](includes/banner.md)]

Warehouses that map to retail stores may also be set up as advanced warehouses. In order for a warehouse to serve both functions, the
configuration to serve as retail and advanced warehouse must be done at the time of warehouse creation. 

Following are the steps required for a warehouse to function as an advanced warehouse while also serving as a warehouse for a retail store: 

**Create an Advanced warehouse:**    
Go to **Warehouse management > Setup > Warehouse > Warehouses**  
Create a new warehouseImmediately after specifying **Warehouse ID**, navigate to **Warehouse** and set ** “Use warehouse management process” ** to **‘Yes’**.  
Set the ** “Default inventory status ID”** to **‘Available’**.  
Under **Retail**, keep ** “Store” ** = **‘No’**.

**Create a location profile:**  
Go to **Warehouse management > Setup > Warehouse > Location profiles**  
Create a new location profile for use in the retail store.  
Set ** “Allow mixed items” ** = ** ‘Yes’**.  
Keep ** “Use license plate tracking” ** = ** ‘No’**.

**Create a location:**  
Go to **Warehouse management > Setup > Warehouse > Locations**  
Create a new location.  
For ** “Location Profile ID” **, specify the previously created location profile.  
For ** “Use warehouse” **, specify the warehouse created above. 

**Set up warehouse as retail store:**  
Go to **Warehouse management > Setup > Warehouse > Warehouses**  
Select the warehouse created above.  
Under **Retail**, set ** “Store” ** = ** ‘Yes’**.  
Set default a **Default return location**.  
Set a ** “Default location” **.

  > [!NOTE] Default locations are used
    when operations are performed at the point of sale which should not require
    cashier to set location. For example, retail sales have a use the ‘Default
    location’ because the cashier does not know from which location the product was
    retrieved by the shopper. Return locations are also specified so products can
    be accounted for separately before it is determined if the can be resold or
    should be otherwise disposed. 

    Default locations should be set up according to instructions provided in ** ‘Create a location’**.

**Map a retail store to the warehouse:**  
Go to **Retail > Channels > Retail stores> All retail stores**  
Select a store by clicking on the **Retail Channel ID**.  
Under ** “Warehouse” ** click on the dropdown and select the warehouse created above and save.  
Go to **Retail > Retail IT > Distribution schedule** and select job ID **1070**.  
Click ** ‘Run now’** to sync the changes to the channel database. 
   
See also
--------

[Warehouse confirguration](warehouse-configuration.md)
