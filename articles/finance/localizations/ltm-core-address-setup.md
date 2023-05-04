--- 
title: Address setup for Latin America
description: This article provides information about how to use the LATAM extension from your address setup.
author: cpicon85 
ms.date: 01/31/2023
ms.topic: article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
--- 

# Address setup for Latin America

[!include [banner](../includes/banner.md)]

Each Latin American country has a tax identification ID to identify its taxpayers. This article explains how to associate the tax identification ID with each country or region, state or province, and county by using the LATAM extension from the **Address setup** page.

## Prerequisites

The following prerequisites must be in place before you can add information to the LATAM extension:

- **Country/region**, **State**, and **County** standard fields
- **LATAM fiscal register** feature

## Country/region configuration

Follow these steps to associate a tax ID with a country or region on the **Address setup** page.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
2. On the **Country/region** tab, find and select the desired country or region.
3. Select **LATAM** \> **LATAM**.
4. If the selected country or region is foreign, make sure that the **Foreign country/region** checkbox is selected.

    > [!IMPORTANT]
    > By default, the **Foreign country/region** checkbox is selected. Make sure that it's cleared for the base country.

5. In the **Allowed country/region document types** section, select **New**.
6. In the list, select a tax identification ID.
7. Select **Save**, and close the page.

Follow these steps to add the codification that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
2. On the **Country/region** tab, select **LATAM** \> **Tax application**.
3. Select **New**.
4. In the list, select the tax application ID. 
5. In the **Tax application code** field, enter a value.
6. Save your changes, and close the page.

The following procedure applies only to organizations with a primary address in Argentina. You might have to add a country tax ID that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
2. On the **Country/region** tab, select **LATAM** \> **Country per Taxpayer Type identification**.
3. In the **Tax application ID** field, select an ID.
4. In the **Taxpayer type** field, select a taxpayer type.
5. In the **Country document type** field, select document type.
6. In the **Country identification number** field, enter a value.
7. Save your changes, and close the page.

## State/province configuration

Follow these steps to associate a tax identification ID with a state or province on the **Address setup** page.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
2. On the **State/province** tab, select **LATAM** \> **LATAM**.
3. Select **New**.
4. In the **State document type** field, select a document type.
5. Save your changes, and close the page.

> [!NOTE]
> Only documents that are configured as **State Document type** in the **Fiscal register** feature can be selected.

Follow these steps to add the codification that's provided by the fiscal authorities.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
2. On the **State/province** tab, select **LATAM** \> **Tax application**.
3. Select **New**.
4. In the list, select the tax application ID.
5. In the **Tax application code** field, enter a value.
6. Save your changes, and close the page. 

## County configuration

In some situations, it might be necessary to indicate whether the city where a client, supplier, or legal entity is located is in a free trade zone.

1. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
2. On the **County** tab, select **LATAM** \> **LATAM**.
3. Select **New**.
4. Select the **Free trade zone** checkbox.
5. Save your changes, and close the page.

Follow these steps to add the codification that's provided by the fiscal authorities.

1. On the **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**.
2. On the **County** tab, select **LATAM** \> **Tax application**.
3. Select **New**.
4. In the list, select the **Tax application ID**.
5. In the **Tax application code** field, enter a value.
6. Save your changes and close the page.
