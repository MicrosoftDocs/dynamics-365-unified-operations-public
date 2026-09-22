---
title: Advanced bank reconciliation MT940 Import – Composite data entity upgrade
description: A sequence number needs to be added to the bank statement import entity to support the MT940 format. 
author: twheeloc
ms.author: twheeloc
ms.topic: upgrade-and-migration-article
ms.date: 08/20/2026
ms.reviewer: twheeloc 
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form:
ms.dyn365.ops.version: Version 1611
ms.assetid: dddc99ae-56ae-48df-856a-131079c17dcb
---

# Advanced bank reconciliation MT940 import – Composite data entity upgrade

[!INCLUDE [banner](../includes/banner.md)]

To support the MT940 format, add a sequence number to the bank statement import entity.

Use the following steps to add the bank statement import entity to support the MT940 format.

1. Compile and synchronize the following components:
    - Composite Entity\\BankStatementImportEntity
    - Entity\\BankStatementBalanceEntity
    - Entity\\BankStatementDocumentEntity
    - Entity\\BankStatementEntity
    - Entity\\BankStatementLineEntity
    - Tables\\BankStatementStaging

1. In Data management, open **Data projects**.
    1. Load MT940 import projects.
        1. Change the XSLT.
            - Select **View map**.
            - Select **View map** on the bank statement document.
            - Select **Transformations**.
            - Delete the **BankReconiliation-to-Composite.xslt** file.
            - Add the new version of **BankReconiliation-to-Composite.xsl**.

        1. Expose the **Sequence Number** on the **Source Data** layout.
            1. Set **Source data format** to **XML-Element**.
            1. Set **Entity name** to **Bank statements**.
            1. Upload the data file **SampleBankCompositeEntity.xml** (new version).
            1. Select **Yes** to overwrite the existing file.
            1. Select **Yes** to generate a new mapping.
            1. Verify that **SequenceNumber** is mapped.
                - Select **View Map** on the statement entity.
                - Verify that **SequenceNumber** is mapped from Source to Staging.

1. Import the new statement.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
