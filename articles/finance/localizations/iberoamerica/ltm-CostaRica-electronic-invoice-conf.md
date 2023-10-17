---
title: Configure electronic invoice parameters for Costa Rica
description: This article explains how to configure the information needed to generate the electronic invoice XML for Costa Rica. 
author: Fhernandez0088
ms.date: 10/10/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure electronic invoice parameters for Costa Rica

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information needed to generate the electronic invoice XML for Costa Rica. 

## Prerequisites
Before you complete the steps in this article, the following prerequisites must be met:

- The country/region-specific LATAM feature for Costa Rica and the general LATAM feature must be enabled.
- Set the company address to Costa Rica.
  
## Configuration required for Costa Rican electronic invoice
1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax application**, and select **New** to create a new tax application record with the code **CRFE** (Costa Rican electronic invoice).
Use this tax application record to assign all the fiscal codification to each element in Dynamics 365 Finance as needed.
2. Go to **Organization administration** > **Organizations** > **Legal entities**, Select the legal entity you want to work with, and in the **LATAM** section, in the **Concept 1** field, add the activity code. The field label **Concept 1** can be changed from the **Concepts and notes** configuration.
3. In the **Country identification number** field, enter the company ID number.
4. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** and for each document class created go to the **Tax application** form, create a new register and complete the **Tax application id** field with the one used for Costa Rican electronic invoicing, complete the **Tax application code** with the codification according to the Costa Rican normative and the **User defined 2** field with the status code of the electronic document code (normal situation, contingency, without internet).
5. Go to **Organization administration > Setup > LATAM > Sales point prefix** for each sales point prefix created go to the **Tax application** form and complete the **Tax application id** with the one used for Costa Rican electronic invoice and the **Tax application code** field with the branch/subsidiary codification. Each prefix field from the sales point from should be an emission point according to the invoicing rules for Costa Rica.
6. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type** for each tax id created enter the **Tax application** form, create a new record, complete the field **Tax application id** with the one used for Costa Rican electronic invoicing and complete the **Tax application code** with the appropriate code according to the Costa Rican normative.
7. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup** and for each address located in Costa Rica, assign the tax codes for Costa Rican states, counties, and cities.
8. Go to **Accounts receivable** > **Payments setup** > **Methods of payment**. Create the methods that will be used and assign each of them the “Tax code” in the **Tax application** form according to the Costa Rican normative.
9. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**. Create the terms, such as credit or cash, that will be used, and assign to each of them the “Tax code” using the **Tax application** form.
10. Go to **Product information management** > **Products** > **Released products**. For each item in the list, add the tax codification according to the Costa Rican normative using the **Tax application** form in the action menu.
11. Go to **Organization administration** > **Setup** > **Units** > **Units**. For each item in the list, add the tax codification according to the Costa Rican normative using the **Tax application** feature in the action menu.
12. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes** for each sales tax code created select the Tax application button on the action pane to access the Tax application form, create a new record and complete the fields:
    * **Tax application id**: select from the drop down list the one used for Costa Rican electronic invoicing.
    * **Income tax code**: enter the code that identifies the tax according to the Costa Rican normative.
    * **Code regime**: enter the code that identifies the tax rate according to the Costa Rican normative.
13. Go to **General ledger** > **Currencies** > **Currencies**, for each currency to be used go to the **Tax application** form in the action pane, create a new record and complete the field Tax application id with the one used for Costa Rican electronic invoices add the field **Tax application code** with the currency code according to the Costa Rican normative.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
