---
# required metadata

title: Retail functionality profile
description: This topic presents an overview of setting up a Retail functionality profile for Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2020-01-20
ms.dyn365.ops.version: Release 10.0.8

---
# Retail functionality profile

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic presents an overview of setting up a Retail functionality profile for Microsoft Dynamics 365 Commerce.

## Overview

TBD

## Create a functionality profile
The following procedure explains how to create a retail functionality profile from within Commerce Headquarters app.

* Go to **Navigation pane** > **Modules** > **Channel setup** > **POS profiles** > **Functionality profiles**.
* From the action pane, click **New**.
* In the **Profile** field, provide an ID for the profile, the example below uses "FN006".
* In the **Description** field, provide a value, the example below uses "Adventure Works Profile".
* Expand the **General** section.
  * Select a country for the **ISO** locale.
  * Modify other settings if desired.
  * Select a **Receipt profile ID* for email receipts.
* Expand the **Functions** section.
  * Modify settings as desired.
* Expand the **Amount** section.
  * Modify settings as desired.
* Expand the **Info Codes** section.
  * Modify settings as desired.
* Expand the **Receipt numbering** section.
  * Modify settings as desired. 
  
The following image shows an example retail functionality profile.
  
![Retail functionality profile example](media/retail-functionality-profile.png)

## Additional resources

[Info codes and info code groups](../retail/info-codes-retail.md?toc=/dynamics365/commerce/toc.json)  		  

[Create new address book](new-address-book.md) 

[Screen layout overview](../retail/pos-screen-layouts.md?toc=/dynamics365/commerce/toc.json)		  

[Configure and install Retail hardware station](../retail/retail-hardware-station-configuration-installation.md?toc=/dynamics365/commerce/toc.json) 
