---
# required metadata

title: AX 2009 migration - Generate maps 
description: This topic provides information about generating data maps to migrate data from Dynamics AX 2009 to Finance and Operations.
author: kfend
manager: AnnBe
ms.date: 06/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: kfend
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration - Generate maps

[!include [banner](../includes/banner.md)]

Before you can migrate your data from Microsoft Dynamics AX 2009 to Microsoft Dynamics 365 for Finance and Operations, you need to align your source data with your target environment. 

This procedure provides information about how to generate source to target mappings, extract the schema from Finance and Operations, and generate the entity sequence after all of the entered values, such as SQL credentials, default configuration file path, and export package file paths have been validated.

Before you can generate maps, you must provide the target URL, Tenant URL, and Service app ID to validate the connection. 

   > [!NOTE]
   > When you create a new App under Azure AAD on the Azure portal, you have two options, **Web API** and **Native**. Select **Native** and grant permissions to the native Azure AAD app.

## Prerequisites
Before you generate the data maps between the source and target environments, you must install the Data migration tool (DMT). For more information, see [Install the Data migration tool]().

## Generate maps
Complete the following steps to generate maps for data migration between AX 2009 and Finance and Operations. 
1. In Dynamics AX 2009, fom the navigation pane, go to **Data migration** > **Setup** > **Configure connections**.
2. Review the field information to verify that it is correct, and then click **Validate**.
3. After the information is validated, close the form and under **Setup**, click **Configure and generate maps**.
4. Verify that the information in the form is correct, and then click **Validate path**.
5. After validation is confirmed, click **Generate maps**.
