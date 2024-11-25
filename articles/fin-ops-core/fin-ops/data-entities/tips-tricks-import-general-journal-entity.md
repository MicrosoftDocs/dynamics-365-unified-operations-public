---
title: Importing vouchers by using the General journal entity
description: Learn how to import data into the General journal by using the General journal entity, including outlines on setup and journal batch numbers.  
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 10/25/2024
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0b8149b5-32c5-4518-9ebd-09c9fd7f4cfc
---

# Importing vouchers by using the General journal entity

[!include [banner](../../../finance/includes/banner.md)]

This article provides tips for importing data into the General journal by using the General journal entity. Find technical information about the entity in [General journal entity](../../dev-itpro/data-entities/entity-general-journal.md).

You can use the General journal entity to import vouchers that have an account or offset account type of **Ledger**, **Customer**, **Vendor**, or **Bank**. The voucher can be entered as one line, using both the **Account** field and the **Offset account** field, or as a multi-line voucher, where only the **Account** field is used (and the **Offset account** is left blank on each line). The General journal entity doesn't support every account type. Instead, other entities exist for scenarios where different combinations of account types are required. For example, to import a project transaction, use the Project expense journal entity. Each entity is designed to support specific scenarios. This means other fields might be available in entities for those scenarios. However, other fields might not be available in entities for different scenarios.

## Data Management Framework and OData entities for general journal imports

The choice of frameworks and entities can significantly affect the efficiency and integrity of data handling processes. Two notable entities are the Data Management Framework (DMF) entity and the OData entity (specifically, **LedgerJournalLineEntity**). Each of these entities has its unique advantages and limitations. By understanding those advantages and limitations, organizations can make informed decisions about how to optimize their data import processes. 

### DMF entity

The DMF entity is designed primarily for scenarios where high-volume imports must be handled. Because the DMF entity is optimized for tasks of this type, it's an invaluable tool for organizations that work with large datasets. Nevertheless, this entity also has limitations. 

#### Advantages of the DMF entity

- **High-volume import handling:** The DMF entity excels in scenarios where large volumes of data must be imported in an efficient manner. Because its design is focused on optimizing bulk data movements, it's suitable for operations where time and performance are critical.
- **Configurability:** Users can configure the DMF entity to suit their specific needs. For example, by adjusting the data entity settings, users can emulate row-by-row validation and defaulting logic. In this way, they can align the DMF entity's performance characteristics with those of the OData entity. 

#### Limitations of the DMF entity

- **Lack of support for intercompany transactions:** A primary limitation of the DMF entity is its inability to effectively handle intercompany transactions. This limitation can be a significant drawback for organizations that operate across multiple legal entities and must seamlessly manage intercompany data. 
- **Minimal validation during import:** The DMF entity does minimal validation during the import process. Therefore, the process must be carefully managed. Otherwise, data integrity issues can occur if errors or inconsistencies in the imported data aren't promptly caught. For example, the default voucher might not be entered. 

### OData entity

The OData entity, and specifically the **LedgerJournalLineEntity** entity, takes a different approach to data import and validation. It's designed to invoke more comprehensive defaulting and validation logic on a row-by-row basis. Although this approach enhances data integrity, it might affect performance. 

#### Advantages of the OData entity

- **Enhanced data integrity:** The OData entity's row-by-row validation ensures that each entry is thoroughly checked before it's imported. This comprehensive validation process helps maintain high data quality and consistency. 
- **Defaulting logic:** The OData entity invokes defaulting logic for each row to ensure that all necessary fields are correctly populated. Therefore, there is less likelihood of incomplete or incorrect data entries. 

#### Limitations of the OData entity

- **Performance impact:** The additional processing that is required for row-by-row defaulting and validation can lead to slower performance. Organizations must consider this trade-off, especially if they work with large datasets.

### Balancing performance and data accuracy

Organizations often have to strike a balance between performance and data accuracy. The flexibility that the DMF entity offers lets users configure it to emulate the validation and defaulting logic of the OData entity. When the set-based import configuration is turned off, the DMF entity can achieve functional parity with the OData entity. It can also align its performance characteristics accordingly. 

### Performance guidelines and characteristics

When you configure data entities for import processes, consider performance guidelines and characteristics. For example, consider row limit thresholds, which help optimize import processes and ensure that system performance remains stable while the system is handling large volumes of data. Correct configuration and adherence to these guidelines can enhance both the efficiency and the effectiveness of data imports. 

Both the DMF entity and the OData entity offer unique benefits and challenges. The DMF entity's strength lies in its ability to handle high-volume imports, whereas the OData entity excels at ensuring data integrity through comprehensive validation. 

## Setup

Before you import by using the General journal entity, validate the following setup:

### Number sequence setup for the journal batch number

- By default, when you import using the General journal entity, the journal batch number uses the number sequence that is defined in the General ledger parameters.
- If you set the number sequence for the journal batch number to **Manual**, a default number isn't applied. This setup isn't supported.

### Financial dimension configuration

- Every organization must define the order of financial dimensions when entities are used to import transactions.
- The order for the **Ledger dimensions integration** format:

    **General ledger** > **Chart of accounts** > **Dimensions** > **Financial dimension configuration for integrating applications** > **Select data entities**.

- The segments of the ledger account that is imported must have the same order. Otherwise, an error occurs during import.

## General journal entity setup

Two settings in Data management affect how the default journal batch number or voucher number is applied:

- **Set-based processing** (on the data entity)
- **Auto-generated** (on the field mapping)

The following sections describe the effect of these settings and explain how the system generates batch numbers for journals and voucher numbers.

### Journal batch number

- The **Set-based processing** setting on the General journal entity doesn't affect the way that journal batch numbers are generated.
- If the **Journal batch number** field is set to **Auto-generated**, a new journal batch number is created for every line that is imported. This behavior isn't recommended. The **Auto-generated** setting is found on the import project, under **View map**, on the **Mapping details** tab.
- If the **Journal batch number** field isn't set to **Auto-generated**, the journal batch number is created as follows:

    - If the journal batch number that is defined in the imported file matches an existing, unposted daily journal, all lines that have a matching journal batch number are imported into the existing journal. Lines are never imported into a posted journal batch number. Instead, a new number is created.
    - If the journal batch number that is defined in the imported file doesn't match an existing, unposted daily journal, all lines that have the same journal batch number are grouped under a new journal. For example, all lines that have a journal batch number of 1 are imported into a new journal, and all lines that have a journal batch number of 2 are imported into a second new journal. The journal batch number is created by using the number sequence that is defined in the General ledger parameters.

### Voucher number

- When you use the **Set-based processing** setting on the General journal entity, the voucher number must be provided in the imported file. Every transaction in the General journal is assigned the voucher number that is provided in the imported file, even if the voucher isn’t balanced. Note the following points if you want to use set-based processing, but you also want to use the number sequence that is defined for voucher numbers.

    - To enable this functionality, on the journal name that is used for imports, set **Number allocation at posting** to **Yes**.
    - A voucher number must still be defined in the imported file. However, when the journal is posted, it overwrites the temporary number with the voucher number. Be sure that you group the lines of the journal correctly by the temporary voucher number. For example, during posting, three lines are found that have a temporary voucher number of 1. The next number in the number sequence overwrites the temporary voucher number of all three lines. If those three lines aren’t a balanced entry, the voucher isn't posted. Next, if lines have a temporary voucher number of 2, the system overwrites this number with the next voucher number in the sequence.

- When you don't use the **Set-based processing** setting, you don't need to provide a voucher number in the imported file. The voucher numbers are created during import, based on the setup of the journal name (**One voucher only**, **In connection of balance**, and so on). For example, if the journal name is defined as **In connection of balance**, the first line receives a new default voucher number. The system then evaluates the line to determine whether the debits equal the credits. If an offset account exists on the line, the next line that is imported receives a new voucher number. If no offset account exists, the system evaluates whether the debits equal the credits as each new line is imported.
- If the **Voucher number** field is set to **Auto-generated**, the import fails. The **Auto-generated** setting for the **Voucher number** field isn't supported.

By default, the General journal entity uses set-based processing. After you evaluate the business requirements for your organization, you can change the **Set-based processing** setting by selecting **Data entities** in the **Data management** workspace. Set-based processing is used to speed up the import process. If you don't use set-based processing, import of the General journal entity import is slower.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
