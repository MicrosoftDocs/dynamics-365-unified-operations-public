---
title: Set up a legal entity and tax information for Ecuador
description: Learn how to configure a legal entity and its tax information for Ecuador. 
author: Cpicon85
ms.date: 01/22/2025
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.author: v-cpicon

---

# Set up a legal entity and tax information for Ecuador

[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to set up a legal entity and tax information for a company that is located in Ecuador by using the Latin American (LATAM) features that are available in Microsoft Dynamics 365 Finance. A legal entity represents the company, and it contains the tax and legal attributes that are required for the rest of the LATAM configuration.

## Prerequisites

Before you begin, open the **Feature management** workspace, and verify that the **LATAM globalization expansion** and **LATAM globalization expansion – Ecuador** features are enabled.

## Create a legal entity

To create a legal entity, follow these steps.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **New**.
1. In the address setup, set up the address format for Ecuador.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
1. On the **Concept and notes** tab, in the **Legal entity** section, set a field as **Activity**.

> [!NOTE]
> This procedure describes the main settings that are required for localization. You can set other fields as required for other Finance features that you must use.

## Set up tax information

To set up tax information, follow these steps.

1. [Create a document class letter](ltm-core-document-class-letter.md) without a prefix. This document class letter is used in taxpayer and document class configurations.
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
1. Select **New**.
1. In the **Overview** section, in the **Tax ID type** field, enter **RUC** (Unique Taxpayer Registry), which is one of the tax ID types for Ecuador.
1. In the **Format** field, enter **XXXXXXXXXX001** for RUC. Learn more in [Tax ID types for Latin America](ltm-core-tax-id-type.md).
1. Go to **Organization administration** \> **Global address book** \> **Addresses**, select the country or region where the company is set up, and then select **LATAM** to add the RUC tax ID type. Learn more in [Address setup for Latin America](ltm-core-address-setup.md).
1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**, and select **New** to create a record that represents organizations.
1. In the **Type** field, select **Sociedad**. Then add the tax ID type and the document class letter that you created. Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).
1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and then, in the **LATAM** section, configure the following tax and legal information for the legal entity:

    - In the **Taxpayer type field**, select **Sociedad** to represent an organization.
    - In the **Based in country/region** field, select **Ecuador**.
    - In the **Country document type** field, select **RUC**.
    - Complete the country document number, including the tax ID number of the company.
    - In the **Concept and notes** section, in the first field, enter the company activity.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
