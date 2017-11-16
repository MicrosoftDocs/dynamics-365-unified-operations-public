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

- PostingAfter you post a cash payment that is liable for registration, a cash register transaction with data to be signed is created and sent for the registration to fiscal service in the specified XML format. 
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
2. Create a sales order. For more information, see [Create a sales order](../../supply-chain/sales-marketing/tasks/create-sales-orders.md)
3. On fast tab Price and discount, choose Method of payment which is set up as a cash register method of payment. Choose Terms of payment with cash on delivery settings in the **Payment field**.
4. Click **Invoice** > **Invoice**.
5. In the dialog Posting invoice, in the fast tab Parameters, activate the check-box Print receipt for printing a cash receipt after the invoice is posted.
6. On the fast tab Cash register, review Location, Terminal, Cash register and Operator code. Terminal code is pre-defaulted from the "Default cash register terminal" field in the Cash register operators form. Change Terminal code if the cash payment is received in a different cash register terminal.

### Register customer payment from Customer payment journal and print cash receipt

1. Go to Customer payment journal at **Accounts receivables** > **Journals** > **Payments** > **Payment journal** (or General journal at **General ledger** > **Journals** > **General journal**).
2. Create the journal lines with a customer cash payment in the standard way. 
3. On tab Payment, choose Method of payment which is set up as a cash register method of payment. Activate the check box **Prepayment journal voucher** if this is a prepayment. 
4. On tab **Payment**, review Location, Terminal, Cash register and Operator code. Terminal code is pre-defaulted from the **Default cash register terminal** field in the Cash register operators form. Change Terminal code if the cash payment is received in a different cash register terminal. Click **Post** > **Post**. Click **Print** > **Cash receipt** to print a receipt with fiscal codes.

### CZ/Czech Republic: Register customer payment from Slip journal and print cash order with cash receipt information

1. Go to **Cash and bank management** > **Journals** > **Slip journal**.
2Create the journal lines with a customer cash payment in the standard way. Review Cash register group of fields on tab Payment. Terminal code is pre-defaulted from the "Default cash register terminal" field in the Cash register operators form. Change Terminal code if the cash payment is received in a different cash register terminal.
Click Documents approval > Approve. Cash order number is assigned to payment.
Click Post > Post.  Click Print > Cash order to print a cash order with fiscal codes.

### Cancel payment

If a payment which is being cancelled, has been registered in the cash register with a cash receipt number, the cancel payment will create a new cash receipt number with a negative amount which will also be registered in the same cash register. The payment cancellation cash receipt is presenting fully the same amounts as in an initial receipt but a negative sign.
Go to Customer transactions form. Place cursor on a payment transaction and click Reverse > Cancel payment.
In the dialog Cancel payment, fill necessary information and review values in group of fields Cash register. Click OK.
Place cursor on the new payment cancellation transaction. Click button **Print** > **Cash receipt** to print a cash receipt with fiscal codes.

### Review Cash register fiscal transactions. Resend transaction to cash register.

You can review the registered cash payments, and also reprint Cash receipt original and copy at Accounts receivable > Inquires > Cash register fiscal transactions.

If cash payment wasn't successfully registered for any infrastructural reason (not related with exception scenarios described in the law which should be correctly handled on Fiscal service side), a user will get respective an error message after a posting of cash payment. The cash register transaction in status "Created" will be available in the Cash register fiscal transactions form. User must fix infrastructural issues and manually resend the created cash transactions to the cash register. Otherwise, user is not able to print the cash receipt with fiscal codes. Correctly, the registered transaction gets status "Registered".
Fields description in the form Cash register payment transactions:

<table class="table ng-scope">
	<tbody>
		<tr>
			<td width="189">
			<p class="x-hidden-focus"><strong><span><span><span class="x-hidden-focus">Field </span></span></span></strong></p>
			</td>
			<td width="444">
			<p><strong><span><span><span>Description </span></span></span></strong></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p class="align-right"><span><span><span lang="EN-US"><strong>Tab Overview</strong></span></span></span></p>
			</td>
			<td width="444" class="x-hidden-focus">
			<p><span><span><span lang="EN-US"> </span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Cash register</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Id of cash register</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Transaction Id</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Id of transaction in cash register</span></span></span></p>
			<p><span><span><span lang="EN-US">This value is received from Fiscal service.</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Cash register URL</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">URL of the place where Fiscal service is located.</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Status</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Status of transaction. </span></span></span><span><span><span lang="EN-US">Possible values:</span></span></span></p>
			<p><span><span><strong><u><span lang="EN-US">Created</span></u></strong><span lang="EN-US">. The&nbsp;payment transaction is posted, but not registered.</span></span></span></p>
			<p><span><span><strong><u><span lang="EN-US">Registered</span></u></strong><span lang="EN-US">. The&nbsp;payment transaction is posted and registered (sent to&nbsp;Fiscal service&nbsp;and received response with fiscal codes).</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">CZ/Czech republic: Offline</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Indication that the cash transaction is registered in Offline regime (allowed exception) and PKP code is received.</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Terminal</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Code of cash register terminal</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Operator</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Code of cash register operator</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p align="right"><strong><span><span><span lang="EN-US">Tab General</span></span></span></strong></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US"> </span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Voucher</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Voucher number of posted cash transaction</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Date</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Date of transaction</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Receipt number</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Number of cash receipt</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Transaction date and time</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Date and time of registered transaction</span></span></span></p>
			<p><span><span><span lang="EN-US">This value is received from Fiscal service.</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Receipt amount</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Payment amount</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Currency</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Currency of payment</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p align="right"><span><span><span lang="EN-US"><strong>Tab</strong> <strong>Fiscal codes</strong></span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US"> </span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Name</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Name of fiscal code received from the fiscal service. Possible values:</span></span></span></p>
			<p><span><span><span lang="EN-US">&nbsp;&nbsp; <strong>Info</strong> – additional information</span></span></span></p>
			<p><span><span><span lang="EN-US">&nbsp;&nbsp; AT/Austria: <strong>Code</strong> - signature</span></span></span></p>
			<p><span><span><span lang="EN-US">&nbsp;&nbsp; AT/Austria: <strong>Link </strong>– signature dependent link</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Label</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Label of the fiscal code received from the fiscal service</span></span></span></p>
			<p><span><span><span lang="EN-US">Possible values:</span></span></span></p>
			<p><span><span><span lang="EN-US">&nbsp;&nbsp; CZ/Czech Republic: <strong>FIK</strong> – Fiscal Identification Code</span></span></span></p>
			<p><span><span><span lang="EN-US">&nbsp;&nbsp; CZ/Czech Republic: <strong>BKP</strong> – Security Code</span></span></span></p>
			<p><span><span><span lang="EN-US">&nbsp;&nbsp; CZ/Czech Republic: <strong>PKP</strong> – Signature Code (returned in case of offline registration)</span></span></span></p>
			<p><span><span><span lang="EN-US"> </span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Value</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Value of fiscal code received from fiscal service</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p align="right"><span><span><span lang="EN-US"><strong>Tab Registered tax amounts</strong></span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US"> </span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Value</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">% of registered tax</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Sales tax amount</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Amount of registered tax</span></span></span></p>
			</td>
		</tr>
		<tr>
			<td width="189">
			<p><span><span><span lang="EN-US">Gross amount</span></span></span></p>
			</td>
			<td width="444">
			<p><span><span><span lang="EN-US">Amount of registered payment</span></span></span></p>
			</td>
		</tr>
	</tbody>
</table>


