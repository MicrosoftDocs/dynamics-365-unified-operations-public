---
title: Update the bank journal composite entity
description: This article lists the steps needed to add the additional BankTransactionType field to the composite BankJournalEntity.
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 10/24/2022
ms.reviewer: kfend 
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form:
ms.dyn365.ops.version: Version 1611
ms.assetid: adb8146b-eb21-4be2-a338-a5b299fcc9a0
---

# Update the bank journal composite entity

[!include [banner](../includes/banner.md)]

This article lists the steps needed to add the additional BankTransactionType field to the composite BankJournalEntity.

Use the following steps to add the additional BankTransactionType field to the composite BankJournalEntity.

1.  Compile and synchronize the following bank journal composite entities, entities, and staging tables:
    -   Composite Entity\\BankJournalEntity
    -   Entity\\BankJournalHeaderEntity
    -   Entity\\BankJournalLineEntity
    -   Table\\BankJournalHeaderStaging
    -   Table\\BankJournalLineStaging

2.  Data management\\data projects
    -   Expose the **Bank Transaction** type on **Source Data** layout.
        -   Source data format = XML-Element
        -   Entity name = Bank Journal
        -   Upload data file = new version SampleBankJournalCompositeEntity.xml
        -   Click **Yes** to overwrite the existing file.
        -   Click **Yes** to generate mapping from scratch.
        -   Verify that the Bank Transaction Type is mapped.
            -   Click **View map** on Line entity.
            -   Verify that Bank Transaction type is mapped from Source to Staging.

3.  Import the new statement.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
