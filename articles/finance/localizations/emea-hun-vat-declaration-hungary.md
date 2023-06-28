---
title: VAT declaration (Hungary)
description: This article describes how to set up the value-added tax (VAT) declaration 65A with Summary report 65M for Hungary in XML format
author: Andosip
ms.date: 09/14/2022
ms.topic: article
audience: 
ms.reviewer: kfend
ms.search.region: Global
ms.author: atrukawk
ms.search.validFrom: 
---

# VAT declaration (Hungary)

[!include[banner](../includes/banner.md)]

This article describes how to set up the value-added tax (VAT) declaration 65A with Summary report 65M for Hungary in XML format, and how to preview the VAT declaration 65A in Microsoft Excel.

To automatically generate the reports, first create enough sales tax codes to keep a separate VAT accounting for each box on the VAT declaration. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, associate sales tax codes with the lookup result of the lookups for the boxes on the VAT declaration.

For Hungary, you must configure the following elements:

- Report field lookup
- Details lookup
- Annex I lookup
- Assets lookup
- In-kind operations lookup

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#parameters) section later in this topic.

In the following table, the "Lookup result" column shows the lookup result that is preconfigured for a specific VAT declaration row in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the row of the VAT declaration.

## <a name="VAT-declaration-overview"></a>VAT declaration overview

The VAT declaration 65A in Hungary contains the following sections:

* 65A-01-01
* 65A-01-02
* 65A-01-03
* 65A-01-05

### Section 65A-01-01

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

**VAT payable**

<p><strong>&nbsp;</strong></p>
<table>
<tbody>
<tr>
<td width="349">
<p><strong>Description</strong></p>
</td>
<td width="47">
<p><strong>Line</strong></p>
</td>
<td width="94">
<p><strong>Lookup</strong></p>
</td>
<td width="228">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="349">
<p>Supply of goods outside the territory of the Community, supply of services covered by it and supply of goods and services in connection with international transport</p>
</td>
<td width="47">
<p>01</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>01-Export</p>
</td>
</tr>
<tr>
<td width="349">
<p>Intra-Community tax-free supplies of goods with the right to deduct (excluding sales of new means of transport)</p>
</td>
<td width="47">
<p>02</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>02-EUSales</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of intra-community sales of a new means of transport</p>
</td>
<td width="47">
<p>03</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>03-EUSalesNewMeansOfTransport</p>
</td>
</tr>
<tr>
<td width="349">
<p>Supply of goods, the provision of services pursuant to &sect; 142 and tax-free domestic sales</p>
</td>
<td width="47">
<p>04</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>04-TaxFreeDomesticSales</p>
</td>
</tr>
<tr>
<td width="349">
<p>Sales at a rate of 5% - reduced rate</p>
</td>
<td width="47">
<p>05</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>05-DomesticSalesLowerReducedRate</p>
</td>
</tr>
<tr>
<td width="349">
<p>Sales at a rate of 18% - reduced rate</p>
</td>
<td width="47">
<p>06</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>06-DomesticSalesHigherReducedRate</p>
</td>
</tr>
<tr>
<td width="349">
<p>Sales at a rate of 27% - standard rate</p>
</td>
<td width="47">
<p>07</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>07-DomesticSalesStandardRate</p>
</td>
</tr>
<tr>
<td width="349">
<p>Tax-free sales due to their public interest or other special nature</p>
</td>
<td width="47">
<p>08</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>08-TaxFreeSpecialSales</p>
</td>
</tr>
<tr>
<td width="349">
<p>Tax established by a special procedure</p>
</td>
<td width="47">
<p>09</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>09-TaxSpecialProcedure</p>
</td>
</tr>
<tr>
<td width="349">
<p>Tax on investment within one's own business</p>
</td>
<td width="47">
<p>10</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>10-InvestmentOwnBusinessTaxPayable</p>
</td>
</tr>
<tr>
<td width="349">
<p>Tax-free Intra - Community acquisitions of goods</p>
</td>
<td width="47">
<p>11</p>
</td>
<td width="94">
<p>Report field lookup</p>
</td>
<td width="228">
<p>11-EUPurchasesTaxFree</p>
</td>
</tr>
</tbody>
</table>
<p><strong>&nbsp;</strong></p>
<table>
<tbody>
<tr>
<td width="255">
<p><strong>Description</strong></p>
</td>
<td width="47">
<p><strong>Line</strong></p>
</td>
<td width="85">
<p><strong>Lookup</strong></p>
</td>
<td width="332">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="255">
<p>Intra - Community acquisitions of products subject to a 5% rate</p>
</td>
<td width="47">
<p>12</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>12-EUPurchasesLowerReducedRateTaxPayable</p>
<p>1269-EUPurchasesLowerReducedRateUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>Intra - Community acquisitions of products subject to a 18% rate</p>
</td>
<td width="47">
<p>13</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>13-EUPurchasesHigherReducedRateTaxPayable</p>
<p>1369-EUPurchasesHigherReducedRateUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>Intra - Community acquisitions of products subject to a 27% rate</p>
</td>
<td width="47">
<p>14</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>14-EUPurchasesStandardRateTaxPayable</p>
<p>1469-EUPurchasesStandardRateUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>Acquisition of a new means of transport within the Community (27% tax rate)</p>
</td>
<td width="47">
<p>15</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>15-EUPurchasesNewMeansOfTransportTaxPayable</p>
<p>1569-EUPurchasesNewMeansOfTransportUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>Intra - Community acquisitions of excise goods (27% tax rate)</p>
</td>
<td width="47">
<p>16</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>16-EUPurchasesExciseGoodsTaxPayable</p>
<p>1669-EUPurchasesExciseGoodsUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>Use of a tax-free service (from a Community taxable person and another country/region taxable person)</p>
</td>
<td width="47">
<p>17</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>17-PurchaseServicesTaxFree</p>
</td>
</tr>
<tr>
<td width="255">
<p>The obligation to pay tax on a service used from a Community taxable person is subject to VAT Act. Pursuant to Section 37 (1) (tax rate of 27%)</p>
</td>
<td width="47">
<p>18</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>18-EUPurchaseServicesTaxPayable</p>
<p>1867-EUPurchaseServicesUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>Other tax liability on services received from a Community taxable person</p>
</td>
<td width="47">
<p>19</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>19-EUPurchaseServicesOtherTaxPayable</p>
<p>1967-EUPurchaseServicesOtherUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>5% tax payable by the purchaser on the supply of goods in the case of a transaction within the community under VAT Act. Section 91 (2)</p>
</td>
<td width="47">
<p>20</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>20-EUPurchasesTriangularLowerReducedRateTaxPayable</p>
<p>2069-EUPurchasesTriangularLowerReducedRateUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>18% tax payable by the purchaser on the supply of goods in the case of a transaction within the community under VAT Act. Section 91 (2)</p>
</td>
<td width="47">
<p>21</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>21-EUPurchasesTriangularHigherReducedRateTaxPayable</p>
<p>2169-EUPurchasesTriangularHigherReducedRateUseTax</p>
</td>
</tr>
<tr>
<td width="255">
<p>27% tax payable by the purchaser on the supply of goods in the case of a transaction within the community under VAT Act. Section 91 (2)</p>
</td>
<td width="47">
<p>22</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="332">
<p>22-EUPurchasesTriangularStandardRateTaxPayable</p>
<p>2269-EUPurchasesTriangularStandardRateUseTax</p>
</td>
</tr>
</tbody>
</table>
<p><strong>&nbsp;</strong></p>
<table>
<tbody>
<tr>
<td width="302">
<p><strong>Description</strong></p>
</td>
<td width="47">
<p><strong>Line</strong></p>
</td>
<td width="95">
<p><strong>Lookup</strong></p>
</td>
<td width="275">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="302">
<p>Tax - free import of goods</p>
</td>
<td width="47">
<p>23</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>23-ImportGoodsTaxFree</p>
</td>
</tr>
<tr>
<td width="302">
<p>Import of goods taxed at 5%</p>
</td>
<td width="47">
<p>24</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>24-ImportGoodsLowerReducedRateTaxPayable</p>
<p>2471-ImportGoodsLowerReducedRateUseTax</p>
</td>
</tr>
<tr>
<td width="302">
<p>Import of goods taxed at 18%</p>
</td>
<td width="47">
<p>25</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>25-ImportGoodsHigherReducedRateTaxPayable</p>
<p>2571-ImportGoodsHigherReducedRateUseTax</p>
</td>
</tr>
<tr>
<td width="302">
<p>Import of goods taxed at 27%</p>
</td>
<td width="47">
<p>26</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>26-ImportGoodsStandardRateTaxPayable</p>
<p>2671-ImportGoodsStandardRateUseTax</p>
</td>
</tr>
<tr>
<td width="302">
<p>Obligation to pay tax on a service provided by a taxable person in a non - Community country/region</p>
</td>
<td width="47">
<p>27</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>27-PurchasesServiceThirdCountryTaxPayable</p>
<p>2767-PurchasesServiceThirdCountryUseTax</p>
</td>
</tr>
<tr>
<td width="302">
<p>Purchase of goods pursuant to VAT Act &sect; 32, &sect; 34 (27% tax rate)</p>
</td>
<td width="47">
<p>28</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>28-DomesticAssemblyElectricityTaxPayable</p>
<p>2867-DomesticAssemblyElectricityUseTax</p>
</td>
</tr>
<tr>
<td width="302">
<p>Tax payable under the rules of reverse charge pursuant to VAT Act &sect; 142</p>
</td>
<td width="47">
<p>29</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>29-PurchaseReverseChargeTaxPayable</p>
<p>2966-PurchaseReverseChargeUseTax</p>
</td>
</tr>
<tr>
<td width="302">
<p>Item reducing the tax payable pursuant to VAT Act Section 99 (9)</p>
</td>
<td width="47">
<p>30</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>30-TaxReimbursedForeignPassenger</p>
</td>
</tr>
<tr>
<td width="302">
<p>Total tax increase item pursuant to VAT Act 153 / C. &sect;</p>
</td>
<td width="47">
<p>31</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>31-TaxIncrease</p>
</td>
</tr>
<tr>
<td width="302">
<p>Other</p>
</td>
<td width="47">
<p>35</p>
</td>
<td width="95">
<p>Report field lookup</p>
</td>
<td width="275">
<p>35-OtherTaxPayable</p>
</td>
</tr>
<tr>
<td width="302">
<p><strong>Total (lines 01 - 35)</strong></p>
</td>
<td width="47">
<p><strong>36</strong></p>
</td>
<td width="95">
<p><strong>Not applicable</strong></p>
</td>
<td width="275">
<p><strong>Total of lines 01 through 35</strong></p>
</td>
</tr>
</tbody>
</table>


### Section 65A-01-02

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

**Details of VAT payable**

<table>
<tbody>
<tr>
<td width="349">
<p><strong>Description</strong></p>
</td>
<td width="47">
<p><strong>Line</strong></p>
</td>
<td width="76">
<p><strong>Lookup</strong></p>
</td>
<td width="247">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="349">
<p>The value of the export of goods from line 01 according to VAT Act &sect; 98</p>
</td>
<td width="47">
<p>37</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>37-Export98</p>
</td>
</tr>
<tr>
<td width="349">
<p>The value of goods placed in a tax warehouse and resold there or unloaded there</p>
</td>
<td width="47">
<p>38</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>38-TaxWarehouseTaxableSales</p>
</td>
</tr>
<tr>
<td width="349">
<p>Value of goods from tax-free Community acquisitions placed in a tax warehouse from the amount of line 11</p>
</td>
<td width="47">
<p>39</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>39-TaxWarehouseTaxFreeSales</p>
</td>
</tr>
<tr>
<td width="349">
<p>The amount of supplies of goods which are the subject of domestic assembly or assembly on the basis of a Community mandate from rows 05-07</p>
</td>
<td width="47">
<p>40</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>40-SalesDomesticAssembly</p>
</td>
</tr>
<tr>
<td width="349">
<p>The amount of distance selling from rows 05-07</p>
</td>
<td width="47">
<p>41</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>41-DistanceSelling</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of purchases of goods to be assembled or assembled domestically on the basis of a Community mandate from line 28</p>
</td>
<td width="47">
<p>42</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>42-PurchasesDomesticAssembly</p>
</td>
</tr>
<tr>
<td width="349">
<p>Sales of property, plant and equipment from line 36 (excluding in-kind sales)</p>
</td>
<td width="47">
<p>43</p>
</td>
<td width="76">
<p>Assets</p>
</td>
<td width="247">
<p>43-SalesPropertyPlantEquipment</p>
</td>
</tr>
<tr>
<td width="349">
<p>In-kind sales from line 36</p>
</td>
<td width="47">
<p>44</p>
</td>
<td width="76">
<p>InKind</p>
</td>
<td width="247">
<p>44-InKindSales</p>
</td>
</tr>
<tr>
<td width="349">
<p>The amount received as an advance payment from the sum of the rows 05-07</p>
</td>
<td width="47">
<p>45</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>45-AdvancesDomesticTaxableSales</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount received as an advance from the sum of lines 01 and 04</p>
</td>
<td width="47">
<p>46</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>46-AdvancesTaxFreeSalesExport</p>
</td>
</tr>
<tr>
<td width="349">
<p>Intra-Community sales of new means of transport to non-taxable persons from line 03</p>
</td>
<td width="47">
<p>47</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>47-EUSalesNewMeansOfTransportNonTaxablePerson</p>
</td>
</tr>
<tr>
<td width="349">
<p>Excise tax content in the tax base of lines 11, 16</p>
</td>
<td width="47">
<p>48</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>48-EUPurchasesExcise</p>
</td>
</tr>
<tr>
<td width="349">
<p>Tax payable on the provision of travel services from line 09</p>
</td>
<td width="47">
<p>49</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>49-SpecialProcedureTravelServices</p>
</td>
</tr>
<tr>
<td width="349">
<p>Tax from the amount of line 09 under VAT Act Chapter XVI</p>
</td>
<td width="47">
<p>50</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>50-SpecialProcedureXVI</p>
</td>
</tr>
<tr>
<td width="349">
<p>The tax payable on the property under the rules of reverse charge in the amount of line 29</p>
</td>
<td width="47">
<p>51</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>51-ReverseChargePropertyTaxPayable</p>
</td>
</tr>
<tr>
<td width="349">
<p>The tax payable on waste under the rules of reverse in the amount of line 29</p>
</td>
<td width="47">
<p>52</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>52-ReverseChargeWasteTaxPayable</p>
</td>
</tr>
<tr>
<td width="349">
<p>The tax payable in case of transfer of a property right entitling to emit a greenhouse gas under the rules of reverse charge taxation from the amount of line 29</p>
</td>
<td width="47">
<p>53</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>53-ReverseChargeGreenhouseGasTaxPayable</p>
</td>
</tr>
<tr>
<td width="349">
<p>The tax payable in case of using the service according to the rules of reverse charge taxation specified in &sect; 142 of VAT Act from the amount of line 29</p>
</td>
<td width="47">
<p>54</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>54-ReverseChargeService142TaxPayable</p>
</td>
</tr>
<tr>
<td width="349">
<p>The tax payable in case of using the service according to the rules of reverse charge taxation specified in &sect; 142 of VAT Act from the amount of line 29</p>
</td>
<td width="47">
<p>55</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>55-TaxGuaranteeTaxWarehousing</p>
</td>
</tr>
<tr>
<td width="349">
<p>Sales subject to tax guarantees on intra-Community sales made by the importer in connection with tax-free imports of products from line 02</p>
</td>
<td width="47">
<p>56</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>56-EUSalesTaxGuarantees</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of tax-free intra-Community sales made by the importer / taxable person but declared by the indirect customs representative / tax warehouse operator from line 02</p>
</td>
<td width="47">
<p>57</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>57-EUSalesDeclaredByRepresentative</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of tax-free sales of a new means of transport within the Community made by the importer / taxable person but declared by the indirect customs representative / tax warehouse operator from line 03</p>
</td>
<td width="47">
<p>58</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>58-EUSalesNewMeansOfTransportDeclaredByRepresentative</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of tax-free imports from line 23 made by the importer but declared by the indirect customs representative in the framework of self-taxation</p>
</td>
<td width="47">
<p>59</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>59-ImportGoodsTaxFreeDeclaredByRepresentative</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of imports of the goods taxed at 5% made by the importer but declared by the indirect customs representative in the framework of self-taxation from line 24</p>
</td>
<td width="47">
<p>60</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>60-ImportGoodsLowerReducedRateDeclaredByRepresentative</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of imports of the goods taxed at 18% made by the importer but declared by the indirect customs representative in the framework of self-taxation from line 25</p>
</td>
<td width="47">
<p>61</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>61-ImportGoodsHigherReducedRateDeclaredByRepresentative</p>
</td>
</tr>
<tr>
<td width="349">
<p>Amount of imports of the goods taxed at 27% made by the importer but declared by the indirect customs representative in the framework of self-taxation from line 26</p>
</td>
<td width="47">
<p>62</p>
</td>
<td width="76">
<p>Details</p>
</td>
<td width="247">
<p>62-ImportGoodsStandardRateDeclaredByRepresentative</p>
</td>
</tr>
</tbody>
</table>


**Deductible input tax on purchases**

<table>
<tbody>
<tr>
<td width="293">
<p><strong>Description</strong></p>
</td>
<td width="38">
<p><strong>Line</strong></p>
</td>
<td width="85">
<p><strong>Lookup</strong></p>
</td>
<td width="304">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="293">
<p>Domestic purchase of tax - free goods</p>
</td>
<td width="38">
<p>63</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>63-TaxFreeDomesticPurchases</p>
</td>
</tr>
<tr>
<td width="293">
<p>Purchase of goods and services under the 5% rate</p>
</td>
<td width="38">
<p>64</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>64-PurchasesLowerReducedRate</p>
</td>
</tr>
<tr>
<td width="293">
<p>Purchase of goods and services under the 18% rate</p>
</td>
<td width="38">
<p>65</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>65-PurchasesHigherReducedRate</p>
</td>
</tr>
<tr>
<td width="293">
<p>Purchase of goods and services under the 27% rate</p>
</td>
<td width="38">
<p>66</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>66-PurchasesStandardRate</p>
<p>2966-PurchaseReverseChargeUseTax</p>
</td>
</tr>
<tr>
<td width="293">
<p>Amount tax deductible from tax paid on a service provided by a taxable person in a non-member country/region or in the Community or as a purchaser of a product in their own name</p>
</td>
<td width="38">
<p>67</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>67-PurchasesServicesTaxDeductible</p>
<p>1867-EUPurchaseServicesUseTax</p>
<p>1967-EUPurchaseServicesOtherUseTax</p>
<p>2767-PurchasesServiceThirdCountryUseTax</p>
<p>2867-DomesticAssemblyElectricityUseTax</p>
</td>
</tr>
<tr>
<td width="293">
<p>Taxable amount deductible (Original tax base, proportional tax)</p>
</td>
<td width="38">
<p>68</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>68-PurchasesProrataTaxDeductible</p>
</td>
</tr>
<tr>
<td width="293">
<p>Amount of tax deductible on intra - Community acquisitions of goods</p>
</td>
<td width="38">
<p>69</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>69-EUPurchasesTaxDeductible</p>
<p>1269-EUPurchasesLowerReducedRateUseTax</p>
<p>1369-EUPurchasesHigherReducedRateUseTax</p>
<p>1469-EUPurchasesStandardRateUseTax</p>
<p>1569-EUPurchasesNewMeansOfTransportUseTax</p>
<p>1669-EUPurchasesExciseGoodsUseTax</p>
<p>2069-EUPurchasesTriangularLowerReducedRateUseTax</p>
<p>2169-EUPurchasesTriangularHigherReducedRateUseTax</p>
<p>2269-EUPurchasesTriangularStandardRateUseTax</p>
</td>
</tr>
<tr>
<td width="293">
<p>Deductible part of the tax paid on an imported product (by imposition)</p>
</td>
<td width="38">
<p>70</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>70-ImportGoodsTaxDeductible</p>
<p>70-ImportGoodsProRataTaxDeductible</p>
</td>
</tr>
<tr>
<td width="293">
<p>Deductible part of tax paid on imported product (with self - taxation)</p>
</td>
<td width="38">
<p>71</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="304">
<p>71-ImportGoodsSelfTaxationTaxDeductible</p>
<p>71-ImportGoodsProRataSelfTaxationTaxDeductible</p>
<p>2471-ImportGoodsLowerReducedRateUseTax</p>
<p>2571-ImportGoodsHigherReducedRateUseTax</p>
<p>2671-ImportGoodsStandardRateUseTax</p>
</td>
</tr>
</tbody>
</table>


### Section 65A-01-03

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

**Deductible input tax on purchases**

<table>
<tbody>
<tr>
<td width="321">
<p><strong>Description</strong></p>
</td>
<td width="47">
<p><strong>Line</strong></p>
</td>
<td width="85">
<p><strong>Lookup</strong></p>
</td>
<td width="266">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="321">
<p>7% agricultural compensation surcharge</p>
</td>
<td width="47">
<p>72</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="266">
<p>72-AgriculturalCompensationSurchargeLowerRate</p>
</td>
</tr>
<tr>
<td width="321">
<p>12% agricultural compensation surcharge</p>
</td>
<td width="47">
<p>73</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="266">
<p>73-AgriculturalCompensationSurchargeHigherRate</p>
</td>
</tr>
<tr>
<td width="321">
<p>After investing within your own business</p>
</td>
<td width="47">
<p>74</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="266">
<p>74-InvestmentsOwnBusiness</p>
</td>
</tr>
<tr>
<td width="321">
<p>Other</p>
</td>
<td width="47">
<p>75</p>
</td>
<td width="85">
<p>Report field lookup</p>
</td>
<td width="266">
<p>75-OtherTaxDeductible</p>
</td>
</tr>
<tr>
<td width="321">
<p><strong>Total (sum of lines 63-75)</strong></p>
</td>
<td width="47">
<p><strong>76</strong></p>
</td>
<td width="85">
<p><strong>Not applicable</strong></p>
</td>
<td width="266">
<p><strong>Total of lines 63 through 75</strong></p>
</td>
</tr>
<tr>
<td width="321">
<p>Amount of tax deductible on the acquisition of a tangible asset from the amount of line 76 (excluding in-kind purchases)</p>
</td>
<td width="47">
<p>77</p>
</td>
<td width="85">
<p>Assets</p>
</td>
<td width="266">
<p>77-PurchasesTangibleAssets</p>
</td>
</tr>
<tr>
<td width="321">
<p>The amount of tax deductible on in-kind purchases from line 76</p>
</td>
<td width="47">
<p>78</p>
</td>
<td width="85">
<p>In-Kind</p>
</td>
<td width="266">
<p>78-InKindPurchases</p>
</td>
</tr>
<tr>
<td width="321">
<p>The amount of the unrealized investment in one's own enterprise from the amount of line 76</p>
</td>
<td width="47">
<p>79</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>79-UnrelizedInvestmentsOwnBusiness</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


**Value added tax accounting**

<table>
<tbody>
<tr>
<td width="312">
<p><strong>Description</strong></p>
</td>
<td width="57">
<p><strong>Line</strong></p>
</td>
<td width="85">
<p><strong>Data source type</strong></p>
</td>
<td width="266">
<p><strong>Data source</strong></p>
</td>
</tr>
<tr>
<td width="312">
<p>Amount of deductible item moved from previous period (from the line "Amount of receivable carried forward" of the previous period's declaration)</p>
</td>
<td width="57">
<p>82</p>
</td>
<td width="85">
<p>User input parameter</p>
</td>
<td width="266">
<p>Tax base - Deductible amount moved from previous period</p>
<p>Tax amount - Deductible amount moved from previous period</p>
</td>
</tr>
<tr>
<td width="312">
<p>The difference between the total amount of tax payable during the reference period and the deductible input tax (line 36 - line 76 - line 82)</p>
</td>
<td width="57">
<p>83</p>
</td>
<td width="85">
<p>Not applicable</p>
</td>
<td width="266">
<p>The result of the following formula:</p>
<p>Line 36 &ndash; line 76 &ndash; line 82</p>
</td>
</tr>
<tr>
<td width="312">
<p>Amount of tax to be paid (if amount in line 83 is positive)</p>
</td>
<td width="57">
<p>84</p>
</td>
<td width="85">
<p>Not applicable</p>
</td>
<td width="266">
<p>The result of the following formula:</p>
<p>Line 83, if line 83 &gt; 0; otherwise, 0</p>
</td>
</tr>
<tr>
<td width="312">
<p>Amount of recoverable tax (if amount in line 83 is negative and you are entitled to a refund)</p>
</td>
<td width="57">
<p>85</p>
</td>
<td width="85">
<p>Not applicable</p>
</td>
<td width="266">
<p>The result of the following formula:</p>
<p>0 &ndash; line 83, if 83 &lt; 0; otherwise, 0</p>
</td>
</tr>
<tr>
<td width="312">
<p>Amount of receivable carried forward</p>
</td>
<td width="57">
<p>86</p>
</td>
<td width="85">
<p>User input parameter</p>
</td>
<td width="266">
<p>Tax base &ndash; Receivable amount carried forward</p>
<p>Tax amount &ndash; Receivable amount carried forward</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


**Details of the return**

<table>
<tbody>
<tr>
<td width="321">
<p><strong>Description</strong></p>
</td>
<td width="47">
<p><strong>Line</strong></p>
</td>
<td width="85">
<p><strong>Lookup</strong></p>
</td>
<td width="266">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="321">
<p>The value, exclusive of tax, of goods acquired for resale in the form of an intermediate customer in a "triangular transaction" (Intra-Community )</p>
</td>
<td width="47">
<p>88</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>88-PurchasesGoodsTriangularB</p>
</td>
</tr>
<tr>
<td width="321">
<p>The value, exclusive tax, of goods resold as an intermediate customer in a "triangular transaction" (Intra-Community)</p>
</td>
<td width="47">
<p>89</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>89-SalesGoodsTriangularB</p>
</td>
</tr>
<tr>
<td width="321">
<p>Tax-free value of supplies of goods effected outside its territorial scope</p>
</td>
<td width="47">
<p>90</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>90-TaxFreeSalesGoodsOutsideTerritorialScope</p>
<p>9094-TaxFreeSalesGoodsAssembledOutsideTerritorialScope</p>
<p>9095-EUDistanceSales</p>
</td>
</tr>
<tr>
<td width="321">
<p>Tax-free value of the supply of services outside its territorial scope</p>
</td>
<td width="47">
<p>91</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>91-TaxFreeSalesServicesOutsideTerritorialScope</p>
<p>9192-TaxFreeSalesServicesOutsideTerritorialScope</p>
<p>9193-TaxFreeSalesServicesOutsideTerritorialScope</p>
</td>
</tr>
<tr>
<td width="321">
<p>Tax-free value for the supply of services falling under Section 37 (1) from the amount of line 91</p>
</td>
<td width="47">
<p>92</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>9192-TaxFreeSalesServicesOutsideTerritorialScope</p>
</td>
</tr>
<tr>
<td width="321">
<p>Tax-free value for the supply of services other than Section 37 (1) from the amount of line 91</p>
</td>
<td width="47">
<p>93</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>9193-TaxFreeSalesServicesOutsideTerritorialScope</p>
</td>
</tr>
<tr>
<td width="321">
<p>The tax-free value of goods which are considered to have been assembled or assembled in another Member State of the Community from line 90</p>
</td>
<td width="47">
<p>94</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>9094-TaxFreeSalesGoodsAssembledOutsideTerritorialScope</p>
</td>
</tr>
<tr>
<td width="321">
<p>Remuneration, net of tax, of distance sales effected in another Member State of the Community from line 90</p>
</td>
<td width="47">
<p>95</p>
</td>
<td width="85">
<p>Details</p>
</td>
<td width="266">
<p>9095-EUDistanceSales</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


### Section 65A-01-05

Use the following tables to determine how a lookup result that is preconfigured in the format is associated with a VAT declaration box.

**Sale / purchase of products listed in Annex I to Regulation (EC)**

<table>
<tbody>
<tr>
<td width="321">
<p><strong>Description</strong></p>
</td>
<td width="47">
<p><strong>Line</strong></p>
</td>
<td width="85">
<p><strong>Lookup</strong></p>
</td>
<td width="266">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="321">
<p>Agricultural products - The tax base of products sold under reverse charge from the amount of line 04</p>
</td>
<td width="47">
<p>100B</p>
</td>
<td width="85">
<p>AnnexI</p>
</td>
<td width="266">
<p>100B-DomesticSalesRCAgriculturalProducts</p>
</td>
</tr>
<tr>
<td width="321">
<p>Agricultural products - Tax base and tax for goods acquired under reverse charge from the amount of line 29</p>
</td>
<td width="47">
<p>100D</p>
</td>
<td width="85">
<p>AnnexI</p>
</td>
<td width="266">
<p>101B-PurchaseReverseChargeAgriculturalProductsTaxDue</p>
</td>
</tr>
<tr>
<td width="321">
<p>Iron and steel products - The tax base of products sold under reverse charge from the amount of line 04</p>
</td>
<td width="47">
<p>101B</p>
</td>
<td width="85">
<p>AnnexI</p>
</td>
<td width="266">
<p>100D-DomesticSalesRCIronSteel</p>
</td>
</tr>
<tr>
<td width="321">
<p>Iron and steel products - Tax base and tax for goods acquired under reverse charge from the amount of line 29</p>
</td>
<td width="47">
<p>101D</p>
</td>
<td width="85">
<p>AnnexI</p>
</td>
<td width="266">
<p>101D-PurchaseReverseChargeIronSteelTaxDue</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


### Purchase reverse charge VAT

If you configure sales tax codes to post incoming reverse charge VAT by using use tax, associate your sales tax codes with the lookup result of **Report field lookup** that contains "UseTax" in the name.

Alternatively, you can configure two separate sales tax codes: one for VAT due and one for VAT deduction. Then associate each code with the corresponding lookup results of **Report field lookup**.

For example, for taxable intra-community acquisitions, you configure sales tax code **UT_S_EU** with use tax and associate it with the **1469-EUPurchasesStandardRateUseTax** lookup result of **Report field lookup**. In this case, transactions that use the **UT_S_EU** sales tax code are reflected on lines 14 ("Intra - Community acquisitions of products subject to a 27% rate") and 69 ("Amount of tax deductible on intra - Community acquisitions of goods").

Alternatively, you configure two sales tax codes:

* **VAT_S_EU**, which has a tax rate value of -27 percent

* **InVAT_S_EU**, which has a tax rate value of 27 percent

You then associate the codes with lookup results of **Report field lookup** in the following way:

* Associate **VAT_S_EU** with the **14-EUPurchasesStandardRateTaxPayable** lookup result.

* Associate **InVAT_S_EU** with the 69-**EUPurchasesTaxDeductible** lookup result.

In this case, amounts that use the **VAT_S_EU** sales tax code are reflected on line 14 ("Intra - Community acquisitions of products subject to a 27% rate"). Amounts that use the **InVAT_S_EU** sales tax code are reflected on line 69 ("Amount of tax deductible on intra - Community acquisitions of goods").

For more information about how to configure reverse charge VAT, see [Reverse charges](emea-reverse-charge.md).

## Summary report overview

In Hungary, you can generate a report 65M that contains the following information for each vendor:

- The number of purchase invoices, and their total tax base and tax amount
- The number of corrective invoices, and their total tax base and tax amount
- The list of all purchase invoices in section 65M-02, regardless of the threshold
- The list of corrective invoices in section 65M-02-K, regardless of the threshold

A list of purchase invoices 65M-02 lists all the purchase invoices for the period. For each invoice, it contains the following information:

- The invoice number.
- The fulfillment date. The fulfillment date is the date when the goods are sold or the services are performed. If an invoice doesn't have a fulfillment date, the invoice date is used.
- The tax base in 1,000 Hungarian forints (HUF).
- The tax amount in 1,000 HUF.
- The marking of the final invoice that is received after receipt of the advance invoice.

A list of corrective invoices 65M-02-K lists all the corrective invoices. For each corrective invoice and its original invoice, it contains the following information:

- The invoice or corrective invoice number
- The line type "E" for original invoice or "KT" for corrective invoice
- The original invoice number for the line for a corrective invoice
- The original invoice fulfillment date for the line for a corrective invoice
- The invoice or corrective invoice fulfillment date
- The tax base in 1,000 HUF
- The tax amount in 1,000 HUF

The following are examples show how report 65M is filled in.

### Example 1: Corrective invoice

- **August 1, 2022 (01.08.2022)**: Purchase invoice Inv1 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.
- **August 20, 2022 (20.08.2022)**: Corrective invoice CN1 for a -100,000 HUF tax base and a -27,000 HUF tax amount.

**Report for August 2022**

_65M-02_

<table>
<tbody>
<tr>
<td width="146">
<p><strong>Invoice number (a)</strong></p>
</td>
<td width="151">
<p><strong>Fulfillment date (b)</strong></p>
</td>
<td width="142">
<p><strong>Tax base (c)</strong></p>
</td>
<td width="146">
<p><strong>Tax amount (d)</strong></p>
</td>
<td width="134">
<p><strong>Difference due to advance invoice marking (e)</strong></p>
</td>
</tr>
<tr>
<td width="146">
<p>Inv1</p>
</td>
<td width="151">
<p>01.08.2022</p>
</td>
<td width="142">
<p>1000</p>
</td>
<td width="146">
<p>270</p>
</td>
<td width="134">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


_65M-02-K_

<table>
<tbody>
<tr>
<td width="94">
<p><strong>Invoice number (a)</strong></p>
</td>
<td width="77">
<p><strong>Type (b)</strong></p>
</td>
<td width="89">
<p><strong>Original invoice number (c)</strong></p>
</td>
<td width="92">
<p><strong>Original fulfillment date (d)</strong></p>
</td>
<td width="110">
<p><strong>Fulfillment date (e)</strong></p>
</td>
<td width="81">
<p><strong>Tax base (f)</strong></p>
</td>
<td width="94">
<p><strong>Tax amount (g)</strong></p>
</td>
</tr>
<tr>
<td width="94">
<p>Inv1</p>
</td>
<td width="77">
<p>E</p>
</td>
<td width="89">
<p>&nbsp;</p>
</td>
<td width="92">
<p>&nbsp;</p>
</td>
<td width="110">
<p>01.08.2022</p>
</td>
<td width="81">
<p>1000</p>
</td>
<td width="94">
<p>270</p>
</td>
</tr>
<tr>
<td width="94">
<p>CN1</p>
</td>
<td width="77">
<p>KT</p>
</td>
<td width="89">
<p>Inv1</p>
</td>
<td width="92">
<p>01.08.2022</p>
</td>
<td width="110">
<p>20.08.2022</p>
</td>
<td width="81">
<p>-100</p>
</td>
<td width="94">
<p>-27</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


### Example 2: Corrective invoice to multiple original invoices

- **August 2, 2022 (02.08.2022)**: Purchase invoice Inv2 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.
- **August 3, 2022 (03.08.2022)**: Purchase invoice Inv3 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.
- **August 22, 2022 (22.08.2022)**: Corrective invoice CN2 for a -200,000 HUF tax base and a -54,000 HUF tax amount, where -100,000 HUF are correcting Inv2, and -100,000 HUF are correcting Inv3.

**Report for August 2022**

_65M-02_

<table>
<tbody>
<tr>
<td width="146">
<p><strong>Invoice number (a)</strong></p>
</td>
<td width="151">
<p><strong>Fulfillment date (b)</strong></p>
</td>
<td width="142">
<p><strong>Tax base (c)</strong></p>
</td>
<td width="146">
<p><strong>Tax amount (d)</strong></p>
</td>
<td width="134">
<p><strong>Difference due to advance invoice marking (e)</strong></p>
</td>
</tr>
<tr>
<td width="146">
<p>Inv1</p>
</td>
<td width="151">
<p>02.08.2022</p>
</td>
<td width="142">
<p>1000</p>
</td>
<td width="146">
<p>270</p>
</td>
<td width="134">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="146">
<p>Inv2</p>
</td>
<td width="151">
<p>03.08.2022</p>
</td>
<td width="142">
<p>1000</p>
</td>
<td width="146">
<p>270</p>
</td>
<td width="134">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


_65M-02-K_

<table>
<tbody>
<tr>
<td width="94">
<p><strong>Invoice number (a)</strong></p>
</td>
<td width="77">
<p><strong>Type (b)</strong></p>
</td>
<td width="89">
<p><strong>Original invoice number (c)</strong></p>
</td>
<td width="92">
<p><strong>Original fulfillment date (d)</strong></p>
</td>
<td width="110">
<p><strong>Fulfillment date (e)</strong></p>
</td>
<td width="81">
<p><strong>Tax base (f)</strong></p>
</td>
<td width="94">
<p><strong>Tax amount (g)</strong></p>
</td>
</tr>
<tr>
<td width="94">
<p>Inv2</p>
</td>
<td width="77">
<p>E</p>
</td>
<td width="89">
<p>&nbsp;</p>
</td>
<td width="92">
<p>&nbsp;</p>
</td>
<td width="110">
<p>02.08.2022</p>
</td>
<td width="81">
<p>1000</p>
</td>
<td width="94">
<p>270</p>
</td>
</tr>
<tr>
<td width="94">
<p>CN2</p>
</td>
<td width="77">
<p>KT</p>
</td>
<td width="89">
<p>Inv2</p>
</td>
<td width="92">
<p>02.08.2022</p>
</td>
<td width="110">
<p>22.08.2022</p>
</td>
<td width="81">
<p>-100</p>
</td>
<td width="94">
<p>-27</p>
</td>
</tr>
<tr>
<td width="94">
<p>Inv3</p>
</td>
<td width="77">
<p>E</p>
</td>
<td width="89">
<p>&nbsp;</p>
</td>
<td width="92">
<p>&nbsp;</p>
</td>
<td width="110">
<p>03.08.2022</p>
</td>
<td width="81">
<p>1000</p>
</td>
<td width="94">
<p>270</p>
</td>
</tr>
<tr>
<td width="94">
<p>CN2</p>
</td>
<td width="77">
<p>KT</p>
</td>
<td width="89">
<p>Inv3</p>
</td>
<td width="92">
<p>03.08.2022</p>
</td>
<td width="110">
<p>22.08.2022</p>
</td>
<td width="81">
<p>-100</p>
</td>
<td width="94">
<p>-27</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


### Example 3: Advance invoice for partial amount

- **August 3, 2022 (03.08.2022)**: Invoice for prepayment Inv4 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.
- **August 23, 2022 (23.08.2022)**: Final invoice (minus the invoice for the prepayment) Inv 5 for a 2,000,000 HUF tax base (= 3,000,000 – 1,000,000) and a 54 000 HUF tax amount (= 81,000 – 27,000).

_65M-02_

<table>
<tbody>
<tr>
<td width="146">
<p><strong>Invoice number (a)</strong></p>
</td>
<td width="151">
<p><strong>Fulfillment date (b)</strong></p>
</td>
<td width="142">
<p><strong>Tax base (c)</strong></p>
</td>
<td width="146">
<p><strong>Tax amount (d)</strong></p>
</td>
<td width="134">
<p><strong>Difference due to advance invoice marking (e)</strong></p>
</td>
</tr>
<tr>
<td width="146">
<p>Inv4</p>
</td>
<td width="151">
<p>03.08.2022</p>
</td>
<td width="142">
<p>1000</p>
</td>
<td width="146">
<p>270</p>
</td>
<td width="134">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="146">
<p>Inv5</p>
</td>
<td width="151">
<p>23.08.2022</p>
</td>
<td width="142">
<p>2000</p>
</td>
<td width="146">
<p>540</p>
</td>
<td width="134">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="146">
<p>Inv5</p>
</td>
<td width="151">
<p>23.08.2022</p>
</td>
<td width="142">
<p>3000</p>
</td>
<td width="146">
<p>810</p>
</td>
<td width="134">
<p>V</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


### Example 4: Advance invoice for full amount

- **August 4, 2022 (04.08.2022)**: Invoice for 100-percent prepayment Inv6 for a 1,000,000 HUF tax base and a 270,000 HUF tax amount.
- **August 24, 2022 (24.08.2022)**: Goods are shipped.

_65M-02_
<table>
<tbody>
<tr>
<td width="146">
<p><strong>Invoice number (a)</strong></p>
</td>
<td width="151">
<p><strong>Fulfillment date (b)</strong></p>
</td>
<td width="142">
<p><strong>Tax base (c)</strong></p>
</td>
<td width="146">
<p><strong>Tax amount (d)</strong></p>
</td>
<td width="134">
<p><strong>Difference due to advance invoice marking (e)</strong></p>
</td>
</tr>
<tr>
<td width="146">
<p>Inv6</p>
</td>
<td width="151">
<p>04.08.2022</p>
</td>
<td width="142">
<p>1000</p>
</td>
<td width="146">
<p>270</p>
</td>
<td width="134">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


## Configure system parameters

To generate a VAT declaration, you must configure the VAT number.

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
2. Select the legal entity, and then select **Registration IDs**.
3. Select or create the address in Hungary, and then, on the **Registration ID** FastTab, select **Add**.
4. In the **Registration type** field, select the registration type that is dedicated to Hungary, and that uses the **VAT Id** registration category.
5. In the **Registration number** field, enter the tax number.
6. On the **General** tab, in the **Effective** field, enter the date when the number becomes effective.

For more information about how to set up registration categories and registration types, see [Registration IDs](emea-registration-ids.md).

## Set up a VAT declaration for Hungary

### Import ER configurations

- Open the **Electronic reporting** workspace, and import the following ER formats:

  - VAT declaration XML (HU)
  - VAT declaration Excel (HU)

For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="parameters"></a>Set up application-specific parameters for VAT declaration fields

> [!NOTE]
> 
> We recommend that you enable the **Use application specific parameters from previous versions of ER formats** feature in the **Feature management** workspace. When this feature is enabled, parameters that are configured for earlier versions of an ER format automatically become applicable for later versions of the same format. If this feature isn't enabled, you must explicitly configure application-specific parameters for each format version. The **Use application specific parameters from previous versions of ER formats** feature is available in the **Feature management** workspace as of Dynamics 365 Finance version 10.0.23. For more information about how to set up the parameters of an ER format for each legal entity, see [Set up the parameters of an ER format per legal entity](../../fin-ops-core/dev-itpro/analytics/er-app-specific-parameters-set-up.md).

To automatically generate a VAT declaration, associate sales tax codes in the application and lookup results in the ER configuration.

#### Set up application-specific parameters for Report field lookup

Follow these steps to define which sales tax codes generate which lines on the VAT declaration (for lines 01–35 and 63–75).

1. Go to **Workspaces** > **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration XML (HU)** configuration, and then select **Configurations** > **Application specific parameters setup**.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and report fields.

<table>
<tbody>
<tr>
<td>
<p><strong>Field</strong></p>
</td>
<td>
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td>
<p>Lookup result</p>
</td>
<td>
<p>Select the value of the report field. For more information about the values and their assignment to VAT declaration lines, see the [VAT declaration overview](#VAT-declaration-overview) section earlier in this topic.</p>
</td>
</tr>
<tr>
<td>
<p>Tax code</p>
</td>
<td>
<p>Select the sales tax code to associate with the report field. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box.</p>
<p>We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration line.</p>
</td>
</tr>
<tr>
<td>
<p>Transaction classifier</p>
</td>
<td>
<p>If you created enough sales tax codes so that one sales tax code generates an amount on only one VAT declaration line, you can select <strong>*Not blank*</strong>. Otherwise, select a transaction classifier. The following transaction classifiers are available:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Purchase &ndash; Tax receivable from a purchase or a purchase reverse charge.</strong></p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>PurchaseExempt</strong> &ndash;Tax-exempt purchase.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Sales &ndash; Tax payable.</strong></p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>SalesExempt</strong> &ndash; Tax-exempt sale.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>SalesReverseCharge</strong> &ndash; Tax payable from a purchase reverse charge.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Use tax &ndash; Use tax.</strong></p>
<p>For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is <strong>PurchaseCreditNote</strong>.</p>
<p>Be sure to create two lines for each sales tax code: one that has the transaction classifier value and one that has the transaction classifier for the credit note value.</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


> [!NOTE]
> 
> Associate all sales tax codes with lookup results. If any sales tax codes should not generate values on the VAT declaration, associate them with the **Other** lookup result.

#### Set up application-specific parameters for Details

1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Details lookup**.
2. On the **Conditions** FastTab, define which sales tax codes generate which lines on the VAT declaration (for lines 37–42, 45–62, 79, and 88–95, which are details of lines 01–35 and 63–75 that are defined in **Report field lookup**).
3. Create the last line, and associate all other sales tax codes with the **Other** lookup result.

<table>
<tbody>
<tr>
<td width="240">
<p><strong>Lookup result</strong></p>
</td>
<td width="240">
<p><strong>Tax code</strong></p>
</td>
<td width="240">
<p><strong>Transaction classifier</strong></p>
</td>
</tr>
<tr>
<td width="240">
<p>Other</p>
</td>
<td width="240">
<p>*Not blank*</p>
</td>
<td width="240">
<p>*Not blank*</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


#### Set up application-specific parameters for In-kind contributions, Assets, and Annex I

1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **In-kind** lookup.
2. On the **Conditions** FastTab, define which sales tax codes are for in-kind contributions and generate values on lines 44 and 78.
3. Create the last line, and associate all other sales tax codes with the **Other** lookup result as shown in the last step of the previous procedure.
4. On the **Lookups** FastTab, select **Assets lookup**.
5. On the **Conditions** FastTab, define which sales tax codes are for assets (property, plant, and equipment), sales, and purchases, and generate values on lines 43 and 77.
6. Create the last line, and associate all other sales tax codes with the **Other** lookup result as before.
7. On the **Lookups** FastTab, select **AnnexI lookup**.
8. On the **Conditions** FastTab, define which sales tax codes generate values in section 65A-01-05 (lines 100 and 101) of the VAT declaration.
9. Create the last line, and associate all other sales tax codes to the **Other** lookup result, as before.
10. On the **Lookups** FastTab, select **Summary report lookup**.
11. On the **Conditions** FastTab, define which invoice sales tax groups and sales tax codes should be included in the 65M summary report when they are used in vendor invoices. If all vendor invoices should be included on the Summary report, regardless of sales tax groups and sales tax codes, create the following lines.

<table>
<tbody>
<tr>
<td width="121">
<p><strong>Lookup result</strong></p>
</td>
<td width="132">
<p><strong>Tax code</strong></p>
</td>
<td width="132">
<p><strong>Tax group</strong></p>
</td>
</tr>
<tr>
<td width="121">
<p>Included</p>
</td>
<td width="132">
<p>*Not blank*</p>
</td>
<td width="132">
<p>*Not blank*</p>
</td>
</tr>
<tr>
<td width="121">
<p>Included</p>
</td>
<td width="132">
<p>*Not blank*</p>
</td>
<td width="132">
<p>*Blank*</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


#### Set up application-specific parameter for the XML file format version

1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **XML values lookup**.
2. On the **Conditions** FastTab, define values for some constant XML elements:

  - In the **Element** column, select **FormatVersion**.
  - In the **Lookup result** column, enter the value of the format version. For example, for the XML file 2265 applicable for the year 2022, enter **2.0**.

3. On the Action Pane, select **Export** to export the settings in an XML file. Then close the page.
4. Select the **VAT declaration Excel (HU)** configuration, and then select **Configurations** > **Application specific parameters setup**.
5. Select **Import**, and select the file that you exported earlier.

### Set up the VAT reporting format for preview amounts in Excel

1. In the **Feature management** workspace, find and select the **VAT statement format reports** feature in the list, and then select **Enable now**.
2. Go to **General ledger** > **Setup** > **General ledger parameters**.
3. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (HU)** ER format.

This format is printed when you run the **Report sales tax for settlement period** report. It's also printed when you select **Print** on the **Sales tax payments** page.

4. On the **Tax authorities** page, select the tax authority, and then, in the **Report layout** field, select **Default**.

If you're configuring the VAT declaration in a legal entity that has [multiple VAT registrations](emea-reporting-for-multiple-vat-registrations.md), follow these steps.

1. Go to **General ledger** > **Setup** > **General ledger parameters**.
2. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the line for **HUN**, select the **VAT Declaration Excel (HU)** ER format.

## Set up electronic messages

### Download and import the data package that has example settings for electronic messages

The data package contains electronic message settings that are used to preview the VAT declaration in Excel. You can extend these settings or create your own. For more information about how to work with electronic messaging and create your own settings, see [Electronic messaging](../general-ledger/electronic-messaging.md).

1. In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download **HU VAT declaration package**. The downloaded file is named **HU VAT declaration package.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In the **Add file** dialog box, verify that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier.
6. Select **Close**.
7. After the data entities are uploaded, on the Action Pane, select **Import**.
8. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**, and validate the electronic message processing that you imported **(HU VAT declaration)**.

### Configure electronic messages

1. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
2. Select the line for **HU Populate VAT return records**, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include on the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

## <a name="preview-vat"></a>Preview the VAT declaration, incoming transactions, and outgoing transactions in Excel

### Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task

1. Go to **Tax** > **Periodic tasks** > **Declarations** > **Sales tax** > **Report sales tax for settlement period**.
2. Set the following fields.

<table>
<tbody>
<tr>
<td>
<p><strong>Field</strong></p>
</td>
<td>
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td>
<p>Settlement period</p>
</td>
<td>
<p>Select the settlement period.</p>
</td>
</tr>
<tr>
<td>
<p>Sales tax payment version</p>
</td>
<td>
<p>Select one of the following values:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong> &ndash; Generate a report for the sales tax transactions of the original sales tax payment or before the sales tax payment is generated.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Corrections</strong> &ndash; Generate a report for the sales tax transactions of all the subsequent sales tax payments for the period.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Total list</strong> &ndash; Generate a report for all the sales tax transactions for the period, including the original and all corrections.</p>
</td>
</tr>
<tr>
<td>
<p>From date</p>
</td>
<td>
<p>Select the start date of the reporting period.</p>
</td>
</tr>
</tbody>
</table>


3. Select **OK**, and then, in the **Electronic report parameters** dialog box, set the following fields.

<table>
<tbody>
<tr>
<td>
<p><strong>Field</strong></p>
</td>
<td width="423">
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td>
<p>Tax base - Deductible amount moved from previous period</p>
<p>Tax amount - Deductible amount moved from previous period</p>
</td>
<td width="423">
<p>Enter the amounts that have been moved from the previous period. These amounts are shown on line 82.</p>
</td>
</tr>
<tr>
<td>
<p>Tax base - Receivable amount carried forward</p>
<p>Tax amount - Receivable amount carried forward</p>
</td>
<td width="423">
<p>Enter the amounts to move to the next period. These amounts are shown on line 86.</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


4. Select **OK**, and review the Excel report.

### <a name="settle"></a>Settle and post sales tax

1. Go to **Tax** > **Periodic tasks** > **Declarations** > **Sales tax** > **Settle and post sales tax**.
2. Set the following fields.

<table>
<tbody>
<tr>
<td>
<p><strong>Field</strong></p>
</td>
<td>
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td>
<p>Settlement period</p>
</td>
<td>
<p>Select the settlement period.</p>
</td>
</tr>
<tr>
<td>
<p>Sales tax payment version</p>
</td>
<td>
<p>Select one of the following values:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong> &ndash; Generate the original sales tax payment for the settlement period.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Latest corrections</strong> &ndash; Generate a correction sales tax payment after the original sales tax payment for the settlement period was created.</p>
</td>
</tr>
<tr>
<td>
<p>From date</p>
</td>
<td>
<p>Select the start date of the reporting period.</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


3. Select **OK**.

### Preview the VAT declaration in Excel from a sales tax payment

1. Go to **Tax** > **Inquiries and reports** > **Sales tax inquiries** > **Sales tax payments**, and select a sales tax payment line.
2. Select Print report, and then select **OK**.
3. Review the Excel file that is generated for the selected sales tax payment line.

> [!NOTE]
> 
> The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the **Report sales tax for settlement period** periodic task.

## Generate a VAT declaration from electronic messages

When you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run a VAT declaration for multiple legal entities](#run-a-vat) section later in this topic.

The following procedure applies to the electronic message processing example that you imported earlier from the LCS Shared asset library.

1. Go to **Tax** > **Inquiries and reports** >** Electronic messages** > **Electronic messages**.
2. In the left pane, select **HU VAT declaration**.
3. On the **Messages** FastTab, select **New**, and then, in the **Run processing** dialog box, select **OK**.
4. Select the message line that is created, enter a description, and then specify the start date and end date for the declaration.

> [!NOTE]
> 
> Steps 5 through 7 are optional.

5. Optional: On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier are added to the message. For more information, see the [Settle and post sales tax](#settle) section earlier in this topic. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration** version field in the **Declaration** dialog box.
6. Optional: On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
7. Optional: Select **Original document** to review the sales tax payments, or select **Delete** to exclude sales tax payments from processing. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
8. On the **Messages** FastTab, select **Update status**. In the **Update status** dialog box, select **Ready to generate**, and then select **OK**. Verify that the message status is changed to **Ready to generate**.
9. Select **Generate report**. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **Preview report**, and then select **OK**.
10. In the **Electronic reporting parameters** dialog box, set the fields as described in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#preview-vat) section earlier in this topic, and then select **OK**.
11. Select the **Attachments** button in the upper-right corner of the page, and then select **Open** to open the file. Review the amounts in the Excel documents.
12. Select **Generate report**.
13. To generate a report in XML format, in the **Run processing** dialog box, select **Generate report**, and then select **OK**.
14. Set the following fields.

<table>
<tbody>
<tr>
<td width="231">
<p><strong>Field</strong></p>
</td>
<td width="464">
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td width="231">
<p>Report periodicity</p>
</td>
<td width="464">
<p>Select <strong>Monthly</strong>, <strong>Quarterly</strong>, or <strong>Yearly</strong>.</p>
</td>
</tr>
<tr>
<td width="231">
<p>Tax representative</p>
</td>
<td width="464">
<p>Select a tax representative, if applicable.</p>
</td>
</tr>
<tr>
<td width="231">
<p>Contact person</p>
</td>
<td width="464">
<p>Select the employee who is a contact for the declaration.</p>
</td>
</tr>
<tr>
<td width="231">
<p>Signatory person</p>
</td>
<td width="464">
<p>Select the employee who signs the declaration.</p>
</td>
</tr>
<tr>
<td width="231">
<p>Power of attorney</p>
</td>
<td width="464">
<p>If you selected a tax representative, select the type of power of attorney: <strong>Add-hoc</strong> or <strong>Permanent</strong>.</p>
</td>
</tr>
<tr>
<td width="231">
<p>Threshold exceeded</p>
</td>
<td width="464">
<p>Select <strong>Yes</strong> if you exceeded the threshold.</p>
</td>
</tr>
<tr>
<td width="231">
<p>Tax base - Deductible amount moved from previous period</p>
<p>Tax amount - Deductible amount moved from previous period</p>
</td>
<td width="464">
<p>Enter the amounts that have been moved from the previous period. These amounts are shown on line 82.</p>
</td>
</tr>
<tr>
<td width="231">
<p>Tax base - Receivable amount carried forward</p>
<p>Tax amount - Receivable amount carried forward</p>
</td>
<td width="464">
<p>Enter the amounts to move to the next period. These amounts are shown on line 86.</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


15. Select the **Attachments** button in the upper-right corner of the page, and download the electronic file that was generated. You should then manually upload this file to the tax authority tool or portal.

## <a name="run-a-vat"></a>Run a VAT declaration for multiple legal entities

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from several legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** > **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
4. On the **Populate records action** page, select the line for **HU Populate VAT return records**.

   In the **Datasources setup** grid, a new **Company** field is available. For existing records, this field shows the identifier of the current legal entity.

5. In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting. For each new line, set the following fields.

<table>
<tbody>
<tr>
<td>
<p><strong>Field</strong></p>
</td>
<td>
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td>
<p>Name</p>
</td>
<td>
<p>Enter a value that will help you understand where this record comes from. For example, enter <strong>VAT payment of Subsidiary 1</strong>.</p>
</td>
</tr>
<tr>
<td>
<p>Message item type</p>
</td>
<td>
<p>Select <strong>VAT return</strong>. This value is the only value that is available for all the records.</p>
</td>
</tr>
<tr>
<td>
<p>Account type</p>
</td>
<td>
<p>Select <strong>All</strong>.</p>
</td>
</tr>
<tr>
<td>
<p>Master table name</p>
</td>
<td>
<p>Specify <strong>TaxReportVoucher</strong> for all the records.</p>
</td>
</tr>
<tr>
<td>
<p>Document number field</p>
</td>
<td>
<p>Specify <strong>Voucher</strong> for all the records.</p>
</td>
</tr>
<tr>
<td>
<p>Document date field</p>
</td>
<td>
<p>Specify <strong>TransDate</strong> for all the records.</p>
</td>
</tr>
<tr>
<td>
<p>Document account field</p>
</td>
<td>
<p>Specify <strong>TaxPeriod</strong> for all the records.</p>
</td>
</tr>
<tr>
<td>
<p>Company</p>
</td>
<td>
<p>Select the ID of the legal entity.</p>
</td>
</tr>
<tr>
<td>
<p>User query</p>
</td>
<td>
<p>This checkbox is automatically selected when you define criteria by selecting <strong>Edit query</strong>.</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>


6. For each new line, select **Edit query**, and specify a related settlement period for the legal entity that is specified in the **Company** field on the line.

  When the setup is completed, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all the legal entities that you defined.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
