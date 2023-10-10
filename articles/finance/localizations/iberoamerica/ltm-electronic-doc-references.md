---
title: Configure electronic documents references
description: This topic provides information about how to configure the electronic documents references form and how to use the feature. 
author: Fhernandez0088
ms.date: 10/10/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---
# Configure electronic documents references
This article explains how to configure and how works the electronic document references feature for LATAM. This feature can create relations between documents that are useful for fiscal purposes.
## Prerequisites
* Enable the Globalization feature and the country specific feature for the Latin American country.
* Set the country address for the legal entity to a country supported by the LATAM Globalization localization.
## Configure the electronic documents references
1. Go to **Organization administration > Setup > LATAM > Electronic documents references**.
2. Complete the field **Tax application id** with the tax application id created for the country electronic invoice in use.
3. Complete the field **Max amount of packing slips** with the total amount of packing slips that a document can have as unique references.
## Use reference button in invoice and packing slip posting
The references feature can be accessed from the invoice posting form to create a relation between the transaction that is being posted and another one previously created.
## Prerequisites 
* Configure **Document classes** as invoices, credit notes and debit notes according to the country normative to use in transactions.
## Invoices, Debit notes and Credit notes posting with references
1. Create an invoice and go to the posting form from sales orders, free text invoice or project invoice.
2. In the LATAM section from the posting form select the document class, and sales point configured previously.
3. Select the **References** button in the LATAM section.
4. Select **New** from the menu to add the references manually.
5. When posting a credit note or debit note in the general section from the action pane select **Source vouchers** to add reference documents that are already posted from a list.
6. When posting an invoice from a sales order with packing slip in the general section from the action pane select **Calculate packing slips** to add reference packing slips that are already posted from the same sales order.
7. After adding the references select **Save** and go back to the posting form.
8. Post the transaction.
