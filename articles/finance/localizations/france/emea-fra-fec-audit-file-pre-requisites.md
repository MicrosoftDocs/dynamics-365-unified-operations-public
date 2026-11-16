---
title: Prerequisites for generating an FEC audit file in France
description: Learn about the prerequisites that must be set up before you can generate a compliant Fichier des écritures comptables (FEC) audit file in France.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 11/16/2026
ms.reviewer: johnmichalak
ms.search.region: France
---

# Prerequisites to generate an FEC audit file in France

[!INCLUDE [banner](../../includes/banner.md)]

To generate a compliant Fichier des écritures comptables (FEC) audit file in Microsoft Dynamics 365 Finance, set up the following prerequisites in the legal entity that you generate the FEC from.

- Set up number sequences for vouchers. Each voucher series must contain a piece of text that serves as the **JournalCode** field value in the FEC audit report. For example, define the voucher series for vendor invoice journals as **FRSIFACF-########** to get the value **FRSIFACF** in the **JournalCode** field in the FEC.
- Set the **Continuous** field to **Yes** for number sequences that you use for invoice numbers and for general ledger transactions for vouchers. This setting accommodates article 100 of BOI-CF-IOR-60-40-20. The numbering in the **EcritureNum** field must increase over time, and it shouldn't include any break. The numbering must be either unique throughout the file or specific to each journal. (The original French text states, "La numérotation dans le champ «EcritureNum» doit être croissante dans le temps et ne pas comporter de rupture. Cette numérotation peut être unique sur l'ensemble du fichier ou être propre à chaque journal."). For more information about set up and use chronological numbers for invoices and vouchers, see [Chronological invoice and voucher numbers](emea-fra-chronological-invoices-vouchers.md).

    > [!NOTE]
    > - Enable the **(France) Number sequences setup for FEC Missing numbers justification** feature in Feature management. Use this feature to generate the **FEC Missing numbers justification** report for specific number sequences or if numerical symbols are included in the prefix segment information of the number sequences that you use for voucher numbering.
    > - When the feature is enabled, you can specify number sequences on the **Number sequences setup for FEC Missing numbers justification** FastTab on the **Ledger** tab of the **General ledger parameters** page. The number sequences are then analyzed when you generate the **FEC Missing numbers justification** report. The prefix segment information of different number sequences must not intersect. When the feature isn't enabled, the **FEC Missing numbers justification** report analyzes all the possible number sequences that are used for voucher numbering. The assumption is that the prefix segment information of the number sequences consists of alphabetic characters and doesn't include numerical symbols.
    > - Set up different formats for different number sequences. Each format should have alphanumeric segments that contain incrementing numbers but not incrementing letters, and the total value of alphanumeric segments should be less than 9,223,372,036,854,775,808 (int64). If you set up identical formats for different number sequences, or if you don't follow the preceding recommendations for alphanumeric segments, you might not be able to generate the [Missing numbers justification annex](emea-fra-fec-audit-file-structure.md#missing-numbers-justification) of FEC.  

- Set the value of the **Limited number of open fiscal years** field in **General ledger parameters** to no more than **2**. This field limits the total number of fiscal years that you can open at the same time. Article 921-4 of the General Accounting Plan (Principes généraux) states that a closing procedure must be executed no later than the end of the next period.
- The chart of accounts that the legal entity uses for generating the FEC must comply with the standard chart of accounts of France (Livre des procédures fiscales, article A47 A-1, chapter VII: "Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français"). Only main accounts starting with **1**, **2**, **3**, **4**, **5**, **6**, or **7** must be included in the FEC.
- Use a posting profile for all customer and supplier balance accounts. These main accounts start with **41** and **40**. The **Do not allow manual entry** parameter must be enabled for them.
- Store all the source documents for general ledger transactions during the period of time required by the accounting obligations of France.
- Post accounting documents that are subject for FEC in EURO and in French.
- Generate the FEC of each fiscal year as part of the closing procedure, after the final year-end close, and store it in the tax archive. The archived FEC is the reference version of the closed fiscal year. For more information, see [Tax archive in France](emea-france-tax-archive.md).

## Main account names and journal names in the FEC 

The FEC includes the name of each main account (*CompteLib*) and the description of the journal name that you use to post each entry (*JournalLib*). Finance reads these values from master data when you generate the file. If a main account has a name translation in French, the FEC uses the translation. As with other master data, users who have the required permissions can update these values. 

French law requires that you keep accounting documents without alteration of any kind (*Code de commerce, article L123-22*). To keep the FEC of a closed fiscal year consistent with the accounting records of that year, follow these practices in legal entities in France: 

- After you post entries to a main account, don't change the name of the main account or its French name translation. If you need an account that has a different name or purpose, create a new main account, and stop posting to the previous one, for example, by suspending it or by entering an end date in the **Active to** field.
- After you post entries with a journal name, don't change its description. If you need a different description, create a new journal name.
- Grant the security privileges that allow users to maintain main accounts and journal names only to a small group of authorized users.
- Turn on [database logging](/dynamics365/fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log) for main accounts, main account name translations, and journal names. The database log records each change, together with the previous and new values, the user, and the date and time. Include the log in the tax archive.
- When you must provide the FEC of a closed fiscal year, for example, during a tax audit, provide the FEC that you stored in the tax archive at year-end closing. 

For information about other data that's included in the FEC, such as customer and vendor names and the descriptions of posted entries, see [Protection of data that's included in the FEC](emea-france-nf203.md#protection-of-data-thats-included-in-the-fec). For information about the tax archive, see [Tax archive in France](emea-france-tax-archive.md). 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
