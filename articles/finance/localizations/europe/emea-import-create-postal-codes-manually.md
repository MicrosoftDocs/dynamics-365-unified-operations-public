---
title: Import or manually create postal codes
description: Learn how to import and manually create postal codes in the correct format. The import process lets you update the ZIP/postal codes for a specific country/region.
author: AdamTrukawka
ms.author: anisagrawal
ms.topic: how-to
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Belgium, Netherlands, Sweden
ms.search.validFrom: 2016-11-30
ms.search.form: LogisticsAddressSetup
ms.custom: 
  - bap-template
---

# Import or manually create postal codes

[!include [banner](../../includes/banner.md)]

This article explains how to import and manually create postal codes in the correct format.

The import process lets you update the ZIP or postal codes for a specific country or region. You can also create postal codes manually.

## Import ZIP/postal codes

Use the **Import ZIP/postal codes** page to import new postal codes into Dynamics 365 Finance. When you import the codes, the process replaces the existing ZIP or postal codes with the new format and adds any new codes.

For some countries or regions, you must use the Data management framework to import codes. For other countries or regions, you only need an upload file. Belgium, Netherlands, and Sweden require a file to upload.

> [!NOTE]
> - For Belgium, the official webpage from the Belgian Post provides an official list of the postcodes and the corresponding city names. The import supports HTML file format.
> - For Netherlands, a partner organization provides the file that contains postal codes. After the import is completed, all postal codes appear in the format (NNNN AA).
> - For Sweden, Postnummerservice.se provides two types of files: Swedish postal codes and Swedish addresses. The import supports text file format for both types.

## Create ZIP/postal codes manually

Instead of importing codes, use the **Address setup** page to manually add new ZIP or postal codes.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
