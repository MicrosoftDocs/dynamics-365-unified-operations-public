---
# required metadata

title: German audit file (GDPdU/GoBD) overview
description: Companies in Germany and some other countries/regions are legally required to provide an export of financial data in a machine-readable form. This article describes how the current version of Microsoft Dynamics 365 Finance supports the GDPdU/GoBD audit file requirements. It also shows the tables that are set up as examples in the electronic reporting configurations.
author: liza-golub
ms.date: 03/11/2021
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERWorkspace
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: ["59201", "intro-internal"]
ms.search.region: Austria, Germany
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# German audit file (GDPdU/GoBD) overview

[!include [banner](../includes/banner.md)]

Companies in Germany and some other countries/regions are legally required to provide an export of financial data in a machine-readable form. This article describes how Dynamics 365 Finance supports the GDPdU/GoBD audit file requirements. It also shows the tables that are set up as examples in the electronic reporting configurations.

Companies in Germany and some other countries/regions are legally required to export data for all transactions and master data from a fiscal year, and to provide this data to auditors within a reasonable time. The data must be collected in a specific file format, so that it can be imported to the auditor’s audit environment. This procedure is controlled by tax authorities. The data that must be exported depends on the requirements for an audit. For example, a typical set of exported data includes the following master data and transaction tables:

-   Main accounts
-   Ledger transactions
-   Tax codes
-   Tax transactions
-   Customer master data
-   Customer transactions
-   Vendor master data
-   Vendor transactions
-   Fixed assets master data
-   Fixed assets transactions

In the current version of Finance, functionality that lets the user export the required data is implemented as GDPdU-specific electronic reporting configurations. Task guides are also available that show how to import GDPdU-specific configurations, add another table group for export, and perform the export.

## Table groups and table definitions
The following sections list the tables that are set up as examples in the **German audit file** electronic reporting data model configuration. You can use these tables out of the box to export the data. You can also customize existing table groups and extend the list of supported table groups in the configuration of the **German audit file** electronic reporting data model.

### General ledger

The following tables show the General ledger data structure definitions.

#### Sachkonten

| Number | Feldname                  | Feldtyp | Beschreibung                                      | Electronic Reporting Data Source Path |
|-----|---------------------------|---------|---------------------------------------------------|------------------------------------------------------------|
| 1   | SACHKONTONUMMER           | Zeichen | Nummer des Sachkontos                             | MainAccount/MainAccountId                                  |
| 2   | SACHKONTONAME             | Zeichen | Bezeichnung des Sachkontos                        | MainAccount/Name                                           |
| 3   | SACHKONTOTYP              | Zeichen | Typ des Sachkontos                                | MainAccount/Type                                           |
| 4   | SACHKONTOSPERRE           | Zeichen | Gesperrt für manuelle Buchungen                   | MainAccount/isBlockedForManualEntry()                      |
| 5   | SACHKONTOEXCLUSIVBENUTZER | Zeichen | Exklusiver Benutzer dieses Sachkontos             | MainAccount/UserInfoId                                     |
| 6   | SACHKONTOBENUTZUNG        | Zeichen | Einstellung für einzelnen Benutzer des Sachkontos | MainAccount/ValidateUser                                   |
| 7   | KONTENART                 | Zeichen | Kontenart                                         | MainAccount/Type                                           |

#### Sachkontobuchungen

| Number | Feldname               | Feldtyp   | Beschreibung                                      | Electronic Reporting Data Source Path                                             |
|-----|------------------------|-----------|---------------------------------------------------|-----------------------------------------------------------------------------------|
| 1   | SACHKONTONUMMER        | Zeichen   | Nummer des Sachkontos                             | $GeneralJournalEntry/$GeneralJournalAccountEntry/$LedgerDimension/DisplayValue    |
| 2   | STEUERBUCHUNGSREFERENZ | Numerisch | Gibt es hierzu eine Mehrwertsteuerbuchung?-lfd Nr | $GeneralJournalEntry/$GeneralJournalAccountEntry/RecId                            |
| 3   | PERIODENCODE           | Zeichen   | Periodencode                                      | $Entries/$GeneralJournalEntry/$FiscalCalendarPeriodName                           |
| 4   | PERIODENZUGEHORIGKEIT  | Zeichen   | Vortrag, Normal oder Abschlussbuchung             | $GeneralJournalEntry/$FiscalCalendarPeriod/Type                                   |
| 5   | BUCHUNGSTYP            | Zeichen   | Buchungstyp                                       | $GeneralJournalEntry/$GeneralJournalAccountEntry/PostingType                      |
| 6   | KORREKTUR              | Zeichen   | Korrektur                                         | $GeneralJournalEntry/$GeneralJournalAccountEntry/IsCorrection                     |
| 7   | HABENBUCHUNG           | Zeichen   | Habenbuchung                                      | $GeneralJournalEntry/$GeneralJournalAccountEntry/IsCredit                         |
| 8   | BUCHUNGSBETRAG         | Num(2Dez) | Betrag der Buchung in Buchungswährung             | $GeneralJournalEntry/$GeneralJournalAccountEntry/TransactionCurrencyAmount        |
| 9   | BUCHUNGSWAHRUNG        | Zeichen   | Währung der Buchung                               | $GeneralJournalEntry/$GeneralJournalAccountEntry/TransactionCurrencyCode          |
| 10  | BUCHUNGSWERT           | Num(2Dez) | Wert der Buchung in Firmenwährung                 | $GeneralJournalEntry/$GeneralJournalAccountEntry/AccountingCurrencyAmount         |
| 11  | BUCHUNGSTEXT           | Zeichen   | Text zur Buchung                                  | $GeneralJournalEntry/$GeneralJournalAccountEntry/Text                                           |
| 12  | BUCHUNGSDATUM          | Datum     | Datum der Wertstellung                            | $GeneralJournalEntry/AccountingDate                                 |
| 13  | BUCHUNGSNUMMER         | Zeichen   | Interne Belegnummer der Buchung                   | $GeneralJournalEntry/SubledgerVoucher                               |
| 14  | BELEGDATUM             | Datum     | Datum des Belegs                                  | $GeneralJournalEntry/DocumentDate                                   |
| 15  | BELEGNUMMER            | Zeichen   | Externe Belegnummer der Buchung                   | $GeneralJournalEntry/DocumentNumber                                 |
| 16  | SPEZIALBUCHUNG         | Zeichen   | 0-Steuerbil.; andere Buchungsebene: int. Buchung  | $GeneralJournalEntry/PostingLayer                                   |
| 17  | ERFASSUNGSNUMMER       | Zeichen   | Nummer der Erfassung                              | $GeneralJournalEntry/$JournalizingJournal                                        |
| 18  | JOURNALZEILE           | Numerisch | Zeile des Journals                                | $GeneralJournalEntry/$JournalizingSeqNumber                                 |
| 19  | GEGENKONTO             | Zeichen   | Nummer des Gegenkontos                            | $GeneralJournalEntry/RecId                                          |
| 20  | DOKUMENT               | Zeichen   | Dokument                                          | $GeneralJournalEntry/DocumentNumber                                 |

### Tax ledger

The following tables show the Tax data structure definitions.

#### Umsatzsteuercodes

| Number | Feldname          | Feldtyp   | Beschreibung      | Electronic Reporting Data Source Path|
|-----|-------------------|-----------|-------------------|-------------------------------------------------------------------------|
| 1   | BUCHUNGSGRUNDLAGE | Zeichen   | Buchungsgrundlage | TaxData/$TaxTable/TaxBase                             |
| 2   | NAME              | Zeichen   | Name              | TaxData/$TaxTable/TaxName                             |
| 3   | PROZENTSATZ       | Num(2Dez) | Prozentsatz       | TaxData/TaxValue                            |
| 4   | GULTIGAB          | Datum     | Gültig ab         | TaxData/TaxFromDate                         |
| 5   | GULTIGBIS         | Datum     | Gültig bis        | TaxData/TaxToDate                           |

#### MehrwertsteuerGruppen

| Number | Feldname                      | Feldtyp | Beschreibung               | Electronic Reporting Data Source Path |
|-----|-------------------------------|---------|----------------------------|-------------------------------------------------|
| 1   | BESCHREIBUNG                  | Zeichen | Beschreibung               | TaxGroupData/$TaxGroupHeading/TaxGroupName     |
| 2   | MEHRWERTSTEUERGRUPPE          | Zeichen | Mehrwertsteuergruppe       | TaxGroupData/TaxGroup       |
| 3   | MWST\_AUF\_SKONTO\_STORNIEREN | Zeichen | MWSt auf Skonto stornieren | TaxGroupData/$TaxGroupHeading/TaxReverseOnCashDisc   |
| 4   | MWST\_CODE\_NAME              | Zeichen | MWSt Code Name             | TaxGroupData/$TaxTable/TaxName  |
| 5   | MEHRWERTSTEUERCODE            | Zeichen | Mehrwertsteuercode         | TaxGroupData/TaxCode    |
| 6   | ERWERBSSTEUER                 | Zeichen | Erwerbssteuer              | TaxGroupData/UseTax       |

#### Umsatzsteuerbuchungen

| Number | Feldname               | Feldtyp   | Beschreibung                                | Electronic Reporting Data Source Path |
|-----|------------------------|-----------|---------------------------------------------|--------------------------------------|
| 1   | STEUERART              | Zeichen   | Beschreibung der Steuerart                  | $TaxTrans/taxName()                                      |
| 2   | STEUERBUCHUNGSREFERENZ | Numerisch | Gibt es hierzu eine MWST-Buchung? - lfd Nr. | $TaxTrans/$TaxTransGeneralJournalAccountEntry/$GeneralJournalAccountEntryRecId                                          |
| 3   | MWST\_CODE             | Zeichen   | MWST Bezeichung                             | $TaxTrans/TaxCode                                        |
| 4   | WERTSTELLUNG           | Datum     | Datum der Wertstellung der Buchung          | $TaxTrans/TransDate                                      |
| 5   | BELEGNUMMER            | Zeichen   | Interne Nummer des Buchungsbelegs           | $TaxTrans/Voucher                                        |
| 6   | BUCHUNGSWAHRUNG        | Zeichen   | Währung der Buchung                         | $TaxTrans/CurrencyCode                                   |
| 7   | BUCHUNGSBETRAG         | Num(2Dez) | Betrag der Buchung                          | $TaxTrans/TaxAmountCur                                   |
| 8   | BUCHUNGSWERT           | Num(2Dez) | Wert der Buchung in Firmenwährung           | $TaxTrans/TaxAmount                                      |
| 9   | QUELLE                 | Zeichen   | Quelle                                      | $TaxTrans/Source                                         |
| 10  | BUCHUNGSGRUNDLAGE      | Zeichen   | Buchungsgrundlage                           | $TaxTrans/TaxDirection                                   |
| 11  | BELEGWAHRUNG           | Zeichen   | Belegwährung                                | $TaxTrans/SourceCurrencyCode                             |
| 12  | GRUNDLAGE              | Num(2Dez) | Grundlage                                   | $TaxTrans/SourceBaseAmountCur                            |
| 13  | PROZENTSATZ            | Num(2Dez) | Prozentsatz                                 | $TaxTrans/TaxValue                                       |
| 14  | MWST\_GRUPPE           | Zeichen   | MwSt Gruppe                                 | $TaxTrans/TaxGroup                                       |
| 15  | KONTO\_MWST\_AUSGABEN  | Zeichen   | Konto MwSt Ausgaben                         | $TaxTrans/accountName()                           |
| 16  | SACHKONTO              | Zeichen   | Sachkonto                                   | $TaxTrans/accountNameOperational()                         |
| 17  | ARTIKEL\_MWST\_GRUPPE  | Zeichen   | Artikel-Mehrwertsteuergruppe                | $TaxTrans/TaxItemGroup                                   |

### Accounts receivable

The following tables show the Accounts receivable data structure definitions.

#### Kunden

| Number | Feldname             | Feldtyp | Beschreibung                          | Electronic Reporting Data Source Path|
|-----|----------------------|---------|---------------------------------------|--------------------------------------|
| 1   | KUNDENKONTONUMMER    | Zeichen | Nummer des Kundenkontos               | CustTable/AccountNum                                     |
| 2   | KUNDENUSTIDNR        | Zeichen | USt-IdNr des Kunden                   | CustTable/getVatNumPrimaryRegistrationNumber()                                         |
| 3   | KUNDENSTRASSE        | Zeichen | Straße des Kunden                     | CustTable/$Party/$LogisticsPostalAddress/Street                                         |
| 4   | KUNDENPLZ            | Zeichen | Postleitzahl des Kunden               | CustTable/$Party/$LogisticsPostalAddress/ZipCode                                        |
| 5   | KUNDENORT            | Zeichen | Ort des Kunden                        | CustTable/$Party/$LogisticsPostalAddress/City                                           |
| 6   | KUNDENSTAAT          | Zeichen | Staat des Kunden                      | CustTable/$Party/$LogisticsPostalAddress/CountryRegionId                                |
| 7   | KUNDENNAME           | Zeichen | Name des Kunden                       | CustTable/$Party/Name                                           |
| 8   | KUNDENGRUPPE         | Zeichen | Gruppe, der der Kunde zugeordnet ist  | CustTable/CustGroup                                      |
| 9   | KUNDENEIGENEKONTONR  | Zeichen | Eigene Kontonummer beim Kunden        | CustTable/OurAccountNum                                  |
| 10  | KUNDENLIEFERANTENNR  | Zeichen | Lieferantenkonto bei uns              | CustTable/VendAccount                                    |
| 11  | KUNDENRECHNUNGSKONTO | Zeichen | Kundenkonto für Rechnungen            | CustTable/InvoiceAccount                                 |
| 12  | MWST\_GRUPPE         | Zeichen | MWSt Gruppe - Inland / EU / Drittland | CustTable/TaxGroup                                       |
| 13  | WÄHRUNG              | Zeichen | Währung                               | CustTable/Currency                                       |

#### Kundenbuchungen

| Number | Feldname                 | Feldtyp   | Beschreibung                          | Electronic Reporting Data Source Path |
|-----|--------------------------|-----------|---------------------------------------|-----------------------------------------------------------------------------------|
| 1   | KUNDENKONTONUMMER        | Zeichen   | Kontonummer des Kundenkontos          | $CustTrans/AccountNum                                     |
| 2   | BUCHUNGSNUMMER           | Zeichen   | Interne Belegnummer der Buchung       | $CustTrans/Voucher                                        |
| 3   | BUCHUNGSDATUM            | Datum     | Wertstellung der Buchung              | $CustTrans/TransDate                                      |
| 4   | BELEGNUMMER              | Zeichen   | Externe Belegnummer der Buchung       | $CustTrans/DocumentNum                                    |
| 5   | BELEGDATUM               | Datum     | Datum des externen Belegs             | $CustTrans/DocumentDate                                   |
| 6   | BUCHUNGSTEXT             | Zeichen   | Buchungstext der Buchung              | $CustTrans/Txt                                            |
| 7   | BUCHUNGSBETRAG           | Num(2Dez) | Betrag der Buchung in Buchungswährung | $CustTrans/AmountCur                                      |
| 8   | BUCHUNGSWAHRUNG          | Zeichen   | Währung der Buchung                   | $CustTrans/CurrencyCode                                   |
| 9   | BUCHUNGSWERT             | Num(2Dez) | Wert der Buchung in Firmenwährung     | $CustTrans/AmountMST                                      |
| 10  | LETZTER\_AUSGLEICHSBELEG | Zeichen   | Letzter Ausgleichsbeleg               | $CustTrans/LastSettleVoucher                              |
| 11  | LETZTER\_AUSGLEICH       | Datum     | Letzter Ausgleich                     | $CustTrans/LastSettleDate                                 |
| 12  | BUCHUNGSART              | Zeichen   | Buchungsart                           | $CustTrans/TransType                                      |

### Accounts payable

The following tables show the Accounts payable data structure definitions.

#### Lieferanten

| Number | Feldname                  | Feldtyp | Beschreibung                             | Electronic Reporting Data Source Path |
|-----|---------------------------|---------|------------------------------------------|------------------------------------------------------------------------------------|
| 1   | LIEFERANTENKONTONUMMER    | Zeichen | Nummer des Lieferantenkontos             | VendTable/AccountNum                                     |
| 2   | LIEFERANTENUSTIDNR        | Zeichen | USt-IdNr des Lieferanten                 | VendTableVendTable/getVatNumPrimaryRegistrationNumber()                                         |
| 3   | LIEFERANTENSTRASSE        | Zeichen | Straße des Lieferanten                   | VendTable/$Party/$LogisticsPostalAddress/Street                                         |
| 4   | LIEFERANTENPLZ            | Zeichen | Postleitzahl des Lieferanten             | VendTable/$Party/$LogisticsPostalAddress/ZipCode                                        |
| 5   | LIEFERANTENORT            | Zeichen | Ort des Lieferanten                      | VendTable/$Party/$LogisticsPostalAddress/City                                           |
| 6   | LIEFERANTENSTAAT          | Zeichen | Staat des Lieferanten                    | VendTable/$Party/$LogisticsPostalAddress/CountryRegionId                                |
| 7   | LIEFERANTENNAME           | Zeichen | Name des Lieferanten                     | VendTable/$Party/Name                                           |
| 8   | LIEFERANTENGRUPPE         | Zeichen | Gruppe, der der Lieferant zugeordnet ist | VendTable/VendGroup                                      |
| 9   | LIEFERANTENRECHNUNGSKONTO | Zeichen | Lieferantenkonto für Rechnungsstellung   | VendTable/InvoiceAccount                                 |
| 10  | MWST\_GRUPPE              | Zeichen | MWSt Gruppe - Inland / EU / Drittland    | VendTable/TaxGroup                                       |
| 11  | WAHRUNG                   | Zeichen | Währung                                  | VendTable/Currency                                       |

#### Lieferantenbuchungen

| Number | Feldname                 | Feldtyp   | Beschreibung                          | Electronic Reporting Data Source Path |
|-----|--------------------------|-----------|---------------------------------------|-------------------------------------------------------------------------------------|
| 1   | LIEFERANTENKONTONUMMER   | Zeichen   | Nummer des Lieferantenkontos          | $VendTrans/AccountNum                                     |
| 2   | BUCHUNGSNUMMER           | Zeichen   | Interne Belegnummer der Buchung       | $VendTrans/Voucher                                        |
| 3   | BUCHUNGSDATUM            | Datum     | Wertstellung der Buchung              | $VendTrans/TransDate                                      |
| 4   | BELEGNUMMER              | Zeichen   | Externe Belegnummer der Buchung       | $VendTrans/DocumentNum                                    |
| 5   | BELEGDATUM               | Datum     | Datum des externen Belegs             | $VendTrans/DocumentDate                                   |
| 6   | BUCHUNGSTEXT             | Zeichen   | Buchungstext der Buchung              | $VendTrans/Txt                                            |
| 7   | BUCHUNGSBETRAG           | Num(2Dez) | Betrag der Buchung in Buchungswährung | $VendTrans/AmountCur                                      |
| 8   | BUCHUNGSWAHRUNG          | Zeichen   | Währung der Buchung                   | $VendTrans/CurrencyCode                                   |
| 9   | BUCHUNGSWERT             | Num(2Dez) | Wert der Buchung in Firmenwährung     | $VendTrans/AmountMST                                      |
| 10  | LETZTER\_AUSGLEICHSBELEG | Zeichen   | Letzter Ausgleichsbeleg               | $VendTrans/LastSettleVoucher                              |
| 11  | LETZTER\_AUSGLEICH       | Datum     | Letzter Ausgleich                     | $VendTrans/LastSettleDate                                 |
| 12  | BUCHUNGSART              | Zeichen   | Buchungsart                           | $VendTrans/TransType                                      |
| 13  | STATUS                   | Zeichen   | Status                                | $VendTrans/Approved                                       |

### Fixed assets

Starting in version **33** of the **Data export model** configuration, Fixed assets data export is supported.

The following tables show the Fixed assets data structure definitions.

#### Anlagen

| Number | Feldname       | Feldtyp | Beschreibung                                 | Electronic Reporting Data Source Path |
|------------|--------------------|-------------|--------------------------------------------------|-------------------------------------------|
| 1          | ANLAGENNUMMER      | Zeichen     | Interne Nummer der Anlage                        | AssetTable/AssetId                        |
| 2          | ANLAGENBEZEICHNUNG | Zeichen     | Bezeichnung der Anlage                           | AssetTable/Name                           |
| 3          | ANLAGENGRUPPE      | Zeichen     | Gruppe, der die Anlage zugeordnet ist            | AssetTable/AssetGroup                     |
| 4          | ANLAGENTYP         | Zeichen     | Typ der Anlage                                   | AssetTable/AssetType                      |
| 5          | ANLAGENSTANDORT    | Zeichen     | Standort der Anlage                              | AssetTable/Location                       |
| 6          | HAUPTANLAGE        | Zeichen     | Nummer der Anlage, der die Anlage zugeordnet ist | AssetTable/MainAssetId                    |
| 7          | ANLAGENHERSTELLER  | Zeichen     | Hersteller der Anlage                            | AssetTable/Make                           |
| 8          | ANLAGENMODELL      | Zeichen     | Modellnummer der Anlage                          | AssetTable/Model                          |
| 9          | STATUS             | Zeichen     | Status der Anlage, ob vorhanden oder nicht       | AssetTable/\$AssetBook/Status             |

#### Anlagenbuchungen

| Number | Feldname       | Feldtyp | Beschreibung                                 | Electronic Reporting Data Source Path |
|------------|-----------------|-------------|-----------------------------------------------|--------------------------------------------------------|
| 1          | ANLAGENNUMMER   | Zeichen     | Interne Nummer der Anlage                     | \$AssetTransJoin/\$AssetTrans/AssetId                  |
| 2          | WERTSTELLUNG    | Datum       | Datum der Wertstellung der Buchung            | \$AssetTransJoin/\$AssetTrans/TransDate                |
| 3          | BELEGNUMMER     | Zeichen     | Interne Nummer des Buchungsbelegs             | \$AssetTransJoin/\$AssetTrans/Voucher                  |
| 4          | BUCHUNGSBETRAG  | Num(2Dez)   | Betrag der Buchung                            | \$AssetTransJoin/\$AssetTrans/AmountCur                |
| 5          | BUCHUNGSWÄHRUNG | Zeichen     | Währung der Buchung                           | \$AssetTransJoin/\$AssetTrans/CurrencyCode             |
| 6          | BUCHUNGSWERT    | Num(2Dez)   | Wert der Buchung in Firmenwährung             | \$AssetTransJoin/\$AssetTrans/AmountMST                |
| 7          | BUCHUNGSART     | Zeichen     | Art der Anlagenbuchung                        | \$AssetTransJoin/\$AssetTrans/TransType                |
| 8          | BUCHUNGSTEXT    | Zeichen     | Text zur Anlagenbuchung                       | \$AssetTransJoin/\$AssetTrans/Txt                      |
| 9          | ANLAGENGRUPPE   | Zeichen     | Gruppe, der die Anlagenbuchung zugeordnet ist | \$AssetTransJoin/\$AssetTrans/AssetGroup               |
| 10         | BUCHUNGSEBENE   | Zeichen     | 0- Steuerbilanz; sonst: interne Buchungen     | \$AssetTransJoin/\$AssetBookTable/CurrentOperationsTax |

## Additional resources

- [Electronic Reporting overview](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md)
- [Import German audit file configuration](./tasks/import-german-audit-file-configuration.md)
- [Customize German audit file configuration](./tasks/customize-german-audit-file-configuration.md)
- [Generate German audit file](./tasks/german-audit-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
