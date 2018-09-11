---
# required metadata
title: Set up bank accounts 
description: This topic provides information about local settings and requisites for bank modules for Russia. 
author: ShylaThompson
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Local settings and requisites for Bank module.

Before start working with Bank management workspace, you should do the following settings:


# Set up Bank

Create new Bank manually or through **Update bank accounts** function in the form **Cash and bank management > Setup > Bank
groups**

Define Russia-specific information:  

- **BIC** – bank identifier code, 
- **Corr. Bank account** – correspondent bank account.
- **Bank type** – Main, Foreign, Branch. 
  For Branch, define also **Main bank**
  For Foreign, define also **Vendor account** associated with the foreign bank, on Fast tab General.
- Optionally define .docx template for **Payment order in currency**. If defined, this will be default template of payment order in currency for all foreign bank accounts related to this bank.
Note.
Before defining document template, you should create them as Files in the Document attachment (icon Clip in the right up corner of the form)

![Bank](bank.jpg)
    

# Set up Bank accounts

1. Create new Bank account at **Cash and bank management > Bank accounts > Bank accounts**.
2. Complete all required fields. The following list includes some fields that might be required. 
  - **Bank account** (code)
  - **Bank account number**
  - **Main account** - This is the general ledger account to be used in posting
  - **Currency**
  - **SWIFT code** 

  For more information see [Bank management workspace](../cash-bank-management/bank-management-workspace.md)

3. Enter Russia-specific information: 
  - Choose **Bank** in the field **Bank groups**. Validate correctness of respective fields **BIC** and **Corr. Bank account**. Also validate **Address** and **Contact information** on respective fast tabs and update accordingly.
  - Define number series for Payment order generation in the field **P/O numeration**.
  - For bank accounts in foreign currency, you may also define .docx templates for generation of payment orders in paper format in the respective fields **Payment order in currency**, **Order template (currency sale)** and **Order template (currency purchase)**. 

> [!NOTE]
> Before defining a document template, create the templates as files and attach them to the record. You can tell if a document is attached by the number indicator on the Document attachment icon.

![Bank account](bank-account.jpg)



