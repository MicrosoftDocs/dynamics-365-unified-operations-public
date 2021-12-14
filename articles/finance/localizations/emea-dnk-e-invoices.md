---
# required metadata

title: Customer electronic invoices in Denmark
description: This topic explains how to set up and process customers electronic invoices in Denmark.
author: ilkond
ms.date: 12/06/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Norway
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: 10.0.21

---

# Customer electronic invoices in Denmark

[!include [banner](../includes/banner.md)]

This topic provides information about how to configure and issue customer electronic invoices in Denmark using specific **[OIOUBL](http://www.oioubl.info/Classes/da/Invoice.html)** format of electronic invoices.

## Prerequisites

The primary address of the legal entity must be in Denmark.

## Import Electronic reporting configurations

In the **Electronic reporting** workspace, import the following Electronic reporting (ER) formats from the repository:

- OIOUBL Sales invoice (DK)
- OIOUBL Project invoice (DK)
- OIOUBL Sales credit note (DK)
- OIOUBL Project credit note (DK)

> [!NOTE]
> These formats are based on the **Invoice model** configuration and use the **Invoice model mapping** configuration. All required additional configurations are automatically imported.

For more information about how to import ER configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

### Reference the imported ER format configurations

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents:

    - **Sales and Free text invoice:** OIOUBL Sales invoice (DK)
    - **Sales and Free text credit note:** OIOUBL Sales credit note (DK)
    - **Project invoice:** OIOUBL Project invoice (DK)
    - **Project credit note:** OIOUBL Project credit note (DK)

## Configure parameters

### Configure legal entity parameters

1. Go to **Organization administration** \> **Organizations** \> **Legal entities**.
2. On the **Tax registration** FastTab, in the **Tax registration number** field, enter the company's VAT number.
3. On the **Bank account information** FastTab, in the **Routing number** field, enter the company's registration number.
4. In the **FI-Creditor ID** field, enter the creditor's identification number if **FIK** payments planned to be used.

### Configure methods of payment

According to OIOUBL standards, the codes of payment methods in the output XML file of electronic invoices must be compliant with the official list of standardized codes: [OIOUBL Payment Means Codes](http://www.oioubl.info/codelists/en/urn_oioubl_codelist_paymentmeanscode-1.1.html).
The system supports the following predefined codes of payment methods and provides its automatic conversion to the official codes:

| Internal payment method code | Official payment method code|
|------------------------------|-----------------------------|
| DK:BANK                      | 42                          |
| DK:FIK                       | 93                          |
| DK:GIRO                      | 50                          |
| All other codes              | 97                          |

To configure methods of payment in the system:

1. Go to **Accounts receivable** \> **Setup** \> **Payments setup** \> **Methods of payment**.
2. Create a new or select an existing method of payment to configure.
3. On the **General** FastTab, in the **Posting** section, in the **Account type** field, select **Bank** value.
4. In the **Payment account** field, enter the company's bank account assosiated with this method of payment.

    > [!NOTE]
    > The company bank account must already be set up at **Cash and bank management** \> **Bank accounts** \> **Bank accounts**.

### Units of measure configuration

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
2. Select a unit ID in the list, and then select **External codes**.
3. On the **External codes** page, in the **Overview** section, in the **Code** field, enter a code that corresponds to the selected unit ID.
4. In **Value** section, in **Value** field, enter the external code that should be used as the recommended unit of measure code according to [Codes for Units of Measure Used in International Trade](https://docs.oasis-open.org/ubl/prd1-UBL-2.1/cva/UBL-DefaultDTQ-2.1.html#d27e1).


### Sales tax codes configuration

When you generate electronic invoices in OIOUBL format, the tax information must be hierarchically structured in a specific way in the output XML file.

The top level of hierarchy is **Tax Scheme**, see the official list of tax schemes applicable for OIOUBL format: [OIOUBL Tax Schemes](http://oioubl.info/documents/da/da/Kodelister/OIOUBL_CODE_TaxSchemeID-1.5.pdf). 

The next level of tax data grouping within the tax scheme is **Tax Category**, see the official list of tax categories applicable for OIOUBL format: [OIOUBL Tax Categories](http://oioubl.info/documents/da/da/Kodelister/OIOUBL_CODE_TAXCATEGORYID.pdf). 

For some taxes, an additional attribute **Tax Type Code** must be also defined.

The following logic is used:
In the next chapter 

### Application specific parameters configuration
In the **Electronic reporting** workspace,

### Configure customer parameters

1. Go to **Accounts receivable** \> **Customers** \> **All customers**, and select a customer.
2. On the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices to be generated.
3. Set the **eInvoice attachment** option to **Yes** to attach a PDF copy of the printable invoice to the electronic invoice.
4. In the **Tax exempt number** field, enter the customer's VAT exempt number.
5. In the **EAN** field, enter the customer's identification number which will be used as **Endpoint ID** in the output XML file of the electronic invoice.
6. On the **Sales demographics** FastTab, in the **Primary contact** field, select a person who will be considered as buyer's contact.
    > [!NOTE]
    > Available contact persons must be preliminary defined for this customer.


### Customer requisition

When you register free text invoices, invoices that are based on sales orders, or project invoices, you must enter a customer requisition. You can also add an optional customer reference.

#### Free text invoices

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Create a new invoice, or select an existing invoice.
3. In the **Header** view, on the **Customer** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Sales orders

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
2. Create a new sales order, or select an existing sales order. 
3. In the **Header** view, on the **General** FastTab, in the **References** section, enter values in the **Customer requisition** and **Customer reference** fields.

#### Project invoices

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. Create a new project contract, or select an existing project contract.
3. On **Funding sources** FastTab, select or create a funding source of the **Customer** type, and then select **Details**.

    ![Funding sources.](media/emea-nor-ger-proj-contracts.jpg)

4. On the **Funding source details** page, on the **Other** FastTab, in **References** section, in the **Customer requisition** and **Customer reference** fields, enter default values for the contract. Alternatively, you can enter project-specific values in the corresponding fields on the **E-invoice** FastTab.

    ![Project references.](media/emea-nor-ger-proj-refs.jpg)

5. To enter customer requisition and reference values directly on the project invoice proposal, follow these steps:

    1. Go to **Project management and accounting** \> **Projects invoices** \> **Project invoice proposals**.
    2. Create a new invoice proposal, or select an existing invoice proposal.
    3. On the **Invoice proposal header** FastTab, in the **e-Invoice** section, enter values in **Customer requisition** and **Customer reference** fields.

    ![Project proposal.](media/emea-nor-ger-proj-prop.jpg)

### Customer accounting code registration

You can enter customer accounting codes when you work with free text invoices, invoices that are based on sales orders, or project invoices.

#### Free text invoices

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Create a new invoice, or select an existing invoice. 
3. In the **Header** view, on the **General** FastTab, in the **e-Invoice** section, in the **Dimension account** field, enter the accounting code for the invoice. 
4. To have a separate accounting code for each invoice line, follow these steps:

    1. Set the **Line-specific** option to **Yes**.
    2. Switch to the **Lines** view.
    3. On the **Line details** FastTab, on the **General** tab, in the **Dimension account** field, enter a line-specific accounting code for each invoice line.

    ![Line-specific accounting code for a free text invoice.](media/emea-nor-ger-fti-cost.jpg)

#### Sales orders

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
2. Create a new sales order, or select an existing sales order.
3. In the **Header** view, on the **General** FastTab, in the **e-Invoice** section, in the **Dimension account** field, enter the accounting code for the order.
4. To have a separate accounting code for each order line, follow these steps:

    1. Set the **Line-specific** option to **Yes**.
    2. Switch to the **Lines** view.
    3. On the **Line details** FastTab, on the **General** tab, in the **Dimension account** field, enter a line-specific accounting code for each order line.

#### Project invoices

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
2. Create a new project contract, or select an existing project contract.
3. On **Funding sources** FastTab, create or select a funding source of the **Customer** type, and then select **Details**.
4. On **Funding source details** page, on the **E-invoice** FastTab, in the **Dimension account** field, enter the project-specific default accounting code.

    ![Project-specific accounting code.](media/emea-nor-ger-proj-cost.jpg)

5. To enter customer accounting codes directly in project invoice proposals, follow these steps:

    1. Go to **Project management and accounting** \> **Projects invoices** \> **Project invoice proposals**.
    2. Create a new invoice proposal, or select an existing invoice proposal.
    3. On the **Invoice proposal header** FastTab, in the **e-Invoice** section, in the **Dimension account** field, enter the accounting code.

6. To have a separate accounting code for each transaction line, follow these steps:

    1. Set the **Line-specific** option to **Yes**.
    2. On the **Invoice proposal transactions** FastTab, in the **Dimension account** field, enter a line-specific accounting code for each transaction line.

    ![Transaction line-specific accounting code.](media/emea-nor-ger-proj-prop-cost.jpg)

## Export customer electronic invoices

### Send e-invoices

When an invoice is posted, you can generate an electronic invoice by selecting **Send** \> **Original** for the selected invoice.

![Sending an e-invoice.](media/emea-nor-ger-einvoice.jpg)

### View e-invoices

To inquire about the XML files of electronic invoices that have been generated, follow these steps.

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
2. Select a job, and then select **Show files**.

    ![Show files button.](media/emea-nor-ger-einvoice-open.jpg)

3. Select **Open** to download the file that contains the electronic invoice.

If generation of the electronic invoices fails because of errors, select **Show log** \> **Message details** to view more details about the error message.

![Message details.](media/emea-nor-ger-einvoice-log.jpg)

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, output XML files that contain electronic invoices will automatically be sent to the defined destinations immediately after the invoices are posted. When you post the invoices, you must turn on the **Print invoice** parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
