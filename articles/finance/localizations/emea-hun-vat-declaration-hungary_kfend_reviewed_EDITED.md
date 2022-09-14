

# VAT declaration (Hungary)

This article describes how to set up the value-added tax (VAT) declaration 65A with Summary report 65M for Hungary in XML format, and how to preview the VAT declaration 65A in Microsoft Excel.

To automatically generate the reports, first create enough sales tax codes to keep a separate VAT accounting for each box on the VAT declaration. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result of the lookups for the boxes on the VAT declaration.

For Hungary, you must configure the following elements:

* Report field lookup

* Details lookup

* Annex I lookup

* Assets lookup

* In-kind operations lookup

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#_Set_up_application-specific_1) section later in this topic.

In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration row in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the row of the VAT declaration.

## VAT declaration overview

The VAT declaration 65A in Hungary contains the following sections:

* 65A-01-01

* 65A-01-02

* 65A-01-03

* 65A-01-05

### Section 65A-01-01

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

VAT payable

| Description| Line| Lookup| Lookup result |
| - |
| Supply of goods outside the territory of the Community, supply of services covered by it and supply of goods and services in connection with international transport| 01| Report field lookup| 01-Export |
| Intra-Community tax-free supplies of goods with the right to deduct (excluding sales of new means of transport)| 02| Report field lookup| 02-EUSales |
| Amount of intra-community sales of a new means of transport| 03| Report field lookup| 03-EUSalesNewMeansOfTransport |
| Supply of goods, the provision of services pursuant to § 142 and tax-free domestic sales| 04| Report field lookup| 04-TaxFreeDomesticSales |
| Sales at a rate of 5% - reduced rate| 05| Report field lookup| 05-DomesticSalesLowerReducedRate |
| Sales at a rate of 18% - reduced rate| 06| Report field lookup| 06-DomesticSalesHigherReducedRate |
| Sales at a rate of 27% - standard rate| 07| Report field lookup| 07-DomesticSalesStandardRate |
| Tax-free sales due to their public interest or other special nature| 08| Report field lookup| 08-TaxFreeSpecialSales |
| Tax established by a special procedure| 09| Report field lookup| 09-TaxSpecialProcedure |
| Tax on investment within one's own business| 10| Report field lookup| 10-InvestmentOwnBusinessTaxPayable |
| Tax-free Intra - Community acquisitions of goods| 11| Report field lookup| 11-EUPurchasesTaxFree |


 

| Description| Line| Lookup| Lookup result |
| - |
| Intra - Community acquisitions of products subject to a 5% rate| 12| Report field lookup| 12-EUPurchasesLowerReducedRateTaxPayable

1269-EUPurchasesLowerReducedRateUseTax |
| Intra - Community acquisitions of products subject to a 18% rate| 13| Report field lookup| 13-EUPurchasesHigherReducedRateTaxPayable

1369-EUPurchasesHigherReducedRateUseTax |
| Intra - Community acquisitions of products subject to a 27% rate| 14| Report field lookup| 14-EUPurchasesStandardRateTaxPayable

1469-EUPurchasesStandardRateUseTax |
| Acquisition of a new means of transport within the Community (27% tax rate)| 15| Report field lookup| 15-EUPurchasesNewMeansOfTransportTaxPayable

1569-EUPurchasesNewMeansOfTransportUseTax |
| Intra - Community acquisitions of excise goods (27% tax rate)| 16| Report field lookup| 16-EUPurchasesExciseGoodsTaxPayable

1669-EUPurchasesExciseGoodsUseTax |
| Use of a tax-free service (from a Community taxable person and a third country taxable person)| 17| Report field lookup| 17-PurchaseServicesTaxFree |
| The obligation to pay tax on a service used from a Community taxable person is subject to VAT Act. Pursuant to Section 37 (1) (tax rate of 27%)| 18| Report field lookup| 18-EUPurchaseServicesTaxPayable

1867-EUPurchaseServicesUseTax |
| Other tax liability on services received from a Community taxable person| 19| Report field lookup| 19-EUPurchaseServicesOtherTaxPayable

1967-EUPurchaseServicesOtherUseTax |
| 5% tax payable by the purchaser on the supply of goods in the case of a transaction within the community under VAT Act. Section 91 (2)| 20| Report field lookup| 20-EUPurchasesTriangularLowerReducedRateTaxPayable

2069-EUPurchasesTriangularLowerReducedRateUseTax |
| 18% tax payable by the purchaser on the supply of goods in the case of a transaction within the community under VAT Act. Section 91 (2)| 21| Report field lookup| 21-EUPurchasesTriangularHigherReducedRateTaxPayable

2169-EUPurchasesTriangularHigherReducedRateUseTax |
| 27% tax payable by the purchaser on the supply of goods in the case of a transaction within the community under VAT Act. Section 91 (2)| 22| Report field lookup| 22-EUPurchasesTriangularStandardRateTaxPayable

2269-EUPurchasesTriangularStandardRateUseTax |


 

| Description| Line| Lookup| Lookup result |
| - |
| Tax - free import of goods| 23| Report field lookup| 23-ImportGoodsTaxFree |
| Import of goods taxed at 5%| 24| Report field lookup| 24-ImportGoodsLowerReducedRateTaxPayable

2471-ImportGoodsLowerReducedRateUseTax |
| Import of goods taxed at 18%| 25| Report field lookup| 25-ImportGoodsHigherReducedRateTaxPayable

2571-ImportGoodsHigherReducedRateUseTax |
| Import of goods taxed at 27%| 26| Report field lookup| 26-ImportGoodsStandardRateTaxPayable

2671-ImportGoodsStandardRateUseTax |
| Obligation to pay tax on a service provided by a taxable person in a non - Community country| 27| Report field lookup| 27-PurchasesServiceThirdCountryTaxPayable

2767-PurchasesServiceThirdCountryUseTax |
| Purchase of goods pursuant to VAT Act § 32, § 34 (27% tax rate)| 28| Report field lookup| 28-DomesticAssemblyElectricityTaxPayable

2867-DomesticAssemblyElectricityUseTax |
| Tax payable under the rules of reverse charge pursuant to VAT Act § 142| 29| Report field lookup| 29-PurchaseReverseChargeTaxPayable

2966-PurchaseReverseChargeUseTax |
| Item reducing the tax payable pursuant to VAT Act Section 99 (9)| 30| Report field lookup| 30-TaxReimbursedForeignPassenger |
| Total tax increase item pursuant to VAT Act 153 / C. §| 31| Report field lookup| 31-TaxIncrease |
| Other| 35| Report field lookup| 35-OtherTaxPayable |
| Total (lines 01 - 35)| 36| Not applicable| Total of lines 01 through 35 |


### Section 65A-01-02

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

Details of VAT payable

| Description| Line| Lookup| Lookup result |
| - |
| The value of the export of goods from line 01 according to VAT Act § 98| 37| Details| 37-Export98 |
| The value of goods placed in a tax warehouse and resold there or unloaded there| 38| Details| 38-TaxWarehouseTaxableSales |
| Value of goods from tax-free Community acquisitions placed in a tax warehouse from the amount of line 11| 39| Details| 39-TaxWarehouseTaxFreeSales |
| The amount of supplies of goods which are the subject of domestic assembly or assembly on the basis of a Community mandate from rows 05-07| 40| Details| 40-SalesDomesticAssembly |
| The amount of distance selling from rows 05-07| 41| Details| 41-DistanceSelling |
| Amount of purchases of goods to be assembled or assembled domestically on the basis of a Community mandate from line 28| 42| Details| 42-PurchasesDomesticAssembly |
| Sales of property, plant and equipment from line 36 (excluding in-kind sales)| 43| Assets| 43-SalesPropertyPlantEquipment |
| In-kind sales from line 36| 44| InKind| 44-InKindSales |
| The amount received as an advance payment from the sum of the rows 05-07| 45| Details| 45-AdvancesDomesticTaxableSales |
| Amount received as an advance from the sum of lines 01 and 04| 46| Details| 46-AdvancesTaxFreeSalesExport |
| Intra-Community sales of new means of transport to non-taxable persons from line 03| 47| Details| 47-EUSalesNewMeansOfTransportNonTaxablePerson |
| Excise tax content in the tax base of lines 11, 16| 48| Details| 48-EUPurchasesExcise |
| Tax payable on the provision of travel services from line 09| 49| Details| 49-SpecialProcedureTravelServices |
| Tax from the amount of line 09 under VAT Act Chapter XVI| 50| Details| 50-SpecialProcedureXVI |
| The tax payable on the property under the rules of reverse charge in the amount of line 29| 51| Details| 51-ReverseChargePropertyTaxPayable |
| The tax payable on waste under the rules of reverse in the amount of line 29| 52| Details| 52-ReverseChargeWasteTaxPayable |
| The tax payable in case of transfer of a property right entitling to emit a greenhouse gas under the rules of reverse charge taxation from the amount of line 29| 53| Details| 53-ReverseChargeGreenhouseGasTaxPayable |
| The tax payable in case of using the service according to the rules of reverse charge taxation specified in § 142 of VAT Act from the amount of line 29| 54| Details| 54-ReverseChargeService142TaxPayable |
| The tax payable in case of using the service according to the rules of reverse charge taxation specified in § 142 of VAT Act from the amount of line 29| 55| Details| 55-TaxGuaranteeTaxWarehousing |
| Sales subject to tax guarantees on intra-Community sales made by the importer in connection with tax-free imports of products from line 02| 56| Details| 56-EUSalesTaxGuarantees |
| Amount of tax-free intra-Community sales made by the importer / taxable person but declared by the indirect customs representative / tax warehouse operator from line 02| 57| Details| 57-EUSalesDeclaredByRepresentative |
| Amount of tax-free sales of a new means of transport within the Community made by the importer / taxable person but declared by the indirect customs representative / tax warehouse operator from line 03| 58| Details| 58-EUSalesNewMeansOfTransportDeclaredByRepresentative |
| Amount of tax-free imports from line 23 made by the importer but declared by the indirect customs representative in the framework of self-taxation| 59| Details| 59-ImportGoodsTaxFreeDeclaredByRepresentative |
| Amount of imports of the goods taxed at 5% made by the importer but declared by the indirect customs representative in the framework of self-taxation from line 24| 60| Details| 60-ImportGoodsLowerReducedRateDeclaredByRepresentative |
| Amount of imports of the goods taxed at 18% made by the importer but declared by the indirect customs representative in the framework of self-taxation from line 25| 61| Details| 61-ImportGoodsHigherReducedRateDeclaredByRepresentative |
| Amount of imports of the goods taxed at 27% made by the importer but declared by the indirect customs representative in the framework of self-taxation from line 26| 62| Details| 62-ImportGoodsStandardRateDeclaredByRepresentative |


Deductible input tax on purchases

| Description| Line| Lookup| Lookup result |
| - |
| Domestic purchase of tax - free goods| 63| Report field lookup| 63-TaxFreeDomesticPurchases |
| Purchase of goods and services under the 5% rate| 64| Report field lookup| 64-PurchasesLowerReducedRate |
| Purchase of goods and services under the 18% rate| 65| Report field lookup| 65-PurchasesHigherReducedRate |
| Purchase of goods and services under the 27% rate| 66| Report field lookup| 66-PurchasesStandardRate

2966-PurchaseReverseChargeUseTax |
| Amount tax deductible from tax paid on a service provided by a taxable person in a non-member country or in the Community or as a purchaser of a product in their own name| 67| Report field lookup| 67-PurchasesServicesTaxDeductible

1867-EUPurchaseServicesUseTax

1967-EUPurchaseServicesOtherUseTax

2767-PurchasesServiceThirdCountryUseTax

2867-DomesticAssemblyElectricityUseTax |
| Taxable amount deductible (Original tax base, proportional tax)| 68| Report field lookup| 68-PurchasesProrataTaxDeductible |
| Amount of tax deductible on intra - Community acquisitions of goods| 69| Report field lookup| 69-EUPurchasesTaxDeductible

1269-EUPurchasesLowerReducedRateUseTax

1369-EUPurchasesHigherReducedRateUseTax

1469-EUPurchasesStandardRateUseTax

1569-EUPurchasesNewMeansOfTransportUseTax

1669-EUPurchasesExciseGoodsUseTax

2069-EUPurchasesTriangularLowerReducedRateUseTax

2169-EUPurchasesTriangularHigherReducedRateUseTax

2269-EUPurchasesTriangularStandardRateUseTax |
| Deductible part of the tax paid on an imported product (by imposition)| 70| Report field lookup| 70-ImportGoodsTaxDeductible

70-ImportGoodsProRataTaxDeductible |
| Deductible part of tax paid on imported product (with self - taxation)| 71| Report field lookup| 71-ImportGoodsSelfTaxationTaxDeductible

71-ImportGoodsProRataSelfTaxationTaxDeductible

2471-ImportGoodsLowerReducedRateUseTax

2571-ImportGoodsHigherReducedRateUseTax

2671-ImportGoodsStandardRateUseTax |


### Section 65A-01-03

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

Deductible input tax on purchases

| Description| Line| Lookup| Lookup result |
| - |
| 7% agricultural compensation surcharge| 72| Report field lookup| 72-AgriculturalCompensationSurchargeLowerRate |
| 12% agricultural compensation surcharge| 73| Report field lookup| 73-AgriculturalCompensationSurchargeHigherRate |
| After investing within your own business| 74| Report field lookup| 74-InvestmentsOwnBusiness |
| Other| 75| Report field lookup| 75-OtherTaxDeductible |
| Total (sum of lines 63-75)| 76| Not applicable| Total of lines 63 through 75 |
| Amount of tax deductible on the acquisition of a tangible asset from the amount of line 76 (excluding in-kind purchases)| 77| Assets| 77-PurchasesTangibleAssets |
| The amount of tax deductible on in-kind purchases from line 76| 78| In-Kind| 78-InKindPurchases |
| The amount of the unrealized investment in one's own enterprise from the amount of line 76| 79| Details| 79-UnrelizedInvestmentsOwnBusiness |


Value added tax accounting

| Description| Line| Data source type| Data source |
| - |
| Amount of deductible item moved from previous period (from the line "Amount of receivable carried forward" of the previous period's declaration)| 82| User input parameter| Tax base - Deductible amount moved from previous period

Tax amount - Deductible amount moved from previous period |
| The difference between the total amount of tax payable during the reference period and the deductible input tax (line 36 - line 76 - line 82)| 83| Not applicable| The result of the following formula:

Line 36 – line 76 – line 82 |
| Amount of tax to be paid (if amount in line 83 is positive)| 84| Not applicable| The result of the following formula:

Line 83, if line 83 > 0; otherwise, 0 |
| Amount of recoverable tax (if amount in line 83 is negative and you are entitled to a refund)| 85| Not applicable| The result of the following formula:

0 – line 83, if 83 < 0; otherwise, 0 |
| Amount of receivable carried forward| 86| User input parameter| Tax base – Receivable amount carried forward

Tax amount – Receivable amount carried forward |


Details of the return

| Description| Line| Lookup| Lookup result |
| - |
| The value, exclusive of tax, of goods acquired for resale in the form of an intermediate customer in a "triangular transaction" (Intra-Community )| 88| Details| 88-PurchasesGoodsTriangularB |
| The value, exclusive tax, of goods resold as an intermediate customer in a "triangular transaction" (Intra-Community)| 89| Details| 89-SalesGoodsTriangularB |
| Tax-free value of supplies of goods effected outside its territorial scope| 90| Details| 90-TaxFreeSalesGoodsOutsideTerritorialScope

9094-TaxFreeSalesGoodsAssembledOutsideTerritorialScope

9095-EUDistanceSales |
| Tax-free value of the supply of services outside its territorial scope| 91| Details| 91-TaxFreeSalesServicesOutsideTerritorialScope

9192-TaxFreeSalesServicesOutsideTerritorialScope

9193-TaxFreeSalesServicesOutsideTerritorialScope |
| Tax-free value for the supply of services falling under Section 37 (1) from the amount of line 91| 92| Details| 9192-TaxFreeSalesServicesOutsideTerritorialScope |
| Tax-free value for the supply of services other than Section 37 (1) from the amount of line 91| 93| Details| 9193-TaxFreeSalesServicesOutsideTerritorialScope |
| The tax-free value of goods which are considered to have been assembled or assembled in another Member State of the Community from line 90| 94| Details| 9094-TaxFreeSalesGoodsAssembledOutsideTerritorialScope |
| Remuneration, net of tax, of distance sales effected in another Member State of the Community from line 90| 95| Details| 9095-EUDistanceSales |


### Section 65A-01-05

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

Sale / purchase of products listed in Annex I to Regulation (EC)

| Description| Line| Lookup| Lookup result |
| - |
| Agricultural products - The tax base of products sold under reverse charge from the amount of line 04| 100B| AnnexI| 100B-DomesticSalesRCAgriculturalProducts |
| Agricultural products - Tax base and tax for goods acquired under reverse charge from the amount of line 29| 100D| AnnexI| 101B-PurchaseReverseChargeAgriculturalProductsTaxDue |
| Iron and steel products - The tax base of products sold under reverse charge from the amount of line 04| 101B| AnnexI| 100D-DomesticSalesRCIronSteel |
| Iron and steel products - Tax base and tax for goods acquired under reverse charge from the amount of line 29| 101D| AnnexI| 101D-PurchaseReverseChargeIronSteelTaxDue |


### Purchase reverse charge VAT

If you configure sales tax codes to post incoming reverse charge VAT by using use tax, associate your sales tax codes with the lookup result of Report field lookup that contains "UseTax" in the name.

Alternatively, you can configure two separate sales tax codes: one for VAT due and one for VAT deduction. Then associate each code with the corresponding lookup results of Report field lookup.

For example, for taxable intra-community acquisitions, you configure sales tax code UT_S_EU with use tax and associate it with the 1469-EUPurchasesStandardRateUseTax lookup result of Report field lookup. In this case, transactions that use the UT_S_EU sales tax code are reflected on lines 14 ("Intra - Community acquisitions of products subject to a 27% rate") and 69 ("Amount of tax deductible on intra - Community acquisitions of goods").

Alternatively, you configure two sales tax codes:

* VAT_S_EU, which has a tax rate value of -27 percent

* InVAT_S_EU, which has a tax rate value of 27 percent

You then associate the codes with lookup results of Report field lookup in the following way:

* Associate VAT_S_EU with the 14-EUPurchasesStandardRateTaxPayable lookup result.

* Associate InVAT_S_EU with the 69-EUPurchasesTaxDeductible lookup result.

In this case, amounts that use the VAT_S_EU sales tax code are reflected on line 14 ("Intra - Community acquisitions of products subject to a 27% rate"). Amounts that use the InVAT_S_EU sales tax code are reflected on line 69 ("Amount of tax deductible on intra - Community acquisitions of goods").

For more information about how to configure reverse charge VAT, see [Reverse charges](https://docs.microsoft.com/dynamics365/finance/localizations/emea-reverse-charge).

## Summary report overview

In Hungary, you can generate a report 65M that contains the following information for each vendor:

-The number of purchase invoices, and their total tax base and tax amount

-The number of corrective invoices, and their total tax base and tax amount

-The list of all purchase invoices in section 65M-02, regardless of the threshold

-The list of corrective invoices in section 65M-02-K, regardless of the threshold

A list of purchase invoices 65M-02 lists all the purchase invoices for the period. For each invoice, it contains the following information:

-The invoice number.

-The fulfillment date. The fulfillment date is the date when the goods are sold or the services are performed. If an invoice doesn't have a fulfillment date, the invoice date is used.

-The tax base in 1,000 Hungarian forints (HUF).

-The tax amount in 1,000 HUF.

-The marking of the final invoice that is received after receipt of the advance invoice.

A list of corrective invoices 65M-02-K lists all the corrective invoices. For each corrective invoice and its original invoice, it contains the following information:

-The invoice or corrective invoice number

-The line type "E" for original invoice or "KT" for corrective invoice

-The original invoice number for the line for a corrective invoice

-The original invoice fulfillment date for the line for a corrective invoice

-The invoice or corrective invoice fulfillment date

-The tax base in 1,000 HUF

-The tax amount in 1,000 HUF

The following are examples show how report 65M is filled in.

### Example 1: Corrective invoice

* August 1, 2022 (01.08.2022): Purchase invoice Inv1 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.

* August 20, 2022 (20.08.2022): Corrective invoice CN1 for a -100,000 HUF tax base and a -27,000 HUF tax amount.

Report for August 2022

65M-02

| Invoice number (a)| Fulfillment date (b)| Tax base (c)| Tax amount (d)| Difference due to advance invoice marking (e) |
| - |
| Inv1| 01.08.2022| 1000| 270|  |


65M-02-K

| Invoice number (a)| Type (b)| Original invoice number (c)| Original fulfillment date (d)| Fulfillment date (e)| Tax base (f)| Tax amount (g) |
| - |
| Inv1| E| | | 01.08.2022| 1000| 270 |
| CN1| KT| Inv1| 01.08.2022| 20.08.2022| -100| -27 |


### Example 2: Corrective invoice to multiple original invoices

* August 2, 2022 (02.08.2022): Purchase invoice Inv2 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.

* August 3, 2022 (03.08.2022): Purchase invoice Inv3 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.

* August 22, 2022 (22.08.2022): Corrective invoice CN2 for a -200,000 HUF tax base and a -54,000 HUF tax amount, where -100,000 HUF are correcting Inv2, and -100,000 HUF are correcting Inv3.

Report for August 2022

65M-02

| Invoice number (a)| Fulfillment date (b)| Tax base (c)| Tax amount (d)| Difference due to advance invoice marking (e) |
| - |
| Inv1| 02.08.2022| 1000| 270|  |
| Inv2| 03.08.2022| 1000| 270|  |


65M-02-K

| Invoice number (a)| Type (b)| Original invoice number (c)| Original fulfillment date (d)| Fulfillment date (e)| Tax base (f)| Tax amount (g) |
| - |
| Inv2| E| | | 02.08.2022| 1000| 270 |
| CN2| KT| Inv2| 02.08.2022| 22.08.2022| -100| -27 |
| Inv3| E| | | 03.08.2022| 1000| 270 |
| CN2| KT| Inv3| 03.08.2022| 22.08.2022| -100| -27 |


### Example 3: Advance invoice for partial amount

* August 3, 2022 (03.08.2022): Invoice for prepayment Inv4 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.

* August 23, 2022 (23.08.2022): Final invoice (minus the invoice for the prepayment) Inv 5 for a 2,000,000 HUF tax base (= 3,000,000 – 1,000,000) and a 54 000 HUF tax amount (= 81,000 – 27,000).

65M-02

| Invoice number (a)| Fulfillment date (b)| Tax base (c)| Tax amount (d)| Difference due to advance invoice marking (e) |
| - |
| Inv4| 03.08.2022| 1000| 270|  |
| Inv5| 23.08.2022| 2000| 540|  |
| Inv5| 23.08.2022| 3000| 810| V |


### Example 4: Advance invoice for full amount

* August 4, 2022 (04.08.2022): Invoice for 100-percent prepayment Inv6 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.

* August 24, 2022 (24.08.2022): Goods are shipped.

65M-02

| Invoice number (a)| Fulfillment date (b)| Tax base (c)| Tax amount (d)| Difference due to advance invoice marking (e) |
| - |
| Inv6| 04.08.2022| 1000| 270|  |


## Configure system parameters

To generate a VAT declaration, you must configure the VAT number.

1.Go to Organization administration > Organizations > Legal entities.

2.Select the legal entity, and then select Registration IDs.

3.Select or create the address in Hungary, and then, on the Registration ID FastTab, select Add.

4.In the Registration type field, select the registration type that is dedicated to Hungary, and that uses the VAT Id registration category.

5.In the Registration number field, enter the tax number.

6.On the General tab, in the Effective field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](https://docs.microsoft.com/dynamics365/finance/localizations/emea-registration-ids).

## Set up a VAT declaration for Hungary

### Import ER configurations

* Open the Electronic reporting workspace, and import the following ER formats:

* VAT declaration XML (HU)

* VAT declaration Excel (HU)

For more information, see [Download ER configurations from the Global repository of Configuration service](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo?toc=/dynamics365/finance/toc.json).

### Set up application-specific parameters for VAT declaration fields

[!NOTE]

We recommend that you enable the Use application specific parameters from previous versions of ER formats feature in the Feature management workspace. When this feature is enabled, parameters that are configured for earlier versions of an ER format automatically become applicable for later versions of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The Use application specific parameters from previous versions of ER formats feature is available in the Feature management workspace as of Dynamics 365 Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up).

To automatically generate a VAT declaration, associate sales tax codes in the application and lookup results in the ER configuration.

#### Set up application-specific parameters for Report field lookup

Follow these steps to define which sales tax codes generate which lines on the VAT declaration (for lines 01–35 and 63–75).

1.Go to Workspaces > Electronic reporting, and select Reporting configurations.

2.Select the VAT declaration XML (HU) configuration, and then select Configurations > Application specific parameters setup.

3.On the Application specific parameters page, on the Lookups FastTab, select Report field lookup.

4.On the Conditions FastTab, set the following fields to associate the sales tax codes and report fields.

| Field| Description |
| - |
| Lookup result| Select the value of the report field. For more information about the values and their assignment to VAT declaration lines, see the [VAT declaration overview](#_VAT_declaration_overview_1) section earlier in this topic. |
| Tax code| Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box.

We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration line. |
| Transaction classifier| If you created enough sales tax codes so that one sales tax code generates an amount on only one VAT declaration line, you can select *Not blank*. Otherwise, select a transaction classifier. The following transaction classifiers are available:

* Purchase – Tax receivable from a purchase or a purchase reverse charge.

* PurchaseExempt –Tax-exempt purchase.

* Sales – Tax payable.

* SalesExempt – Tax-exempt sale.

* SalesReverseCharge – Tax payable from a purchase reverse charge.

* Use tax – Use tax.

For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is PurchaseCreditNote.

Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for the credit note value. |


[!NOTE]

Associate all sales tax codes with lookup results. If any sales tax codes should not generate values on the VAT declaration, associate them with the Other lookup result.

#### Set up application-specific parameters for Details

1.On the Application specific parameters page, on the Lookups FastTab, select Details lookup.

2.On the Conditions FastTab, define which sales tax codes generate which lines on the VAT declaration (for lines 37–42, 45–62, 79, and 88–95, which are details of lines 01–35 and 63–75 that are defined in Report field lookup).

3.Create the last line, and associate all other sales tax codes with the Other lookup result.

| Lookup result| Tax code| Transaction classifier |
| - |
| Other| *Not blank*| *Not blank* |


#### Set up application-specific parameters for In-kind contributions, Assets, and Annex I

1.On the Application specific parameters page, on the Lookups FastTab, select In-kind lookup.

2.On the Conditions FastTab, define which sales tax codes are for in-kind contributions and generate values on lines 44 and 78.

3.Create the last line, and associate all other sales tax codes with the Other lookup result as shown in the last step of the previous procedure.

4.On the Lookups FastTab, select Assets lookup.

5.On the Conditions FastTab, define which sales tax codes are for assets (property, plant, and equipment), sales, and purchases, and generate values on lines 43 and 77.

6.Create the last line, and associate all other sales tax codes with the Other lookup result as before.

7.On the Lookups FastTab, select AnnexI lookup.

8.On the Conditions FastTab, define which sales tax codes generate values in section 65A-01-05 (lines 100 and 101) of the VAT declaration.

9.Create the last line, and associate all other sales tax codes to the Other lookup result, as before.

10.On the Lookups FastTab, select Summary report lookup.

11.On the Conditions FastTab, define which invoice sales tax groups and sales tax codes should be included in the 65M summary report when they are used in vendor invoices. If all vendor invoices should be included on the Summary report, regardless of sales tax groups and sales tax codes, create the following lines.

| Lookup result| Tax code| Tax group |
| - |
| Included| *Not blank*| *Not blank* |
| Included| *Not blank*| *Blank* |


#### Set up application-specific parameter for the XML file format version

1.On the Application specific parameters page, on the Lookups FastTab, select XML values lookup.

2.On the Conditions FastTab, define values for some constant XML elements:

-In the Element column, select FormatVersion.

-In the Lookup result column, enter the value of the format version. For example, for the XML file 2265 applicable for the year 2022, enter 2.0.

5.On the Action Pane, select Export to export the settings in an XML file. Then close the page.

3.Select the VAT declaration Excel (HU) configuration, and then select Configurations > Application specific parameters setup.

4.Select Import, and select the file that you exported earlier.

### Set up the VAT reporting format for preview amounts in Excel

1.In the Feature management workspace, find and select the VAT statement format reports feature in the list, and then select Enable now.

2.Go to General ledger > Setup > General ledger parameters.

3.On the Sales tax tab, on the Tax options FastTab, in the VAT statement format mapping field, select the VAT declaration Excel (HU) ER format.

This format is printed when you run the Report sales tax for settlement period report. It's also printed when you select Print on the Sales tax payments page.

4.On the Tax authorities page, select the tax authority, and then, in the Report layout field, select Default.

If you're configuring the VAT declaration in a legal entity that has [multiple VAT registrations](https://docs.microsoft.com/dynamics365/finance/localizations/emea-reporting-for-multiple-vat-registrations), follow these steps.

1.Go to General ledger > Setup > General ledger parameters.

2.On the Sales tax tab, on the Electronic reporting for countries/regions FastTab, on the line for HUN, select the VAT Declaration Excel (HU) ER format.

## Set up electronic messages

### Download and import the data package that has example settings for electronic messages

The data package contains electronic message settings that are used to preview the VAT declaration in Excel. You can extend these settings or create your own. For more information about how to work with electronic messaging and create your own settings, see [Electronic messaging](https://docs.microsoft.com/dynamics365/finance/general-ledger/electronic-messaging).

1.In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select Data package as the asset type, and then download HU VAT declaration package. The downloaded file is named HU VAT declaration package.zip.

2.In Finance, in the Data management workspace, select Import.

3.On the Import FastTab, in the Group name field, enter a name for the job.

4.On the Selected entities FastTab, select Add file.

5.In the Add file dialog box, verify that the Source data format field is set to Package, select Upload and add, and then select the zip file that you downloaded earlier.

6.Select Close.

7.After the data entities are uploaded, on the Action Pane, select Import.

8.Go to Tax > Inquiries and reports > Electronic messages > Electronic messages, and validate the electronic message processing that you imported (HU VAT declaration).

### Configure electronic messages

1.Go to Tax > Setup > Electronic messages > Populate records actions.

2.Select the line for HU Populate VAT return records, and then select Edit query.

3.Use the filter to specify the settlement periods to include on the report.

4.If you must report tax transactions from other settlement periods in a different declaration, create a new Populate records action, and select the appropriate settlement periods.

## Preview the VAT declaration, incoming transactions, and outgoing transactions in Excel

### Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1.Go to Tax > Periodic tasks > Declarations > Sales tax > Report sales tax for settlement period.

2.Set the following fields.

| Field| Description |
| - |
| Settlement period| Select the settlement period. |
| Sales tax payment version| Select one of the following values:

* Original – Generate a report for the sales tax transactions of the original sales tax payment or before the sales tax payment is generated.

* Corrections – Generate a report for the sales tax transactions of all the subsequent sales tax payments for the period.

* Total list – Generate a report for all the sales tax transactions for the period, including the original and all corrections. |
| From date| Select the start date of the reporting period. |


3.Select OK, and then, in the Electronic report parameters dialog box, set the following fields.

| Field| Description |
| - |
| Tax base - Deductible amount moved from previous period

Tax amount - Deductible amount moved from previous period| Enter the amounts that have been moved from the previous period. These amounts are shown on line 82. |
| Tax base - Receivable amount carried forward

Tax amount - Receivable amount carried forward| Enter the amounts to move to the next period. These amounts are shown on line 86. |


4.Select OK, and review the Excel report.

### Settle and post sales tax

1.Go to Tax > Periodic tasks > Declarations > Sales tax > Settle and post sales tax.

2.Set the following fields.

| Field| Description |
| - |
| Settlement period| Select the settlement period. |
| Sales tax payment version| Select one of the following values:

* Original – Generate the original sales tax payment for the settlement period.

* Latest corrections – Generate a correction sales tax payment after the original sales tax payment for the settlement period was created. |
| From date| Select the start date of the reporting period. |


3.Select OK.

### Preview the VAT declaration in Excel from a sales tax payment

1.Go to Tax > Inquiries and reports > Sales tax inquiries > Sales tax payments, and select a sales tax payment line.

2.Select Print report, and then select OK.

3.Review the Excel file that is generated for the selected sales tax payment line.

[!NOTE]

The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the Report sales tax for settlement period periodic task.

## Generate a VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run a VAT declaration for multiple legal entities](#_Run_a_VAT) section later in this topic.

The following procedure applies to the electronic message processing example that you imported earlier from the LCS Shared asset library.

1.Go to Tax > Inquiries and reports > Electronic messages > Electronic messages.

2.In the left pane, select HU VAT declaration.

3.On the Messages FastTab, select New, and then, in the Run processing dialog box, select OK.

4.Select the message line that is created, enter a description, and then specify the start date and end date for the declaration.

[!NOTE]

Steps 5 through 7 are optional.

5.Optional: On the Messages FastTab, select Collect data, and then select OK. The sales tax payments that were generated earlier are added to the message. For more information, see the [Settle and post sales tax](#_Settle_and_post) section earlier in this topic. If you skip this step, you can still generate a VAT declaration by using the Tax declaration version field in the Declaration dialog box.

6.Optional: On the Message items FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.

7.Optional: Select Original document to review the sales tax payments, or select Delete to exclude sales tax payments from processing. If you skip this step, you can still generate a VAT declaration by using the Tax declaration version field in the Declaration dialog box.

8.On the Messages FastTab, select Update status. In the Update status dialog box, select Ready to generate, and then select OK. Verify that the message status is changed to Ready to generate.

9.Select Generate report. To preview the VAT declaration amounts, in the Run processing dialog box, select Preview report, and then select OK.

10.In the Electronic reporting parameters dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#_Preview_VAT_declaration) section earlier in this topic, and then select OK.

11.Select the Attachments button in the upper-right corner of the page, and then select Open to open the file. Review the amounts in the Excel documents.

12.Select Generate report.

13.To generate a report in XML format, in the Run processing dialog box, select Generate report, and then select OK.

14.Set the following fields.

| Field| Description |
| - |
| Report periodicity| Select Monthly, Quarterly, or Yearly. |
| Tax representative| Select a tax representative, if applicable. |
| Contact person| Select the employee who is a contact for the declaration. |
| Signatory person| Select the employee who signs the declaration. |
| Power of attorney| If you selected a tax representative, select the type of power of attorney: Add-hoc or Permanent. |
| Threshold exceeded| Select Yes if you exceeded the threshold. |
| Tax base - Deductible amount moved from previous period

Tax amount - Deductible amount moved from previous period| Enter the amounts that have been moved from the previous period. These amounts are shown on line 82. |
| Tax base - Receivable amount carried forward

Tax amount - Receivable amount carried forward| Enter the amounts to move to the next period. These amounts are shown on line 86. |


15.Select the Attachments button in the upper-right corner of the page, and download the electronic file that was generated. You should then manually upload this file to the tax authority tool or portal.

## Run a VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1.Go to Workspaces > Feature management.

2.Find and select the Cross-company queries for the populate records actions feature in the list, and then select Enable now.

3.Go to Tax > Setup > Electronic messages > Populate records actions.

4.On the Populate records action page, select the line for HU Populate VAT return records.

In the Datasources setup grid, a new Company field is available. For existing records, this field shows the identifier of the current legal entity.

5.In the Datasources setup grid, add a line for each additional legal entity that must be included in reporting. For each new line, set the following fields.

| Field| Description |
| - |
| Name| Enter a value that will help you understand where this record comes from. For example, enter VAT payment of Subsidiary 1. |
| Message item type| Select VAT return. This value is the only value that is available for all the records. |
| Account type| Select All. |
| Master table name| Specify TaxReportVoucher for all the records. |
| Document number field| Specify Voucher for all the records. |
| Document date field| Specify TransDate for all the records. |
| Document account field| Specify TaxPeriod for all the records. |
| Company| Select the ID of the legal entity. |
| User query| This checkbox is automatically selected when you define criteria by selecting Edit query. |


6.For each new line, select Edit query, and specify a related settlement period for the legal entity that is specified in the Company field on the line.

When the setup is completed, the Collect data function on the Electronic messages page collects sales tax payments from all the legal entities that you defined.
