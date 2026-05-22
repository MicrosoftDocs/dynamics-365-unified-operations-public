---
title: CFDI layout version 3.3
description: Learn about Comprobante Fiscal Digital por Internet (CFDI) layout version 3.3 for Mexico, including an outline on changes introduced in this layout version.
author: ankviklis
ms.author: ankviklis
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2026
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2017-12-01
ms.search.form: CustPosting, VendParameters
---

# CFDI layout version 3.3

[!include [banner](../../includes/banner.md)]

## Electronic invoice parameters

If your organization uses electronic invoices that a third-party digital signature service provider (PAC) validates and certifies, use the fields in the **CFDI** area of the **Electronic invoice parameters** page to enable electronic invoicing.

Version 3.3 of the Comprobante Fiscal Digital por Internet (CFDI) layout introduces the following changes:

- **CFDI version:** Version 3.3 is now available.
- **CFDI digest algorithm:** SHA-256.
- **CFDI payment XML schema file:** The path and name of the schema file that is used to validate the CFDI payment complement.
- **Total amount limits:** Specify the incoming and outgoing total amount limits that require a confirmation number.
- **Default government classification codes:**

  - **SAT product code** – Use this classification for scenarios where the item code isn't identified.
  - **SAT unit code** – Use this classification for scenarios where the unit of measure isn't identified.

#### CFDI Foreign trade parameters

If your organization uses electronic invoices for foreign trade business (CFDI), enable the following information in the CFDI foreign trade area of the **Electronic invoice parameters** page:

- **Operation type:** Select **Export**.
- **CFDI version:** Select version 1.1.
- **Reporting currency:** Select the currency code that represents US dollar, as the foreign complement should be expressed in this currency.
- **CFDI Foreign trade XML schema file:** Select the path and schema file to validate the CFDI foreign trade complement.
- **Brand:** Use this field to enter the brand for scenarios where the product or service isn't identified as a Dynamics 365 Finance item code.

#### CFDI withholding parameters

If your organization uses electronic invoice withholding documents that a third-party digital signature service provider (PAC) validates and certifies, use the fields in the **CFDI Withholding** and **Number sequences** area of the **Electronic invoice parameters** page to enable electronic invoicing.

- **Enable CFDI withholding:** Select **Yes** to enable the generation of CFDI withholding.
- **CDFI XSLT file:** Path and schema file to validate the CFDI withholding document.
- **CFDI digest algorithm:** SHA-256.
- **CFDI XML schema file:** Path and schema file to validate the CFDI withholding document.
- **Send mail:** Select **Yes** to enable the action to send email with the CFDI withholding XML file attached.
- **Email ID:** Select the email ID template.
- **Number sequences:** Select the number sequence code used for Withholding journals.

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
<td>Select **Organization administration** &gt; **Setup** &gt; **Einvoice** &gt; **SAT classifications** &gt; **CFDI purpose** to enter the list of CFDI purpose classifications that the government defines. You can enter the following information: Mexican tax authorities (SAT) code classification, description, effective version, and expiration date.

Enter this information in the **CFDI purpose** field on the sales invoice transaction header. You can also define a default CFDI purpose for each customer by selecting **Customers** and using the **Invoice and delivery** option.</td>
</tr>
<tr>
<td>c_Aduana</td>
<td>Not applicable.</td>
</tr>
<tr>
<td>c_ClaveProdServ</td>
<td>Select **Organization administration** &gt; **Setup** &gt; **Einvoice** &gt; **SAT classifications** &gt; **Product and services** to enter the list of item code classifications that the government defines. You can enter the following information: SAT code classification, description, effective version, and expiration date.

After you create or update the list, map the related classification in the following master data:
<ul>
<li>**Electronic invoice parameters** in default classifications</li>
<li>**Product information** &gt; **Released products** &gt; **General** &gt; **Electronic invoices**</li>
<li>**Accounts receivable** &gt; **Setup** &gt; **Charges** &gt; **Charges code**</li>
</ul>
</td>
</tr>
<tr>
<td>c_ClaveUnidad</td>
<td>Select **Organization administration** &gt; **Setup** &gt; **Einvoice** &gt; **SAT classifications** &gt; **Unit of measures** to enter the list of unit of measure classifications that the government defines. You can enter the following information: SAT code classification, description, effective version, and expiration date.

After you create or update the list, map the related classification in the following master data:
<ul>
<li>**Organization administration** &gt; **Setup** &gt; **Units** &gt; **Units** &gt; **Electronic invoices**</li>
</ul>
</td>
</tr>
<tr>
<td>c_CodigoPostal</td>
<td>This information is identified by the ZIP Code or postal code in the address code of the customer, company, or other related address.</td>
</tr>
<tr>
<td>c_FormaPago</td>
<td>Use existing information at **Accounts receivable** &gt; **Setup** &gt; **Payment** &gt; **Method of Payment** &gt; **SAT payment**.</td>
</tr>
<tr>
<td>c_Impuesto</td>
<td>This information is determined by the **Tax type** value in the sales tax code setup.</td>
</tr>
<tr>
<td>c_MetodoPago</td>
<td>Select **Organization administration** &gt; **Setup** &gt; **Einvoice** &gt; **SAT classifications** &gt; **Method of payment** to enter the list of methods of payment that the government defines.

Enter this information in the **Payment type** field on the sales invoice transaction header. You can also define the default payment type for each customer by selecting **Customers** and using the **Invoice and delivery** option.</td>
</tr>
<tr>
<td>c_Moneda</td>
<td>Finance uses the **Currency code** value to identify this information.

The government defines the exchange rate variation that is allowed. Configure this value at **General ledger** &gt; **Setup** &gt; **Currencies** &gt; **Electronic invoices**. You can enter the **Exchange rate variation limit** value per currency.</td>
</tr>
<tr>
<td>c_NumPedimentoAduana</td>
<td>Use existing information in the **Custom Number** field on the sales invoice transaction line.</td>
</tr>
<tr>
<td>c_Pais</td>
<td>Finance uses the **Country code** value to identify this information.</td>
</tr>
<tr>
<td>c_PatenteAduanal</td>
<td>Not applicable.</td>
</tr>
<tr>
<td>c_RegimenFiscal</td>
<td>Select **Organization administration** &gt; **Setup** &gt; **Einvoice** &gt; **SAT classifications** &gt; **Tax regime** to enter the list of tax regime classifications that the government defines. You can enter the following information: SAT code classification, description, effective version, and expiration date.

After you create or update the list, map the related classification in the following master data:
<ul>
<li>Select **Organization administration** &gt; **Setup** &gt; **Organization** &gt; **Legal entities** &gt; **Tax registration**. You can then select the tax regime.</li>
</ul>
</td>
</tr>
<tr>
<td>c_TasaCuota</td>
<td>This information is determined by the **Tax type** value in the sales tax code setup.</td>
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
<td>This information is determined by the **Tax type** value in the sales tax code setup.

The sales tax code configuration identifies the **Exempt** type as **tax rate = 0.00** and **tax type = VAT**. It identifies the **TASA** type as **tax rate &lt;&gt; 0.00**.</td>
</tr>
<tr>
<td>c_TipoRelacion</td>
<td>New CFDI reference functionality has been implemented that lets users identify the various types of relations between CFDI documents. Some of these relation types are assigned automatically. Users can manually select other relationship types in specific scenarios.</td>
</tr>
<tr>
<td>c_Incoterm</td>
<td>Select **Organization administration > Setup > Einvoice > SAT classifications > Incoterm**, to introduce the list of incoterm classifications as defined by the government. Enter the following information: SAT code classification, description, version effective, and expiration date. After you create or update the list, you can map the related classification in the following master data:
<ul>
<li>**Electronic invoice parameters** in default classifications. Use this classification for Project invoice and proposals that aren't generated from sales orders.</li>
 <li>**Product information > Released products > General > Electronic invoices**</li>
 <li>**Account receivables > Sales orders and Return orders > Sales order** header</li>
 <li>**Account receivables > Free text invoice > All free text invoices** header </li>
</ul>
</tr>
<tr>
<td> c_TipoOperation</td>
<td> The only available value is **Exportacion** (Export), which you select from the **Einvoice parameters** page. </td>
</tr>
<tr>
    <td>c_Brand </td>
    <td>Use **Product Information Management > Setup >Brand** to enter the brand code. You can enter the brand code and description. </td>
</tr>
<tr>
    <td> c_FraccionArancelaria </td>
    <td> Use **Organization administration > Setup > Einvoice > SAT Classifications > Tariff fraction** to enter the list of tariff fraction classifications as defined by the government. You can enter the following information: SAT code classification, description, version effective, and expiration date. After you create or update the list, you can select the tariff fraction at the line level in a sales order line, free text invoice line, and project invoice. </td>
</tr>
<tr>
    <td> c_UnidadAduana </td>
        <td> Use **Organization administration > Setup > Einvoice > SAT Classifications > Customs unit of measure** to enter the list custom unit of measure classifications as defined by the government. You can enter the following information: SAT code classification, description, version effective, and expiration date. After you create or update the list, you can select the customs unit of measure at the line level in a sales order line, free text invoice line, and project invoice. </td>
</tr>
<tr>,
<td> c_Retenciones </>
  <td> Use **Organization administration > Setup > Einvoice > SAT classifications > Withholding type** to enter the list of withholding type classifications as defined by the government. You can enter the following information: Code, description, and the type of complement that the CFDI withholding will generate. </td>
</tr>
<tr>
 <td>c_TipoContribuyenteSujetoRetencio </>
    <td> This categorization is included in the **Vendor master data > Invoice and delivery**, where you can select the type of tax payer that is subject to withholding. </td>
</tr>

</tbody>
</table>

## CFDI reference

Users must be able to reference one or more related CFDI invoices in specific scenarios. For example, a customer might return an item if the incorrect item was received, or if the item is defective. You must then create a return order, identify the original sales invoice that you submitted, and identify the type of relation (**cTipoRelacion**) that the government defines. In this case, the relation is **03: Goods return**.

Before you post a sales invoice, you can reference the related CFDI invoice by selecting **Post > Setup > CFDI reference**.

You can select from the available list of approved CFDI invoices, or you can enter the following information:

- Universally unique identifier (UUID)
- Type of relation

When you generate a CFDI payment complement, you can also use this functionality under **Payment journals > CFDI reference**.

The following information describes how you generate a CFDI payment complement when you collect payment from a customer and apply it to an existing CFDI invoice document.

You generate CFDI payment complements from the payment journal and settlement process under the following conditions:

- You settle the journal payment with one or more invoices.
- You settle the journal settlement with one or more invoices.
- In the journal name definition, you set the journal type to **Customer payment**.

After you post the journal payment or journal settlement, the system runs the Export/Import batch process to get the related approval from PAC (third-party software).

The following additional information is required for the journal payment, depending on the method of payment that you select:

- An offset main account.
- A third-party customer bank account.
- A Registro Federal de Contribuyentes (RFC) customer bank account. To meet the legal requirements that the tax authorities established, the system adds a new field to the **Customer bank account** page.

Based on a customer's request, you can use the CFDI electronic invoice inquiry to view, email, export, or print a CFDI payment complement that you previously generated. Select **Accounts receivable > Inquiries and reports > CFDI (electronic invoices)**, and then select the **Payment** tab. The printed CFDI electronic invoice includes a two-dimensional barcode in accordance with the format for Quick Response Codes (QR codes) that is described in the International Organization for Standardization (ISO)/International Electrotechnical Commission (IEC) 18004 standard.

## Customer advance payments

This section describes the processing and setup of an advance customer payment so that you can generate and issue a CFDI electronic invoice. Per the government definition, you must follow a specific procedure when you collect advance payments from customers.

1. **CFDI advance payment** – You issue an electronic invoice to the customer for the amount of the advance that you received.
1. **CFDI invoice** – After you complete the operation and apply the advance payment, you must issue the CFDI invoice of operation and details of the CFDI advance payment UUID that you issued in step 1.
1. **CFDI advance payment reverse** – You issue an electronic invoice to reverse the advance payment that you applied.

:::image type="content" source="../media/mex-advance-payments-cfdi.png" alt-text="Screenshot of the advance payment process.":::

## Prerequisites

Use the functionality for prepayment journal vouchers to issue a CFDI advance payment. Before you submit the advance payment, complete the following prerequisites.

1. Select **Accounts receivable** > **Setup** > **Customer posting profiles**, and create a posting profile for advance payments.
1. Select **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Ledger and sales tax** > **Payment**, and follow these steps:

    1. Select the posting profile that you created earlier.
    1. If sales tax is calculated and posted when you post a prepayment journal voucher, select the **Sales tax on prepayment journal voucher** check box.

## Step 1: Issue a CFDI advance payment

1. Select **Accounts receivable** > **Journals** > **Payments** > **Payment journal** to create the advance payment.
1. Enter the lines and the related information. Include the method of payment and sales tax codes as appropriate.
1. On the **Payment** tab, select the **Prepayment journal voucher** check box.
1. Post the advance payment.
1. Select **Accounts receivable** > **Periodic** > **CFDI electronic invoices** > **Export/Import electronic invoice process** to request the digital stamp of CFDI advance payment.
1. Select **Accounts receivable** > **Inquire** > **Journals** > **CFDI electronic invoice**, and then select the **Payment** tab to inquire about the status of the CFDI advance payment. This transaction is classified in the **Document type information** field as **Prepayment**.

    > [!NOTE]
    > The system uses the following criteria to identify CFDI advance payment transactions:
    >
    > - The journal name type is set to **Customer payment**.
    > - The **Prepayment journal voucher** check box is selected.
    >
    > Any payment transaction that doesn't meet these criteria is considered a regular payment.

## Step 2: Issue a CFDI invoice together with details of the advance payment that was applied

1. Create a sales invoice transaction.
1. Before you post the invoice, settle the advance payment that you created in [Step 1: Issue a CFDI advance payment](#step-1-issue-a-cfdi-advance-payment). To settle the advance payment, use the **Open transaction settle** option.
1. On the **Post** page, verify the referenced CFDI invoice. The invoice is created automatically, and the type of relation (**cTipoRelacion**) is set to **07**.
1. Post the sales invoice.

    > [!NOTE]
    > As of this release, the government hasn't updated the schema to enable **cTipoRelacion** to be set to **07**. If you receive an error message during schema validation, you can manually select **01: Credit note** to solve the issue.

## Step 3: Issue a CFDI advance payment reverse

After the company issues a CFDI invoice for the total amount of the operation, it must submit a CFDI advance payment reverse (Egreso) for the advance payment that it settled. You automatically generate this CFDI advance payment reverse when you receive approval for the CFDI invoice that you generated in [Step 2: Issue a CFDI invoice together with details of the advance payment that was applied](#step-2-issue-a-cfdi-invoice-together-with-details-of-the-advance-payment-that-was-applied).

Based on a customer's request, you can use the CFDI electronic invoice inquiry to view, email, export, or print a CFDI payment complement that you previously generated. Select **Accounts receivable** &gt; **Inquiries and reports** &gt; **CFDI (electronic invoices)**, and then select the **Payment** tab. The printed CFDI electronic invoice includes a two-dimensional barcode in accordance with the format for QR codes that is described in the ISO/IEC 18004 standard.

You identify CFDI advance payments by a document type of **Prepayment**.

## Confirmation number

You need the confirmation number on a CFDI invoice when the total amount of the invoice or the exchange rate variation is outside the limits that the government established. In this scenario, you can specify the required confirmation in two ways:

- If the company knows that the limits are exceeded, include the confirmation code on the sales invoice transaction header.
- If you receive a rejection from PAC because the limits are exceeded, set the confirmation code for the approval process at **CFDI electronic invoice inquire** &gt; **Functions** &gt; **Set authorization code and Resend again**.

## CFDI Foreign trade

When you post a sales order, free text invoice, credit note, return order, project invoice, or project sales order as an electronic invoice CFDI layout 3.3 for a foreign customer, you can generate the foreign trade complement 1.1 by introducing the following required information to generate this complement.

### Sales order header

- **Purpose**: Select the option P01. If you don't select this option, you get a rejection from PAC services.
- **Incoterm**: Select the incoterm code established by the government in the catalog cIncoterm.
- **Foreign trade**: Select this field to generate CFDI foreign trade complement.
- **Source certificate**: The selection you make depends on free trade agreements that the Mexican government has with different countries or regions:

 	- **Unmarked (0)**: No certificate is required.
 	- **Marked (1)**: Certificate is required.

- **Certificate**: The certificate number if you define the source certificate as marked (1).

> [!NOTE]
> Use the **Registration number** and **Fiscal address** fields to submit a CFDI packing slip with foreign complement. Refer to the CFDI packing slip for the foreign complement feature.

### Line

- **CFDI electronic invoice**:
  - Consignment
  - Samples
  - Tariff Fraction: Select the tariff fraction code established by the government in the catalog cFraccionArancelaria.
  - Custom unit of measure: Select the custom unit of measure code established by the government in the catalog cUnidadAduana.

- **Brand**: Select the related brand. This information defaults from product information in case of Sales order and from electronic invoice parameters when free text invoice and project is used.

- **Product**: Tracking dimensions > Serial number: Mandatory information to specify the serial number of goods.
 
After you complete all of the required information, proceed with the regular process of CFDI 3.3 invoice generation. Refer to the CFDI 3.3 invoice layout feature that was recently released.

## CFDI packing slip

The CFDI packing slip (Traslado), previously known as Carta de Porte, is an electronic document (CFDI) that carriers use to protect goods during transport. You declare all goods when transporting them from one site to another.

You can generate the CFDI packing slip document from the following entry points:

- **Sales order > Packing slip for customers**.
- **Transfer order > Shipped from different sites.** Transfers between the same site don't generate a CFDI packing slip. This requirement applies only when you transfer goods between different locations.

Additionally, users can perform the following actions after the PAC issues and approves the CFDI packing slip:

- Manually cancel a CFDI packing slip.
- View and export a generated XML file.
- Print the CFDI packing slip in PDF format.
- Email a printable version of the CFDI packing slip.

### Customer master data

Complete the following steps to generate a CFDI packing slip from the **Customer** page.

 1. Select **Account receivables > Customer > All customers**, and select a customer record.
 1. In the customer record, on the action pane, select **Invoice and delivery > Electronic invoice**.
 1. Set the **Enable CFDI Packing slip** option as necessary. The default for this option is in **Sales order > Pack and Pick > Packing slip**.

### Sales order packing slip

Complete the following steps to generate a CFDI packing slip document from a sales order.

1. Create and confirm a sales order.
1. On the **Sales order** page, on the action pane, select **Pick and Pack > Packing slip**.
1. Select the **Enable CFDI** option to generate a CFDI packing slip.
1. Select **OK** to generate the packing slip.
1. Select **Account receivables > Periodic > CFDI - Electronic invoice > Export/Import electronic invoice process**, to request the digital stamp and issue the CFDI packing slip XML to PAC service provider.
1. Select **Account receivables > Inquire > Journals > CFDI (electronic invoice)** to review the status of the CFDI packing slip.
1. Select the **Packing slip** tab to view the status of CFDI packing slip.
1. View, email, export, or print a CFDI packing slip. The printed CFDI packing slip includes a two-dimensional bar code in accordance with the format of Quick Response Code (QR code) that is described in the standard ISO/IEC18004.

> [!NOTE]
> A foreign trade complement CFDI packing slip isn't supported for a sales order packing slip. However, it's supported in the CFDI invoice for foreign trade.

### Transfer orders

Complete the following steps to generate the CFDI packing slip document for items that are in transit from one site to another.

1. Select **Inventory management > Periodic > Transfer orders**.
1. Create a transfer order, and select the from warehouse and the to warehouse.
1. Add the related items and the quantity of items to ship.
1. On the action pane, select **Post > Ship transfer**.
1. Select **Edit lines** and then select the shipment.
1. Select **Enable CFDI** to generate the packing slip.

> [!NOTE]
> You can only generate CFDI packing slip documents from transfer orders between different sites. If the from and to warehouses belong to the same site, the **Enable CFDI** option isn't enabled because the CFDI packing slip isn't required between the same sites.

1. Select **Account receivables > Periodic > CFDI - Electronic invoice > Export/Import electronic invoice process** to request the digital stamp and issue the CFDI packing slip XML to the PAC service provider.
1. To view the status of the CFDI packing slip, select **Account receivables > Inquire > Journals > CFDI (electronic invoice)**.
1. Select the **Transfer order** tab to check the status of the CFDI packing slip.
1. View, email, export, or print the CFDI packing slip. The printed CFDI packing slip includes a two-dimensional bar code in accordance with the format of Quick Response Code (QR code) that is described in the standard ISO/IEC18004.

## CFDI withholding

The tax authorities in Mexico (SAT) established the CFDI withholding document as an electronic withholding certificate. You use it for vendor payments when you apply ISR and VAT withholding taxes.

The CFDI withholding document includes all of the information that the government requires, such as company details, vendor accounts, and the amount of related withholding taxes.

You generate CFDI withholding documents from tax transactions where the sales tax codes **IVA** and **ISR** are defined as negative in the following transaction entry points:

- Purchase invoice
- Vendor invoice (non PO)
- Invoice register
- Invoice journal
- Journal transaction in the **General Ledger** area when vendor account is present

The system defaults the withholding type from the vendor account, but you can change the withholding type during the transaction registration process.

### Periodic process

Generate a CFDI withholding document from **Accounts payables > Periodic > CFDI > Generate CFDI withholding**.
Select the vendor account and the from and to **Month/year**.

After you confirm the process, the system generates CFDI withholding documents. To request the digital stamp from the PAC service provider, select **Accounts payables > Periodic > CFDI > Export/Import CFDI withholding process**.

The system generates specific complements for the following withholding types:

- **Interest (16):** Enter additional information during the transaction registration, such as:  

  - Transaction belongs to financial system.
  - Interest cashed in the current period/year.
  - Interests belongs to derived financial operations.
  - Nominal, real interest, and loss interest amounts.

- **Foreign payments (18):** Configure additional information in the vendor master data when foreign vendor RFC of legal representative in Mexico.

> [!NOTE]
> The system doesn't currently support other complements.

### Inquire CFDI withholding documents

After you issue the CFDI withholding document to PAC, you can view the status and complete the related actions by selecting **Accounts payables > Inquire > Journals > CFDI withholding journal**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
