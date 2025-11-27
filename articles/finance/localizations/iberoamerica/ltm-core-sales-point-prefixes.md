---
title: Sales point prefixes for Latin America
description: Learn about the sales point prefix configuration for Latin America, including prerequisites and an outline on setting up sales point prefixes.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 07/01/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Sales point prefixes for Latin America

[!include [banner](../../includes/banner.md)]

You can configure the sales point prefixes that some fiscal authorities require for legal documents, treasury documents and check books.

## Prerequisites

Before you set up a sales point prefix record, the following prerequisites must be met:
- The legal entity must have an address in a country/region within the LATAM localization.
- Both the region-specific LATAM feature and the general feature must be enabled.
- Warehouses that will be added to the sales point prefix configuration must already exist.

## Set up a sales point prefix for Latin America

Follow these steps to set up a sales point prefix for Latin America.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales Point Prefix**.
1. On the **Action pane**, select **New**.
1. In the **General** section, complete the **Sales point** field with a code that identifies the record.
1. Complete the **Description** field with a brief description of the sales point prefix.
1. Enable the **Validate CA** toggle to require a CA number when this sales point prefix is used in a transaction.
1. In the **Sales point type** field, select the document printing method that will be applied when the sales point is used in transactions. The recommended default value is **Pre-printed**.
1. In the **Prefix** field, add the prefix that will be included in the document number of the transaction.
1. In the **Report/Service Id** field, select a **SSRS Reports/Services references** record.

   Learn more in [SSRS Reports/Services references configuration for Latin America](ltm-ssrsreport-services.md).
   
1. In the **Warehouse** section, complete the grid by listing the warehouses involved in transactions with this sales point.

## Add the fiscal codification provided by the fiscal authorities

You can use the **Tax application** option to add this codification.

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point Prefix**.
2. On the Action Pane, select **Tax application**.
3. Select **New** to add a line to the grid.
4. In the **Tax application ID** field, select a value.
5. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the sales point
6. Select **Save**.

Learn more in [Tax application for Latin America](ltm-core-tax-application.md)
