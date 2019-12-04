<p>
	<strong>SPED Fiscal 2020: Complementary information of the ICMS-ST for Sped fiscal 2020 layout 014</strong>
</p>
<p>For the Companies who want to utilize the complement &amp; compensation of ICMS-ST for calendar year 2020, they need to start registering the complementary information of ICMS-ST during receiving of electronic fiscal documents model 55 from Jan 1st 2020 onwards.</p>
<p>&nbsp;</p>
<p>Only for Microsoft Dynamics 365 Finance, this feature must be previously enabled throughout Feature Management. In order to enable it:</p>
<ol>
	<li>Go to Home;</li>
	<li>Click on Feature Management on the dashboard;</li>
	<li>Search feature Complementary information of ICMS-ST and select it;</li>
	<li>Click on button Enable Now.</li>
</ol>
<p>&nbsp;</p>
<p>Whenever the vendor fiscal document, or transfer fiscal document have on some of its lines a product subject to ICMS-ST taxation on the UF (state) of the destination address, if the receiving fiscal establishment utilizes the complement &amp; compensation of ICMS-ST, then the following attributes of the fiscal document must be entered.</p>
<p>&nbsp;</p>
<ul>
	<li>Who was the responsible for withholding the ICMS-ST:
		<ul>
			<li>Direct: when the third party or the fiscal establishment issuer of the fiscal document was the direct responsible for withholding the ICMS-ST for the product present in the fiscal document;</li>
			<li>Indirect: when the third party or the fiscal establishment issuer of the fiscal document already received the product with withheld ICMS-ST from its supply chain;</li>
			<li>Own declarant: when the receiving fiscal establishment becomes responsible for withholding the ICMS-ST that should have been withheld by the third party issuer, but for some reason, was not.</li>
		</ul>
	</li>
	<li>The ICMS-ST collection payment mode:
		<ul>
			<li>State document of collection: when the due ICMS-ST is withheld through the regular ICMS-ST tax assessment and payment after the end of the transaction period;</li>
			<li>GNRE: when the receiving fiscal document is accompanied by a GNRE demonstrating the due ICMS-ST was already withheld and paid at the origin, by the fiscal document issuer.</li>
		</ul>
	</li>
	<li>The ICMS-ST collection payment number: the number of GNRE used to settle the ICMS-ST payment amount by the fiscal document issuer.</li>
</ul>
<p>&nbsp;</p>
<p>For a given fiscal document line with a product subject to ICMS-ST on the receiving destination, the responsible for withholding the ICMS-ST will be determined by looking at the taxation code of the ICMS-ST in the receiving fiscal document and comparing towards the equivalent ICMS-ST line in present in the NF-e XML issued by the sender of the fiscal document, as shown in figure 1 and 2</p>
<p>&nbsp;</p>
<img src="https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Complementary-information-ICMS-ST-Sped-fiscal/articles/finance/localizations/media/Complementary%20Information%20of%20ICMS-ST%20SPED%20Fiscal%202020-Figure%2001.PNG" width="800" height="320">
<p style="text-align: center;">Figure 1</p>
<p style="text-align: left;">&nbsp;</p>
<img src="https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/Complementary-information-ICMS-ST-Sped-fiscal/articles/finance/localizations/media/Complementary%20Information%20of%20ICMS-ST%20SPED%20Fiscal%202020-Figure%2002.PNG" width="800" height="320">
<p style="text-align: center;">Figure 2</p>
<p>Nevertheless, a default value for the Responsible for withholding the ICMS-ST can be set up at:</p>
<ol>
	<li>Go to Tax &gt; Set up &gt; Sales tax &gt; Responsible for withholding the ICMS-ST</li>
	<li>On CFOP Code field, select Table, Group or All;</li>
	<li>On CFOP Relation field, enter the relation defined by CFOP Code;</li>
	<li>On Fiscal document issuer field, select Fiscal establishment or Third party to define the origin of the fiscal document;</li>
	<li>On Receiver taxation code field, enter the taxation code of the ICMS-ST configured for the receiving fiscal document line, where the product is subject to ICMS tax substitution;</li>
	<li>On Sender taxation code field, enter the taxation code of the ICMS-ST present in the issuer's fiscal document line, where the product is subject to ICMS tax substitution;</li>
	<li>For a give CFOP relation and Fiscal document issuer, and based on the relation between the Receiver taxation code vs the Sender taxation code, Enter on Responsible for withholding the ICMS-ST field, select Direct, Indirect or Own declarant.</li>
</ol>
<p>&nbsp;</p>
<p>The Responsible for withholding the ICMS-ST, the ICMS-ST collection payment mode and ICMS-ST collection payment number are new fields at:</p>
<ul>
	<li>Vendor invoices form, at Fiscal information tab;</li>
	<li>Transfer order form, at Fiscal information of receiving tab;</li>
	<li>Customer invoice form, at Fiscal information tab only for customer returns.</li>
</ul>
<p>&nbsp;</p>
<p>Note:</p>
<p style="text-align: left;">Operations where the ICMS-ST is taxable during receiving (taxation code = 10), although can be captured by the new field Responsible for withholding ICMS-ST, the further treatment of accounting, financial and costing remains out of scope of localization.</p>
