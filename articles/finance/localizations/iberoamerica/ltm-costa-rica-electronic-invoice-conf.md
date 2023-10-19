---
title: Configure electronic invoice parameters for Costa Rica
description: This article explains how to configure the information needed to generate the electronic invoice XML for Costa Rica. 
author: Fhernandez0088
ms.date: 10/18/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure electronic invoice parameters for Costa Rica

[!include [banner](../../includes/banner.md)]
[!include [banner](../../includes/preview-banner.md)]

This article explains how to configure the information needed to generate the electronic invoice XML for Costa Rica. 

## Prerequisites
Before you complete the steps in this article, the following prerequisites must be met:

- The country/region-specific LATAM feature for Costa Rica and the general LATAM feature must be enabled.
- Set the company address to Costa Rica.
  
## Configuration required for Costa Rican electronic invoice
1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax application**2and select **New** to create a new tax application record with the code **CRFE** (Costa Rican electronic invoice). Use this tax application record to assign all the fiscal codification to each element in Dynamics 365 Finance as needed.
2. Go to **Organization administration** > **Organizations** > **Legal entities**.

   1. Select the legal entity you want to work with, and in the **LATAM** section, in the **Concept 1** field, add the activity code. The field label **Concept 1** can be changed from the **Concepts and notes** configuration.
   2. In the **Country identification number** field, enter the company ID number.

3. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**.

   1. Select a record in the list and then select **Tax application**.
   2. In the **Tax application** page, in the **Tax application id** field, enter the ID used for Costa Rican electronic invoicing.
   3. In the **Tax application code** field, enter the code according to the Costa Rican normative.
   4. In the **User defined 2** field, enter the status code of the electronic document code (normal situation, contingency, without internet).
   5. Repeat steps 1-4 for each record on the **Document class** page.

4. Go to **Organization administration > Setup > LATAM > Sales point prefix**.

   1. Select a record in the list and then select **Tax application**.
   2. On the **Tax application** page, in the **Tax application id** field, enter the ID used for Costa Rican electronic invoicing.
   3. In the **Tax application code** field, enter the branch/subsidiary code. Each prefix field on the **Sales point prefix** page should be an emission point according to the invoicing rules for Costa Rica.
   4. Repeat steps 1-3 for each record on the **Sales point prefix** page.

5. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.

   1. Select a record in the list and then select **Tax application**. 
   2. On the **Tax application page**, in the **Tax application id** field, enter the code used for Costa Rican electronic invoicing.
   3. In the **Tax application code** field, enter the code according to the Costa Rican normative.
   4. Repeat steps 1-3 for each record on the **Tax ID type** page.
      
6. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.
7. For each record with an address in Costa Rica, assign the tax codes for Costa Rican states, counties, and cities.
8. Go to **Accounts receivable** > **Payments setup** > **Methods of payment**.

   1. Select a record in the list and then select **Tax application**.
   2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.
   3. For each record in the list, repeat steps 1-2.

9. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**.

   1. Select a record in the list and then select **Tax application**.
   2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.
   3. For each record in the list, repeat steps 1-2.

10. Go to **Product information management** > **Products** > **Released products**.

    1. Select a record in the list and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.
    3. For each record in the list, repeat steps 1-2.

11. Go to **Organization administration** > **Setup** > **Units** > **Units**.

    1. Select a record in the list and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.
    3. For each record in the list, repeat steps 1-2.

12. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.

    1. Select a record in the list and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax application id** field, select the ID used for Costa Rican electronic invoicing.
    3. In the **Income tax code** field, enter the code that identifies the tax according to the Costa Rican normative.
    4. In the **Code regime** field, enter the code that identifies the tax rate according to the Costa Rican normative. 
    5. For each record in the list, repeat steps 1-4..
       
13. Go to **General ledger** > **Currencies** > **Currencies**.

    1. Select a record in the list and then select **Tax application**.
    2. On the **Tax application** page, in the **Tax code** field, enter the code according to the Costa Rican normative.
    3. For each record in the list, repeat steps 1-2.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
