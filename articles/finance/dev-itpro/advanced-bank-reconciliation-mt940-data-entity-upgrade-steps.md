---
title: Advanced bank reconciliation MT940 Import – Composite data entity upgrade
description: A sequence number needs to be added to the bank statement import entity to support the MT940 format. Learn about advanced bank reconciliation.
author: twheeloc
ms.author: twheeloc
ms.topic: upgrade-and-migration-article
ms.date: 06/20/2019
ms.reviewer: twheeloc 
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form:
ms.dyn365.ops.version: Version 1611
ms.assetid: dddc99ae-56ae-48df-856a-131079c17dcb
---

# Advanced bank reconciliation MT940 Import – Composite data entity upgrade

[!include [banner](../includes/banner.md)]

A sequence number needs to be added to the bank statement import entity to support the MT940 format. 

Use the following steps to add the bank statement import entity to support the MT940 format.

1.  Compile and synchronize the following:
    -   Composite Entity\\BankStatementImportEntity
    -   Entity\\BankStatementBalanceEntity
    -   Entity\\BankStatementDocumentEntity
    -   Entity\\BankStatementEntity
    -   Entity\\BankStatementLineEntity
    -   Tables\\BankStatementStaging

2.  Data management\\data projects.
    1.  Load MT940 import project(s)
        1.  Change XSLT.
            -   Click **View map**.
            -   Click **View map** on the bank statement document.
            -   Click **Transformations**
            -   Delete the BankReconiliation-to-Composite.xslt file.
            -   Add the new version of BankReconiliation-to-Composite.xsl.

        2.  Expose the **Sequence Number** on **Source Data** layout.
            1.  Source data format = XML-Element.
            2.  Entity name = Bank statements.
            3.  Upload data file = new version SampleBankCompositeEntity.xml.
            4.  Click **Yes** to overwrite the existing file.
            5.  Click **Yes** to generate a new mapping.
            6.  Verify that S**equenceNumber** is mapped.
                -   Click **View Map** on the statement entity.
                -   Verify that **SequenceNumber** is mapped from Source to Staging.

3.  Import the new statement.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
