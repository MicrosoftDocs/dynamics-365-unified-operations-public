---
title: Update how amounts are displayed on reports and documents
description: Learn about how to update how amounts are displayed on reports and other documents for Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/24/2024
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.search.validFrom: 2016-11-30
ms.search.form: Currency
ms.dyn365.ops.version: Version 1611
---

# Update how amounts are displayed on reports and documents

[!include [banner](../../includes/banner.md)]

This article provides information about how to update how amounts are displayed on reports and other documents for Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia.

For legal entities in Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia, you can set up full names and short names for currency units and subunits. These names can be used to transform how amounts are represented on documents and reports. For example, the amount **LTL 100.20** can be displayed as **100 Litas 20 Centas**.

## Set up full and short names for currency units and subunits
To set up full and short names for currency units and subunits for a language, complete the following steps:

1. Open the **Currencies** page.
2. Select a currency.
3. On the Action Pane, select **Declension**.
4. To add full name and short name for a language, select **New** and enter information the following fields.

   |             Field                                                           |                        Description                                                                                                                                                                                                                                                |
   |------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                       <strong>Language</strong>                        |                                                                                                               Select the language for the current text.                                                                                                                |
   |    <strong>Singular nominative (Name of units field group)</strong>    |                                                                                       Enter the singular form of the currency. For example, the singular form of Litas is Litas.                                                                                       |
   |     <strong>Plural nominative (Name of units field group)</strong>     | Enter the plural form of the currency. For example, enter Litai. <strong>Note</strong>: The <strong>Singular genitive</strong> and <strong>Plural genitive</strong> fields are available based on the language that you select in the <strong>Language</strong> field. |
   | <strong>Singular nominative field (Name of parts field group)</strong> |                                                                                                        Enter the singular form of the subunit of the currency.                                                                                                         |
   |     <strong>Plural nominative (Name of parts field group)</strong>     |                                                                                                         Enter the plural form of the subunit of the currency.                                                                                                          |
   |    <strong>Shortcut name of units (Short name field group)</strong>    |                                                                                         Enter the ISO code to identify the currency. For example, enter LTL to identify Litas.                                                                                         |
   |   <strong>Shortcut name for parts (Short name field group)</strong>    |                                                                                               Enter the denomination of the currency subunit. For example, enter Centas.                                                                                               |
   |       <strong>Conjunction 'and' between units and parts</strong>       |                                     Select to print the conjunction “and” between the currency units and unit parts. For example, on invoices or reports, the amount for LTL 100.20 will be displayed as 100 Litas and 20 Centas.                                      |
   |       <strong>Gender</strong>       |  Select **Masculine**, **Feminine**, or **Neuter**. This parameter can influence the text of the amount declension that is shown in text of the local language on Cash order. For example, when you set up **Gender** for EUR currency as **Neuter**, the amount 1,01 EUR is written in Czech language on a Cash order as *Jedno euro 01 cent*.  |

5. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
