---
title: Set up a legal entity and tax information for Costa Rica
description: Learn how to set up a legal entity and tax information for a company in Costa Rica, including a step-by-step process on creating a legal entity.
author: Cpicon85
ms.author: v-cpicon 
ms.topic: article
ms.date: 10/12/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Set up a legal entity and tax information for Costa Rica

[!include [banner](../../includes/banner.md)]

This article explains how to set up a legal entity and tax information for a company that's located in Costa Rica and is using the Latin American (LATAM) features that are available in Microsoft Dynamics 365 Finance. A legal entity represents the company, and it contains the tax and legal attributes that are required for the rest of the LATAM configuration.

Before you begin, open the **Feature management** workspace, and verify that the **LATAM globalization expansion – Costa Rica** feature is enabled. If it isn't enabled, search for it in the list, and enable it. After you're sure that the feature is enabled, complete the following procedures.

## Create a legal entity

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**, create a legal entity, and set the country for the address to Costa Rica. Some functionality is enabled only for Costa Rica. Examples include specific tax reports or electronic invoices.
2. In the address setup, set up the Costa Rican territorial organization, and configure **State** as **Provincia**, **County** as **Cantón** and **City** as **Distrito**.
3. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
4. On the **Concept and notes** tab, in the **Legal entity** section, set a field to **Activity** to complete that information in the legal entity tax and legal information.

## Set up tax information

1. [Create a document class letter](ltm-core-document-class-letter.md) without a prefix. This document class letter will be used in taxpayer and document class configurations. 
2. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
3. Select **New**, and then, in the **Overview** section, in the **Tax ID type** field, enter **CJ** (Cedula Jurídica), which is one of the tax ID types for Costa Rica.
4. In the **Format** field, enter **XXXXXXXX-X**. For more information, see [Tax ID types for Latin America](ltm-core-tax-id-type.md).
5. Go to **Organization administration** \> **Global address book** \> **Addresses**, select the country where the company is located, and then select **LATAM** to add the **CJ** tax ID type. For more information, see [Address setup for Latin America](ltm-core-address-setup.md).
6. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**, and create a **Persona juridica** record that represents the organization.
7. Add the tax ID type and the document class letter that you created earlier. For more information, see [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).
8. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and then, in the **LATAM** section, enter the following entity tax and legal information:

    - In the **Taxpayer type** field, select **Persona juridica** to represent an organization.
    - In the **Based in country/region** field, select **Costa Rica**.
    - In the **Country document type** field, select **CJ**.
    - Complete the country document number (tax ID number) of the company.
    - In the **Concepts and notes** section, in the first field, enter the company activity.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
