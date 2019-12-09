---
# required metadata

title: Standard Audit File for Tax (SAF-T) for Norway
description: This topic explains how to set up and generate the Standard Audit File for Tax (SAF-T) for legal entities that have a primary address in Norway. 
author: v-elgolu
ms.author: v-elgolu
ms.date: 12/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

manager: 
# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Standard Audit File for Tax (SAF-T) for Norway

[!include [banner](../includes/banner.md)]

This topic includes country-specific information about how to set up the Standard Audit File for Tax (SAF-T) for legal entities that have a primary address in Norway.

## Introduction

Starting from January 2020 all the companies in Norway are obliged to provide by request of Norwegian Tax Administration Standard Audit File for Taxes Financial data (SAF-T) in accordance with the Documentation v.1.4 published on July 08,2019 and Technical documentation v.1.3 published on March 23, 2018 in the format of XML report coincident with the XSD schema v.1.1 of “Norwegian SAF-T Financial data” developed by “SAF-T Working group”, Skatteetaten ©, based on “OECD Standard Audit File - Taxation 2.00” modified on 02-02-2018.

## Overview

To support “Norwegian SAF-T Financial data” report in Microsoft Dynamics 365 for Finance and Operations, version of the application must be of the following or later version:

| Version of Finance and Operations | Build number                       | 
|-----------------------------------|------------------------------------|
| 10.0.6      | 10.0.234.**20020**            |
| 10.0.7      | 10.0.283.**10012**            |
| 10.0.8      | 10.0.319.**12**               |
| 10.0.9      | 10.0.328.**20020**            |

When version of the Finance and Operations application is suitable, import from the LCS portal the following or later versions of the Electronic reporting (ER) configurations:

|ER configuration name | Configuration type                       | Version |
|----------------------|------------------------------------------|---------|
| Standard Audit File (SAF-T)    | **Model**            | 32 |
| SAF-T Financial data model mapping   | **Model mapping**            | 32.30 |
| SAF-T Format (NO)   | Format (exporting)           | 32.41 |

Import the latest versions of the configurations. The version description usually contains the number of the KB article that explains the change introduced by the configuration version.

**Note**: After all the ER configurations from the preceding table are imported, set the **Default for model mapping** option to **Yes** for the following configuration:	**SAF-T Financial data model mapping**.

For more information about how to download ER configurations from Microsoft Dynamics Lifecycle Services (LCS), see Download Electronic reporting configurations from Lifecycle Services.

## Setup

To start using “Norwegian SAF-T Financial data” report in Microsoft Dynamics 365 for Finance and Operations the following setup must be done:

•	General ledger parameters – to setup ER format

•	Sales tax code – to associate with Standard tax codes (read more in the about this requirement in “Norwegian SAF-T Financial data Documentation”)

•	Main accounts – to associate with Standard accounts (read more in the about this requirement in “Norwegian SAF-T Financial data Documentation”)




