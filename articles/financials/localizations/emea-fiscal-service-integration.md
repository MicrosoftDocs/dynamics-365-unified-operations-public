---
# required metadata

title: Fiscal service (ESR) integration
description: This topic provides information about the Fiscal service integration for Austria and the Czech Republic.
author: Anasyash
manager: AnnBe
ms.date: 11/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics365operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Austria, Czech Republic 
# ms.search.industry: 
ms.author: Anasyash
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Fiscal service (ESR) integration

[!include[banner](../includes/banner.md)]

In Austria, all cash payments should be signed by an external device or service and securely stored. In Czech Republic, all cash payments should be sent to the government portal for a fiscal signature. In both countries, a cash receipt should be issued where the signature is printed.

To support these requirements for these two countries, Microsoft Dynamics 365 for Finance and Operations, Enterprise edition allows you to integrate with a fiscal service that is compliant with specific requirements for cash payment control in different countries. 

> [!NOTE]
> It's assumed that all other specific country legal requirements concerning the registered transactions are fulfilled on the side of fiscal service and it is the user's responsibility to properly set up and administer the third-party fiscal service.

## Available configurations
The following configurations are available:

<table class="table ng-scope">
	<tbody>
		<tr>
			<td width="198">
			<p><span><strong>Configuration Name</strong></span></p>
			</td>
			<td width="208" class="x-hidden-focus">
			<p><span><strong>Configuration Description</strong></span></p>
			</td>
			<td width="227">
			<p><span><strong>Comment</strong></span></p>
			</td>
			<td width="227"><strong>GER configuration files in LCS Shared Asset Library</strong></td>
		</tr>
		<tr>
			<td width="198">
			<p><span><strong>Cash Receipt Model</strong></span></p>
			</td>
			<td width="208" class="x-hidden-focus">
			<p><span><strong><span lang="EN-US"> </span></strong></span></p>
			</td>
			<td width="227">
			<p><span><strong>Data model for cash receipt format</strong></span></p>
			</td>
			<td width="227"><strong>Cash Receipt Model.version.1.xml</strong></td>
		</tr>
		<tr>
			<td width="198">
			<p><span> Cash Receipt Format</span></p>
			</td>
			<td width="208">
			<p><span><span> </span></span></p>
			</td>
			<td width="227">
			<p><span class="x-hidden-focus">Basic format for cash receipt</span></p>
			</td>
			<td width="227">Cash Receipt Format.version.1.1.xml</td>
		</tr>
		<tr>
			<td width="198">
			<p><span> Cash Receipt Format (AT)</span></p>
			</td>
			<td width="208">
			<p><span><span lang="EN-US"> </span></span></p>
			</td>
			<td width="227">
			<p><span>Format for cash receipt in Austria (incl. QR code)</span></p>
			</td>
			<td width="227">Cash Receipt Format (AT).version.1.1.1.xml</td>
		</tr>
		<tr>
			<td width="198">
			<p><span> Cash Receipt Format (CZ)</span></p>
			</td>
			<td width="208">
			<p><span><span lang="EN-US"> </span></span></p>
			</td>
			<td width="227" class="x-hidden-focus">
			<p><span>Format for cash receipt in Czech Republic (incl. BP Id)</span></p>
			</td>
			<td width="227">Cash Receipt Format (CZ).version.1.1.1.xml</td>
		</tr>
		<tr>
			<td width="198">
			<p><span><strong>Cash Register Model</strong></span></p>
			</td>
			<td width="208">
			<p><span><strong><span lang="EN-US"> </span></strong></span></p>
			</td>
			<td width="227">
			<p><span><strong>Data model for cash register integration</strong></span></p>
			</td>
			<td width="227"><strong>Cash Register Model</strong>.<strong>version.1.xml</strong></td>
		</tr>
		<tr>
			<td width="198">
			<p><span> ESR Request example</span></p>
			</td>
			<td width="208">
			<p><span>EFSTA Simple Receipt Request example</span></p>
			</td>
			<td width="227">
			<p><span>Basic format for Sample XML request to Fiscal service EFSTA (could be used in Austria)</span></p>
			</td>
			<td width="227">ESR Request example.version.1.1.xml</td>
		</tr>
		<tr>
			<td width="198">
			<p><span> ESR Request example (CZ)</span></p>
			</td>
			<td width="208">
			<p><span>EFSTA Simple Receipt Request example (CZ)</span></p>
			</td>
			<td width="227">
			<p><span>Format for Sample XML request to Fiscal service EFSTA in Czech Republic</span></p>
			</td>
			<td width="227">ESR Request example (CZ).version.1.1.1.xml</td>
		</tr>
		<tr>
			<td width="198">
			<p><span> ESR Response example</span></p>
			</td>
			<td width="208">
			<p><span>EFSTA Simple Receipt Response example</span></p>
			</td>
			<td width="227">
			<p><span>Basic format for Sample XML response to Fiscal service EFSTA (could be used in Austria)</span></p>
			</td>
			<td width="227">ESR Response example.version.1.1.xml</td>
		</tr>
		<tr>
			<td width="198">
			<p><span> ESR Response example (CZ)</span></p>
			</td>
			<td width="208">
			<p><span>EFSTA Simple Receipt Response example (CZ)</span></p>
			</td>
			<td width="227">
			<p><span>Format for Sample XML response to Fiscal service EFSTA in Czech Republic</span></p>
			</td>
			<td width="227">ESR Response example (CZ).<strong>version</strong>.1.1.1.xml</td>
		</tr>
	</tbody>
</table>

## Setup

### Cash registers 
Each cash register must be set up to communicate with the fiscal service. You can set up cash registers on the **Cash registers** page (**Accounts receivable** > **Setup** > **Cash registers** > **Cash registers**). Refer to the following table for more information.

<table> 
<tr>
	<td><strong>Setup</strong></td>
<td><strong>Details</strong></td>
<td><strong>More information</strong></td></tr>
<tr>
	<td>Cash Register settings</td>
	<td>Enter the <strong>Cash register URL</strong>, the <strong>Certificate</strong> and the <strong>Class name</strong>.</td>
	<td><p><strong>Cash register URL</strong> - Enter the URL for the Fiscal service. <strong>WARNING</strong>: Third party services or other services that you configure here do not require a certification and they might not meet Microsoft privacy standards. You should review each service's privacy documentation and work with each service provider to learn more about each service's provided level of compliance. You are responsible for ensuring that these services meet your security, privacy and legal standards. You bear the risk of using it. Microsoft gives no express warranties, guarantees or conditions. It is strongly recommended that you use only services that provide secure and authorized connections (https://).</p>
		<p><strong>Certificate</strong> - </p>
		<p><strong>Class name</strong> - </p>
	</td>
	</tr>
<tr>
<td>Configurations</td>
<td>For each cash register, select the electronic reporting formats that are appropriate for the legal entity's primary address.	</td>
<td><p><strong>Example</strong>: For the receipt format, select "Cash receipt format (AT)" for Austria and "Cash receipt format(CZ) for the Czech Republic.</p> 
	<p>If you can't find a format in the list, you can download recent electronic formats from Lifecycle Services. For more information, see <a href="https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs"> Download Electronic reporting configurations</a>.</p>
	</td>
</tr>
<tr>
<td>Cash register certificate settings</td>
<td>If the fiscal service is accessible at a secure connection (https://), you should set up certificates and store them properly on both sides – Microsoft Dynamics 365 for Finance and Operations, Enterprise edition and the third party fiscal service.</td>
	<td><p><strong>Use a self-signed certificate</strong> - Select <strong>yes</strong> if you are going to use a self-generated and self-signed certificate which you are not able to add in the list of trusted certificates.</p><p><strong>Cash register certificate thumbprint</strong> - Enter the thumbprint of the self-signed certificate that is stored in a fiscal service which will be used for validating the fiscal service certificate.</p></td>
</tr>
</table>

### Cash register locations
You can set up locations of cash registers on the **Cash register locations** page (**Accounts receivable** > **Setup** > **Cash registers** > **Cash register locations**). 

#### Czech Republic prerequisites
Before you set up cash register locations for a legal entity with a primary address in the Czech Republic, you must do the following:

1. Create a tax registration type for Business Premises ID (**Organization administration** > **Global address book** > **Registration types** > **Registration types**). 
	1. This registration type should be restricted to **Organization**.
2. Associate the registration type that you created in step one with the registration category **Business Premise ID**.
	1. Go to **Organization administration** > **Global address book** > **Registration types** > **Registration categories**. 
	2. Select the registration type that you created earlier, and then select **Business Premise ID** for the **Registration category**.
3. Associate the Business Premises ID number with the operating unit address for the operating unit that you will use for the cash register loation. 
	1. Go to **Organization administration** > **Common** > **Organizations** > **Internal organizations**.
	2. Select the organization to associate with the Business Premise ID number.
	3. Expand the **Addresses** FastTab and click **More options** > **Advanced**. 
	4. On the **Registration Id** FastTab, click **Add**. 
	5. Select the registration type that you created in step one earlier.
	6. Enter the registration number.

### Create cash register terminals
Create cash register terminals on the **Cash register terminals** page (**Accounts receivable** > **Setup** > **Cash registers** > **Cash register terminals**).

### Assign the user to a person
Assign a User who is acting as cash operator and is allowed to log a cash transaction which will be registered in cash register, to a Person in **System administration** > **Users**. 

### Set up cash register operators
Set up cash register operators and assign them to the cash register location in **Accounts receivable** > **Setup** > **Cash register** > **Cash register operators**. 

### Set up methods of payment that require fiscal registration
Set up methods of payment, which needs to be registered in cash register at **Accounts receivable** > **Setup** > **Cash registers** > **Cash register methods of payment**. 

|Field |Description |
|--|-------|
|Method of payment|Choose a method of payment which needs to be registered in cash register and sent to Fiscal service.|
|Register tax amount|Activate the check box if the tax amounts related to the cash payment amount need to be registered in Fiscal service.|

#### Important notices
In the following scenarios, the tax amounts related to the payment amount can be identified reliably from the posted transactions:
- For the cash payment posted automatically during posting of a COD invoice (cash on delivery terms of payment), tax amounts sent are equal to the tax amounts produced by an invoice posting.
- For the cash prepayment posted manually from the customer payment journal, when sales tax amounts are calculated and posted from the payment journal (tax amounts posted from the prepayment are always sent irrespectively from the parameter Register tax amount).
User should consult with local tax authority to identify the requirements to registering the tax amounts related to the cash payment in the cash register. User should split methods of payment if necessary.

In the following scenarios, the tax amounts related to payment amount can't be identified reliably from the posted transactions:
- For the cash payment posted manually from the customer payment journal and settled to the previously posted invoice which contains a posted tax amount.
- If you set up to send these tax amounts to cash register, they can't be considered as fully correct tax amounts but rather rough tax amounts are calculated from the payment amount by a specific amount distribution logic. 

In these scenarios, the correct tax amounts are presented only in the settled posted invoice. Consult with local tax authority to identify the right way for submitting the invoiced tax amounts to tax authority checks for these scenarios.

### Create terms of payment for cash on delivery scenario
Create Terms of payment with Cash on delivery payment method if a cash payment can be received in the moment of an invoice posting, at **Account receivables** > **Payment** > **Terms of payment**.

|Field |Description |
|--|-------|
|Payment method |Choose "COD".|
|Cash payment| Enable the parameter to create an automatic payment transaction.|
|Cash| Choose G/L account for posting of an automatically generated cash payment.| 

## Example
This section walks you through the following business processes using the [EFR](http://public.efsta.net/efr/) fiscal service provided by EFSTA(European Fiscal Standards Association) as an example.

- After you post a cash payment that is liable for registration, a cash register transaction with data to be signed is created and sent for the registration to fiscal service in the specified XML format. 
- Response with a signature and fiscal codes (generated by Fiscal service per country-specific rules) is received from the fiscal service and stored in the Cash register fiscal transaction.
- The cash receipt with transaction data and signatures/fiscal codes is printed.

### Register automatically posted COD payment for the Free text invoice and print cash receipt
1. Go to **Accounts receivable** > **Free text invoices** > **All free text invoices**.
2. Create a free text invoice. For more information, see [Create a free text invoice](../accounts-receivable/tasks/create-free-text-invoice.md).
3. On the **Payment** FastTab, select the method of payment that is set up as cash a register method of payment. 
4. Select a terms of payment that is set up for cash on delivery. 
5. Click **Post**.
6. In the **Post free text invoice** dialog, do the following:
	1. Activate the check-box **Print receipt** in the fast tab **Parameters** for printing the cash receipt after the invoice is posted.
	2. On fast tab **Cash register** review the location, terminal, cash register and operator code. The terminal code is pre-filled from the **Default cash register terminal** field in the **Cash register operators** page. Change the Terminal code only if the cash payment is received in a different cash register terminal available for the current operator.
	3. Click **OK**.
7. Review the generated cash receipt for the posted invoice. By default, the generated cash receipt is available as a file. For information about how to set up other destinations that you could use for cash receipt output, see [Electronic Reporting Destinations](../../dev-itpro/analytics/electronic-reporting-destinations.md).


### Register automatically posted COD payment for the Sales order invoice and print cash receipt
1. Go to **Accounts receivable** > **Orders** > **All sales orders**.
2. Create a sales order. For more information, see [Create a sales order](../../supply-chain/sales-marketing/tasks/create-sales-orders.md).
3. On fast tab Price and discount, choose Method of payment which is set up as a cash register method of payment. Choose Terms of payment with cash on delivery settings in the **Payment field**.
4. Click **Invoice** > **Invoice**.
5. Expand the **Parameters** FastTab and select the **Print receipt** check box to print a cash receipt after the invoice is posted.
6. On the **Cash register** FastTab, review and modify the following information if necessary: Location, Terminal, Cash register and Operator code. The terminal code is pre-filled from the **Default cash register terminal** field in the **Cash register operators** page. Change the Terminal code only if the cash payment is received in a different cash register terminal available for the current operator.

### Register customer payment from Customer payment journal and print cash receipt

1. Go to Customer payment journal at **Accounts receivables** > **Journals** > **Payments** > **Payment journal** (or General journal at **General ledger** > **Journals** > **General journal**).
2. Create the journal lines with a customer cash payment. 
3. On the **Payment** tab, select a method of payment that is set up as a cash register method of payment. Select the **Prepayment journal voucher** check box if this is a prepayment. 
4. On tab **Payment**, review and modify the following information if necessary: Location, Terminal, Cash register and Operator code. The terminal code is pre-filled from the **Default cash register terminal** field in the **Cash register operators** page. Change the Terminal code only if the cash payment is received in a different cash register terminal available for the current operator. 
5. Click **Post** > **Post**. 
6. Click **Print** > **Cash receipt** to print a receipt with fiscal codes.

### Register customer payment from Slip journal and print cash order with cash receipt information (Czech Republic only)

1. Go to **Cash and bank management** > **Journals** > **Slip journal**.
2. Create the journal lines with a customer cash payment.
3. On the **Payment** tab, review the fields in the **Cash register** section. 
4. Modify the **Terminal code** only if the cash payment was received in a different cash register terminal. The terminal code is auto-filled from the **Default cash register terminal** field on the **Cash register operators** page. 
5. Click **Documents approval** > **Approve**. The cash order number is assigned to the payment.
6. Click **Post** > **Post**.  
7. Click **Print** > **Cash order** to print a cash order that includes fiscal codes.

### Cancel a payment

If the payment to be cancelled has been registered in the cash register with a cash receipt number, then a new cash receipt number with a negative amount will be registered in the same cash register when you cancel the payment. The payment cancellation cash receipt will include the same amounts as the initial receipt except with a negative sign.

1. Go to the **Customer transactions** page.
	1. Go to **Accounts receivable** > **Customers** > **All Customers**. 
	2. Select a customer.
	3. On the Action Pane, click **Customer** > **Transactions**. 
2. Select the payment transaction to reverse.
3. Click **Reverse** > **Cancel payment**.
3. Enter the necessary information and then click **OK** to create the payment cancellation transaction and return to the **Customer transactions** page. 
4. Select the newly created payment cancellation transaction and then click **Print** > **Cash receipt** to print a cash receipt that includes fiscal codes.

### Review Cash register fiscal transactions. Resend transaction to cash register.

You can review the registered cash payments, and you can also reprint the original cash receipt or a copy of the cash receipt from the  original and copy at **Accounts receivable** > **Inquires** > **Cash register fiscal transactions**.

If the cash payment wasn't successfully registered for a reason that is not related to the exception scenarios described in the law which should be correctly handled on fiscal service side, you will get an error message after a posting a cash payment. The cash register transaction with a status of **Created** will be available on the **Cash register fiscal transactions** page. You must fix issues and manually resend the created cash transactions to the cash register. Otherwise, you cannot print the cash receipt with fiscal codes. When a cash payment is correctly registered, it will have a status of **Registered**.

Fields description for the Cash register payment transactions:

<table >
		<tr>
			<td >
			<p><strong>Field</strong></p>
			</td>
			<td >
			<p><strong>Description</strong></p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Cash register</p>
			</td>
			<td>
			<p>ID of cash register</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Transaction ID</p>
			</td>
			<td>
			<p>ID of transaction in cash register</p>
			<p>This value is received from Fiscal service.</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Cash register URL</p>
			</td>
			<td>
			<p>URL of the place where Fiscal service is located.</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Status</p>
			</td>
			<td>
			<p>Status of transaction. Possible values:</p>
				<ul><li>Created. The payment transaction is posted, but not registered.</li>
			<li>Registered The payment transaction is posted and registered (sent to Fiscal service and received response with fiscal codes). </li></ul>
			</td>
		</tr>
		<tr>
			<td>
			<p>CZ/Czech republic: Offline </p>
			</td>
			<td>
			<p>Indication that the cash transaction is registered in Offline regime (allowed exception) and PKP code is received. </p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Terminal</p>
			</td>
			<td>
			<p>Code of cash register terminal</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Operator</p>
			</td>
			<td>
			<p>Code of cash register operator</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Voucher</p>
			</td>
			<td>
			<p>Voucher number of posted cash transaction</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Date</p>
			</td>
			<td>
			<p>Date of transaction</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Receipt number</p>
			</td>
			<td>
			<p>Number of cash receipt</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Transaction date and time</p>
			</td>
			<td>
			<p>Date and time of registered transaction</p>
			<p>This value is received from Fiscal service.</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Receipt amount</p>
			</td>
			<td>
			<p>Payment amount</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Currency</p>
			</td>
			<td>
			<p>Currency of payment</p>
			</td>
		</tr>
		<tr>
			<td>Name</td>
			<td>
			<p>Name of fiscal code received from the fiscal service. Possible values:
				<ul>
			<li>Info – additional information</li>
			<li>AT/Austria: Code - signature</li>
			<li>AT/Austria: Link – signature dependent link</li>
				</ul>
				</p>
			</td>
		</tr>
		<tr>
			<td> Label </td>
			<td> <p>Label of the fiscal code received from the fiscal service</p>
			<p>Possible values:
				<ul>
					<li> CZ/Czech Republic: <strong>FIK</strong> – Fiscal Identification Code</li>
			<li> CZ/Czech Republic: <strong>BKP</strong> – Security Code</li>
			<li> CZ/Czech Republic: <strong>PKP</strong> – Signature Code (returned in case of offline registration)</li>
				</ul></p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Value</p>
			</td>
			<td>
			<p>Value of fiscal code received from fiscal service</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Value</p>
			</td>
			<td>
			<p>% of registered tax</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Sales tax amount</p>
			</td>
			<td>
			<p>Amount of registered tax</p>
			</td>
		</tr>
		<tr>
			<td>
			<p>Gross amount</p>
			</td>
			<td>
			<p>Amount of registered payment</p>
			</td>
		</tr>
</table>


