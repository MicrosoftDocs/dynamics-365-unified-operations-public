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

## CFDI Reference
As per legal requirement, user must be able to reference one or more CFDI invoices related under specific scenarios. For example, a customer might return items if the incorrect item was received, or if an item is defective. You must create a return order and also identify the original sales invoice that was submitted before and identify the type of relation (cTipoRelacion) defined by the government, in this case 03: Goods return.
Before to post a Sales invoice, the user will be able to reference the related CFDI invoice under the following path: Post > Setup > CFDI reference button
User can select the available list of CFDI invoice approved or can enter manually the following information:
UUID
Type of relation
This functionality is also available in Payment journals > CFDI reference when CFDI payment complement is generated as well. 

This process describes the processing of CFDI payment complement generation when a payment is collected from customer and applied to an existing CFDI invoice document.
CFDI payment complement are generated from the payment journal and settlement process under the following criterias:
Journal payment settled with one or more invoices;
Journal settlement, settled with one or more invoices;
Journal name must be defined with journal type = Customer payment.
Once the journal payment or journal settlement is posted, and then Export/Import batch process is executed to get the related approval from PAC (third party software).
Some addition information will be required for journal payment depending on the method of payment selected:
Offset main account;
Third party customer bank account;
RFC customer bank account. We introduced a new field into the Customer bank account form to fulfill the legal requirements established by the tax authorities.
Use the CFDI electronic invoice inquire to view, email, export, or print an already-generated CFDI payment complement based on a customer’s request. The printed CFDI electronic invoice includes two-dimensional bar code in accordance with the format of QR Code (Quick Response Code) that is described in the standard ISO/IEC18004. Go to Accounts receivable > Inquiries and reports > CFDI (electronic invoices) > Payment tab.


## Customer advance payments
This process describes the processing and setup of advanced customer payment to generate and issue a CFDI electronic invoice.
As per government definition, there is an specific process to follow when advance payments are collected from customers.
CFDI advance payment. Issuance of an electronic invoice to the customer for the amount of the advance received
CFDI Invoice. Once the operation is realized and advance payment is applied, the company must issue the CFDI invoice of operation, and details the CFDI advance payment UUID issued in the step one.
CFDI Invoice reverse. Issuance of an electronic invoice to reverse the Advance payment applied.

## Prerequisites
Use prepayment journal vouchers functionality to issue CFDI advance payment. Before to submit, the CFDI additional configuration is required to fulfill the step 1 detailed in previous section.
Accounts receivable > Setup > Customer posting profiles, create and Advance payment profile.
Accounts receivable > Setup > Accounts receivable parameters > Ledger and sales tax > Payment
Select the posting profile created before.
If sales tax is calculated and posted when you post a prepayment journal voucher, select the Sales tax on prepayment journal voucher check box.
Issuing CFDI for Advance payment - Step 1
Click Accounts receivable > Journals > Payments > Payment journal to create the advance payment.
Introduce the lines and the related information. Include the Method of payment and Sales tax codes is applicable.
On the Payment tab, select the Prepayment journal voucher check box.
Post the Advance payment.
Click Accounts receivable >Periodic > CFDI electronic invoices > Export/Import electronic invoice process, to request the digital stamp of CFDI advance payment.
Click Accounts receivable > Inquire > Journals > CFDI electronic invoice > Payment tab, to inquire the status of CFDI advance payment. This transaction is classified in Document type information as Prepayment.
Note
CFDI Advance payment transactions are identified in the system by the following criterias, Journal name type = Customer payment and Prepayment journal voucher marked. Otherwise, the payment transaction is considered as regular payment
 
Issuing CFDI invoice with Advance application - Step 2
Create a sales invoice transaction.
Before to post the invoice, you can settle the advance payment created in the step 1, by using the Open Transaction settle option.
In the Post form, you can check the referenced CFDI invoice. It has been created automatically with cTipoRelacion = 07.
Post the Sales invoice and proceed with the regular process.
Note
At the time we released this KB, the government has not updated the schema to allow cTipoRelacion = 07. In case of getting error schema validation, you can select manually the option 01: Credit note to solve the issue.
 
Issuing CFDI Advance reverse - Step 3
After the company issue a CFDI for the total amount of operation, the company needs to submit another CFDI Advance reverse ( Egreso) for the advance payment settled.
This CFDI advance reverse is generated automatically when we get the approval of CFDI generated in step 2. No additional actions are required from the user point of view.
Use the CFDI electronic invoice inquire to view, email, export, or print an already-generated CFDI advance payment based on a customer's request. The printed CFDI electronic invoice includes two-dimensional bar code in accordance with the format of QR Code (Quick Response Code) that is described in the standard ISO/IEC18004. Go to Accounts receivable > Inquiries and reports > CFDI (electronic invoices) > Payment tab.
CFDI Advance payment are identified with the document type = Prepayment.
Confirmation number
The confirmation number in a CFDI invoice is required when the total amount of invoice or exchange rate vairaiton is out of range of limits established by the government. Under this scenario, it is required a specific confirmation code that could be included in two ways.
If the company knows that exceed the limits, you can include the confirmation code in the header of sales invoice transaction.
If you receive a Rejection from PAC because the limits, you can set the confirmation code in CFDI electronic invoice inquire > Functions > Set authorization code and Resend again for the approval process.
