---
title: Set up legal entity and tax information for Nicaragua
description: This article explains how to set up legal entity and tax information for a company located in Nicaragua. 
author: Cpicon85
ms.date: 10/13/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-cpicon
ms.custom: bap-template
---
# Set up legal entity and tax information for Nicaragua

This article explains how to set up a legal entity and the tax information for a company located in Nicaragua who is using the LATAM features available in Dynamics 365 Finance. A legal entity represents the company and contains the tax and legal attributes required for the rest of the LATAM configuration.
Before you begin, go to the **Feature management** workspace, and verify that the feature, **LATAM globalization expansion – Nicaragua** is enabled. If it's not, enable it. When you have verified that the feature is enabled, complete the following steps.

## Create a legal entity
1.  Go to **Organization administration** > **Organizations** > **Legal entities**,  and select **New** to create a new legal entity. Some functionalities are enabled only for Nicaragua. For example, specific tax reports or electronic invoices.
2.  In the address setup, set up the Nicaragua address format using **State** as **Departamento** and **County** as **Municipio**.
3.  Go to **Organization administration** > **Setup** > **LATAM** > **LATAM parameters**.
4.  On the **Concept and notes** tab, set a field in the **Legal entity** section as **Activity**.
 

## Set up tax information

1.  [Create a document class letter](../ltm-core-document-class-letter.md) without a prefix. This document class letter will be used in taxpayer and document class configurations.
2.  Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.
3.  Select **New** and in the **Overview** section, in the **Tax ID type** field, enter **RUC** (Unique Taxpayer Registry), which is one of the tax ID types for Nicaragua.
4.  In the **Format** field, enter **XXXXXXXXXXXXXX**. For more information, see [Tax ID types](../ltm-core-tax-id-type.md).
5.  Go to **Organization administration** > **Global address book** > **Addresses**, select the country where the company is set and select **LATAM** to add the tax ID type **RUC**. For more information, see [Address setup for Latin America](https://learn.microsoft.com/en-us/dynamics365/finance/localizations/ltm-core-address-setup).
6.  Go to **Organization administration** > **Setup** > **LATAM** > **Taxpayer type** and select **New** to create a new record that represents organizations.
7.  In the **Type** field, select **persona juridica** and add the tax ID type and the document class letter you created. For more information, see [Tax payer type](../ltm-core-taxpayer-type.md).
8.  Go to **Organization administration** > **Organizations** > **Legal entities**, and in the **LATAM** section, configure the following entity tax and legal information:
    - Taxpayer type: Select **persona juridica** to represent an organization.
    - Based in country/region: Select **Nicaragua**.
    - Country document type: Select **RUC**.
    - Complete the country document number, including the Tax ID number of the company.
    - In the first field of the **Concept and notes** section, enter the company activity.
