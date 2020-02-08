---
# required metadata

title: Create a retail functionality profile
description: This topic describes how to create a retail functionality profile in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/27/2020
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
# Create a retail functionality profile


[!include [banner](includes/banner.md)]

This topic describes how to create a retail functionality profile in Microsoft Dynamics 365 Commerce.

## Overview

The retail functionality profile provides various settings used for online channels. Each retail channel must specify a retail functionality profile.

## Create a retail functionality profile

To create a retail functionality profile, follow these steps.

1. In the navigation pane, go to **Modules \> Channel setup \> POS profiles \> Functionality profiles**.
1. On the action pane, select **New**.
1. In the **Profile** field, enter an ID for the profile ("FN006" in the example image below).
1. In the **Description** field, enter a value ("Adventure Works Profile" in the example image below).
1. In the **General** section, select a country for the **ISO** locale.
1. In the **General** section, modify other settings, as needed.
1. In the **General** section, select a **Receipt profile ID** for email receipts.
1. In the **Functions** section, modify settings, as needed.
1. In the **Amount** section, modify settings as, needed.
1. In the **Info Codes** section, modify settings, as needed.
1. In the **Receipt numbering** section, modify settings, as needed. 
  
The following image shows an example retail functionality profile.
  
![Retail functionality profile example](media/retail-functionality-profile.png)

## Additional resources

[Info codes and info code groups](info-codes-retail.md)  		  

[Create new address book](new-address-book.md) 

[Screen layout overview](pos-screen-layouts.md)		  

[Configure and install Retail hardware station](retail-hardware-station-configuration-installation.md) 
