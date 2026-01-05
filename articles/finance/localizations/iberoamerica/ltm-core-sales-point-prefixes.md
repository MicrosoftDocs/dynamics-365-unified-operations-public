---
title: Sales point prefixes for Latin America
description: Learn about the sales point prefix configuration for Latin America, including prerequisites and an outline on setting up sales point prefixes.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Sales point prefixes for Latin America

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](../includes/does-not-apply-to.md)]

You can configure the sales point prefixes that some fiscal authorities require for legal documents, treasury documents, and checkbooks.

## Prerequisites

Before you set up a sales point prefix record, meet the following prerequisites:
- The legal entity must have an address in a country or region within the LATAM localization.
- Both the region-specific LATAM feature and the general feature must be enabled.
- Warehouses that you add to the sales point prefix configuration must already exist.

## Set up a sales point prefix for Latin America

To set up a sales point prefix for Latin America, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales Point Prefix**.
1. On the **Action pane**, select **New**.
1. In the **General** section, enter a code in the **Sales point** field that identifies the record.
1. Enter a brief description of the sales point prefix in the **Description** field.
1. Enable the **Validate CA** toggle to require a CA number when this sales point prefix is used in a transaction.
1. In the **Sales point type** field, select the document printing method that you want to apply when the sales point is used in transactions. The recommended default value is **Pre-printed**.
1. In the **Prefix** field, add the prefix that you want to include in the document number of the transaction.
1. In the **Report/Service Id** field, select a **SSRS Reports/Services references** record.

   Learn more in [SSRS Reports/Services references configuration for Latin America](ltm-ssrsreport-services.md).
   
1. In the **Warehouse** section, complete the grid by listing the warehouses involved in transactions with this sales point.

## Add the fiscal codification provided by the fiscal authorities

Use the **Tax application** option to add this codification.

To add the fiscal codification provided by the fiscal authorities, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point Prefix**.
1. On the Action Pane, select **Tax application**.
1. Select **New** to add a line to the grid.
1. In the **Tax application ID** field, select a value.
1. In the **Tax application code** field, enter the code that the fiscal authority uses to identify the sales point.
1. Select **Save**.

Learn more in [Tax application for Latin America](ltm-core-tax-application.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]