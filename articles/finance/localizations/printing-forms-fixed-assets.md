---
# required metadata

title: Unified printing forms for fixed assets (Russia)
description: This topic includes information about fixed asset unified printing forms for Microsoft Dynamics 365 Finance in Russia.
author: v-oloski
ms.date: 04/19/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2019-04-01
ms.dyn365.ops.version: 10.0
---
# Unified printing forms for fixed assets (Russia)

[!include [banner](../includes/banner.md)]


The following unified printing forms for fixed assets are supported.

| **Form code** | **Form name**                                               |
|---------------|-------------------------------------------------------------|
| \#FA-1        | Acceptance report (excluding building, structures)          |
| \#FA-1        | Statement about fixed assets object acceptance-transference |
| \#FA-1        | Transference statement                                      |
| \#FA-1a       | Acceptance report (building, structures)                    |
| \#FA-1a       | Statement about fixed assets object acceptance-transference |
| \#FA-1a       | Transference statement                                      |
| \#FA-2        | Internal transfer slip                                      |
| \#FA-3        | Acceptance-handover statement                               |
| \#FA-4        | Statement about FA writing off (excluding vehicles)         |
| \#FA-4a       | Statement about FA writing off (vehicles)                   |
| \#FA-6        | Fixed asset inventory card                                  |
| \#FA-14       | Equipment acceptance statement                              |

## Set up number sequences for numerating fixed asset forms

To have automatic numbering on printing forms, you need to set up number sequences on the **Fixed asset parameters** page (**Fixed asset (Russia)** \> **Setup** \> **Parameters**, **Document** tab, **Document types** FastTab). You should set up the number sequences for all printing forms that you are going to print.

## Create unified printing forms

Unified printing forms can be created from:

- Fixed asset transactions
- Fixed asset record – only Fixed asset inventory card (#FA-6)
- Transfer history

The following table provides the sources and path for unified printing forms that are located under **Fixed asset (Russia) \> Common \> Fixed assets**.

| **Form code** | **Form name**                                               | **Source**                                                   |
|---------------|-------------------------------------------------------------|--------------------------------------------------------------|
| \#FA-1        | Acceptance report (excluding building, structures)          | **Value models** \> **Transactions** \> **Documents** \> **Documents** |
| \#FA-1        | Statement about fixed assets object acceptance-transference | **History** \> **Transfer** \> **Documents**                         |
| \#FA-1        | Transference statement                                      | **Value models** \> **Transactions** \> **Documents** \> **Documents** |
| \#FA-1a       | Acceptance report (building, structures)                    | **Value models** \> **Transactions** \> **Documents** \> **Documents** |
| \#FA-1a       | Statement about fixed assets object acceptance-transference | **History** \> **Transfer** \> **Documents**                         |
| \#FA-1a       | Transference statement                                      | **Value models** \> **Transactions** \> **Documents** \> **Documents** |
| \#FA-2        | Internal transfer slip                                      | **History** \> **Transfer** \> **Documents**                         |
| \#FA-3        | Acceptance-handover statement                               | **Value models**/ **Transactions** \> **Documents** \> **Documents** |
| \#FA-4        | Statement about FA writing off (excluding vehicles)         | **Value models** \> **Transactions** \> **Documents** \> **Documents** |
| \#FA-4a       | Statement about FA writing off (vehicles)                   | **Value models** \> **Transactions** \> **Documents** \> **Documents** |
| \#FA-6        | Fixed asset inventory card                                  | Highlight the fixed asset record and then select **Documents** \> **Documents**   |
| \#FA-14       | Equipment acceptance statement                              | **Value models** \> **Transactions** \> **Documents** \> **Documents** |

> [!NOTE]  
> It is possible to print Fixed asset inventory card (#FA-6) only when fixed assets are put into operation with the transaction type, **Putting into operation**.

The system saves the information of all printing forms on a special list page. This page can be opened from a fixed asset transaction, transfer history, or from a fixed asset record (\#FA-6 only).

For example, to create a Fixed asset inventory card (\#FA-6):

1. Go to **Fixed asset (Russia)** \> **Common** \> **Fixed assets**.
2. Select the **Fixed assets** tab, and then on the Action Pane, select **Documents** \> **Documents** \> **Inventory card (\#FA6)**.

  ![Selection of FA inventory card.](media/RUS-Selection-of-FA6-inventory-card.png) 

3. Click **New** in the Inventory card (\#FA-6) page list to create the inventory card for the value model.

 ![FA inventory card.](media/RUS-FA6-inventory-card.png)


After the record is created, you can print the unified form from this page list.

> [!NOTE]
> You can use this procedure to create and print other unified forms.

## Print pro forms of unified forms 

All pro forms can be printed from a fixed asset record, when the transaction that corresponds to the document type has not yet been posted. In this case, the document number can be set manually. However, it is not controlled and saved in the system and the data in the pro forms is partially entered.

> [!NOTE]
> It is not possible to print pro form of Fixed asset inventory card (#FA-6).

1. To print pro forms, go to **Fixed asset (Russia)** \> **Common** \> **Fixed assets** and select a fixed asset record.
2. On the **Fixed assets** tab, select **Documents** \> **Documents** and then select the document to print.

## Print unified forms 

You can print existing unified printing forms from different places, including:

- Where the unified printing form was originally created. For more information, see the **Create unified printing forms** section earlier in this topic.
- From a fixed asset record.
- From the Inquiries page.

### Print unified forms from a fixed asset record
To print existing unified printing forms from a fixed asset record, follow these steps:

1. Select the fixed asset record and then on the Action Pane, select **Documents** \> **Documents**. 
2. Select the unified printing form. If you are printing more than one document, the page list for corresponded document type is displayed. 
3. Highlight the record to print, and then select **Print**.

If there is only one unified printing form document for the selected fixed asset, then this document will be output by default.

### Print unified forms from Inquiries

To print documents that are created from inquiries, go to **Fixed assets (Russia)** \> **Inquiries** \> **Documents**. Highlight the document to print and then select **Print**.

![Print unified forms from Inquiries.](media/RUS-Print-unified-forms.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]