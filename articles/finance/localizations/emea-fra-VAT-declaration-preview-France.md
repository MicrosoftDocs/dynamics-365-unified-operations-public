---
# required metadata

title: VAT declaration (France)
description: This topic describes how to set up and generate a report for France that can be used to report a value-added tax (VAT) declaration.
author: anasyash
ms.date: 09/14/2021
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
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: AX 10.0.21

---

# VAT declaration (France)

[!include [banner](../includes/banner.md)]


## Overview

This topic describes how to set up and generate a report for France that can be used to report a value-added tax (VAT) declaration in the [www.impots.gouv.fr](http://www.impots.gouv.fr) online portal by using the exchange of computerized forms (EFI) channel.

To automatically generate the report, you must first create enough sales tax codes to keep a separate VAT accounting for each box on the VAT declaration. Additionally, in the application-specific parameters of the Electronic reporting (ER) format for the VAT declaration, you must associate sales tax codes with the result of the lookups for the VAT declaration boxes.

For France, you must configure three lookups:

   - Operation lookup
   - Report field lookup
   - Monaco lookup

For more information about how to set up application-specific parameters, see the [Set up application-specific parameters for VAT declaration fields](#set-up-application-specific-parameters-for-vat-declaration-fields) section later in this topic.

In the following tables, the **Lookup result** column shows the lookup result that is preconfigured for a specific VAT declaration row in the VAT declaration format. Use this information to correctly associate sales tax codes with the lookup result and then with the row of the VAT declaration.

### <a name="vat-declaration-preview-overview"> VAT declaration preview overview </a>

The VAT declaration preview in France contains the following information.

**SECTION A - AMOUNT OF OPERATIONS CARRIED OUT**

<table width="100%">
<tbody>
<tr>
<td width="41">
<p><strong>Line</strong></p>
</td>
<td width="49">
<p><strong>Box</strong></p>
</td>
<td width="265">
<p><strong>Description</strong></p>
</td>
<td width="80">
<p><strong>Lookup</strong></p>
</td>
<td width="188">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td colspan="3" width="356">
<p><strong>TAXABLE OPERATIONS</strong></p>
</td>
<td width="80">
<p><strong>&nbsp;</strong></p>
</td>
<td width="188">
<p><strong>&nbsp;</strong></p>
</td>
</tr>
<tr>
<td width="41">
<p>01</p>
</td>
<td width="49">
<p>0979</p>
</td>
<td width="265">
<p>Sales and services</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>TaxableSalesServices</p>
</td>
</tr>
<tr>
<td width="41">
<p>02</p>
</td>
<td width="49">
<p>0981</p>
</td>
<td width="265">
<p>Other taxable transactions</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>OtherTaxableTransactions</p>
</td>
</tr>
<tr>
<td width="41">
<p>2A</p>
</td>
<td width="49">
<p>0044</p>
</td>
<td width="265">
<p>Intra-community purchases of services</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>EUPurchaseServices</p>
</td>
</tr>
<tr>
<td width="41">
<p>2B</p>
</td>
<td width="49">
<p>0045</p>
</td>
<td width="265">
<p>Imports (companies that have chosen the reverse charge mechanism for import VAT)</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>Imports (Line 7C is also affected.)</p>
<p>ImportsUseTax (Lines 7C and 24 are also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>03</p>
</td>
<td width="49">
<p>0031</p>
</td>
<td width="265">
<p>Intra-community acquisitions</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>EUPurchase (Line 17 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>3A</p>
</td>
<td width="49">
<p>0030</p>
</td>
<td width="265">
<p>Deliveries of electricity, natural gas, heat, or cold that are taxable in France (domestic reverse charge)</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>TaxableElectricityGasHeatCold</p>
</td>
</tr>
<tr>
<td width="41">
<p>3B</p>
</td>
<td width="49">
<p>0040</p>
</td>
<td width="265">
<p>Purchases of goods or services from a taxable person who isn't established in France</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>PurchasesFromPersonNotEstablished</p>
</td>
</tr>
<tr>
<td width="41">
<p>3C</p>
</td>
<td width="49">
<p>0036</p>
</td>
<td width="265">
<p>Regularizations</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>TaxableRegularizations</p>
</td>
</tr>
<tr>
<td colspan="3" width="356">
<p><strong>NON-TAXABLE OPERATIONS</strong></p>
</td>
<td width="80">
<p>&nbsp;</p>
</td>
<td width="188">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="41">
<p>04</p>
</td>
<td width="49">
<p>0032</p>
</td>
<td width="265">
<p>Exports outside the European Union (EU)</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>ExportsOutsideEU</p>
</td>
</tr>
<tr>
<td width="41">
<p>05</p>
</td>
<td width="49">
<p>0033</p>
</td>
<td width="265">
<p>Other non-taxable transactions</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>OtherNonTaxableTransactions</p>
</td>
</tr>
<tr>
<td width="41">
<p>5A</p>
</td>
<td width="49">
<p>0047</p>
</td>
<td width="265">
<p>Distance sales that are taxable in another member state for the benefit of non-taxable persons (business-to-consumer [B2C] sales)</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>EUDistanceB2CSales</p>
</td>
</tr>
<tr>
<td width="41">
<p>06</p>
</td>
<td width="49">
<p>0034</p>
</td>
<td width="265">
<p>Intra-community deliveries to a taxable person (business-to-business [B2B] sales)</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>EUSales</p>
</td>
</tr>
<tr>
<td width="41">
<p>6A</p>
</td>
<td width="49">
<p>0029</p>
</td>
<td width="265">
<p>Deliveries of electricity, natural gas, heat, or cold that aren't taxable in France</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>ElectricityGasHeatColdNotTaxable</p>
</td>
</tr>
<tr>
<td width="41">
<p>07</p>
</td>
<td width="49">
<p>0037</p>
</td>
<td width="265">
<p>Tax-free purchases</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>TaxFreePurchases</p>
</td>
</tr>
<tr>
<td width="41">
<p>7A</p>
</td>
<td width="49">
<p>0043</p>
</td>
<td width="265">
<p>Sales of goods or services by a taxable person who isn't established in France</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>SalesByPersonNotEstablished</p>
</td>
</tr>
<tr>
<td width="41">
<p>7B</p>
</td>
<td width="49">
<p>0039</p>
</td>
<td width="265">
<p>Regularizations</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>NotTaxableRegularizations</p>
</td>
</tr>
</tbody>
</table>                                                              |

**SECTION B - VAT CALCULATION TO BE PAID**

**GROSS VAT**

<table width="100%">
<tbody>
<tr>
<td width="41">
<p><strong>Line</strong></p>
</td>
<td width="49">
<p><strong>Box</strong></p>
</td>
<td width="265">
<p><strong>Description</strong></p>
</td>
<td width="80">
<p><strong>Lookup</strong></p>
</td>
<td width="188">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td colspan="3" width="356">
<p><strong>Operations carried out inFrance</strong></p>
</td>
<td width="80">
<p>&nbsp;</p>
</td>
<td width="188">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="41">
<p>08</p>
</td>
<td width="49">
<p>0207</p>
</td>
<td width="265">
<p>Standard rate of 20 percent</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueFranceStandard</p>
<p>UseTaxFranceStandard (Line 20 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>8A</p>
</td>
<td width="49">
<p>0208</p>
</td>
<td width="265">
<p>Standard rate of 20 percent on petroleum products</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueFrancePetroleumStandard</p>
<p>UseTaxFrancePetroleumStandard (Lines 20 and 2E are also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>09</p>
</td>
<td width="49">
<p>0105</p>
</td>
<td width="265">
<p>Reduced rate of 5.5 percent</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueFranceReduced</p>
<p>UseTaxFranceReduced (Line 20 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>9B</p>
</td>
<td width="49">
<p>0151</p>
</td>
<td width="265">
<p>Reduced rate of 10 percent</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueFranceReduced2</p>
<p>UseTaxFranceReduced2 (Line 20 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>9C</p>
</td>
<td width="49">
<p>0152</p>
</td>
<td width="265">
<p>Reduced rate of 13 percent on petroleum products</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueFrancePetroleumReduced</p>
<p>UseTaxFrancePetroleumReduced (Lines 20 and 2E are also affected.)</p>
</td>
</tr>
<tr>
<td colspan="3" width="356">
<p><strong>Operations carried out in the overseas departments</strong></p>
</td>
<td width="80">
<p>&nbsp;</p>
</td>
<td width="188">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="41">
<p>10</p>
</td>
<td width="49">
<p>0201</p>
</td>
<td width="265">
<p>Standard rate of 8.5 percent</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueOverseasStandard</p>
<p>UseTaxOverseasStandard (Line 20 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>11</p>
</td>
<td width="49">
<p>0100</p>
</td>
<td width="265">
<p>Reduced rate of 2.1 percent</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueOverseasReduced</p>
<p>UseTaxOverseasReduced (Line 20 is also affected.)</p>
</td>
</tr>
<tr>
<td colspan="3" width="356">
<p><strong>Transactions taxable at another rate (France or overseas departments)</strong></p>
</td>
<td width="80">
<p>&nbsp;</p>
</td>
<td width="188">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="41">
<p>13</p>
</td>
<td width="49">
<p>0900</p>
</td>
<td width="265">
<p>Old rates</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueOldRates</p>
<p>UseTaxOldRates (Line 20 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>14</p>
</td>
<td width="49">
<p>0950</p>
</td>
<td width="265">
<p>Transactions that are taxable at a specific rate (The statement is made on note 3310 A.)</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDueSpecificRate</p>
<p>UseTaxSpecificRate (Line 20 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>15</p>
</td>
<td width="49">
<p>0600</p>
</td>
<td width="265">
<p>Previously deducted VAT that must be returned</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATDeductedToBeReturned</p>
<p>VATDeductedToBeReturnedRegularizations</p>
</td>
</tr>
<tr>
<td width="41">
<p>5B</p>
</td>
<td width="49">
<p>0602</p>
</td>
<td width="265">
<p>Amounts that must be added, including holiday deposits (expressed in euros)</p>
</td>
<td width="80">
<p>Report field lookup</p>
</td>
<td width="188">
<p>VATCorrectionAmountToBeAdded</p>
</td>
</tr>
<tr>
<td width="41">
<p>16</p>
</td>
<td width="49">
<p>&nbsp;</p>
</td>
<td width="265">
<p>Total gross VAT due (lines 08 through 5B)</p>
</td>
<td width="80">
<p>&nbsp;</p>
</td>
<td width="188">
<p>08 + 8A + 09 + 9B + 9C + 10 + 11 + 13 + 14 + 15 + 5B</p>
</td>
</tr>
<tr>
<td width="41">
<p>7C</p>
</td>
<td width="49">
<p>0046</p>
</td>
<td width="265">
<p>Including VAT on imports that benefit from the reverse charge scheme</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>Imports (Line 2B is also affected.)</p>
<p>ImportsUseTax (Lines 2B and 24 are also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>17</p>
</td>
<td width="49">
<p>0035</p>
</td>
<td width="265">
<p>Including VAT on intra-community acquisitions</p>
</td>
<td width="80">
<p>Operation lookup</p>
</td>
<td width="188">
<p>EUPurchase (Line 03 is also affected.)</p>
</td>
</tr>
<tr>
<td width="41">
<p>18</p>
</td>
<td width="49">
<p>0038</p>
</td>
<td width="265">
<p>Including VAT on transactions to Monaco</p>
</td>
<td width="80">
<p>Monaco lookup</p>
</td>
<td width="188">
<p>Monaco</p>
</td>
</tr>
</tbody>
</table>

**DEDUCTIBLE VAT**

<table width="100%">
<tbody>
<tr>
<td width="6%">
<p><strong>Line</strong></p>
</td>
<td width="7%">
<p><strong>Box</strong></p>
</td>
<td width="27%">
<p><strong>Description</strong></p>
</td>
<td width="12%">
<p><strong>Lookup</strong></p>
</td>
<td width="45%">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="6%">
<p>19</p>
</td>
<td width="7%">
<p>0703</p>
</td>
<td width="27%">
<p>Property that constitutes capital assets</p>
</td>
<td width="12%">
<p>Report field lookup</p>
</td>
<td width="45%">
<p>VATDeductionPropertyCapitalAssets</p>
</td>
</tr>
<tr>
<td width="6%">
<p>20</p>
</td>
<td width="7%">
<p>0702</p>
</td>
<td width="27%">
<p>Other goods and services</p>
</td>
<td width="12%">
<p>Report field lookup</p>
</td>
<td width="45%">
<p>VATDeductionOtherGoodsServices</p>
<p>VATDeductionOtherGoodsServicesImports (Line 24 is also affected.)</p>
<p>VATDeductionOtherGoodsServicesPetroleum (Line 2E is also affected.)</p>
<p>VATDeductionOtherGoodsServicesImportPetroleum (Lines 24 and 2E are also affected.)</p>
<p>UseTaxFranceStandard (Line 08 is also affected.)</p>
<p>UseTaxFrancePetroleumStandard (Lines 8A and 2E are also affected.)</p>
<p>UseTaxFranceReduced (Line 09 is also affected.)</p>
<p>UseTaxFranceReduced2 (Line 9B is also affected.)</p>
<p>UseTaxFrancePetroleumReduced (Lines 9C and 2E are also affected.)</p>
<p>UseTaxOverseasStandard (Line 10 is also affected.)</p>
<p>UseTaxOverseasReduced (Line 11 is also affected.)</p>
<p>UseTaxOldRates (Line 13 is also affected.)</p>
<p>UseTaxSpecificRate (Line 14 is also affected.)</p>
</td>
</tr>
<tr>
<td width="6%">
<p>21</p>
</td>
<td width="7%">
<p>0059</p>
</td>
<td width="27%">
<p>Other VAT that must be deducted</p>
</td>
<td width="12%">
<p>Report field lookup</p>
</td>
<td width="45%">
<p>VATDeductionTaxableRegularizations</p>
</td>
</tr>
<tr>
<td width="6%">
<p>22</p>
</td>
<td width="7%">
<p>8001</p>
</td>
<td width="27%">
<p>Credit that was carried forward and that appeared on line 27 of the previous statement</p>
</td>
<td width="12%">
<p><em>&nbsp;</em></p>
</td>
<td width="45%">
<p>The user defines the value in a dialog box.</p>
</td>
</tr>
<tr>
<td width="6%">
<p>2C</p>
</td>
<td width="7%">
<p>0603</p>
</td>
<td width="27%">
<p>Amounts that must be charged, including holiday deposits (expressed in euros)</p>
</td>
<td width="12%">
<p>Report field lookup</p>
</td>
<td width="45%">
<p>VATDeductionAmountsToBeCharged</p>
</td>
</tr>
<tr>
<td width="6%">
<p>22A</p>
</td>
<td width="7%">
<p>&nbsp;</p>
</td>
<td width="27%">
<p>The single tax coefficient that is applicable for the period, if it differs</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>The user defines the value in a dialog box.</p>
</td>
</tr>
<tr>
<td width="6%">
<p>23</p>
</td>
<td width="7%">
<p>&nbsp;</p>
</td>
<td width="27%">
<p>Total deductible VAT (lines 19 through 2C)</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>Total 19 + 20 + 21 + 22 + 2C</p>
</td>
</tr>
<tr>
<td width="6%">
<p>24</p>
</td>
<td width="7%">
<p>0710</p>
</td>
<td width="27%">
<p>Of which deductible VAT on imports</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>VATDeductionOtherGoodsServicesImports (Line 20 is also affected.)</p>
<p>VATDeductionOtherGoodsServicesImportPetroleum (Lines 20 and 2E are also affected.)</p>
<p>ImportsUseTax (Lines 2B and 7C are also affected.)</p>
</td>
</tr>
<tr>
<td width="6%">
<p>2E</p>
</td>
<td width="7%">
<p>0711</p>
</td>
<td width="27%">
<p>Of which deductible VAT on petroleum products</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>VATDeductionOtherGoodsServicesImportPetroleum (Lines 20 and 24 are also affected.)</p>
<p>UseTaxFrancePetroleumReduced (Lines 9C and 20 are also affected.)</p>
<p>VATDeductionOtherGoodsServicesPetroleum (Line 20 is also affected.)</p>
<p>UseTaxFrancePetroleumReduced (Lines 9C and 20 are also affected.)</p>
<p>UseTaxFrancePetroleumStandard (Lines 8A and 20 are also affected.)</p>
</td>
</tr>
</tbody>
</table>                                                                                                                                                                        

**CREDIT / TAX PAYABLE**

<table width="100%">
<tbody>
<tr>
<td width="6%">
<p><strong>Line</strong></p>
</td>
<td width="7%">
<p><strong>Box</strong></p>
</td>
<td width="27%">
<p><strong>Description</strong></p>
</td>
<td width="12%">
<p><strong>Lookup</strong></p>
</td>
<td width="45%">
<p><strong>Lookup result</strong></p>
</td>
</tr>
<tr>
<td width="6%">
<p>25</p>
</td>
<td width="7%">
<p>0705</p>
</td>
<td width="27%">
<p>VAT credit (line 23 &ndash; line 16)</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>Total 23 &ndash; 16</p>
</td>
</tr>
<tr>
<td width="6%">
<p>26</p>
</td>
<td width="7%">
<p>8002</p>
</td>
<td width="27%">
<p>Credit repayment that is requested</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>The user defines the value in a dialog box.</p>
</td>
</tr>
<tr>
<td width="6%">
<p>AA</p>
</td>
<td width="7%">
<p>8005</p>
</td>
<td width="27%">
<p>VAT credit that is transferred to the head company of the group</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>The user defines the value in a dialog box.</p>
</td>
</tr>
<tr>
<td width="6%">
<p>27</p>
</td>
<td width="7%">
<p>8003</p>
</td>
<td width="27%">
<p>Credit to carry forward (line 25 &ndash; line 26 &ndash; line AA)</p>
<p>This amount should be carried over to line 22 of the next return.</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>Total 25 &ndash; 26 &ndash; AA</p>
</td>
</tr>
<tr>
<td width="6%">
<p>28</p>
</td>
<td width="7%">
<p>&nbsp;</p>
</td>
<td width="27%">
<p>Total net VAT payable (line 16 &ndash; line 23)</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>Total 16 &ndash; 23</p>
</td>
</tr>
<tr>
<td width="6%">
<p>29</p>
</td>
<td width="7%">
<p>9979</p>
</td>
<td width="27%">
<p>Assimilated taxes</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>The user defines a value in a dialog box.</p>
</td>
</tr>
<tr>
<td width="6%">
<p>AB</p>
</td>
<td width="7%">
<p>9991</p>
</td>
<td width="27%">
<p>Total payable that is paid by the head company of the group on the summary declaration</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>The user defines a value in a dialog box.</p>
</td>
</tr>
<tr>
<td width="6%">
<p>32</p>
</td>
<td width="7%">
<p>&nbsp;</p>
</td>
<td width="27%">
<p>Total payable (line 28 + line 29 &ndash; line AB)</p>
</td>
<td width="12%">
<p>&nbsp;</p>
</td>
<td width="45%">
<p>Total 28 + 29 &ndash; AB</p>
</td>
</tr>
</tbody>
</table>

### Note about purchase reverse charge VAT

If you configure sales tax codes to post incoming reverse charge VAT by using use tax, associate your sales tax codes with the lookup result of the **Report field** lookup that contains "UseTax" in the name.

Alternatively, you can configure two separate sales tax codes: one for VAT due and one for VAT deduction. Then associate each code with the appropriate lookup report of the **Report field** lookup.

**Example**

For a taxable purchase of electricity, gas, heat, or cold that has a domestic reverse charge, you configure sales tax code **UT_S_RC** with use tax. You then associate the code with the **UseTaxTaxableElectricityGasHeatCold** lookup result of the **Operation** lookup and the **UseTaxFranceStandard** lookup result of the **Report field** lookup. In this case, amounts that use the **UT_S_RC** sales tax code will be reflected on line 3A (via the **Operation** lookup), and on lines 08 and 20 (using the **Report field** lookup).

Alternatively, you configure two sales tax codes:

   - **VAT_S_RC**, which has a tax rate value of -20 percent
   - **InVAT_S_RC**, which has a tax rate value of 20 percent

You then associate the codes with lookup results in the following way:

   - Associate **VAT_S_RC** with the **TaxableElectricityGasHeatCold** lookup result of the **Operation** lookup and the **VATDueFranceStandard** lookup result of the **Report field** lookup.
   - Associate **InVAT_S_RC** with the **VATDeductionOtherGoodsServices** lookup result of the **Report field** lookup.

In this case, amounts that use the **VAT_S_RC** sales tax code will be reflected on lines 3A (via the **Operation** lookup) and 08 (via the **Report field** lookup). Amounts that use the **InVAT_S_RC** sales tax code will be reflected on line 20 (via the **Report field** lookup).

For more information about how to configure reverse charge VAT, see [Reverse charges](emea-reverse-charge.md).

## Set up a VAT declaration preview for France

### Import ER configurations

1. Open the **Electronic reporting** workspace.
2. Import the following version or later of this ER format:

    - VAT Declaration Excel (FR) version 85.15

### <a name="set-up-application-specific-parameters-for-vat-declaration-fields">Set up application-specific parameters for VAT declaration fields</a>

To automatically generate a VAT declaration preview report in Microsoft Excel, associate sales tax codes in the application and lookup results in the ER configuration.

#### Set up operations

Follow these steps to define which sales tax codes generate which boxes in section A, "AMOUNT OF OPERATIONS CARRIED OUT."

1. Go to **Workspaces** > **Electronic reporting**, and select **Reporting configurations**.
2. Select the **VAT declaration Excel (FR)** configuration, and then select **Configurations** > **Application specific parameters setup** to open the **Application specific parameters** page.
3. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Operation lookup**.
4. On the **Conditions** FastTab, set the following fields to associate the sales tax codes and operations.

   | Field                  | Description                                                                                                                                                                                                                                                                                                       |
   |------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | Lookup result          | Select the operation to set up. For more information about the operations and their assignment to VAT declaration rows, see the [VAT declaration preview overview](#vat-declaration-preview-overview) section earlier in this topic.                                                                              |
   | Tax code               | Select the sales tax code to associate with the operation. Posted tax transactions that use the selected sales tax code will be collected in the appropriate declaration box. We recommend that you separate sales tax codes in such a way that one sales tax code generates amounts in only one declaration box. |
   | Transaction classifier | If you created enough sales tax codes to determine a declaration box, select **\*Not blank\***. If you didn't create enough sales tax codes so that one sales tax code generates amounts in only one declaration box, set up a transaction classifier. The following transaction classifiers are available: <br>- **Purchase** <br>- **PurchaseExempt** (tax-exempt purchase)<br> - **PurchaseReverseCharge** (tax receivable from a purchase reverse charge)<br> - **Sales**<br> - **SalesExempt** (tax-exempt sale)<br> - **SalesReverseCharge** (tax payable from a purchase reverse charge or a sales reverse charge)<br> - **Use tax**<br> For each transaction classifier, a classifier for the credit note is also available. For example, one of these classifiers is **PurchaseCreditNote** (purchase credit note).      |

   > [!NOTE]
   > Be sure to associate all sales tax codes with lookup results. If any sales tax codes should not generate values in section A, associate them with the **Other** lookup result.
   > 
   > ![Application parameters operations](media/5121ad123182da7ffea8892f687fef34.png)

#### Set up report fields

Follow these steps to define which sales tax codes generate which boxes in section B, "VAT CALCULATION TO BE PAID."

1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Report field lookup**.
2. On the **Conditions** FastTab, associate the sales tax codes and report fields.

    > [!NOTE] 
    > Be sure to associate all sales tax codes with lookup results. If any sales tax codes should not generate values in section B, associate them with the **Other** lookup result.

    ![Application_parameters_report_fields](media/54cd612e95ccd127c4de57c9281661e0.png)

#### Set up sales tax codes for Monaco

Follow these steps to define which sales tax codes generate the amount in box 18, **Including VAT on transactions to Monaco**.

1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **Monaco lookup**.
2. On the **Conditions** FastTab, associate the sales tax codes and the **Monaco** lookup result.

    > [!NOTE]
    >  As the last line in the setup, create a line where you associate the **Not blank** value of the **Tax code** field with the **France** lookup result. This line indicates that all other sales tax codes are related to operations in France and should not generate the amount in box 18.

    ![Application parameter Monaco](media/19d301e4a786455234417faca00fe0ea.png)

### Set up the VAT reporting format

1. In the **Feature management** workspace, enable the **VAT statement format reports** feature.
2. Go to **General ledger** > **Setup** > **General ledger parameters**.
3. On the **Sales tax** tab, on the **Tax options** FastTab, in the **VAT statement format mapping** field, select the **VAT declaration Excel (FR)** ER format.

    This format will be printed when you run the **Report sales tax for settlement period** report. It will also be printed when you select **Print** on the **Sales tax payments** page.

4. Go to **Tax** > **Sales tax** > **Sales tax authorities**. On the **Tax authorities** page, select the tax authority, and then, in the **Report layout** field, select **Default**.If you configured a VAT declaration in a legal entity that has [multiple VAT registrations](emea-reporting-for-multiple-vat-registrations.md), go to **General ledger** > **Setup** > **General ledger parameters**. On the **Sales tax** tab, on the **Electronic reporting for countries/regions** FastTab, on the **FRA country/region** line, select the **VAT Declaration Excel (FR)** ER format.

## Preview the VAT declaration in Excel

### <a name="preview-the-vat-declaration-in-excel-from-the-report-sales-tax-for-settlement-period-periodic-task"> Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task</a>

1. Go to **Tax** > **Periodic tasks** > **Declarations** > **Sales tax** > **Report sales tax for settlement period**.
2. Set the following fields.

    | Field                     | Description                                    |
    |---------------------------|------------------------------------------------|
    | Settlement period         | Select the settlement period.                  |
    | Sales tax payment version | Select one of the following values:            |
    | From date                 | Select the start date of the reporting period. |

    - **Original**: Generate a report for sales tax transactions of the original sales tax payment or before the sales tax payment is generated
    - **Corrections**: Generate a report for sales tax transactions of all the subsequent sales tax payments for the period
    - **Total list**: Generate a report for all sales tax transactions for the period, including the original and all corrections.
3. Select **OK**.
4. In the **Electronic report parameters** dialog box, set the following fields.

    | Field                                                                          | Description                                                     |
    |--------------------------------------------------------------------------------|-----------------------------------------------------------------|
    | Credit carried forward from the previous statement                             | Enter the amount to export in line 22 (box 8001) of the report. |
    | Single tax coefficient                                                         | Enter the coefficient to export in line 22A of the report.      |
    | Credit repayment requested                                                     | Enter the amount to export in line 26 (box 8002) of the report. |
    | VAT credit transferred to the group head company on the summary declaration    | Enter the amount to export in line AA (box 8005) of the report. |
    | Assimilated taxes                                                              | Enter the amount to export in line 29 (box 9979) of the report. |
    | Total payable paid by the company head of the group on the summary declaration | Enter the amount to export in line AB (box 9991) of the report. |

5. Select **OK**, and review Excel report.

### <a name="settle-and-post-sales-tax">Settle and post sales tax</a>

1. Go to **Tax** > **Periodic tasks** > **Declarations** > **Sales tax** > **Settle and post sales tax**.
2. Set the following fields.

    | Field                     | Description                                    |
    |---------------------------|------------------------------------------------|
    | Settlement period         | Select the settlement period.                  |
    | Sales tax payment version | Select one of the following values:            |
    | From date                 | Select the start date of the reporting period. |

    - **Original**: Generate the original sales tax payment for the settlement period.
    - **Latest corrections** – Generate a correction sales tax payment after the original sales tax payment for the settlement period was created.

3. Select **OK**.

### Preview the VAT declaration in Excel from the Sales tax payments inquiry

1. Go to **Tax** > **Inquiries and reports** > **Sales tax inquiries** > **Sales tax payments**, and select a sales tax payment line.
2. Select **Print report**.
3. In the **Electronic report parameters** dialog box, set the fields as explained in the [Preview the VAT declaration in Excel from the Report sales tax for settlement period periodic task](#preview-the-vat-declaration-in-excel-from-the-report-sales-tax-for-settlement-period-periodic-task) section earlier in this topic. Then review the Excel file that is generated for the selected sales tax payment line.

> [!NOTE] 
> The report is generated only for the selected line of the sales tax payment. If you must generate, for example, a corrective declaration that contains all corrections for the period, or a replacement declaration that contains original data and all corrections, use the **Report sales tax for settlement period** periodic task.

## Preview the VAT declaration from electronic messages

If you use electronic messages to generate the report, you can collect tax data from multiple legal entities. For more information, see the [Run a VAT
declaration for multiple legal entities](#run-a-vat-declaration-for-multiple-legal-entities) section later in this topic.

### Set up electronic messages

#### Download and import example settings for electronic messages

The data package that includes example settings contains electronic message settings that are used to generate the Excel report for France. You can extend these settings or create your own. For more information about how to work with electronic messaging and create your own settings, see [Electronic messaging](../general-ledger/electronic-messaging.md).

1. In [LCS](https://lcs.dynamics.com/v2), in the Shared asset library, select **Data package** as the asset type, and then download the **FR VAT declaration** package. The downloaded file is named **FR VAT declaration package.zip**.
2. In Finance, in the **Data management** workspace, select **Import**.
3. On the **Import** FastTab, in the **Group name** field, enter a name for the job.
4. On the **Selected entities** FastTab, select **Add file**.
5. In **Add file** dialog box, make sure that the **Source data format** field is set to **Package**, select **Upload and add**, and then select the zip file that you downloaded earlier. Select **Close**.
6. After the data entities are uploaded, on the Action Pane select **Import**.
7. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**, and review the electronic message processing that you imported (**FR VAT declaration**).

#### Configure electronic messages

1. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
2. Select the **FR Populate VAT return records** line, and then select **Edit query**.
3. Use the filter to specify the settlement periods to include in the report.
4. If you must report tax transactions from other settlement periods in a different declaration, create a new **Populate records** action, and select the appropriate settlement periods.

### Generate a VAT declaration preview from electronic messages

The following procedure applies to the example electronic message processing that you imported earlier from the LCS Shared asset library.

1. Go to **Tax** > **Inquiries and reports** > **Electronic messages** > **Electronic messages**.
2. In the left pane, select the report format to generate. For example, select **FR VAT declaration**.
3. On the **Messages** FastTab, select **New**, and then, in the **Run processing** dialog box, select **OK**.
4. Select the message line that is created, enter a description, and then specify the start and end dates for the declaration.

    > [!NOTE]
    > Steps 5 through 7 are optional.

5. Optional: On the **Messages** FastTab, select **Collect data**, and then select **OK**. The sales tax payments that were generated earlier are added to the message. For more information, see the [Settle and post sales tax](#settle-and-post-sales-tax) section earlier in this topic. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
6. Optional: On the **Message items** FastTab, review the sales tax payments that are transferred for processing. By default, all sales tax payments of the selected period that weren't included in any other message of the same processing are included.
7. Optional: Select **Original document** to review the sales tax payments, or select **Delete** to exclude sales tax payments from processing. If you skip this step, you can still generate a VAT declaration by using the **Tax declaration version** field in the **Declaration** dialog box.
8. On the **Messages** FastTab, select **Update status**. In the **Update status** dialog box, select the **Ready to generate** action, and then select **OK**. Verify that the message status is changed to **Ready to generate**.
9. Select **Generate report**. To preview the VAT declaration amounts, in the **Run processing** dialog box, select **Preview report**, and then select **OK**.
10. In the **Electronic reporting parameters** dialog box, set the following fields, and then select **OK**.

    | **Field**                                                                                                                                                                                                                                                                         | **Description**                                                                                                                                                                                                            |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Settlement period                                                                                                                                                                                                                                                                 | Select the settlement period. If you selected **Collect data** in step 5, you can disregard this field. The report will be generated for the sales tax transactions that are included in the collected sales tax payments. |
    | Tax declaration version                                                                                                                                                                                                                                                           | Select one of the following values:                                                                                                                                                                                        |
    | Credit carried forward from the previous statement Single tax coefficient Credit repayment requested VAT credit transferred to the group head company on the summary declaration Assimilated taxes Total payable paid by the company head of the group on the summary declaration | Set these fields as explained in the [Preview the VAT declaration in Excel](#preview-the-vat-declaration-in-excel-from-the-report-sales-tax-for-settlement-period-periodic-task) section earlier in this topic.            |

    - **Original**: Generate a report for sales tax transactions of the original sales tax payment or before the sales tax payment is generated.
    - **Corrections** – Generate a report for sales tax transactions of all the subsequent sales tax payments for the period.
    - **Total list** – Generate a report for all sales tax transactions for the period, including the original and all corrections.

    If you selected **Collect data** in step 5, you can disregard this field. The report will be generated for the sales tax transactions that are included in the collected sales tax payments.

11. Select the **Attachments** button (paper clip symbol) in the upper-right corner of the page, and then select **Open** to open the file. Review the amounts in the Excel document.

## <a name="run-a-vat-declaration-for-multiple-legal-entities">Run a VAT declaration for multiple legal entities</a>

To use the formats to report the VAT declaration for a group of legal entities, you must first set up the application-specific parameters of the ER formats for sales tax codes from all required legal entities.

### Set up electronic messages to collect tax data from multiple legal entities

Follow these steps to set up electronic messages to collect data from multiple legal entities.

1. Go to **Workspaces** > **Feature management**.
2. Find and select the **Cross-company queries for the populate records actions** feature in the list, and then select **Enable now**.
3. Go to **Tax** > **Setup** > **Electronic messages** > **Populate records actions**.
4. On the **Populate records action** page, select the **FR Populate VAT return records** line.

    In the **Datasources setup** grid, a new **Company** field is available. For existing records, this field shows the identifier of the current legal entity.

5. In the **Datasources setup** grid, add a line for each additional legal entity that must be included in reporting, and set the following fields.

    | Field                  | Description                                                                                                                   |
    |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | Name                   | Enter a value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
    | Message item type      | Select **VAT return**. This value is the only value that is available for all the records.                                    |
    | Account type           | Select **All**.                                                                                                               |
    | Master table name      | Specify **TaxReportVoucher** for all the records.                                                                             |
    | Document number field  | Specify **Voucher** for all the records.                                                                                      |
    | Document date field    | Specify **TransDate** for all the records.                                                                                    |
    | Document account field | Specify **TaxPeriod** for all the records.                                                                                    |
    | Company                | Select the ID of the legal entity.                                                                                            |
    | User query             | The checkbox is automatically selected when you define criteria by selecting **Edit query**.                                  |

6. For each new line, select **Edit query**, and specify a related settlement period for the legal entity that is specified in the **Company** field on the line.

    When the setup is completed, the **Collect data** function on the **Electronic messages** page collects sales tax payments from all legal entities that you defined.
