--- 
# required metadata 
 
title: Set up manual packing (February 2016 & May 2016)
description: The packing process allows you to validate and pack products into containers. 
author: Mirzaab
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSLocationProfile, WHSParameters, WHSContainerType, WHSPackProfile, WHSCloseContainerProfile, InventLocationIdLookup, UnitOfMeasureLookup
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up manual packing (February 2016 & May 2016)

[!include [banner](../../includes/banner.md)]

The packing process allows you to validate and pack products into containers. In this process, warehouse workers pick products from the storage locations and move them to a packing station where they check the item quantities and types, and assign them to appropriate containers. When a container is fully packed, they can close it and move it to the outbound docks, and the products are ready to ship. This procedure uses the USMF demo company. This procedure is for the February 2016 & May 2016 versions of Dynamics 365 for Operations only.


## Set up location profiles
1. Go to Warehouse management > Setup > Warehouse > Location profiles.
2. Click New.
    * The location profile is used for packing stations and contains information and rules for a location.  
3. In the Location profile ID field, type a value.
4. In the Name field, type a value.
5. In the Location format field, enter or select a value.
6. In the Location type field, enter or select a value.
7. Select Yes in the Allow mixed items field.
8. Select Yes in the Allow mixed  inventory statuses field.
9. Select Yes in the Override rules for batch days field.
10. Close the page.

## Set up warehouse management parameters 
1. Go to Warehouse management > Setup > Warehouse management parameters.
2. Click the Packing tab.
3. In the Profile ID for packing location field, enter or select a value.
    * Select the location profile that you want to use for packing.  
4. Close the page.

## Set up container types
1. Go to Warehouse management > Setup > Containers > Container types.
2. Click New.
    * You can define the types of containers to use. You can specify the physical dimensions of the container, including tare weight, maximum weight, maximum volume, length, width, and weight.  The Attributes are customized fields that allow you to add extra dimensions on the container type.     
3. In the Container type code field, type a value.
4. In the Description field, type a value.
5. In the Tare weight field, enter a number.
6. In the Maximum weight field, enter a number.
7. In the Volume field, enter a number.
8. In the Length field, enter a number.
9. In the Width field, enter a number.
10. In the Height field, enter a number.
11. Click Save.
12. Close the page.

## Set up packing profiles
1. Go to Warehouse management > Setup > Packing > Packing profiles.
2. Click New.
3. In the Packing profile ID field, type a value.
4. In the Description field, type a value.
5. In the Container closing profile ID field, enter or select a value.
    * A container closing profile ID is optional and is the default close container profile for this packing profile.  
6. In the Container ID mode field, select an option.
    * This option determines whether a container ID will be automatically generated when a container is created or if a container ID will be created manually.  
7. In the Container type field, enter or select a value.
    * The container type will be used by default when a new container is created.  
8. Select the Autocreate container at container close check box.
9. Click Save.
10. Close the page.

## Set up container closing profiles
1. Go to Warehouse management > Setup > Containers > Container closing profiles.
    * Container closing profiles define what happens when a container is closed. You can set up multiple close container profiles.       
2. Click New.
3. In the Container closing profile ID field, type a value.
4. In the Description field, type a value.
5. In the Manifest at field, select an option.
    * Specify whether manifesting will occur when closing containers or when confirming the shipment. Note that manifesting requires Transportation management. Manifesting must be implemented in the transportation engines in order for it work.  
6. In the Warehouse field, enter or select a value.
7. In the Default location for final shipment field, enter or select a value.
    * This will be location to which products will be moved after the containers are closed. This location must have a location profile defined on Warehouse parameters.  
8. In the Weight unit field, enter or select a value.
9. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]