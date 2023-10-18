---
title: Configure electronic invoice parameters for Panama
description: This article explains how to configure the information needed to generate the electronic invoice XML for Panama. 
author: Fhernandez0088
ms.date: 10/18/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure electronic invoice parameters for Panama

[!include [banner](../../includes/banner.md)]

This article explains how to configure the information needed to generate the electronic invoice XML for Panama. 

## Prerequisites
Before you complete the steps in this article, the following prerequisites must be met:

- The country/region-specific LATAM feature for Panama and the general LATAM feature must be enabled.
- Set the company address to Panama.
  
## Configuration required for Panamanian electronic invoice
1. Go to **Organization administration** > **Setup** > **LATAM** > **Tax application**, and select **New** to create a new tax application record with the code **PNFE** (Panamanian electronic invoice).
Use this tax application record to assign all the fiscal codification to each element in Dynamics 365 Finance as needed.
2. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type** for each tax id created enter the **Tax application** form, create a new record, complete the field **Tax application id** with the one used for Panamanian electronic invoicing and complete the **Tax application code** with the appropriate identification code according to the Panamanian normative.
3. Go to **Organization administration > Setup > LATAM > Taxpayer type** in each taxpayer type select the **Tax application** button in the action pane to access the form. Create a new record, and in the **Tax application Id** field select “PNFE’’ and in the “Tax application code’’ enter the code according to the Panamanian normative.
4. Go to **Organization administration > Setup > LATAM > Fields master List** create the following lists and assign the codes to identify each element of each list according the Panamanian normative:
    * **List field 1:** electronic document issue types.
    * **List field 2:** transaction nature types.
    * **List field 3:** operation destinies.
    * **List field 4:** sales transaction types.
    * **List field 5:** transaction types.
See [Field list configuration for Latin America]( https://learn.microsoft.com/en-us/dynamics365/finance/localizations/iberoamerica/ltm-core-field-master-lists) article
5. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** and for each document class created go to the **Tax application** form, create a new register and complete the **Tax application id** field with the one used for Panamanian electronic invoicing, complete the **Tax application code** with the codification according to the Panamanian normative.
6. Go to **Organization administration > Setup > LATAM > Sales point prefix** for each sales point prefix created go to the **Tax application** form and complete the **Tax application id** with the one used for Panamanian electronic invoice and the **Tax application code** field with the branch/subsidiary number. Each prefix field from the sales point prefix from should be a sales point number according to the invoicing rules for Panama.
7. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup** go to the Country/region** section select Panama and go to the tax application form. Create a new record, in the **Tax application Id** field select “PNFE” and in the **Tax application code** field enter the country code according to the Panamanian normative.
8. In the **Address setup** go to the **State/province** section, filter the Panamanian states and select each of them, go to the tax application form and create a new record. In the **Tax application Id** field select “PNFE” and in the **Tax application code** field enter the state/province code according to the Panamanian normative.
9. In the **Address setup** go to the **County** section, filter the Panamanian counties and select each of them, go to the tax application form and create a new record. In the **Tax application Id** field select “PNFE” and in the **Tax application code** field enter the county code according to the Panamanian normative.
10. In the **Address setup** go to the **City** section, filter the Panamanian cities and select each of them, go to the tax application form and create a new record. In the **Tax application Id** field select “PNFE” and in the **Tax application code** field enter the city code according to the Panamanian normative.
11. Go to **Sales and marketing > Setup > Distribution > Terms of delivery** for each delivery term created select the **Tax application** button on the action pane to access the form and create a new register completing the **Tax application Id** field with “PNFE” and the **Tax application code** field with the code according to the Panamanian normative.
12. Go to **Accounts receivable** > **Payments setup** > **Methods of payment**. Create the methods that will be used. For each method created select the Tax application button on the action pane and create a new record. In the Tax application Id field select PNFE and in the Tax application code field enter the code that identifies it according to the Panamanian normative.
13. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**. Create the terms that will be used. For each created select the **Tax application** button on the action pane and create a new record. In the **Tax application Id** field select “PNFE” and in the **Tax application code** enter the code that identifies the payment term according to the Panamanian normative.
14. Go to **Product information management** > **Products** > **Released products**. For each item in the list, select the **Tax application** button on the action pane and create a new record. In the **Tax application id** field select “PNFE” and in the **Tax application code** field enter the code according to the Panamanian normative.
15. Go to **Organization administration** > **Setup** > **Units** > **Units**. For each unit created select the **Tax application** button to enter the form and create a new record. In the **Tax application Id** field with “PNFE” and Tax application code with the unit code according to the Panamanian normative.
16. Go to **Accounts receivable > Charges setup > Charges code** for each charge code select the Tax application button on the action pane and create a new record. In the **Tax application Id** field select “PNFE” and in the Tax application code field enter “dPrAcarItem” if the charge is related to the transportation expense or "dPrSegItem" if the charge is related to the insurance expense.
17. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes** for each sales tax code created select the **Tax application button** on the action pane create a new record, in the field **Tax application Id** select “PNFE” and in the field Tax application code enter the code that identifies the tax according to the Panamanian normative.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

