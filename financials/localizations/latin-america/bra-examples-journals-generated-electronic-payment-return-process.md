---
# required metadata

title: Examples -  Journals generated during the electronic payment return process for Brazil
description: This topic shows how payment journals are generated when you import and post the return file for electronic payments. The approved payment lines in the return file can be posted either to one journal or multiple journals.
author: ShylaThompson
manager: AnnBe
ms.date: 2017-02-03 16 - 41 - 43
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 269174
ms.assetid: 41afdcbd-d53f-4034-a664-1e859195b672
ms.search.region: Brazil
# ms.search.industry: 
ms.author: sndray
ms.dyn365.ops.intro: 01-11-2016
ms.dyn365.ops.version: Version 1611

---

# Examples -  Journals generated during the electronic payment return process for Brazil

This topic shows how payment journals are generated when you import and post the return file for electronic payments. The approved payment lines in the return file can be posted either to one journal or multiple journals.

You can make electronic payments by transferring files between a legal entity and a bank. First, you generate and send electronic remittance files to the bank. Then, after the bank processes the exported files, you import a return file from the bank. The return file contains information about the acceptance of an invoice, together with the payment number that is provided by the bank, or information about the payments that are received from a customer or paid to a vendor. When you import a return file, the status of the payments is updated in the **Payment status** field on the **Payment transfers** page. The new status depends on the relationship between the bank return occurrence codes in the return file and the return occurrence codes in Microsoft Dynamics 365 for Operations. When you post the payments that the return file is imported for, only payments that have a status of **Approved** are posted. These payments can be posted to either the same payment journal or multiple payment journals.

## Approved payment lines that are posted to the same payment journal
You can post all approved payment lines that belong to the same journal name to a payment journal. For example, you import a return file that contains six payment lines. Three payment lines have a status of **Approved**, and three payment lines have a status of **Rejected**. Two of the approved payment lines, for journal numbers 001 and 002, belong to the same journal name, DP. The third approved payment line, for journal number 100, belongs to the Test journal name. The following table contains information about the payment lines in the return file.

| Journal name | Journal number | Payment line | Status   | Amount |
|--------------|----------------|--------------|----------|--------|
| DP           | 001            | 1            | Received | 1,000  |
| DP           | 001            | 2            | Approved | 2,000  |
| Test         | 100            | 1            | Approved | 3,000  |
| Test         | 100            | 2            | Rejected | 4,000  |
| DP           | 002            | 1            | Approved | 5,000  |
| DP           | 002            | 2            | Sent     | 6,000  |

When you post the payment lines, the two approved payment lines for journal numbers 001 and 002 that belong to the DP journal name are posted to the same payment journal, 003. However, the approved payment line for journal number 100 that belongs to the Test journal name is posted to payment journal 101.The following table contains information about the payment journals that are created when you post the approved payment lines.

| New journal number | From journal number | Payment line | Status   | Amount |
|--------------------|---------------------|--------------|----------|--------|
| 003                | 001                 | 2            | Approved | 2,000  |
|                    | 002                 | 1            | Approved | 5,000  |
| 101                | 100                 | 1            | Approved | 3,000  |

## Approved payment lines that are posted to multiple payment journals
If the transaction date that is updated for the approved payment lines differs for each payment line in a return file, the payment lines are posted to different payment journals. For example, you import a return file that contains approved payment files that have three different transaction dates. The following table contains information about the three approved payment lines that have different transaction dates.

| Journal number | Payment line | Transaction date | Status   | Amount |
|----------------|--------------|------------------|----------|--------|
| 001            | 1            | January 5, 2013  | Approved | 1,000  |
|                | 2            | January 2, 2013  | Received | 2,000  |
|                | 3            | January 1, 2013  | Approved | 3,000  |
|                | 4            | January 3, 2013  | Approved | 4,000  |

When you post the approved payment lines, the three payment lines are posted to three different journals. The following table contains information about the payment journals that are created when you post the approved payment lines.

| Journal number | Payment line | Transaction date | Status   | Amount |
|----------------|--------------|------------------|----------|--------|
| 002            | 1            | January 5, 2013  | Approved | 1,000  |
| 003            | 1            | January 1, 2013  | Approved | 3,000  |
| 004            | 1            | January 3, 2013  | Approved | 4,000  |



