---
title: Configure electronic invoice parameters for Panama
description: Learn how to generate electronic invoices in XML format for Panama, including prerequisites and a process for the required configuration for electronic invoices.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/20/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic invoice parameters for Panama

[!include [banner](../../includes/banner.md)]

This article explains how to generate electronic invoices in XML format for Panama.

## Prerequisites

Before you complete the procedure in this article, the following prerequisites must be met:

- The country/region-specific Latin American (LATAM) feature for Panama and the general LATAM feature must be enabled.
- The company address must be set to Panama.

## Configuration required for Panamanian electronic invoices

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record that has the code **PNFE** (Panamanian electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.
2. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each tax ID in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, create a record.
    3. In the **Tax application id** field, enter the tax ID that's used for Panamanian electronic invoicing.
    4. In the **Tax application code** field, enter the appropriate identification code according to the Panamanian normative.

3. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Taxpayer type**, and follow these steps for each taxpayer type:

    1. In the taxpayer type record, on the Action Pane, select **Tax application**.
    2. On the **Tax application** page, create a record.
    3. In the **Tax application Id** field, select **PNFE**.
    4. In the **Tax application code**, enter the code according to the Panamanian normative.

4. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Fields master List**, and create the following lists. Assign the codes to identify each element of each list according the Panamanian normative.

    - **List field 1:** Electronic document issue types.
    - **List field 2:** Transaction nature types.
    - **List field 3:** Operation destinations.
    - **List field 4:** Sales transaction types.
    - **List field 5:** Transaction types.

    For more information, see [Field list configuration for Latin America](ltm-core-field-master-lists.md).

5. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps for each document class:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, create a register.
    3. In the **Tax application id** field, enter the ID that's used for Panamanian electronic invoicing.
    4. In the **Tax application code** field, enter the codification according to the Panamanian normative.

6. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, and follow these steps for each sales point prefix:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax application id** field, enter the ID that's used for Panamanian electronic invoicing.
    3. In the **Tax application code** field, enter the branch/subsidiary number. Each prefix field on the **Sales point prefix** page should be a sales point number according to the invoicing rules for Panama.

7. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**, and follow these steps:

    1. In the **Country/region** section, follow these steps:

        1. Select **Panama**, and then select **Tax application**.
        2. On the **Tax application** page, create a record.
        3. In the **Tax application Id** field, select **PNFE**.
        4. In the **Tax application code** field, enter the country/region code according to the Panamanian normative.

    2. In the **State/province** section, filter the Panamanian states. Then, for each state record, follow these steps:

        1. Select the state, and then select **Tax application**.
        2. On the **Tax application** page, select **New** to create a record. 
        3. In the **Tax application Id** field select **PNFE**.
        4. In the **Tax application code** field, enter the state/province code according to the Panamanian normative.

    3. In the **County** section, filter the Panamanian counties. Then, for each county record, follow these steps:

        1. Select the county, and then select **Tax application**.
        2. On the **Tax application** page, select **New** to create a record.
        3. In the **Tax application Id** field, select **PNFE**.
        4. In the **Tax application code** field, enter the county code according to the Panamanian normative.
 
    4. In the **City** section, filter the Panamanian cities. Then, for each city record, follow these steps:

        1. Select the city, and then select **Tax application**.
        2. On the **Tax application** page, select **New** to create a record.
        3. In the **Tax application Id** field select **PNFE**.
        4. In the **Tax application code** field, enter the city code according to the Panamanian normative.

8. Go to **Sales and marketing** \> **Setup** \> **Distribution** \> **Terms of delivery**, and follow these steps for each delivery term:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, select **New** to create a register.
    3. In the **Tax application Id** field, enter **PNFE**.
    4. In the **Tax application code** field, enter the code according to the Panamanian normative.

9. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**, and follow these steps for each method of payment:

    1. Select the record, and then, on the Action Pane, select **Tax application**.
    2. On the **Tax application** page, in the **Tax application Id** field, select **PNFE**.
    3. In the **Tax application code** field, enter the code according to the Panamanian normative.

10. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and follow these steps for each term of payment:

    1. Select the record, and then, on the Action Pane, select **Tax application**.
    2. In the **Tax application Id** field, select **PNFE**.
    3. In the **Tax application code** field, enter the code that identifies the payment term according to the Panamanian normative.

11. Go to **Product information management** \> **Products** \> **Released products**, and follow these steps for each item in the list:

    1. Select the record, and then, on the Action Pane, select **Tax application**.
    2. In the **Tax application id** field, select **PNFE**.
    3. In the **Tax application code** field, enter the code according to the Panamanian normative.

12. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**, and follow these steps for each unit:

    1. Select the record, and then select **Tax application**.
    2. In the **Tax application Id** field, select **PNFE**.
    3. In the **Tax application code** field, enter the unit code according to the Panamanian normative.

13. Go to **Accounts receivable** \> **Charges setup** \> **Charges code**, and follow these steps for each charge code:

    1. Select the record, and then, on the Action Pane, select **Tax application**.
    2. In the **Tax application Id** field, select **PNFE**.
    3. In the **Tax application code** field, enter **dPrAcarItem** if the charge is related to the transportation expense. If the charge is related to the insurance expense, enter **dPrSegItem**.

14. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**, and follow these steps for each sales tax code:

    1. Select the record, and then, on the Action Pane, select **Tax application**.
    2. In the **Tax application Id** field, select **PNFE**.
    3. In the **Tax application code** field, enter the code that identifies the tax according to the Panamanian normative.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
