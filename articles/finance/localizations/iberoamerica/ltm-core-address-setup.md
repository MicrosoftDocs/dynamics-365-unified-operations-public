--- 
title: Address setup for Latin America
description: Learn how to use the LATAM extension from your address setup, including prerequisites and an outline of country/region configuration.
author: cpicon85
ms.author: v-cpicon
ms.topic: how-to
ms.custom: bap-template
ms.date: 11/25/2026
ms.reviewer: johnmichalak
--- 

# Address setup for Latin America

[!INCLUDE [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

Each Latin American country or region has a tax identification ID to identify its taxpayers. This article explains how to associate the tax identification ID with each country or region, state or province, and county by using the LATAM extension from the **Address setup** page.

## Prerequisites

Before you can add information to the LATAM extension of the **Address setup** page, ensure you meet the following prerequisites.
- The legal entity has an address in a country or region within the LATAM localization.
- Both the region-specific LATAM feature and the general feature are enabled.
- **Country/region**, **State**, **County**, **City**, and **District** records are created.

## Country/region configuration

Follow these steps to associate a tax ID with a country or region on the **Address setup** page.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **Country/region** tab, find and select the country or region you want.
1. Select **LATAM** \> **LATAM**.
1. If the selected country or region is foreign, make sure the **Foreign country/region** checkbox is selected.

    > [!IMPORTANT]
    > By default, the **Foreign country/region** checkbox is selected. Only clear it for the legal entity's base country/region.

1. In the **Allowed country/region document types** section, select **New**.
1. In the list, select a tax identification ID.
1. Select **Save**, and close the page.

### Add the fiscal codification provided by the fiscal authorities

Follow these steps to add the codification provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **Country/region** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the **Tax application ID**. 
1. In the **Tax application code** field, enter a value.
1. Save your changes and close the page.

Learn more in [Tax application for Latin America](ltm-core-tax-application.md).

### Country per taxpayer type identification

Use this form to assign the document numbers that the base country's tax authority uses to identify each foreign country as a taxpayer.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Go to the **Country/region** tab, select **LATAM** \> **Country per Taxpayer Type identification**.
1. In the **Tax application ID** field, select an ID.
1. In the **Taxpayer type** field, select a taxpayer type.
1. In the **Country document type** field, select a document type.
1. In the **Country identification number** field, enter a value.
1. Save your changes and close the page.

## State/province configuration

Follow these steps to associate a tax identification ID with a state or province on the **Address setup** page.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Go to the **State/province** tab, select **LATAM** \> **LATAM**.
1. Select **New**.
1. In the **State document type** field, select a document type.
1. Save your changes and close the page.

> [!NOTE]
> You can select only documents that are configured as **State Document type** in the **Fiscal register** feature.

### Add the fiscal codification provided by the fiscal authorities

Follow these steps to add the codification that the fiscal authorities provide.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Go to the **State/province** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the **Tax application ID**.
1. In the **Tax application code** field, enter a value.
1. Save your changes and close the page.

## County configuration

Follow these steps to add the codification that the fiscal authorities provide.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Go to the **County** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the **Tax application ID**.
1. In the **Tax application code** field, enter a value.
1. Save your changes and close the page.

## City configuration

Follow these steps to add the codification that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Go to the **City** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the **Tax application ID**.
1. In the **Tax application code** field, enter a value.
1. Save your changes and close the page.

## District configuration

Follow these steps to add the codification that the fiscal authorities provide.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. Go to the **District** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the **Tax application ID**.
1. In the **Tax application code** field, enter a value.
1. Save your changes and close the page.
