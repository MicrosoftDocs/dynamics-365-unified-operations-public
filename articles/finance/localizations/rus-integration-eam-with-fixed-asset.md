
---
# required metadata
title: Integration of Asset management module with Fixed asset (Russia) module 
description: This topic provides information about the Integration of Asset management module with Fixed asset (Russia) module.
author: v-oloski
ms.date: 01/27/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata
ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 

ms.search.region: Russia
# ms.search.industry: 
ms.author: v-olgaoskina
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: 10.0.25

---
# Integration of Asset management module with Fixed asset (Russia) module

[!include [banner](../includes/banner.md)]

Manufacturers and certain distributors invest and operate assets that help them to perform the needed product transformation to add value to the supply chain they are a part of. With this release, substantial additions will be made to support various types of maintenance (Predictive, Corrective, Condition, and Preventive). This will allow assets-sensitive operations to enroll our base application without investing in additional solutions.
See more details in Asset management overview - Supply Chain Management | Dynamics 365 | Microsoft Docs, Functional locations and assets - Supply Chain Management | Dynamics 365 | Microsoft Docs, Assets and work orders - Supply Chain Management | Dynamics 365 | Microsoft Docs.
Asset management module has been integrated with Fixed asset (Russia) module.
This functionality allows:
•	Relate a fixed asset (Russia) with the asset
•	Create an asset, and view the asset and cost related with the fixed asset from a fixed asset (Russia).
To relate an asset with the fixed asset (Russia), open Asset management > Assets > All assets, select an asset record, and select the fixed asset on the Fixed asset FastTab (Fixed asset (RUSSIA) field group).
You can create an asset directly from a fixed asset (Russia) and the system automatically relates the created asset with the fixed asset (Fixed asset (Russia) > Common > Fixed assets, select the fixed asset record, Action pane > Assets management > Create maintenance asset). 
You can open the asset related to the fixed asset (Russia) from a fixed asset (Russia) record and track the asset cost (Fixed asset (Russia) > Common > Fixed assets, select the fixed asset record, Action pane > Assets management > Maintenance asset/ Maintenance cost). 

Note. When a user creates a work order (Investment type) from the asset, related to the fixed asset (Russia) then the system does not set this fixed asset in the automatically created project. Integration fixed asset (Russia) with the Project accounting and management is out of scope.  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]


