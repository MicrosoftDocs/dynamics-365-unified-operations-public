---
title: Set up a legal entity and tax information for Venezuela
description: Learn how to configure a legal entity and its tax information for Venezuela. 
author: Fhernandez0088
ms.date: 05/15/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Set up a legal entity and tax information for Venezuela

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up a legal entity and tax information for a company in Venezuela by using the Latin American (LATAM) features that are available in Microsoft Dynamics 365 Finance. A legal entity represents the company. It contains the tax and legal attributes that are required for the rest of the LATAM configuration.

## Prerequisites

Before you begin, open the **Feature management** workspace, and verify that the **LATAM globalization expansion** and **LATAM globalization expansion – Venezuela** features are enabled.

## Create a legal entity

To create a legal entity, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **New**.
1. In the address setup, set up the address format for Venezuela.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
1. On the **Concept and notes** tab, in the **Legal entity** section, set a field as **Activity**.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields as required for other Finance features that you must use.

## Set up tax information

To set up tax information, follow these steps.

1. [Create a document class letter](ltm-core-document-class-letter.md) without a prefix. This document class letter is used in taxpayer and document class configurations.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. Select **New**.
1. In the **Overview** section, in the **Tax ID type** field, enter **RIF-J** (Unique Taxpayer Registry), which is one of the tax ID types for Venezuelan organizations.
1. In the **Format** field, enter **X-XXXXXXXX-X** for RIF. Learn more in [Tax ID types for Latin America](ltm-core-tax-id-type.md).
1. Go to **Organization administration** \> **Global address book** \> **Addresses**, select the country or region where the company is set up, and then select **LATAM** to add the RIF-J tax ID type. Learn more in [Address setup for Latin America](ltm-core-address-setup.md).
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**, and select **New** to create a record that represents organizations.
1. In the **Type** field, enter **PJD** for organizations that are located in Venezuela. Then add the tax ID type and the document class letter that you created. Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
1. In the **LATAM** section, configure the following tax and legal information for the legal entity:

    - In the **Taxpayer type** field, select **PJD** to represent an organization.
    - In the **Based in country/region** field, select **Venezuela**.
    - In the **Country document type** field, select **RIF-J**.
    - Complete the country document number, including the tax ID number of the company.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
