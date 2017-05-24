---
# required metadata

title: German audit file (GDPdU/GoBD)
description: Companies in Germany and some other countries/regions are legally required to provide an export of financial data in a machine-readable form. This article describes how the current version of Microsoft Dynamics 365 for Operations supports the GDPdU/GoBD audit file requirements. It also shows the tables that are set up as examples in the electronic reporting configurations.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 59201
ms.assetid: 0f885fd8-5425-48df-bc4d-a83c3789dd59
ms.search.region: Austria, Germany
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# German audit file (GDPdU/GoBD)

[!include[banner](../includes/banner.md)]


Companies in Germany and some other countries/regions are legally required to provide an export of financial data in a machine-readable form. This article describes how the current version of Microsoft Dynamics 365 for Operations supports the GDPdU/GoBD audit file requirements. It also shows the tables that are set up as examples in the electronic reporting configurations.

Companies in Germany and some other countries/regions are legally required to export data for all transactions and master data from a fiscal year, and to provide this data to auditors within a reasonable time. The data must be collected in a specific file format, so that it can be imported to the auditor’s audit environment. This procedure is controlled by tax authorities. The data that must be exported depends on the requirements for an audit. For example, a typical set of exported data includes the following master data and transaction tables:

-   Main accounts
-   Ledger transactions
-   Tax codes
-   Tax transactions
-   Customer master data
-   Customer transactions
-   Vendor master data
-   Vendor transactions
-   Item master data
-   Item transactions
-   Fixed assets master data
-   Fixed assets transactions

In the current version of Microsoft Dynamics 365 for Operations, functionality that lets the user export the required data is implemented as GDPdU-specific electronic reporting configurations. Task guides are also available that show how to import GDPdU-specific configurations, add another table group for export, and perform the export.

## Table groups and table definitions
The following sections list the tables that are set up as examples in the GDPdU electronic data model configuration. You can use these tables out of the box to export the data. You can also customize existing table groups and extend the list of supported table groups in the configuration of the GDPdU electronic reporting data model.

### General ledger

The following tables show the General leger data structure definitions.

#### Sachkonten

|     | Feldname                  | Feldtyp | Beschreibung                                      | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|---------------------------|---------|---------------------------------------------------|--------------------------------------|------------------------------------------------|
| 1   | SACHKONTONUMMER           | Zeichen | Nummer des Sachkontos                             | MainAccount                          | MainAccountId                                  |
| 2   | SACHKONTONAME             | Zeichen | Bezeichnung des Sachkontos                        | MainAccount                          | Name                                           |
| 3   | SACHKONTOTYP              | Zeichen | Typ des Sachkontos                                | MainAccount                          | Type                                           |
| 4   | SACHKONTOSPERRE           | Zeichen | Gesperrt für manuelle Buchungen                   | MainAccount                          | isBlockedForManualEntry()                      |
| 5   | SACHKONTOEXCLUSIVBENUTZER | Zeichen | Exklusiver Benutzer dieses Sachkontos             | MainAccount                          | UserInfoId                                     |
| 6   | SACHKONTOBENUTZUNG        | Zeichen | Einstellung für einzelnen Benutzer des Sachkontos | MainAccount                          | ValidateUser                                   |
| 7   | KONTENART                 | Zeichen | Kontenart                                         | MainAccount                          | Type                                           |

#### Sachkontobuchungen

|     | Feldname               | Feldtyp   | Beschreibung                                      | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|------------------------|-----------|---------------------------------------------------|--------------------------------------|------------------------------------------------|
| 1   | SACHKONTONUMMER        | Zeichen   | Nummer des Sachkontos                             | DiensionAttributeValueCombination    | DisplayValue                                   |
| 2   | BUCHUNGSDATUM          | Datum     | Datum der Wertstellung                            | GeneralJournalEntry                  | AccountingDate                                 |
| 3   | BUCHUNGSNUMMER         | Zeichen   | Interne Belegnummer der Buchung                   | GeneralJournalEntry                  | SubledgerVoucher                               |
| 4   | BUCHUNGSTEXT           | Zeichen   | Text zur Buchung                                  | GeneralJournalAccountEntry           | Text                                           |
| 5   | BUCHUNGSBETRAG         | Num(2Dez) | Betrag der Buchung in Buchungswährung             | GeneralJournalAccountEntry           | TransactionCurrencyAmount                      |
| 6   | BUCHUNGSWAHRUNG        | Zeichen   | Währung der Buchung                               | GeneralJournalAccountEntry           | TransactionCurrencyCode                        |
| 7   | BUCHUNGSWERT           | Num(2Dez) | Wert der Buchung in Firmenwährung                 | GeneralJournalAccountEntry           | AccountingCurrencyAmount                       |
| 8   | BELEGDATUM             | Datum     | Datum des Belegs                                  | GeneralJournalEntry                  | DocumentDate                                   |
| 9   | BELEGNUMMER            | Zeichen   | Externe Belegnummer der Buchung                   | GeneralJournalEntry                  | DocumentNumber                                 |
| 10  | SPEZIALBUCHUNG         | Zeichen   | 0-Steuerbil.; andere Buchungsebene: int. Buchung  | GeneralJournalEntry                  | PostingLayer                                   |
| 11  | STEUERBUCHUNGSREFERENZ | Numerisch | Gibt es hierzu eine Mehrwertsteuerbuchung?-lfd Nr | GeneralJournalAccountEntry           | displaySalesTaxTransId()                       |
| 12  | PERIODENZUGEHORIGKEIT  | Zeichen   | Vortrag, Normal oder Abschlussbuchung             | FiscalCalendarPeriod                 | Type                                           |
| 13  | ERFASSUNGSNUMMER       | Zeichen   | Nummer der Erfassung                              | LedgerEntryJournalizing              | Journal                                        |
| 14  | JOURNALZEILE           | Numerisch | Zeile des Journals                                | LedgerEntryJournalizing              | SequenceNumber                                 |
| 15  | GEGENKONTO             | Zeichen   | Nummer des Gegenkontos                            | GeneralJournalAccountEntry           | RecId                                          |
| 16  | BUCHUNGSTYP            | Zeichen   | Buchungstyp                                       | GeneralJournalAccountEntry           | PostingType                                    |
| 17  | KORREKTUR              | Zeichen   | Korrektur                                         | GeneralJournalAccountEntry           | IsCorrection                                   |
| 18  | HABENBUCHUNG           | Zeichen   | Habenbuchung                                      | GeneralJournalAccountEntry           | IsCredit                                       |
| 19  | PERIODENCODE           | Zeichen   | Periodencode                                      | FiscalCalendarPeriod                 | Type                                           |
| 20  | DOKUMENT               | Zeichen   | Dokument                                          | GeneralJournalEntry                  | DocumentNumber                                 |

### Tax ledger

The following tables show the Tax data structure definitions.

#### Umsatzsteuercodes

|     | Feldname          | Feldtyp   | Beschreibung      | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|-------------------|-----------|-------------------|--------------------------------------|------------------------------------------------|
| 1   | NAME              | Zeichen   | Name              | TaxTable                             | TaxName                                        |
| 2   | BUCHUNGSGRUNDLAGE | Zeichen   | Buchungsgrundlage | TaxTable                             | TaxBase                                        |
| 3   | PROZENTSATZ       | Num(2Dez) | Prozentsatz       | TaxData                              | TaxValue                                       |
| 4   | GULTIGAB          | Datum     | Gültig ab         | TaxData                              | TaxFromDate                                    |
| 5   | GULTIGBIS         | Datum     | Gültig bis        | TaxData                              | TaxToDate                                      |

#### MehrwertsteuerGruppen

|     | Feldname                      | Feldtyp | Beschreibung               | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|-------------------------------|---------|----------------------------|--------------------------------------|------------------------------------------------|
| 1   | MEHRWERTSTEUERGRUPPE          | Zeichen | Mehrwertsteuergruppe       | TaxGroupData                         | TaxGroup                                       |
| 2   | BESCHREIBUNG                  | Zeichen | Beschreibung               | TaxGroupHeading                      | TaxGroupName                                   |
| 3   | MWST\_AUF\_SKONTO\_STORNIEREN | Zeichen | MWSt auf Skonto stornieren | TaxGroupHeading                      | TaxReverseOnCashDisc                           |
| 4   | MEHRWERTSTEUERCODE            | Zeichen | Mehrwertsteuercode         | TaxGroupData                         | TaxCode                                        |
| 5   | MWST\_CODE\_NAME              | Zeichen | MWSt Code Name             | TaxTable                             | TaxName                                        |
| 6   | ERWERBSSTEUER                 | Zeichen | Erwerbssteuer              | TaxGroupData                         | UseTax                                         |

#### Umsatzsteuerbuchungen

|     | Feldname               | Feldtyp   | Beschreibung                                | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|------------------------|-----------|---------------------------------------------|--------------------------------------|------------------------------------------------|
| 1   | STEUERART              | Zeichen   | Beschreibung der Steuerart                  | TaxTrans                             | TaxName()                                      |
| 2   | MWST\_CODE             | Zeichen   | MWST Bezeichung                             | TaxTrans                             | TaxCode                                        |
| 3   | WERTSTELLUNG           | Datum     | Datum der Wertstellung der Buchung          | TaxTrans                             | TransDate                                      |
| 4   | BELEGNUMMER            | Zeichen   | Interne Nummer des Buchungsbelegs           | TaxTrans                             | Voucher                                        |
| 5   | BUCHUNGSWAHRUNG        | Zeichen   | Währung der Buchung                         | TaxTrans                             | CurrencyCode                                   |
| 6   | BUCHUNGSBETRAG         | Num(2Dez) | Betrag der Buchung                          | TaxTrans                             | TaxAmountCur                                   |
| 7   | BUCHUNGSWERT           | Num(2Dez) | Wert der Buchung in Firmenwährung           | TaxTrans                             | TaxAmount                                      |
| 8   | STEUERBUCHUNGSREFERENZ | Numerisch | Gibt es hierzu eine MWST-Buchung? - lfd Nr. | TaxTrans                             | RecId                                          |
| 9   | QUELLE                 | Zeichen   | Quelle                                      | TaxTrans                             | Source                                         |
| 10  | BUCHUNGSGRUNDLAGE      | Zeichen   | Buchungsgrundlage                           | TaxTrans                             | TaxDirection                                   |
| 11  | MEHRWERTSTEUERART      | Zeichen   | Mehrwertsteuerart                           | Not applicable                       | Not applicable                                 |
| 12  | BELEGWAHRUNG           | Zeichen   | Belegwährung                                | TaxTrans                             | SourceCurrencyCode                             |
| 13  | GRUNDLAGE              | Num(2Dez) | Grundlage                                   | TaxTrans                             | SourceBaseAmountCur                            |
| 14  | PROZENTSATZ            | Num(2Dez) | Prozentsatz                                 | TaxTrans                             | TaxValue                                       |
| 15  | MWST\_GRUPPE           | Zeichen   | MwSt Gruppe                                 | TaxTrans                             | TaxGroup                                       |
| 16  | KONTO\_MWST\_AUSGABEN  | Zeichen   | Konto MwSt Ausgaben                         | TaxTrans                             | mainAccountTaxRef ()                           |
| 17  | SACHKONTO              | Zeichen   | Sachkonto                                   | TaxTrans                             | mainAccountOperation()                         |
| 18  | ARTIKEL\_MWST\_GRUPPE  | Zeichen   | Artikel-Mehrwertsteuergruppe                | TaxTrans                             | TaxItemGroup                                   |

### Accounts receivable

The following tables show the Accounts receivable data structure definitions.

#### Kunden

|     | Feldname             | Feldtyp | Beschreibung                          | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|----------------------|---------|---------------------------------------|--------------------------------------|------------------------------------------------|
| 1   | KUNDENKONTONUMMER    | Zeichen | Nummer des Kundenkontos               | CustTable                            | AccountNum                                     |
| 2   | KUNDENNAME           | Zeichen | Name des Kunden                       | DirPartyTable                        | Name                                           |
| 3   | KUNDENSTRASSE        | Zeichen | Straße des Kunden                     | LogisticsPostalAddress               | Street                                         |
| 4   | KUNDENPLZ            | Zeichen | Postleitzahl des Kunden               | LogisticsPostalAddress               | ZipCode                                        |
| 5   | KUNDENORT            | Zeichen | Ort des Kunden                        | LogisticsPostalAddress               | City                                           |
| 6   | KUNDENSTAAT          | Zeichen | Staat des Kunden                      | LogisticsPostalAddress               | CountryRegionId                                |
| 7   | KUNDENGRUPPE         | Zeichen | Gruppe, der der Kunde zugeordnet ist  | CustTable                            | CustGroup                                      |
| 8   | KUNDENUSTIDNR        | Zeichen | USt-IdNr des Kunden                   | CustTable                            | VATNum                                         |
| 9   | KUNDENEIGENEKONTONR  | Zeichen | Eigene Kontonummer beim Kunden        | CustTable                            | OurAccountNum                                  |
| 10  | KUNDENLIEFERANTENNR  | Zeichen | Lieferantenkonto bei uns              | CustTable                            | VendAccount                                    |
| 11  | KUNDENRECHNUNGSKONTO | Zeichen | Kundenkonto für Rechnungen            | CustTable                            | InvoiceAccount                                 |
| 12  | MWST\_GRUPPE         | Zeichen | MWSt Gruppe - Inland / EU / Drittland | CustTable                            | TaxGroup                                       |
| 13  | WÄHRUNG              | Zeichen | Währung                               | CustTable                            | Currency                                       |

#### Kundenbuchungen

|     | Feldname                 | Feldtyp   | Beschreibung                          | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|--------------------------|-----------|---------------------------------------|--------------------------------------|------------------------------------------------|
| 1   | KUNDENKONTONUMMER        | Zeichen   | Kontonummer des Kundenkontos          | CustTrans                            | AccountNum                                     |
| 2   | BUCHUNGSNUMMER           | Zeichen   | Interne Belegnummer der Buchung       | CustTrans                            | Voucher                                        |
| 3   | BUCHUNGSDATUM            | Datum     | Wertstellung der Buchung              | CustTrans                            | TransDate                                      |
| 4   | BELEGNUMMER              | Zeichen   | Externe Belegnummer der Buchung       | CustTrans                            | DocumentNum                                    |
| 5   | BELEGDATUM               | Datum     | Datum des externen Belegs             | CustTrans                            | DocumentDate                                   |
| 6   | BUCHUNGSTEXT             | Zeichen   | Buchungstext der Buchung              | CustTrans                            | Txt                                            |
| 7   | BUCHUNGSBETRAG           | Num(2Dez) | Betrag der Buchung in Buchungswährung | CustTrans                            | AmountCur                                      |
| 8   | BUCHUNGSWAHRUNG          | Zeichen   | Währung der Buchung                   | CustTrans                            | CurrencyCode                                   |
| 9   | BUCHUNGSWERT             | Num(2Dez) | Wert der Buchung in Firmenwährung     | CustTrans                            | AmountMST                                      |
| 10  | LETZTER\_AUSGLEICHSBELEG | Zeichen   | Letzter Ausgleichsbeleg               | CustTrans                            | LastSettleVoucher                              |
| 11  | LETZTER\_AUSGLEICH       | Datum     | Letzter Ausgleich                     | CustTrans                            | LastSettleDate                                 |
| 12  | BUCHUNGSART              | Zeichen   | Buchungsart                           | CustTrans                            | TransType                                      |

### Accounts payable

The following tables show the Accounts payable data structure definitions.

#### Lieferanten

|     | Feldname                  | Feldtyp | Beschreibung                             | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|---------------------------|---------|------------------------------------------|--------------------------------------|------------------------------------------------|
| 1   | LIEFERANTENKONTONUMMER    | Zeichen | Nummer des Lieferantenkontos             | VendTable                            | AccountNum                                     |
| 2   | LIEFERANTENNAME           | Zeichen | Name des Lieferanten                     | DirPartyTable                        | Name                                           |
| 3   | LIEFERANTENSTRASSE        | Zeichen | Straße des Lieferanten                   | LogisticsPostalAddress               | Street                                         |
| 4   | LIEFERANTENPLZ            | Zeichen | Postleitzahl des Lieferanten             | LogisticsPostalAddress               | ZipCode                                        |
| 5   | LIEFERANTENORT            | Zeichen | Ort des Lieferanten                      | LogisticsPostalAddress               | City                                           |
| 6   | LIEFERANTENSTAAT          | Zeichen | Staat des Lieferanten                    | LogisticsPostalAddress               | CountryRegionId                                |
| 7   | LIEFERANTENGRUPPE         | Zeichen | Gruppe, der der Lieferant zugeordnet ist | VendTable                            | VendGroup                                      |
| 8   | LIEFERANTENUSTIDNR        | Zeichen | USt-IdNr des Lieferanten                 | VendTable                            | VATNum                                         |
| 9   | LIEFERANTENKUNDENKONTO    | Zeichen | Kundenkonto des Lieferanten bei uns      | Not applicable                       | Not applicable                                 |
| 10  | LIEFERANTENRECHNUNGSKONTO | Zeichen | Lieferantenkonto für Rechnungsstellung   | VendTable                            | InvoiceAccount                                 |
| 11  | MWST\_GRUPPE              | Zeichen | MWSt Gruppe - Inland / EU / Drittland    | VendTable                            | TaxGroup                                       |
| 12  | WAHRUNG                   | Zeichen | Währung                                  | VendTable                            | Currency                                       |

#### Lieferantenbuchungen

|     | Feldname                 | Feldtyp   | Beschreibung                          | Table in Dynamics 365 for Operations | Field or method in Dynamics 365 for Operations |
|-----|--------------------------|-----------|---------------------------------------|--------------------------------------|------------------------------------------------|
| 1   | LIEFERANTENKONTONUMMER   | Zeichen   | Nummer des Lieferantenkontos          | VendTrans                            | AccountNum                                     |
| 2   | BUCHUNGSNUMMER           | Zeichen   | Interne Belegnummer der Buchung       | VendTrans                            | Voucher                                        |
| 3   | BUCHUNGSDATUM            | Datum     | Wertstellung der Buchung              | VendTrans                            | TransDate                                      |
| 4   | BELEGNUMMER              | Zeichen   | Externe Belegnummer der Buchung       | VendTrans                            | DocumentNum                                    |
| 5   | BELEGDATUM               | Datum     | Datum des externen Belegs             | VendTrans                            | DocumentDate                                   |
| 6   | BUCHUNGSTEXT             | Zeichen   | Buchungstext der Buchung              | VendTrans                            | Txt                                            |
| 7   | BUCHUNGSBETRAG           | Num(2Dez) | Betrag der Buchung in Buchungswährung | VendTrans                            | AmountCur                                      |
| 8   | BUCHUNGSWAHRUNG          | Zeichen   | Währung der Buchung                   | VendTrans                            | CurrencyCode                                   |
| 9   | BUCHUNGSWERT             | Num(2Dez) | Wert der Buchung in Firmenwährung     | VendTrans                            | AmountMST                                      |
| 10  | LETZTER\_AUSGLEICHSBELEG | Zeichen   | Letzter Ausgleichsbeleg               | VendTrans                            | LastSettleVoucher                              |
| 11  | LETZTER\_AUSGLEICH       | Datum     | Letzter Ausgleich                     | VendTrans                            | LastSettleDate                                 |
| 12  | BUCHUNGSART              | Zeichen   | Buchungsart                           | VendTrans                            | TransType                                      |
| 13  | STATUS                   | Zeichen   | Status                                | VendTrans                            | Approved                                       |



See also
--------

[Electronic Reporting overview](/dynamics365/operations/dev-itpro/analytics/general-electronic-reporting)



