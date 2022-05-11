---
# required metadata

title: Unique certification
description: This topic provides information about the Unique certification for companies in Italy.
author: ilkond
ms.date: 03/22/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
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

In Italy, withholding tax agents must electronically communicate the Unique certification to the revenue agency to certify the following information:

- Income of dependent employments
- Self-employed income
- Commissions
- Other income

## Prerequisites

The following prerequisites must be met before the functionality can be used:

- The primary address of the legal entity must be in Italy.
- The **Unique certification** feature must be turned on in the **Feature management** workspace. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up the Unique certification

### Set up a number sequence

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **Number sequences** tab, in the **Unique certification Id** field, define a number sequence.

### Set up the unique certification values

1. Go to **Tax** \> **Setup** \> **Withholding tax** \> **Set up unique certification values**
2. Specify the values for the **Unique certification** feature.

The **Set up unique certification values** page allows you to configure the values available for several fields:

- **record B**: Exceptional events
- **record D**: Exceptional events, special categories, and unified counties
- **record H**: Reason and code

Values that are specified on **Setup Unique Certification values** page, and marked with **Yes** in the **Active** column, will be available in the related lookup fields on the **Unique certification** page. Use this page for future regulatory upgrades of the unique certification to add or delete values.

You can import the initial set of values for **Setup Unique Certification values** by using the **Setup Unique certification values** (UniqueCertificationValueEntity) entity and the Data management framework. For more information, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md). You can download the initial set of values for the **Setup Unique Certification values** from the **IT SetupUniqueCertificationValues** file in the **Data package** asset data type section of the **Shared asset library** in the [LCS portal](https://lcs.dynamics.com/v2) and then import it in to the Data management framework.

The source data used for import can be presented as a Microsoft Excel file that has the following column names:

- FIELD
- VALUE
- ACTIVE
- VALUEDESCRIPTION

### Set up a revenue typology for the Unique certification

You must set up a revenue typology in the **Revenue typology** field in the **Invoice and delivery** section on the **Vendors** page.

### Set up a format for the Unique certification

1. Go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
2. On the **Withholding tax** tab, in the **Unique Certification format mapping** field, define the Electronic reporting (ER) format that should be used to generate the Unique certification.

## Generate the Unique certification

1. Go to **Tax** \> **Declarations** \> **Withholding tax** \> **Unique Certification**.
2. Select **New**.

    > [!NOTE]
    > The year before the year of the current system date is automatically assigned as the reporting year of the declaration.

3. In the **Title-page** section, enter the company information and the information about the person who is in charge of communicating the Unique certification to the revenue agency.
4. Select **Generate** to create the certifications for each recipient and to automatically fill in the other sections. The **Vendor** section contains the list of recipients (vendors) and the vendor details.
5. Select **Generate details** to enter the details of vendors transactions in the declaration.
6. The **Withholding tax** section shows the amounts of each vendor certification. The amounts are calculated and sorted by withholding tax code.

## Process the Unique certification

After the Unique certification is generated and filled with data, you can select **Validate** to validate the data before the output file is generated. After the output file is validated, select **Export** to generate the electronic output file in the legally required format.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
