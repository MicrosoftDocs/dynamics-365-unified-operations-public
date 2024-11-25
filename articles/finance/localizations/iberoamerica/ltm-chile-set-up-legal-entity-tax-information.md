---
title: Set up legal entity and tax information for Chile
description: Learn how to set up legal entity and tax information for a Chilean company, including outlines for creating legal entities and setting up tax information.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/10/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Set up legal entity and tax information for Chile

[!include [banner](../../includes/banner.md)]

This article explains how to set up a legal entity and the tax information for a company in Chile that's using the Latin American (LATAM) features that are available in Microsoft Dynamics 365 Finance. A legal entity represents the company, and contains the tax and legal attributes that are required for the rest of the LATAM configuration.

Before you begin, open the **Feature management** workspace, and verify that the **LATAM globalization expansion - Chile** feature is enabled. If it isn't enabled, enable it. When you're sure that the feature is enabled, complete the following procedures.

## Create a legal entity

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **New** to create a legal entity.
2. Set the company address to Chile. Some functionality is enabled only for Chile. Examples include specific tax reports and electronic invoices.
3. In the address setup, set up the Chilean territorial organization, and configure **States** as **Regions**, **Counties** as **Provinces**, and **Cities** as **Communes**.
4. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
5. On the **Concept and notes** tab, enter any necessary information, and set the **Legal entity** field to **Active**.

## Set up tax information

1. [Create a document class letter](../ltm-core-document-class-letter.md) without a prefix. This document class letter is used in taxpayer and document class configurations.
2. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and select **New**.
3. In the **Overview** section, in the **Tax ID type** field, enter **RUT**. (RUT is short for "Registro Único Tributario.")
4. In the **Format** field, enter **XXXXXXXX-X**. For more information, see [Tax ID types for Latin America](../ltm-core-tax-id-type.md).
5. Go to **Organization administration** \> **Global address book** \> **Addresses**, and select the country/region where the company is located.
6. Select **LATAM**, and then, in the **Tax ID type** field, enter **RUT**. For more information, see [Address setup for Latin America](../iberoamerica/ltm-core-address-setup.md).
7. Go to **Organization administration** \> **Organizations** **Legal entities**.
8. In the **LATAM** section, configure the following entity tax and legal information:

    - In the **Taxpayer type** field, select the **Persona Juridica** type that represents an organization.
    - In the **Based in country/region** field, select **Chile**.
    - In the **Country document type** field, select **RUT**.
    - Complete the **Country document number** field with the RUT of the company.
    - In the **Concept and notes** section, complete the first field with the company activity.

You'll notice that customers and vendors have a similar structure in the LATAM configuration.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
