---
# required metadata

title: CFDI Version 3.3
description: This topic provides information about the CFDI layout version 3.3 for Mexico.
author: sndray
manager: AnnBe
ms.date: 11/02/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2017-12-01
# ms.dyn365.ops.version: 

---

# Adjustment inflation declaration report

[!include[banner](../includes/banner.md)]



## Electronic invoice parameters
If your organization uses electronic invoices that are validated and certified by a third-party digital signature service provider (PAC), enable the electronic invoicing by using the fields in the CFDI area of the Electronic invoice parameters form.
The following changes are introduced as part of changes in layout version 3.3:
- CFDI version. Version 3.3 is now available.
- CFDI digest algorithm. SHA-256.
- CFDI payment XML schema file. Path and schema file to validate the CFDI payment complement.
- Total amount limits. Identify the incoming and outgoing total amount limits that requires confirmation number.
- Default government classification codes: 
  - SAT product code. Use this classification for scenarios where the item code is not identified.
  - SAT unit code. Use this classification for scenarios where the unit of measure is not identified.
  
##  SAT catalogs

<table>
		<tr><td>SAT Catalogs
			</td>
			<td>
			Microsoft Dynamics AX mapping
			</td>
		</tr>
		<tr>
			<td>cUsoCFDI</td>
			<td>
			<p><strong>Organization administration &gt; Setup &gt; Einvoice &gt; SAT classifications &gt; CFDI purpose</strong>, to introduce the list of CFDI purpose classification defined by the government. The user will be able to introduce the following information: SAT code classification, description, version effective and expiration date.</p>
			<p>This information must be identified into the&nbsp;Sales invoice transaction header under the <strong>CFDI purpose </strong>field. The user can also define the default&nbsp;<strong>CFDI purpose </strong>per customer in <strong>Customers &gt; Invoice and delivery </strong>option.</p>
			</td>
		</tr><tr>
			<td>c_Aduana</td>
			<td>Not applicable for this feature.</td>
		</tr>
		<tr>
			<td>c_ClaveProdServ</td>
			<td>
			<p><strong>Organization administration &gt; Setup &gt; Einvoice &gt; SAT classifications &gt; Product and services</strong>, to introduce the list of item code classification defined by the government. The user will be able to introduce the following information: SAT code classification, description, version effective and expiration date.</p>
			<p>Once the list is created or updated, the user will be able to map the related classification in the following master data:</p>
			<ul>
				<li><strong>Electronic invoice parameters </strong>in default classifications.</li>
				<li><strong>Product information &gt; Released products&gt; General &gt; Electronic invoices</strong></li>
				<li><strong>Account receivables &gt; Setup &gt; Charges &gt; Charges code</strong></li>
			</ul>
			</td>
		</tr>
		<tr>
			<td>c_ClaveUnidad</td>
			<td>
			<p><strong>Organization administration &gt; Setup &gt; Einvoice &gt; SAT classifications &gt; Unit of measures</strong>, to introduce the list of unit of measure classification defined by the government. The user will be able to introduce the following information: SAT code classification, description, version effective and expiration date.</p>
			<p>Once the list is created or updated, the user will be able to map the related classification in the following master data:</p>
			<ul>
				<li><strong>Organization administration &gt; Setup</strong> &gt; <strong>Units</strong> &gt; <strong>Units &gt; Electronic invoices </strong></li>
			</ul>
			</td>
		</tr>
		<tr>
			<td>c_CodigoPostal</td>
			<td>Identified by the ZIP code in the address code of customer, company or other related address.</td>
		</tr>
		<tr>
			<td>c_FormaPago</td>
			<td>Existing information in <strong>Account&nbsp;receivables &gt; Setup &gt; Payment &gt; Method of Payment &gt; SAT payment</strong>.</td>
		</tr>
		<tr>
			<td>c_Impuesto</td>
			<td>
			<p>Determined by the <strong>Tax type </strong>in Sales tax code setup.</p>
			</td>
		</tr>
		<tr>
			<td>c_MetodoPago</td>
			<td>
			<p><strong>Organization administration &gt; Setup &gt; Einvoice &gt; SAT classifications &gt; Method of payment, </strong>to introduce the list of method of payments defined by the government.</p>
			<p>This information must be identified into the&nbsp;Sales invoice transaction header under the <strong>Payment type</strong> field. The user can also define the default payment type per customer in <strong>Customers &gt; Invoice and delivery </strong>option.</p>
			</td>
		</tr>
		<tr>
			<td>cMoneda</td>
			<td>
			<p>Identified by the <strong>Currency code </strong>configured in Microsoft Dynamics AX.</p>
			<p>The allowed exchange rate variation defined by the government must configured in <strong>General ledger &gt; Setup &gt; Currencies &gt; Electronic invoices</strong>. You will be able to introduce the <strong>Exchange rate variation</strong> <strong> limit</strong> per currency.</p>
			</td>
		</tr>
		<tr>
			<td>c_NumPedimentoAduana</td>
			<td>Existing information in the Sales invoice transaction line in the&nbsp;<strong>Custom Number</strong> field.</td>
		</tr>
		<tr>
			<td>cPais</td>
			<td>Identified by the <strong>Country code </strong>configured in Microsoft Dynamics AX.</td>
		</tr>
		<tr>
			<td>c_PatenteAduanal</td>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td>cRegimenFiscal</td>
			<td>
			<p><strong>Organization administration &gt; Setup &gt; Einvoice &gt; SAT classifications &gt; Tax regime</strong>, to introduce the list of tax regime classification defined by the government. The user will be able to introduce the following information: SAT code classification, description, version effective and expiration date.</p>
			<p>Once the list is created or updated, the user will be able to map the related classification in the following master data:</p>
			<ul>
				<li><strong>Organization administration &gt; Setup</strong> <strong>&gt;Organization &gt; Legal entities &gt; Tax registration</strong>. You will bale to select the tax regime.</li>
			</ul>
			</td>
		</tr>
		<tr>
			<td>cTasaCuota</td>
			<td>Determined by the <strong>Tax type </strong>in Sales tax code setup.</td>
		</tr>
		<tr>
			<td>cTipodeComprobante</td>
			<td>
			<p>Determined by the type of Sales invoice transaction. The support types for this feature are:</p>
			<ul>
				<li>Incoming</li>
				<li>Outgoing</li>
				<li>Payment</li>
			</ul>
			</td>
		</tr>
		<tr>
			<td>cTipoFactor</td>
			<td>
			<p>Determined by the <strong>Tax type </strong>in Sales tax code setup.</p>
			<p><strong>Exempt&nbsp;</strong>type is identified by&nbsp;the sales tax code configuration as <strong>tax rate = 0.00 </strong>and <strong>tax type = VAT</strong>.</p>
			<p><strong>TASA </strong>type identified by sales tax code configuration with <strong>tax rate &lt;&gt; 0.00</strong>.</p>
			</td>
		</tr>
		<tr>
			<td>cTipoRelacion</td>
			<td>New functionality has been implemented<strong> CFDI reference </strong>to allow users to identify the different types of relations between CFDI documents. Some of them are assigned automatically, and others scenarios will allow manually selection by the user.</td>
		</tr>
</table>
