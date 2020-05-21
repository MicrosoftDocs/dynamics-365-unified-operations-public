---
# required metadata

title: Customer electronic invoices
description: This topic provides information about managing customer electronic invoices for Italy.
author: v-oloski
manager: 
ms.date: 05/21/2020
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
  
Electronic invoices "FatturaPA" version 1.2, can be used for all types of businesses, including public administrations, private companies, and professionals. 

> [!NOTE] 
> The primary address of the legal entity must be in Italy.

This topic contains information about:

- Setup
- How to fill in data for CIG and CUP ouput
- Overview of **Electronic invoices** page

## Setup

Before you can begin to work with the electronic invoice functionality, the following must be set up:
- [Accounts receivable parameters](#arparameters)
- [E-invoice parameters](#einvoicesparameters)
- [Electronic documents properties](#edproperties)
- [Customers](#customers)
- [Digital certificate](#digitalcert)
- Optional - [Destination for xml file output](#destination)

## <a name="arparameters"></a>Accounts receivable parameters

Select the configurations to create electronic invoice xml files for Sales and Free text invoices, Sales and Free text credit notes,
Project invoices, and Project credit notes. These configurations are located on the **Electronic document** tab of the **Accounts receivable parameters** page (**Accounts receivable \> Setup \> Accounts receivable parameters**).

![Accounts receivable parameters](media/emea-ita-electronic-invocies-AR-parameter-e-invoices.png)

 > [!NOTE] 
 > The configurations must be imported before they are selected. For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## <a name="einvoicesparameters"></a>E-Invoices parameters
Use these parameters to specify business scenarios and company-specific information. 

1. Go to **Accounts receivable \> Setup \> Electronic invoice parameters**.
2. On the  **General** tab, specify the electronic signature requirement.
3. On the **Company information** tab, specify the company information and tax reperesentative, if needed. This information overrides the information in the Legal entity record.
4. On the **Art. 2250 Civil code registration** tab, provide any necessary information if the company is registered under the terms of Art. 2250 of the Italian Civil Code.
5. On the **Number sequences** tab, fill in number sequences for the e-invoice file number and transmission number.

## <a name="edproperties"></a>Electronic document properties
Electronic document properties functionality are used for setting the output to xml document blocks for different business cases including: 

- A VAT registration number for customers who are not in the EU and don't have VAT registration codes  
- A certified e-mail address (PEC) for private companies or professionals
- A stamp duty (payable and not payble by customer)
- A customer's representative data 

For the functionality to work, the following must be set up:

- **Electronic document property types** (**Account receivable > Setup > Electronic document property types**) and the table to which the document property type is applied. For electronic invoice functionality, the **Customers** and **Legal entities** tables are applied.

![Electronic document property types](media/emea-ita-electronic-invocies-electronic-document-property-types.png)

- Required values in set tables on the customer and legal entity level (**Accounts receivable** \> **Customers** \> **All customers**, **Customer** tab, **Electronic document properties** button and **Organization administration** > **Organizations** > **Legal entities**, **Electronic document properties** button).

Set values are used for output to the xml file blocks. The following table provides information about how and where these values are used.

| Business scenario | Electronic document property type | Electronic document property type description | Applicability (table) | Where to use | Element in the xml file |
|-------------------|-----------------------------------|-----------------------------------------------|-----------------------|--------------|-------------------------|
| For customers who are outside of the EU and don't have VAT registration codes, the VAT registration number should be 00000000000 | **VATnonEU** | For example: Customer, non-EU VAT number|**CustTable** (Customers) | **Customer, Electronic document properties**, Value=00000000000 |**IdCodice** (CessionarioCommittente\ DatiAnagrafici\ IdFiscaleIVA block) |
| Certified e-mail address (PEC) for private companies or professionals | **PEC** | For example: Customer, Certified e-mail address | **CustTable** (Customers) | **Customer, Electronic document properties**,   Value = < PEC >  | **PECDestinatario** (DatiTrasmissione block) |
| Stamp duty not included in invoice total (for sales invoices) and included/not included for project invoices | **Bollo** Note that it is used for sales order, free text, and project invoices | For example: Stamp duty, included/not included into invoice totals | **CompanyInfo** (Legal entities) |**Legal entity, Electronic document properties**,  Value = <Charge code/Project category, which is used for stamp duties>. **Charges code**: Debit type for this charge code should be Ledger  **Project category**: should be billable | **ImportoBollo** (DatiBollo block) |
| Stamp duty included into invoice total | **BolloPay**. Note that it is used only for sales order and free text invoices | For example: Stamp duty, included into invoice totals | **CompanyInfo** (Legal entities) | **Legal entity, Electronic document properties**, Value=<Charge code/Project category, which is used for stamp duties>. **Charges code**: Debit type should be Customer/Vendor | **ImportoBollo** (DatiBollo block) |
| Representative | TaxRepPaese, TaxRepPaese, TaxRepCodice, TaxRepDenominazione, TaxRepNome, TaxRepCognome | Any description | **CustTable** (Customers) | **Customer, Electronic document properties**. Value=IT (for TaxRepPaese) For other types, fill in data of representative | **Cognome** (RappresentanteFiscale block) |

> [!NOTE 1] 
> In the table:
>
> - **Customer, Electronic document properties** is **Account receivable > Customers > All customers**, **Customer** tab, **Electronic document properties** button.
> - **Legal entity, Electronic document properties** is **Organization administration > Legal entities**, **Electronic document properties** button

> [!NOTE 2]  
> In **Electronic document property types** list page, the **Description** field is filled in automatically when a user enters information in the **Group description** and **Description**fields.

> [!NOTE 3]
> Electronic document property type must have the same code as specified in the table.

### Use project categories for stamp duty

- Go to **Project management and accounting** > **Setup** > **Categories** > **Project categories** to set up Project categories with a Fee/Expense transaction type. The Category ID should be equal to the value defined for **Bollo** on the legal entity level. For m ore informaito, see the table above.

The Project category of Fee transaction type can be used only for stamp duty included in the invoice. The Project category of expense transaction type can be used both for invoices included and not included in a customer invoice. In both cases, the **Bollo** document property type is used. When you create **Fee** or **Expese** journal lines, select the category that was defined as stamp duty, and enter a Cost price. The system considers this cost price as stamp duty amount. If you fill in sales price with the cost price amount, the system considers this ammount included in the invoice totals. Sales price amount is equal to zero (0), and this transaction is not included in invoice totals. 

> [!NOTE]
> You can use only one of the journal types (Fee or Exepense) for stamp duty. If a company uses only payable stamp dute it is possible to use Fee journal type. If a company uses both payable and unpayable stamp duty it is better to use Expense journal type.   


## <a name="customers"></a>Customers 

### Authority office field
The **Authority office** field is located under, **Accounts receivable** \> **Customers** \> **All customers**, open a customer record in **Edit** mode, and expand the **Sales demographics** FastTab.

This field value is used to define the type of communication (B2G or B2B). If the length of this value is 6, the customer will be considered a public administration (Transmission format is **FPA12**). If the length of this value is 7, the customer will be considered private companies or professionals (Transmission Format is **FPR12**). 
In both of these cases, the system fills in the **CodiceDestinatario** tag (xml file) with this field value.

![Authority office](media/emea-ita-electronic-invocies-customer-authority-office.png)

If **Authority office** field value is empty, the system considers a customer a private company or professional (Transmission format is **FPR12**) and fills in the **CodiceDestinatario** tag (xml file) with **0000000**.

In this case, a certified e-mail address (**PEC**) should be set up. For more information, see the table in the [Electronic document properties](/electronic-document-properties) section.

### Activate automatic creation of e-invoices  

**Accounts receivable** \> **Customers** \> **All customers**. Open a customer record in **Edit** mode, and on the **Invoice and delivery** FastTab, in the **E-INVOICE** field group, find **eInvoice register** option.

If this option is set to **Yes**, the system automatically creates the record in **Electronic customer invoices** page list. For more information, see the [Overview of electronic invoices page](/overview-of-electronic-invoices-page.

![E-invoice activation](media/emea-ita-electronic-invocies-customer-e-invoice.png)

## <a name="digitalcert"></a>Digital certificates

Go to **Accounts receivable** \> **Setup** \> **Electronic invoice digital certificates** to perform electronic signing of e-Invoices by using either a **Company** or **User** certificate.

![digital certificate](media/emea-ita-electronic-invocies-certificate.png)

Each [FatturaPA file](http://www.fatturapa.gov.it/export/fatturazione/en/b-2.htm) that is transmitted to the [Exchange System](http://www.fatturapa.gov.it/export/fatturazione/en/sdi.htm) must be signed by using a qualified signature certificate by the party that is issuing the invoice.  
A qualified signature certificate may be obtained from one of the certifiers in the [list of authorized certifiers](http://www.digitpa.gov.it/firma-digitale/certificatori-accreditati).  
  
Dynamics 365 Finance supports the **XAdES-BES** signature format. To support FatturaPA you must perform the following steps:

1. Install and configure digital certificates that have private and public keys in the **Certificate Server** to the **Personal** node on client computers.  
      
  > [!NOTE] 
  > You can complete the isntallation and configuration by using standard Windows functionality.

2. As required, define company-level certificates and user-level certificates.

## <a name="destination"></a>Destination for xml file output

If xml files must be output to a specified place when invoices are posted, for example a SharePoint folder, set up a document type and then set up a destination. For more information about these tasks, see [Configure document management](../../fin-ops-core/fin-ops/organization-administration/configure-document-management.md) and [Electronic reporting (ER) destinations](../../dev-itpro/analytics/electronic-reporting-destinations.md).

> [!NOTE] 
> **Print invoice** must be set to **Yes** and if the destination is set up, the e-invoice record for this invoice is automatically given a status of **Sent**.

## Fill in data for related documents

Companies may report additional information about some base documents related to invoices. This includes: 

 - The **DatiOrdineAcquisto** block contains the information relative to the purchase order. 
 - The **DatiContratto** block contains the information relative to the contract. 
 - The **DatiConvenzione** block contains the information relative to the agreement. 
 - The **DatiRicezione** block contains the information relative to the data present on the management system that is used by the PA (tax agencies) regarding the reception phase. 
 - The **DatiFattureCollegate** block contains the information relative to the invoices previously transmitted and to which the present document is connected. The block regards the cases of the forwarding of a credit note and/or invoice pursuant to previous advance payment invoices.

So that the system can populate these blocks, the following fields should be filled in on the **Free text invoice**, **Sales order**, and **Project proposal** pages:

- **Accounts receivable** \> **Orders** \> **All sales orders**, the **Header** view, on the **Setup** FastTab, the **Base document** field group.
- **Accounts receivable** \> **Invoices** \> **All free text invoices**, the **Header** view, the **Base document** field group.
- **Project management and accounting** \> **Projects** \> **All projects**, the **Manage** tab, **Bill** \> **Invoice proposal**, **Base document** field group

> [!NOTE]
> The block from which the system outputs data from **Base document** fields depends on the value specified in the **Base document** field: 
> - **Payment order** - **DatiOrdineAcquisto** block
> - **Contract** - **DatiContratto** block
> - **Agreement** - **DatiConvenzione** block
> - **Management system** - **DatiRicezione** block
> - **Original invoice** - **DatiFattureCollegate** block

For each base document, a user can add the details about document number and date, CUP code (managed by Inter Ministerial Committee for Economic Planning), CIG code (tender procedure identification code), and agreement code.

## Electronic invoices register 

To view all customer e-invoices and perform various actions, go to**Accounts receivable** \> **Invoices** \> **E-invoices** \> **Electronic invoices**, to open the **Electronic customer invoices** page.

In this page, you can:

- Click **Select** to select invoices based on different criteria. This function is useful if the **eInvoice register** option is not set to **Yes**.
- Create xml files and a digital signature for selected invoices and send them.
- Export the selected invoice to an xml file.

>[!NOTE]
> The system outputs a file to the folder set up on your computer (the destination settings are not used).   

- Overview details of the electronic invoice.

> [!NOTE]  
> A similar page with the same functions is the**Electronic invoices** page (**Project management and accounting** \> **Project invoices** \> **E-invoices** \> **Electronic invoices**).

![Customer electronic invoices](media/emea-ita-electronic-invocies-electronic-customer-invoices.png)

 
