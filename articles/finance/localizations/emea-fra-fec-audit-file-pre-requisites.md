---
# required metadata

title: Prerequisites to generate the FEC audit file in France
description: This topic describes the prerequisites that must be met before you can generate the FEC compliant audit file in France.
author: liza-golub
ms.date: 05/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: France

---

# Prerequisites to generate the FEC audit file in France

To generate a compliant FEC audit file from Dynamics 365 Finance, the following prerequisites must be set up in the legal entity from which the FEC will be generated.

- Set up number sequences for vouchers. Each voucher series must contain a portion of text which is considered a value for the **JournalCode** in the FEC audit report. For example, configure a voucher series for vendor invoice journals as **FRSIFACF-########** to get the value **FRSIFACF** in **JournalCode** in the FEC.

    - The **Continuous** field must be set to **YES** for number sequences that are used in general ledger transactions for voucher. This setting accomodates Article 100 du BOI CF IOR 60 40 20. The numbering in the **EcritureNum** field must increase over time and shouldn't include a break. The numbering must be unique throughout the file, or be specific to each journal (original text in French, "Lanumérotation dans le champ «EcritureNum» doit être croissante dans le temps et ne pas comporter de rupture. Cette numérotation peut être unique sur l’ensemble du fichier ou être propre à chaque journal.")
    - The **Continuous** field must be  set to **YES** for number sequences that are used in invoice numbering.

- The field, **Limited number of open fiscal years** must not exceed **2**. This number limits the total number of fiscal years that can be open at the same time.
- The chart of accounts used by the legal entity from which FEC is generated must be compliant with the standard chart of accounts of France (Livre des procédures fiscales A 47 A 1 chapitre VII «Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français»).
- Use a posting profile for all customers and suppliers balance accounts. These accounts start with **41** and **40**. The parameter, **Do not allow manual entry** must be activate for these main accounts.
- Store all of the source documents for general ledger transactions. 

> [!NOTE]
> Changes to the description of main accounts and posted journals aren't allowed in France.

