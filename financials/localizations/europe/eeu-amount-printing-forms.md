---
# required metadata

title: Update how amounts are displayed on reports and documents | Microsoft Docs
description: This topic provides information about how to update how amounts are displayed on reports and other documents for Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-16 19:53:21
ms.topic: 
ms.prod: 
ms.service: 
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 264254
ms.assetid: 4c711057-a8c4-49dc-b480-6cbb60900908
ms.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
# ms.industry: 
ms.author: v-elgolu

---

# Update how amounts are displayed on reports and documents

This topic provides information about how to update how amounts are displayed on reports and other documents for Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia.

For legal entities in Estonia, Latvia, Lithuania, Poland, Czech Republic, Hungary, and Russia, you can set up full names and short names for currency units and subunits. These names can be used to transform how amounts are represented on documents and reports. For example: The amount **LTL 100.20** can be displayed as **100 Litas 20 Centas**.

## Set up full and short names for currency units and subunits
To set up full and short names for currency units and subunits for a language, complete the following steps:

1.  Open the **Currencies** page.
2.  Select a currency.
3.  On the Action Pane, click **Declension**.
4.  To add full name and short name for a language, click **New** and complete the following fields.
    |                                                           |                                                                                                                                                                                                                    |
    |-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Field**                                                 | **Description**                                                                                                                                                                                                    |
    | **Language**                                              | Select the language for the current text.                                                                                                                                                                          |
    | **Singular nominative (Name of units field group)**       | Enter the singular form of the currency. For example, the singular form of Litas is Litas.                                                                                                                         |
    | **Plural nominative (Name of units field group)**         | Enter the plural form of the currency. For example, enter Litai. **Note**: The **Singular genitive** and **Plural genitive** fields are available based on the language that you select in the **Language** field. |
    | **Singular nominative field (Name of parts field group)** | Enter the singular form of the subunit of the currency.                                                                                                                                                            |
    | **Plural nominative (Name of parts field group)**         | Enter the plural form of the subunit of the currency.                                                                                                                                                              |
    | **Shortcut name of units (Short name field group)**       | Enter the ISO code to identify the currency. For example, enter LTL to identify Litas.                                                                                                                             |
    | **Shortcut name for parts (Short name field group)**      | Enter the denomination of the currency subunit. For example, enter Centas.                                                                                                                                         |
    | **Conjunction 'and' between units and parts**             | Select to print the conjunction “and” between the currency units and unit parts. For example, on invoices or reports, the amount for LTL 100.20 will be displayed as 100 Litas and 20 Centas.                      |

5.  Click **Save**.


