---
title: Customer electronic invoices in Denmark
description: Learn how to set up and process electronic invoices in Denmark in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/30/2025
ms.reviewer: johnmichalak
ms.search.region: Norway
ms.search.validFrom: 2021-01-01
---

# Customer electronic invoices in Denmark

[!include [banner](../../includes/banner.md)]

This article explains how to set up and process outgoing customers-related electronic invoices in the Denmark-specific **OIOUBL** format in Microsoft Dynamics 365 Finance.

## Prerequisites

The primary address of the legal entity must be in Denmark.

## Import electronic reporting configurations

In the **Electronic reporting** workspace, import the following or later versions of the electronic reporting (ER) formats from the repository to enable electronic invoices generation in the **OIOUBL version 3** format:

- OIOUBL Sales invoice (DK) **version 272.46.13**
- OIOUBL Project invoice (DK) **version 272.40.13**
- OIOUBL Sales credit note (DK) **version 272.45.12**
- OIOUBL Project credit note (DK) **version 272.36.9**

> [!NOTE]
> If the versions of the ER configurations earlier than listed above are used, then the system will continue electronic invoices generation following the previous OIOUBL format version, older then version 3.

For more information about how to import ER configurations, see [Import electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### Reference the imported ER format configurations

To reference the imported ER format configurations, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Electronic documents** tab, on the **Electronic reporting** FastTab, select the imported formats for electronic documents:

    - **Sales and Free text invoice:** OIOUBL Sales invoice (DK)
    - **Sales and Free text credit note:** OIOUBL Sales credit note (DK)
    - **Project invoice:** OIOUBL Project invoice (DK)
    - **Project credit note:** OIOUBL Project credit note (DK)

## Configure parameters

### Configure legal entity parameters

To configure legal entity parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Organizations** \> **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add a valid primary address for the selected legal entity.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter the company's VAT number.
1. On the **Bank account information** FastTab, in the **Routing number** field, enter the company's CVR number.
1. Companies can be identified by their CVR number (with **0184** schema value) or their Global Location Number, GLN (with **0088** schema value). The GLN is also known as a European article numbering (EAN) location number. To identify a company by its EAN, follow these steps:
 
    - Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
    - Define a new registration type for Denmark that has the name **EAN**. You must enter the name exactly as it appears here.
    - Go to **Organization administration** \> **Organizations** \> **Legal entities**, and select **Registration IDs** on the Action Pane.
    - On the **Registration ID** FastTab, add the **EAN** registration type that you created.
    - In the **Registration number** field, enter a valid EAN number.
      
    > [!NOTE]
    > The EAN has higher priority than the CVR number. If both numbers are configured at the same time, the EAN is used.  

1. In the **FI-Creditor ID** field, enter the creditor's identification number if you plan to use FIK payments.

> [!NOTE]
> The contact information for the legal entity is automatically retrieved from the related Person that is associated with the current user in Dynamics 365 Finance. Make sure that the person has a valid email address and phone number. The phone number must start from **+** and the country code. 

### Configure customer parameters

To configure customer parameters, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Customers** \> **All customers**, and select a customer.
1. On the **Addresses** FastTab, add a valid address for the selected customer.
1. On the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable the generation of electronic invoices.
1. Set the **eInvoice attachment** option to **Yes** to attach a PDF copy of the printable invoice to the electronic invoice.
1. In the **Tax exempt number** field, enter the customer's tax exempt number.
1. In the **EAN** field, enter the customer's identification number. 

    > [!NOTE]
    > If no EAN is defined, the customer's tax exempt number is used for the customer's company identification.

1. On the **Sales demographics** FastTab, in the **Primary contact** field, select a person who will be considered the buyer's contact.

    > [!NOTE]
    > All available contact people must already be defined for the selected customer. Make sure that the selected contact person has a valid email address and phone number. The phone number must start from **+** and the country code.

### Configure methods of payment

According to OIOUBL standards, the payment method codes in the XML file output of electronic invoices must comply with the [official list of standardized codes](https://oioubl21.oioubl.dk/codelists/en/urn_oioubl_codelist_paymentmeanscode-1.1.html).

The system supports the following predefined codes for payment methods and provides automatic conversion to the official codes.

| Internal payment method code | Official payment method code |
|------------------------------|------------------------------|
| DK:BANK                      | 42                           |
| DK:FIK                       | 93                           |
| DK:GIRO                      | 50                           |
| All other codes              | 97                           |

To configure methods of payment, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Payments setup** \> **Methods of payment**.
1. Create a new method of payment, or select an existing method to configure.
1. On the **General** FastTab, in the **Posting** section, in the **Account type** field, select **Bank**.
1. In the **Payment account** field, enter the company bank account that is associated with the method of payment.

    > [!NOTE]
    > The company bank account must already be set up at **Cash and bank management** \> **Bank accounts** \> **Bank accounts**.

### Configure units of measure

To configure units of measure, follow these steps:

1. Go to **Organization administration** \> **Setup** \> **Units** \> **Units**.
1. Select a unit ID, and then select **External codes**.
1. On the **External codes** page, in the **Overview** section, in the **Code** column, enter a code that is equal to the selected unit ID.
1. In the **Standard code** column, select the checkbox.
1. In the **Value** section, in the **Value** field, enter the external code according to [the required codification](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/).

    > [!NOTE]
    > For scenarios where no specific units of measure are assumed, the default value **EA** is used.

## Configure sales tax codes

Configuration of sales tax codes depends on which OIOUBL format is used, version 3 or earlier. Refer to the respective chapter below.

### Configure sales tax codes for the version 3 of OIOUBL format

To additionally configure sales tax codes, follow these steps:

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes**.
1. Select a sales tax code, and then, on the Action Pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
1. In the **Overview** section, create a line for the selected unit. In the **External code** field, enter the sales tax code you selected in step 2.
1. In the **Value** section, in the **Value** field, enter an external code to use for the selected sales tax code, according to [Duty or tax or fee category code (Subset of UNCL5305)](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/).

### Configure sales tax codes for the previous OIOUBL format versions

When you generate electronic invoices in OIOUBL format, the tax information in the output XML file must be hierarchically structured in a specific way.

The top level of the hierarchy is **Tax Scheme**. <!-- The provided link appears to be broken For the official list of tax schemes that are applicable to the OIOUBL format, see [OIOUBL Tax Schemes](https://oioubl21.oioubl.dk/documents/da/da/Kodelister/OIOUBL_CODE_TAXSCHEMEID.pdf). -->

The next level of tax data grouping, within the tax scheme, is **Tax Category**. For the official list of tax categories that are applicable to the OIOUBL format, see [OIOUBL Tax Categories](https://oioubl21.oioubl.dk/documents/da/da/Kodelister/OIOUBL_CODE_TAXCATEGORYID.pdf). 

For some taxes, an additional attribute, **Tax Type Code**, must also be defined.

You can associate tax schemes, tax categories, and tax type codes with sales tax codes by using application-specific parameters. 

Application-specific parameters must be configured for the following configurations:

- OIOUBL Sales invoice (DK)
- OIOUBL Project invoice (DK)
- OIOUBL Sales credit note (DK)
- OIOUBL Project credit note (DK)

For each configuration, follow these steps:

1. In the **Electronic reporting** workspace, on the **Reporting configurations** tile, in the list of configurations, select a required configuration. For example, select **OIOUBL Sales invoice (DK)**.
1. On the **Configurations** menu, in the **Application specific parameters** section, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** FastTab, select **TaxSchemeSelector** in the grid.

    Next, on the **Conditions** FastTab, you will configure the correspondence between internal sales tax codes and official tax schemes codes. 

1. On the **Conditions** FastTab, select **Add** to add a condition to the grid.
1. In the **Code** field for the new condition, select the sales tax code that is defined in the system. 

    > [!NOTE]
    > In the **Code** field, you can select the **\*Blank\*** or **\*Not blank\*** placeholder value instead of a specific sales tax code.

1. In the **Lookup result** field, select a corresponding official tax schemes code.

    ![Defining conditions for the TaxSchemeSelector lookup on the Application specific parameters page.](../media/emea-dnk-ASP-parameters.jpg)

1. On the **Lookups** FastTab, select **TaxCategorySelector** in the grid.
1. On the **Conditions** FastTab, repeat steps 4 through 6 to configure the correspondence between internal sales tax codes and official tax categories codes.
1. On the **Lookups** FastTab, select **TaxCodeTypeSelector** in the grid.
1. On the **Conditions** FastTab, repeat steps 4 through 6 to configure the correspondence between internal sales tax codes and tax type codes. If no tax type code is required, select **Not applicable**.
1. In the **State** field at the top of the page, select **Completed**, and then save your changes.

## Buyer reference

According to **OIOUBL version 3** requirements, when you register free text invoices, invoices that are based on sales orders, or project invoices, you must enter either a customer reference.

### Free text invoices

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
1. Create a new invoice, or select an existing invoice.
1. In the **Header** view, on the **Customer** FastTab, in the **References** section, enter a value in the **Customer reference** field.

### Sales orders

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Create a new sales order, or select an existing sales order.
1. In the **Header** view, on the **General** FastTab, in the **References** section, enter a value in the **Customer reference** field.

### Project invoices

1. Go to **Project management and accounting** \> **Projects** \> **Project contracts**.
1. Create a new project contract, or select an existing project contract.
1. On the **Funding sources** FastTab, select or create a funding source of the **Customer** type, and then select **Details**.
1. On the **Funding source details** page, on the **Other** FastTab, in the **References** section, in the **Customer reference** field, enter default value for the contract. Alternatively, you can enter project-specific value in the corresponding field on the **E-invoice** FastTab.
1. To enter customer reference values directly on the project invoice proposal, follow these steps:

    1. Go to **Project management and accounting** \> **Projects invoices** \> **Project invoice proposals**.
    1. Create a new invoice proposal, or select an existing invoice proposal.
    1. On the **Invoice proposal header** FastTab, in the **e-Invoice** section, enter a value in the **Customer reference** field.

## Export customer electronic invoices

### Send e-invoices

After an invoice is posted, you can generate an electronic invoice by selecting the invoice and then selecting **Send** \> **Original** in the **Document** group on the **Invoice** tab of the Action Pane.

![Sending an e-invoice.](../media/emea-nor-ger-einvoice.jpg)

### View electronic invoices

To view electronic invoices, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.
1. Select **Open** to download the file that contains the electronic invoice.

    If generation of the electronic invoices failed because of errors, select **Show log**. Then select **Message details** in the message bar to view more details about the error.

    ![Viewing the message details for an error.](../media/emea-nor-ger-einvoice-log.jpg)

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, output XML files that contain electronic invoices are automatically sent to the defined destinations immediately after the invoices are posted. When you post the invoices, you must turn on the **Print invoice** parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
