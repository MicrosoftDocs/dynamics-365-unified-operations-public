---
title: Fiscal service (ESR) integration
description: This article provides information about the fiscal service integration for Austria and the Czech Republic.
author: AdamTrukawka
ms.date: 01/17/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: kfend
ms.search.region: Austria, Czech Republic
ms.author: atrukawk
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
ms.search.form: CashRegister_W
---

# Fiscal service (ESR) integration

[!include [banner](../includes/banner.md)]

In Austria, all cash payments should be signed by an external device or service, and they should be securely stored. In the Czech Republic, all cash payments should be sent to the government portal for a fiscal signature. In both countries, a cash receipt should be issued where the signature is printed.

To support these country/region-specific requirements, Dynamics 365 Finance lets you integrate with a third-party fiscal service that complies with specific requirements for cash payment control in various countries or regions.

> [!NOTE]
> It's assumed that the third-party fiscal service meets all other country/region-specific legal requirements about registered transactions. You're responsible for correctly setting up and administering the fiscal service.

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

Every cash register must be set up to communicate with the fiscal service. You can set up cash registers on the **Cash registers** page (**Accounts receivable** &gt; **Setup** &gt; **Cash registers** &gt; **Cash registers**). The following table gives more information about the setup that is required.

<table>
<thead>
<tr>
<th>Setup</th>
<th>Details</th>
<th>More information</th>
</tr>
</thead>
<tbody>
<tr>
<td>Cash register settings</td>
<td>Specify the URL of the cash register, the name of the instance of Microsoft Azure Key Vault, and the class name.</td>
<td><ul>
<li><strong>Cash register URL</strong> – Enter the URL of the fiscal service.
<p><strong>Warning:</strong> Third-party services or other services that you configure here don&#39;t require certification, and they might not meet Microsoft privacy standards. You should review each service&#39;s privacy documentation and work with each service provider to learn more about the level of compliance that each service provides. You&#39;re responsible for making sure that these services meet your security-related, privacy-related, and legal standards. You bear the risk of using these services. Microsoft gives no express warranties, guarantees, or conditions. We strongly recommend that you use only services that provide secure and authorized connections (that is, services that use the HTTPS protocol).</p>
</li>
<li><strong>Key Vault name</strong> – If the fiscal service is accessible at a secure connection (that is, the URL starts with https://), you should set up certificates and store them correctly on both sides (the Finance app and the third-party fiscal service). In this field, select the name of the Azure Key Vault instance where the Finance certificate is stored. For more information, see <a href="https://support.microsoft.com/help/4040305/setting-up-a-key-vault-client">Setting up Azure Key Vault Client</a>.</li>
<li><strong>Class name</strong> – Select the class where specifics of the integration with the fiscal service are implemented. The available class is <strong>CashRegisterProcessingEFSTA_W</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>Configurations</td>
<td>For each cash register, select the ER formats to use to print receipts, send requests to the fiscal service, and receive responses from the fiscal service. The ER formats that you select must be appropriate for the legal entity&#39;s primary address.</td>
<td>For example, for the receipt format, select <strong>Cash receipt format (AT)</strong> for Austria and <strong>Cash receipt format (CZ)</strong> for the Czech Republic.

If you can't find a format in the list, you can download recent electronic formats from LCS. For more information, see <a href="/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs">Download Electronic reporting configurations from Lifecycle Service</a>.</td>
</tr>
<tr>
<td>Cash register certificate settings</td>
<td>Enable usage of self-signed certificates.</td>
<td>
<ul>
<li><strong>Use a self-signed certificate</strong> – Set this option to <strong>Yes</strong> if you will use a self-generated, self-signed certificate that you can&#39;t add to the list of trusted certificates.</li>
<li><strong>Cash register certificate thumbprint</strong> – Enter the thumbprint of the self-signed certificate that is stored in a fiscal service, and that will be used to validate the fiscal service certificate.</li>
</ul>
</td>
</tr>
</tbody>
</table>

### Cash register locations

You can set up the locations of cash registers on the **Cash register locations** page (**Accounts receivable** &gt; **Setup** &gt; **Cash registers** &gt; **Cash register locations**).

#### Prerequisites for the Czech Republic

Before you set up cash register locations for a legal entity that has its primary address in the Czech Republic, you must follow these steps.

1. Create a tax registration type for the BP ID by selecting **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration types**.

    This registration type should be restricted to **Organization**.

2. Associate the registration type with the **Business Premise ID** registration category:

    1. Select **Organization administration** &gt; **Global address book** &gt; **Registration types** &gt; **Registration categories**.
    2. Select the registration type that you created earlier, and then, in the **Registration category** field, select **Business Premise ID**.

3. Associate the BP ID with the operating unit address of the operating unit that will be used for the cash register location.

    1. Select **Organization administration** &gt; **Common** &gt; **Organizations** &gt; **Internal organizations**.
    2. Select the organization to associate with the BP ID.
    3. On the **Addresses** FastTab, select **More options** &gt; **Advanced**.
    4. On the **Registration ID** FastTab, select **Add**.
    5. Select the registration type that you created earlier.
    6. Enter the registration number.

### Create cash register terminals

You can create the cash register terminals that will be available for the location, and then assign the cash register to the terminal, on the **Cash register terminals** page (**Accounts receivable** &gt; **Setup** &gt; **Cash registers** &gt; **Cash register terminals**).

### Assign the user to a person

The user who will act as a cash operator, and who will be allowed to log cash transactions that are registered in the cash register, must be assigned to a person. You can assign a user to a person by selecting **System administration** &gt; **Users**.

### Set up cash register operators

You can set up cash register operators, assign them to the cash register location, and assign a default terminal by selecting **Accounts receivable** &gt; **Setup** &gt; **Cash register** &gt; **Cash register operators**.

### Set up methods of payment that require fiscal registration

You can set up methods of payment that must be registered in a cash register. Select **Accounts receivable** &gt; **Setup** &gt; **Cash registers** &gt; **Cash register methods of payment**, and then set the following fields.

| Field | Description |
|---|---|
| Method of payment | Select a method of payment that must be registered in the cash register and sent to the fiscal service. |
| Register tax amount | Select the check box to indicate that the tax amounts that are related to a cash payment amount must be registered in the fiscal service. |

#### Important notices

In the following scenarios, the tax amounts that are related to the payment amount can be reliably identified from the posted transactions:

- For the cash payment that is automatically posted when a cash on delivery (COD) invoice (COD terms of payment) is posted. In this case, tax amounts that are sent are equal to the tax amounts that are produced by an invoice posting.
- For the cash prepayment that is manually posted from the Customer payment journal, when sales tax amounts are calculated and posted from the payment journal. (Tax amounts that are posted from a prepayment are always sent, regardless of the setting of the **Register tax amount** check box.)

You should consult the local tax authority to identify the requirements for registering tax amounts that are related to a cash payment in the cash register. You should split methods of payment as required.

In the following scenarios, the tax amounts that are related to the payment amount can't be reliably identified from the posted transactions:

- For the cash payment that is manually posted from the Customer payment journal and settled against the previously posted invoice that contains a posted tax amount.

If the Cash register method of payment is configured to register tax amounts, a specific amount distribution logic calculates approximate tax amounts, based on the payment amount, in this scenario.

In these scenarios, the correct tax amounts are presented only in the posted invoice that is settled. Consult the local tax authority to identify the correct method for submitting the invoiced tax amounts to tax authority checks for these scenarios.

### Create terms of payment for a COD scenario

If a cash payment can be received when an invoice is posted, you can create terms of payment that have the **Cash on delivery** payment method. Select **Account receivables** &gt; **Payment** &gt; **Terms of payment**, and then set the following fields.

| Field | Description |
|---|---|
| Payment method | Select **COD**. |
| Cash payment | Set the option to **Yes** to create an automatic payment transaction. |
| Cash | Select the general ledger account that is used to post cash payments that are automatically generated. |

## Example

This section walks you through the following business processes and uses the [EFSTA Fiscal Register (EFR)](https://public.efsta.net/efr/) fiscal service as an example:

- After you post a cash payment that is liable for registration, a cash register transaction that has data that must be signed is created. This transaction is then sent, in the specified XML format, to the fiscal service for registration.
- You receive a response from the fiscal service. This response has a signature and fiscal codes that the fiscal service generates according to country/region-specific rules. This response is stored in the cash register fiscal transaction.
- The cash receipt is printed. This receipt includes the transaction data, signatures, and fiscal codes.

### Register an automatically posted COD payment for a free text invoice and print a cash receipt

1. Select **Accounts receivable** &gt; **Free text invoices** &gt; **All free text invoices**.
2. Create a free text invoice. For more information, see [Create free text invoices](../accounts-receivable/create-free-text-invoice-new.md). 
3. On the **Payment** FastTab, select a method of payment that is set up as a method of payment for the cash register.
4. Select terms of payment that are set up for COD.
5. Select **Post**.
6. In the **Post free text invoice** dialog box, follow these steps:

    1. On the **Parameters** FastTab, select the **Print receipt** check box to print a cash receipt after the invoice is posted.
    2. On the **Cash register** FastTab, review the location, terminal, cash register, and operator codes. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment is received at a different cash register terminal that is available for the current operator.
    3. Select **OK**.

7. Review the cash receipt that is generated for the posted invoice. By default, the generated cash receipt is available as a file. For information about how to set up other destinations that you can use for cash receipts, see [Electronic Reporting Destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).


### Register an automatically posted COD payment for a sales order invoice and print a cash receipt

1. Select **Accounts receivable** &gt; **Orders** &gt; **All sales orders**.
2. Create a sales order. For more information, see [Create sales orders](../../supply-chain/sales-marketing/tasks/create-sales-orders.md).
3. On the **Price and discount** FastTab, select a method of payment that is set up as a method of payment for the cash register.
4. In the **Payment** field, select terms of payment that are set up for COD.
5. Select **Invoice** &gt; **Invoice**.
6. On the **Parameters** FastTab,set the **Print receipt** option to **Yes** to print a cash receipt after the invoice is posted.
7. On the **Cash register** FastTab, review the location, terminal, cash register, and operator codes. Modify the information as you require. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment is received at a different cash register terminal that is available for the current operator.

### Register a customer payment from the Customer payment journal and print a cash receipt

1. Select **Accounts receivables** &gt; **Journals** &gt; **Payments** &gt; **Payment journal** to open the Customer payment journal. (Alternatively, select **General ledger** &gt; **Journals** &gt; **General journal** to open the General journal.)
2. Create the journal lines that have a customer cash payment.
3. On the **Payment** tab, select a method of payment that is set up as a method of payment for the cash register.
4. Select the **Prepayment journal voucher** check box if the payment is a prepayment.
5. On the **Payment** tab, review the location, terminal, cash register, and operator codes. Modify the information as you require. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment is received at a different cash register terminal that is available for the current operator.
6. Select **Post** &gt; **Post**.
7. Select **Print** &gt; **Cash receipt** to print a receipt that includes fiscal codes.

### Register a customer payment from the Slip journal and print a cash order that includes cash receipt information (Czech Republic only)

1. Select **Cash and bank management** &gt; **Journals** &gt; **Slip journal**.
2. Create the journal lines that have a customer cash payment.
3. On the **Payment** tab, review the fields in the **Cash register** section. The terminal code is automatically filled from the **Default cash register terminal** field on the **Cash register operators** page. Change the terminal code only if the cash payment was received at a different cash register terminal. 
4. Select **Documents approval** &gt; **Approve**. The cash order number is assigned to the payment.
5. Select **Post** &gt; **Post**.
6. Select **Print** &gt; **Cash order** to print a cash order that includes fiscal codes.

### Cancel a payment

If a cash receipt number has been registered for a payment in the cash register, and you then cancel the payment, a new cash receipt number is registered in the same cash register. The payment cancellation cash receipt includes all the same amounts as the original receipt, but the amounts have a negative sign.

1. Open the **Customer transactions** page:

    1. Select **Accounts receivable** &gt; **Customers** &gt; **All Customers**.
    2. Select a customer.
    3. On the Action Pane, select **Customer** &gt; **Transactions**.

2. Select the payment transaction to reverse.
3. Select **Reverse** &gt; **Cancel payment**.
3. Enter the required information, and then select **OK** to create the payment cancellation transaction and return to the **Customer transactions** page.
4. Select the new payment cancellation transaction, and then select **Print** &gt; **Cash receipt** to print a cash receipt that includes fiscal codes.

### Review cash register fiscal transactions and resend a transaction to the cash register

You can review the cash payments that have been registered, and also reprint Cash receipt original or a copu of Cash receipt, by selecting **Print** at the **Accounts receivable** &gt; **Inquires** &gt; **Cash register fiscal transactions**.

The law describes exception scenarios that the fiscal service should correctly handle. If a cash payment wasn't successfully registered for a reason that isn't related to one of those exception scenarios, you will receive an error message after you post a cash payment. The cash register transaction that has a status of **Created** will be available on the **Cash register fiscal transactions** page. You must fix the issues and manually resend the cash transactions that are created to the cash register. Otherwise, you can't print a cash receipt that includes fiscal codes. When a cash payment is correctly registered, it has a status of **Registered**.

The following table describes the fields for cash register payment transactions.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Cash register</td>
<td>The ID of the cash register.</td>
</tr>
<tr>
<td>Transaction ID</td>
<td>The ID of the transaction in the cash register. This value is received from the fiscal service.</td>
</tr>
<tr>
<td>Cash register URL</td>
<td>The URL of the place where the fiscal service is located.</td>
</tr>
<tr>
<td>Status</td>
<td>The status of the transaction. The following values are used:
<ul>
<li><strong>Created</strong> – The payment transaction has been posted but hasn&#39;t been registered.</li>
<li><strong>Registered</strong> – The payment transaction has been posted and registered. (In other words, you&#39;ve sent the payment transaction to the fiscal service, and you&#39;ve received a response that includes fiscal codes.)</li>
</ul></td>
</tr>
<tr>
<td>(CZ/Czech Republic) Offline</td>
<td>An indicator that the cash transaction was registered offline (allowed exception), and a PKP (signature code) was received.</td>
</tr>
<tr>
<td>Terminal</td>
<td>The code of the cash register terminal.</td>
</tr>
<tr>
<td>Operator</td>
<td>The code of the cash register operator.</td>
</tr>
<tr>
<td>Voucher</td>
<td>The voucher number of the posted cash transaction.</td>
</tr>
<tr>
<td>Date</td>
<td>The date of the transaction.</td>
</tr>
<tr>
<td>Receipt number</td>
<td>The number of the cash receipt.</td>
</tr>
<tr>
<td>Transaction date and time</td>
<td>The date and time of the registered transaction. This value is received from the fiscal service.</td>
</tr>
<tr>
<td>Receipt amount</td>
<td>The payment amount.</td>
</tr>
<tr>
<td>Currency</td>
<td>The currency of the payment.</td>
</tr>
<tr>
<td>Name</td>
<td>The name of the fiscal code that is received from the fiscal service. The following values can be used:
<ul>
<li><strong>Info</strong> – Additional information</li>
<li>(AT/Austria) <strong>Code</strong> – Signature</li>
<li>(AT/Austria) <strong>Link</strong> – Signature-dependent link</li>
</ul>
</td>
</tr>
<tr>
<td>Label</td>
<td>The label of the fiscal code that is received from the fiscal service. The following values can be used:
<ul>
<li>(CZ/Czech Republic) <strong>FIK</strong> – Fiscal identification code</li>
<li>(CZ/Czech Republic) <strong>BKP</strong> – Security code</li>
<li>(CZ/Czech Republic) <strong>PKP</strong> – Signature code (This code is returned in the event of offline registration.)</li>
</ul>
</td>
</tr>
<tr>
<td>Value</td>
<td>The value of the fiscal code that is received from the fiscal service.</td>
</tr>
<tr>
<td>Value</td>
<td>The percentage of registered tax.</td>
</tr>
<tr>
<td>Sales tax amount</td>
<td>The amount of registered tax.</td>
</tr>
<tr>
<td>Gross amount</td>
<td>The amount of the registered payment.</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
