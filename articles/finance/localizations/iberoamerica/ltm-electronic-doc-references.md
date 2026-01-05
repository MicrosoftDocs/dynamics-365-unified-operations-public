---
title: Configure electronic document references
description: Learn about how to configure and use the Electronic document references feature, including an outline on configuring the electronic document references.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Configure electronic document references

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](../includes/does-not-apply-to.md)]

This article explains how to configure and use the **Electronic document references** feature for Latin America (LATAM). This feature creates a relationship between documents that are used for fiscal purposes.

## Prerequisites

Before you configure the electronic document references, the following prerequisites must be met:

- You must enable the country/region-specific LATAM feature and the general feature.
- The legal entity must have an address in a country/region that's within the LATAM localization.

Before you can post an invoice that has references, you must configure document classes as invoices, credit notes, and debit notes to use in transactions according to the country's/region's requirements.

## Configure the electronic document references

1. Go to **Organization administration** \> **Setup** \> **LATAM** \> **Electronic documents references**.
1. In the **Tax application ID** field, select the tax application ID that was created for the country/region's electronic invoices.
1. In the **Max amount of packing slips** field, enter the total number of packing slips that a document can have as unique references.

## Electronic document references in invoice and packing slip posting

Access the **Electronic document references** feature from the **Invoice posting** page to create a relationship between the transaction that's being posted and a previously posted transaction.

## Post invoices, debit notes, and credit notes that have references

1. Create an invoice, and then go to the appropriate posting page for a sales order, free text invoice, or project invoice.
1. In the **LATAM** section, select the document class and sales point.
1. Select **References**.
1. Select **New** to manually add the references.
1. Follow one of these steps:

    - If you're posting a credit note or debit note, on the Action Pane, in the **General** group, select **Source vouchers** to add previously posted reference documents from a list.
    - If you're posting an invoice from a sales order that has a packing slip, on the Action Pane, in the **General** group, select **Calculate packing slips** to add previously posted reference packing slips from the same sales order.

1. When you've finished adding the references, select **Save**, and then post the transaction.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
