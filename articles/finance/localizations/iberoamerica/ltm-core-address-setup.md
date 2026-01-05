--- 
title: Address setup for Latin America
description: Learn about how to use the LATAM extension from your address setup, including prerequisites and an outline on country/region configuration.
author: cpicon85
ms.author: v-cpicon
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/05/2026
ms.reviewer: johnmichalak
--- 

# Address setup for Latin America

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](../includes/does-not-apply-to.md)]

Each Latin American country/region has a tax identification ID to identify its taxpayers. This article explains how to associate the tax identification ID with each country or region, state or province, and county by using the LATAM extension from the **Address setup** page.

## Prerequisites

The following prerequisites must be in place before you can add information to the LATAM extension:

- **Country/region**, **State**, and **County** standard fields
- **LATAM fiscal register** feature

## Country/region configuration

Follow these steps to associate a tax ID with a country or region on the **Address setup** page.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **Country/region** tab, find and select the desired country or region.
1. Select **LATAM** \> **LATAM**.
1. If the selected country or region is foreign, make sure that the **Foreign country/region** checkbox is selected.

    > [!IMPORTANT]
    > By default, the **Foreign country/region** checkbox is selected. Make sure that it's cleared for the base country/region.

1. In the **Allowed country/region document types** section, select **New**.
1. In the list, select a tax identification ID.
1. Select **Save**, and close the page.

Follow these steps to add the codification that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **Country/region** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the tax application ID. 
1. In the **Tax application code** field, enter a value.
1. Save your changes, and close the page.

The following procedure applies only to organizations with a primary address in Argentina. You might have to add a country/region tax ID that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **Country/region** tab, select **LATAM** \> **Country/region per Taxpayer Type identification**.
1. In the **Tax application ID** field, select an ID.
1. In the **Taxpayer type** field, select a taxpayer type.
1. In the **Country/region document type** field, select document type.
1. In the **Country/region identification number** field, enter a value.
1. Save your changes, and close the page.

## State/province configuration

Follow these steps to associate a tax identification ID with a state or province on the **Address setup** page.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **State/province** tab, select **LATAM** \> **LATAM**.
1. Select **New**.
1. In the **State document type** field, select a document type.
1. Save your changes, and close the page.

> [!NOTE]
> Only documents that are configured as **State Document type** in the **Fiscal register** feature can be selected.

Follow these steps to add the codification that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **State/province** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the tax application ID.
1. In the **Tax application code** field, enter a value.
1. Save your changes, and close the page. 

## County configuration

In some situations, it might be necessary to indicate whether the city where a client, supplier, or legal entity is located is in a free trade zone.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **County** tab, select **LATAM** \> **LATAM**.
1. Select **New**.
1. Select the **Free trade zone** checkbox.
1. Save your changes, and close the page.

Follow these steps to add the codification that's provided by the fiscal authorities.

1. On the **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
1. On the **County** tab, select **LATAM** \> **Tax application**.
1. Select **New**.
1. In the list, select the **Tax application ID**.
1. In the **Tax application code** field, enter a value.
1. Save your changes and close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]