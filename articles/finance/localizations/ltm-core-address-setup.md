--- 
title: Address setup for Latin America
description: This article provides information about how to use the LATAM extension from your address setup.
author: cpicon85 
ms.date: 11/14/2022  
ms.topic: article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
--- 

# Latam Address setup

Each Latin American country has a Tax Identification to identify its taxpayers. This article provides information about how to associate the tax identification ID to each country, state, and county using the LATAM extension from the Address setup.

## Prerequisites
The following prerequisites must be met before you can add information to the LATAM extension.
- **Country/region**, **State**, and **County** standard fields
- **LATAM fiscal register** feature

## Country/region tab configuration

Complete the following steps to associate a tax ID to a country on the **Address setup** page.

1.	Go to the Country/region tab.
2.	On the **Country/region** tab, find and select the desired country/region.
3.	Select **LATAM** > **LATAM**.
4.	In the **Foreign country/region** field select Yes only for a foreign country.
5.	In the **Allowed country/region document types** section select **New**.
6.	In the list, select a tax identification ID.
7.  Select **Save** and close the page.

> [!NOTE]
> By default, the **Foreign country/region** field checkbox is marked. Verify that this checkbox is cleared for the base country.


To add the codification provided by the fiscal authorities.

1.	Go to the Country/region tab.
2.	On the **Country/region** tab, select **LATAM** > **Tax application**.
3.	Select **New**.
4.	In the list, select the **Tax application ID**. 
5.	In the **Tax application code** field, type a value.
6.	Save your changes and close the page.

The following steps are only for Argentina. Youmay need to add a country tax ID provided by the fiscal authorities.

1.  Go to the Country/region tab.
2.	On the **Country/region** tab, select **LATAM** > **Country per Taxpayer Type identification**.
4.	In the **Tax application ID** field, select an ID .
5.	In the **Taxpayer type** field, select a taxpayer type.
6.	In the **Country document type** field, select document type.
7.	In the **Country identification number** field, type a value.
8.	Save your changes and close the page.


## State configuration

Complete the following steps to associate a tax identification ID to a state or province on the **Address setup** page.

1. Go to the State/province tab.
2. On the **State/province** tab, select **LATAM** > **LATAM**.
3. Select **New**.
4. In the **State document type** field, select a document type from the list.
5. Save your changes and close the page.

> [!NOTE] 
> Only documents that are configured as the **State Document type** in the **Fiscal register** feature can be selected.

Complete the following steps to add the codification provided by the fiscal authorities.

1.	Go to the State/province tab.
2.	On the **State/province** tab, select **LATAM** > **Tax application**.
3.	Select **New**.
4.	In the list, select the **Tax application ID**.
5.	In the **Tax application code** field, type a value.
6.	Save your changes and close the page. 

## County configuration

In different situations, it might be necessary to indicate if the city where a client, supplier, or the legal entity is located, is in a free trade zone.

1. Go to the County tab.
2. On the **County** tab, select **LATAM** > **LATAM**.
3. Select **New**.
4. Select the **Free trade zone** checkbox.
5. Save your changes and close the page.

By default, brings the full fields Country/Region, Description, State, Description, County and Description.

Complete the following steps to add the codification provided by the fiscal authorities.

1.	Go to the County tab.
2.	On the **County** tab, select **LATAM** > **Tax application**.
3.	Select **New**.
4.	In the list, select the **Tax application ID**.
5.	In the **Tax application code** field, type a value.
6.	Save your changes and close the page.

