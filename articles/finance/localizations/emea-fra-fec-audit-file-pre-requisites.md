---
# required metadata

title: Prerequisites for generating an FEC audit file in France
description: This topic describes the prerequisites that must be set up before you can generate a compliant Fichier des écritures comptables (FEC) audit file in France.
author: liza-golub
ms.date: 05/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.author: elgolu
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France

---

# Prerequisites to generate an FEC audit file in France

To generate a compliant Fichier des écritures comptables (FEC) audit file in Microsoft Dynamics 365 Finance, you must set up the following prerequisites in the legal entity that the FEC will be generated from.

- Set up number sequences for vouchers. Each voucher series must contain a piece of text that will be considered a value for the **JournalCode** field in the FEC audit report. For example, define the voucher series for vendor invoice journals as **FRSIFACF-\#\#\#\#\#\#\#\#** to get the value **FRSIFACF** in the **JournalCode** field in the FEC.

- The **Continuous** field must be set to **Yes** for number sequences that are used for invoice numbers and for general ledger transactions for vouchers. This setting accommodates article 100 of BOI-CF-IOR-60-40-20. The numbering in the **EcritureNum** field must increase over time, and it should not include any break. The numbering must be either unique throughout the file or specific to each journal. (The original French text states, "La numérotation dans le champ «EcritureNum» doit être croissante dans le temps et ne pas comporter de rupture. Cette numérotation peut être unique sur l'ensemble du fichier ou être propre à chaque journal."). For more information about set up and use chronological numbers for invoices and vouchers, see [Chronological invoice and voucher numbers](emea-fra-chronological-invoices-vouchers.md).
- The value of the **Limited number of open fiscal years** field in **General ledger parameters** must not be more than **2**. This field limits the total number of fiscal years that can be open at the same time. Article 921-4 of the General Accounting Plan (Principes généraux) states that a closing procedure must be executed no later than the end of the next period.
- The chart of accounts that is used by the legal entity that the FEC is generated from must comply with the standard chart of accounts of France (Livre des procédures fiscales, article A47 A-1, chapter VII: "Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français"). Only main accounts starting with **1**, **2**, **3**, **4**, **5**, **6** or **7** must be included to the FEC.
- Use a posting profile for all customer and supplier balance accounts. These main accounts start with **41** and **40**. The **Do not allow manual entry** parameter must be enabled for them.
- Store all the source documents for general ledger transactions during the period of time required by the accounting obligations of France.
- Accounting documents that are subject for FEC must be posted in EURO and in French. 

> [!NOTE]
> In France, changes aren't allowed to the description of main accounts and posted journals.
