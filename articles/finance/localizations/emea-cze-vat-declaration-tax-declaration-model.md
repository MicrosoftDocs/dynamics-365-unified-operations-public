
# VAT declaration (The Czech Republic)


This topic provides information about the value-added tax (VAT) declaration for
the Czech Republic. It includes instructions for setting up and generating the
VAT declaration and VAT control statement.

# VAT declaration overview

## VAT declaration

This paragraph provides an overview of the sections and rows of VAT declaration,
calculations, and relations between the VAT declaration and VAT control
statement

To be able to generate VAT declaration and VAT control statement automatically,
you should first create enough sales tax codes for keeping separate VAT
accounting for each of VAT declaration box. You also need to associate **Sales
tax codes** with the **Lookup result** of the **Lookup for the VAT declaration
boxes** in the **Application specific parameters** of the VAT declaration format
and VAT control statement format. You can find more details about how to set up
**Application specific parameters** in the sections
[below](#set-up-parameters-for-declarations-fields).

Column **Application specific parameters – lookup result** in the table below
shows you which **Lookup result** is preconfigured for a specific VAT
declaration row in the VAT declaration format and VAT control statement format.
You should use this information to correctly associate Sales tax codes with the
Lookup result and subsequently with the VAT declaration row.

Note. If you configure Sales tax codes for posting incoming reverse charge VAT
with **Use tax**, you should associate your Sales tax codes with the Lookup
result that contains UseTax in the name, for example for EU purchases, configure
**EUPurchaseGoodsUseTaxStandard** for **Use tax** sales tax codes or
**EUPurchaseGoodsVATPayableStandard** for sales tax codes with Reverse charge.
See more details about how to configure Reverse charge VAT in the topic [Reverse
charges](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-reverse-charge).

### Section I Taxable transactions

<table width="100%">
<tbody>
<tr>
<td width="4%">
<p><strong>Row</strong></p>
</td>
<td width="8%">
<p><strong>Control statement </strong><strong>section</strong></p>
</td>
<td width="25%">
<p><strong>Description</strong></p>
</td>
<td width="9%">
<p><strong>R</strong><strong>ate</strong></p>
</td>
<td width="11%">
<p><strong>XML element - </strong><strong>Tax base</strong></p>
</td>
<td width="10%">
<p><strong>XML element -</strong><strong>Tax payable</strong></p>
</td>
<td width="31%">
<p><strong>Report field (Application specific parameters &ndash; lookup result)</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>1</p>
</td>
<td width="8%">
<p>A4 \ A5</p>
</td>
<td width="25%">
<p>Domestic sales of goods and services</p>
</td>
<td width="9%">
<p>standard</p>
</td>
<td width="11%">
<p>obrat23</p>
</td>
<td width="10%">
<p>dan23</p>
</td>
<td width="31%">
<p>DomesticSalesVATPayableStandard<br /> (minus) VATAdjustmentCustomerBadDebtsStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>2</p>
</td>
<td width="8%">
<p>A4 \ A5</p>
</td>
<td width="25%">
<p>Domestic sales of goods and services</p>
</td>
<td width="9%">
<p>reduced</p>
</td>
<td width="11%">
<p>obrat5</p>
</td>
<td width="10%">
<p>dan5</p>
</td>
<td width="31%">
<p>DomesticSalesVATPayableReduced<br /> DomesticSalesVATPayableReduced2<br /> (minus) VATAdjustmentCustomerBadDebtsReduced<br /> (minus) VATAdjustmentCustomerBadDebtsReduced2</p>
</td>
</tr>
<tr>
<td width="4%">
<p>3</p>
</td>
<td width="8%">
<p>A2</p>
</td>
<td width="25%">
<p>Intra-community purchase of goods</p>
</td>
<td width="9%">
<p>standard</p>
</td>
<td width="11%">
<p>p_zb23</p>
</td>
<td width="10%">
<p>dan_pzb23</p>
</td>
<td width="31%">
<p>EUPurchaseGoodsVATPayableStandard</p>
<p>EUPurchaseGoodsUseTaxStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>4</p>
</td>
<td width="8%">
<p>A2</p>
</td>
<td width="25%">
<p>Intra-community purchase of goods</p>
</td>
<td width="9%">
<p>reduced</p>
</td>
<td width="11%">
<p>p_zb5</p>
</td>
<td width="10%">
<p>dan_pzb5</p>
</td>
<td width="31%">
<p>EUPurchaseGoodsVATPayableReduced<br /> EUPurchaseGoodsVATPayableReduced2</p>
<p>EUPurchaseGoodsUseTaxReduced</p>
<p>EUPurchaseGoodsUseTaxReduced2</p>
</td>
</tr>
<tr>
<td width="4%">
<p>5</p>
</td>
<td width="8%">
<p>A2</p>
</td>
<td width="25%">
<p>Intra-community purchase of services</p>
</td>
<td width="9%">
<p>standard</p>
</td>
<td width="11%">
<p>p_sl23_e</p>
</td>
<td width="10%">
<p>dan_psl23_e</p>
</td>
<td width="31%">
<p>EUPurchaseServicesVATPayableStandard</p>
<p>EUPurchaseServicesUseTaxStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>6</p>
</td>
<td width="8%">
<p>A2</p>
</td>
<td width="25%">
<p>Intra-community purchase of services</p>
</td>
<td width="9%">
<p>reduced</p>
</td>
<td width="11%">
<p>p_sl5_e</p>
</td>
<td width="10%">
<p>dan_psl5_e</p>
</td>
<td width="31%">
<p>EUPurchaseServicesVATPayableReduced<br /> EUPurchaseServicesVATPayableReduced2</p>
<p>EUPurchaseServicesUseTaxReduced</p>
<p>EUPurchaseServicesUseTaxReduced2</p>
</td>
</tr>
<tr>
<td width="4%">
<p>7</p>
</td>
<td width="8%">
<p>n/a</p>
</td>
<td width="25%">
<p>Import of goods</p>
</td>
<td width="9%">
<p>standard</p>
</td>
<td width="11%">
<p>dov_zb23</p>
</td>
<td width="10%">
<p>dan_dzb23</p>
</td>
<td width="31%">
<p>ImportGoodsVATPayableStandard</p>
<p>ImportGoodsUseTaxStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>8</p>
</td>
<td width="8%">
<p>n/a</p>
</td>
<td width="25%">
<p>Import of goods</p>
</td>
<td width="9%">
<p>reduced</p>
</td>
<td width="11%">
<p>dov_zb5</p>
</td>
<td width="10%">
<p>dan_dzb5</p>
</td>
<td width="31%">
<p>ImportGoodsVATPayableReduced</p>
<p>ImportGoodsUseTaxReduced</p>
</td>
</tr>
<tr>
<td width="4%">
<p>9</p>
</td>
<td width="8%">
<p>A2</p>
</td>
<td width="25%">
<p>Intra-community purchase of new means of transport</p>
</td>
<td width="9%">
<p>&nbsp;</p>
</td>
<td width="11%">
<p>p_dop_nrg</p>
</td>
<td width="10%">
<p>dan_pdop_nrg</p>
</td>
<td width="31%">
<p>EUPurchaseNewTransportVATPayable</p>
<p>EUPurchaseNewTransportUseTax</p>
</td>
</tr>
<tr>
<td width="4%">
<p>10</p>
</td>
<td width="8%">
<p>B1</p>
</td>
<td width="25%">
<p>Purchase of goods and services under domestic reverse charge ($92)</p>
</td>
<td width="9%">
<p>standard</p>
</td>
<td width="11%">
<p>rez_pren23</p>
</td>
<td width="10%">
<p>dan_rpren23</p>
</td>
<td width="31%">
<p>DomesticPurchaseReverseChargeVATPayableStandard</p>
<p>DomesticPurchaseReverseChargeUseTaxStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>11</p>
</td>
<td width="8%">
<p>B1</p>
</td>
<td width="25%">
<p>Purchase of goods and services under domestic reverse charge ($92)</p>
</td>
<td width="9%">
<p>reduced</p>
</td>
<td width="11%">
<p>rez_pren5</p>
</td>
<td width="10%">
<p>dan_rpren5</p>
</td>
<td width="31%">
<p>DomesticPurchaseReverseChargeVATPayableReduced<br /> DomesticPurchaseReverseChargeVATPayableReduced2</p>
<p>DomesticPurchaseReverseChargeUseTaxReduced</p>
<p>DomesticPurchaseReverseChargeUseTaxReduced2</p>
</td>
</tr>
<tr>
<td width="4%">
<p>12</p>
</td>
<td width="8%">
<p>A2</p>
</td>
<td width="25%">
<p>Other purchases with obligation to pay VAT</p>
</td>
<td width="9%">
<p>standard</p>
</td>
<td width="11%">
<p>p_sl23_z</p>
</td>
<td width="10%">
<p>dan_psl23_z</p>
</td>
<td width="31%">
<p>OtherPurchasesVATPayableStandard</p>
<p>OtherPurchasesUseTaxStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>13</p>
</td>
<td width="8%">
<p>A2</p>
</td>
<td width="25%">
<p>Other purchases with obligation to pay VAT</p>
</td>
<td width="9%">
<p>reduced</p>
</td>
<td width="11%">
<p>p_sl5_z</p>
</td>
<td width="10%">
<p>dan_psl5_z</p>
</td>
<td width="31%">
<p>OtherPurchasesVATPayableReduced<br /> OtherPurchasesVATPayableReduced2</p>
<p>OtherPurchasesUseTaxReduced</p>
<p>OtherPurchasesUseTaxReduced2</p>
</td>
</tr>
</tbody>
</table>

### Section II Other supplies and supplies with place of supply outside the Czech Republic with the right to deduct

<table width="100%">
<tbody>
<tr>
<td width="4%">
<p><strong>Row</strong></p>
</td>
<td width="9%">
<p><strong>&nbsp;Control statement </strong><strong>section</strong></p>
</td>
<td width="36%">
<p><strong>Description</strong></p>
</td>
<td width="17%">
<p><strong>XML element - </strong><strong>Tax base</strong></p>
</td>
<td width="31%">
<p><strong>Report field (Application specific parameters &ndash; lookup result)</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>20</p>
</td>
<td width="9%">
<p>n/a</p>
</td>
<td width="36%">
<p>Intra-community sales of goods</p>
</td>
<td width="17%">
<p>dod_zb</p>
</td>
<td width="31%">
<p>EUSalesGoods</p>
</td>
</tr>
<tr>
<td width="4%">
<p>21</p>
</td>
<td width="9%">
<p>n/a</p>
</td>
<td width="36%">
<p>Intra-community sales of services</p>
</td>
<td width="17%">
<p>pln_sluzby</p>
</td>
<td width="31%">
<p>EUSalesServices</p>
</td>
</tr>
<tr>
<td width="4%">
<p>22</p>
</td>
<td width="9%">
<p>n/a</p>
</td>
<td width="36%">
<p>Export of goods</p>
</td>
<td width="17%">
<p>pln_vyvoz</p>
</td>
<td width="31%">
<p>ExportGoods</p>
</td>
</tr>
<tr>
<td width="4%">
<p>23</p>
</td>
<td width="9%">
<p>n/a</p>
</td>
<td width="36%">
<p>Intra-community sales of new means of transport to non-taxable person</p>
</td>
<td width="17%">
<p>dod_dop_nrg</p>
</td>
<td width="31%">
<p>EUSalesNewTransport</p>
</td>
</tr>
<tr>
<td width="4%">
<p>24</p>
</td>
<td width="9%">
<p>n/a</p>
</td>
<td width="36%">
<p>Intra-community consignment of goods</p>
</td>
<td width="17%">
<p>pln_zaslani</p>
</td>
<td width="31%">
<p>EUConsignmentGoods</p>
</td>
</tr>
<tr>
<td width="4%">
<p>25</p>
</td>
<td width="9%">
<p>A1</p>
</td>
<td width="36%">
<p>Sales of goods and services under domestic reverse charge ($92)</p>
</td>
<td width="17%">
<p>pln_rez_pren</p>
</td>
<td width="31%">
<p>DomesticSalesReverseCharge</p>
</td>
</tr>
<tr>
<td width="4%">
<p>26</p>
</td>
<td width="9%">
<p>A3 and Other</p>
</td>
<td width="36%">
<p>Other tax deductible transactions</p>
</td>
<td width="17%">
<p>pln_ost</p>
</td>
<td width="31%">
<p>OtherSalesWithRightToDeduct<br /> OtherSalesWithRightToDeductGoldInvestment</p>
</td>
</tr>
</tbody>
</table>


### Section III Additional data

<table width="1020">
<tbody>
<tr>
<td width="47">
<p><strong>Row</strong></p>
</td>
<td width="95">
<p><strong>&nbsp;Control statement </strong><strong>section</strong></p>
</td>
<td width="340">
<p><strong>Description</strong></p>
</td>
<td width="113">
<p><strong>XML element - </strong><strong>Tax base</strong></p>
</td>
<td width="104">
<p><strong>XML element - </strong><strong>Tax amount</strong></p>
</td>
<td width="321">
<p><strong>Report field (Application specific parameters &ndash; lookup result)</strong></p>
</td>
</tr>
<tr>
<td width="47">
<p>30</p>
</td>
<td width="95">
<p>n/a</p>
</td>
<td width="340">
<p>Simplified triangular Intra-community acquisition of goods</p>
</td>
<td width="113">
<p>tri_pozb</p>
</td>
<td width="104">
<p>n/a</p>
</td>
<td width="321">
<p>SimplifiedTriangularEUPurchaseGoods</p>
</td>
</tr>
<tr>
<td width="47">
<p>31</p>
</td>
<td width="95">
<p>n/a</p>
</td>
<td width="340">
<p>Simplified triangular Intra-community sale of goods</p>
</td>
<td width="113">
<p>tri_dozb</p>
</td>
<td width="104">
<p>n/a</p>
</td>
<td width="321">
<p>SimplifiedTriangularEUSalesGoods</p>
</td>
</tr>
<tr>
<td width="47">
<p>32</p>
</td>
<td width="95">
<p>n/a</p>
</td>
<td width="340">
<p>Import of exempt goods</p>
</td>
<td width="113">
<p>dov_osv</p>
</td>
<td width="104">
<p>n/a</p>
</td>
<td width="321">
<p>ImportGoodsVATExempt</p>
</td>
</tr>
<tr>
<td width="47">
<p>33</p>
</td>
<td width="95">
<p>A4</p>
</td>
<td width="340">
<p>VAT amount adjustment for bad debts - creditor</p>
</td>
<td width="113">
<p>n/a</p>
</td>
<td width="104">
<p>opr_verit</p>
</td>
<td width="321">
<p><em>Informative value. Included in Rows 1 and 2</em><br /> <br /> VATAdjustmentCustomerBadDebtsStandard<br /> VATAdjustmentCustomerBadDebtsReduced<br /> VATAdjustmentCustomerBadDebtsReduced2</p>
</td>
</tr>
<tr>
<td width="47">
<p>34</p>
</td>
<td width="95">
<p>B2</p>
</td>
<td width="340">
<p>VAT amount adjustment for bad debts - debtor</p>
</td>
<td width="113">
<p>n/a</p>
</td>
<td width="104">
<p>opr_dluz</p>
</td>
<td width="321">
<p><em>Informative value. Included in Rows 40 and 41</em><br /> <br /> VATAdjustmentVendorBadDebtsStandard<br /> VATAdjustmentVendorBadDebtsReduced<br /> VATAdjustmentVendorBadDebtsReduced2</p>
</td>
</tr>
</tbody>
</table>


### Section IV VAT deduction

<table width="99%">
<tbody>
<tr>
<td width="4%">
<p><strong>Row</strong></p>
</td>
<td width="7%">
<p><strong>&nbsp;Control statement </strong><strong>section</strong></p>
</td>
<td width="20%">
<p><strong>Description</strong></p>
</td>
<td width="7%">
<p><strong>&nbsp;</strong><strong>Rate</strong></p>
</td>
<td width="9%">
<p><strong>XML element - </strong><strong>Tax base</strong></p>
</td>
<td width="7%">
<p><strong>XML element -Full tax deduction</strong></p>
</td>
<td width="9%">
<p><strong>XML element - Tax deduction adjustment</strong></p>
</td>
<td width="34%">
<p><strong>Report field (Application specific parameters &ndash; lookup result)</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>40</p>
</td>
<td width="7%">
<p>B2/B3</p>
</td>
<td width="20%">
<p>From taxable purchases</p>
</td>
<td width="7%">
<p>standard</p>
</td>
<td width="9%">
<p>pln23</p>
</td>
<td width="7%">
<p>odp_tuz23_nar</p>
</td>
<td width="9%">
<p>odp_tuz23</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> PurchaseVATDeductionStandard<br /> AcquiredAssetsStandard<br /> (minus) VATAdjustmentVendorBadDebtsStandard<br /> <br /> <strong>Deduction adjustment</strong>:<br /> PurchaseVATDeductionAdjustStandard</p>
<p>AcquiredAssetsAdjustStandard<br /> (minus) VATAdjustmentVendorBadDebtsAdjustStandard<br /> </p>
</td>
</tr>
<tr>
<td width="4%">
<p>41</p>
</td>
<td width="7%">
<p>B2/B3</p>
</td>
<td width="20%">
<p>From taxable purchases</p>
</td>
<td width="7%">
<p>reduced</p>
</td>
<td width="9%">
<p>pln5</p>
</td>
<td width="7%">
<p>odp_tuz5_nar</p>
</td>
<td width="9%">
<p>odp_tuz5</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> PurchaseVATDeductionReduced<br /> PurchaseVATDeductionReduced2<br /> AcquiredAssetsReduced<br /> (minus) VATAdjustmentVendorBadDebtsReduced<br /> (minus) VATAdjustmentVendorBadDebtsReduced2<br /> <br /> <strong>Deduction adjustment</strong>:<br /> PurchaseVATDeductionAdjustReduced<br /> PurchaseVATDeductionAdjustReduced2<br /> (minus)VATAdjustmentVendorBadDebtsAdjustReduced<br /> (minus)VATAdjustmentVendorBadDebtsAdjustReduced2<br /> AcquiredAssetsAdjustReduced</p>
</td>
</tr>
<tr>
<td width="4%">
<p>42</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>From import of goods when Tax authority is the customs office</p>
</td>
<td width="7%">&nbsp;</td>
<td width="9%">
<p>dov_cu</p>
</td>
<td width="7%">
<p>odp_cu_nar</p>
</td>
<td width="9%">
<p>odp_cu</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> ImportVATDeductionTaxAdminCustomsOffice<br /> <br /> <strong>Deduction adjustment</strong>:<br /> ImportVATDeductionAdjustTaxAdminCustomsOffice</p>
</td>
</tr>
<tr>
<td width="4%">
<p>43</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>From taxable transactions reported in rows 3-13</p>
</td>
<td width="7%">
<p>standard</p>
</td>
<td width="9%">
<p>nar_zdp23</p>
</td>
<td width="7%">
<p>od_zdp23</p>
</td>
<td width="9%">
<p>odkr_zdp23</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> VATDeductionFromPurchasesWithVATPayableStandard</p>
<p>&nbsp;</p>
<p>EUPurchaseGoodsUseTaxStandard (from row 3)</p>
<p>EUPurchaseServicesUseTaxStandard (from row 5)</p>
<p>ImportGoodsUseTaxStandard (from row 7)</p>
<p>EUPurchaseNewTransportUseTax (from row 9)</p>
<p>DomesticPurchaseReverseChargeUseTaxStandard&nbsp; (from row 10)</p>
<p>OtherPurchasesUseTaxStandard (from row 12)<br /> <br /> <strong>Deduction adjustment</strong>:<br /> VATDeductionAdjustFromPurchasesWithVATPayableStandard</p>
</td>
</tr>
<tr>
<td width="4%">
<p>44</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>From taxable transactions reported in rows 3-13</p>
</td>
<td width="7%">
<p>reduced</p>
</td>
<td width="9%">
<p>nar_zdp5</p>
</td>
<td width="7%">
<p>od_zdp5</p>
</td>
<td width="9%">
<p>odkr_zdp5</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> VATDeductionFromPurchasesWithVATPayableReduced</p>
<p>&nbsp;</p>
<p>EUPurchaseGoodsUseTaxReduced (from row 4)</p>
<p>EUPurchaseGoodsUseTaxReduced2 (from row 4)</p>
<p>EUPurchaseServicesUseTaxReduced&nbsp; (from row 6)</p>
<p>EUPurchaseServicesUseTaxReduced2 (from row 6)</p>
<p>ImportGoodsUseTaxReduced (from row 8)</p>
<p>DomesticPurchaseReverseChargeUseTaxReduced (from row 11)</p>
<p>DomesticPurchaseReverseChargeUseTaxReduced2 (from row 11)</p>
<p>OtherPurchasesUseTaxReduced (from row 13)</p>
<p>OtherPurchasesUseTaxReduced2 (from row 13)<br /> <br /> <strong>Deduction adjustment</strong>:<br /> VATDeductionAdjustFromPurchasesWithVATPayableReduced</p>
</td>
</tr>
<tr>
<td width="4%">
<p>45</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>Correction of tax deductions</p>
</td>
<td width="7%">&nbsp;</td>
<td width="9%">
<p>n/a</p>
</td>
<td width="7%">
<p>odp_rez_nar</p>
</td>
<td width="9%">
<p>odp_rezim</p>
</td>
<td width="34%">
<p><strong>Full deduction:</strong><br /> VATDeductionCorrection<br /> <br /> <strong>Deduction adjustment</strong>:<br /> VATDeductionAdjustCorrection</p>
</td>
</tr>
<tr>
<td width="4%">
<p><strong>46</strong></p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p><strong>Total deduction (40 + 41 + 42 + 43 + 44 + 45)</strong></p>
</td>
<td width="7%">&nbsp;</td>
<td width="9%">
<p><strong>n/a</strong></p>
</td>
<td width="7%">
<p><strong>odp_sum_nar</strong></p>
</td>
<td width="9%">
<p><strong>odp_sum_kr</strong></p>
</td>
<td width="34%">&nbsp;</td>
</tr>
<tr>
<td width="4%">
<p>47</p>
</td>
<td width="7%">
<p>n/a</p>
</td>
<td width="20%">
<p>Value of acquired assets defined in &sect; 4 para. d) ae)</p>
</td>
<td width="7%">
<p>x</p>
</td>
<td width="9%">
<p>nar_maj</p>
</td>
<td width="7%">
<p>od_maj</p>
</td>
<td width="9%">
<p>odkr_maj</p>
</td>
<td width="34%">
<p><em>Informative value. Included in Rows 40 and 41</em></p>
<p>&nbsp;</p>
<p><strong>Full deduction:</strong></p>
<p>AcquiredAssetsStandard<br /> AcquiredAssetsReduced<br /> </p>
<p><strong>Deduction adjustment</strong>:</p>
<p>AcquiredAssetsAdjustStandard</p>
<p>AcquiredAssetsAdjustReduced</p>
</td>
</tr>
</tbody>
</table>


### V Reduction of the right to deduct

<table width="98%">
<tbody>
<tr>
<td width="4%">
<p><strong>Row</strong></p>
</td>
<td width="24%">
<p><strong>Description</strong></p>
</td>
<td width="11%">
<p><strong>XML element - Tax base</strong></p>
</td>
<td width="60%">
<p><strong>Comment</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>50</p>
</td>
<td width="24%">
<p>Exempt sales</p>
</td>
<td width="11%">
<p>plnosv_kf</p>
</td>
<td width="60%">
<p>Application specific parameter &ndash; lookup result: SalesVATExempt</p>
</td>
</tr>
<tr>
<td width="4%">
<p>51</p>
</td>
<td width="24%">
<p>Value of sales not included in calculation of coefficient Row 53 - With right to deduct</p>
</td>
<td width="11%">
<p>pln_nkf</p>
</td>
<td width="60%">
<p><em>Informative value - <u>only for December declaration.</u> Relates to all January-December transactions</em></p>
<p>&nbsp;</p>
<p>Manual amount &ndash; user input parameter on the report dialog: <strong>Value of taxable sales not included in calculation of coefficient</strong></p>
<p><strong>&nbsp;</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>51</p>
</td>
<td width="24%">
<p>Value of sales not included in calculation of coefficient Row 53 - Without right to deduct</p>
</td>
<td width="11%">
<p>plnosv_nkf</p>
</td>
<td width="60%">
<p><em>Informative value - <u>only for December declaration. </u>Relates to all January-December transactions</em></p>
<p>&nbsp;</p>
<p>Manual amount &ndash; user input parameter on the report dialog: <strong>Value of exempt sales not included in calculation of coefficient</strong></p>
<p><em>&nbsp;</em></p>
</td>
</tr>
<tr>
<td width="4%">
<p>52</p>
</td>
<td width="24%">
<p>Part of the reduced tax deduction (with deduction adjustment): Pro rata coefficient</p>
</td>
<td width="11%">
<p>koef_p20_nov</p>
</td>
<td width="60%">
<p>Pro rata coefficient.</p>
<p>&nbsp;</p>
<p>User input parameter <strong>Pro rata coefficient</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>52</p>
</td>
<td width="24%">
<p>Part of the reduced tax deduction (with deduction adjustment): Deduction amount</p>
</td>
<td width="11%">
<p>dp_uprav_kf</p>
</td>
<td width="60%">
<p>Calculated automatically as: Deduction amount = 46.odp_sum_kr * 52.koef_p20_nov</p>
</td>
</tr>
<tr>
<td width="4%">
<p>53</p>
</td>
<td width="24%">
<p>Settlement of tax deduction &ndash; New pro rata coefficient</p>
</td>
<td width="11%">
<p>koef_p20_vypor</p>
</td>
<td width="60%">
<p><em><u>Only for December declaration</u></em><em>.</em></p>
<p><em>&nbsp;</em></p>
<p>New pro rata coefficient.&nbsp; Manual amount &ndash; user input parameter on the report dialog: <strong>New pro rata coefficient</strong></p>
<p><strong>&nbsp;</strong></p>
<p>You can calculate this amount manually based on all January-December declarations amounts as follows:</p>
<p>1. Calculate <strong>Value of Taxable sales</strong> = Rows (1 + 2 + 20 + 21 + 22 + 23 + 24 + 25 + 26 + 31).TaxBase</p>
<p>2. Calculate <strong>Value of Exempt sales</strong> = Row 50.TaxBase</p>
<p>3. Calculate <strong>New pro rata coefficient</strong> =</p>
<p><strong>Value of Taxable sales</strong> - <strong>Value of taxable sales not included in calculation of coefficient</strong><br /> delete on <br /> <strong>Value of Taxable sales</strong> + <strong>Value of Exempt sales</strong> - <strong>Value of taxable sales not included in calculation of coefficient</strong> - <strong>Value of exempt sales not included in calculation of coefficient</strong></p>
<p><strong>&nbsp;</strong></p>
</td>
</tr>
<tr>
<td width="4%">
<p>53</p>
</td>
<td width="24%">
<p>Settlement of tax deduction &ndash; Change of deduction</p>
</td>
<td width="11%">
<p>vypor_odp</p>
</td>
<td width="60%">
<p><em><u>Only for December declaration</u></em><em>.</em></p>
<p>&nbsp;</p>
<p>Adjustment of tax deduction. This line reflects correction of annual VAT deduction based on actual pro rata coefficient versus applied during the year estimated pro rata coefficient.<strong><br /> <br /> </strong>Manual amount &ndash; user input parameter on the report dialog: <strong>Value of annual settlement of tax deduction</strong></p>
<p>&nbsp;</p>
<p>You can calculate this amount manually based on all January-December declarations amounts as follows:</p>
<p>Row 46.Tax deduction adjustment * (<strong>New pro rata coefficient</strong> &ndash; <strong>Pro rata coefficient</strong>)<br /> </p>
</td>
</tr>
</tbody>
</table>


### VI Tax calculation

<table width="99%">
<tbody>
<tr>
<td width="10%">
<p><strong>Row</strong></p>
</td>
<td width="27%">
<p><strong>Description</strong></p>
</td>
<td width="16%">
<p><strong>Value</strong></p>
</td>
<td width="44%">
<p><strong>Comment</strong></p>
</td>
</tr>
<tr>
<td width="10%">
<p>60</p>
</td>
<td width="27%">
<p>Tax deduction adjustment</p>
</td>
<td width="16%">
<p>uprav_odp</p>
</td>
<td width="44%">
<p><em><u>Only for December declaration</u></em></p>
<p>&nbsp;</p>
<p>Application specific parameter &ndash; lookup result: VATDeductionAdjustmentFA</p>
<p>&nbsp;</p>
<p><em>For all fixed assets from which the Tax payer claimed VAT deduction the Tax payer has to monitor how the fixed assets are used. If the entitlement to VAT deduction changes during the monitoring period, then the Tax payer is obliged to adjust the relevant VAT deduction in the VAT statement for December of the year when the entitlement to VAT deduction has changed.</em></p>
<p>&nbsp;</p>
<p>You should set up a special Sales tax code for tax deduction adjustment due to the change in fixed assets usage and manually post the tax transaction for 100% of tax amount when you need to adjust the VAT deduction in this line</p>
<p><strong>&nbsp;</strong></p>
</td>
</tr>
<tr>
<td width="10%">
<p>61</p>
</td>
<td width="27%">
<p>Tax refund</p>
</td>
<td width="16%">
<p>dan_vrac</p>
</td>
<td width="44%">
<p>Application specific parameter &ndash; lookup result: TaxRefund</p>
<p>&nbsp;</p>
<p><em>Under some conditions, a Tax payer is obliged to pay back amount of VAT to a customer &ndash; an individual from third countries who paid Czech VAT from goods which the individual purchased in the Czech Republic and subsequently transported to third country. </em></p>
<p><em>It means that the tax payer will declare the respective transaction on row 1 or 2 in the VAT statement and then they can claim a tax refund on row 61 once all conditions stipulated by the Czech VAT Act are met.</em></p>
<p>&nbsp;</p>
<p>You should set up a special Sales tax code for tax refund to the individuals and manually post the tax transaction for 100% of tax amount when you need to show Tax refund in this line</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="10%">
<p><strong>62</strong></p>
</td>
<td width="27%">
<p><strong>Total tax payable</strong></p>
</td>
<td width="16%">
<p>dan_zocelk</p>
</td>
<td width="44%">
<p><strong>&nbsp;</strong></p>
<p>Calculated automatically as <strong>Rows 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10 + 11 + 12 + 13 - 61</strong></p>
</td>
</tr>
<tr>
<td width="10%">
<p>63</p>
</td>
<td width="27%">
<p>Total tax deduction</p>
</td>
<td width="16%">
<p>odp_zocelk</p>
</td>
<td width="44%">
<p><strong>&nbsp;</strong></p>
<p>Calculated automatically as<strong> Row 46.Full tax deduction + Row 52.Deduction + Row 53.Change of deduction + Row 60</strong></p>
</td>
</tr>
<tr>
<td width="10%">
<p>64</p>
</td>
<td width="27%">
<p>Tax to be paid</p>
</td>
<td width="16%">
<p>dano_da</p>
</td>
<td width="44%">
<p>Calculated automatically as Row 62 &ndash; Row 63 if 62 &gt; 63</p>
</td>
</tr>
<tr>
<td width="10%">
<p>65</p>
</td>
<td width="27%">
<p>Excess deduction</p>
</td>
<td width="16%">
<p>dano_no</p>
</td>
<td width="44%">
<p>Calculated automatically as Row 63 &ndash; Row 62 if 63 &gt; 62</p>
</td>
</tr>
<tr>
<td width="10%">
<p>66</p>
</td>
<td width="27%">
<p>Adjustment for additional tax return</p>
</td>
<td width="16%">
<p>dano</p>
</td>
<td width="44%">
<p>Calculated automatically as Row 62 &ndash; Row 63</p>
</td>
</tr>
</tbody>
</table>


## VAT control statement

This section provides an overview of the sections of VAT control statement

### Section A1 Sales of goods and services under domestic reverse charge

Section A1 shows documents which generate amount in the Row 25 of the VAT
declaration.

This section contains the following information about each document:

| **Field**                                      | **XML element** |
|------------------------------------------------|-----------------|
| Tax document number                            | c_evid_dd       |
| VAT number of the customer (numeric part only) | ic_odb          |
| Date (which is the date of VAT register)       | duzp            |
| Subject code                                   | kod_pred_pl     |
| Tax base                                       | zakl_dane1      |

For automatic determination of the **Subject code** for the document, you should
set up enough **Reverse charge item groups** and associate them with Items
(products), Items group, or procurement categories. You can find more details
about this step in the sections [below](#set-up-reverse-charge-item-groups). You
can find more details about how to configure reverse charges fully in the topic
[Reverse charge
VAT](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-reverse-charge)
. If you are going to post incoming reverse charges in the vendor invoice
journals that do not have association to products, you should have enough item
sales tax groups to differentiate the subject codes of the reverse charges.

You also need to associate pairs **Reverse charge item groups** – **Tax code**
with the **Lookup result** of the **\$SubjectCodeLookup** in the **Application
specific parameters** of the **VAT control statement (CZ)** format. You can find
more details about how to set up **Application specific parameters** in the
sections [below](#set-up-parameters-for-subject-codes).

The following subject codes are available in the **VAT control statement XML
(CZ)** format:

| **Code**                 | **Description**                                                               |
|--------------------------|-------------------------------------------------------------------------------|
| GoldDelivery             | 1. Gold delivery (§92b)                                                       |
| TangibleAssetDelivery    | 3. Delivery of tangible asset (§92d)                                          |
| ConstructionInstallation | 4. Construction or installation (§92e)                                        |
| GoodsAnnex5              | 5. Goods listed in Annex 5 of VAT Act (§92c)                                  |
| AllowancesGasEmission    | 11. Transfer of allowances and greenhouse gas emissions                       |
| CerealsIndustrialCrops   | 12. Cereals and industrial crops                                              |
| Metals                   | 13. Metals including precious metals                                          |
| MobilePhones             | 14. Mobile phones                                                             |
| Integrated circuits      | 15. Integrated circuits and printed circuit boards                            |
| PortableDevices          | 16. Portable devices for automatic data processing (e.g. tablets or notebook) |
| VideoGameConsole         | 17. Video game consoles                                                       |

### Section B1 Purchase of goods and services under domestic reverse charge (\$92)

Section B1 contains document which generate amounts in Rows 10,11 of VAT
declaration.

This section contains the following information about each document:

| **Field**                                           | **XML element** |
|-----------------------------------------------------|-----------------|
| Tax document number                                 | c_evid_dd       |
| VAT number of the vendor (numeric part only)        | dic_dod         |
| Date (which is the date of incoming vendor invoice) | duzp            |
| Subject code                                        | kod_pred_pl     |
| Tax base at standard rate                           | zakl_dane1      |
| Tax amount at standard rate                         | dan1            |
| Tax base at first reduced rate                      | zakl_dane2      |
| Tax amount at first reduced rate                    | dan2            |
| Tax base at second reduced rate                     | zakl_dane3      |
| Tax amount at second reduced rate                   | dan3            |

For automatic determination of the **Subject code** for the document, you should
make the same settings as described above for the Section A1.

### Section A2 Purchases with reverse charge (excluding domestic reverse charge) with obligation to pay VAT

Section A2 shows documents which generate amount in the Rows 3,4,5,6,9
(Intracommunity purchase of goods and services), and in the Rows 11,12 (Other
purchases with the obligation to pay VAT) of the VAT declaration.

This section contains the following information about each document:

| **Field**                                                              | **XML element** |
|------------------------------------------------------------------------|-----------------|
| Tax document number                                                    | c_evid_dd       |
| VAT number of the vendor from another Member State (numeric part only) | vatid_dod       |
| Country that allocated the VAT number to the vendor                    | k_stat          |
| Date (which is the date of VAT register)                               | Dppd            |
| Tax base at standard rate                                              | zakl_dane1      |
| Tax amount at standard rate                                            | dan1            |
| Tax base at first reduced rate                                         | zakl_dane2      |
| Tax amount at first reduced rate                                       | dan2            |
| Tax base at second reduced rate                                        | zakl_dane3      |
| Tax amount at second reduced rate                                      | dan3            |

### Section A3 Transactions with the special scheme of gold sales

Section A3 shows documents which generate amount in the Row 25 of the VAT
declaration together with other sales with right to deduct incoming VAT.

To automatically determine such transactions, you should set up a special Sales
tax code for such transactions and associate this sales tax code with the
**Lookup result OtherSalesWithRightToDeductGoldInvestment** of the
**\$ReportFieldLookup** in the **Application specific parameters** of the VAT
declaration format and VAT control statement format.

This section contains the following information about each document:

| **Field**                                                     | **XML element** |
|---------------------------------------------------------------|-----------------|
| Tax document number                                           | c_evid_dd       |
| VAT number of the customer (numeric part only) if it exists   | vatid_odb       |
| Country that allocated the VAT number to the customer         | k_stat          |
| Date (which is the date of VAT register)                      | dup             |
| The value of the sales                                        | osv_plneni      |
| Place of residence of the customer if there is no VAT number  | m_pobytu_sidlo  |
| First and last name of the customer if there is no VAT number | jm_prijm_obch   |
| Date of birth of the customer if there is no VAT number       | d_narozeni      |

### Section A4. Taxable sales with amount above 10 000 including VAT and all VAT adjustments made for customer bad debts

Sections A4 and A5 show documents which generate amounts in the Rows 1,2 of the
VAT declaration.

Also note that VAT amount adjustments for customer bad debts are also
informationally shown in the Row 33 of the VAT declaration.

To automatically determine amount of VAT adjustment for bad debts, you should
create a special Tax code and post writing off the customer bad debts using this
Tax code. You can find more details about this procedure in the sections
[below](#write-off-customer-bad-debts-using-write-off-function). You also should
associate this sales tax code with the **Lookup results
VATAdjustmentCustomerBadDebtsStandard, VATAdjustmentCustomerBadDebtsReduced,
VATAdjustmentCustomerBadDebtsReduced2** of the **\$ReportFieldLookup** in the
**Application specific parameters** of the VAT declaration format and VAT
control statement format.

This section contains the following information about each document:

| **Field**                                                                                                                                          | **XML element** |
|----------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| Tax document number                                                                                                                                | c_evid_dd       |
| VAT number of the customer                                                                                                                         | dic_odb         |
| Date (which is the date of VAT register)                                                                                                           | Dppd            |
| Fulfillment mode code: - “0” for normal filling - “1” for special scheme for travel service - “2” for special regime for second-hand goods         | kod_rezim_pl    |
| Tax base at standard rate                                                                                                                          | zakl_dane1      |
| Tax amount at standard rate                                                                                                                        | dan1            |
| Tax base at first reduced rate                                                                                                                     | zakl_dane2      |
| Tax amount at first reduced rate                                                                                                                   | dan2            |
| Tax base at second reduced rate                                                                                                                    | zakl_dane3      |
| Tax amount at second reduced rate                                                                                                                  | dan3            |
| Flag of VAT adjustment for bad debts: -“N” if the document is not VAT adjustment of bad debts - “P” if the document is VAT adjustment of bad debts | zdph_44         |

To automatically determine Fulfillment mode code, you should associate sales tax
codes with the **Lookup result** of the **\$FulfillmentModeCodeLookup** in the
**Application specific parameters** of the VAT control statement (XML) format.
You can find more details about how to set up **Application specific
parameters** in the sections
[below](#set-up-parameters-for-fulfillment-mode-codes).

The following Fulfillment mode codes are available in the format VAT control
statement XML:

| **Code**                        | **Description**                                     |
|---------------------------------|-----------------------------------------------------|
| NormalFilling                   | 0. Normal filling                                   |
| SpecialSchemeForTravelService   | 1. § 89 ZDPH (special scheme for travel service)    |
| SpecialRegimeForSecondHandGoods | 2. § 90 ZDPH (special regime for second-hand goods) |

### Section B2 Taxable purchases with amount above 10 000 including VAT and all VAT adjustments made for vendor bad debts

Sections B2 and B3 show documents which generate amounts in the Rows 40,41 of
the VAT declaration.

Also note that VAT amount adjustments for vendor bad debts are also
informationally shown in the Row 34 of the VAT declaration.

To automatically determine amount of VAT adjustment for bad debts, you should
create a special Tax code and post writing off the vendor bad debts using this
Tax code. You can find more details about this procedure in the sections
[below.](#write-off-vendor-bad-debts-manually) You also should associate this
sales tax code with the **Lookup results VATAdjustmentVendorBadDebtsStandard,
VATAdjustmentVendorBadDebtsReduced, VATAdjustmentVendorBadDebtsReduced2** of the
**\$ReportFieldLookup** in the **Application specific parameters** of the VAT
declaration format and VAT control statement format.

Section B2 contains the following information about each document:

| **Field**                                                                                                                                           | **XML element** |
|-----------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| Tax document number                                                                                                                                 | c_evid_dd       |
| VAT number of the vendor                                                                                                                            | dic_dod         |
| Date (which is the date of incoming vendor invoice)                                                                                                 | Dppd            |
| Tax base at standard rate                                                                                                                           | zakl_dane1      |
| Tax amount at standard rate                                                                                                                         | dan1            |
| Tax base at first reduced rate                                                                                                                      | zakl_dane2      |
| Tax amount at first reduced rate                                                                                                                    | dan2            |
| Tax base at second reduced rate                                                                                                                     | zakl_dane3      |
| Tax amount at second reduced rate                                                                                                                   | dan3            |
| Flag of VAT adjustment for bad debts: - “N” if the document is not VAT adjustment of bad debts - “P” if the document is VAT adjustment of bad debts | zdph_44         |
| Flag of the proportional right of deduction: Yes/No                                                                                                 | pomer           |

Out of the box, flag of the proportional right of deduction is set to No.

### Section A5 Taxable sales with amount below 10 000 incl. VAT and when there is no obligation to issue tax document

Sections A4 and A5 show documents which generate amounts in the Rows 1,2 of the
VAT declaration

Section A5 contains 1 line with the following information for all documents
included in this section:

| **Field**                         | **XML element** |
|-----------------------------------|-----------------|
| Tax base at standard rate         | zakl_dane1      |
| Tax amount at standard rate       | dan1            |
| Tax base at first reduced rate    | zakl_dane2      |
| Tax amount at first reduced rate  | dan2            |
| Tax base at second reduced rate   | zakl_dane3      |
| Tax amount at second reduced rate | dan3            |

### Section B3 Taxable purchases with amount below 10 000 incl. VAT

Sections B2 and B3 show documents which generate amounts in the in the Rows
40,41 of the VAT declaration.

Section B3 contains 1 line with the following information for all documents
included in this section:

| **Field**                         | **XML element** |
|-----------------------------------|-----------------|
| Tax base at standard rate         | zakl_dane1      |
| Tax amount at standard rate       | dan1            |
| Tax base at first reduced rate    | zakl_dane2      |
| Tax amount at first reduced rate  | dan2            |
| Tax base at second reduced rate   | zakl_dane3      |
| Tax amount at second reduced rate | dan3            |

# Set up the VAT declaration

To start to work with the VAT declaration, you should make the following
settings:

## Download electronic reporting formats

In [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/V2),
in the Shared asset library, download the latest versions of the Electronic
reporting (ER) configurations for the VAT declaration format:

-   **Tax declaration model**

-   **Tax declaration model mapping**

-   **VAT declaration XML (CZ)** – this is configuration in XML format DPHDP3

-   **VAT declaration Excel (CZ)** – this configuration could be used to preview
    VAT declaration amounts in Excel. Please take into account that Excel
    template in is English language only. If you need to have the report printed
    in another language, you need have a small customization: to translate the
    Excel template to another language and attach it to your derived
    configuration.

-   **VAT control statement (CZ)** – this is configuration in XML format DPHKH1

>   For more information, see [Download Electronic reporting configurations from
>   Lifecycle
>   Services](https://docs.microsoft.com/en-us/dynamics365/dev-itpro/analytics/download-electronic-reporting-configuration-lcs).

## Set up Application specific parameters for formats

### Set up parameters for declarations fields

To automatically generate VAT declaration, you should associate sales tax codes
in the application and report fields in the Electronic reporting configuration.

1.  Go to **Workspaces \> Electronic reporting**. Select **Reporting
    configurations**.

2.  Select configuration **VAT declaration XML (CZ)**. Click **Configurations \>
    Application specific parameters setup**

3.  On the FastTab **Lookups**, select lookup **\$ReportFieldLookup**

4.  On the FastTab **Conditions**, associate Sales tax codes and report fields:

<table>
<tbody>
<tr>
<td>
<p><strong>Column</strong></p>
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
<p>Select report field for which you make setup. See details on report fields assignment to VAT declaration rows in the section <a href="#_VAT_declaration">VAT declaration overview</a></p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td>
<p>Tax code (Code)</p>
</td>
<td>
<p>Select Sales tax code which you associate to the report field. Tax transactions posted with the selected sales tax code will be collected in the respective report field.</p>
<p>It&rsquo;s highly recommended to separate sales tax codes in a way that one sales tax code is generating amounts in only one report field.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td>
<p>Name</p>
</td>
<td>
<p>If you didn&rsquo;t create enough sales tax codes so that one sales tax code is generating amounts in only one report field, you can additionally setup <strong>Transaction classifier</strong> in this column.</p>
<p>The following transaction classifiers are available for selection:</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;Purchase&rdquo; (Purchase),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;PurchaseExempt&rdquo; (Tax exempt purchase),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;PurchaseReverseCharge&rdquo; (Tax receivable from purchase reverse charge),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;Sales&rdquo; (Sales),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;SalesExempt&rdquo; (Tax exempt sales),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;SalesReverseCharge&rdquo; (Tax payable from purchase reverse charge/ Sales reverse charge),</p>
<p>-&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &ldquo;Use tax&rdquo; (Use tax)</p>
<p>&nbsp;</p>
<p>For each transaction classifier a classifier for the credit note is also available, for example, &ldquo;PurchaseCreditNote&rdquo; (Purchase credit note)</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

To prevent the format to throw an exception error message due to missed setup,
you can create the following line in the parameters:

| **Lookup result** | **Tax code (Code)** | **Name**      |
|-------------------|---------------------|---------------|
| Other             | \*Not blank\*       | \*Not blank\* |

> Notes: This line must be created as the last line in the parameters.
> If you create this line, you should make sure that you set up parameters for all
> sales tax codes in the system. If some sales tax codes are missing in the setup,
> tax transactions with them will not be collected to VAT declaration.
> If you don’t create this line, you’ll get error message during the report run in
> case of there is tax transaction with the sales tax code that is not configured
> in the Application specific parameters.

5.  Change **State** of Application specific parameters to **Completed**.

6.  Review example of parameters on the picture:

![](media/9ee9c0c4f7590ccdb0280c9e9c95e88c.png)

>   A screenshot of a social media post Description automatically generated

7.  On the Action pane, click **Export** to export parameters at XML file.

8.  Select configuration **VAT declaration Excel (CZ**). On the Action pane,
    click **Import** to import parameters that you configured for **VAT
    declaration XML (CZ)**. Change **State** to **Completed.**

9.  Select configuration **VAT control statement XML (CZ)**. Make the same
    settings manually as you did in point 4 above. Change **State** to
    **Completed.**

### Set up parameters for subject codes 

To automatically classify the transaction to the subject code of reverse charge
in VAT control statement sections A1 and B1, you should associate pairs of
reverse charge item groups and item sales tax groups in the application and
supply codes in the Electronic reporting configuration.

1.  Go to **Workspaces \> Electronic reporting**. Select **Reporting
    configurations**.

2.  Select configuration **VAT control statement XML (CZ)**. Click
    **Configurations \> Application specific parameters setup.**

3.  On the FastTab **Lookups**, select lookup **\$SubjectCodeLookup**

4.  On the FastTab **Conditions**, associate **Reverse charge item groups** and
    subject codes:

| **Column**                          | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Lookup result                       | Select subject code. The full list of subject codes is available above in [Section A1 Sales of goods and services under domestic reverse charge](#section-a1-sales-of-goods-and-services-under-domestic-reverse-charge)                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Reverse charge code (Code)          | Select Reverse charge item group which you associate to the selected Subject code. Note that if for certain transactions you post incoming reverse charge transaction without reference to the product, you will need to associate item sales tax group to the Subject code and in this case you should select \*Blank\* in this field. You must always have one line in the Application specific parameter with **Lookup result** = **Other** and **Reverse charge code (Code)** = **\*Blank\*** so that system does not throw an exception error message when taking transactions without reverse charge. This must be the last line in the setup. |
| Item sales tax group (TaxItemGroup) | Select Item sales tax group which you associate to the selected Subject code. Note that you need to select specific item sales tax group here if you do not have appropriate reverse charge item group in the application and is going to post incoming reverse charge transaction without reference to the product (for example from the vendor invoice journal). Otherwise for all lines you can select **\*Not blank\*** in this column.                                                                                                                                                                                                          |

To prevent the format to fail with exception due to missed setup, you should set
up the following lines as the last lines:

| **Lookup result** | **Reverse charge code (Code)** | **Item sales tax group (TaxItemGroup)** | **Comment**                                                                                                     |
|-------------------|--------------------------------|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| Other             | \*Blank\*                      | \*Not blank\*                           | It’s a must to set up this line so that there is no error message for transactions without reverse charge code. |

Review example of parameters on the picture:

![A screenshot of a social media post Description automatically generated](media/f9a43bf89c05bab0c2c4cc878c2eefdf.png)

### Set up parameters for fulfillment mode codes

To automatically classify the transaction to the fulfillment mode code in VAT
control statement section A4, you should associate sales tax codes in the
application and fulfillment subjects mode codes in the Electronic reporting
configuration.

1.  Go to **Workspaces \> Electronic reporting**. Select **Reporting
    configurations**.

2.  Select configuration **VAT control statement XML (CZ)**. Click
    **Configurations \> Application specific parameters setup.**

3.  On the FastTab **Lookups**, select lookup **\$FulfillmentModeCodeLookup**

4.  On the FastTab **Conditions**, associate sales tax codes and fulfillment
    subjects mode codes:

| **Column**      | **Description**                                                                                                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Lookup result   | Select fulfillment code. The full list of codes is available above in [Section A4. Taxable sales with amount above 10 000 including VAT and all VAT adjustments made for customer bad debts](#section-a4.-taxable-sales-with-amount-above-10000-including-vat-and-all-vat-adjustments-made-for-customer-bad-debts) |
| Tax code (Code) | Select sales tax code                                                                                                                                                                                                                                                                                              |

If you have only transactions with normal filling, you can create the following
lines of the setting:

| **Lookup result** | **Tax code (Code)** |
|-------------------|---------------------|
| NormalFilling     | \*Not blank\*       |

Otherwise, to prevent the format to fail with exception due to missed setup, you
should set up the same line as the last line of the setting.

### Set up parameters for no obligation to issue tax document

To automatically classify the sales transaction to the condition that there was
no obligation to issue tax document and consequently the transaction should be
shown in Section A5 regardless the threshold, you should associate pairs of
Sales tax group and sales tax code from the application to Yes or No condition
in the Electronic reporting configuration.

1.  Go to **Workspaces \> Electronic reporting**. Select **Reporting
    configurations**.

2.  Select configuration **VAT control statement XML (CZ)**. Click
    **Configurations \> Application specific parameters setup.**

3.  On the FastTab **Lookups**, select lookup **\$NoTaxDocument**

4.  On the FastTab **Conditions**, associate sales tax groups and sales tax
    codes:

| **Column**      | **Description**                                                                                                                                                                                                          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Lookup result   | Select Yes if there is no obligation to issue tax document (primarily this may be because customer is not registered for VAT purposes).                                                                                  |
| Sales tax group | Select sales tax group that you associate to customer when there is no obligation to issue tax document to them. If you are going to determine the condition using Sales tax code values, select **\*Not blank\*** here. |
| Tax code (Code) | Select sales tax code assigned to transaction if there is no obligation to issue tax document. If you can determine conditions using Sales tax group only, select **\*Not blank\*** here.                                |

5.  To prevent the format to fail with exception due to missed setup, create the
    following line as the last line in the setup:

| **Lookup result** | **Sales tax group (TaxGroup)** | **Tax code (Code)** |
|-------------------|--------------------------------|---------------------|
| No                | \*Not blank\*                  | \*Not blank\*       |

Review example of parameters on the picture:

![A screenshot of a social media post Description automatically generated](media/de6e7ebd2dad61ba82d80d75af80d1aa.png)

6.  Change **State** of all parameters to **Completed**.

## Download and import the Data management package with example settings of Electronic messages.

>   The data package with example settings contains Electronic message settings
>   that are used to generate VAT declaration and VAT control statement as well
>   as to preview VAT declaration in Excel. You can extend these settings or
>   create your own. For more information about how to work with Electronic
>   messaging and how to create your own settings, see [Electronic
>   messaging](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/electronic-messaging).

Follow these steps:

1.  In the LCS Shared asset library, select **Data package** as the asset type.
    Download the package that is named **CZ VAT EM declaration package**. The
    file that is downloaded is named **CZ VAT declaration EM package.zip**.

2.  In the **Data management** workspace, select **Import**.

3.  In the **Job details** section, set the following values:

    -   In the **Name** field, enter any name for the job.

    -   In the **Data source format** field, select **Package**.

4.  In the **Upload data file** field, select **Upload**, and then select
    the **CZ VAT declaration EM package.zip** file that you downloaded earlier.

5.  After the data entities are uploaded, select **Import**.

6.  Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic
    messages** and validate the electronic message processings that you
    imported.

| **Processing**        | **Processing code** | **Description**                             |
|-----------------------|---------------------|---------------------------------------------|
| VAT declaration       | DPHDP3              | VAT declaration in the Czech Republic       |
| VAT control statement | DPHKH1              | VAT control statement in the Czech Republic |

## Configure Electronic messages

1.  Set up information about Taxpayer in Electronic message additional fields

    1.1  Go to **Tax \> Setup \> Electronic messages \> Additional fields**

    1.2  Select the line with additional field and on the FastTab **Value** add
        respective values of the field:

| **Additional field**     | **Value**                                                                                                                                                                           |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **DataBoxID**            | Enter identifier of the company’s Data box.                                                                                                                                         |
| **MainEconomicActivity** | Enter the code of company’s main economic activity                                                                                                                                  |
| **TaxAuthorityToFile**   | Enter the code of the tax authority to which the declaration file will be sent                                                                                                      |
| **ProRataCoef**          | Enter the pro rata coefficient applied during the year. If you need to apply pro rata coefficient in the declaration, enter the decimal value between 0 and 1 with comma separator. |

2.  Set up default values for declarations run in Electronic message processing

    2.1  Go to **Tax \> Setup \> Electronic messages \> Electronic message
        processing**

    2.2  Select the line with processing and set up default values for
        declarations parameters on the FastTab **Message additional fields**:

| **Processing**                                           | **Additional field**         | **Comment**                                                                                                                                               | **XML element**                                                                                                                     |
|----------------------------------------------------------|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| DPHKH1 (VAT control statement)                           | **\<DataBoxID\>**            | Select Data box Id entered earlier                                                                                                                        | id_dats                                                                                                                             |
| DPHDP3 (VAT declaration)                                 | **\<MainEconomicActivity\>** | Select main economic activity code entered earlier                                                                                                        | c_okec                                                                                                                              |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<TaxAuthorityToFile\>**   | Select tax authority code entered earlier                                                                                                                 | c_pracufo                                                                                                                           |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<ReportPeriodicity\>**    | Select the periodicity of the declaration submission in the reporting year: Monthly or Quarterly                                                          | Ctvrt – will be filled with the quarter number for Quarterly report Mesic – will be filled with the month number for Monthly report |
| DPHDP3 (VAT declaration)                                 | **\<TaxpayerType\>**         | Select the type of the Taxpayer: Taxpayer, Group or Other                                                                                                 | typ_platce                                                                                                                          |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<TaxpayerLegalForm\>**    | Select the form of the taxpayer: Person or Organization                                                                                                   | typ_ds                                                                                                                              |
| DPHDP3 (VAT declaration)                                 | **\<ProRataCoef\>**          | Select the pro rata coefficient entered earlier                                                                                                           | koef_p20_nov                                                                                                                        |
| DPHDP3 (VAT declaration), DPHKH1 (VAT control statement) | **\<NullDeclaration\>**      | Select No, which is the default value, whether you submit Null declaration. You should be able to change this default value during declaration processing | VAT declaration: Trans = “N”, if Yes = “A”, if No VAT control statement: vyzva_odp = “B”, if Yes                                    |

3.  Set up parameters in Populate records

    3.1  Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate
        records actions**. On the **Populate records action** page, select the
        line and select **Edit query.** Specify filter on settlement period(s)
        to be included in the report.

    3.2  If you need to report tax transactions from other settlement periods in
        a different declaration, you should create new Populate records action,
        and select appropriate settlement period(s).

# Configure system parameters and master records

You should do the following settings prior to generating VAT declaration:

| **Page**                                                                                                                                   | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Legal entities** (Go to **Organization administration \> Organizations \> Legal entities**)                                              | **Click Registration IDs**. Set up Tax registration number of the company. It should be setup for **Tax registration type** that is assigned to Tax registration category **VAT ID**. Find more details in [Set up VAT ID](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tasks/eur-00015-vat-id).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **Legal entities**                                                                                                                         | On the FastTab **Addresses**, define the primary address for the legal entity. On the FastTab Contact information define **Phone** and **Email address.** Set them to **Primary.**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **Tax Authorities**                                                                                                                        | Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax authorities**. Create the tax authority where the tax declaration is provided. Enter the tax authority code in the field **Authority identification**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **All customers (Go to Accounts receivable \> Customers \> All customers) All vendors (Go to Accounts payable \> Vendors \> All vendors)** | Set up Vat IDs for customers and vendors. Find more details in [Registration of vendor VAT ID](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tasks/eur-00015-registration-vendor-vat-id)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **General ledger parameters** (Go to **General ledger \> Setup \> Ledger setup \> General ledger parameters**)                             | On the tab **Sales tax**, FastTab **Tax options**, in the **Electronic reporting** group of fields, in the **VAT statement format mapping** field, select **VAT declaration Excel (CZ)** format. This format will be printed when you run **Report sales tax for settlement period**. Also this format will be printed when you click **Print** in **Sales tax payments** page. Find more details in the sections below.                                                                                                                                                                                                                                                                                                                                                                                          |
| **General ledger parameters**                                                                                                              | On the tab **Sales tax**, FastTab **Tax options**, in the **Special report** group of fields, select **Yes** in the **Date of VAT register** field.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **General ledger parameters**                                                                                                              | On the tab **Sales tax**, on the FastTab **VAT statement**, you can define some parameters of the company: **Taxpayer status** - select **Taxpayer**, **Group**, or **Other Taxpayer type** - select **Individual**, or **Corporation Main economic activity** - Enter the code **Factor** - Enter the pro rata coefficient applied during the year. Note that you can configure the same information about the company in **Additional fields** of **Electronic messages.** When you run the declaration, you’ll be able to select the source of information about the company in the field **Tax Jurisdiction**: local fields described below that are available for the legal entity in CZE country\\region only (select **The Czech Republic**) or Electronic message additional fields (select **Default**). |

## Set up reverse charge item groups

Refer to the topic [Reverse charge
VAT](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-reverse-charge)
to find all details about how to set up and use reverse charges functionality.

1.  Go to **Tax \> Setup \> Sales tax \> Reverse charge item groups**. Create the new group.

2.  On the FastTab **Setup,** in the **Sales/purchase field**, select **Purchase.** Create a line and define Item code, Item group or Procurement category code that purchase is associated to the created reverse charge item group: 
  2.1 In the field **Item code** select **Table**, **Group** or **Category**.
  2.2 In the field **Item relation**, select item code or item group.
  2.3 In the field **Category**, select procurement category.

3.  On the FastTab **Setup,** in the **Sales/purchase field**, select **Sales** and associate item, item group and procurement category as described above.

# Generate VAT declaration

## Generate VAT declaration from Electronic messages.

The processing steps described below are applicable to the example Electronic
message processing that is released to LCS.

1.  To generate the VAT declaration XML file, go to **Tax \> Inquiries and
    reports \> Electronic messages \> Electronic messages**.

2.  In the left pane, select the report format to generate. For example,
    select **DPHDP3**.

3.  On the **Messages** FastTab, select **New**. Then, in the **Run
    processing** dialog box, select **OK**.

4.  Select the message line that was created. Enter a **Description** and
    specify the **Start date** and **End date** for the declaration.

5.  On the **Messages** FastTab, select **Collect data**, select **OK**.

    On the **Message items** FastTab, review the Sales tax payments that are
    transferred for processing. By default, you get sales tax payments of the
    selected period that were not included in any other message of the same
    processing.

    Click **Original document** to review sales tax payment.

    Click **Delete** to exclude some sales tax payments from processing. Note, that this step is optional. If you skip this step, you still can
    generate VAT declaration using **Tax declaration version** parameter on the
    declaration dialog. See below for more details.

6.  On the **Message additional fields** FastTab, validate the value of the
    field \<**NullDeclaration\>**. Select Yes if you are reporting the null
    declaration.

7.  On the **Messages** FastTab, select **Update status**. In the **Update
    status** dialog, select **Ready to generate** action. Select **OK**.
    Validate that the message status is changed to **Ready to generate**.

8.  On the **Messages** FastTab, select **Generate report**. Then, to preview
    VAT declaration amounts, in the **Run processing** dialog box,
    select **Preview DPHDP3 in Excel** and click **OK**. In the **Electronic
    reporting parameters** dialog box, enter parameters of VAT declaration. See
    below for details of available parameters

9.  Select **OK**. When Excel file with VAT declaration preview is generated,
    select the **Attachments** button (the paper clip symbol) in the upper-right
    corner of the page. Then select **Open** to open the file. Review amounts in
    Excel.

10.  On the **Messages** FastTab, select **Generate report**. Then, in the **Run
    processing** dialog box, select **Generate DPHDP3** to generate XML file and
    click **OK**.

11.  In the **Electronic reporting parameters** dialog box, enter the following
    information:

<table width="973">
<thead>
<tr>
<td width="255">
<p><strong>Field</strong></p>
</td>
<td width="718">
<p><strong>Description</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="255">
<p>Tax settlement period</p>
</td>
<td width="718">
<p>If you run <strong>Collect data</strong> above, skip this step. Otherwise, select the applicable settlement period.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Tax declaration version</p>
</td>
<td width="718">
<p>If you run <strong>Collect data</strong> above, skip this step. Report will be generated for sales tax transactions included in the collected sales tax payments.</p>
<p>Otherwise, select one of the following values:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong>&nbsp;&ndash; Generate a report for sales tax transactions of the original sales tax payment, or before the sales tax payment is generated (<strong>Sales tax payment version</strong> has value <strong>Original</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Corrections</strong>&nbsp;&ndash; Generate a report for sales tax transactions of all the subsequent sales tax payments for the period (<strong>Sales tax payment version</strong> has value <strong>Latest corrections</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Total list</strong>&nbsp;&ndash; Generate a report for all sales tax transactions for the period, including the original and all corrections.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Tax Jurisdiction</p>
</td>
<td width="718">
<p>Select <strong>Default</strong> to take information about the company from <strong>Additional fields</strong> of <strong>Electronic messages</strong>.</p>
<p>Select The Czech Republic to take information about the company from the local Czech fields in <strong>General ledger parameters</strong> page.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Contact person</p>
</td>
<td width="718">
<p>Select the employee who has created the report. Name, surname and phone of this employee will be exported to XML file.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Signatory</p>
</td>
<td width="718">
<p>Select employee who has signed the report. Name, surname and position of this employee in the company will be exported to XML file.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Correction reason date</p>
</td>
<td width="718">
<p>Enter date on which the reason for submitting supplementary declaration was observed. Applicable for Supplementary and Supplementary/corrective declarations.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>New pro rata coefficient</p>
</td>
<td width="718">
<p>For December declaration, enter new pro rata coefficient which you have calculated based on annual data.</p>
<p>This value will be exported to Row 53 if the declaration.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Next year report periodicity</p>
</td>
<td width="718">
<p>For December declaration specify periodicity of declaration for the next year of this is different from the current periodicity.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Value of exempt sales not included in calculation of coefficient,</p>
<p>Value of taxable sales not included in calculation of coefficient</p>
</td>
<td width="718">
<p>For December declaration specify amounts of exempt and taxable sales respectively that are not included in calculation of new coefficient if your company had such sales during the year.</p>
<p>These amounts will be exported to Row 51 of the declaration.</p>
</td>
</tr>
<tr>
<td width="255">
<p>Value of annual settlement of tax deduction</p>
</td>
<td width="718">
<p>For December declaration specify amount of annual tax deduction adjustment due to applying of the new pro rata coefficient.</p>
<p>This amount will be exported to Row 53 of the declaration.</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

12.  Select **OK**. When the declaration in XML is generated, the status of the
    message is changed to **Generated**.

![](media/88e0c7eea30f6fef270d134eac29ef7a.jpg)

>   A screenshot of a cell phone Description automatically generated

  If an error occurs while the report is generated, the status of the message is changed to **Technical error**.

13.  Select the **Attachments** button (the paper clip symbol) in the upper-right
    corner of the page. Then select **Open** to open the file.

14.  Review the file and if this is ok, update the status to **Approved** to
    finish the processing: select **Update status**. Then, in the **Update
    status** dialog box select action **Approve** and select **OK**.

   If you need to delete message, you can select action **Allow delete** and select **OK**. Now you can Delete the message.

   If the message status is **Technical error**, you can update the message status to one of initial statuses: **Created** or **Ready to generate**.

15.  On the **Action log** FastTab, review all user actions for the current
    message.

16.  When you complete generating the VAT declaration, you should manually send
    the generated file to the tax authority.

## Generate VAT control statement from Electronic messages.

1.  To generate the VAT control statement XML file, go to **Tax \> Inquiries and
    reports \> Electronic messages \> Electronic messages**.

2.  In the left pane, select the report format to generate. For example,
    select **DPHKH1**.

3.  Follow steps 3-7 of previous paragraph to create the message and update the
    status to **Ready to generate**.

4.  On the **Messages** FastTab, select **Generate report**. Then, in the **Run
    processing** dialog box, select **Generate DPHKH1** to generate XML file and
    click **OK**.

5.  In the **Electronic reporting parameters** dialog box, enter the following
    information:

| **Field**                                                                                                           | **Description**                                                                                                     |
|---------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Tax settlement period, Tax declaration version, Contact person, Signatory, Correction reason date, Declaration type | Define values in the same way as described in the paragraph above for VAT declaration                               |
| Reference number                                                                                                    | Enter reference number if applicable                                                                                |
| Threshold                                                                                                           | Enter threshold amount to split documents between sections A4/A5 and B2/B3. For example, for year 2020 enter 10000. |

## Generate VAT declaration in Excel from Inquiries and reports menu item.

1. Go to **Tax \> Periodic tasks \> Declarations \> Sales tax \> Report sales tax for settlement period**. In the **Report sales tax for settlement period** dialog, select the following:

<table width="973">
<thead>
<tr>
<td width="255">
<p><strong>Field</strong></p>
</td>
<td width="718">
<p><strong>Description</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="255">
<p>Settlement period</p>
<p>&nbsp;</p>
</td>
<td width="718">
<p>Select the settlement period</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Sales tax payment version</p>
</td>
<td width="718">
<p>Select the following:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong>&nbsp;&ndash; Generate a report for sales tax transactions of the original sales tax payment, or before the sales tax payment is generated (<strong>Sales tax payment version</strong> has value <strong>Original</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Corrections</strong>&nbsp;&ndash; Generate a report for sales tax transactions of all the subsequent sales tax payments for the period (<strong>Sales tax payment version</strong> has value <strong>Latest corrections</strong>).</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Total list</strong>&nbsp;&ndash; Generate a report for all sales tax transactions for the period, including the original and all corrections.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>From date</p>
</td>
<td width="718">
<p>Select the first date of the reporting period</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

2.  Select **OK**. Review generated Excel file.

## Generate VAT declaration in Excel from Sales tax payments

1. Go to **Tax \> Periodic tasks \> Declarations \> Sales tax \> Settle and post sales tax.** In the **Settle and post sales tax** dialog, define the following:

<table width="973">
<thead>
<tr>
<td width="255">
<p><strong>Field</strong></p>
</td>
<td width="718">
<p><strong>Description</strong></p>
</td>
</tr>
</thead>
<tbody>
<tr>
<td width="255">
<p>Settlement period</p>
<p>&nbsp;</p>
</td>
<td width="718">
<p>Select the settlement period</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>Sales tax payment version</p>
</td>
<td width="718">
<p>Select the following:</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Original</strong>&nbsp;&ndash; Generate original sales tax payment for settlement period.</p>
<p>&middot;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <strong>Latest corrections</strong>&nbsp;&ndash; Generate a correction sales tax payment after the original sales tax payment for the settlement period was created.</p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="255">
<p>From date</p>
</td>
<td width="718">
<p>Select the first date of the reporting period</p>
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>

2. Select **OK**. Go to **Tax \> Inquiries and reports \> Sales tax inquiries \> Sales tax payments**. Review generated sales tax payment line.

# Set up to run VAT declaration for several legal entities

To use the formats to report the VAT declaration for a group of several legal
entities, you should first set up Application specific parameters of the ER
formats for each of the legal entities.

## Set up Electronic messages to collect data from several legal entities

1.  Turn on the **Cross-company queries for the populate records
    actions** feature in Feature management. Go to **Workspaces** \> **Feature
    management**, find **Cross-company queries for the populate records
    actions** in the list, and then select **Enable now** in the lower right of
    the page.

2.  Go to **Tax** \> **Setup** \> **Electronic messages** \> **Populate records
    actions**. On the **Populate records action** page, a new **Company** field
    is available in the **Datasources setup** grid. For existing records, this
    field shows the identifier of the current legal entity.

3.  In the **Datasources setup** grid, add a line for each additional legal
    entity that must be included in reporting. Set up the following fields.

| **Field name**         | **Value**                                                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Name                   | Enter a text value that will help you understand where this record comes from. For example, enter **VAT payment of Subsidiary 1**. |
| Message item type      | Select **VAT return**. This value is the only value that is available for all the records.                                         |
| Account type           | Select **All**.                                                                                                                    |
| Master table name      | Specify **TaxReportVoucher** for all the records.                                                                                  |
| Document number field  | Specify **Voucher** for all the records.                                                                                           |
| Document date field    | Specify **TransDate** for all the records.                                                                                         |
| Document account field | Specify **TaxPeriod** for all the records.                                                                                         |
| Company                | Select the ID of the legal entity.                                                                                                 |
| User query             | The check box is automatically selected when you define criteria by using **Edit query** button.                                   |

4.  For each new line, select **Edit query**, and specify a related settlement
    period for the legal entity that is specified in the **Company** field on
    the line.

5.  As result of this setup, **Collect data** function on **Electronic
    message**s page will collect sales tax payments from all legal entities that
    you define here.

# Generate VAT declaration for several legal entities

The following are preconditions for running this procedure:

1.  The field **Date of VAT register** on **General ledger parameters** page,
    **Sales tax** tab, has the same value for all legal entities for which you
    collect data.

2.  Sales tax payment is posted for the reporting period in all legal entities.

    To generate VAT declaration for several legal entities, do the following:

3.  Go to **Tax \> Inquiries and reports \> Electronic messages \> Electronic
    messages**.

4.  In the left pane, select the report format to generate. For example,
    select **DPHDP3**.

5.  On the **Messages** FastTab, select **New**. Then, in the **Run
    processing** dialog box, select **OK**.

6.  Select the message line that was created. Enter a **Description** and
    specify the **Start date** and **End date** for the declaration.

7.  On the **Messages** FastTab, select **Collect data**, select **OK**.

    On the **Message items** FastTab, review the Sales tax payments that are
    transferred for processing. Value in the field **Company** indicates the
    legal entity where Sales tax payment is processed.

    Click **Original document** to review sales tax payment.

    Click **Delete** to exclude some sales tax payments from processing

8.  Process declaration in standard way. When the file is generated, review that
    the report contains all tax transactions from the selected sales tax
    payments.

# How to

## How to attach a File or a Note to the VAT declaration

Follow these steps to attach a File or a Note to the VAT declaration XML file.

Attached text notes will be exported to Sections **VetaR** of the VAT
declaration XML file.

Attached files will be exported as Base64 binary file attachments to the
**Prilohy** XML element.

1.  Go to **Organization administration \> Document management \> Active
    document tables**. In the **Table name** select **Sales tax payment**.

2.  Go to **Tax \> Inquiries and reports \> Sales tax inquiries \> Sales tax
    payments**. Select a line with sales tax payment and click **Paperclip**
    link in the upper right corner.

3.  In the opened page **Attachments for Sales tax payments**, select **New \>
    File** and add a file attachment.

4.  Select **New \> Note** and fill **Description** and **Notes** fields.

## How to post VAT adjustment for bad debts

### Write off customer bad debts using Write off function

Follow the example steps to write off customer bad debts:

1.  Create a customer on **All customers** page in a standard way.

2.  Create and post a free text invoice on **All free text invoices** page in a
    standard way.

3.  Create a sales tax code WRITEOFF21 on **Sales tax codes** page, specifically
    for usage in writing off bad debts with 21% of VAT rate

4.  Go to **General ledger \> Ledger setup \> Journal setup \> Journal names**.
    Create a general ledger journal “WriteOff”. Select **Journal type** =
    **Daily**.

5.  **Go to Accounts receivable \> Setup \> Account receivable parameters \>
    Collections** tab **\> Write-off** FastTab**.** Select the journal
    “WriteOff” in the field **Write-off journal**. Set **Separate sales tax** to
    **Yes.**

6.  Go to **Accounts receivable \> Customers \> All customers**. Select the
    customer record created above. Select **Collections \> Write off**. On the
    **Write off** dialog, define **Write-off date, Reason code** and
    **Description.** Click **OK.**

7.  Go to General ledger \> Journal entries \> General journals. Select the
    journal “WriteOff” that was automatically generated. Select Lines. Review
    that tree lines were created:

    -   Account type **Customer** – on the total invoice amount including VAT
    -   Account type **Ledger** – on the invoice amount without VAT
    -   Account type **Ledger** – on the VAT amount.

8.  Select the line with VAT amount. Go to Tab **General**. Select sales tax code WRITEOFF21 created above in the field **Sales tax code**.

9.  Post the journal. Review posted sales tax transaction:

   -   **Sales tax direction** = **Sales tax payable**
   -   **Amount origin** is equal to invoice amount without VAT
   -   **Actual sales tax amount** is equal to VAT amount

10.  Go to **Electronic reporting** workspace, select configuration with VAT declaration format. Select **Configurations \> Application specific parameters \> Set up**. Create the following lines:

| **Lookup result**                     | **Tax code (Code)** | **Name**          |
|---------------------------------------|---------------------|-------------------|
| VATAdjustmentCustomerBadDebtsStandard | WRITEOFF19          | Sales             |
| VATAdjustmentCustomerBadDebtsStandard | WRITEOFF19          | Sales credit note |

### Write off vendor bad debts manually

Follow the example steps to write off vendor bad debts:

1.  Create a vendor on **All vendors** page in a standard way.

2.  Create and post a vendor invoice on **Invoice journal** page in a standard
    way.

3.  Review the settings of the sales tax code **WRITEOFF21** created above on
    **Sales tax codes** page. Alternatively create a new one fore writing off
    vendor bad debts.

4.  Create Sales tax group **WRITEOFF**. Add a line with sales tax code
    **WRITEOFF21** on the FastTab **Setup**.

5.  Go to Items sales tax groups. Select affected item sales tax group. Add a
    line with sales tax code WRITEOFF21 on the FastTab **Setup**.

6.  Go to daily general journal and create a line for writing off the vendor
    invoice manually. Fill the following fields:

    Enter **Date**,

    Select Vendor in the field **Account type**,

    Select vendor account created above in the field **Account**

    Enter write off amount in the field **Debit**

    On tab **General**, select Sales tax group **WRITEOFF,** and **Item sales
    tax group** selected on step 5 above.

7.  Settle open vendor invoice in standard way. Post journal. Review posted sales tax transaction:

    -   **Sales tax direction** = **Sales tax receivable**
    -   **Amount origin** is equal to invoice amount without VAT
    -   **Actual sales tax amount** is equal to VAT amount

8.  Go to **Electronic reporting** workspace, select configuration with VAT declaration format. Select **Configurations \> Application specific parameters \> Set up**. Create the following lines:

| **Lookup result**                   | **Tax code (Code)** | **Name**             |
|-------------------------------------|---------------------|----------------------|
| VATAdjustmentVendorBadDebtsStandard | WRITEOFF19          | Purchase             |
| VATAdjustmentVendorBadDebtsStandard | WRITEOFF19          | Purchase credit note |

## How to post tax amount correction

Follow the example steps to post correction of VAT deduction (Row 45)

1.  Create a sales tax code **CORR** on **Sales tax codes** page, specifically for usage in correction of the VAT deduction that is reflected in Row 45 of VAT declaration

2.  Go to **General ledger \> Journal entries \> General journals**. Select the daily journal. Select **Lines**.

3.  Create the following journal line:

| **Date**       | **Account type**  | **Account**                                         | **Description**                       | **Debit**                                     | **Offset account type** | **Offset account**                                           |
|----------------|-------------------|-----------------------------------------------------|---------------------------------------|-----------------------------------------------|-------------------------|--------------------------------------------------------------|
| Enter the date | Select **Ledger** | Select **Ledger account** for posting VAT deduction | Enter description for the transaction | Enter amount in increase VAT deduction amount | Select **Ledger**       | Select **Ledger account** to offset posting of VAT deduction |

4.  Go to Tab **General**. Select sales tax code **CORR** created above in the field **Sales tax code**.

5.  Post the journal. Review posted sales tax transaction:

    -   **Sales tax direction** = **Sales tax receivable**
    -   **Amount origin** is equal to zero
    -   **Actual sales tax amount** is equal to Debit amount

6.  Go to **Electronic reporting** workspace, select configuration with VAT declaration format. Select **Configurations \> Application specific parameters \> Set up**. Create the following lines:

| **Lookup result**      | **Tax code (Code)** | **Name**             |
|------------------------|---------------------|----------------------|
| VATDeductionCorrection | CORR                | Purchase             |
| VATDeductionCorrection | CORR                | Purchase credit note |
