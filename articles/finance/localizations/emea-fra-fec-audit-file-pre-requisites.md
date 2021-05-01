---
# required metadata

title: Pre-requisites to generate FEC compliant with accounting rules in France
description: This topic describes the pre-requisites that must be met before you can generate FEC compliant with accounting rules in France in Microsoft Dynamics 365 Finance.
author: liza-golub
ms.date: 05/01/2021
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

# Pre-requisites to generate FEC compliant with accounting rules in France

To generate compliant FEC from Dynamics 365 Finance we recommend the following rules to be accommodated in the setup of the legal entity from which FEC will be generated:

1.	Set up number sequences for vouchers. Each voucher series must contain a portion of text which is considered as value for the JournalCode in the FEC audit report. For example, configure a voucher series for vendor invoice journals as FRSIFACF-######## to get the value "FRSIFACF" in JournalCode in the FEC.
2.	Set up **Continuous** = **YES** for number sequences that are used in general ledger transactions for voucher to accommodate the “Article 100 du BOI CF IOR 60 40 20”: “The numbering in the "EcritureNum" field must be increasing over time and not include a break. This numbering must be unique throughout the file or be specific to each journal” (original in French: «Lanumérotation dans le champ «EcritureNum» doit être croissante dans le temps et ne pas comporter de rupture. Cette numérotation peut être unique sur l’ensemble du fichier ou être propre à chaque journal»).
3.	Set up **Continuous** = **YES** for number sequences that are used in invoices numbering.
4.	Set up **Limited number of open fiscal years** not exceeding **2** to limit total number of open fiscal year at the same moment.
5.	Chart of accounts used by the legal entity from which FEC to be generated must be compliant with standard chart of accounts of France (Livre des procédures fiscales A 47 A 1 chapitre VII «Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français»)
6.	Customers and suppliers balance accounts (accounts starting with “41” and “40”) must be used with posting profile. **Do not allow manual entry** parameter must be activated for these main accounts.
7.	Keep stored all the documents that are sources for general ledger transactions. 
8.	Changes in the description of main accounts are not allowed in France.
9.	Changes in the description of posted journals are not allowed in France.
