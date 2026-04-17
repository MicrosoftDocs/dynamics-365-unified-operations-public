---
title: Fiscal service (ESR) integration
description: Learn about the fiscal service integration for Austria and the Czech Republic, including overviews on available configurations and setup.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/13/2026
ms.reviewer: johnmichalak
ms.search.region: Austria, Czech Republic
ms.search.validFrom: 2017-12-31
ms.search.form: CashRegister_W
ms.dyn365.ops.version: 7.3
---

# Fiscal service (ESR) integration

[!include [banner](../../includes/banner.md)]

In Austria, all cash payments must be signed by an external device or service, and they must be securely stored. In the Czech Republic, all cash payments must be sent to the government portal for a fiscal signature. In both countries, a cash receipt must be issued where the signature is printed.

To support these country or region-specific requirements, Dynamics 365 Finance lets you integrate with a third-party fiscal service that complies with specific requirements for cash payment control in various countries or regions.

> [!NOTE]
> It's assumed that the third-party fiscal service meets all other country or region-specific legal requirements about registered transactions. You're responsible for correctly setting up and administering the fiscal service.

## Available configurations

The formats of the cash receipt, the XML request to the fiscal service, and the XML response from the fiscal service are configured as Electronic reporting (ER) configurations that are stored in the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS). The following configurations are available.

| Configuration name | Configuration description | Comment | ER configuration file in the LCS Shared asset library |
|---|---|---|---|
| **Cash Receipt Model** | | **Data model for the cash receipt format** | **Cash Receipt Model.version.1.xml** |
| Cash Receipt Format | | Basic format for a cash receipt | Cash Receipt Format.version.1.1.xml |
| Cash Receipt Format (AT) | | Format for a cash receipt in Austria (This format includes a Quick Response Code \[QR code\].) | Cash Receipt Format (AT).version.1.1.1.xml |
| Cash Receipt Format (CZ) | | Format for a cash receipt in the Czech Republic (This format includes the Business Premises \[BP\] ID.) | Cash Receipt Format (CZ).version.1.1.1.xml |
| **Cash Register Model** | | **Data model for cash register integration** | **Cash Register Model.version.1.xml** |
| ESR Request example | Example of a European Fiscal Standards Association (EFSTA) Simple Receipt (ESR) Request | Basic format for a sample XML request to the EFSTA fiscal service (This format can be used in Austria.) | ESR Request example.version.1.1.xml |
| ESR Request example (CZ) | Example of an ESR Request for the Czech Republic | Format for a sample XML request to the EFSTA fiscal service in the Czech Republic | ESR Request example (CZ).version.1.1.1.xml |
| ESR Response example | Example of an ESR Response | Basic format for a sample XML response to the EFSTA fiscal service (This format can be used in Austria.) | ESR Response example.version.1.1.xml |
| ESR Response example (CZ) | Example of an ESR Response for the Czech Republic | Format for a sample XML response to the EFSTA fiscal service in the Czech Republic | ESR Response example (CZ).version.1.1.1.xml |

## Setup

### Cash registers

Set up each cash register to communicate with the fiscal service. Set up cash registers on the **Cash registers** page (**Accounts receivable** &gt; **Setup** &gt; **Cash registers** &gt; **Cash registers**). The following table provides more information about the required setup.

| Setup | Details | More information |
|---|---|---|
| Cash register settings | Specify the URL of the cash register, the name of the instance of Microsoft Azure Key Vault, and the class name. | **Cash register URL** – Enter the URL of the fiscal service. **Warning:** Third-party services or other services that you configure here don't require certification, and they might not meet Microsoft privacy standards. Review each service's privacy documentation and work with each service provider to learn more about the level of compliance that each service provides. You're responsible for making sure that these services meet your security-related, privacy-related, and legal standards. You bear the risk of using these services. Microsoft gives no express warranties, guarantees, or conditions. Use only services that provide secure and authorized connections (that is, services that use the HTTPS protocol). **Key Vault name** – If the fiscal service is accessible at a secure connection (that is, the URL starts with https://), set up certificates and store them correctly on both sides (the Finance app and the third-party fiscal service). In this field, select the name of the Azure Key Vault instance where the Finance certificate is stored. For more information, see [Setting up Azure Key Vault Client](https://support.microsoft.com/help/4040305/setting-up-a-key-vault-client). **Class name** – Select the class where specifics of the integration with the fiscal service are implemented. The available class is **CashRegisterProcessingEFSTA_W**. |
| Configurations | For each cash register, select the ER formats to use to print receipts, send requests to the fiscal service, and receive responses from the fiscal service. The ER formats that you select must be appropriate for the legal entity's primary address. | For example, for the receipt format, select **Cash receipt format (AT)** for Austria and **Cash receipt format (CZ)** for the Czech Republic. If you can't find a format in the list, you can download recent electronic formats from LCS. For more information, see [Download Electronic reporting configurations from Lifecycle Service](/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs). |
| Cash register certificate settings | Enable usage of self-signed certificates. | **Use a self-signed certificate** – Set this option to **Yes** if you use a self-generated, self-signed certificate that you can't add to the list of trusted certificates. **Cash register certificate thumbprint** – Enter the thumbprint of the self-signed certificate that is stored in a fiscal service, and that is used to validate the fiscal service certificate. |

### Cash register locations

Set up the locations of cash registers on the **Cash register locations** page (**Accounts receivable** &gt; **Setup** &gt; **Cash registers** &gt; **Cash register locations**).

#### Prerequisites for the Czech Republic

Before you set up cash register locations for a legal entity that has its primary address in the Czech Republic, complete these steps:

1. Create a tax registration type for the BP ID by selecting **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration types**.

    Restrict this registration type to **Organization**.

1. Associate the registration type with the **Business Premise ID** registration category:

    1. Select **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration categories**.
    1. Select the registration type that you created earlier, and then, in the **Registration category** field, select **Business Premise ID**.

1. Associate the BP ID with the operating unit address of the operating unit that you use for the cash register location.

    1. Select **Organization administration** &gt; **Common** &gt; **Organizations** &gt; **Internal organizations**.
    1. Select the organization to associate with the BP ID.
    1. On the **Addresses** FastTab, select **More options** &gt; **Advanced**.
    1. On the **Registration ID** FastTab, select **Add**.
    1. Select the registration type that you created earlier.
    1. Enter the registration number.

### Create cash register terminals

Create the cash register terminals that are available for the location. Then, assign the cash register to the terminal on the **Cash register terminals** page (**Accounts receivable** &gt; **Setup** &gt; **Cash registers** &gt; **Cash register terminals**).

### Assign the user to a person

Assign the user who acts as a cash operator and logs cash transactions registered in the cash register to a person. Select **System administration** &gt; **Users** to assign a user to a person.

### Set up cash register operators

Select **Accounts receivable** &gt; **Setup** &gt; **Cash register** &gt; **Cash register operators** to set up cash register operators, assign them to the cash register location, and assign a default terminal.

### Set up methods of payment that require fiscal registration

Set up methods of payment that require registration in a cash register. Select **Accounts receivable** > **Setup** > **Cash registers** > **Cash register methods of payment**, and then set the following fields.

| Field | Description |
|---|---|
| Method of payment | Select a method of payment that requires registration in the cash register and sending to the fiscal service. |
| Register tax amount | Select the check box to indicate that the tax amounts related to a cash payment amount must be registered in the fiscal service. |

> [!IMPORTANT]
> In the following scenarios, you can reliably identify the tax amounts related to the payment amount from the posted transactions:

- For the cash payment that the system automatically posts when you post a cash on delivery (COD) invoice (COD terms of payment). In this case, the tax amounts that you send are equal to the tax amounts that the invoice posting produces.
- For the cash prepayment that you manually post from the Customer payment journal, when sales tax amounts are calculated and posted from the payment journal. (Tax amounts that the system posts from a prepayment are always sent, regardless of the setting of the **Register tax amount** check box.)

Consult the local tax authority to identify the requirements for registering tax amounts related to a cash payment in the cash register. Split methods of payment as required.

In the following scenarios, you can't reliably identify the tax amounts related to the payment amount from the posted transactions:

- For the cash payment that you manually post from the Customer payment journal and settle against the previously posted invoice that contains a posted tax amount.

If you configure the Cash register method of payment to register tax amounts, a specific amount distribution logic calculates approximate tax amounts, based on the payment amount, in this scenario.

In these scenarios, the correct tax amounts appear only in the posted invoice that you settle. Consult the local tax authority to identify the correct method for submitting the invoiced tax amounts to tax authority checks for these scenarios.

### Create terms of payment for a COD scenario

If you can receive a cash payment when you post an invoice, create terms of payment that use the **Cash on delivery** payment method. Select **Account receivables** > **Payment** > **Terms of payment**, and then set the following fields.

| Field | Description |
|---|---|
| Payment method | Select **COD**. |
| Cash payment | Set the option to **Yes** to create an automatic payment transaction. |
| Cash | Select the general ledger account that you use to post cash payments that are automatically generated. |

## Example

This section walks you through the following business processes and uses the [EFSTA Fiscal Register (EFR)](https://public.efsta.net/efr/) fiscal service as an example:

- After you post a cash payment that is liable for registration, you create a cash register transaction that has data that must be signed. You send this transaction, in the specified XML format, to the fiscal service for registration.
- You receive a response from the fiscal service. This response has a signature and fiscal codes that the fiscal service generates according to country/region-specific rules. You store this response in the cash register fiscal transaction.
- You print the cash receipt. This receipt includes the transaction data, signatures, and fiscal codes.

### Register an automatically posted COD payment for a free text invoice and print a cash receipt

1. Select **Accounts receivable** &gt; **Free text invoices** &gt; **All free text invoices**.
1. Create a free text invoice. For more information, see [Create free text invoices](../../accounts-receivable/create-free-text-invoice-new.md). 
1. On the **Payment** FastTab, select a method of payment that you set up as a method of payment for the cash register.
1. Select terms of payment that you set up for COD.
1. Select **Post**.
1. In the **Post free text invoice** dialog box, follow these steps:

    1. On the **Parameters** FastTab, select the **Print receipt** check box to print a cash receipt after the invoice is posted.
    1. On the **Cash register** FastTab, review the location, terminal, cash register, and operator codes. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment is received at a different cash register terminal that is available for the current operator.
    1. Select **OK**.

1. Review the cash receipt that is generated for the posted invoice. By default, the generated cash receipt is available as a file. For information about how to set up other destinations that you can use for cash receipts, see [Electronic Reporting Destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).


### Register an automatically posted COD payment for a sales order invoice and print a cash receipt

1. Select **Accounts receivable** &gt; **Orders** &gt; **All sales orders**.
1. Create a sales order. For more information, see [Create sales orders](../../../supply-chain/sales-marketing/tasks/create-sales-orders.md).
1. On the **Price and discount** FastTab, select a method of payment that you set up as a method of payment for the cash register.
1. In the **Payment** field, select terms of payment that you set up for COD.
1. Select **Invoice** &gt; **Invoice**.
1. On the **Parameters** FastTab,set the **Print receipt** option to **Yes** to print a cash receipt after the invoice is posted.
1. On the **Cash register** FastTab, review the location, terminal, cash register, and operator codes. Modify the information as you require. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment is received at a different cash register terminal that is available for the current operator.

### Register a customer payment from the Customer payment journal and print a cash receipt

1. Select **Accounts receivables** > **Journals** > **Payments** > **Payment journal** to open the Customer payment journal. (Alternatively, select **General ledger** > **Journals** > **General journal** to open the General journal.)
1. Create the journal lines that have a customer cash payment.
1. On the **Payment** tab, select a method of payment that is set up as a method of payment for the cash register.
1. Select the **Prepayment journal voucher** check box if the payment is a prepayment.
1. On the **Payment** tab, review the location, terminal, cash register, and operator codes. Modify the information as you require. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment is received at a different cash register terminal that is available for the current operator.
1. Select **Post** > **Post**.
1. Select **Print** > **Cash receipt** to print a receipt that includes fiscal codes.

### Register a customer payment from the Slip journal and print a cash order that includes cash receipt information (Czech Republic only)

1. Select **Cash and bank management** > **Journals** > **Slip journal**.
1. Create the journal lines that have a customer cash payment.
1. On the **Payment** tab, review the fields in the **Cash register** section. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment was received at a different cash register terminal. 
1. Select **Documents approval** > **Approve**. The cash order number is assigned to the payment.
1. Select **Post** > **Post**.
1. Select **Print** > **Cash order** to print a cash order that includes fiscal codes.

### Cancel a payment

If you register a cash receipt number for a payment in the cash register and then cancel the payment, the same cash register registers a new cash receipt number. The payment cancellation cash receipt includes all the same amounts as the original receipt, but the amounts have a negative sign.

1. Open the **Customer transactions** page:

    1. Select **Accounts receivable** &gt; **Customers** &gt; **All Customers**.
    1. Select a customer.
    1. On the Action Pane, select **Customer** &gt; **Transactions**.

1. Select the payment transaction to reverse.
1. Select **Reverse** &gt; **Cancel payment**.
1. Enter the required information, and then select **OK** to create the payment cancellation transaction and return to the **Customer transactions** page.
1. Select the new payment cancellation transaction, and then select **Print** &gt; **Cash receipt** to print a cash receipt that includes fiscal codes.

### Review cash register fiscal transactions and resend a transaction to the cash register

You can review the cash payments that you registered. You can also reprint the original cash receipt or a copy of the cash receipt by selecting **Print** at **Accounts receivable** &gt; **Inquiries** &gt; **Cash register fiscal transactions**.

The law describes exception scenarios that the fiscal service should correctly handle. If a cash payment isn't successfully registered for a reason that isn't related to one of those exception scenarios, you receive an error message after you post a cash payment. The cash register transaction that has a status of **Created** appears on the **Cash register fiscal transactions** page. You must fix the issues and manually resend the cash transactions that are created to the cash register. Otherwise, you can't print a cash receipt that includes fiscal codes. When a cash payment is correctly registered, it has a status of **Registered**.

The following table describes the fields for cash register payment transactions.

| Field | Description |
|---|---|
| Cash register | The ID of the cash register. |
| Transaction ID | The ID of the transaction in the cash register. The fiscal service provides this value. |
| Cash register URL | The URL of the place where the fiscal service is located. |
| Status | The status of the transaction. The following values are used: **Created** – The payment transaction is posted but isn't registered. **Registered** – The payment transaction is posted and registered. (In other words, you sent the payment transaction to the fiscal service, and you received a response that includes fiscal codes.) |
| (CZ/Czech Republic) Offline | An indicator that the cash transaction was registered offline (allowed exception), and a PKP (signature code) was received. |
| Terminal | The code of the cash register terminal. |
| Operator | The code of the cash register operator. |
| Voucher | The voucher number of the posted cash transaction. |
| Date | The date of the transaction. |
| Receipt number | The number of the cash receipt. |
| Transaction date and time | The date and time of the registered transaction. The fiscal service provides this value. |
| Receipt amount | The payment amount. |
| Currency | The currency of the payment. |
| Name | The name of the fiscal code that the fiscal service provides. The following values can be used: **Info** – Additional information. (AT/Austria) **Code** – Signature. (AT/Austria) **Link** – Signature-dependent link. |
| Label | The label of the fiscal code that the fiscal service provides. The following values can be used: (CZ/Czech Republic) **FIK** – Fiscal identification code. (CZ/Czech Republic) **BKP** – Security code. (CZ/Czech Republic) **PKP** – Signature code (This code is returned in the event of offline registration.) |
| Value | The value of the fiscal code that the fiscal service provides. |
| Value | The percentage of registered tax. |
| Sales tax amount | The amount of registered tax. |
| Gross amount | The amount of the registered payment. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
