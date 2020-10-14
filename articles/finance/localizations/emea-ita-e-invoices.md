---
# required metadata

title: Customer electronic invoices
description: This topic provides information about management of customer electronic invoices for Italy.
author: v-oloski
manager: 
ms.date: 08/26/2020
ms.topic: article
ms.: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Italy
# ms.search.industry: 
ms.author: v-oloski

---

# Customer electronic invoices

[!include [banner](../includes/banner.md)]

This topic describes how to set up and work with the functionality for creating and sending sales and project invoices in an electronic format (FatturaPA).

Version 1.2 of FatturaPA electronic invoices can be used for all types of businesses, including public administrations, private companies, and professionals.

> [!NOTE]
> The primary address of the legal entity must be in Italy.

This topic contains the following information:

- [Setup information](#setup)
- [How to fill in data for output of a tender procedure identification code (Codice Identificativo di Gara \[CIG\]) and unique project code (Codice Unico di Progetto \[CUP\])](#releteddoc)
- [Overview of the Electronic invoice register](#einvoiceregister)
- [Additional functionality that affects the XML file](#additionalfunctionality)
- [Functionality that is available in monthly update 10.0.12 and later versions](#fatturaPA)

## <a name="setup"></a>Setup

Before you can begin to work with the electronic invoice functionality, the following data must be set up:

- [Accounts receivable parameters](#arparameters)
- [Electronic invoice parameters](#einvoicesparameters)
- [Electronic document properties](#edproperties)
- [Customers](#customers)
- [Items (filling CodiceArticolo block)](#items)
- [Digital certificates](#digitalcert)
- [Optional: Destination for XML file output](#destination)

### <a name="arparameters"></a>Accounts receivable parameters

Select the configurations that are used to create electronic invoice XML files for sales and free text invoices, sales and free text credit notes,
project invoices, and project credit notes. You can find these configurations on the **Electronic document** tab of the **Accounts receivable parameters** page (**Accounts receivable** \> **Setup** \> **Accounts receivable parameters**).

![Electronic document tab of the Accounts receivable parameters page](media/emea-ita-electronic-invocies-AR-parameter-e-invoices.png)

> [!NOTE]
> The configurations must be imported before they can be selected. For more information, see [Download ER configurations from the Global repository of Configuration service](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

### <a name="einvoicesparameters"></a>Electronic invoice parameters

Use these parameters to specify business scenarios and company-specific information.

1. Go to **Accounts receivable** \> **Setup** \> **Electronic invoice parameters**.
2. On the **General** tab, specify the electronic signature requirement.
3. On the **Company information** tab, specify the company information and tax representative, as required. This information overrides the information in the legal entity record.
4. On the **Art. 2250 Civil code registration** tab, provide any required information if the company is registered under the terms of Article 2250 of the Italian Civil Code.
5. On the **Number sequences** tab, fill in number sequences for the **eInvoice unique file number** and **eInvoice transmission number** references.

### <a name="edproperties"></a>Electronic document properties

The functionality for electronic document properties is used to set up the output to XML document blocks for different business cases. Here are some examples:

- A value-added tax (VAT) registration number for customers who aren't in the European Union (EU) and don't have VAT registration codes
- A certified email address (posta elettronica certificata \[PEC\]) for private companies or professionals
- A stamp duty (payable and not payable by the customer)
- Data about a customer's representative

For the functionality to work, the following data must be set up:

- Electronic document property types (**Accounts receivable** \> **Setup** \> **Electronic document property types**) and the table that each document property type is applicable to. For electronic invoice functionality, the **Customers** and **Legal entities** tables are used.

    ![Setting applicability on the Electronic document property types page](media/emea-ita-electronic-invocies-electronic-document-property-types.png)

- Required values in the specified tables at the customer and legal entity levels:

    - **Customer:** Go to **Accounts receivable** \> **Customers** \> **All customers**, and then, on the Action Pane, on the **Customer** tab, select **Electronic document properties**.
    - **Legal entity:** Go to **Organization administration** \> **Organizations** \> **Legal entities**, and then, on the Action Pane, select **Electronic document properties**.

The specified values are used for output to the XML file blocks. The following table provides information about how and where those values are used.

| Business scenario | Electronic document property type | Electronic document property type description | Applicability (table) | Where to use the values | Element in the XML file |
|-------------------|-----------------------------------|-----------------------------------------------|-----------------------|--------------|-------------------------|
| Customers who are outside the EU and don't have VAT registration codes. For these customers, the VAT registration number should be **00000000000**. | VATnonEU | Example: **Customer, non-EU VAT number** | **CustTable** (Customers) | In customer electronic document properties, set the **Value** field to **00000000000**. | **IdCodice** (**CessionarioCommittente\\DatiAnagrafici\\IdFiscaleIVA** block) |
| Certified email address (PEC) for private companies or professionals | PEC | Example: **Customer, Certified e-mail address** | **CustTable** (Customers) | In customer electronic document properties, set the **Value** field to **\<PEC\>**. | **PECDestinatario** (**DatiTrasmissione** block) |
| Stamp duty that isn't included in the invoice total for sales invoices, and that is or isn't included for project invoices | Bollo<p><strong>Note:</strong> This document property type is used for sales order invoices, free text invoices, and project invoices.</p> | Example: **Stamp duty, included/not included into invoice totals** | **CompanyInfo** (Legal entities) | In legal entity electronic document properties, set the **Value** field to **\<Charge code/project category that is used for stamp duties\>**:<ul><li>**Charge code** – The debit type for this charge code should be **Ledger**.</li><li>**Project category** – This project category should be billable.</li></ul> | **ImportoBollo** (**DatiBollo** block) |
| Stamp duty that is included in the invoice total | BolloPay<p><strong>Note:</strong> This document property type is used only for sales order invoices and free text invoices.</p> | Example: **Stamp duty, included into invoice totals** | **CompanyInfo** (Legal entities) | In legal entity electronic document properties, set the **Value** field to **\<Charge code/project category that is used for stamp duties\>**:<ul><li>**Charge code** – The debit type should be **Customer/Vendor**.</li></ul> | **ImportoBollo** (**DatiBollo** block) |
| Representative | TaxRepPaese, TaxRepCodice, TaxRepDenominazione, TaxRepNome, TaxRepCognome | Any description | **CustTable** (Customers) | In customer electronic document properties, set the **Value** field to **IT** for the **TaxRepPaese** document property type. For other types, fill in data for the representative. | **Cognome** (**RappresentanteFiscale** block) |
| Invoice types | DocumentType | Example: **Invoice, document type** | **CustInvoiceJour** (Customer invoice journal), **ProjInvoiceJour** (Project invoice) | Go to **Accounts receivable \> Inquiries and reports \> Invoices \> Invoice journal** or **Project management and accounting \> Project invoices \> Project invoices**, and set the **Value** field to a document type, such as **TD16**. | **TipoDocumento** (**DatiGeneraliDocumento** block) |

> [!NOTE]
> The preceding table uses the following shorthand:
>
> - "Customer electronic document properties" refers to the **Electronic document properties** page that is opened by selecting **Electronic document properties** on the **Customer** tab on the Action Pane of the **All customers** page (**Accounts receivable \> Customers \> All customers**).
> - "Legal entity electronic document properties" refers the **Electronic document properties** page that is opened by selecting **Electronic document properties** on the Action Pane of the **Legal entities** page (**Organization administration \> Organizations \> Legal entities**).
> 
> On the **Electronic document property types** list page, the **Description** field is automatically filled in when a user enters information in the **Group description** and **Description** fields.
>
> The electronic document property type must have the same code that is specified in the table.

#### Use project categories for stamp duty

Go to **Project management and accounting** \> **Setup** \> **Categories** \> **Project categories** to set up project categories that have a transaction type of **Fee** or **Expense**. The category ID should equal the value that is defined for the **Bollo** document property type at the legal entity level. For more information, see the previous table.

The project category of the **Fee** transaction type can be used only for stamp duty that is included in the invoice. The project category of the **Expense** transaction type can be used for both stamp duty that is included in a customer invoice and stamp duty that isn't included. In both cases, the **Bollo** document property type is used.

When you create **Fee** or **Expense** journal lines, select the category that was defined for stamp duty, and enter a cost price. The system considers this cost price the stamp duty amount. If you enter a sales price that equals the cost price amount, the system considers this amount included in invoice totals. The sales price amount equals 0 (zero), and the transaction isn't included in invoice totals.

> [!NOTE]
> You can use only one of the journal types (**Fee** or **Expense**) for stamp duty. A company that uses only payable stamp duty can use the **Fee** journal type. If a company uses both payable and non-payable stamp duty, it's better to use the **Expense** journal type.

### <a name="customers"></a>Customers

#### Authority office field

You can find the **Authority office** field on the **Sales demographics** FastTab of a customer record (go to **Accounts receivable** \> **Customers** \> **All customers**, and open the customer record in **Edit** mode).

The value of this field is used to define the type of communication (business to government \[B2G\] or business to business \[B2B\]):

- If the length of the value is 6, the customer is considered a public administration (the transmission format equals **FPA12**).
- If the length of the value is 7, the customer is considered a private company or professional (the transmission format equals **FPR12**).

In both cases, the system enters the value of this field in the **CodiceDestinatario** tag in the XML file.

![Authority office field on the Sales demographics FastTab of a customer record](media/emea-ita-electronic-invocies-customer-authority-office.png)

If the **Authority office** field is blank, the system considers the customer a private company or professional (the transmission format equals **FPR12**) and enters **0000000** in the **CodiceDestinatario** tag in the XML file. In this case, a certified e-mail address (PEC) should be set up. For more information, see the table in the [Electronic documents properties](#edproperties) section earlier in this topic.

#### Activate automatic creation of e-invoices

Go to **Accounts receivable** \> **Customers** \> **All customers**, and open a customer record in **Edit** mod. Then, on the **Invoice and delivery** FastTab, in the **E-invoice** section, find the **eInvoice register** option. If this option is set to **Yes**, the system automatically creates the record on the **Electronic customer invoices** list page. For more information, see [Electronic invoice register](#einvoiceregister).

![E-invoice section on the Invoice and delivery FastTab of a customer record](media/emea-ita-electronic-invocies-customer-e-invoice.png)

In the **E-invoice** section, you can also set the **eInvoice attachment** option to **Yes**. In this case, after you print an invoice (either during or after posting), the system automatically attaches the PDF file to the invoice and eInvoice (see [Electronic invoice register](#einvoiceregister)), and the file is included in the XML file (**Allegatti** block).

### <a name="items"></a>Items (filling CodiceArticolo block)

**CodiceArticolo** block is filled in on base of item bar code or external item decription (**Product information management** \> **Products** \> **Released products**,tab **Sell**, **Related information**). **Customer relation**, **External item number**, **Description** and **External item text** should be filled in on **External item description** page.   

**CodiceTipo** field is filled in on following conditions:
- If Item bar code is filled in the item the this field is fillig with "EAN"
- If Item bar code is not filled in the item and external item description exists for this item and the customer then this field is filling with the value in Description field
- If Item bar code is not filled in the item and external item description does not exist for this item then this field is filling with "Codice Art. fornitore"

**CodiceValore** field is filled in on following conditions:
- If Item bar code is filled in the item the this field is fillig with theItem bar code
- If Item bar code is not filled in the item and external item description exists for this item and the customer then this field is filling with the value in External item number field
- If Item bar code is not filled in the item and external item description does not exist for this item then this field is filling with Item number 


### <a name="digitalcert"> </a>Digital certificates

Go to **Accounts receivable** \> **Setup** \> **Electronic signature certificates** to electronically sign electronic invoices by using a certificate of either the **Company** type or the **User** type.

![Electronic signature certificates page](media/emea-ita-electronic-invocies-certificate.png)

The party that is issuing invoices must use a qualified signature certificate to sign each FatturaPA file that is transmitted to the Exchange System - **SDI** (*Sistema di Interscambio*). A qualified signature certificate can be obtained from one of the certifiers in the [list of authorized certifiers](http://www.digitpa.gov.it/firma-digitale/certificatori-accreditati).

Microsoft Dynamics 365 Finance supports the **XAdES-BES** signature format. To enable Finance to support FatturaPA, follow these steps.

1. On client computers, in the **Application server machine** field of the **Personal** node, install and configure digital certificates that have private and public keys.

    > [!NOTE]
    > You can complete the installation and configuration by using standard Windows functionality.

2. Define company-level certificates and user-level certificates, as required.

### <a name="destination"></a>Destination for XML file output

If XML files must be sent as output to a specific place when invoices are posted (for example, if they must be sent to a SharePoint folder), set up a document type, and then set up a destination. For more information about these steps, see [Configure document management](../../fin-ops-core/fin-ops/organization-administration/configure-document-management.md) and [Electronic reporting (ER) destinations](../../dev-itpro/analytics/electronic-reporting-destinations.md).

> [!NOTE]
> The **Print invoice** option must be set to **Yes**. If the destination is set up, the status of the electronic invoice record for the invoice is automatically set to **Sent**.

## <a name="releteddoc"></a>Fill in data for related documents

Companies can report additional information about some base documents that are related to invoices. Here are some examples:

- The **DatiOrdineAcquisto** block contains information that is related to the purchase order.
- The **DatiContratto** block contains information that is related to the contract.
- The **DatiConvenzione** block contains information that is related to the agreement.
- The **DatiRicezione** block contains information that is related to data about the reception phase. This data is present in the management system that is used by the PA (tax agencies).
- The **DatiFattureCollegate** block contains information that is related to invoices that were previously transmitted and that the current document is connected to. This block is used for cases where a credit note and/or invoice is forwarded in accordance with previous advance payment invoices.

To enable the system to enter information in these blocks, set the following fields:

- On the **Sales order** page (**Accounts receivable** \> **Orders** \> **All sales orders**), in the **Header** view, on the **Setup** FastTab, set the fields in the **Base document** section.
- On the **Free text invoice** page (**Accounts receivable** \> **Invoices** \> **All free text invoices**), in the **Header** view, on the **General** FastTab, set the fields in the **Base document** section.
- On the **Project proposal** page (**Project management and accounting** \> **Projects** \> **All projects**), on the Action Pane, on the **Manage** tab, in the **Bill** group, select **Invoice proposal**, and then set the fields in the **Base document** section.

> [!NOTE]
> Data from the fields in the **Base document** section is sent as output from different blocks, depending on the value of the **Base document** field.
> 
> | Value of the Base document field | Block that data is sent from |
> |---|---|
> | Payment order | DatiOrdineAcquisto |
> | Contract | DatiContratto |
> | Agreement | DatiConvenzione |
> | Management system | DatiRicezione |
> | Original invoice | DatiFattureCollegate |

For each base document, users can add details about the document number and date, CUP (unique project code, which is managed by the Inter Ministerial Committee for Economic Planning), CIG (tender procedure identification code), and agreement code.

## <a name="einvoiceregister"></a>Electronic invoice register

To view all customer electronic invoices and perform various actions, go to **Accounts receivable** \> **Invoices** \> **E-Invoices** \> **Electronic invoices** to open the **Electronic customer invoices** page.

On this page, you can perform any of the following actions:

- Select **Select** to select invoices, based on various criteria. This function is useful if the **eInvoice register** option is set to **No**.
- Select **Create XML**, **Create signature**, and **Send** to create XML files and a digital signature for selected invoices, and send them.
- Select **Export** to export a selected invoice to an XML file.

    > [!NOTE]
    > The system sends a file to the folder that is set up on your computer. (The destination settings aren't used.)

- Select the **Details** tab to view details of the electronic invoice.

> [!NOTE]
> The **Electronic invoices** page (**Project management and accounting** \> **Project invoices** \> **E-invoices** \> **Electronic invoices**) resembles the **Electronic customer invoices** page and has the same functions.

![Electronic customer invoices page](media/emea-ita-electronic-invocies-electronic-customer-invoices.png)

## <a name="additionalfunctionality"></a>Additional functionality that affects the XML file

### Tax invoice for goods delivered for free

For information about how to set up and work with this functionality, see [Tax invoice for goods delivered for free](emea-ita-exil-goods-for-free.md).

On the **Distribution** page (**Sales and marketing** \> **Setup** \> **Distribution**), if **Goods for free** is selected in the **Reason for delivery** field and the **Invoice account** field is blank, the **TipoCessionePrestazione** element is sent as output in the XML file.

### Intent letters – Invoicing of usual exporters

For information about how to set up and work with this functionality, see [Intent letters – Invoicing of usual exporters](emea-ita-exil-intent-letter.md).
If an intent letter is set up for a customer, the **Causale** element (**DatiGeneraliDocumento** block) that has the number of the intent letter is sent as output in the XML file.

## <a name='fatturaPA'></a>Functionality that is available in Finance version 10.0.12

### Reverse charge and reverse charge group configuration

The settings in this section are required when a company uses the reverse charge functionality. Additionally, application-specific parameters that have these groups should be set up. For more information about this functionality, see [A country-specific hotfix to support changes in "FatturaPA" format of Italian electronic invoices in Microsoft Dynamics 365 Finance](https://support.microsoft.com/help/4569342/a-country-specific-hotfix-to-support-changes-in-fatturapa-format-of-it).

Go to **Tax** \> **Setup** \> **Reverse charge item groups** to define specific reverse charge groups for specific products or categories.

![Reverse charge item groups page](media/emea-ita-FatturaPA-161-RC-groups.png)

### Invoice type configuration

The following types of invoice documents are supported and will automatically be filled in:

- TD01 – Invoice
- TD04 – Credit note
- TD05 – Debit note
- TD20 – Self-invoice

If a required document type isn't covered by the values in the preceding list, you can manually adjust the document type in the invoice journals. To enable manual adjustment, you must complete the following setup:

- Electronic document property definition
- Invoice document type registration

For more information, see [A country-specific hotfix to support changes in "FatturaPA" format of Italian electronic invoices in Microsoft Dynamics 365 Finance](https://support.microsoft.com/help/4569342/a-country-specific-hotfix-to-support-changes-in-fatturapa-format-of-it).
