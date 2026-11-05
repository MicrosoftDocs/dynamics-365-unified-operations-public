---
title: Customer electronic invoices for United Arab Emirates
description: Learn how to get started with Customer Electronic invoices generation for United Arab Emirates in Microsoft Dynamics 365 Finance.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.date: 11/05/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: United Arab Emirates
ms.search.validFrom: 2026-12-01
ms.dyn365.ops.version: AX 10.0.50
---

# Customer electronic invoices for United Arab Emirates

[!include [banner](../../includes/banner.md)]

This article helps you get started with electronic invoicing for United Arab Emirates. Set up the system to generate electronic invoices in the UAE extension of the [PEPPOL International (PINT)](https://docs.peppol.eu/poac/ae/) format in Microsoft Dynamics 365 Finance.

## Prerequisites

The primary address of the legal entity must be in United Arab Emirates.

## Import Electronic reporting configurations

In the **Electronic reporting** workspace, import the following Electronic reporting (ER) formats from the repository:

- PINT Sales e-invoice (AE)
- PINT Sales e-credit note (AE)
- PINT Project e-invoice (AE)
- PINT Project e-credit note (AE)

> [!NOTE]
> The UAE-specific format configurations are based on the corresponding generic **PINT** format configurations. Those format configurations are based on the **PEPPOL** format configurations that use the **Invoice model** configuration and the **Invoice model mapping** configuration. The import process automatically imports all required additional configurations.

For more information about how to import ER configurations, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

### Reference the imported ER format configurations

To reference the imported ER format configurations, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. On the **Electronic documents** tab, in the **Electronic reporting** section, select the imported formats for electronic documents:

    - **Sales and Free text invoice:** PINT Sales e-invoice (AE)
    - **Sales and Free text credit note:** PINT Sales e-credit note (AE)
    - **Project invoice:** PINT Project e-invoice (AE)
    - **Project credit note:** PINT Project e-credit note (AE)

## <a id="UEN"></a>Configure legal registration numbers

If these registration types and categories already exist, skip this procedure.

To configure registration numbers, follow these steps:

1. In Dynamics 365 Finance, go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration types**.
1. Create a registration type.
1. In the **Country/region** field, select **ARE - United Arab Emirates**.
1. Go to **Organization administration** \> **Global address book** \> **Registration types** \> **Registration categories**.
1. Create a registration category.
1. In the **Registration types** field, select the registration type that you created in step 2.
1. In the **Registration categories** field, select **Enterprise ID (COID)**.

> [!NOTE]
> When the system generates the output files for electronic invoices, it uses registration numbers from the **Enterprise ID (COID)** category as the sellers' commercial registration numbers.

## Set up address structure

To set up the postal address structure, follow these steps:

1. Go to **Organization administration** > **Global address book** > **Addresses** > **Address setup**.
1. Ensure that you configure at least the following required elements:

   - Country/region
   - State
   - City
   - Street

## Configure legal entity data

### Enter the address

To add the primary address, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Legal entities**, and select a legal entity.
1. On the **Addresses** FastTab, add the primary address for the legal entity.

### Seller identification

To add the registration numbers, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Legal entities**.
1. On the **Tax registration** FastTab, in the **Tax registration number** field, enter a valid tax registration number (TRN).

   > [!NOTE]
   > The system puts the **TRN** number in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cac:PartyTaxScheme\\cbc:CompanyID** element in the generated electronic invoice XML file. The first 10 characters of the **TRN** represent the **Tax Identification Number (TIN)** and are used in the **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cbc:EndpointID** element for routing the generated electronic invoice as the seller's identification during submission.

1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**, set **Registration type** to the [legal registration number](#UEN) type you created earlier, and enter the company registration number in the **Registration number** field.
   > [!NOTE]
   > The system puts this number in the mandatory **Invoice\\cac:AccountingSupplierParty\\cac:Party\\cac:PartyLegalEntity\\cbc:CompanyID** element in the generated electronic invoice XML file.

## Configure customer data

### Enter the address

To enter the address, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. Select a customer.
1. On the **Addresses** FastTab, add a valid address for the selected customer.

### Enable customers for electronic invoicing

To enable customers for electronic invoicing, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**, and select a customer.
1. On the **Invoice and delivery** FastTab, set the **eInvoice** option to **Yes** to enable electronic invoices.
1. Optionally, set the **eInvoice attachment** option to **Yes** to attach an automatically created PDF copy of the printable invoice to the electronic invoice, if such an attachment is necessary.

### Buyer identification

To enter the tax registration numbers, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers** and select a customer.
1. On the **Invoice and delivery** FastTab, in the **SALES TAX** section, enter a valid tax registration number (TRN) in the **Tax exempt number** field for the selected customer.

   > [!NOTE]
   > The system puts the **TRN** number in the **Invoice\\cac:AccountingCustomerParty\\cac:Party\\cac:PartyTaxScheme\\cbc:CompanyID** element in the generated electronic invoice XML file. The first 10 characters of the **TRN** represent the **Tax Identification Number (TIN)** and are used in the **Invoice\\cac:AccountingCustomerParty\\cac:Party\\cbc:EndpointID** element for routing the generated electronic invoice as the seller's identification during submission.

1. On the Action Pane, select **Registration IDs**.
1. On the **Registration ID** FastTab, select **Add**, set **Registration type** to the [registration number](#UEN) type you created earlier, and enter the customer registration number in the **Registration number** field.

   > [!NOTE]
   > The system puts this number in the **Invoice\\cac:BuyerCustomerParty\\cac:Party\\cac:PartyIdentification\\cbc:ID** element in the generated electronic invoice XML file. This number is required for the **Free Trade Zone** transaction type.

> [!NOTE]
> For both seller and buyer identification, the schema **0235** (UAE Tax Identification Number) is used for EndpointIDs by default according to the [Electronic Address Scheme (EAS)](https://docs.peppol.eu/poacc/billing/3.0/codelist/eas/). If you need to redefine the default schema, see the next section. Otherwise, you can ignore the next section.

## Configure identification schemas

Follow these steps only if you need to redefine the default identification schemas for sellers or buyers.

### Configure electronic document properties

To set up electronic document properties, follow these steps:

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types**, and select **New**.
1. In the **Type** field, enter **CompanyEndpointType**. Enter the value exactly as shown. Use this type for the **Seller** identification schema definition.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Legal entities**.
1. Save your changes and return to the **Electronic document property types** page.
1. Select **New** to create another electronic document property type.
1. In the **Type** field, enter **CustomerEndpointType**. Enter the value exactly as shown. Use this type for the **Buyer** identification schema definition.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, in the **Table name** field, select **Customers**.
1. Save your changes, and return to the **Electronic document property types** page.
1. Save your changes, and close the page.

   :::image type="content" source="../belgium/emea-bel-einoices-schemas.jpg" alt-text="Screenshot of the property type added on the Electronic document property types page.":::

### Enter the seller schema code

To enter the Seller schema code, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Legal entities** and select a legal entity.
1. Select **Electronic document properties** from the Action Pane.
1. In the **Value** column, enter the required seller schema code.

### Enter the buyer schema codes

To enter the buyer schema codes, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. Select a specific customer in the list. On the **Action** pane, select the **Customer** tab. In the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter the required buyer schema code.

> [!NOTE]
> Schema codes defined by electronic document property types take priority over the default **0235** schema code.

## Configure units of measure

To configure units of measure, follow these steps:

1. Go to **Organization administration** > **Setup** > **Units** > **Units**.
1. Select a unit ID, and then select **External codes**.
1. On **External codes**, in **Overview**, enter the unit ID in the **Code** column.
1. Select the check box in the **Standard code** column.
1. In the **Value** section, enter the external code from the [UNECE Recommendation 20 code list](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/) in the **Value** field.

   > [!NOTE]
   > If no specific unit of measure applies, the system uses the default value **EA**.

## Configure sales tax codes

To configure sales tax codes, follow these steps:

1. Go to **Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**.
1. Select a sales tax code. On the **Action** pane, on the **Sales tax code** tab, in the **Sales tax code** group, select **External codes**.
1. In the **Overview** section, create a line for the selected unit. Enter the sales tax code from step 2 in the **External code** field.
1. In the **Value** section, enter an external code according to the [Duty or tax or fee category code (Subset of UNCL5305)](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNCL5305/) in the **Value** field.
1. Go to **Tax** > **Setup** > **Sales tax** > **Sales tax exempt codes**.
1. Define exempt codes that you use for nontaxable, zero-rated, or exempted operations.

> [!NOTE]
> The value you define in the **Description** field is used as **Tax Exemption Reason** when generating the output XML files for electronic invoices.

## Invoice transaction type determination

To meet the UAE requirements, e-invoices must include the invoice transaction type code. This code goes into the dedicated **Invoice\cbc:ProfileExecutionID** XML element.

The following values are available.

| Position | Description | Dynamics 365 Finance implementation |
| ------------ | ------------------ | ---------------------------------- |
| **1**XXXXXXX | Free Trade Zone | Implemented via Electronic document properties. See the next section for details. |
| X**1**XXXXXX | Deemed Supply | Out of scope - always **0**. |
| XX**1**XXXXX | Profit Margin Scheme | Out of scope - always **0**. |
| XXX**1**XXXX | Summary Invoice | Indicates **1** if the invoice covers several deliveries with different dates. |
| XXXX**1**XXX | Continuous Supply | Out of scope - always **0**. |
| XXXXX**1**XX | Disclosed Agent Billing | Out of scope - always **0**. |
| XXXXXX**1**X | Supply through e-commerce | Out of scope - always **0**. |
| XXXXXXX**1** | Export transaction | Indicates **1** if the invoice is issued for the customer outside UAE. |

### Configure Free Trade Zone property

To configure the Free Trade Zone property, follow these steps:

1. Go to **Accounts receivable** > **Setup** > **Electronic document property types**, and select **New**.
1. In the **Type** field, enter **FreeTradeZone**. Enter the value exactly as shown.
1. Select **Applicability** to add an applicable table.
1. On the **Electronic document property type applicability setup** page, select **New** to add the applicability table.
1. In the **Table name** column, select the following tables depending on your scenario:
    - **CustTable** (Customers) - to set the property for a specific customer so all invoices for this customer are marked as *Free Trade Zone*.
    - **CustInvoiceJour** (Customer invoice journal) - to set the property for a specific *customer* invoice individually.
    - **ProjInvoiceJour** (Project invoice) - to set the property for a specific *project* invoice individually.
    - **CompanyInfo** (Legal entities) - to set the property for the entire legal entity so **all** invoices from this legal entity are marked as *Free Trade Zone*.
1. Save your changes and return to the **Electronic document property types** page.
1. Save your changes, and close the page.

   :::image type="content" source="free-trade-zone.jpg" alt-text="Screenshot of the FreeTradeZone property type added on the Electronic document property types page.":::

#### Enter customer properties

To enter customer properties, follow these steps:

1. Go to **Accounts receivable** > **Customers** > **All customers**.
1. Select a specific customer in the list. On the Action Pane, select the **Customer** tab. In the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter any non-empty value, such as **Yes**.

   > [!NOTE]
   > Any non-empty value indicates that the **FreeTradeZone** property is turned on. An empty value or an unconfigured property indicates the customer isn't **FreeTradeZone**.

#### Enter customer invoice properties

To enter customer invoice properties, follow these steps:

1. Go to **Accounts receivable** > **Inquiries and reports** > **Invoices** > **Invoice journal**.
1. Select a specific invoice in the list. On the Action Pane, on the **Invoice** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter any non-empty value.

#### Enter project invoice properties

To enter project invoice properties, follow these steps:

1. Go to **Project management and accounting** > **Project invoices** > **Project invoices**.
1. Select a specific project invoice in the list. On the Action Pane, on the **Project invoice** tab, in the **Properties** group, select **Electronic document properties**.
1. In the **Value** column, enter any non-empty value.

#### Enter legal entity properties

To enter legal entity properties, follow these steps:

1. Go to **Organization administration** > **Organizations** > **Legal entities** and select a legal entity.
1. Select **Electronic document properties** from the Action Pane.
1. In the **Value** column, enter any non-empty value.

> [!NOTE]
> Invoice-level values take priority over customer-level values and legal entity-level values. Use them if you need to mark a particular invoice. Customer-level values take priority over legal entity-level values. Use them when you need to mark all invoices for a specific customer. Use legal entity-level values to mark all invoices from the legal entity for all customers.

## Export customer electronic invoices

### Generate e-invoices

When you post an invoice, you can generate an electronic invoice from any invoice journal. Select the invoice. On the **Action** pane, on the **Invoice** tab, in the **Document** group, select **Send** > **Original**.

:::image type="content" source="../media/emea-nor-ger-einvoice.jpg" alt-text="Screenshot of sending an e-invoice.":::

### View e-invoices

To view the XML files of electronic invoices that you generated, follow these steps:

1. Go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.
1. Select a job, and then select **Show files**.

    :::image type="content" source="../media/emea-nor-ger-einvoice-open.jpg" alt-text="Screenshot of the Show files button.":::

1. Select **Open** to download the file that contains the electronic invoice.

    If the system can't generate the electronic invoices because of errors, select **Show log** > **Message details** to view more details about the error.

    :::image type="content" source="../media/emea-nor-ger-einvoice-log.jpg" alt-text="Screenshot of viewing message details.":::

### Send e-invoices to ER destinations

You can set up ER destinations for electronic invoice formats. In this case, the system automatically sends output XML files that contain electronic invoices to the defined destinations immediately after you post the invoices. When you post the invoices, you must turn on the **Print invoice** parameter.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

## More information

- [Electronic invoicing coverage by country and region](../global/e-invoicing-coverage.md)
- [Forced electronic invoices generation](../europe/emea-eur-forced-einvoices.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
