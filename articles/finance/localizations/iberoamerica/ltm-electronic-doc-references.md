---
title: Configure electronic documents references
description: This article provides information about how to configure and use the Electronic documents references feature. 
author: Fhernandez0088
ms.date: 10/10/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Configure electronic documents references

[!include [banner](../../includes/banner.md)]

This article explains how to configure and use the **Electronic document references** feature for LATAM. This feature creates a relationship between documents that are used for fiscal purposes.

## Prerequisites
Before you configure the electronic document references, the following prerequisites must be met: 

- You must enable the country/region-specific LATAM feature and the general feature.
- The legal entity must have an address in a country/region that's within the LATAM localization.

## Configure the electronic documents references

1. Go to **Organization administration** > **Setup** > **LATAM** > **Electronic documents references**.
2. In the **Tax application ID** field, select the tax application ID created for the country's electronic invoices.
3. In the **Max amount of packing slips** field, enter the total amount of packing slips that a document can have as unique references.

## Electronic document references in invoice and packing slip posting

Access the **Electronic document references** feature from the **Invoice posting** page to create a relationship between the transaction that's being posted and a previously posted transaction.

## Prerequisites 
Before you can post an invoice with references, you need to configure **Document classes** as invoices, credit notes, and debit notes to use in transactions according to the country requirements.

## Post invoices, debit notes, and credit notes with references

1. Create an invoice and go to the appropriate posting page for a sales orders, free text invoice, or project invoice.
2. In the **LATAM** section, select the document class, and sales point.
3. Select **References**.
4. Select **New** to manually add the references.
5. If you're posting a credit note or debit note, on the Action Pane, in the **General** section, select **Source vouchers** to add reference documents that are already posted from a list.
6. If you're posting an invoice from a sales order with a packing slip, on the Action Pane, in the **General** section, select **Calculate packing slips** to add reference packing slips that are already posted from the same sales order.
7. After you add the references, select **Save** and then post the transaction.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
