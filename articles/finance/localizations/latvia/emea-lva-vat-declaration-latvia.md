---
title: VAT declaration for Latvia
description: This article explains how to set up a value-added tax (VAT) declaration for legal entities in Latvia.
author: liza-golub
ms.date: 09/14/2024
ms.topic: article
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Latvia
ms.author: egolub
ms.search.validFrom: 2024-09-14
ms.dyn365.ops.version: AX 7.0.1
ms.search.form: TaxAuthority, TaxReportCollection, TaxReportVoucher, TaxTable
---

# VAT declaration for Latvia

[!include [banner](../../includes/banner.md)]

This article describes how to set up and generate a value-added tax (VAT) declaration for Latvia in the XML format, and how to preview it in Microsoft Excel.

The VAT declaration feature for Latvia supports filing a VAT return for companies that have [multiple VAT registrations](../global/emea-multiple-vat-registration-numbers.md) 
and for companies that report as a VAT group in the same system database.

## <a name="vat-declaration-overview"></a>VAT declaration overview

The VAT declaration feature for Latvia supports reporting of the following parts:

- **PVN**: declaration part which contains summary of total transaction value (both taxable, exempt, local reverse charge), calculated VAT and amount of input VAT on goods and services received, amendments to calculated VAT and input VAT (if any) and the final payable or receivable amount which is payable or receivable towards the Latvian State Budget;
- **PVN 1-I**: Amount of input VAT on goods and services purchased domestically;
- **PVN 1-II**: Amount of VAT on goods and services purchased from other European Union Member States;
- **PVN 1-III**: Calculated VAT on supplied goods and services domestically;
- **PVN 2**: Overview of supplies of goods and services to other European Union Member States (EU sales list).

To automatically generate the report, first create enough sales tax codes to keep a separate VAT accounting for each type of operation that's subject to reporting in the VAT declaration for Latvia. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate available sales tax transaction attributes (sales tax code, tax classifier) with the lookup result of the **Report field lookup** lookup field. 

In the following table, the **Lookup result** column shows the lookup result that's preconfigured for a specific VAT declaration field in the VAT declaration format. 
Use this information to correctly associate tax transaction attributes with the lookup result and then with the field of the VAT declaration.

| Operation description | PVN - Tax Base<br>(sum without VAT) | PVN - VAT amount | Reference to annex of the VAT return | Lookup result<br>(ReportFieldLookup) | Lookup result description label EN | Lookup result description label LV |
|-----------------------|-------------------------------------|------------------|--------------------------------------|--------------------------------------|------------------------------------|---------|
| Supply of goods and provision of services (including credit notes for the same period and advance payments received) subject to the standard VAT rate. | 41 |52 | PVN 1 - III | 41/52 DomesticSalesStandardRate | Supply of goods and provision of services (including credit notes for the same period and advance payments received) subject to the standard VAT rate. | Ar nodokļa standartlikmi apliekamo darījumu (preču piegādes un pakalpojumu sniegšanas) vērtību bez nodokļa. |
| Tax invoice for property that has been sold at an auction organized by a bailiff. | 41 |52 | PVN 1 - III | 41/52 SalesOfPropertyAtAuction | Registered delivery of property of the taxpayer at an auction organized by a sworn bailiff. | Reģistrēta nodokļa maksātāja mantas piegāde zvērināta tiesu izpildītāja rīkotā izsolē |
| Supply of goods and provision of services subject to the standard VAT rate to unregistered tax payer. | 41 |52 | PVN 1 - III | 41/52 SalesNotRegistered | Transactions registered by the tax payer in accordance with the Cabinet of Ministers Regulation of January 15, 2013 no. 40 32.3. subsection. Transactions of 150 euros or more (excluding VAT), if the recipient of the goods or services is an unregistered tax payer or a person who is not a tax payer, or a person who cannot be identified. In this case, indicating the document type code "X". | Darījumus, kuru vērtība bez nodokļa ir 150 euro vai vairāk, ja preču vai pakalpojumu saņēmējs ir nereģistrēts nodokļa maksātājs vai persona, kas nav nodokļa maksātāja, vai persona, kuru nevar identificēt. Tajā norādot dokumenta veida kodu "X". |
| Domestic transactions for which tax is paid by the recipient of goods or services. | 411 | - | PVN 1 - III | 411 DomesticSupplyReverseCharge | Goods and services, for which tax is paid to the state budget by the recipient of goods and services in accordance with Articles 141, 142, 143, 143.1, 143.2, 143.3 and 143.4 of the law. | Piegādāto preču un sniegto pakalpojumu vērtību, par kuriem nodokli valsts budžetā maksā preču un pakalpojumu saņēmējs saskaņā ar likuma 141., 142., 143., 143.1, 143.2, 143.3 un 143.4 pantu. |
| Transactions subject to the reduced rate. | 42 | 53 | PVN 1 - III | 42/53 DomesticSalesReducedRate | Supply of goods and the provision of services are taxable transactions with a reduced tax rate of 12 percent. | Preču piegādes un pakalpojumu sniegšanas ar samazināto nodokļa likmi 12 procentu apmērā apliekamo darījumu. |
| Transactions subject to the second reduced rate. | 421 | 531 | PVN 1 - III | 421/531 DomesticSalesSecondReducedRate | Supply of goods and provision of services with the second reduced tax rate of 5 percent. | Preču piegādes un pakalpojumu sniegšanas ar otrā samazināto nodokļa likmi 5 procentu. |
| Transactions subject to zero rate. | 43 | - | PVN 1 - III | 43 SalesZeroRate | The value of transactions for the supply of goods and services with a tax rate of 0 percent (including a reduced tax rate of 0 percent). | Preču piegādes un pakalpojumu sniegšanas ar nodokļa 0 procentu likmi (tai skaitā ar samazināto nodokļa likmi 0 procentu apmērā). |
| Goods delivered to free ports and special economic zones taxed at 0%. | 44, 43 | - | PVN 1 - III | 44/43 GoodsFreePorts | The value of goods delivered in free ports and special economic zones, which are taxed at a 0 percent tax rate in accordance with the law "On the application of taxes in free ports and special economic zones". | Brīvostās un speciālajās ekonomiskajās zonās piegādāto preču vērtību, kas apliekamas ar nodokļa 0 procentu likmi saskaņā ar likumu “Par nodokļu piemērošanu brīvostās un speciālajās ekonomiskajās zonās“. |
| Supply of goods to another EU Member State after release for free circulation, excluding specific sales. | 45, 43 | - | PVN 2 (EC sales list) | 45/43 EUSales | Supply of goods to another EU Member State that is carried out following their release for free circulation inland, except supplies of fresh fruits, berries and vegetables, including washed, peeled, shelled, cut and packaged, but not thermally or otherwise processed (for example, frozen, salted, dried). | Citu ES dalībvalsti piegādāto preču ES teritorijā vērtību, izņemot likuma 42. panta sešpadsmitajā daļā minētās preces, ja preču saņēmējs ir citas ES dalībvalsts reģistrēts nodokļa maksātājs. |
| Specific supply of goods to another EU Member State. | 451, 43 | - | PVN 2 (EC sales list) | 451/43 SpecificEUSales | Supply of fresh fruits, berries and vegetables, including washed, peeled, shelled, cut and packaged, but not thermally or otherwise processed (for example, frozen, salted, dried) to another EU Member State registered taxpayer. | Likuma 42. panta sešpadsmitajā daļā minēto uz citu ES dalībvalsti piegādāto preču ES teritorijā vērtību, ja preču saņēmējs ir citas ES dalībvalsts reģistrēts nodokļa maksātājs. Šajā rindā norāda arī ES teritorijā piegādāto preču vērtību likuma 31.1 pantā noteiktajā brīdī. |
| The value of goods brought into the EU from third countries or territories, not released for free circulation, stored in customs warehouses and free zones. | 46, 43 | - | - | 46/43 ImportDeliveryInCustoms | The value of the goods brought into the EU territory from third countries or third territories and not released for free circulation in delivery customs warehouses and free zones. | To preču vērtību, kas ievestas ES teritorijā no trešajām valstīm vai trešajām teritorijām un nav izlaistas brīvā apgrozībā piegādes muitas noliktavās un brīvajās zonās. |
| The value of new vehicles delivered to an unregistered or non-taxpayer in another EU member state, with the tax invoice copy attached to the tax declaration. | 47, 43 | - | - | 47/43 NewVehiclesEUSales | The value of new vehicles delivered to another EU member state to an unregistered taxpayer of that member state or to a non-tax payer of another EU member state. A copy of the tax invoice for the delivery of a new vehicle is attached to the tax declaration. | Uz citu ES dalībvalsti šīs dalībvalsts nereģistrētam nodokļa maksātājam vai citas ES dalībvalsts personai, kas nav nodokļa maksātāja, piegādāto jaunu transportlīdzekļu vērtību. Nodokļa deklarācijai pievieno nodokļa rēķina kopiju par jauna transportlīdzekļa piegādi. |
| Services taxed at a 0% rate under Articles 46, 47, 48, and 50 (parts 4-7.1) of the law, effective January 1, 2021. | 48, 43 | - | - | 48/43 ServicesProvidedZeroRate | With the tax rate of 0 percent (including the reduced tax rate of 0 percent) of the value of the services rendered in accordance with Articles 46, 47, 48 and 2.1 of Article 50 of the law (starting from January 1, 2021), fourth, fifth, sixth, seventh and 7.1 parts. | Ar nodokļa 0 procentu likmi (tai skaitā ar samazināto nodokļa likmi 0 procentu apmērā) apliekamo sniegto pakalpojumu vērtību saskaņā ar likuma 46., 47., 48. pantu un 50. panta 2.1 (sākot ar 2021. gada 1. janvāri), ceturto, piekto, sesto, septīto un 7.1 daļu. |
| Exported goods. | 481, 43 | - | - | 481/43 ExportGoods | Exported goods. | Eksportēto preču vērtību. |
| Not domestic transactions. | 482 | - | PVN 1 - III | 482 NonDomesticTransactions | Supply of services to another EU Member State registered taxpayer. | Pakalpojumu sniegšana citā ES dalībvalstī reģistrētam nodokļu maksātājam. |
| Supply of services to another EU Member State. | 482 | - | PVN 2 (EC sales list) | 482 EUTransaction | Supply of services to another EU Member State registered taxpayer. | Pakalpojumu sniegšana citā ES dalībvalstī reģistrētam nodokļu maksātājam. |
| VAT exempt supplies. | 49 | - | - | 49 NonTaxableTransactions | Value of non-taxable transactions in accordance with Article 52 of the Law (including in accordance with Part 3.1 of this Article). In this line, the value of the delivery of tax-exempt investment gold according to Article 139 of the law is also indicated. | Ar nodokli neapliekamo darījumu vērtību saskaņā ar likuma 52. pantu (tai skaitā saskaņā ar šā panta 3.1 daļu). Šajā rindā norāda arī no nodokļa atbrīvotu ieguldījumu zelta piegādes vērtību saskaņā ar likuma 139. pantu. |
| Purchases from EU member state subject to standard VAT rate 21%. | 49 | - | - | 50/55 EUPurchaseStandardRateReverseCharge | Goods and services received from EU including credit notes, subject to standard rate VAT 21%, reverse charge. | Preces un pakalpojumi, kas saņemti no ES, ieskaitot kredītrēķinus, apliekami ar standarta likmi PVN 21%, apgrieztā iekasēšana. |
| Purchases from EU member state subject to standard VAT rate 21%. | 50 | 55 | PVN 1-II | 50/55 EUPurchaseStandardRateReverseCharge | Goods and services received from EU including credit notes, subject to standard rate VAT 21%, reverse charge. | Preces un pakalpojumi, kas saņemti no ES, ieskaitot kredītrēķinus, apliekami ar standarta likmi PVN 21%, apgrieztā iekasēšana. |
| UseTax - Goods received from EU after importation subject to standard VAT rate 21%. | 50 | 55,64 | PVN 1-II | 50/55/64 EUPurchaseStandardRateAfterImportationUseTax | Goods and services received from EU, reported with code "C" - purchase of such goods in the territory of the EU in accordance with the third part of Article 9 of the law, which is carried out after importation from third countries and release into free circulation in another EU member state posted using UseTax, subject to standard VAT rate 21%. | Preces un pakalpojumi, kas saņemti no ES, uzrādīti ar kodu "C", šādu preču iegāde ES teritorijā saskaņā ar likuma 9.panta trešo daļu, kas tiek veikta pēc ievešanas no trešajām valstīm un izlaišanas. laist brīvā apgrozībā citā ES dalībvalstī, publicēts, izmantojot UseTax, tiek piemērota standarta PVN likme 21%. |
| UseTax - Goods received from EU subject to standard VAT rate 21%. | 50 | 55, 64 | PVN 1-II | 50/55/64 EUPurchaseStandardRateGoodsUseTax | Goods received from EU, reported with code "G" – goods received from registered taxpayers of another EU member state (purchase of goods in EU territory), posted using UseTax, subject to standard VAT rate 21%. | Preces, kas saņemtas no citas ES dalībvalsts reģistrētiem nodokļa maksātājiem (preču iegāde ES teritorijā, kods “G”), publicēts, izmantojot UseTax, tiek piemērota standarta PVN likme 21%. |
| UseTax - Services received from EU subject to standard VAT rate 21%. | 50 | 55, 64 | PVN 1-II | 50/55/64 EUPurchaseStandardRateServicesUseTax | Services received from EU, reported with code "P" - services received from a taxpayer registered in another EU member state and the place of provision of which, in accordance with the first part of Article 19 of the law, is domestic, posted using UseTax, subject to standard VAT rate 21%. | Pakalpojumi, kuri saņemti no citas ES dalībvalsts reģistrēta nodokļa maksātāja un kuru sniegšanas vieta saskaņā ar likuma 19. panta pirmo daļu ir iekšzeme (kods “P”), publicēts, izmantojot UseTax, tiek piemērota standarta PVN likme 21%. |
| Purchases from EU member state subject to reduced VAT rate 12%. | 51 | 56 | PVN 1-II | 51/56 EUPurchaseReducedRateReverseCharge | Goods and services received from EU including credit notes, subject to reduced rate VAT 12%, reverse charge. | Preces un pakalpojumi, kas saņemti no ES, ieskaitot kredītrēķinus, apliekami ar samazināts likmi PVN 12%, apgrieztā iekasēšana. |
| UseTax - Goods received from EU after importation subject to reduced VAT rate 12%. | 51 | 56,64 | PVN 1-II | 51/56/64 EUPurchaseReducedRateAfterImportationUseTax | Goods and services received from EU, reported with code "C" - purchase of such goods in the territory of the EU in accordance with the third part of Article 9 of the law, which is carried out after importation from third countries and release into free circulation in another EU member state posted using UseTax, subject to reduced VAT rate 12%. | Preces un pakalpojumi, kas saņemti no ES, uzrādīti ar kodu "C", šādu preču iegāde ES teritorijā saskaņā ar likuma 9.panta trešo daļu, kas tiek veikta pēc ievešanas no trešajām valstīm un izlaišanas. laist brīvā apgrozībā citā ES dalībvalstī, publicēts, izmantojot UseTax, tiek piemērota samazināts PVN likme 12%. |
| UseTax - Goods received from EU subject to reduced VAT rate 12%. | 51 | 56,64 | PVN 1-II | 51/56/64 EUPurchaseReducedRateGoodsUseTax | Goods received from EU, reported with code "G" – goods received from registered taxpayers of another EU member state (purchase of goods in EU territory), posted using UseTax, subject to reduced VAT rate 12%. | Preces, kas saņemtas no citas ES dalībvalsts reģistrētiem nodokļa maksātājiem (preču iegāde ES teritorijā, kods “G”), publicēts, izmantojot UseTax, tiek piemērota samazināts PVN likme 12%. |
| Purchases from EU member state subject to second reduced VAT rate 5%. | 511 | 561 | PVN 1-II | 511/561 EUPurchaseSecondReducedRateReverseCharge | Goods and services received from EU including credit notes, subject to second reduced rate VAT 5%, reverse charge. | Preces un pakalpojumi, kas saņemti no ES, ieskaitot kredītrēķinus, apliekami ar otro samazinātolikmi PVN 5%, apgrieztā iekasēšana. |
| UseTax - Goods received from EU after importation subject to second reduced VAT rate 5%. | 511 | 561, 64 | PVN 1-II |511/561/64 EUPurchaseSecondReducedRateAfterImportationUseTax | Goods and services received from EU, reported with code "C" - purchase of such goods in the territory of the EU in accordance with the third part of Article 9 of the law, which is carried out after importation from third countries and release into free circulation in another EU member state posted using UseTax, subject to second reduced VAT rate 5%. | Preces un pakalpojumi, kas saņemti no ES, uzrādīti ar kodu "C", šādu preču iegāde ES teritorijā saskaņā ar likuma 9.panta trešo daļu, kas tiek veikta pēc ievešanas no trešajām valstīm un izlaišanas. laist brīvā apgrozībā citā ES dalībvalstī, publicēts, izmantojot UseTax, tiek piemērota otro samazinātoPVN likme 5%. |
| UseTax - Goods received from EU subject to second reduced VAT rate 5%. | 511 | 561, 64 | PVN 1-II | 511/561/64 EUPurchaseSecondReducedRateGoodsUseTax | Goods received from EU, reported with code "G" – goods received from registered taxpayers of another EU member state (purchase of goods in EU territory), posted using UseTax, subject to second reduced VAT rate 5%. | Preces, kas saņemtas no citas ES dalībvalsts reģistrētiem nodokļa maksātājiem (preču iegāde ES teritorijā, kods “G”), publicēts, izmantojot UseTax, tiek piemērota otro samazinātoPVN likme 5%. |
| Special regime of tax application in goods import transactions. | - | 52 | PVN 1-I | 52 ImportSpecialRegimeReverseCharge | Importation of goods from countries outside EU if a permit for application of a special VAT regime for imported goods is received from the State Revenue Service. | Preču ievešana no valstīm ārpus ES, ja no Valsts ieņēmumu dienesta saņemta atļauja īpaša PVN režīma piemērošanai ievestajām precēm. |
| Domestic reverse charge purchases. | - | 52 | PVN 1-I | 52 DomesticGoodsServicesReverseCharge | Domestic reverse charge purchases. | Iekšzemes apgrieztās maksāšanas pirkumi. |
| Received services from non-EU registered businesses. | - | 54 | PVN 1-I | 54 NonDomesticReceivedServicesReverseCharge | Received services from non-EU registered traders or businesses (third countries). | Saņemtie pakalpojumi no ārpus ES reģistrētiem tirgotājiem vai uzņēmumiem (trešās valstis). |
| Refunding input tax deductions - credit notes. | - | 57 | PVN 1-I | 57 RefundingInputTaxDeductions | Tax amounts that were deducted as input tax in previous taxation periods and that must be paid to the state budget, credit notes to invoices in previous periods. | Nodokļa summas, kuras iepriekšējos taksācijas periodos tika atskaitītas kā priekšnodoklis un kuras jāiemaksā valsts budžetā, kredītrēķini rēķiniem iepriekšējos periodos. |
| Tax receivable reduction from previous periods - bad debts. | - | 57 | PVN 1-I | 57 TaxReductionPreviousPeriodsReceivableBadDebts | Tax amounts that were deducted as input tax in previous taxation periods and that must be paid to the state budget, bad debts. | Nodokļa summas, kuras iepriekšējos taksācijas periodos tika atskaitītas kā priekšnodoklis un kuras jāiemaksā valsts budžetā, bezcerīgie parādi. |
| Domestically imported goods. | - | 61 | PVN 1-I | 61 Import | Paid tax amounts for imported goods and calculated tax amounts for the import of goods subject to the special regime of tax application in goods import transactions. | Samaksātās nodokļa summas par importētajām precēm un aprēķinātās nodokļa summas par preču importu, kam noteikts īpašais nodokļa piemērošanas režīms preču importa darījumos. |
| Acquisition and importation of new passenger cars. | - | 61 | PVN 1-I | 61 PurchaseAndImportLightVehicles | The amount of tax for the purchase and import of light vehicles (in accordance with the category M1 and N1 vehicles specified in the Cabinet of Ministers' regulations of December 22, 2009 No. 1494 "Rules for assessing the conformity of mopeds, motor vehicles, their trailers and components"). | Nodokļa summas par vieglo transportlīdzekļu (saskaņā ar Ministru kabineta 2009. gada 22. decembra noteikumos Nr. 1494 “Mopēdu, mehānisko transportlīdzekļu, to piekabju un sastāvdaļu atbilstības novērtēšanas noteikumi” noteikto M1 un N1 transportlīdzekļu kategoriju) iegādi un importu. |
| UseTax - Special regime of tax application in goods import transactions. | - | 61, 52 | PVN 1-I | 61/52 ImportSpecialRegimeUseTax | Importation of goods from countries outside EU if a permit for application of a special VAT regime for imported goods is received from the State Revenue Service, posted using UseTax. | Preču ievešana no valstīm ārpus ES, ja no Valsts ieņēmumu dienesta saņemta atļauja īpaša PVN režīma piemērošanai ievestajām precēm, publicēts, izmantojot UseTax. |
| Domestic purchase of goods and services, subject to different VAT rates - 5%, 12%, 21%. | - | 62 | PVN 1-I | 62 DomesticGoodsServices | Domestic purchase of goods and services including credit notes for the same period and advance payments paid, subject to different VAT rates - 5%, 12%, 21%. | Iekšzemes preču un pakalpojumu iegāde, tai skaitā kredītrēķini par to pašu periodu un avansa maksājumi, kuriem piemēro dažādas PVN likmes - 5%, 12%, 21%. |
| Purchase of goods and services from not VAT registered partner. | - | 62 | PVN 1-I | 62 PurchaseGoodsServicesNotRegistered | Purchased goods and received services in transactions with a business partner who does not have a VAT registration number. | Iegādātas preces un saņemti pakalpojumi darījumos ar darījumu partneri, kuram nav PVN reģistrācijas numura. |
| Purchase of property. | - | 62 | PVN 1-I | 62 PurchaseOfProperty | Purchase of property of a registered taxpayer at an auction organized by a sworn bailiff. | Reģistrēta nodokļu maksātāja mantas iegāde zvērināta tiesu izpildītāja organizētā izsolē. |
| Domestic purchase reverse charge - art. 141. | - | 62 | PVN 1-I | 62-141 DomesticGoodsServices | Amount of tax calculated by a registered taxpayer as a recipient of goods and services in accordance with Articles 141 of the law. | Nodokļa summu, kuru reģistrēts nodokļa maksātājs aprēķina kā preču un pakalpojumu saņēmējs saskaņā ar likuma 141 pantu. |
| Domestic purchase reverse charge - art. 142. | - | 62 | PVN 1-I | 62-142 DomesticGoodsServices | Amount of tax calculated by a registered taxpayer as a recipient of goods and services in accordance with Articles 142 of the law. | Nodokļa summu, kuru reģistrēts nodokļa maksātājs aprēķina kā preču un pakalpojumu saņēmējs saskaņā ar likuma 142 pantu. |
| Domestic purchase reverse charge - art. 143. | - | 62 | PVN 1-I | 62-143 DomesticGoodsServices | Amount of tax calculated by a registered taxpayer as a recipient of goods and services in accordance with Articles 143 of the law. | Nodokļa summu, kuru reģistrēts nodokļa maksātājs aprēķina kā preču un pakalpojumu saņēmējs saskaņā ar likuma 143 pantu. |
| Domestic purchase reverse charge - art. 143.1. | - | 62 | PVN 1-I | 62-143.1 DomesticGoodsServices | Amount of tax calculated by a registered taxpayer as a recipient of goods and services in accordance with Articles 143.1 of the law. | Nodokļa summu, kuru reģistrēts nodokļa maksātājs aprēķina kā preču un pakalpojumu saņēmējs saskaņā ar likuma 143.1 pantu. |
| Domestic purchase reverse charge - art. 143.2. | - | 62 | PVN 1-I | 62-143.2 DomesticGoodsServices | Amount of tax calculated by a registered taxpayer as a recipient of goods and services in accordance with Articles 143.2 of the law. | Nodokļa summu, kuru reģistrēts nodokļa maksātājs aprēķina kā preču un pakalpojumu saņēmējs saskaņā ar likuma 143.2 pantu. |
| Domestic purchase reverse charge - art. 143.3. | - | 62 | PVN 1-I | 62-143.3 DomesticGoodsServices | Amount of tax calculated by a registered taxpayer as a recipient of goods and services in accordance with Articles 143.3 of the law. | Nodokļa summu, kuru reģistrēts nodokļa maksātājs aprēķina kā preču un pakalpojumu saņēmējs saskaņā ar likuma 143.3 pantu. |
| Domestic purchase reverse charge - art. 143.4. | - | 62 | PVN 1-I | 62-143.4 DomesticGoodsServices | Amount of tax calculated by a registered taxpayer as a recipient of goods and services in accordance with Articles 143.4 of the law. | Nodokļa summu, kuru reģistrēts nodokļa maksātājs aprēķina kā preču un pakalpojumu saņēmējs saskaņā ar likuma 143.4 pantu. |
| Received services from outside of EU. | - | 63 | PVN 1-I | 63 NonDomesticReceivedServices | Received services from outside of EU. | Saņemti pakalpojumi ārpus ES. |
| UseTax - Received services from outside of EU. | - | 63, 54 | PVN 1-I | 63/54 NonDomesticReceivedServicesUseTax | Received services from outside of EU, posted using UseTax. | Saņemti pakalpojumi ārpus ESpublicēts, izmantojot UseTax. |
| Goods received from EU. | - | 64 | PVN 1-II | 64 EUGoods | Goods received from EU, including credit notes. | Preces, kas saņemtas no ES, ieskaitot kredītzīmes. |
| Goods received from EU after importation. | - | 64 | PVN 1-II | 64 EUGoodsServicesAfterImportation | Goods and services received from EU, reported with code "C" - purchase of such goods in the territory of the EU in accordance with the third part of Article 9 of the law, which is carried out after importation from third countries and release into free circulation in another EU member state. | Preces un pakalpojumi, kas saņemti no ES, uzrādīti ar kodu "C" - šādu preču iegāde ES teritorijā saskaņā ar likuma 9.panta trešo daļu, kas tiek veikta pēc ievešanas no trešajām valstīm un izlaišanas bezmaksas. aprite citā ES dalībvalstī. |
| Services received from EU. | - | 64 | PVN 1-II | 64 EUServices | Services received from EU, reported with code "P" - services received from a taxpayer registered in another EU member state and the place of provision of which, in accordance with the first part of Article 19 of the law, is domestic. | Pakalpojumi, kas saņemti no ES, uzrādīti ar kodu "P" - pakalpojumi, kas saņemti no citā ES dalībvalstī reģistrēta nodokļu maksātāja un kuru sniegšanas vieta saskaņā ar likuma 19.panta pirmo daļu ir iekšzemes. |
| 65 CompensationToFarmers. | - | 65 | - | 65 CompensationToFarmers |Tax compensation paid to farmers by processors of agricultural products in accordance with Article 135 of the law in the amount of 14 percent of the value of the received production. | Lauksaimniecības produkcijas pārstrādātāju saskaņā ar likuma 135. pantu lauksaimniekiem izmaksāto nodokļa kompensāciju 14 procentu apmērā no saņemtās produkcijas vērtības. |
| Non-deductible tax. | - | 66 | - | 66 NotDeductibleTax | The amount of tax not deducted from the amount of tax payable in the state budget for the purchased goods and received services, which are used to perform non-taxable transactions, to ensure the functions of the executive power of the state or municipalities, or to ensure transactions that are outside the scope of the law; as well as amounts of tax paid or payable by the trader on works of art, collectors' items or antiques which the trader has himself released into free circulation, and amounts of tax paid or payable by the trader on works of art which he has been delivered by the author of the work of art or the assignee of the copyright, in cases where a tax is imposed on the delivery of goods in accordance with the special regime of tax application in transactions with second-hand goods, works of art, collectibles and antiques. | No valsts budžetā maksājamās nodokļa summas neatskaitāmo nodokļa summu par iegādātajām precēm un saņemtajiem pakalpojumiem, kas tiek izmantoti ar nodokli neapliekamo darījumu veikšanai, valsts vai pašvaldību izpildvaras funkciju nodrošināšanai vai tādu darījumu nodrošināšanai, kas ir ārpus likuma darbības jomas; kā arī nodokļa summas, kuras tirgotājs ir samaksājis vai kuras tam ir jāsamaksā par mākslas darbiem, kolekciju priekšmetiem vai senlietām, ko tirgotājs pats ir izlaidis brīvā apgrozībā, un nodokļa summas, kuras tirgotājs ir samaksājis vai kuras tam ir jāsamaksā par mākslas darbiem, ko tam ir piegādājis mākslas darbu autors vai autortiesību pārņēmējs, gadījumos, kad preču piegādei nosaka nodokli saskaņā ar īpašo nodokļa piemērošanas režīmu darījumos ar lietotām mantām, mākslas darbiem, kolekciju priekšmetiem un senlietām. |
| Tax reduction previous periods - credit notes. | - | 67 | PVN 1-I | 67 TaxReductionPreviousPeriods | A reduction of the amount of tax calculated in the state budget for payment in previous taxation periods, credit notes related to original invoices in previous periods. | Iepriekšējos taksācijas periodos samaksai valsts budžetā aprēķinātās nodokļa summas samazinājumu, kredītzīmes, kas saistītas ar iepriekšējo periodu rēķinu oriģināliem. |
| Tax reduction previous periods - bad debts. | - | 67 | PVN 1-I | 67 TaxReductionPreviousPeriodsPayableBadDebts | The tax amount for lost debt for registered taxpayers (goods suppliers or service providers) who have the right to reduce the amount of tax paid to the state budget by the tax amount of lost debt. | Nodokļa summu par zaudēto parādu reģistrētiem nodokļa maksātājiem (preču piegādātājiem vai pakalpojumu sniedzējiem), kuriem ir tiesības valsts budžetā iemaksāto nodokļa summu samazināt par zaudētā parāda nodokļu summu. |
| Other tax transactions not reported in VAT declaration. | - | - | - | Other | Set Not blank or specify tax codes that must be excluded from VAT declaration. | Iestatiet Nav tukšu vai norādiet nodokļu kodus, kas ir jāizslēdz no PVN deklarācijas. |

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up) section later in this article.

## Set up the VAT declaration for Latvia

These tasks will prepare your Dynamics 365 Finance environment to generate the electronic file for the VAT declaration for Latvia and preview the VAT amounts in Excel format.

- [Import ER configurations](#import-er).
- [Set up application-specific parameters for VAT declaration fields](#set-up).
- [Set up the VAT reporting format to preview amounts in Excel](#setup-preview).
- [Set up electronic messages](#setup-em).
- [Set up the VAT registration number of the company that's reporting VAT](#vat-id).

### <a name="import-er"></a>Import ER configurations

Open the **Electronic reporting** workspace, and import the latest versions of these ER formats under **Tax declaration model**:

- VAT Declaration XML (LV)
- VAT Declaration Excel (LV)

Import **Tax declaration model mapping** under **Tax declaration model**, and mark it **Default for model mapping**.

For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="set-up"></a>Set up application-specific parameters for VAT declaration fields

To automatically generate the VAT declaration, associate available sales tax transaction attributes (sales tax code, tax classifier) in Finance and lookup results in the ER configuration.

> [!NOTE]
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for an earlier version of an ER format automatically become applicable for a later version of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

Follow these steps to define which of the available sales tax transaction attributes (sales tax code, tax classifier) in Finance generates which field of the VAT declaration for Latvia.

1. Go to **Workspaces** \> **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration XML (LV)** configuration, and then, on the Action Pane, select **Configurations** \> **Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.

    | Field | Description |
    |---|---|
    | Lookup result | Select the value of the report field. For more information about the values and their assignment to VAT declaration rows, see the [VAT declaration overview](#vat-declaration-overview) section earlier in this article. |
    | Tax code | Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
    | Transaction classifier | <p>If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, you can set up a transaction classifier. The following transaction classifiers are available:</p><ul><li>**Purchase**</li><li>**PurchaseExempt** (tax-exempt purchase)</li><li>**PurchaseReverseCharge** (tax receivable from a purchase reverse charge)</li><li>**Sales**</li><li>**SalesExempt** (tax-exempt sale)</li><li>**SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)</li><li>**Use tax**</li></ul><p>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).</p><p>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for credit note value.</p> |
    | Item sales tax group | Use the **Item sales tax group** column to supplement your setup that's specified with **Tax code** and **Transaction classifier** columns when necessary. |
    | Sales tax group | Use the **Sales tax group** column to supplement your setup that's specified with **Tax code** and **Transaction classifier** columns when necessary. |

    > [!NOTE]
    > Associate all sales tax codes (or combinations of a sales tax code and a tax classifier) with lookup results. If any combination should not generate values on the VAT declaration, associate it with the **Other** lookup result.

5. In the **State** field, change the value to **Completed**.
6. On the Action Pane, select **Export** to export the settings of the application-specific parameters.
7. Select the **VAT declaration Excel (LV)** configuration, and then, on the Action Pane, select **Import** to import the parameters that you configured for **VAT declaration XML (LV)**.
8. In the **State** field, select **Completed**.

### <a name="setup-preview"></a>Set up the VAT reporting format to preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
2. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax authorities**, and select the tax authority.
3. In the **Report layout** field, select **Default**.
4. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
5. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (LV)** ER format. This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

If you're configuring the VAT declaration for Latvia in a legal entity that has [multiple VAT registrations](../global/emea-reporting-for-multiple-vat-registrations.md), follow these steps.

1. Go to **General ledger** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **LVA**, select the **VAT Declaration Excel (LV)** ER format.

### <a name="setup-em"></a>Set up electronic messages

Electronic messaging (EM) functionality is provided to maintain the different processes that are used in electronic reporting for different document types. For more information about electronic messages, see [Electronic messaging](../../general-ledger/electronic-messaging.md).

#### <a name="import-em"></a>Download and import the data package that has example settings for electronic messages

The process of setting up the **Electronic messages** functionality to generate the VAT declaration for Latvia in XML format and preview it in Excel has many steps. Because the data of some entities is used in the ER configurations, use a set of predefined values that are delivered in a package of data entities for the related tables. You can extend these settings or create your own.

> [!NOTE]
> Some records in the data entities in the package include a link to ER configurations. Before you start to import the data entities package, [import ER configurations into Finance](#import-er).

1. In [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **LV VAT declaration - PVN - EM setup v.\#**. The downloaded file is named **LV VAT declaration - PVN - EM setup v.\#.zip**. Always download the latest version of the package that's available in Lifecycle Services.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**, and validate the electronic message processing that you imported (**LV VAT declaration**).

For more information about how you can use the data management framework, see [Data management](../../../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md).

#### Configure electronic messages

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
2. Select the line for **LV Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

You can specify default values for **Deduction percent** and **Main economic activity** parameters of your VAT declaration in additional fields of electronic messages.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and select the **LV VAT declaration** processing.
2. On the **Message additional fields** FastTab, in the **DeductionPercent** (Kalendorinių metų proporcinis PVM atskaitos procentas) field, define the deduction percent that will be used further in reporting as default value.
3. On the **Message additional fields** FastTab, in the **MainEconomicActivity** (Pagrindinė vykdomos veiklos rūšis) field, define the main economic activity code that will be used further in reporting as default value.
4. Save your changes.

### <a id="vat-id"></a>Set up the registration numbers of the company that's reporting PVN

Follow these steps to configure the registration numbers of your organization.

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Latvia, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that's dedicated to Latvia and that uses the **VAT ID** registration category.
5. In the **Registration number** field, enter the tax number. This value is reported in the VAT declaration.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](../europe/emea-registration-ids.md).

Follow these steps to define the VAT registration number that EM uses during generation of the VAT declaration for Latvia.

1. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Electronic messages processing**, and select the **LV VAT declaration** processing.
2. On the **Message additional fields** FastTab, in the **Tax registration number** field, define the VAT registration number that should be used in the VAT declaration for Latvia.
3. Save your changes.

If the VAT registration number isn't specified in the **Tax registration number** additional field of the **LV VAT declaration** processing, the system retrieves it from the registration ID that's defined in the properties of the legal entity that's associated with the **VAT ID** registration category.

## Preview the VAT declaration in Excel

### <a name="report-sales-tax-for-settlement-period"></a>Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1. Go to **Tax** \> **Periodic tasks** \> **Declarations** \> **Sales tax** \> **Report sales tax for settlement period**.
2. Set the following fields.

    | Field | Description |
    |---|---|
    | From date | Select the start date of the reporting period. |
    | Settlement period | Select the settlement period. |
    | Sales tax payment version | <p>Select one of the following values:</p><ul><li>**Original** – Generate a report for the sales tax transactions of the original sales tax payment or before the sales tax payment is generated.</li><li>**Corrections** – Generate a report for the sales tax transactions of all the subsequent sales tax payments for the period.</li><li>**Total list** – Generate a report for all the sales tax transactions for the period, including the original and all corrections.</li></ul> |

3. Select **OK**, and then, in the next dialog box, set the following fields.

    | Field | Description |
    |---|---|
    | Report date | Specify the date when report is prepared. |
    | Declaration period type | Select **Initial** to prepare a file for initial submission in the reporting period. Select **Corrected** to prepare a file to submit a corrected VAT declaration. |
    | Contact person | Select a contact person in the lookup list. This parameter is available in XML format only. |
    | Main economic activity code | Specify the main economic activity code for your company. |
    | Deduction percent | Specify the deduction percent for the reporting period. |

4. On the **Run in the background** FastTab, specify parameters of the batch processing, and select the **Batch processing** checkbox to run the report in batch mode.
5. Select **OK**, and review the Excel report. When the report is run in batch mode, you can find the generated file as an attachment of the batch job on the **Electronic reporting jobs** page (**Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**).

### Preview the VAT declaration in Excel from a sales tax payment

Sales tax payment transactions are produced by the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job procedure that settles sales tax balances in the sales tax accounts and offsets them to the sales tax settlement account for a given period. After the **Settle and post sales tax** job procedure is completed for an interval of the sales tax settlement period, you can generate the VAT declaration in Excel from the **Sales tax payments** page.

1. Go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**, specify report parameters as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section earlier in this article, and then select **OK**.
3. Review the Excel file that's generated for the selected sales tax payment line.

    > [!NOTE]
    > The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the [Report sales tax for settlement period](#report-sales-tax-for-settlement-period) periodic task.

## Generate the electronic file for the VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run the VAT declaration for multiple legal entities](#run-the-vat-declaration-for-multiple-legal-entities) section later in this article.

The following procedure applies to the electronic message processing example that you [imported earlier from the Lifecycle Services Shared asset library](#import-em).

1. Go to **Tax** \> **Inquiries and reports** \> **Electronic messages** \> **Electronic messages**.
2. In the left pane, select **LV VAT declaration**.
3. On the **Messages** FastTab, select **New**.
4. In the **Run processing** dialog box, the **LV VAT Create message** action is predefined. Select **OK**.
5. Select the message line that's created, enter a description, and then specify the start and end dates for the declaration.
6. On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier because of the [Settle and post sales tax](../../general-ledger/tasks/create-sales-tax-payment.md) job procedure are added to the message.
7. On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
8. Optional: Select **Original document** to review the sales tax payments, or select **Delete** to exclude sales tax payments from processing.
9. On the **Messages** FastTab, select **Update status**.
10. In the **Update status** dialog box, select **LV VAT Ready to generate**, and then select **OK**.
11. Verify that the message status is changed to **LV VAT Ready to generate VAT return**.
12. Select **Generate report**.
13. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **LV VAT Preview report**, and then select **OK**.
14. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section earlier in this article, and then select **OK**.
15. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file.
16. Review the amounts in the Excel document, and then select **Generate report**.
17. To generate the VAT declaration in XML format, in the **Run processing** dialog box, select **LV VAT Generate report**, and then select **OK**.
18. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#report-sales-tax-for-settlement-period) section, and then select **OK**.
19. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, download the file, and use it for your submission to the tax authority.

## Run the VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** \> **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records actions**.
4. On the **Populate records action** page, select the line for **LV Populate VAT return records**.

    In the **Datasources setup** grid, a new **Company** field is available. For existing records, this field shows the identifier of the current legal entity.

5. In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. For each new line, set the following fields.

    | Field | Description |
    |---|---|
    | Name | Enter a value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
    | Message item type | Select **VAT return**. This value is the only value that's available for all the records. |
    | Account type | Select **All**. |
    | Master table name | Specify **TaxReportVoucher** for all the records. |
    | Document number field | Specify **Voucher** for all the records. |
    | Document date field | Specify **TransDate** for all the records. |
    | Document account field | Specify **TaxPeriod** for all the records. |
    | Company | Select the ID of the legal entity. |
    | User query | This checkbox is automatically selected when you define criteria by selecting **Edit query**. |

6. For each new line, select **Edit query**, and specify a related settlement period for the legal entity that's specified in the **Company** field on the line.

    When the setup is completed, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all legal entities that you defined.
