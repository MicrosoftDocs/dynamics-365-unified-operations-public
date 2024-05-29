---
title: Configure electronic invoice parameters for Costa Rica
description: Learn how to configure the information required to generate the electronic invoice XML for Costa Rica, including an outline on the required configuration.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/18/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic invoice parameters for Costa Rica

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information that's required to generate the electronic invoice XML for Costa Rica.

## Prerequisites

Before you complete the procedure in this article, the following prerequisites must be met:

- The country/region-specific Latin American (LATAM) feature for Costa Rica and the general LATAM feature must be enabled.
- The company address must be set to Costa Rica.

## Configuration required for Costa Rican electronic invoices

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax application**, and select **New** to create a tax application record that has the code **CRFE** (Costa Rican electronic invoice). Use this tax application record to assign the fiscal codification to each element in Microsoft Dynamics 365 Finance as required.
2. Go to **Organization administration** \> **Organizations** \> **Legal entities**, and follow these steps:

    1. Select the legal entity that you want to work with.
    2. In the **LATAM** section, in the **Concept 1** field, add the activity code. The field label **Concept 1** can be changed in the **Concepts and notes** configuration.
    3. In the **Country identification number** field, enter the company ID number.

3. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Document class**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax application id** field, enter the ID that's used for Costa Rican electronic invoicing.
    3. In the **Tax application code** field, enter the code according to the Costa Rican normative.
    4. In the **User defined 2** field, enter the status code of the electronic document code (normal situation, contingency, or without internet).

4. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Sales point prefix**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax application id** field, enter the ID that's used for Costa Rican electronic invoicing.
    3. In the **Tax application code** field, enter the branch/subsidiary code. Each prefix field on the **Sales point prefix** page should be an emission point according to the invoicing rules for Costa Rica.

5. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Tax ID type**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax application id** field, enter the code that's used for Costa Rican electronic invoicing.
    3. In the **Tax application code** field, enter the code according to the Costa Rican normative.

6. Go to **Organization administration** \> **Global address book** \> **Addresses** \> **Address setup**. For each record that has an address in Costa Rica, assign the tax codes for Costa Rican states, counties, and cities.
7. Go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.

8. Go to **Accounts receivable** \> **Payments setup** \> **Terms of payment**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.

9. Go to **Product information management** \> **Products** \> **Released products**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.

10. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.

11. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax application id** field, select the ID that's used for Costa Rican electronic invoicing.
    3. In the **Income tax code** field, enter the code that identifies the tax according to the Costa Rican normative.
    4. In the **Code regime** field, enter the code that identifies the tax rate according to the Costa Rican normative.

12. Go to **General ledger** \> **Currencies** \> **Currencies**, and follow these steps for each record in the list:

    1. Select the record, and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
