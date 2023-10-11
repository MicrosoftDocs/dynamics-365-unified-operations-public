---
title: Configure electronic invoice parameters for Costa Rica
description: This topic provides information about the configuration needed to generate the electronic invoice XML for Costa Rica. 
author: Fhernandez0088
ms.date: 10/10/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---
# Configure electronic invoice parameters for Costa Rica
This article explains the configuration needed to be done by the user to add the information that the Costa Rican electronic invoice will contain.
## Prerequisites
* Enable LATAM Globalization feature and country specific LATAM feature for Costa Rica.
* Set the company address to Costa Rica.
## Configuration required for Costa Rican electronic invoice
1. Go to **Organization administration > Setup > LATAM > Tax application**, for e-invoicing purposes create a tax application record with the code CRFE (Costa Rican electronic invoice).
Use this tax application record to assign all the fiscal codification to each element in finance as needed.
2. Go to **Organization administration > Organizations > Legal entities** in the LATAM section complete the field **Concept 1** with the activity code. The field label **Concept 1** can be changed from the **Concepts and notes** configuration.
3. Go to **Organization administration > Organizations > Legal entities** in the LATAM section complete the field **Country identification number** with the company ID number.
4. Go to **Organization administration > Setup > LATAM > Document class** for each document class used in transactions go to the **Tax application** form and complete the **Tax application** field with the codification for the fiscal document according to the Costa Rican normative and the **User defined 2** field with the status of the electronic document code (normal situation, contingency, without internet).
5. Go to ** Organization administration > Setup > LATAM > Sales point prefix** to each sales point in use go to the **Tax application** form and complete the **Tax application code** with the branch/subsidiary codification.
6. Set the **Sales points** name with the codification according to the Costa Rican normative.
7. Go to **Organization administration > Setup > LATAM > Tax ID type** add the tax codification to each tax id type according to the Costa Rican using the **Tax application** feature in the **Tax application code** field.
8. Go to **Organization administration > Global address book > Addresses > Address setup** and assign the tax codes for Costa Rican states, counties, and cities.
9. Go to ** Accounts receivable > Payments setup > Methods of payment** create the methods that will be used and assign each of them the “Tax code” according to the Costa Rican normative using the **Tax application** feature.
10. Go to ** Accounts receivable > Payments setup > Terms of payment** create the terms (credit, cash, etc.) that will be used and assign each of them the “Tax code” according to the Costa Rican normative using the **Tax application** feature.
11. Go to ** Product information management > Products > Released products** add to each product/service the tax codification according to the Costa Rican normative using the **Tax application** feature in the action menu.
12. Go to ** Organization administration > Setup > Units > Units** add to each unit the tax codification according to the Costa Rican normative using the **Tax application** feature in the action menu.
13. Go to ** Tax > Indirect taxes > Sales tax > Sales tax codes** using the **Tax application** feature add to each Costa Rican tax code the codification that identifies the tax type in the field **Income tax code** and the codification that identifies the tax rate in the field **Code regime** according to the Costa Rican normative.
14. Go to **General ledger > Currencies > Currencies** add the currency codes needed for posting transactions according to the Costa Rican normative in the **Tax application** feature in the tax application code field.

Once these steps are completed the user will be able to issue electronic invoices from free text invoices, sales orders, and projects.
