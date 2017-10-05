---
# required metadata

title: 
description: 
author: zalin
manager: AnnBe
ms.date: 10/05/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
# ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: zlinster
ms.search.validFrom: 2017-10-05
ms.dyn365.ops.version: Retail April 2017 update

---

# Using example screen layouts and sizes in MPOS/CPOS

This topic provides information about demo data screen layouts provided for the Microsoft Dynamics 365 for Retail point of sale (POS) experiences.

[Overview](#overview)<br>
[Anatomy of a screen layout ID](#anatomy-of-a-screen-layout-id)<br>
[Layout sizes](#layout-sizes)<br>
[Companies and brands](#companies-and-brands)<br>
[User sign in matrix](#user-sign-in-matrix)<br>
[Reference icons and images](#reference-icons-and-images)<br>

## Overview

The example screen layouts included with Dynamics 365 for Retail demo data provide content optimized for various segments of retail, store workers, and devices.  A single layout can contain several layout sizes and button grid combinations to ensure coverage as store workers transition between devices and stations.  This document will highlight the differences between these layouts, the operations they provide, and the overall experiences they deliver.

## Anatomy of a screen layout ID

To find screen layouts in Dynamics 365 for Retail, navigate to **Retail > Channel setup > POS setup >POS > Screen layouts**.

![Screen layouts form in Dynamics 365 for Retail](../media/demo-screen-layouts-fig-2-1.png)

Screen layout IDs allow a maximum of 10 characters.  We use three pieces of information to build the string for a given ID.

[Company] + [Layout version] + [Persona]

### Company

| Letter 	| Company         	|
|--------	|-----------------	|
| A      	| Adventure Works 	|
| F      	| Fabrikam         	|
| C      	| Contoso        	|

### Layout version

| Version number 	| Description                                                                                	|
|----------------	|--------------------------------------------------------------------------------------------	|
| 3              	| Base version that includes multi-screen size support for various devices and aspect ratios 	|
| 3.1            	| Base version with additional support for “Recommended products” panel                      	|

### Persona

| Abbreviation 	| Persona       	| Contents                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   	|
|--------------	|---------------	|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| CSH          	| Cashier       	| Cashier layouts include all transaction related operations such as customer orders, returns, discounts, voids, and gift cards.  Daily tasks are included for inventory management such as price check, inventory lookup and stock counts.  Basic shift management is provided for start amount, suspending shifts, and time clock.                                                                                                                                                                                         	|
| MGR          	| Store Manager 	| Store Manager layouts include all transaction operations found in cashier layouts, with the addition of tax overrides.  Daily tasks are included for inventory management such as price check, inventory lookup and stock counts.  Shift management is provided for starting, suspending and closing shifts.  Also, drawer operations for entries, removals, tender declarations, along with safe and bank drops.  Finally, manager layouts also include access to performance reports, as well as printing X & Z-reports. 	|
| STK          	| Stock Clerk   	| Stock Clerk layouts are optimized for inventory management, and include access to daily tasks for price check, inventory lookup, picking and receiving, stock count and kit disassembly.  Basic shift operations for time clock and suspending shifts are provided as well.  Though mainly intended for back office tasks, stock clerks have the same operations as cashiers for transaction screens.                                                                                                                      	|

### Example layout
F3MGR (Fabrikam + Layout version 3 + Store Manager)

![Welcome screen for the Fabrikam store manager](../media/demo-screen-layouts-fig-2-2.png)


## Layout sizes

### Full vs. Compact
A screen layout can contain configurations for both full and compact devices. This configuration allows a user to be assigned to a single screen layout that will work across various sizes and form factors within the store.

**Modern POS - Full** - Full layouts are typically best used for larger displays such as PC monitors or tablets. Users can choose which UI elements to include, determine their size and placement, and configure their detailed properties. Full layouts support both portrait and landscape configurations.

**Modern POS - Compact** - Compact layouts are typically best used for phones or small tablets. Design possibilities are limited for compact devices. Users can configure the columns and fields for the receipt and totals panes.

### Provided screen resolutions
Sizes are provided for these common resolutions.

| Layout type 	| Resolution 	| Aspect ratio 	| Target display          	|
|-------------	|------------	|--------------	|-------------------------	|
| Compact*    	| 480x853    	| 16:9         	| Phones                  	|
| Full        	| 1024x768   	| 4:3          	| Tablets                 	|
| Full*       	| 1280x720   	| 16:9         	| Tablets                 	|
| Full        	| 1366x768   	| 16:9         	| Tablets, larger screens 	|
| Full        	| 1440x960   	| 3:2          	| Tablets, larger screens 	|

*These additional layout sizes are only availalbe in Adventure Works and Fabrikam layouts

>[!TIP]<br><br>
> POS selects layout sizes automatically based on the closest size available for the current app window resolution.<br><br>
> In MPOS or CPOS, navigate to the **Settings** page and locate the **Session information** section.  In that section you will find the current Screen layout ID and layout resolution size being used.  You can also see the actual window resolution for your current application or browser frame.<br><br>
> Using that information, you can locate the source of the layout content in Dynamics 365 for Retail by navigating to **Channel setup > POS setup >POS > Screen layouts**.

![Screen layouts and resolution sizes in Dynamics 365 for Retail and POS](../media/demo-screen-layouts-fig-3-1.png)

## Companies and brands

Each fictitious company is targeted for a different retail segment, and includes product catalogs tuned for their market.  The companies include a unique visual brand to accompany their products.  Brands include accent color, dark or light theme, and accompanying photographs to provide realistic experiences.

### Company segment and visual characteristics  

| Company         	| Location 	| Segment        	| Accent 	| Theme 	|
|-----------------	|----------	|----------------	|--------	|-------	|
| Adventure Works 	| Seattle  	| Sporting Goods 	| Blue   	| Dark  	|
| Fabrikam        	| Houston  	| Fashion        	| Green  	| Light 	|
| Contoso         	| Boston   	| Electronics    	| Red    	| Dark  	|

>[!TIP]<br><br>
> Adventure Works and Fabrikam are the two flagship brands.  Contoso is available, but not all layouts have been provided.

### Adventure Works
<!-- Insert Fig 4.1 here -->

### Fabrikam
<!-- Insert Fig 4.2 here -->

### Contoso
<!-- Insert Fig 4.3 here -->


## User sign in matrix

Users have been provided to light up the various screen layouts.  Using the table below, you should be able to access any of the screens.

| Company         	| Screen layout ID 	| Persona       	| Operator ID            	|
|-----------------	|------------------	|---------------	|------------------------	|
| Adventure Works 	| A3MGR            	| Store Manager 	| 000154, 000137, 000073 	|
| Adventure Works 	| A3CSH            	| Cashier       	| 000150, 000175, 000165 	|
| Adventure Works 	| A3STK            	| Stock Clerk   	| 000155, 000181, 000152 	|
| Fabrikam        	| F3MGR            	| Store Manager 	| 000160, 000168, 000163 	|
| Fabrikam        	| F3CSH            	| Cashier       	| 000161, 000113, 000114 	|
| Fabrikam        	| F3STK            	| Stock Clerk   	| 000164, 000112, 000123 	|
| Contoso         	| C3MGR            	| Store Manager 	| 000100, 000111         	|
| Contoso         	| C3CSH            	| Cashier       	| 000110, 000120         	|
| Contoso         	| n/a              	| Stock Clerk   	| n/a                    	|


>[!TIP]<br><br>
> For best results, activate a register in the corresponding store location as the company of the persona you plan to use when signing in.  This will ensure that the visual profile and branding images align across the experience.  For example, if you are interested in seeing a Fabrikam layout for a cashier, you should activate using a register in the Houston store.

## Reference icons and images

The screen layouts, button grids, and visual profiles were created using images and icons that can be found in **Retail > Channel setup > POS setup > POS > Images**.

<!-- Insert Fig 5.1 here -->

Use the <linked> spreadsheet to locate operation icons, reference photos, swap logos, or provide new images of your own that can be referenced in custom designs.

