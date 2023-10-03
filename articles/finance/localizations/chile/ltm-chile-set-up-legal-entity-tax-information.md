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
1. Go to **Organization administration** > **Organizations** > **Legal entities** and select **New** to create a new legal entity.
2. Set the company address to Chile. Some functionalities are enabled only for Chile. For example, specific tax reports or electronic invoices. 
3. Create and configure a geographical structure according to the company address using States as “Regiones”, Counties as “Provincias”, Cities as “Comunas”.
4. Go to **Organization administration** > **Setup** > **LATAM** > **LATAM parameters**.
5. On the **Concept and notes** tab, configure the labels required.

## Set up tax information

1. [Create a document class letter](../ltm-core-document-class-letter.md) without a prefix. This document class letter will be used in taxpayer and document class configurations. 
2. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.
3. Select **New** and in the **Overview** section, in the **Tax ID type** field, enter **RUT** (Registro unico tributario).
4. In the **Format** field, enter **XXXXXXXX-X**. For more information, see [Tax ID types](../ltm-core-tax-id-type.md).
5. Go to **Organization administration** > **Global address book** >**Addresses** and select the country where the company is located.
6. Select **LATAM** and in the **Tax ID type** field, enter **RUT**. To learn more, see, [Address setup for Latin America](../iberoamerica/ltm-core-address-setup.md).
7. Go to **Organization administration** > **Organizations** **Legal entities** and in the **LATAM** section, configure the following entity tax and legal information:
    * Taxpayer type: select “Persona juridica” represents an organization.
    * Based in country/region: Chile.
    * Country document type: RUT (Registro Unico Tributario).
    * Complete the country document number RUT of the company.
    * Complete the first field from the “Concept and notes” section with the company activity.
You will find similar structure for customers and vendor LATAM configuration.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
