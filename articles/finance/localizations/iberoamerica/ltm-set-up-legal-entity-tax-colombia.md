---
title: Set up legal entity and tax information for Colombia
description: Learn how to set up legal entity and tax information for a company in Colombia, including a step-by-step process for creating a legal entity.
author: Cpicon85
ms.author: v-cpicon
ms.topic: article
ms.date: 12/08/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Set up legal entity and tax information for Colombia

[!include [banner](../../includes/banner.md)]

This article explains how to set up a legal entity and tax information for a company in Colombia that's using the Latin American (LATAM) features that are available in Microsoft Dynamics 365 Finance. A legal entity represents the company, and it contains the tax and legal attributes that are required for the rest of the LATAM configuration.

Before you begin, open the **Feature management** workspace, and verify that the **LATAM globalization expansion – Colombia** feature is enabled. If it isn't enabled, enable it. After you've verified that the feature is enabled, complete the following procedures.

## Create a legal entity

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Create a legal entity to use as the company, and set the address to Colombia. Some functionality is enabled only for Colombia. Examples include specific tax reports or electronic invoices.
3. In the address setup, set up the address format for Colombia by using **State** as **Departamento** and **County** as **Municipio**.
4. Go to **Organization administration** \> **Setup** \> **LATAM** \> **LATAM parameters**.
5. On the **Concept and notes** tab, set a concept field from the **Legal entity** section as **Activity** to complete that information in the legal entity tax and legal information.

## Set up tax information

1. [Create a document class letter](ltm-core-document-class-letter.md) without a prefix. This document class letter is used in taxpayer and document class configurations.
2. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**.
3. Select **New**, and then, in the **Overview** section, in the **Tax ID type** field, enter **NIT** (tax identification number), which is one of the tax ID types for Colombia.
4. In the **Format** field, enter **XXX.XXX.XXX-X**. For more information, see [Tax ID types for Latin America](ltm-core-tax-id-type.md).
5. Go to **Organization administration** \> **Global address book** \> **Addresses**, select the country where the company is set, and then select **LATAM** to add the **NIT** tax ID type. For more information, see [Address setup for Latin America](ltm-core-address-setup.md).
6. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**, and create a record that represents organizations.
7. In the **Type** field, select **Persona juridica**. Then add the tax ID type and the document class letter that you created. For more information, see [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).
7. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and then, in the **LATAM** section, configure the following entity tax and legal information:

    - In the **Taxpayer type** field, select **Persona juridica** to represents an organization.
    - In the **Based in country/region** field, select **Colombia**.
    - In the **Country document type** field, select **NIT**.
    - Complete the country document number, including the tax ID number of the company.
    - In the **Concept and notes** section, in the first field, enter the company activity.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
