---
# required metadata

title: Clean up the TaxDocument JSON table 
description: This topic provides inoformation about how free up space in the database by removing old data from the TaxDocument JSON table.
author: prabhatb
manager: Annbe
ms.date: 10/07/2019
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


# Clean up the TaxDocument JSON table

[!include [banner](../includes/banner.md)]

## Supported versions

- 10.0.13 and later: Support compressing the old data before 10.0.9.
- 10.0.14 and later: Support removing data.


## Purpose
With the system running, more and more data is produced, and the database size continues to become larger. To free up space in the database, old data may be cleaned up. During cleanup, if you observe that the **TaxDocumentJSON** table is using too muchspace, you can complete the steps in the topic to clean it up.

## Before you begin
Before you begin the cleanup, complete the following tasks:

- Confirm with the customer's technical consultant or administrator that no customization depends on the tax document object of the posted transaction.
- Ask the customer to work with their business department to determine a date before which all transactions have been closed.
- Export and backup the data of the **TaxDocumentJSON** table.

## Clean up the database

1. Verify that you have enabled the flighted feature, **TaxRemoveDependenciesOnTaxDocumentJSONFlighting**.
2. Go to **Tax** > **Periodic tasks** > **Tax document JSON cleanup**. 

    ![Tax document JSON cleanup dialog window](media/TaxDocument-JSON-01.PNG)

    > [!NOTE]
    > **Compress** is used to compress the tax document JSON before 10.0.9 and is a one-time optimization.

3. Select **Remove**. The following note will display. Verify with the customer that they understand the impact of the change.

    **NOTE: By choosing the remove option, the tax document JSON will be cleared out. Before continuing, please:**
 
   **1. Confirm with technical consultant or administrator that no customization depends on tax document object.**
   **2. Specify conditions in 'Records to include' tab. It's recommended to only remove the data prior to current fiscal year.**
   
4. Expand the **Records to include** FastTab, and specify the conditions that you confirmed with business department. For example, you may have agreed to remove the Tax document JSON before 31/3/2018. This means that in the **TAX DOCUMENT EXTENSION INFORMATION FOR INDIA** field, you will select 31/3/2018.

    ![Tax document extension information for India field](media/TaxDocument-JSON-02.PNG)

5. Select **OK** to start the cleanup.
