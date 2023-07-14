---
# required metadata

title: Import or manually create postal codes
description: This article explains how to import and manually create postal codes in the correct format. 
author: EvgenyPopovMBS
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LogisticsAddressSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.search.region: Belgium, Netherlands, Sweden
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Import or manually create postal codes

[!include [banner](../includes/banner.md)]

This article explains how to import and manually create postal codes in the correct format. 

The import process lets you update the ZIP/postal codes for a specific country/region. You can also create postal codes manually.

## Import ZIP/postal codes
You can use the **Import ZIP/postal codes** page to import new postal codes into Dynamics 365 Finance. When you import the codes, the existing ZIP or postal codes are replaced with the new format, and any new codes are added.

For some countries/regions, you must use the Data management framework to import codes, while for other countries/regions only an upload file is required. Belgium, Netherlands, and Sweden require a file to upload.

> [!NOTE]
> -   For Belgium, the official webpage from the Belgian Post provides an official list of the postcodes and the corresponding city names. The import supports html file format.
> -   For Netherlands, a third-party organization provides the file that contains postal codes. After the import is completed, all postal codes will appear in the format (NNNN AA).
> -   For Sweden, Postnummerservice.se provides two types of files: Swedish postal codes and Swedish addresses. The import supports text file format for both types.


## Create ZIP/postal codes manually
Instead of importing codes, you can use the **Address setup** page to manually add new ZIP/postal codes.




[!INCLUDE[footer-include](../../includes/footer-banner.md)]