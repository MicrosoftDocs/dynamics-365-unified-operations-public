---
title: Configure electronic invoice parameters for Panama
description: This article explains how to generate the electronic invoice in XML format for Panama. 
author: Fhernandez0088
ms.date: 10/18/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure electronic invoice parameters for Panama

[!include [banner](../../includes/banner.md)]

This article explains how to generate the electronic invoice in XML format for Panama. 

## Prerequisites
Before you complete the steps in this article, the following prerequisites must be met:

- The country/region-specific LATAM feature for Panama and the general LATAM feature must be enabled.
- Set the company address to Panama.
  
## Configuration required for Panamanian electronic invoice
1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax application**.
 
   1. Select **New** to create a new tax application record with the code **PNFE** (Panamanian electronic invoice). Use this tax application record to assign all the fiscal codification to each element in Dynamics 365 Finance as needed.

2. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type**.

   1. For each tax ID in the list, select the record and then select **Tax application**.
   2. On the **Tax application** page, create a new record, and in the **Tax application id** field enter the tax ID used for Panamanian electronic invoicing.
   3. In the **Tax application code** field, enter the appropriate identification code according to the Panamanian normative.

3. Go to **Organization administration** > **Setup** > **LATAM** > **Taxpayer type**.

   1. In each taxpayer type record, on the Action Pane, select **Tax application**.
   2. On the **Tax application** page, create a new record, and in the **Tax application Id** field, select **PNFE**.
   3. In the **Tax application code**, enter the code according to the Panamanian normative.
    
4. Go to **Organization administration** > **Setup** > **LATAM** > **Fields master List**.

   1. Create the following lists and assign the codes to identify each element of each list according the Panamanian normative:

      - **List field 1:** Electronic document issue types.
      - **List field 2:** Transaction nature types.
      - **List field 3:** Operation destinations.
      - **List field 4:** Sales transaction types.
      - **List field 5:** Transaction types.

   For more details, see [Field list configuration for Latin America](ltm-core-field-master-lists.md).

5. Go to **Organization administration** > **Setup** > **LATAM** > **Document class**.

   1. For each document class, select the record and then select **Tax application**.
   2. On the **Tax application** page, create a new register, and in the **Tax application id** field, enter the ID used for Panamanian electronic invoicing.
   3. In the **Tax application code** field, enter the codification according to the Panamanian normative.
      
6. Go to **Organization administration** > **Setup** > **LATAM** > **Sales point prefix**.

   1. For each sales point prefix, select the record and then select **Tax application**.
   2. On the **Tax application** page, in the **Tax application id** field, enter the ID used for Panamanian electronic invoice.
   3. In the **Tax application code** field, enter the branch/subsidiary number. Each prefix field in the **Sales point prefix** page should be a sales point number according to the invoicing rules for Panama.

7. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.

   1. In to the **Country/region** section, select **Panama** and then select **Tax application**.
   2. On the **Tax application** page, create a new record and in the **Tax application Id** field, select **PNFE**.
   3. In the **Tax application code** field, enter the country code according to the Panamanian normative.
   4. On the **Address setup**, in the **State/province** section, filter the Panamanian states.
   5. Select a state and then select **Tax application**.
   6. On the **Tax application** page, select **New** to create a new record.
   7. In the **Tax application Id** field select **PNFE**, and in the **Tax application code** field, enter the state/province code according to the Panamanian normative.
   8. Repeat steps 5-7 for each state record.

8. On the **Address setup** page, in the **County** section, filter the Panamanian counties.
    
   1. Select a county and then select **Tax application**.
   2. On the **Tax application** page, select **New** to create a new record.
   3. In the **Tax application Id** field select **PNFE**, and in the **Tax application code** field, enter the county code according to the Panamanian normative.
   4. Repeat steps 1-3 for each state record
 
9. On the **Address setup** page, in the **City** section, filter the Panamanian cities.

    1. Select a city and then select **Tax application**.
    2. On the **Tax application** page, select **New** to create a new record.
    3. In the **Tax application Id** field select **PNFE**, and in the **Tax application code** field, enter the city code according to the Panamanian normative.
    4. Repeat steps 1-3 for each city record.

10. Go to **Sales and marketing** > **Setup** > **Distribution** > **Terms of delivery**.

    1. For each delivery term, select a record and then select **Tax application**.
    2. On the **Tax application** page, select **New** to create a new register.
    3. In the **Tax application Id** field enter **PNFE**.
    4. In the **Tax application code** field, enter the code according to the Panamanian normative.

11. Go to **Accounts receivable** > **Payments setup** > **Methods of payment**.

    1. For each method of payment, select the record and on the Action Pane, select **Tax application**.
    2. On the **Tax application** page, in the **Tax application Id** field, select **PNFE**.
    3. In the **Tax application code** field enter the code according to the Panamanian normative.
    
12. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**.

    1. For each term of payment, select the record and on the Action Pane, select **Tax application**.
    2. In the **Tax application Id** field select **PNFE**.
    3. In the **Tax application code** enter the code that identifies the payment term according to the Panamanian normative.
      
13. Go to **Product information management** > **Products** > **Released products**.

    1. For each item in the list, select the record and on the Action Pane, select **Tax application**.
    2. In the **Tax application id** field, select **PNFE**.
    3. In the **Tax application code** field, enter the code according to the Panamanian normative.
  
14. Go to **Organization administration** > **Setup** > **Units** > **Units**.

    1. For each unit, select the record and then select **Tax application**.
    2. In the **Tax application Id** field, select with **PNFE**.
    3. In the **Tax application code** field, enter the unit code according to the Panamanian normative.
     
15. Go to **Accounts receivable > Charges setup > Charges code**.

    1. For each charge code, select the record and on the Action Pane, select **Tax application**.
    2. In the **Tax application Id** field select **PNFE**.
    3. In the **Tax application code** field enter **dPrAcarItem** if the charge is related to the transportation expense. If the charge is realted to the insurance expense, enter **dPrSegItem**.

16. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.

    1. For each sales tax code, select the record and on the Action Pane, select **Tax application**.
    2. In the **Tax application Id** field select **PNFE**
    3. In the **Tax application code** field, enter the code that identifies the tax according to the Panamanian normative.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

