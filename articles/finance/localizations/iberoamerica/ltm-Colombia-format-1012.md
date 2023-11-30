---
title: Format 1012 file for Colombia configuration
description: This article explains how to set up and issue a format 1012 file for Colombia. 
author: Fhernandez0088
ms.date: 11/30/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1012 file for Colombia configuration  

This article explains how to set up and issue a format 1012 file. The format 1012 file includes information about the company investments that must be provided to the tax authority.

## Prerequisites
Before you print the report, the following prerequisites must be met:

- The address that's set for the legal entity must be in Colombia.
- Enable the country-specific LATAM globalization feature and the general LATAM feature.
* Import the following configurations from the Global repository: 
  - LTM Tax Report
  - File format 1012

   For more information, see [Download ER Configuration](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure ER parameters. For more information, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters 

Lookups and conditions are designed so that you can select the combination of documents classification IDs and ledger account numbers that's used in transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**, and select **Reporting configuration**.
2. On the left side, select **LTM Tax Report deployment** > **Format 1012**.
3. On the Action Pane, select **Configurations** > **Application specific parameters** > **Setup**.
4. In the **Lookups** section, select the first lookup that refers to the main account group, **MainAccountGroup**. 
5. In the **Conditions** section, add a line and in the **Lookup result** field, select one of the following options.
    - **1110**: National bank accounts.
    - **1115**: International bank accounts.
    - **1200**: Treasury bonds.
    - **1201**: Deposit certifies.
    - **1202**: Shares value.
    - **1203**: Fiduciary rights.
    - **1204**: Other investments value.
    - **1205**: Crypto investments value.

   These options represent different concepts for the format 1012 file. You can add as many lines as needed.
6. For each condition you add, in the **Label** field, enter the concept number.
7. In the **Main account** field, select the ledger account that represents the concept.

  > [!NOTE]
  > The ledger accounts selected in this configuration must be used in the company transactions included in the report.

.8 In the **Lookups** section, select the second lookup **COMP1012**. This lookup refers to the payment method document class used to post transactions for each concept in the other lookup.
9. In the **Conditions** section, add a line and in the **Lookup result** column, select one of the following concepts:
    - **DEP BCO**: Bank deposits.
    - **EFE CAJA CLP**: Cash national currency.
    - **EFE CAJA USD**: Cash USD.
    - **EFECTIVO**:
    - **EFECTIVO MN**: 
    - **TRB**: Wire transfers.

## Issue a format 1012 file

1. Go to **Tax** > **Inquiries and Reports** > **LATAM** > **Tax reporting**.
2. Select **Format 1012** and select **OK**.
3. Select the date range. 
4. Select **OK**.
