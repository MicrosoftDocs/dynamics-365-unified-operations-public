---
title: Vendor sets for Latin America
description: Learn about the vendor set configuration for Latin America, including prerequisites and an outline and process for setting up a vendor set.
author: Fhernandez0088
ms.author: v-federicohe 
ms.topic: how-to
ms.date: 11/18/2025
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Vendor sets for Latin America

[!include [banner](../../includes/banner.md)]

You can define which document classes are allowed in transactions for vendors assigned to this vendor set. Additionally, you can predefine default document classes for each transaction type.

## Prerequisites

Before you set up a vendor set, make sure that you meet the following prerequisites:

- The legal entity has an address in a country or region within the LATAM localization.
- The country or region-specific LATAM feature and the general feature are enabled.
- Document classes that you want to include already exist.

## Set up a vendor set

To set up a vendor set, follow these steps:

1. Go to **Accounts payable** \> **Setup** \> **LATAM** \> **Vendors set** and create a new record.
1. In the **Customers/Vendors set** section, enter a code that identifies the set in the **Customers/Vendors set** field.
1. In the **Description** field, enter a brief description of the set.
1. In the **Authorized vouchers** section, select the document classes for the set.
1. In the **Default document class for documents** section, set the predetermined document classes that are selected by default for each transaction type.

    | Field                | Transaction                                |
    |----------------------|--------------------------------------------|
    | Purchase invoice     | Invoice from a purchase order.             |
    | Purchase credit note | Credit note from a purchase order.         |
    | Packing slip document        | Packing slip from a purchase order.        |
    | Return delivery note voucher | Packing slip from a return purchase order. |
    | Credit journal document class     | Credit movement in an invoice journal.     |
    | Debit journal        | Debit movement in an invoice journal.      |
    | Value document       | Payment line in a journal.                 |

1. On the Action Pane, select **Save**.
