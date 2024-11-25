---
title: Format 1012 file for Colombia configuration
description: Learn how to set up and issue a format 1012 file for Colombia, including an outline on configuring application-specific parameters.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 11/30/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Format 1012 file for Colombia configuration

This article explains how to set up and issue a format 1012 file. The format 1012 file includes information about company investments that must be provided to the tax authority.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The address that's set for the legal entity must be in Colombia.
- Enable the country-specific Latin American (LATAM) globalization feature and the general LATAM feature.
- Import the following configurations from the Global repository:

    - LTM Tax Report
    - File format 1012

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classification IDs and ledger account numbers that's used in transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **Format 1012**.
3. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup that refers to the main account group, **MainAccountGroup**.
5. In the **Conditions** section, add a line. In the **Lookup result** field, select one of the following options:

    - **1110** – National bank accounts.
    - **1115** – International bank accounts.
    - **1200** – Treasury bonds.
    - **1201** – Deposit certifies.
    - **1202** – Shares value.
    - **1203** – Fiduciary rights.
    - **1204** – Other investments value.
    - **1205** – Crypto investments value.

    These options represent different concepts for the format 1012 file. You can add as many lines as you require.

6. For each condition that you add, in the **Label** field, enter the concept number.
7. In the **Main account** field, select the ledger account that represents the concept.

    > [!NOTE]
    > The ledger accounts that are selected in this configuration must be used in the company transactions that are included on the report.

8. In the **Lookups** section, select the second lookup, **COMP1012**. This lookup refers to the payment method document class that's used to post transactions for each concept in the **MainAccountGroup** lookup.
9. In the **Conditions** section, add a line. In the **Lookup result** field, select one of the following concepts:

    - **DEP BCO** – Bank deposits.
    - **EFE CAJA CLP** – Cash national currency.
    - **EFE CAJA USD** – Cash USD.
    - **EFECTIVO**
    - **EFECTIVO MN**
    - **TRB** – Wire transfers.

## Issue a format 1012 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **Format 1012**.
3. Select **OK**.
4. Select the date range. 
5. Select **OK**.
