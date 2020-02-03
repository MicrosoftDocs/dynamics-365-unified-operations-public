---
# required metadata

title: Unique certification
description: This topic provides information about unique certification for companies in Italy.
author: ilkond
manager: AnnBe
ms.date: 02/03/2020
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

In Italy, withholding tax agents must electronically communicate the Unique certification to the Revenue agency to certify the following:

-	Incomes of dependent employments
-	Self-employed incomes
-	Commissions
-	Other incomes

## Prerequisites

The following prerequisites must be met before the feature functionality can be used:

- The primary address of the legal entity must be in Italy.
- The feature, **Unique certification** must be enabled in the **Feature management** workspace. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Set up Unique certification

### Set up number sequences

1. Go to **General ledger** > **Ledger setup** >** General ledger parameters**.
2. On the **Number sequences** tab, in the **Unique certification Id** field, define a number sequence.

### Set up Unique certification revenue typology

**Revenue typology** must to be set up on the **Vendors** page, in the **Invoice and delivery** section, in the **Revenue typology** field.

You can import the list of possible revenue typology values by using the **Setup Unique certification values** (UniqueCertificationValueEntity) entity and the Data management framework. For more information, see [Data import and export jobs overview](../../dev-itpro/data-entities/data-import-export-job.md).

The source data that is used to import revenue typology values can be presented as a Microsoft Excel file that has the following column names:

- FIELD
- VALUE
- ACTIVE
- VALUEDESCRIPTION

Revenue topology values can be manually editted by going to **Tax** > **Setup** > **Withholding tax** > **Setup Unique certification values**.

### Set up Unique certification format

1. Go to **General ledger** > **Ledger setup** > **General ledger parameters**.
2. On the **Withholding tax** tab, in the **Unique Certification format mapping** field, define the Electronic reporting format that will be used for Unique certification generation.

## Create Unique certification

1. To create a new Unique certification declaration, go to **Tax** > **Declarations** > **Withholding tax** > **Unique Certification**.
2. Select **New**.

> [!NOTE]
> The reporting year of the declaration will be automatically assigned as the previous year of the current system's date.

3. In the **Tilte-page** section, enter the company information and the information about the person in charge of communicating the Unique certification to the Revenue agency.
4. Select **Generate** to create the certifications for each recipient and automatically populate the other sections. The **Vendor** section contains the list of the recipients (vendors) and the informantion about vendors details. 
5. Select **Generate details** to populate the declaration with the details of vendors transactions.
6. In **Withholding tax** section, there are the amounts of each vendor certification. The amounts are calculated and sorted by the withholding tax codes.

## Process Unique certification

When Unique certification is created and populated with data, you can select **Validate** to validate the data before the output file is generated. After the output file is validated, select **Export** to generate the output electronic file in the legally required format.

