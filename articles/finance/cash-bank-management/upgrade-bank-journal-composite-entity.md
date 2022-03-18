---
# required metadata

title: Update the bank journal composite entity
description: This topic lists the steps needed to add the additional BankTransactionType field to the composite BankJournalEntity.
author: panolte
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 221654
ms.assetid: adb8146b-eb21-4be2-a338-a5b299fcc9a0
ms.search.region: Global
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Update the bank journal composite entity

[!include [banner](../includes/banner.md)]

This topic lists the steps needed to add the additional BankTransactionType field to the composite BankJournalEntity.

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
