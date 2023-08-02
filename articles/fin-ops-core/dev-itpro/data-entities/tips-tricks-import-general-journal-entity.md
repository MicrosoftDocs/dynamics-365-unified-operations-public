---
# required metadata

title: Importing vouchers by using the General journal entity
description: This article provides tips for importing data into the General journal by using the General journal entity.  
author: rcarlson
ms.date: 04/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 0b8149b5-32c5-4518-9ebd-09c9fd7f4cfc
ms.search.region: Global
# ms.search.industry: 
ms.author: rcarlson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Importing vouchers by using the General journal entity

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-1.md)]

This article provides tips for importing data into the General journal by using the General journal entity.

You can use the General journal entity to import vouchers that have an account or offset account type of **Ledger**, **Customer**, **Vendor**, or **Bank**. The voucher can be entered as one line, using both the **Account** field and the **Offset account** field, or as a multi-line voucher, where only the **Account** field is used (and the **Offset account** is left blank on each line). The General journal entity doesn't support every account type. Instead, other entities exist for scenarios where different combinations of account types are required. For example, to import a project transaction, use the Project expense journal entity. Each entity is designed to support specific scenarios. This means additional fields may be available in entities for those scenarios. However, additional fields might not be available in entities for different scenarios.

## Setup
Before you import by using the General journal entity, validate the following setup:

- **Number sequence setup for the journal batch number** – By default, when you import by using the General journal entity, the journal batch number uses the number sequence that is defined in the General ledger parameters. If you set the number sequence for the journal batch number to **Manual**, a default number isn't applied. This setup isn't supported.
- **Financial dimension configuration** – Every organization must define the order of financial dimensions when entities are used to import transactions. The order is defined for the **Ledger dimensions integration** format, at **General ledger** &gt; **Chart of accounts** &gt; **Dimensions** &gt; **Financial dimension configuration for integrating applications** &gt; **Select data entities**. The segments of the ledger account that is imported must have the same order. Otherwise, an error will occur during import.

## General journal entity setup
Two settings in Data management affect how the default journal batch number or voucher number is applied:

- **Set-based processing** (on the data entity)
- **Auto-generated** (on the field mapping)

The following sections describe the effect of these settings. They also explain how the system generates batch numbers for journals and voucher numbers.

### Journal batch number

- The **Set-based processing** setting on the General journal entity doesn't affect the way that journal batch numbers are generated.
- If the **Journal batch number** field is set to **Auto-generated**, a new journal batch number is created for every line that is imported. This behavior isn't recommended. The **Auto-generated** setting is found on the import project, under **View map**, on the **Mapping details** tab.
- If the **Journal batch number** field isn't set to **Auto-generated**, the journal batch number is created as follows:

    - If the journal batch number that is defined in the imported file matches an existing, unposted daily journal, all lines that have a matching journal batch number are imported into the existing journal. Lines are never imported into a posted journal batch number. Instead, a new number is created.
    - If the journal batch number that is defined in the imported file doesn't match an existing, unposted daily journal, all lines that have the same journal batch number are grouped under a new journal. For example, all lines that have a journal batch number of 1 are imported into a new journal, and all lines that have a journal batch number of 2 are imported into a second new journal. The journal batch number is created by using the number sequence that is defined in the General ledger parameters.

### Voucher number

- When you use the **Set-based processing** setting on the General journal entity, the voucher number must be provided in the imported file. Every transaction in the General journal is assigned the voucher number that is provided in the imported file, even if the voucher isn’t balanced. Note the following points if you want to use set-based processing, but you also want to use the number sequence that is defined for voucher numbers.

    - To enable this functionality, on the journal name that is used for imports, set **Number allocation at posting** to **Yes**.
    - A voucher number must still be defined in the imported file. However, this number is temporary and will be overwritten by the voucher number when the journal is posted. Be sure that the lines of the journal are grouped correctly by temporary voucher number. For example, during posting, three lines are found that have a temporary voucher number of 1. The temporary voucher number of all three lines is overwritten by the next number in the number sequence. If those three lines aren’t a balanced entry, the voucher won't be posted. Next, if lines are found that have a temporary voucher number of 2, this number is overwritten by the next voucher number in the  sequence, and so on.

- When you don't use the **Set-based processing** setting, you do not need to provide a voucher number in the imported file. The voucher numbers are created during import, based on the setup of the journal name (**One voucher only**, **In connection of balance**, and so on). For example, if the journal name is defined as **In connection of balance**, the first line receives a new default voucher number. The system then evaluates the line to determine whether the debits equal the credits. If an offset account exists on the line, the next line that is imported receives a new voucher number. If no offset account exists, the system evaluates whether the debits equal the credits as each new line is imported.
- If the **Voucher number** field is set to **Auto-generated**, the import won't succeed. The **Auto-generated** setting for the **Voucher number** field isn't supported.

By default, the General journal entity uses set-based processing. After you evaluate the business requirements for your organization, you can change the **Set-based processing** setting by clicking **Data entities** in the **Data management** workspace. Set-based processing is used to speed up the import process. If you don't use set-based processing, import of the General journal entity import will be slower.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
