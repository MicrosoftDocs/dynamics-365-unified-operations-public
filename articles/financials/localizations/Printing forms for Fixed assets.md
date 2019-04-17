---
# required metadata

title: Unified printing forms for Fixed assets (Russia)
description: This topic includes information about fixed asset unified printing forms for Microsoft Dynamics 365 for Finance and Operations in Russia.
author: Olga Oskina
manager: AnnBe
ms.date: 04/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: v-oloski
ms.search.validFrom: 2019-04-01
ms.dyn365.ops.version: 10.0
---
# Unified printing forms for Fixed assets (Russia)

[!include [banner](../includes/banner.md)]


The following unified printing forms for fixed asset are supported in Dynamics
365 for Finance and Operations:

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

# Set up number sequences for numerating fixed asset forms

For automatic numbering of the printing forms it is necessary to set up number
sequences in the Fixed asset parameters (**Fixed asset (Russia)** \> **Setup**
\> **Parameters**, **Document** tab, **Document types** FastTab). You should set
up the number sequences for all printing forms, which you are going to print.

# Unified printing form creation


Unified printing forms can be created from:

-   Fixed asset transactions

-   Fixed asset record – only Fixed asset inventory card (#FA-6)
   
-   Transfer history

The sources and path for unified printing forms are listed below (**Fixed asset
(Russia) \> Common \> Fixed assets**):

| **Form code** | **Form name**                                               | **Source**                                                   |
|---------------|-------------------------------------------------------------|--------------------------------------------------------------|
| \#FA-1        | Acceptance report (excluding building, structures)          | **Value models**/ **Transactions/ Documents**/ **Documents** |
| \#FA-1        | Statement about fixed assets object acceptance-transference | **History**/ **Transfer/ Documents**                         |
| \#FA-1        | Transference statement                                      | **Value models**/ **Transactions/ Documents**/ **Documents** |
| \#FA-1a       | Acceptance report (building, structures)                    | **Value models**/ **Transactions/ Documents**/ **Documents** |
| \#FA-1a       | Statement about fixed assets object acceptance-transference | **History**/ **Transfer/ Documents**                         |
| \#FA-1a       | Transference statement                                      | **Value models**/ **Transactions/ Documents**/ **Documents** |
| \#FA-2        | Internal transfer slip                                      | **History**/ **Transfer/ Documents**                         |
| \#FA-3        | Acceptance-handover statement                               | **Value models**/ **Transactions/ Documents**/ **Documents** |
| \#FA-4        | Statement about FA writing off (excluding vehicles)         | **Value models**/ **Transactions/ Documents**/ **Documents** |
| \#FA-4a       | Statement about FA writing off (vehicles)                   | **Value models**/ **Transactions/ Documents**/ **Documents** |
| \#FA-6        | Fixed asset inventory card                                  | Highlight Fixed asset record, **Documents**/ **Documents**   |
| \#FA-14       | Equipment acceptance statement                              | **Value models**/ **Transactions/ Documents**/ **Documents** |

> [!NOTE]  
> It is possible to print Fixed asset inventory card (#FA-6) only when a fixed asset are put into operation (there is the transaction with the **Putting into operation** transaction type).

The system saves information of all created printing forms on special list page,
which you may open from a fixed asset transaction, transfer history or from a
fixed asset record (for \#FA-6 only).

For example, to create Fixed asset inventory card (\#FA-6) open **Fixed asset
(Russia) \> Common \> Fixed assets** and click **FIXED ASSETS** tab/
**Documents**/ **Documents/ Inventory card (\#FA6)** on Action Pane:


  ![Selection of FA inventory card](media/RUS-%20Selection%20of%20FA6-%20inventory%20card.png) 

Click **New** in the Inventory card (\#FA-6) page list to create the inventory
card for the value model:

 ![FA inventory card](media/RUS-FA6%20-%20inventory%20card.png)


You may print unified form from this page list after creating the record.

The similar procedure may be applied for creation and printing any other unified
form.

# Printing pro forms of unified forms 

All pro forms can be printed from a fixed asset record, when the transaction,
corresponded to the document type, has not been posted yet. In this case the
document number can be set manually but it is not controlled and saved in the
system and data in pro forms are filled in partially.

> [!NOTE]
> It is not possible to print pro form of Fixed asset inventory card (#FA-6)

To print pro forma highlight a fixed asset record (**Fixed asset (Russia) \>
Common \> Fixed assets**) and click **FIXED ASSETS** tab/ **Documents**/
**Documents** on Action panel and select needed document.

# Printing unified form, created earlier 

A user may print existing unified printing forms from different places:

-   From the place where unified printing form has been created earlier (see
    [Unified printing form creation](#unified-printing-form-creation).

-   From a fixed asset record.

-   From Inquiries.

## Printing unified form from a fixed asset record

To print existing unified printing forms from a fixed asset record it is
necessary to highlight the fixed asset record and click Documents/ documents on
Action Pane and then select needed unified printing form. If quantity of
selected type of unified printing form more than one, the page list for
corresponded document type is displayed. Highlight the needed record and click
**Print**.

If there is only one document of unified printing form for the selected fixed
asset, then this document will be output by default.

## Printing unified form from Inquiries

To print created documents from inquiries, open **Fixed assets (Russia) \>
Inquiries \> Documents** and highlight needed document than click **Print**.

![Print unified forms from Inquiries](media/RUS-Print%20unified%20forms.png)
