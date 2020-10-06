---
# required metadata

title: How to clean up TaxDocument JSON table 
description: Along with the system running, more and more data will be produced, and the Database size will also become larger and larger. 
To release the database space, some old data may be cleaned up.
author: prabhatb
manager: EricWang
ms.date: 10/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 2020-09-01
ms.dyn365.ops.version: 10.0.14

---

# How to cleanup TaxDocumentJSON table

[!include [banner](../includes/banner.md)]

## Introduction
How to use "Tax>Periodic tasks>Tax document JSON cleanup" to cleanup TaxDocumentJSON table.

** Support version:**

10.0.13+ Support compressing the old data before 10.0.9.
10.0.14+ Support removing data.

## Purpose
Along with the system running, more and more data will be produced, and the Database size will also become larger and larger. To release the database space, some old data may be cleaned up.
During cleanup, if it is observed that TaxDocumentJSON table is utilizing too large of space, you can follow this TSG to clean it up.

## Before you begin

1. Please confirm with customer's technical consultant or administrator that no customization depends on tax document object of transaction posted.
2. Ask customer work with their business department to determine a date before which all transactions have been closed.
3. It's recommended to export and backup the data of TaxDocumentJSON table into file.

## Steps to cleanup

1. Enable the flighting TaxRemoveDependenciesOnTaxDocumentJSONFlighting.
2. Open Tax>Periodic tasks>Tax document JSON cleanup. Then the dialog below will popup

    ![](media/IND-GST-GSTIN-1.png)

**INFO:**the Compress option is used to compress the tax document JSON before 10.0.9, and it's a one-time optimization
3. Choose Remove option, and then the Note below will be shown. Please make sure that customer is clear about it.

- NOTE: By choosing the remove option, the tax document JSON will be cleared out. Before continuing, please:
 
   1. Confirm with technical consultant or administrator that no customization depends on tax document object.
   2. Specify conditions in 'Records to include' tab. It's recommended to only remove the data prior to current fiscal year.
   
4. Expand Records to include, specify the condition that confirmed with business department. For example, to remove the Tax document JSON before 31/3/2018, we can set the condition as below

    ![](media/IND-GST-GSTIN-1.png)

5. Click OK to start execution the cleanup.

   
