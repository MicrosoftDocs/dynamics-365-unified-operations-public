---
# required metadata

title: CFDI layout version 3.3
description: This topic provides information about Comprobante Fiscal Digital por Internet (CFDI) layout version 3.3 for Mexico.
author: sndray
manager: AnnBe
ms.date: 01/03/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustPosting, VendParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2017-12-01
# ms.dyn365.ops.version: 

---

# CFDI layout version 3.3

[!include [banner](../includes/banner.md)]

## Electronic invoice parameters

If your organization uses electronic invoices that are validated and certified by a third-party digital signature service provider (PAC), you enable electronic invoicing by using the fields in the **CFDI** area of the **Electronic invoice parameters** page.

The following changes are introduced in version 3.3 of the Comprobante Fiscal Digital por Internet (CFDI) layout:

- **CFDI version:** Version 3.3 is now available.
- **CFDI digest algorithm:** SHA-256.
- **CFDI payment XML schema file:** The path and name of the schema file that is used to validate the CFDI payment complement.
- **Total amount limits:** Specify the incoming and outgoing total amount limits that require a confirmation number.
- **Default government classification codes:**

    - **SAT product code** – Use this classification for scenarios where the item code isn't identified.
    - **SAT unit code** – Use this classification for scenarios where the unit of measure isn't identified.
    
#### CFDI Foreign trade parameters

If your organization uses electronic invoices for foreign trade business (CFDI), enable the following information in the CFDI foreign trade area of the Electronic invoice parameters
The following changes are introduced as part of generation of CFDI foreign trade complement

- **Operation type:** Select Export
- **CFDI version:** Select version 1.1
- **Reporting currency:** Select the currency code that represents the US Dollar since the foreign complement should be expressed in this currency
- **CFDI Foregn trade XML schema file:** Path and schema file to validate the CFDI foreign trade complement
- **Brand:** Use this field to introduce the brand for scenarios where the product or service is not identified as a Microsoft Dynamics AX item code

#### CFDI witholding parameters
If your organization uses electronic invoicwithholding documents es that are validated and certified by a third-party digital signature service provider (PAC), you enable electronic invoicing by using the fields in the **CFDI Withholding** and **Number sequences** area of the **Electronic invoice parameters** page.

-**Enable CFDI witholding:** Select Yes to enable the generation of CFDI withholding

-**CDFI XSLT file:** Path and schema file to validate the CFDI withhdolding document

-**CFDI digest algorithm:** SHA-256

-**CFDI XML schema file:** Path and schema file to validate the CFDI withhdolding  document

-**Send mail:** Select Yes to enable the action to send email with the CFDI withholding XMLfile attached

-**Email ID:** Select the email ID template

-**Number sequences:** Select the number sequence code used for Withdoling journals

## SAT catalogs

<table>
<thead>
<tr>
<th>SAT catalog</th>
<th>Dynamics 365 Finance mapping</th>
</tr>
</thead>
<tbody>
<tr>
<td>cUsoCFDI</td>
<td>Select <strong>Organization administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Einvoice</strong> &gt; <strong>SAT classifications</strong> &gt; <strong>CFDI purpose</strong> to enter the list of CFDI purpose classifications that are defined by the government. You can enter the following information: Mexican tax authorities (SAT) code classification, description, effective version, and expiration date.

This information must be entered in the <strong>CFDI purpose</strong> field on the sales invoice transaction header. You can also define a default CFDI purpose per customer by selecting <strong>Customers</strong> and using the <strong>Invoice and delivery</strong> option.</td>
</tr>
<tr>
<td>c_Aduana</td>
<td>Not applicable</td>
</tr>
<tr>
<td>c_ClaveProdServ</td>
<td>Select <strong>Organization administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Einvoice</strong> &gt; <strong>SAT classifications</strong> &gt; <strong>Product and services</strong> to enter the list of item code classifications that are defined by the government. You can enter the following information: SAT code classification, description, effective version, and expiration date.

After the list is created or updated, you can map the related classification in the following master data:
<ul>
<li><strong>Electronic invoice parameters</strong> in default classifications</li>
<li><strong>Product information</strong> &gt; <strong>Released products</strong> &gt; <strong>General</strong> &gt; <strong>Electronic invoices</strong></li>
<li><strong>Accounts receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Charges</strong> &gt; <strong>Charges code</strong></li>
</ul>
</td>
</tr>
<tr>
<td>c_ClaveUnidad</td>
<td>Select <strong>Organization administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Einvoice</strong> &gt; <strong>SAT classifications</strong> &gt; <strong>Unit of measures</strong> to enter the list of unit of measure classifications that are defined by the government. You can enter the following information: SAT code classification, description, effective version, and expiration date.

After the list is created or updated, you can map the related classification in the following master data:
<ul>
<li><strong>Organization administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Units</strong> &gt; <strong>Units</strong> &gt; <strong>Electronic invoices</strong></li>
</ul>
</td>
</tr>
<tr>
<td>c_CodigoPostal</td>
<td>This information is identified by the ZIP Code/postal code in the address code of the customer, company, or other related address.</td>
</tr>
<tr>
<td>c_FormaPago</td>
<td>Existing information at <strong>Accounts receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Payment</strong> &gt; <strong>Method of Payment</strong> &gt; <strong>SAT payment</strong> is used.</td>
</tr>
<tr>
<td>c_Impuesto</td>
<td>This information is determined by the <strong>Tax type</strong> value in the sales tax code setup.</td>
</tr>
<tr>
<td>c_MetodoPago</td>
<td>Select <strong>Organization administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Einvoice</strong> &gt; <strong>SAT classifications</strong> &gt; <strong>Method of payment</strong> to enter the list of methods of payment that are defined by the government.

This information must be entered in the <strong>Payment type</strong> field on the sales invoice transaction header. You can also define the default payment type per customer by selecting <strong>Customers</strong> and using the <strong>Invoice and delivery</strong> option.</td>
</tr>
<tr>
<td>c_Moneda</td>
<td>This information is identified by the <strong>Currency code</strong> value that is configured in Finance.

The government defines the exchange rate variation that is allowed. This value must be configured at <strong>General ledger</strong> &gt; <strong>Setup</strong> &gt; <strong>Currencies</strong> &gt; <strong>Electronic invoices</strong>. You can enter the <strong>Exchange rate variation limit</strong> value per currency.</td>
</tr>
<tr>
<td>c_NumPedimentoAduana</td>
<td>Existing information in the <strong>Custom Number</strong> field on the sales invoice transaction line is used.</td>
</tr>
<tr>
<td>c_Pais</td>
<td>This information is identified by the <strong>Country code</strong> value that is configured in Finance.</td>
</tr>
<tr>
<td>c_PatenteAduanal</td>
<td>Not applicable</td>
</tr>
<tr>
<td>c_RegimenFiscal</td>
<td>Select <strong>Organization administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Einvoice</strong> &gt; <strong>SAT classifications</strong> &gt; <strong>Tax regime</strong> to enter the list of tax regime classifications that are defined by the government. You can enter the following information: SAT code classification, description, effective version, and expiration date.

After the list is created or updated, you can map the related classification in the following master data:
<ul>
<li>Select <strong>Organization administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Organization</strong> &gt; <strong>Legal entities</strong> &gt; <strong>Tax registration</strong>. You can then select the tax regime.</li>
</ul>
</td>
</tr>
<tr>
<td>c_TasaCuota</td>
<td>This information is determined by the <strong>Tax type</strong> value in the sales tax code setup.</td>
</tr>
<tr>
<td>c_TipodeComprobante</td>
<td>This information is determined by the type of sales invoice transaction. The following types are supported for this feature:
<ul>
<li>Incoming</li>
<li>Outgoing</li>
<li>Payment</li>
</ul>
</td>
</tr>
<tr>
<td>c_TipoFactor</td>
<td>This information is determined by the <strong>Tax type</strong> value in the sales tax code setup.

The sales tax code configuration identifies the <strong>Exempt</strong> type as <strong>tax rate = 0.00</strong> and <strong>tax type = VAT</strong>. It identifies the <strong>TASA</strong> type as <strong>tax rate &lt;&gt; 0.00</strong>.</td>
</tr>
<tr>
<td>c_TipoRelacion</td>
<td>New CFDI reference functionality has been implemented that lets users identify the various types of relations between CFDI documents. Some of these relation types are assigned automatically. Users can manually select other relationship types in specific scenarios.</td>
</tr>
<tr>    
<td>c_Incoterm</td>
<td><strong>Organization administration > Setup > Einvoice > SAT classifications > Incoterm</strong>, to introduce the list of incoterm classification defined by the government. The user will be able to introduce the following information: SAT code classification, description, version effective and expiration date. Once the list is created or updated, the user will be able to map the related classification in the following master data:
<ul>
<li>Electronic invoice parameters in default classifications. This is used for Project invoice and proposals when is not generated from Sales order.
    <li>Product information > Released products> General > Electronic invoices</li>
    <li>Account receivables > Sales orders and Return orders> Sales order header</li>
    <li>Account receivables > Free text invoice  > All free text invoices > Header </li>
</ul>
</tr>
<tr>
<td> c_TipoOperation</td>
<td> Only available value is <strong>Exportacion</strong> (Export) and it's selected from Einvoice parameters </td>
</tr>
<tr>
    <td>c_Brand </td>
    <td><strong>Product Information Management > Setup >Brand</strong>, to introduce the brand code. The user will be able to introduce the following information: brand code and description. </td>
</tr>
<tr>
    <td> c_FraccionArancelaria </td>
    <td> <strong>Organization administration > Setup > Einvoice > SAT Classifications > Tariff fraction</strong> to introduce the list of tariff fraction classification defined by the government. The user will be able to introduce the following information: SAT code classification, description, version effective and expiration date. Once the list is created or updated, the user will be able to select the tariff fraction at the line level in sales order line, free text invoice lines and project invoice  </td>
</tr>
<tr>
    <td> c_UnidadAduana </td>
    <td> <strong>Organization administration > Setup > Einvoice > SAT Classifications > Customs unit of measure </strong>, to introduce the list custom unit of measure classification defined by the government. The user will be able to introduce the following information: SAT code classification, description, version effective and expiration date. Once the list is created or updated, the user will be able to select the customs unit of measureat the line level in sales order line, free text invoice lines and project invoice  </td>
</tr>
<tr>
<td> c_Retenciones </>
	<td> <strong> Organization administration > Setup > Einvoice > SAT classifications > Withholding type </strong>, to introduce the list of withholding type classification defined by the government. The user will be able to introduce the following information: Code, description, type of complement that the CFDI withholding will generates </td>
</tr>
<tr>
	<td>c_TipoContribuyenteSujetoRetencio </>
		<td> This categorization is included in the <strong>Vendor master data> Invoice and delivery </strong>, where the user will be able to select the type of tax payer subject to withholding </td>
</tr>

</tbody>
</table>

## CFDI reference

Per the legal requirement, users must be able to reference one or more related CFDI invoices in specific scenarios. For example, a customer might return items if the incorrect item was received, or if an item is defective. You must then create a return order, identify the original sales invoice that was submitted, and identify the type of relation (**cTipoRelacion**) that is defined by the government. In this case, the relation is **03: Goods return**.

Before you post a sales invoice, you can reference the related CFDI invoice at **Post** &gt; **Setup** &gt; **CFDI reference**.

You can select the available list of CFDI invoices that have been approved, or you can enter the following information:

- Universally unique identifier (UUID)
- Type of relation

When a CFDI payment complement is generated, this functionality is also available at **Payment journals** &gt; **CFDI reference**. 

The following information describes how a CFDI payment complement is generated when payment is collected from a customer and applied to an existing CFDI invoice document.

CFDI payment complements are generated from the payment journal and settlement process under the following conditions:

- The journal payment is settled with one or more invoices.
- The journal settlement is settled with one or more invoices.
- In the journal name definition, the journal type is set to **Customer payment**.

After the journal payment or journal settlement is posted, the Export/Import batch process is run to get the related approval from PAC (third-party software).

The following additional information is required for the journal payment, depending on the method of payment that is selected:

- Offset main account.
- Third-party customer bank account.
- Registro Federal de Contribuyentes (RFC) customer bank account. A new field has been added to the **Customer bank account** page to meet the legal requirements that were established by the tax authorities.

Based on a customer's request, you can use the CFDI electronic invoice inquiry to view, email, export, or print a CFDI payment complement that was previously generated. Select **Accounts receivable** &gt; **Inquiries and reports** &gt; **CFDI (electronic invoices)**, and then select the **Payment** tab. The printed CFDI electronic invoice includes a two-dimensional barcode in accordance with the format for Quick Response Codes (QR codes) that is described in the International Organization for Standardization (ISO)/International Electrotechnical Commission (IEC) 18004 standard.

## Customer advance payments

This section describes the processing and setup of an advance customer payment so that a CFDI electronic invoice can be generated and issued. Per the government definition, a specific procedure must be followed when advance payments are collected from customers.

1. **CFDI advance payment** – An electronic invoice is issued to the customer for the amount of the advance that was received.
2. **CFDI invoice** – After the operation is realized, and the advance payment is applied, the company must issue the CFDI invoice of operation and details of the CFDI advance payment UUID that was issued in step 1.
3. **CFDI advance payment reverse** – An electronic invoice is issued to reverse the advance payment that was applied.

![Advance payment process](./media/mex-advance-payments-cfdi.png "Diagram that shows the advance payment process")

## Prerequisites

You use the functionality for prepayment journal vouchers to issue a CFDI advance payment. Before you can submit the advance payment, you must complete the following prerequisites.

1. Select **Accounts receivable** &gt; **Setup** &gt; **Customer posting profiles**, and create a posting profile for advance payments.
2. Select **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters** &gt; **Ledger and sales tax** &gt; **Payment**, and follow these steps:

    1. Select the posting profile that you created earlier.
    2. If sales tax is calculated and posted when you post a prepayment journal voucher, select the **Sales tax on prepayment journal voucher** check box.

## Step 1: Issue a CFDI advance payment

1. Select **Accounts receivable** &gt; **Journals** &gt; **Payments** &gt; **Payment journal** to create the advance payment.
2. Enter the lines and the related information. Include the method of payment and sales tax codes as appropriate.
3. On the **Payment** tab, select the **Prepayment journal voucher** check box.
4. Post the advance payment.
5. Select **Accounts receivable** &gt; **Periodic** &gt; **CFDI electronic invoices** &gt; **Export/Import electronic invoice process** to request the digital stamp of CFDI advance payment.
6. Select **Accounts receivable** &gt; **Inquire** &gt; **Journals** &gt; **CFDI electronic invoice**, and then select the **Payment** tab to inquire about the status of the CFDI advance payment. This transaction is classified in the **Document type information** field as **Prepayment**.

    > [!NOTE]
    > The following criteria are used to identify CFDI advance payment transactions in the system:
    >
    > - The journal name type is set to **Customer payment**.
    > - The **Prepayment journal voucher** check box is selected.
    > 
    > Any payment transaction that doesn't meet these criteria is considered a regular payment.

## Step 2: Issue a CFDI invoice together with details of the advance payment that was applied

1. Create a sales invoice transaction.
2. Before you post the invoice, you can settle the advance payment that you created in [Step 1: Issue a CFDI advance payment](#step-1-issue-a-cfdi-advance-payment). To settle the advance payment, use the **Open transaction settle** option.
3. On the **Post** page, you can verify the referenced CFDI invoice. The invoice is created automatically, and the type of relation (**cTipoRelacion**) is set to **07**.
4. Post the sales invoice.

    > [!NOTE]
    > As of publication, the government hasn't updated the schema to enable **cTipoRelacion** to be set to **07**. If you receive an error message during schema validation, you can manually select **01: Credit note** to solve the issue.

## Step 3: Issue a CFDI advance payment reverse

After the company issues a CFDI invoice for the total amount of the operation, it must submit a CFDI advance payment reverse (Egreso) for the advance payment that was settled. This CFDI advance payment reverse is automatically generated when you receive approval for the CFDI invoice that you generated in [Step 2: Issue a CFDI invoice together with details of the advance payment that was applied](#step-2-issue-a-cfdi-invoice-together-with-details-of-the-advance-payment-that-was-applied).

Based on a customer's request, you can use the CFDI electronic invoice inquiry to view, email, export, or print a CFDI payment complement that was previously generated. Select **Accounts receivable** &gt; **Inquiries and reports** &gt; **CFDI (electronic invoices)**, and then select the **Payment** tab. The printed CFDI electronic invoice includes a two-dimensional barcode in accordance with the format for QR codes that is described in the ISO/IEC 18004 standard.

CFDI advance payments are identified by a document type of **Prepayment**.

## Confirmation number

The confirmation number is required on a CFDI invoice when the total amount of the invoice or the exchange rate variation is outside the limits that the government has established. In this scenario, you can specify the required confirmation in two ways:

- If the company knows that the limits have been exceeded, you can include the confirmation code on the sales invoice transaction header.
- If you receive a rejection from PAC because the limits have been exceeded, you can set the confirmation code for the approval process at **CFDI electronic invoice inquire** &gt; **Functions** &gt; **Set authorization code and Resend again**.

## CFDI Foreign trade
When you post a sales order, free text invoice, credit note, return order, project invoice, or project sales order as an electronic invoice CFDI layout 3.3 for a foreign customer, you will able to generate the foreign trade complement 1.1 by introducing the following information that is required for the generation of this complement. 

**Sales order header**
- Purpose: You must select the option P01 otherwise you will get a rejection from PAC services

- Incoterm: Select the incoterm code established by the government in the catalog cIncoterm

- Foreign trade: Mark this field to generate CFDI foreign trade complement

- Source certificate: Use this option . The selection will depend on free trade agreements that the Mexican government has with different countries:
		-Unmarked (0): No certificate is required
		-Marked (1): Certificate is required 
- Certificate: Certificate number in case of source certificate has been defined as marked (1)

	
Note: Registration number and fiscal address fields are used to submit CFDI packing slip with foreign complement. Please refer to CFDI packing slip foreign complement feature

**Line**
-CFDI electronic invoice:

   - Consignment
   
   - Samples
   
   - Tariff Fraction: Select the tariff fraction code established by the government in the catalog cFraccionArancelaria.
   
   - Custom unit of measure: Select the custom unit of measure code established by the government in the catalog cUnidadAduana.
   
- Brand: Select the related brand. This information is defaulted from product information in case of Sales order and from electronic invoice parameters when free text invoice and project is used.

- Product: Tracking dimensions > Serial number: Mandatory information to specify the serial number of goods. 
	
After you completed all the required information, you need to proceed with the regular process of CFDI 3.3 invoice generation. Please refer to CFDI 3.3 invoice layout feature recently released.

## CFDI Packing slip

CFDI packing slip (Traslado) previously known as Carta de Porte, is an electronic document (CFDI) in which is declared all goods when are transported from one site to other site and is required by the carrier to protect the goods.

CFDI packing slip document is generated from the following entries points:
- **Sales order -> Packing slip for customers**. 
- **Transfer order -> Shipped from different sites.** Transfers between the same site will not go to generate a CFDI packing slip, since this requirement is mandatory when the goods are transferred between different locations.

In addition to this, users will be able to execute the following actions when the CFDI packing slip is issued and approved by the PAC:
- Manually cancel CFDI packing slip.
- View and Export an XML file generated.
- Print a pdf version of CFDI packing slip.
- Send e-mail of printable version of CFDI packing slip.


#### Customer master data

You can specify the generation of CFDI packing slip from customer form.
 1. Account receivables > Customers > All customers and select the customer;
 2.  Invoice and delivery > Electronic invoice;
 3. Mark and unmark Enable CFDI Packing slip. This option is defaulted in Sales order > Pack and Pick > Packing slip.
 
#### Sales order packing slip
 
CFDI packing slip document is generated from the sales order by executing the following steps:
1. Create a Sales order and confirm;
2. Pick and Pack > Packing slip;
3. Enable CFDI checkbox to generate a CFDI packing slip;
4. Press OK to confirm the generation of packing slip;
5. Request the digital stamp in Account receivables > Periodic > CFDI - Electronic invoice > Export/Import electronic invoice process, to issue the CFDI packing slip XML to PAC service provider;
6. Inquire the status of CFDI packing slip on Account receivables > Inquire > Journals > CFDI (electronic invoice);
7. Check the status of CFDI packing slip in the Packing slip tab;
8. View, email, export, or print a CFDI packing slip. The printed CFDI packing slip includes two-dimensional bar code in accordance with the format of QR Code (Quick Response Code) that is described in the standard ISO/IEC18004.

Note Foreign trade complement CFDI packing slip is not supported in this feature. This functionality is supported in CFDI invoice for Foreign trade.

#### Transfer orders

CFDI packing slip document for items in transit from specific site to another site is generated by executing the following steps:  
1. Inventory management > Periodic > Transfer orders;
2. Create a transfer order and select the warehouse from and warehouse to;
3. Introduce the related items and the quantity to ship;
4. Post > Ship transfer;
5. Edit lines to select the shipment;
6. Mark Enable CFDI to generate CFDI packing slip document.

Note CFDI packing slip documents are only generated from Transfers orders between different sites. This means that if the warehouse from and warehouse to belong to the same site, the Enable CFDI checkbox remains as disable because CFDI packing slip is not mandatory between same sites.

7. Request the digital stamp in Account receivables > Periodic > CFDI - Electronic invoice > Export/Import electronic invoice process, to issue the CFDI packing slip XML to PAC service provider;
8. Inquire the status of CFDI packing slip on Account receivables > Inquire > Journals > CFDI (electronic invoice);
9. Check the status of CFDI packing slip in the Transfer order tab;
10. View, email, export, or print a CFDI packing slip. The printed CFDI packing slip includes two-dimensional bar code in accordance with the format of QR Code (Quick Response Code) that is described in the standard ISO/IEC18004.
 
 
 ## CFDI Withholding
 
CFDI withholding document is an electronic withholding certificate established by the tax authorities in Mexico (SAT) and applicable for vendor payments when ISR and VAT withholding taxes are applied.

The CFDI withholding document includes all information required by government as company details, vendor account and amount of withholding taxes related.

CFDI withholding documents will be generated from tax transactions where the sales tax codes **IVA** and **ISR** tax type are defined as Negative in the following transactions entry points:
- Purchase invoice;
- Vendor invoice (non PO);
- Invoice register;
- Invoice journal;
- Journal transaction in General Ledger module when vendor account is present.

Withholding type is defaulted from the vendor account and the user can change the withholding type during the transaction registration process.

#### Periodic process
The generation of CFDI withholding document is performed from Accounts payables > Periodic > CFDI > Generate CFDI withholding.
The user can select the vendor account, from and to **Month/year**

After the process if confirmed, CFDI withholding documents are generated and the user must to start the process to request the digital stamp to PAC service provider, **Accounts payables > Periodic > CFDI > Export/Import CFDI withholding process.**

Specific complements are generated for the following withholding types:
- **Interest (16).** Additional information is required during the transaction registration as:  
    - Transaction belongs to financial system;
    - Interest cashed in the current period/year;
    - Interests belongs to derived financial operations;
    - Nominal, real interest and loss interest amounts.
- **Foreign payments (18).** Additional information must be configured in the vendor master data when foreign vendor RFC of legal representative in Mexico.

Note Other complement are not currently supported in this feature.

#### Inquire CFDI withholding documents

After the CFDI withholding document is issued to PAC, you can inquire the status and perform the related actions in **Accounts payables >Inquire > Journals > CFDI withholding journal.**



