---
# required metadata

title: Advanced bank reconciliation MT940 Import – Composite data entity upgrade
description: A sequence number needs to be added to the bank statement import entity to support the MT940 format. 
author: twheeloc
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221594
ms.assetid: dddc99ae-56ae-48df-856a-131079c17dcb
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Advanced bank reconciliation MT940 Import – Composite data entity upgrade

A sequence number needs to be added to the bank statement import entity to support the MT940 format. 

Use the following steps to add the bank statement import entity to support the MT940 format.

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
            -   Click **View map** on the bank statement document.
            -   Click **Transformations**
            -   Delete the BankReconiliation-to-Composite.xslt file.
            -   Add the new version of BankReconiliation-to-Composite.xsl.

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


