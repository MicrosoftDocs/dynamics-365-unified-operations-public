---
# required metadata

title: Structure of Dynamics 365 Finance data sources for the FEC
description: This topic describes the structure of Microsoft Dynamics 365 Finance data sources for the Fichier des écritures comptables (FEC).
author: liza-golub
ms.date: 11/24/2021
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

# Structure of Dynamics 365 Finance data sources for the FEC

In Microsoft Dynamics 365 Finance, you can generate the [FEC main](#fec-main) (Fichier des écritures comptables) file and the following annexes:

- **[Customers balance](#customers-balances):** Customers fiscal year opening balances annex
- **[Vendors balance](#vendors-balances):** Vendors fiscal year opening balances annex
- **[Customers transactions](#customers-transactions):** Customers transactions annex for a specified period
- **[Vendors transactions](#vendors-transactions):** Vendors transactions annex for a specified period

You can also generate an FEC that includes customer and vendor fiscal year opening balances ([FEC Main Extended](#fec-main-extended)). Use this option for companies that have only a few records during the reporting period. The reporting period must include the beginning of the fiscal year.

As explained in [Prerequisites to generate an FEC audit file in France](emea-fra-fec-audit-file-pre-requisites.md), to accommodate article 100 of BOI-CF-IOR-60-40-20, the numbering must be continuous, consistent, and sequential. Because of these numbering requirements, we recommend that you set the **Continuous** option to **Yes** for number sequences. In some scenarios, the consistency of the number sequence for general ledger account entries (voucher) can be interrupted in the FEC Main file for the following reasons:

  - A general ledger account entry is created in accounting but isn't reported in the FEC when the amount is 0.00.
  - A voucher number is used for an inventory transaction that has a zero amount that isn't reflected in the general ledger account entries table.
  - A gap in the number sequence for general ledger account entries occurs because of a technical issue.

As of version 10.0.23 of Finance, use the [Missing numbers justification](#missing-numbers-justification) annex to report general ledger account transactions that are missing in the FEC Main file.

The following sections list the data sources that are used in the FEC main file and annexes.

## <a id="fec-main"></a>Main FEC file for the period specified

The following table shows the **Main FEC file for the period specified** data structure definitions (\$GeneralJournalView\_FR).

| Number | Name          | Type           | Description (FR) | Description (EN) | Electronic reporting (ER) data source |
|--------|---------------|----------------|------------------|------------------|---------------------------------------|
| 1      | JournalCode   | Alphanumérique | Le code journal de l'écriture comptable | The journal code of the accounting entry. | \$GeneralJournalView\_FR/\$JournalCodeText |
| 2      | JournalLib    | Alphanumérique | Le libellé journal de l'écriture comptable | The journal caption of the accounting entry. | \$GeneralJournalView\_FR/getGeneralJournalEntry()/deJournalLib\_FR() |
| 3      | EcritureNum   | Alphanumérique | Le numéro sur une séquence continue de l'écriture comptable | The number in a continuous sequence for the accounting entry. | \$GeneralJournalView\_FR/GeneralJournalEntrySubledgerVoucher |
| 4      | EcritureDate  | Date           | La date de comptabilisation de l'écriture comptable | The posting date of the accounting entry. | \$GeneralJournalView\_FR/GeneralJournalEntryAccountingDate |
| 5      | CompteNum     | Alphanumérique | Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français | The account number, the first three characters of which must correspond to figures that respect the standards of the French chart of accounts. Information on multiple customers or vendors transactions can be found in respective annexes. | \$GeneralJournalView\_FR/\$MainAccountId |
| 6      | CompteLib     | Alphanumérique | Le libellé de compte, conformément à la nomenclature du plan comptable français | The account name in accordance with the nomenclature of the French chart of accounts. | \$GeneralJournalView\_FR/getGeneralJournalAccountEntry()/getMainAccountName() |
| 7      | CompAuxNum    | Alphanumérique | Le numéro de compte auxiliaire (à blanc si non utilisé) | The auxiliary account number. This field is blank if it isn't used. | \$GeneralJournalView\_FR/getGeneralJournalAccountEntry()/deCompteAuxNum\_FR() |
| 8      | CompAuxLib    | Alphanumérique | Le libellé de compte auxiliaire (à blanc si non utilisé) | The auxiliary account description. This field is blank if it isn't used. | \$GeneralJournalView\_FR/getGeneralJournalAccountEntry()/deCompteAuxLib\_FR() |
| 9      | PieceRef      | Alphanumérique | La référence de la pièce justificative | The reference of the supporting document. If reference of the supporting document can't be found, this field is populated with EcritureNum. | \$GeneralJournalView\_FR/getGeneralJournalEntry()/dePieceNum\_FR() |
| 10     | PieceDate     | Date           | La date de la pièce justificative | The date of the supporting document. | \$GeneralJournalView\_FR/getGeneralJournalEntry()/dePieceDate\_FR() |
| 11     | EcritureLib   | Alphanumérique | Le libellé de l'écriture comptable | The wording of the accounting entry. | \$GeneralJournalView\_FR/\$ReplaceIntoDeEcritureLib\_FR |
| 12     | Montant       | Numérique      | Le montant au débit/ au crédit | The debit/credit amount. | \$GeneralJournalView\_FR/\$AbsAmount |
| 13     | Sens          | Numérique      | Le sens: "D" au débit; "C" au crédit | The direction: **D** = debit, **C** = credit | \$GeneralJournalView\_FR/\$Direction |
| 14     | EcritureLet   | Alphanumérique | Le lettrage de l'écriture comptable (à blanc si non utilisé) | The lettering of the accounting entry. This field is blank if it isn't used. | \$GeneralJournalView\_FR/\$deEcritureLet |
| 15     | DateLet       | Date           | La date de lettrage (à blanc si non utilisé) | The lettering date. This field is blank if it isn't used. | \$GeneralJournalView\_FR/\$deDateLet |
| 16     | ValidDate     | Date           | La date de validation de l'écriture comptable | The validation date of the accounting entry. | \$GeneralJournalView\_FR/GeneralJournalEntryAccountingDate |
| 17     | Montantdevise | Numérique      | Le montant en devise (à blanc si non utilisé) | The amount in currency. This field is blank if it isn't used. | \$GeneralJournalView\_FR/GeneralJournalAccountEntryTransactionCurrencyAmount |
| 18     | Idevise       | Alphanumérique | L'identifiant de la devise (à blanc si non utilisé) | The currency identifier. This field is blank if it isn't used. | \$GeneralJournalView\_FR/GeneralJournalAccountEntryTransactionCurrencyCode |

## <a id="customers-balances"></a>Customers fiscal year opening balances annex 

Customers fiscal year opening transactions are posted as summary transactions in general ledger. To provide detailed information on fiscal year opening transactions by customers, the **Customers fiscal year opening balances annex** is implemented. This annex collects the amounts of opening balances by customers at the beginning of the fiscal year and provides this information together with the opening transaction voucher from the general ledger.

The following table shows the **Customers fiscal year opening balances annex** data structure definitions (\$CustLedgerBalance).

| Number | Name          | Type           | Description (FR) | Description (EN) | ER data source |
|--------|---------------|----------------|------------------|------------------|----------------|
| 1      | JournalCode   | Alphanumérique | Le code journal de l'écriture comptable | The journal code of the accounting entry. | CustTransGroupedByLedgerAccount/\$JournalCodeText |
| 2      | JournalLib    | Alphanumérique | Le libellé journal de l'écriture comptable | The journal caption of the accounting entry. | CustTransGroupedByLedgerAccount/\$JournalLibText |
| 3      | EcritureNum   | Alphanumérique | Le numéro sur une séquence continue de l'écriture comptable | The number in a continuous sequence for the accounting entry. | CustTransGroupedByLedgerAccount/\$Voucher |
| 4      | EcritureDate  | Date           | La date de comptabilisation de l'écriture comptable | The posting date of the accounting entry. | CustTransGroupedByLedgerAccount/\$Date |
| 5      | CompteNum     | Alphanumérique | Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français | The account number, the first three characters of which must correspond to figures that respect the standards of the French chart of accounts. | CustTransGroupedByLedgerAccount/grouped/\$LedgerAccount |
| 6      | CompteLib     | Alphanumérique | Le libellé de compte, conformément à la nomenclature du plan comptable français | The account name in accordance with the nomenclature of the French chart of accounts. | CustTransGroupedByLedgerAccount/\$LedgerAccountName |
| 7      | CompAuxNum    | Alphanumérique | Le numéro de compte auxiliaire (à blanc si non utilisé) | The auxiliary account number. This field is blank if it isn't used. | CustTransGroupedByLedgerAccount/grouped/AccountNum |
| 8      | CompAuxLib    | Alphanumérique | Le libellé de compte auxiliaire (à blanc si non utilisé) | The auxiliary account description. This field is blank if it isn't used. | CustTransGroupedByLedgerAccount/\$PartyName |
| 9      | PieceRef      | Alphanumérique | La référence de la pièce justificative | The reference of the supporting document. | CustTransGroupedByLedgerAccount/\$PieceNum |
| 10     | PieceDate     | Date           | La date de la pièce justificative | The date of the supporting document. | CustTransGroupedByLedgerAccount/\$PieceDate |
| 11     | EcritureLib   | Alphanumérique | Le libellé de l'écriture comptable | The wording of the accounting entry. | CustTransGroupedByLedgerAccount/\$EcritureLib |
| 12     | Montant       | Numérique      | Le montant au débit/ au crédit | The debit/credit amount. | CustTransGroupedByLedgerAccount/\$AbsAmount |
| 13     | Sens          | Numérique      | Le sens: "D" au débit; "C" au crédit | The direction: **D** = debit, **C** = credit | CustTransGroupedByLedgerAccount/\$Direction |
| 14     | EcritureLet   | Alphanumérique | Le lettrage de l'écriture comptable (à blanc si non utilisé) | The lettering of the accounting entry. This field is blank if it isn't used. | \$deEmpty |
| 15     | DateLet       | Date           | La date de lettrage (à blanc si non utilisé) | The lettering date. This field is blank if it isn't used. | \$deDateNull |
| 16     | ValidDate     | Date           | La date de validation de l'écriture comptable | The validation date of the accounting entry. | CustTransGroupedByLedgerAccount/\$ValidDate |
| 17     | Montantdevise | Numérique      | Le montant en devise (à blanc si non utilisé) | The amount in currency. This field is blank if it isn't used. | CustTransGroupedByLedgerAccount/aggregated/AmountCur |
| 18     | Idevise       | Alphanumérique | L'identifiant de la devise (à blanc si non utilisé) | The currency identifier. This field is blank if it isn't used. | CustTransGroupedByLedgerAccount/grouped/CurrencyCode |

## <a id="vendors-balances"></a>Vendors fiscal year opening balances annex 

Vendors fiscal year opening transactions are posted as summary transactions in general ledger. To provide detailed information on fiscal year opening transactions by vendors, the **Vendors fiscal year opening balances annex** is implemented. This annex collects amounts of opening balances by vendors on the beginning of the fiscal year and represents this information in combination with opening transaction voucher from general ledger.

The following table shows the **Vendors fiscal year opening balances annex** data structure definitions.

| Number | Name          | Type           | Description (FR) | Description (EN) | ER data source |
|--------|---------------|----------------|------------------|------------------|----------------|
| 1      | JournalCode   | Alphanumérique | Le code journal de l'écriture comptable | The journal code of the accounting entry. | Not included |
| 2      | JournalLib    | Alphanumérique | Le libellé journal de l'écriture comptable | The journal caption of the accounting entry. | VendTransGroupedByLedgerAccount/\$JournalLibText |
| 3      | EcritureNum   | Alphanumérique | Le numéro sur une séquence continue de l'écriture comptable | The number in a continuous sequence for the accounting entry. | VendTransGroupedByLedgerAccount/\$Voucher |
| 4      | EcritureDate  | Date           | La date de comptabilisation de l'écriture comptable | The posting date of the accounting entry. | VendTransGroupedByLedgerAccount/\$Date |
| 5      | CompteNum     | Alphanumérique | Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français | The account number, the first three characters of which must correspond to figures that respect the standards of the French chart of accounts. | VendTransGroupedByLedgerAccount/grouped/\$LedgerAccount |
| 6      | CompteLib     | Alphanumérique | Le libellé de compte, conformément à la nomenclature du plan comptable français | The account name in accordance with the nomenclature of the French chart of accounts. | VendTransGroupedByLedgerAccount/\$LedgerAccountName |
| 7      | CompAuxNum    | Alphanumérique | Le numéro de compte auxiliaire (à blanc si non utilisé) | The auxiliary account number. This field is blank if it isn't used. | VendTransGroupedByLedgerAccount/grouped/AccountNum |
| 8      | CompAuxLib    | Alphanumérique | Le libellé de compte auxiliaire (à blanc si non utilisé) | The auxiliary account description. This field is blank if it isn't used. | VendTransGroupedByLedgerAccount/\$PartyName |
| 9      | PieceRef      | Alphanumérique | La référence de la pièce justificative | The reference of the supporting document. | VendTransGroupedByLedgerAccount/\$PieceNum |
| 10     | PieceDate     | Date           | La date de la pièce justificative | The date of the supporting document. | VendTransGroupedByLedgerAccount/\$PieceDate |
| 11     | EcritureLib   | Alphanumérique | Le libellé de l'écriture comptable | The wording of the accounting entry. | VendTransGroupedByLedgerAccount/\$EcritureLib |
| 12     | Montant       | Numérique      | Le montant au débit/ au crédit | The debit/credit amount. | VendTransGroupedByLedgerAccount/\$AbsAmount |
| 13     | Sens          | Numérique      | Le sens: "D" au débit; "C" au crédit | The direction: **D** = debit, **C** = credit | VendTransGroupedByLedgerAccount/\$Direction |
| 14     | EcritureLet   | Alphanumérique | Le lettrage de l'écriture comptable (à blanc si non utilisé) | The lettering of the accounting entry. This field is blank if it isn't used. | \$deEmpty |
| 15     | DateLet       | Date           | La date de lettrage (à blanc si non utilisé) | The lettering date. This field is blank if it isn't used. | \$deDateNull |
| 16     | ValidDate     | Date           | La date de validation de l'écriture comptable | The validation date of the accounting entry. | VendTransGroupedByLedgerAccount/\$ValidDate |
| 17     | Montantdevise | Numérique      | Le montant en devise (à blanc si non utilisé) | The amount in currency. This field is blank if it isn't used. | VendTransGroupedByLedgerAccount/aggregated/AmountCur |
| 18     | Idevise       | Alphanumérique | L'identifiant de la devise (à blanc si non utilisé) | The currency identifier. This field is blank if it isn't used. | VendTransGroupedByLedgerAccount/grouped/CurrencyCode |

## <a id="customers-transactions"></a>Customers transactions annex for the period specified

**Customers transactions annex for the period specified** annex can be requested to provide additional details on customers transactions. For example, in case a company uses [Allow multiple transactions within one voucher](../../finance/general-ledger/one-voucher.md) parameter on the **General** tab of the **General ledger parameters** page, one voucher can be assigned to multiple customers transactions. To provide detailed information by customers accounts for such scenario, **Customers transactions annex for the period specified** annex is implemented. 

The following table shows the **Customers transactions annex for the period specified** data structure definitions.

| Number | Name          | Type           | Description (FR) | Description (EN) | ER data source |
|--------|---------------|----------------|------------------|------------------|----------------|
| 1      | JournalCode   | Alphanumérique | Le code journal de l'écriture comptable | The journal code of the accounting entry. | \$CustTrans/\$JournalCodeText |
| 2      | JournalLib    | Alphanumérique | Le libellé journal de l'écriture comptable | The journal caption of the accounting entry. | \$CustTrans/\$JournalLibText |
| 3      | EcritureNum   | Alphanumérique | Le numéro sur une séquence continue de l'écriture comptable | The number in a continuous sequence for the accounting entry. | \$CustTrans/Voucher |
| 4      | EcritureDate  | Date           | La date de comptabilisation de l'écriture comptable | The posting date of the accounting entry. | \$CustTrans/TransDate |
| 5      | CompteNum     | Alphanumérique | Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français | The account number, the first three characters of which must correspond to figures that respect the standards of the French chart of accounts. | \$CustTrans/deLedgerAccount\_FR() |
| 6      | CompteLib     | Alphanumérique | Le libellé de compte, conformément à la nomenclature du plan comptable français | The account name in accordance with the nomenclature of the French chart of accounts. | \$CustTrans/deLedgerAccountName\_FR() |
| 7      | CompAuxNum    | Alphanumérique | Le numéro de compte auxiliaire (à blanc si non utilisé) | The auxiliary account number. This field is blank if it isn't used. | \$CustTrans/AccountNum |
| 8      | CompAuxLib    | Alphanumérique | Le libellé de compte auxiliaire (à blanc si non utilisé) | The auxiliary account description. This field is blank if it isn't used. | \$CustTrans/custTableName() |
| 9      | PieceRef      | Alphanumérique | La référence de la pièce justificative | The reference of the supporting document. | \$CustTrans/\$PieceNum |
| 10     | PieceDate     | Date           | La date de la pièce justificative | The date of the supporting document. | \$CustTrans/\$PieceDate |
| 11     | EcritureLib   | Alphanumérique | Le libellé de l'écriture comptable | The wording of the accounting entry. | \$CustTrans/deEcritureLib\_FR() |
| 12     | Montant       | Numérique      | Le montant au débit/ au crédit | The debit/credit amount. | \$CustTrans/\$AbsAmount |
| 13     | Sens          | Numérique      | Le sens: "D" au débit; "C" au crédit | The direction: **D** = debit, **C** = credit | \$CustTrans/\$Direction |
| 14     | EcritureLet   | Alphanumérique | Le lettrage de l'écriture comptable (à blanc si non utilisé) | The lettering of the accounting entry. This field is blank if it isn't used. | \$CustTrans/LastSettleVoucher |
| 15     | DateLet       | Date           | La date de lettrage (à blanc si non utilisé) | The lettering date. This field is blank if it isn't used. | \$CustTrans/LastSettleDate |
| 16     | ValidDate     | Date           | La date de validation de l'écriture comptable | The validation date of the accounting entry. | \$CustTrans/createdDateTime |
| 17     | Montantdevise | Numérique      | Le montant en devise (à blanc si non utilisé) | The amount in currency. This field is blank if it isn't used. | \$CustTrans/AmountCur|
| 18     | Idevise       | Alphanumérique | L'identifiant de la devise (à blanc si non utilisé) | The currency identifier. This field is blank if it isn't used. | \$CustTrans/CurrencyCode |

## <a id="vendors-transactions"></a>Vendors transactions annex for the period specified

**Vendors transactions annex for the period specified** annex can be requested to provide additional details on vendors transactions. For example, in case a company uses [Allow multiple transactions within one voucher](../../finance/general-ledger/one-voucher.md) parameter on the **General** tab of the **General ledger parameters** page, one voucher can be assigned to multiple vendors transactions. To provide detailed information by vendors accounts for such scenario, **Vendors transactions annex for the period specified** annex is implemented. 

The following table shows the **Vendors transactions annex for the period specified** data structure definitions.

| Number | Name          | Type           | Description (FR) | Description (EN) | ER data source |
|--------|---------------|----------------|------------------|------------------|----------------|
| 1      | JournalCode   | Alphanumérique | Le code journal de l'écriture comptable | The journal code of the accounting entry. | \$VendTrans/\$JournalCodeText |
| 2      | JournalLib    | Alphanumérique | Le libellé journal de l'écriture comptable | The journal caption of the accounting entry. | \$VendTrans/\$JournalLibText |
| 3      | EcritureNum   | Alphanumérique | Le numéro sur une séquence continue de l'écriture comptable | The number in a continuous sequence for the accounting entry. | \$VendTrans/Voucher |
| 4      | EcritureDate  | Date           | La date de comptabilisation de l'écriture comptable | The posting date of the accounting entry. | \$VendTrans/TransDate |
| 5      | CompteNum     | Alphanumérique | Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français | The account number, the first three characters of which must correspond to figures that respect the standards of the French chart of accounts. | \$VendTrans/deLedgerAccount\_FR() |
| 6      | CompteLib     | Alphanumérique | Le libellé de compte, conformément à la nomenclature du plan comptable français | The account name in accordance with the nomenclature of the French chart of accounts. | \$VendTrans/deLedgerAccountName\_FR() |
| 7      | CompAuxNum    | Alphanumérique | Le numéro de compte auxiliaire (à blanc si non utilisé) | The auxiliary account number. This field is blank if it isn't used. | \$VendTrans/AccountNum |
| 8      | CompAuxLib    | Alphanumérique | Le libellé de compte auxiliaire (à blanc si non utilisé) | The auxiliary account description. This field is blank if it isn't used. | \$VendTrans/custTableName() |
| 9      | PieceRef      | Alphanumérique | La référence de la pièce justificative | The reference of the supporting document. | \$VendTrans/\$PieceNum |
| 10     | PieceDate     | Date           | La date de la pièce justificative | The date of the supporting document. | \$VendTrans/\$PieceDate |
| 11     | EcritureLib   | Alphanumérique | Le libellé de l'écriture comptable | The wording of the accounting entry. | \$VendTrans/deEcritureLib\_FR() |
| 12     | Montant       | Numérique      | Le montant au débit/ au crédit | The debit/credit amount. | \$VendTrans/\$AbsAmount |
| 13     | Sens          | Numérique      | Le sens: "D" au débit; "C" au crédit | The direction: **D** = debit, **C** = credit | \$VendTrans/\$Direction |
| 14     | EcritureLet   | Alphanumérique | Le lettrage de l'écriture comptable (à blanc si non utilisé) | The lettering of the accounting entry. This field is blank if it isn't used. | \$VendTrans/LastSettleVoucher |
| 15     | DateLet       | Date           | La date de lettrage (à blanc si non utilisé) | The lettering date. This field is blank if it isn't used. | \$VendTrans/LastSettleDate |
| 16     | ValidDate     | Date           | La date de validation de l'écriture comptable | The validation date of the accounting entry. | \$VendTrans/createdDateTime |
| 17     | Montantdevise | Numérique      | Le montant en devise (à blanc si non utilisé) | The amount in currency. This field is blank if it isn't used. | \$VendTrans/AmountCur |
| 18     | Idevise       | Alphanumérique | L'identifiant de la devise (à blanc si non utilisé) | The currency identifier. This field is blank if it isn't used. | \$VendTrans/CurrencyCode |

## <a id="fec-main-extended"></a>FEC main file including fiscal year opening balances details for customers and vendors

The following table shows the **FEC main file including fiscal year opening balances details for customers and vendors** data structure definitions.

| Number | Name          | Type           | Description (FR) | Description (EN) | ER data source |
|--------|---------------|----------------|------------------|------------------|----------------|
| 1      | JournalCode   | Alphanumérique | Le code journal de l'écriture comptable | The journal code of the accounting entry. | \$FECExtendedAggregation/\$JournalCodeText |
| 2      | JournalLib    | Alphanumérique | Le libellé journal de l'écriture comptable | The journal caption of the accounting entry. | \$FECExtendedAggregation/\$JournalLibText |
| 3      | EcritureNum   | Alphanumérique | Le numéro sur une séquence continue de l'écriture comptable | The number in a continuous sequence for the accounting entry. | \$FECExtendedAggregation/\$Voucher |
| 4      | EcritureDate  | Date           | La date de comptabilisation de l'écriture comptable | The posting date of the accounting entry. | \$FECExtendedAggregation/\$Date |
| 5      | CompteNum     | Alphanumérique | Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français | The account number, the first three characters of which must correspond to figures that respect the standards of the French chart of accounts. Information on multiple customers or vendors transactions can be found in respective annexes. | \$FECExtendedAggregation/\$LedgerAccount |
| 6      | CompteLib     | Alphanumérique | Le libellé de compte, conformément à la nomenclature du plan comptable français | The account name in accordance with the nomenclature of the French chart of accounts. | \$FECExtendedAggregation/\$LedgerAccountName |
| 7      | CompAuxNum    | Alphanumérique | Le numéro de compte auxiliaire (à blanc si non utilisé) | The auxiliary account number. This field is blank if it isn't used. | \$FECExtendedAggregation/\$AccountNum |
| 8      | CompAuxLib    | Alphanumérique | Le libellé de compte auxiliaire (à blanc si non utilisé) | The auxiliary account description. This field is blank if it isn't used. | \$FECExtendedAggregation/\$PartyName |
| 9      | PieceRef      | Alphanumérique | La référence de la pièce justificative | The reference of the supporting document. If reference of the supporting document cannot be found, this field is populated with EcritureNum. | \$FECExtendedAggregation/\$PieceNum |
| 10     | PieceDate     | Date           | La date de la pièce justificative | The date of the supporting document. | \$FECExtendedAggregation/\$PieceDate |
| 11     | EcritureLib   | Alphanumérique | Le libellé de l'écriture comptable | The wording of the accounting entry. | \$FECExtendedAggregation/\$EcritureLib |
| 12     | Montant       | Numérique      | Le montant au débit/ au crédit | The debit/credit amount. | \$FECExtendedAggregation/\$AbsAmount |
| 13     | Sens          | Numérique      | Le sens: "D" au débit; "C" au crédit | The direction: **D** = debit, **C** = credit | \$FECExtendedAggregation/\$Direction |
| 14     | EcritureLet   | Alphanumérique | Le lettrage de l'écriture comptable (à blanc si non utilisé) | The lettering of the accounting entry. This field is blank if it isn't used. | \$FECExtendedAggregation/\$LastSettleVoucher |
| 15     | DateLet       | Date           | La date de lettrage (à blanc si non utilisé) | The lettering date. This field is blank if it isn't used. | \$FECExtendedAggregation/\$LastSettleDate |
| 16     | ValidDate     | Date           | La date de validation de l'écriture comptable | The validation date of the accounting entry. | \$FECExtendedAggregation/\$ValidDate |
| 17     | Montantdevise | Numérique      | Le montant en devise (à blanc si non utilisé) | The amount in currency. This field is blank if it isn't used. | \$FECExtendedAggregation/\$AmountCur |
| 18     | Idevise       | Alphanumérique | L'identifiant de la devise (à blanc si non utilisé) | The currency identifier. This field is blank if it isn't used. | $FECExtendedAggregation/$CurrencyCode |

## <a id="missing-numbers-justification"></a>Missing numbers justification annex

As of Finance version 10.0.23, the **Missing numbers justification** annex represents data that is collected from Finance for the following scenarios where the consistency of the number sequence for general ledger account entries (voucher) can be interrupted in the FEC Main file:

- **Scenario 1**: A general ledger account entry is created in accounting but isn't reported in the FEC when the amount is 0.00.
- **Scenario 2**: A voucher number is used for an inventory transaction that has a zero amount that isn't reflected in the general ledger account entries table.
- **Scenario 3**: A gap in the number sequence for general ledger account entries occurs because of a technical issue.

Use the [Missing numbers justification](#missing-numbers-justification) annex to report general ledger account transactions that are missing in the FEC Main file for the preceding reasons.

The following table shows the **FEC main file including fiscal year opening balances details for customers and vendors** data structure definitions.

| Number | Name          | Type           | Description (FR) | Description (EN) | ER data source |
|--------|---------------|----------------|------------------|------------------|----------------|
| 1      | JournalCode   | Alphanumérique | Le code journal de l'écriture comptable | The journal code of the accounting entry. | <p>\$VouchersOmissions/\$JournalCodeText</p><ul><li>**Scenario 1:** GeneralJournalView_FR.GeneralJournalEntrySubledgerVoucher</li><li>**Scenario 2:** InventTrans.VoucherPhysical</li><li>**Scenario 3:** Autogenerated missing voucher number</li></ul> |
| 2      | JournalLib    | Alphanumérique | Le libellé journal de l'écriture comptable | The journal caption of the accounting entry. | <p>$VouchersOmissions/$JournalLib</p><ul><li>**Scenario 1:** GeneralJournalView_FR.\'getGeneralJournalEntry()\'.\'deJournalLib_FR()\'</li><li>**Scenario 2:** \"Stock\"</li><li>**Scenario 3:** Empty value</li></ul> |
| 3      | EcritureNum   | Alphanumérique | Le numéro sur une séquence continue de l'écriture comptable | The number in a continuous sequence for the accounting entry. | $VouchersOmissions/$Voucher |
| 4      | EcritureDate  | Date           | La date de comptabilisation de l'écriture comptable | The posting date of the accounting entry. | <p>$VouchersOmissions/$Date</p><ul><li>**Scenario 1:** GeneralJournalView_FR.GeneralJournalEntryAccountingDate</li><li>**Scenario 2:** InventTrans.DatePhysical</li><li>**Scenario 3:** Empty value</li></ul> |
| 5      | CompteNum     | Alphanumérique | Le numéro de compte, dont les trois premiers caractères doivent correspondre à des chiffres respectant les normes du plan comptable français | The account number, the first three characters of which must correspond to figures that respect the standards of the French chart of accounts. Information on multiple customers or vendors transactions can be found in respective annexes. | <p>$VouchersOmissions/$AccountNum</p><ul><li>**Scenario 1:** GeneralJournalView_FR.GeneralJournalAccountEntryMainAccount</li><li>**Scenario 2:** Empty value</li><li>**Scenario 3:** Empty value</li></ul> |
| 6      | CompteLib     | Alphanumérique | Le libellé de compte, conformément à la nomenclature du plan comptable français | The account name in accordance with the nomenclature of the French chart of accounts. | <p>$VouchersOmissions/$AccountName</p><ul><li>**Scenario 1:** GeneralJournalView_FR.\'getGeneralJournalAccountEntry()\'.getMainAccountName()</li><li>**Scenario 2:** Empty value</li><li>**Scenario 3:** Empty value</li></ul> |
| 7      | CompAuxNum    | Alphanumérique | Le numéro de compte auxiliaire (à blanc si non utilisé) | The auxiliary account number. This field is blank if it isn't used. | <p>$VouchersOmissions/$CompteAuxNum</p><ul><li>**Scenario 1:** GeneralJournalView_FR.\'getGeneralJournalAccountEntry()\'.\'deCompteAuxNum_FR()\'</li><li>**Scenario 2:** Not applicable</li><li>**Scenario 3:** Not applicable</li></ul> |
| 8      | CompAuxLib    | Alphanumérique | Le libellé de compte auxiliaire (à blanc si non utilisé) | The auxiliary account description. This field is blank if it isn't used. | <p>$VouchersOmissions/$CompteAuxLib</p><ul><li>**Scenario 1:** GeneralJournalView_FR.\'getGeneralJournalAccountEntry()\'.\'deCompteAuxLib_FR()\'</li><li>**Scenario 2:** Not applicable</li><li>**Scenario 3:** Not applicable</li></ul> |
| 9      | PieceRef      | Alphanumérique | La référence de la pièce justificative | The reference of the supporting document. If reference of the supporting document cannot be found, this field is populated with EcritureNum. | <p>$VouchersOmissions/$PieceRef</p><ul><li>**Scenario 1:** GeneralJournalView_FR.\'getGeneralJournalEntry()\'.\'dePieceNum_FR()\'</li><li>**Scenario 2:** InventTrans.VoucherPhysical</li><li>**Scenario 3:** Empty value</li></ul> |
| 10     | PieceDate     | Date           | La date de la pièce justificative | The date of the supporting document. | <p>$VouchersOmissions/$PieceDate</p><ul><li>**Scenario 1:** GeneralJournalView_FR.\'getGeneralJournalEntry()\'.\'dePieceDate_FR()\'</li><li>**Scenario 2:** InventTrans.DatePhysical</li><li>**Scenario 3:** Empty value</li></ul> |
| 11     | EcritureLib   | Alphanumérique | Le libellé de l'écriture comptable | The wording of the accounting entry. | <p>$VouchersOmissions/$EcritureLib</p><ul><li>**Scenario 1:** GeneralJournalView_FR.\'getGeneralJournalAccountEntry()\'</li><li>**Scenario 2:** \'InventTrans_\' and  InventTrans.RecID</li><li>**Scenario 3:** Empty value</li></ul> |
| 12     | Montant       | Numérique      | Le montant au débit/ au crédit | The debit/credit amount. | <p>$VouchersOmissions/$AbsAmount</p><ul><li>**Scenario 1:** GeneralJournalView_FR.GeneralJournalAccountEntryAccountingCurrencyAmount</li><li>**Scenario 2:** InventTrans.CostAmountPhysical</li><li>**Scenario 3:** \'0.00\'</li></ul> |
| 13     | Sens          | Numérique      | Le sens: "D" au débit; "C" au crédit | The direction: **D** = debit, **C** = credit | <p>$VouchersOmissions/$Direction</p><ul><li>**Scenario 1:** Debit\/credit indicator of the financial voucher (GeneralJournalView_FR.GeneralJournalAccountEntryAccountingCurrencyAmount)</li><li>**Scenario 2:** Debit\/credit indicator of the physical voucher (InventTrans.CostAmountPhysical)</li><li>**Scenario 3:** Empty value</li></ul> |
| 14     | EcritureLet   | Alphanumérique | Le lettrage de l'écriture comptable (à blanc si non utilisé) | The lettering of the accounting entry. This field is blank if it isn't used. | <p>$VouchersOmissions\/$EcritureLet</p><ul><li>**Scenario 1:** GeneralJournalAccountEntry_Extension.deEcritureLet_FR(GeneralJournalView_FR.\'getGeneralJournalAccountEntry()\',\'$Period_DateFrom', \'$Period_DateTo\')</li><li>**Scenario 2:** Not applicable</li><li>**Scenario 3:** Not applicable</li></ul> |
| 15     | DateLet       | Date           | La date de lettrage (à blanc si non utilisé) | The lettering date. This field is blank if it isn't used. | <p>$VouchersOmissions/$DateLet</p><ul><li>**Scenario 1:** GeneralJournalAccountEntry_Extension.deDateLet_FR(GeneralJournalView_FR.\'getGeneralJournalAccountEntry()\',\'$Period_DateFrom',\'$Period_DateTo\')</li><li>**Scenario 2:** Not applicable</li><li>**Scenario 3:** Not applicable</li></ul> |
| 16     | ValidDate     | Date           | La date de validation de l'écriture comptable | The validation date of the accounting entry. | <p>$VouchersOmissions/$Date</p><ul><li>**Scenario 1:** GeneralJournalView_FR.GeneralJournalEntryAccountingDate</li><li>**Scenario 2:** InventTrans.DatePhysical</li><li>**Scenario 3:** Empty value</li></ul> |
| 17     | Montantdevise | Numérique      | Le montant en devise (à blanc si non utilisé) | The amount in currency. This field is blank if it isn't used. | <p>$VouchersOmissions/$AmountCur</p><ul><li>**Scenario 1:** GeneralJournalView_FR.GeneralJournalAccountEntryTransactionCurrencyAmount</li><li>**Scenario 2:** InventTrans.CostAmountPhysical</li><li>**Scenario 3:** \'0.00\'</li></ul> |
| 18     | Idevise       | Alphanumérique | L'identifiant de la devise (à blanc si non utilisé) | The currency identifier. This field is blank if it isn't used. | <p>$VouchersOmissions/$Currency</p><ul><li>**Scenario 1:** GeneralJournalView_FR.GeneralJournalAccountEntryTransactionCurrencyCode</li><li>**Scenario 2:** InventTrans.CurrencyCode</li><li>**Scenario 3:** Not applicable</li></ul> |
