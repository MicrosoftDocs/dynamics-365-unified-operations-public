---
title: Set up the SAF Fixed Assets Tax report (JPK_KR_ST)
description: Learn about how to set up and generate the SAF Fixed Assets Tax report (JPK_KR_ST) in Poland
author: baryshnikova
ms.author: baryshnikova 
ms.topic: concept-article
ms.custom: 
  - bap-template
ms.date: 07/13/2026
ms.reviewer: johnmichalak
ms.search.region: Poland
---


# Set up the SAF Fixed Assets Tax report (JPK_KR_ST)

[!INCLUDE [banner](../../includes/banner.md)]

This article describes how to set up and generate the SAF Fixed Assets Tax report (JPK_KR_ST) for Poland in Microsoft Dynamics 365 Finance. The report produces the JPK audit file required by the Polish Ministry of Finance, providing fixed asset analytics for accounting and tax purposes based on the existing Assets Roll Forward report, exported in the extended JPK structure (SAF-T concept).

## Prerequisites

Before configuring the report, ensure the following prerequisites are in place:

- Finance version 10.0.44, 10.0.45, 10.0.46, 10.0.47, or later.

  > [!NOTE]
  > The feature (Poland) JPK Audit File for Fixed Assets Reporting is enabled by default. You can confirm its status under Workspaces > Feature management.

- The Polish localization is enabled for the legal entity (CountryRegionCodes = PL).
- The Fixed assets module is configured, including:
  - Fixed asset books - the report requires both a Tax book and an Accounting book.
  - Depreciation profiles, asset groups, and posting profiles.
- The Electronic reporting (ER) framework is enabled and configured to access the Microsoft global repository.
- The user generating the report has access to the Fixed assets reports menu and to Electronic reporting configurations.

## Set up the SAF Fixed Assets Tax report (JPK_KR_ST)

The following sections describe the setup for the SAF Fixed Assets Tax report (JPK_KR_ST)

1. Step 1 - Import the Electronic Reporting (ER) configurations
1. Step 2 - Configure Application Specific Parameters
1. Step 3 - Configure General Ledger parameters

### Step 1 - Import the Electronic Reporting (ER) configurations

To import the Electronic Reporting (ER) configurations, follow these steps:

1. Go to **Workspaces \> Electronic reporting \> Reporting configurations**.
1. From the **Configuration repository**, import the following configurations in the order shown (later configurations depend on earlier ones):

   - Standard Audit File (SAF-T) model
   - Standard Audit File (SAF-T) model mapping (Fixed assets data sources)
   - JPK_KR_ST XML (PL) format

   > [!NOTE]
   > If a configuration isn't available from the configured repository, import it directly from XML via **Reporting configurations \> Exchange \> Load from XML file**.

### Step 2 - Configure Application Specific Parameters

To configure Application Specific Parameters, follow these steps:

1. Go to **Electronic reporting \> Reporting configurations \> JPK_KR_ST XML (PL) \> Configurations \> Application specific parameters**.
1. Configure the required parameter mappings for your environment.
1. Set the **Parameter setup** state to **Completed**.
1. Select **Save**.

### Step 3 - Configure General Ledger parameters

To configure General Ledger parameters, follow these steps:

1. Go to **General ledger \> Ledger setup \> General ledger parameters**.
1. In the **SAF Fixed Assets** field, select the JPK_KR_ST XML (PL) ER format mapping that you imported in Step 1.

> [!NOTE]
> This setting is per legal entity. Repeat this step for each Polish entity that generates the report.

## Generate the SAF Fixed Assets Tax report

To generate the SAF Fixed Assets Tax report, follow these steps:

1. Go to **Fixed assets > the SAF Fixed Assets Tax report menu item (country/region: Poland)**.
1. In the dialog, set the following parameters:

   | \# | Parameter | Description |
   | ---- | ---- | ---- |
   | 1 | From date | The start of the reporting period. |
   | 2 | To date | The end of the reporting period. |
   | 3 | Tax book | The fixed asset Tax book to include in the report. |
   | 4 | Accounting book | The fixed asset Accounting book to include in the report. |
   | 5 | Currency | The reporting currency (ledger currency selection). |
   | 6 | Reclassification | Select this checkbox if the submission is a reclassification. |

1. The From date, To date, Tax book, and Accounting book parameters are required. If the ER format mapping isn't configured in General ledger parameters (Step 3), the report fails validation and displays a message pointing back to setup.
1. Select **OK** to generate the XML file.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
