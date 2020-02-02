---
# required metadata

title: Unique certification
description: Unique certification.
author: ilkond
manager: AnnBe
ms.date: 11/13/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.9

---

# Unique certification

[!include [banner](../includes/banner.md)]

In Italy, Withholding tax agents must electronically communicate the Unique Certification to the Revenue Agency to certify:
-	Incomes of dependent employments
-	Self-employed incomes
-	Commissions
-	Other incomes

## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Unique certification** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Setup Unique Certification
### Setup Unique Certification Number Sequence
In **General ledger > Ledger setup > General ledger parameters > Number sequences** (tab), in **Unique certification Id** field define a number sequence.

### Setup Unique Certification Revenue typology
**Revenue typology** needs to be set up in Vendors master data, in **Invoice and delivery** section and in the **Revenue typology** field.

You can import the list of possible Revenue typology values by using the **Setup Unique certification values** (UniqueCertificationValueEntity) entity and the Data management framework. For more information, see [Data import and export jobs overview](../../dev-itpro/data-entities/data-import-export-job.md).

The source data that is used to import Revenue typology values can be presented as a Microsoft Excel file that has the following column names:

- FIELD
- VALUE
- ACTIVE
- VALUEDESCRIPTION

Revenue topology values can be manually editted via **Tax > Setup > Withholding tax > Setup Unique certification values**.

### Setup Unique Certification format
In **General ledger > Ledger setup > General ledger parameters > Withholding tax** (tab), in **Unique Certification format mapping** field define the Electronic reporting format that will be used for Unique Certification report generation.

## Use...

### Post

When you post...

> [!NOTE]
> Warning...
