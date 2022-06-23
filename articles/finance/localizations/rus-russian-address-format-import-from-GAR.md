---
# required metadata
title: Russian address formats
description: This topic provides information about how to import addresses in the GAR format.
author: epodkolz
ms.date: 23/06/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 
ms.dyn365.ops.version: Version 10.0.29

---

# Import from State Address Register (GAR) 
[!include [banner](../includes/banner.md)]

Starting from the 10.0.29 update, import of addresses is available in a new State Address Register (GAR) format – Import from GAR.

This topic provides information about how to import addresses in the GAR format.

The GAR format that is provided by the Federal Tax Service (FTS) contains information about addresses in administrative-territorial and municipal divisions. Current GAR functionality provides import of addresses in municipal division only.
In addition to the FIAS functionality that provides import of States, Counties, Cities, Districts, Streets, group of houses, group of flats, ZIP/Postal codes, and land plots, the GAR functionality provides import of Urban/Rural settlements and Localities, that are the components of the municipal division.
Parking lots (spaces), Room numbers and Rooms numbers within the premises are not supported in the GAR functionality.

The following table provides information about GAR levels and corresponding tabs/tables on the **Address setup** page.

| Level | Name in GAR | Tab on the Address setup page | Table |
|---|---|---|---|
| 1 | Subject of the Russian Federation | State/Province | LOGISTICSADDRESSSTATE |
| 2 | Administrative area | City （Address level - City）|LOGISTICSADDRESSCity |
| 3 | Municipal district | County | LOGISTICSADDRESSCOUNTY |

| 4 |	Rural / Urban Settlement | City （Address level - Rural / Urban Settlement）|	LOGISTICSADDRESSCITY |
| 5 |	City | City （Address level - City) |	LOGISTICSADDRESSCity |
| 6 |	Locality	|City （Address level - Locality) | LOGISTICSADDRESSCity
| 7	| Planning structure element |	District	| LOGISTICSADDRESSDISTRICT |
| 8 |	Road network element	| Street	| LOGISTICSADDRESSSTREET_RU |
| 9	| Steads |	Land plots	| LOGISTICSADDRESSHOUSENUMBER_RU |
| 10 |	House	| Group of houses |	LOGISTICSADDRESSHOUSENUMBER_RU |
| 11 |	Apartments and Rooms |	Group of flats	| LOGISTICSADDRESSFLATNUMBER_RU |

## Import from GAR 

### Enable Import from GAR feature
1. Go to **Workspaces** > **Feature management**.
2. In the feature list, select and enable the following feature: **(Russia) Import addresses from the State Address Register (GAR)**.

After enabling the feature, the Import from FIAS functionality won’t be available. The new menu item Import from GAR will be available instead.

### Import ER configurations
The GAR import feature utilizes the **Electronic Reporting (ER) functionality**. You need to import the following ER configurations:
1.	GAR address import ADDR_OBJ(RU)
2.	GAR address import APARTMENTS(RU)
3.	GAR address import HOUSES(RU)
4.	GAR address import ROOMS(RU)
5.	GAR address import STEADS(RU)
6.	GAR hierarchy import MUN_HIERARCHY(RU)
7.	GAR metadata import ADDHOUSE(RU)
8.	GAR metadata import ADDR_OBJ(RU)
9.	GAR metadata import APARTMENT(RU)
10.	GAR metadata import HOUSE(RU)
11.	GAR metadata import OPERATION(RU)
12.	GAR metadata import ROOM(RU)
13.	GAR parameters import ADDR_OBJ(RU)
14.	GAR parameters import APARTMENTS(RU)
15.	GAR parameters import HOUSES(RU)
16.	GAR parameters import ROOMS(RU)
17.	GAR parameters import STEADS(RU)

For more information on importing ER configurations, see **Download ER configurations** from the Global repository of Configuration service - Finance & Operations | Dynamics 365 | Microsoft Docs.

### GAR import

1.	Download the database from https://fias.nalog.ru/Updates
2.	Go to **Organization administration** > **Global address book** > **Import from GAR**.
3.	Select **Import from GAR** to open the **Import from GAR** dialog box.
4.	On the **Parameters** FastTab, select **Browse** to select the zip archive.
5.	Set the **Full import** option to **Yes**, if you are importing a full database. If you are importing a delta file, set the **Full import** option to **No**.
6.	If you intend to import houses and steads, set the **Import Houses and Steads** option to **Yes**.
7.	If you intend to import rooms, set the **Import Rooms and Apartments** option to **Yes**.
8.	Select **OK** to start the import.














