--- 
# required metadata 
 
title: Audit file (XML Auditfile Financieel, XAF)
description: This topic explains how to set up and generate the Audit file (XML Auditfile Financieel, XAF) for legal entities in the Netherlands.  
author: liza-golub
ms.date: 05/06/2020
ms.topic: article
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxEvatParameters_NL   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Finance
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Netherlands
# ms.search.industry: 
ms.author: elgolu
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Audit file (XML Auditfile Financieel, XAF)

[!include [banner](../../includes/banner.md)]

This functionality is available for legal entities whose primary address is in the Netherlands.

This topic explains how to import Electronic reporting (ER) configurations for the Audit file and how to generate the Audit file (XML Auditfile Financieel, XAF) for legal entities in the Netherlands.

## Import and set up ER configurations

To prepare Microsoft Dynamics 365 Finance to generate the Audit file, you must import the following ER configurations.

| Number | ER configuration name         | Type                                 | Description |
|--------|-------------------------------|--------------------------------------|-------------|
| 1      | Audit file model              | Model                                | A model for the Audit file for Netherlands. |
| 2      | Audit file (NL)               | Format (exporting)                   | ER format for XML Auditfile Financieel, XAF. |

## Generate the Audit file

The steps in this procedure walk you through using the Audit file (XML Auditfile Financieel, XAF).

1. Go to **General ledger** > **Periodic tasks** > **Audit file**.
2. In the **From date** field, enter a date. For example, enter or select 2020-11-01.
3. In the **To date** field, enter a date. For example, enter or select 2020-11-30.
4. In the **Format mapping** field, enter or select **Audit file (NL)**.
5. Select **OK**.
