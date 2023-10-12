---
title: Set up a legal entity and tax information for Costa Rica
description: This article explains how to set up a legal entity and the tax information for a company in Costa Rica.
author: Cpicon85
ms.date: 10/12/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon 
ms.custom: bap-template
---

# Set up legal entity and tax information for Costa Rica

[!include [banner](../../includes/banner.md)]

This article explains how to set up a legal entity and the tax information for a company in Costa Rica who is using the LATAM features available in Dynamics 365 Finance. A legal entity represents the company and contains the tax and legal attributes required for the rest of the LATAM configuration.
Before you begin, go to the **Feature management** workspace, and verify that the feature, **LATAM globalization expansion – Costa Rica** is enabled. If it's not, search for it in the list and enable it. When you have verified that the feature is enabled, complete the following steps.

## Create a legal entity
1. Go to **Organization administration** > **Organizations** > **Legal entities**, create a new legal entity and set the country for the address to Costa Rica. Some functionalities are enabled only for Costa Rica. For example, specific tax reports or electronic invoices. 
2. In the address setup, set up the Costa Rican territorial organization and configure State as **Provincia**, County as **Cantón** and City as **Distrito**.
3. Go to **Organization administration** > **Setup** > **LATAM** > **LATAM parameters**.
4. On the **Concept and notes** tab, set a field from the **Legal entity** section to **Activity** to complete that information in the legal entity tax and legal information.

## Set up tax information
1. [Create a document class letter](../ltm-core-document-class-letter.md) without a prefix. This document class letter is used in taxpayer and document class configurations. 
2. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.
3. Select **New** and in the **Overview** section, in the **Tax ID type** field, enter **CJ** (Cedula Jurídica). This is one of the tax ID types for Costa Rica.
4. In the **Format** field, enter **XXXXXXXX-X**. For more information, see [Tax ID types](../ltm-core-tax-id-type.md).
5. Go to **Organization administration** > **Global address book** > **Addresses**, select the country where the company is located, and then select **LATAM** to add the tax ID type **CJ**. For more information, see [Address setup for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/ltm-core-address-setup).
6. Go to **Organization administration** > **Setup** > **LATAM** > **Taxpayer type** and create a new record, **Persona juridica** that represents organization.
7. Add the tax ID type and the document class letter you created earlier. For more information, see [Tax payer type](../ltm-core-taxpayer-type.md).
8. Go to **Organization administration** > **Organizations** > **Legal entities**, and in the **LATAM** section, enter the following entity tax and legal information:
    
   - Taxpayer type: Select **Persona juridica** which represents an organization.
   - Based in country/region: Costa Rica.
   - Country document type: CJ
   - Complete the country document number (Tax ID number) of the company.
   - In teh **Concepts and notes** section, enter the company activity in the first field.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
