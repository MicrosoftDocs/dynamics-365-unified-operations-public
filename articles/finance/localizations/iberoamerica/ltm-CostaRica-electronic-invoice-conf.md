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
4. Go to **Organization administration** > **Setup** > **LATAM** > **Document class** for each document class used in transactions go to the **Tax application** form and complete the **Tax application** field with the codification for the fiscal document according to the Costa Rican normative and the **User defined 2** field with the status of the electronic document code (normal situation, contingency, without internet).
5. Go to **Organization administration > Setup > LATAM > Sales point prefix** to each sales point in use go to the **Tax application** form and complete the **Tax application code** with the branch/subsidiary codification.
6. Set the **Sales points** name with the codification according to the Costa Rican normative.
7. Go to **Organization administration** > **Setup** > **LATAM** > **Tax ID type** and add the tax codification to each tax id type according to the Costa Rican using the **Tax application** feature in the **Tax application code** field.
8. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup** and for each address located in Costa Rica, assign the tax codes for Costa Rican states, counties, and cities.
9. Go to **Accounts receivable** > **Payments setup** > **Methods of payment**. Create the methods that will be used, and assign each of them the “Tax code” according to the Costa Rican normative using the **Tax application** feature.
10. Go to **Accounts receivable** > **Payments setup** > **Terms of payment**. Create the terms, such as credit or cash, that will be used, and assign each of them the “Tax code” according to the Costa Rican normative using the **Tax application** feature.
11. Go to **Product information management** > **Products** > **Released products**. For each item in the list, add the tax codification according to the Costa Rican normative using the **Tax application** feature in the action menu.
12. Go to **Organization administration** > **Setup** > **Units** > **Units**. For each item in the list, add the tax codification according to the Costa Rican normative using the **Tax application** feature in the action menu.
13. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes** using the **Tax application** feature add to each Costa Rican tax code the codification that identifies the tax type in the field **Income tax code** and the codification that identifies the tax rate in the field **Code regime** according to the Costa Rican normative.
14. Go to **General ledger** > **Currencies** > **Currencies** add the currency codes needed for posting transactions according to the Costa Rican normative in the **Tax application** feature in the tax application code field.

After you complete these steps, you can issue electronic invoices from free text invoices, sales orders, and projects.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
