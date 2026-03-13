---
title: Update how amounts are displayed on reports and documents
description: Learn how to update how amounts are displayed on reports and other documents for Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-11-30
ms.search.form: Currency
---

# Update how amounts are displayed on reports and documents

[!include [banner](../../includes/banner.md)]

This article explains how to update the display of amounts on reports and other documents for Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia.

For legal entities in Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia, you can set up full names and short names for currency units and subunits. Use these names to change how amounts appear on documents and reports. For example, you can display the amount **LTL 100.20** as **100 Litas 20 Centas**.

## Set up full and short names for currency units and subunits

To set up full and short names for currency units and subunits for a language, complete the following steps:

1. Open the **Currencies** page.
1. Select a currency.
1. On the action pane, select **Declension**.
1. To add a full name and short name for a language, select **New** and enter information in the following fields.

   |             Field                                                           |                        Description                                                                                                                                                                                                                                                |
   |------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                       **Language**                        |                                                                                                               Select the language for the current text.                                                                                                                |
   |    **Singular nominative (Name of units field group)**    |                                                                                       Enter the singular form of the currency. For example, the singular form of Litas is Litas.                                                                                       |
   |     **Plural nominative (Name of units field group)**     | Enter the plural form of the currency. For example, enter Litai. The **Singular genitive** and **Plural genitive** fields are available based on the language that you select in the **Language** field. |
   | **Singular nominative field (Name of parts field group)** |                                                                                                        Enter the singular form of the subunit of the currency.                                                                                                         |
   |     **Plural nominative (Name of parts field group)**     |                                                                                                         Enter the plural form of the subunit of the currency.                                                                                                          |
   |    **Shortcut name of units (Short name field group)**    |                                                                                         Enter the ISO code to identify the currency. For example, enter LTL to identify Litas.                                                                                         |
   |   **Shortcut name for parts (Short name field group)**    |                                                                                               Enter the denomination of the currency subunit. For example, enter Centas.                                                                                               |
   |       **Conjunction 'and' between units and parts**       |                                     Select to print the conjunction “and” between the currency units and unit parts. For example, on invoices or reports, the amount for LTL 100.20 is displayed as 100 Litas and 20 Centas.                                      |
   |       **Gender**       |  Select **Masculine**, **Feminine**, or **Neuter**. This parameter can influence the text of the amount declension that is shown in text of the local language on Cash order. For example, when you set up **Gender** for EUR currency as **Neuter**, the amount 1.01 EUR is written in Czech language on a Cash order as *Jedno euro 01 cent*.  |

1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
