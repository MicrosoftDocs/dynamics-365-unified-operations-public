---
# required metadata

title: Update the bank journal composite entity | Microsoft Docs
description: The following steps are needed in order to add the additional BankTransactionType field to the composite BankJournalEntity.
author: twheeloc
manager: AnnBe
ms.date: 2016-10-31 16:22:18
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Application User, Developer
# ms.devlang: 
ms.reviewer: 101
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 221654
ms.assetid: c8109fa1-56b6-4a05-b666-a49d1cd2fa12
ms.region: Global
# ms.industry: 
ms.author: saraschi

---

# Update the bank journal composite entity

The following steps are needed in order to add the additional BankTransactionType field to the composite BankJournalEntity.

Use the following steps to add the additional BankTransactionType field to the composite BankJournalEntity.

1.  Compile and synchronize the following bank journal composite entities, entities, and staging tables:
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


