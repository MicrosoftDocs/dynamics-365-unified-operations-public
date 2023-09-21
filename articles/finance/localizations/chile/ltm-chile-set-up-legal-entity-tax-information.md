---
title: Set up legal entity and tax information 
description: This article explains how to set up legal entity and tax information for a Chilean company. 
author: Fhernandez0088
ms.date: 09/21/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Set up legal entity and tax information

[!include [banner](../../includes/banner.md)]

This article explains how to set up a legal entity and the tax information for a company in Chile who is using the LATAM features available in Dynamics 365 Finance. A legal entity represents the company and contains the tax and legal attributes required for the rest of the LATAM configuration.

Before you begin, go to the **Feature management** workspace and verify that the feature, **LATAM globalization expansion - Chile** is enabled. If it's not, enable it. When you have verified that the feature is enabled, complete the following steps.

## Create a legal entity
1. Go to **Organization administration** > **Organizations** > **Legal entities**, and set the company address to Chile. Some functionalities are enabled only for Chile. For example, specific tax reports or electronic invoices. 
2. Create and configure a geographical structure according to the company address using States as “Regiones”, Counties as “Provincias”, Cities as “Comunas”.
3. Go to **Organization administration** > **Setup** > **LATAM** > **LATAM parameters**.
4. On the **Concept and notes** tab, configure the labels required.

## Set up tax information

1. [Create a document class letter](../ltm-core-document-class-letter.md) without a prefix. This document class letter will be used in taxpayer and document class configurations. 
2. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.
3. Select **New** and in the **Overview** section, in the **Tax ID type** field, enter **RUT** (Registro unico tributario).
4. In the **Format** field, enter **XXXXXXXX-X**. For more information, see [Tax ID types](../ltm-core-tax-id-type.md).
5. Return to the **Legal entities** page and select the legal entity you created earlier. On the **Address** tab, add the tax ID type **RUT**. 
6. Create a taxpayer type that represents organizations “Persona juridica” and add the tax ID type created and the document class letter created. For more information, see [Tax payer type](../ltm-core-taxpayer-type.md).
7. Configure the entity LATAM Tax and legal information:
    * Taxpayer type: select “Persona juridica” represents an organization.
    * Based in country/region: Chile.
    * Country document type: RUT (Registro Unico Tributario).
    * Complete the country document number RUT of the company.
    * Complete the first field from the “Concept and notes” section with the company activity.
You will find similar structure for customers and vendor LATAM configuration.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
