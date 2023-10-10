---
title: Configure electronic invoice parameters for Chile
description: This topic provides information about the configuration needed to generate the electronic invoice XML for Chile. 
author: Fhernandez0088
ms.date: 10/10/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---
# Configure electronic invoice parameters for Chile
This article explains the configuration needed to be done by the user to add the information that the Chilean electronic invoice will contain.
## Prerequisites
* Enable LATAM Globalization feature and country specific LATAM feature for Chile.
* Set the company address to Chile.
## Configuration required for Chilean electronic invoice
The following steps go through the information that the XML tags requires in that specific order.
1. Go to **Organization administration > Setup > LATAM > Tax application**, for e-invoicing purposes create a tax application record with the code CHFE (Chilean electronic invoice).
Use this tax application record to assign all the fiscal codification to each element in finance as needed.
2. Go to **Organization administration > Organizations > Legal entities** in the **LATAM** section complete the **Country identification number** field with the complete RUT number.
3. Go to **Organization administration > Organizations > Legal entities** in the **LATAM** section complete the **Concept 1** field with the business activity known as “Giro emisor”. The title of this field can be changed from **Concept and notes** configuration in **LATAM parameters**.
4. Go to **Organization administration > Organizations > Legal entities** in the contact information add a telephone number and a mail and set them as primary.
5. Go to **Organization administration > Organizations > Legal entities** in the **Statutory reporting** section complete the field Branch/Subsidiary with the code for the business activity according to the Chilean normative.
6. Go to **Organization administration > Setup > LATAM > Document class** select the **Tax application** button on the action menu and assign a tax code to each document class that will be used according to the updated Chilean normative. Also add the letter “R” to the credit notes and debit notes to set mandatory the references documents when posting those type of transactions.
7. Go to **Accounts receivable > Payments setup > Terms of payment** create the terms of payments for cash payment, credit and donation. Assign a tax code to the terms of payment according the Chilean normative.
8. Go to ** Organization administration > Setup > LATAM > Document class sales point** assign a document number sequence to the document class sales point configuration. This will be used as document number for the fiscal document.
9. Go to **Organization administration > Setup > LATAM > Sales point prefix** set the tax application code to the sales points that are used with the codification that the fiscal authority assigned to it.
10. Go to **Accounts receivable > Customers > All customers** in the **LATAM** section complete the **Country identification number** with the RUT of the client.
11. Go to **Accounts receivable > Customers > All customers** add a business classification to the customers in use with the business activity. In the General menu from the action pane, select the business activity to add this code to each customer.
12. Go to **Organization administration > Setup > LATAM > Document class** Configure the additional data section fields to match the information requirements for electronic invoicing:
Remission document classes should have the **Free text 1** and **Free text 3** required and for the driver’s RUT and driver’s name respectively. 
13. Go to **Sales and marketing > Setup > Distribution > Reasons for delivery** and set the options for selling modes according to the Chilean normative stablished by the customs office. It is used only for export documents.
14. Go to **Sales and marketing > Setup > Distribution > Terms of delivery** and set the options for selling clauses according to the Chilean normative (FOB, CIF, etc.).
15. Go to **Sales and marketing > Setup > Distribution > Modes of delivery** and set the options for transportation routes according to the Chilean normative (aerial, terrestrial, maritime, etc.).
16. Go to **General ledger > Currencies > Currencies** and set on each currency used in transactions the **Tax application** code with currency indicator according to the electronic invoice schema (PESO CL, DOLAR USA, EURO, etc.).	
17. Go to **Organization administration > Setup > LATAM > Electronic documents references** set the **Tax application id** created for electronic invoicing for Chile (CHFE) and set the limit to trigger the global indicator according to the Chilean normative (20). This will trigger the limit for references in one document and make a summary of the references.
18. Go to **Organization administration > Setup > Units > Units** and configure the tax application code for the units that will be used according to the Chilean customs office normative.
19. Go to **Organization administration > Setup > LATAM > Field master list** and create the following field lists:
**Field list 3**: add elements with the ports of shipment and their codes according to the Chilean normative.
**Field list 4**: add elements with the landing ports and their codes according to the Chilean normative.
**Field list 5**: add elements with the options for transport type indicators and their codes according to the Chilean normative.
**Field list 7**: add the elements with the options for remission type and their codes according to the Chilean normative.
**Field list 8**: add elements with the options for products transfer type and their codes according to the Chilean normative.
Once these steps are completed the user will be able to issue electronic invoices from free text invoices, sales orders, and projects.
