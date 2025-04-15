---
title: Set up a legal entity and tax information for Peru
description: Learn how to set up a legal entity and tax information for a company in Peru.
author: Fhernandez0088
ms.date: 04/15/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.author: v-federicohe
ms.custom: bap-template
---

# Set up a legal entity and tax information for Perú

[!include [banner](../../includes/banner.md)]

This article explains how to use the Latin American (LATAM) features that are available in Microsoft Dynamics 365 Finance to set up a legal entity and tax information for a company that is located in Perú. A legal entity represents the company. It contains the tax and legal attributes that are required for the rest of the LATAM configuration.
Before you begin, open the **Feature management** workspace, and verify that the **LATAM globalization expansion** and **LATAM globalization expansion – Perú** features are enabled. If they aren't enabled, enable them. After you're sure that the features are enabled, complete the following procedures.

## Create a legal entity

To create a legal entity, follow these steps.

1.	Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **New**.
2.	In the address setup, set up the address format for Perú.

> [!NOTE] 
> This procedure describes the main settings that are required for localization. You can set other fields that are required for other Dynamics 365 Finance features that you use.

## Set up tax information

To set up tax information, follow these steps.

1.	[Create a document class letter](ltm-core-document-class-letter.md) without a prefix. This document class letter is used in taxpayer and document class configurations.
2.	Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and select **New**.
3.	In the **Overview** section, in the **Tax ID type** field, enter **RUC** (Unique Taxpayer Registry).
4.	In the **Format** field, enter **XXXXXXXXXXX** for the **RUC** tax ID type. Learn more in [Tax ID types for Latin America](ltm-core-tax-id-type.md).
5.	Go to **Organization administration** \> **Global address book** \> **Addresses**, select the country where the company is located, and then select **LATAM** to add the **RUC** tax ID type. Learn more in [Address setup for Latin America](ltm-core-address-setup.md).
6.	Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**, and select **New** to create a record for organizations.
7.	In the **Type** field, select **Persona juridica**. Then add the tax ID type and the document class letter that you created. Learn more in [Taxpayer types for Latin America](ltm-core-taxpayer-type.md).
8.	Go to **Organization administration** \> **Organizations** \> **Legal entities**.
9.	In the **LATAM** section, configure the following entity tax and legal information:
 - In the **Taxpayer type field**, select **Persona juridica** to represent an organization.
 - In the **Based in country/region** field, select **Perú**.
-  In the **Country document type** field, select **RUC**.
 -  Complete the country document number, including the tax ID number of the company.
