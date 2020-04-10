---
# required metadata

title: Hazardous materials
description: This topic provides information about hazardous material documents and information that is stored in your environment.
author: lachlancashMS
manager: tfehr
ms.date: 01/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 19171
ms.assetid: 81fa3709-4ab8-4fbf-9806-359892a05985
ms.search.region: Global
ms.search.industry: Retail
ms.author: conradv
ms.search.validFrom: 2019-10-14
ms.dyn365.ops.version: 

---

# Hazardous materials

[!include [banner](../includes/banner.md)]

Information about hazardous materials is set up in Product information management. This module also provides documents that can be printed through warehouse management.

When you ship materials that are classified as dangerous goods, additional paperwork must be included with the shipments. The hazardous materials functionality lets customers store classification information and relate it to release items. This information can then be used to help prepare shipping documentation.

> [!IMPORTANT]
> To help manage shipments of dangerous goods, Microsoft Dynamics 365 Supply Chain Management lets you set up additional reference information that is related to products. You can also set up additional shipment documents. However, the system isn't automatically compliant with your country's or region's regulations. Instead, it's a tool that can help your overall program.

Before you can use this functionality, the following setup is required:

- **Product information management:** Set up codes that can be applied to released products.
- **Warehouse management:** Use additional shipping documents to print shipment information.

## Product information management

In Product information management, there is a range of setup tables where you can add the reference information that is provided in the dangerous goods lists for road, air, and sea freight.

Here are some of the regulations that are often referenced:

- **ADR** – Regulations that are related to the international carriage of dangerous goods by road
- **CFR 49** – Regulations in the United Sates for the carriage of dangerous goods
- **IMDG** – The International Marine Dangerous Goods (IMDG) code
- **IATA** – The International Air Transport Association (IATA) dangerous goods regulations

Each of these regulations has a dangerous goods list that includes reference codes. The lists for each type of transport are combined on shared international classifications. Supply Chain Management provides a reference table for the shared codes in those lists. Each list also has some unique codes that can be defined.

To start to configure this information, create a regulation that you can use to configure the initial parameters.

## Warehouse management

When a shipment is prepared, several new reports can be printed. These reports use the information that you set up in Product information management.
