---
title: Set up a legal entity and tax information for Bolivia
description: Learn how to set up a legal entity and tax information for a company in Bolivia.
author: Cpicon85
ms.date: 02/10/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.author: v-cpicon
ms.custom: bap-template
---

# Set up a legal entity and tax information for Bolivia

[!include [banner](../../includes/banner.md)]

This article explains how to use the Latin American (LATAM) features that are available in Microsoft Dynamics 365 Finance to set up a legal entity and tax information for a company that is located in Bolivia. A legal entity represents the company. It contains the tax and legal attributes that are required for the rest of the LATAM configuration.

Before you begin, open the **Feature management** workspace, and verify that the **LATAM globalization expansion** and **LATAM globalization expansion – Bolivia** features are enabled. If they aren't enabled, enable them. After you're sure that the features are enabled, complete the following procedures.

## Create a legal entity

To create a legal entity, follow these steps:

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **New**.
1. In the address setup, set up the address format for Bolivia.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
1. On the **Concept and notes** tab, in the **Legal entity** section, set a field as **Activity**.

> [!NOTE] 
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Dynamics 365 Finance features that you use.

## Set up tax information

To set up tax information, follow these steps:

1. [Create a document class letter](ltm-core-document-class-letter.md) without a prefix. This document class letter is used in taxpayer and document class configurations.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and select **New**.
1. In the **Overview** section, in the **Tax ID type** field, enter **NIT** (Unique Taxpayer Registry), which is one of the tax ID types for Bolivia.
1. In the **Format** field, enter **XXXXXXXXXX** for the **NIT** tax ID type. Learn more in [Tax ID types for Latin America](ltm-core-tax-id-type.md).
1. Go to **Organization administration** \> **Global address book** \> **Addresses**, select the country where the company is located, and then select **LATAM** to add the **NIT** tax ID type. Learn more in [Address setup for Latin America](ltm-core-address-setup.md).
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**, and select **New** to create a record that represents organizations.
1. In the **Type** field, select **Persona juridica**. Then add the tax ID type and the document class letter that you created. Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. In the **LATAM** section, configure the following entity tax and legal information:

    - In the **Taxpayer type field**, select **Persona juridica** to represent an organization.
    - In the **Based in country/region** field, select **Bolivia**.
    - In the **Country document type** field, select **NIT**.
    - Complete the country document number, including the tax ID number of the company.
    - In the **Concept and notes** section, in the first field, enter the company activity.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
