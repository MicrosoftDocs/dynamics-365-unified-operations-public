---
# required metadata

title: Import or manually create postal codes
description: This article explains how to import and manually create Dutch postal codes in the correct format. This topic includes information about feature that was added for Microsoft Dynamics 365 for Operations. 
author: ShylaThompson
manager: AnnBe
ms.date: 2016-01-21 17 - 15 - 40
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: LogisticsAddressSetup
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 29901
ms.assetid: 0c9cbc5f-88ae-4ed2-8331-13ecea029f79
ms.search.region: Belgium, Netherlands, Sweden
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Import or manually create postal codes

This article explains how to import and manually create Dutch postal codes in the correct format. This topic includes information about feature that was added for Microsoft Dynamics 365 for Operations. 

The import process lets you update the ZIP/postal codes for a specific country/region. You can also create postal codes manually.

## Import ZIP/postal codes
You can use the **Import ZIP/postal codes** page to import new postal codes into Microsoft Dynamics 365 for Operations. When you import the codes, the existing ZIP or postal codes are replaced with the new format, and any new codes are added.

For some countries, you must use the Data management framework to import codes, while for other countries only a upload file is required. Belgium, Netherlands, and Sweden require a file to upload.

> [!NOTE]
> -   For Belgium, the official webpage from the Belgian Post provides an official list of the postcodes and the corresponding city names. The import supports html file format.
> -   For Netherlands, a third-party organization provides the file that contains postal codes. After the import is completed, all postal codes will appear in the format (NNNN AA).
> -   For Sweden, Postnummerservice.se provides two types of files: Swedish postal codes and Swedish addresses. The import supports text file format for both types.


## Create ZIP/postal codes manually
Instead of importing codes, you can use the **Address setup** page to manually add new ZIP/postal codes.
