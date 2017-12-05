---
# required metadata

title: India GST | Microsoft Docs
description: This article provides information about India Goods and Services Tax (GST) for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 
author: ShylaThompson
manager: AnnBe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# keywords: 
audience: IT Pro, Application User
# ms.devlang: 
ms.reviewer: shylaw
# ms.suite: 
# ms.tgt_pltfrm: 
ms.custom: 1587884
ms.search.region: India
ms.search.scope: Core, Operations
# ms.search.industry: 
ms.author: ralin
ms.dyn365.ops.version: 2012
# ms.search.validFrom:
---

# India Goods and Services Tax (GST)

This topic provides a walkthrough of the features that are related to the Goods and Services Tax (GST). Each documented scenario walks you through basic business transactions that typically occur across various business segments in industries of all types. This document also highlights the effect of GST on various type of business transactions, and shows the accounting and posting of transactions of various types.

## Setup

### Create a business vertical
Create business verticals on the Business verticals page (**General ledger** > **Setup** > **Sales tax** > **India** > **Business verticals**).

### Update the state code and union territory
1.	Click **Organization administration** > **Setup** > **Addresses** > **Address setup**.
2.	On the State/province tab, select a state.
3.	In the State code field, enter a value.
4.	Select the Union territory check box to identify the state as a union territory.
5.	Click Close.

### Create a GSTIN master
1.	Click **General ledger** > **Setup** > **Enterprise tax registration numbers**.
2.	Create a record.
3.	In the Tax type field, select GST.
4.	In the Registration number type field, select Company to create state-wide company registration numbers.
5.	In the Type field, verify that GSTIN, GDI, and UID appear in the list. Select a value.
6.	In the Registration number field, enter a value.
7.	In the Description field, enter a value.
8.	In the Business vertical field, select a value.
9.	On the Casual registration FastTab, click Add.
10.	In the From date and To date fields, define the valid period for the casual registration number.
11.	In the Description field, enter a value.
12.	On the Number sequences FastTab, define number sequences for the GST invoice and Bill of supply references.
  -	The GST invoice number sequence will be used when customer sales that have GST transactions are posted
  -	The Bill of supply number sequence will be used when customer sales that have non-GST transactions are posted.

### Define vendor registration numbers for the GST tax type
13.	Create a record.
14.	In the Registration number type field, select Vendors to create state-wide vendor registration numbers.
15.	In the Registration number field, enter value.
16.	In the Description field, enter a value.
17.	In the Business vertical field, select a value.

### Define customer registration numbers for the GST tax type
18.	Create a record.
19.	In the Registration number type field, select Customers to create state-wide customer registration numbers.
20.	In the Registration number enter a value.
21.	In the Description field, enter a value.
22.	In the Business vertical select a value.

### Define GSTIN numbers for the legal entity, warehouse, vendor, or customer masters
#### Legal entity
1.	Click **Organization administration** > **Setup** > **Organizations** > **Legal entities** > **Addresses** > **Edit** > **Tax information**.
2.	Click New.
3.	In the Name or description field, enter a value.
4.	On the GST FastTab, in the GSTIN/GDI/UID field, select a value.
5.	Select the Primary check box.
6.	Click Yes to acknowledge the message.
7.	Click Close.
8.	Repeat steps 2 through 7, for all the other required legal entity addresses.
#### Warehouses
9.	Click **Inventory management** > **Setup** > **Inventor**y > **Inventory breakdown** > **Warehouse** > **Addresses** > **Edit** > **Tax information**.
10.	Click Add.
11.	In the Name or description field, enter a value.
12.	On the GST FastTab, in the GSTIN/GDI/UID field, select a value.
13.	Select the Primary check box.
14.	Click Yes to acknowledge the message.
15.	Save the record.
16.	Click Close.
#### Vendors
17.	Click **Accounts payable** > **Vendors** > **All vendors** > **Addresses** > **Edit** > **Tax information**.
18.	Click Add.
19.	In the Name or description field, enter a value.
20.	On the GST FastTab, in the GSTIN/GDI/UID field, select a value.
21.	Select the Primary check box.
22.	Click Yes to acknowledge the message.
23.	Save the record.
24.	Click Close.
25.	On the Tax information FastTab, select the Composition scheme check box if a composition scheme is used to purchase from the dealer.

#### Customers
26.	Click **Accounts receivable** > **Customers** > **All customers** > **Addresses** > **Edit** > **Tax information**.
27.	Click Add.
28.	In the Name or description field, enter a value.
29.	On the GST FastTab, in the GSTIN/GDI/UID field, select a value.
30.	Select the Primary check box.
31.	Click Yes to acknowledge the message.
32.	Save the record.
33.	Click Close.
34.	On the Tax information FastTab, select the Consumer check box to identify the customer as a consumer.
35.	For customer sales through an e-commerce operator, enter a value in the Merchant ID field, and select a value in the Default E- Commerce operator field.
36.	In the Customer type field, select Govt company or other agencies for sales with government companies or other agencies.

#### HSN codes and Service accounting codes
HSN codes
1.	Click **General ledger** > **Setup** > **Sales tax** > **India** > **HSN code**.
2.	Create a record.
3.	In the Chapter field, enter a value.
4.	In the Heading field, enter a value.
5.	In the Subheading field, enter a value.
6.	In the Country/region extension field, enter a value.
7.	In the Statistical suffix field, enter a value.
8.	Save the record.
9.	Verify that the HSN code field is updated.
10.	In the Description field, enter a value.

11	Click Close.
Service accounting codes
1	Click **General ledger** > **Setup** > **Sales tax** > **India** > **Service accounting codes**.
2	Create a record.
3	In the SAC field, enter a value.
4	In the Description field, enter a value.

5	Click Close.
Assign HSN codes and Service accounting codes to products
1	Click **Product information management** > **Common** > **Released products**.
2	Select an item.
3	On the Action Pane, on the Product tab, in the Maintain group, click Edit.
4	In the HSN code field, select a value.

Note: The following setup is required for the calculation of GST:
●	A Harmonized System of Nomenclature (HSN) code should be defined for the Item item type, or a Service accounting code (SAC) should be defined for the Service item type.
●	Item sales tax group should be removed.
Assign a Service accounting code to miscellaneous charges
Accounts payable
1	Click **Accounts payable** > **Setup** > **Charges** > **Charges code**.
2	Select a charges code.
3	On the Tax information FastTab, enter a value in the SAC or HSN code field.
4	Enter a value in the Service category or ITC Category field.
5	Select the Exempt check box to exempt these charges from the calculation of GST.
6	Save the record.
When this charges code is selected for a transaction, the defined tax information automatically entered, and GST is calculated accordingly.

Accounts receivable
7	Click **Accounts receivable** > **Setup** > **Charges** > **Charges code**.
8	Select a charges code.
9	On the Tax information FastTab, enter a value in the SAC or HSN code field.
10	Select the Exempt check box to exempt this charges from the calculation of GST.
11	Save the record.
When this charges code is selected for a transaction, the defined tax information is automatically entered, and GST is calculated accordingly.
Update number sequences
Accounts payable parameters
1	Click **Accounts payable** > **Setup** > **Accounts payable parameters**.
2	On the Number sequences tab, define a number sequence for Debit note references. This number sequence will be used for purchase debit note transactions.
3	Define a number sequence for GST transaction ID references. This number sequence will be used for vendor advance payment transactions.

Accounts receivable parameters
1	Click **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
2	On the Number sequences tab, define a number sequence for Debit note references. This number sequence will be used for sales debit note transactions.
3	Define a number sequence for GST transaction ID references. This number sequence will be used for customer advance payment transactions.

Create main accounts for the GST posting type
1	Click **General ledger** > **Common** > **Main accounts**.
2	Create a record.
3	In the Main account field, enter a value.
4	In the Name field, enter a value.
5	On the General FastTab, in the Main account type field, select a value.
6	On the Setup FastTab, in the Posting type field, select GST.

7	Repeat steps 2 through 6 to create all the other required state-wide ledger accounts.
8	Click Close.

Create a tax settlement period

1	Click **Accounts payable** > **Vendors** > **All vendors**, and create a GST authority.

2	Click **General ledger** > **Setup** > **Sales tax** > **Sales tax authorities**.

3	Click **General ledger** > **Setup** > **Sales tax** > **Sales tax settlement periods**, and create a tax period for GST.

### Attach the GSTIN to a tax registration group
Click **General ledger** > **Setup** > **Sales tax** > **India** > **Tax registration group**, create a group, and define the required GSTIN.

### Import the configuration and deploy it to a specific company
Save all the configuration files in one folder that the instance of Microsoft Dynamics AX Application Object Server (AOS) can access.
1	Click **General ledger** > **Setup** > **Sales tax** > **India** > **Load configuration**.
2	In the **Directory** field, enter a value.

> [!NOTE]
> Both the tax configuration and the report configuration are saved in the same folder.

3	Click **OK**.
4	Click **Close**.
5	Click **General ledger** > **Setup** > **Sales tax** > **India** > **Tax setup**.
6	Create a record.
7	In the **Tax setup** field, enter a value.
8	In the **Description** field, enter a value.
9	Click **Configurations**.
10	On the **Tax configuration** tab, under **Available configurations**, click **New**.
11	In the **Configurations** field, select a value. The new tax configuration is listed in the **Available configurations** grid.
12	Click **OK**.
13	Click **Synchronize**.
14	Click **Activate**.

  > [!NOTE]
  > The activated configuration is updated as the current configuration.
15	Click the **Report configurations** tab. The **Available configurations** grid lists the configurations that are related to the report.
16	Select the **Select** check box.
17	In the **Report data provider** field, select a value.
18	Click **Close**.
19	On the **Companies** FastTab, create a record.
20	In the **Companies** field, select a value.
21	Save the record.
22	Click **Activate** to activate the configuration for the company.

Update the configuration version
23	Click **Deactivate**.
24	Repeat steps 2 through 5 to load the latest configuration.

25	Click **Configurations**.
26	On the **Tax configuration** tab, under **Available configurations**, click **New**.
27	In the **Configurations** field, select a value.
The new tax configuration is listed in the Available configurations grid.

28	Click **OK**.
29	Select the record, and then click **Synchronize**.
30	Click **Activate**.

Note: The activated configuration is updated as the current configuration.
31	Click **Close**.
32	Click **Activate.

Tax setup
Map configuration tax types to ERP tax types
Tax type - Customs
1	Click **General ledger** > **Setup** > **Sales tax** > **India** > **Tax setup**.
2	Select a company.
3	Click **Setup**.
4	Select the **Customs** node.
5	On the Tax type mapping tab, in the Tax type field, select Customs.

Define a tax period
1	Select the node for the tax component.
2. On the **Tax period mapping** tab, in the **Period** field, select a value.


Define main accounts
1	On the **Accounting** tab, on the **Conditions** FastTab, click **Add**.
2	In the **Import Order** field, select a value.
3	In the **Export order** field, select a value.
4	Save the record.
5	On the **Values** FastTab, in the **Main account** field, select a value.
> [!NOTE]
> The list of accounts is generated dynamically, based on the posting profile from the configuration. Selected Main account should be of posting type ‘Customs’.

6	Select **IGST CUS** node
7	On the **Values** FastTab, in the **Main account** field, select a value.

> [!NOTE]
> Main account selected for Customs duty accrual should be the same account selected for the Customs duty accrual account of the GST > IGST node


Tax type - GST
6.	Click **General ledger** > **Setup** > **Sales tax** > **India** > **Tax setup**.
7.	Select a company.
8.	Click Setup.
9.	Select the GST node.
10.	On the Tax type mapping tab, in the Tax type field, select GST.

Define a tax period
2.	Select the node for the tax component.
3.	On the Tax period mapping tab, in the Period field, select a value.

Define main accounts
8.	On the **Accounting** tab, on the **Conditions** FastTab, click **Add**.
9.	In the **GST Registration Number** field, select a value.
10.	Save the record.
11.	On the **Values** FastTab, in the **Main account** field, select a value.
> [!NOTE]
> The list of accounts is generated dynamically, based on the posting profile from the configuration.
> Tax main accounts can be defined at level of the tax type or the tax component. The value at the tax component level will override the value at the tax type level. If the field is left blank for a posting type at the tax component level, the corresponding value from the tax type level will be used for posting. We recommend that you set up the tax accounts at the tax component level per registration.

Set up rate and percentage tables
1.	Expand the node for the tax Component.
2.	Select the **Rate** node, and then, in the Value field, define the tax rates.
3.	Select the **Reverse Charge Percentage** node, and then, in the **Value** field, define the reverse charge percentage.
4.	Select the **Load on Inventory Percentage** node, and then, in the **Value** field, define the load on inventory percentage.
5.	Click **Close**.
6.	Click **Parameters**.
7.	Click **OK**.

Set up and activate a tax hierarchy tree
Set up the General ledger parameter
1.	Click **General ledger** > **Setup** > **General ledger parameters**.
2.	On the **Sales tax** tab, select the Use the sales tax hierarchy framework check box.
3.	Click **Close**.
Set up a sales tax hierarchy and setoff rules
1.	Click **General ledger** > **Setup** > **Sales tax** > **India** > **Sales tax hierarchies**.
2.	Click **New**.
3.	In the **Name** field, enter a value.
4.	In the **Structure** field, select **GTE hierarchy**.
5.	Click **OK**.
6.	On the **Versions** FastTab, click **Synchronize**.
7.	Close the message.
8	Click **View**. The Sales tax hierarchy designer form shows the tax type and tax components per the configuration.
9.	Click Setoff rules for sales tax hierarchy.
10.	Click New.
11.	In the Name field, enter a value.
12.	Save the record.
13.	On the Recoverable FastTab, select the tax components, and adjust the Priority values.
14.	On the Payable FastTab, select the tax components, and adjust the Priority values.
15.	Define the setoff rules per the legal requirement.
16.	Click Close.
17.	Close the Sales tax hierarchy designer form.
18.	Click Activate.
19.	Click Close.
20.	Click General ledger > Setup > Maintain setoff hierarchy profiles.
21.	Click New.
22.	In the Effective date field, enter a value.
23.	In the Hierarchy field, select a value.
24.	Click OK.
25.	Click Activate.
26.	Click Yes.
27.	Close the message.
28.	Close the form.

GST minor codes

1.	Click General ledger > Setup > Sales tax > India > GST minor codes.
2.	Create a record.
3.	In the Tax component field, select a value.
4.	In the Minor code field, enter a value.
5.	In the Description field, enter a value.
6.	Click Close.
Purchase transactions
Purchases from an unregistered vendor
Purchase requisition
1.	Click Procurement and sourcing > Common > Purchase requisitions > All purchase requisitions.
2.	Create a purchase requisition for a taxable item.
3.	Save the record. The Tax information button becomes available.
4.	Click Tax information.
5.	On the GST tab, validate the default values for the following fields.
    -	GSTIN/GDI/UID
    -	HSN code
    -	ITC category: Input
    -	Service category: Inward

6.	Click the Vendor tax information tab.

  > [!NOTE]
  >  -	The company address and the vendor address are in different states. Therefore, this transaction is an interstate transaction.
  >  -	The Tax information field is blank for the vendor. Therefore, the dealer is an unregistered dealer.
7.	Click OK.
8.	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document to review the calculated taxes.
Example:
●	Taxable value: 10,000.00
●	IGST: 20 percent

9	Click Close.
10	Click Submit.
11	Update the comment, and then click Submit to process the purchase requisition through a workflow.
Approve the purchase requisition
12	Click Procurement and sourcing > Common > Purchase requisitions > Purchase requisitions prepared by me.
13	Select the purchase requisition.
14	Click Actions > Approve.
15	Update the comment, and then click Approve.
Release the approved purchase requisition
16	Click Procurement and sourcing > Common > Purchase requisitions > Release approved purchase requisition.
17	Select the purchase requisition.
18	Click New Purchase order.
19	Close the message.
Purchase order form
20	Click Accounts payable > Common > Purchase orders > All purchase orders.
21	Select the purchase order.
22	On the Action Pane, on the Purchase order tab, in the Maintain group, click Edit.
23 Click Tax information.
24	Click the GST tab.
25	Click the Vendor tax information tab.
26	Click OK.
Validate the tax details
27	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document to review the calculated taxes.
Example:
●	Taxable value: 10,000.00
●	IGST: 20 percent

If you change any tax attributes after the order line is created, click Recalculate to recalculate tax.
28	Click Close.
29	Click Confirm.
Post the purchase invoice
30	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
31	In the Default quantity for lines field, select Ordered quantity.
32	Enter the invoice number.
33	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
34	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
●	Financial entry for the purchase of goods
 
Note: After the authority payment, the credit should be claimed.
●	Financial entry for the purchase of services
 
Tax liability arises on invoice payment.
Financial entry on invoice payment
 
Note: An appropriate Service accounting code must be selected.
●	Financial entry for the purchase of goods where the ITC category is set to Others
 
●	Financial entry for the purchase of services where the service category is set to Others
 
Tax liability arises on invoice payment.
Financial entry on invoice payment
 
-	Financial entry for purchases where the load on inventory is set to 100 percent
-	Financial entry for purchases where the non-business usage is set to 40 percent
 
Note: Based on the business requirements, the non-business usage value can be used to load on inventory. Configure the account in the tax configuration file.
Purchases from a registered vendor
Purchase of goods and services
Request for quotation
1	Click Procurement and sourcing > Common > Requests for quotations > All requests for quotations.
2	Create a request for quotation (RFQ) for a taxable item.
3	On the Action Pane, on the Quotation tab, in the Process group, click Send and publish to Vendor portal.
4	Click OK.
5	Close the message.
6	Close the Request for quotation details form.
Request for quotation replies
7	Click Procurement and sourcing > Common > Requests for quotations > Request for quotation replies.
8	Select the record.
9	On the Action Pane, on the Reply tab, in the Maintain group, click Edit.
10	On the Action Pane, on the Reply tab, in the Process group, click Copy data to reply.
11	On the Purchase quotation lines FastTab, click Tax information.
12	Click the GST tab.
13	Click the Vendor tax information tab.
14	Click OK.
Validate the tax details
15	On the Action Pane, on the Reply tab, in the Financials group, click Tax document.
16	Select the GST node.
17	On the Purchase request for quotation reply and Tax details FastTabs, review the tax applicability, tax attributes, and tax calculation.
Example:
●	Taxable value: 10,000.00
●	CGST: 10 percent
●	SGST: 10 percent

18	Click Close.
19	On the Action Pane, on the Reply tab, in the Process group, click Accept.
20	Click OK.
21	Close the message.
22	Close the Request for quotation reply form.
Purchase order form
23	Click Accounts payable > Common > Purchase orders > All purchase orders.
24	Select the purchase order that was created through the RFQ.
25	On the Action Pane, on the Purchase order tab, in the Maintain group, click Edit.
26	On the Purchase order lines FastTab, click Tax information.
27	Click the GST tab.
28	Click the Vendor tax information tab.
29	Click OK.
Validate the tax details
30	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
31	On the Purchase order and Tax details FastTabs, review the tax applicability, tax attributes, and tax calculation.
Example:
●	Taxable value: 10,000.00
●	CGST: 10 percent
●	SGST: 10 percent

32	Click Close.
33	Click Confirm.
Post the purchase invoice
34	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
35	In the Default quantity for lines field, select Ordered quantity.
36	Enter the invoice number.
37	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
38	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview, tab, click Voucher.
  -	Financial entry for the purchase of goods
  -	Financial entry for the purchase of services
  -	Financial entry for the purchase of goods where the ITC category is set to Others
  -	Financial entry for the purchase of services where the service category is set to Others
  -	Financial entry for the purchase of goods where the load on inventory is set to 100 percent
  -	Financial entry for the purchase of goods where the reverse charge is set to 100 percent
  -	Financial entry for the purchase of goods where the reverse charge is set to 70 percent and the ITC category is set to Others
  -	Financial entry for purchases where the non-business usage is set to 40 percent
 
Purchase of goods where there is a discount
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order for a taxable item.
3	In the Discount percent field, enter a value.
4	Save the record.
Validate the tax details
5	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
6	Verify that the tax that is calculated considers the discount.
7	Click Close.
8	Click Confirm.
Post the purchase invoice
9	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
10	In the Default quantity for lines field, select Ordered quantity.
11	Enter the invoice number.
12	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
13	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Purchase of exempted goods
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order for an exempted item.
3	Save the record.
4	Click Tax information.
5	On the GST tab, verify that the Exempted check box is selected by default.
6	Click OK.
Validate the tax details
7	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
8	Verify that the Exempt field is set to Yes and the Tax computed field is set to 0.00.
9	Click Close.
10	Click Confirm.
Post the purchase invoice
11	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
12	In the Default quantity for lines field, select Ordered quantity.
13	Enter the invoice number.
14	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
15	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Purchase of zero-rated goods
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order for a zero-rated item.
3	Save the record.
4	Click Tax information.
5	Click the GST tab.
6	Click OK.
Validate the tax details
7	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
8	Verify that the Tax computed field is set to 0.00.
9	Click Close.
10	Click Confirm.
Post the purchase invoice
11	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
12	In the Default quantity for lines field, select Ordered quantity.
13	Enter the invoice number.
14	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
15	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Purchase of non-GST goods
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order, and define value-added tax (VAT) tax groups.
3	Save the record.
4	Click Tax information.
5	In the Tax Information field, select the Tax Identification Number (TIN).
6	On the VAT tab, in the Non recoverable pct. field, enter 100.00.
7	Click OK.
8	On the Line details FastTab, on the Setup tab, select values in the Item sales tax group and Sales tax groups fields.
Validate the tax details
9	On the Action Pane, on the Purchase tab, in the Tax group, click Sales tax.
Note: The Tax document button isn’t available.
10	Verify that VAT is calculated.
11	Click Close.
12	Click Confirm.
Post the purchase invoice
13	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
14	In the Default quantity for lines field, select Ordered quantity.
15	Enter the invoice number.
16	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
17	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Purchase from a composite dealer
1	Click Accounts payable > Journals > Invoice > Invoice journals.
2	Create a journal.
3	Click Lines.
4	Create a purchase transaction for a composite vendor.
5	Save the record.
6	Click Tax information.
7	On the GST tab, in the HSN code field, select a value.
8	Click the Vendor tax information tab.
9	Click OK.
Validate the tax details
10	Click Tax document.
11	Click Close.
12	Click Post > Post to post the journal.
13	Close the message.
Validate a voucher
14	Click Inquiries > Voucher.
 
Purchase of taxable goods where there are shipping charges
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order for a taxable item.
3	On Purchase order lines FastTab, click Financials > Maintain charges.
4	Select the charges code.
5	In the Charges value field, enter a value.
6	Select the Assessable value check box.
7	Save the record.
8	Click Close.

Note: Freight charges are added to the assessable value.
Validate the tax details
9	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
10	On the Tax details FastTab, review the tax calculation.
Example:
●	Line amount: 10,000.00
●	CGST: 10 percent
●	SGST: 10 percent
●	CESS: 1 percent

11	Click Close.
12	Click Confirm.
Post the purchase invoice
13	On the Action Pane, on the Invoice tab, in the> Generate group, click Invoice.
14	In the Default quantity for lines field, select Ordered quantity.
15	Enter the invoice number.
16	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
17	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Revised purchase invoice that has taxable goods
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order for a taxable item.
Validate the tax details
3	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
4	On the Tax details FastTab, review the tax calculation.
Example:
●	Line amount: 10,000.00
●	CGST: 10 percent
●	SGST: 10 percent
●	CESS: 1 percent

5	Click Close.
6	Click Confirm.
Post the purchase invoice
7	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
8	In the Default quantity for lines field, select Ordered quantity.
9	On the Lines FastTab, enter the invoice number.
10	In the Invoice type field, select Revised.
11	In the Original invoice number field, select a value.
12	Verify that the Original invoice date field is automatically set, based on the original invoice number that you selected.
13	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
14	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Purchase of a fixed asset
1	Click General ledger > Journals > General journal.
2	Create a journal, and define a journal name.
3	Click Lines.
4	In the Account type field, select Fixed assets.
5	In the Account field, select a value.
6	In the Debit field, enter a value.
7	In the Offset account type field, select Vendor.
8	In the Offset account field, select a value.
9	Save the record.
10	Click Tax information.
11	On the GST tab, in the HSN code field, select a value.
12	Click the Vendor tax information tab.
13	Click OK.
Validate the tax details
14	Click Tax document.
15	Click Close.
16	Click Post > Post.
17	Close the message.
Validate the financial entries
18	Click Inquiries > Voucher.
 
Credit note against the purchase invoice
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order.
3	On the Action Pane, on the Purchase tab, click Create credit note.
4	Select the invoice to issue a credit note against.
5	Click OK.
6	Verify that the Original invoice number and Original invoice date fields are automatically set on the order line.
7	Click Tax information.
8	Click the GST tab.
9	Click the Vendor tax information tab.
10	Click OK.
Validate the tax details
11	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
12	Click Close.
13	Click Confirm.
Post the purchase invoice
14	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
15	In the Default quantity for lines field, select Ordered quantity.
16	Enter the invoice number.
17	On the Lines FastTab, verify that the Invoice type field is set to Original.

Note: You can post a revised credit note by selecting Revised in the Invoice type field and adding a reference to the original credit note.
18	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
19	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Note: The general journal also lets you create a purchase credit note that has details of the original invoice.
Debit note against the purchase invoice
1	Click General ledger > Journals > General journal.
2	Create a journal, and define a journal name.
3	Click Lines.
4	In the Account type field, select Vendor.
5	In the Account field, select a value.
6	In the Credit field, enter a value.
7	In the Offset account type field, select Ledger.
8	In the Offset account field, select a value.
9	On the General tab, in the Original purchase invoice field group, in the Original invoice number field, select a value.
10	Verify that the Original invoice date field is automatically set, based on the original invoice.

Note: You can post a revised debit note by selecting Revised in the Invoice type field and adding a reference to the original debit note.
11	Click Tax information.
12	On the GST tab, in the HSN code field, select a value.
13	Click the Vendor tax information tab.
14	Click OK.
Validate the tax details
15	Click Tax document.
16	Click Close.
17	Click Post > Post.
18	Close the message.
Validate the financial entries
19	Click Inquiries > Voucher.
 
Note: The purchase order also lets you create a debit note that has details of the original invoice.
Quality order that involves destruction of the sampling item
Purchase order form
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order.
Validate the tax details
3	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
Example:
●	Taxable value: 10,000.00
●	CGST: 10 percent
●	SGST: 10 percent

4	Click Close.
5	Click Confirm.
Post the packing slip
6	On the Action Pane, on the Receive tab, in the Generate group, click Product receipt.
7	In the Quantity field, select Ordered quantity.
8	In the Product receipt field, enter a value.
9	Click OK.
10	Click Show.

Quality order form
11	Click Results.
12	Update the Result quantity field.
13	Click Validate.
14	Click Close.
15	Click Tax document.

Note: Tax is calculated for the quantity that was used for the quality check and destroyed.
16	Click Close.
17	Click Validate.
18	In the Validate by field, select a value.
19	Click OK.
20	Close the Quality orders form.
Post the purchase invoice
21	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
22	Enter the invoice number.
23	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
24	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Purchase return order
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order where the Purchase type field is set to Returned order.
3	In the RMA number, enter a value.
4	Click OK.
5	Create purchase order lines that have a negative quantity.
6	Save the record.
7	Click Tax information.
8	Click the GST tab.
9	Click the Vendor tax information tab.
10	Click OK.
Validate the tax details
11	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
12	Click Close.
13	Click Confirm.
Post the purchase invoice
14	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
15	In the Default quantity for lines field, select Ordered quantity.
16	Enter the invoice number.
17	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
18	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Vendor advance payment where there are reverse charges
1	Click Accounts payable > Journals > Payments > Payment journal.
2	Create a record.
3	In the Name field, select a value.
4	Click Lines.
5	Create a vendor advance payment journal.
6	Save the record.
7	Click Tax information.
8	On the GST tab, in the HSN code field, select a value.
9	Click the Vendor tax information tab.
10	Click OK.
Validate the tax details
11	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
Example:
●	CGST: 10 percent
●	SGST: 10 percent
●	CESS: 1 percent
●	Reverse charge percentage: 70 percent for all the three components

12	Click Close.
13	Click Post > Post.
14	Close the message.
Update the transaction ID
15	Click Functions > GST transaction Id.
16	In the Date field, enter a value.
17	In the Text field, enter a value.
18	Click Close.
Validate the financial entries
19	Click Inquiries > Voucher.
 
Sales transactions
Sale of taxable goods to a consumer
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for a taxable item.
3	Save the record.
4	Click Tax information.
5	Click the GST tab.
6	Click the Customer tax information tab.

Note: The Tax information field is blank. Therefore, the dealer is an unregistered dealer.
7	Click OK.
8	On the Action Pane, on the Sell tab, in the Tax group, click Tax document to review the calculated taxes.
Example:
●	Taxable value: 10,000.00
●	IGST: 20 percent

9	Click Close.
Post the invoice
10	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
11	In the Quantity field, select Packing slip.
12	Select the Print invoice check box.
13	Click OK.
14	Click Yes to acknowledge the warning message.
Validate the report
 
Note: The invoice serial number is selected per the Tax invoice number sequence that is defined for the registration number.
Validate the voucher
15	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
16	Click Voucher.
Financial entries for both the intrastate and interstate transactions
 
Sales to a registered customer
Sale of taxable goods
Sales quotation
1	Click Sales and marketing > Common > Sales quotation > All quotations.
2	Create a quotation for a taxable item for the registered customer.
3	Save the record.
4	Click Tax information.
5	On the GST tab, validate the default values.
6	Click the Customer tax information tab.

Notes:
●	The company address and the customer address are in the same state. Therefore, this transaction is an intrastate transaction.
●	Customer tax information is defined. Therefore, the dealer is a registered dealer.
7	On the Action Pane, on the Quotation tab, in the Financials group, click Tax document.
8	Select the GST node.
9	On the Sales quotation and Tax details FastTabs, review the tax applicability, tax attributes, and tax calculation.
Example:
●	Taxable value: 10,000.00
●	CGST: 10 percent
●	SGST: 10 percent
 
10	Click Close.
11	On the Action Pane, on the Quotation tab, in the Generate group, click Send quotation.
12	Click OK.
13	Close the message.
14	On the Action Pane, on the Follow up tab, in the Generate group, click Confirm.
15	Click OK.
16	Close the message.
17	Close the forms.
Sales order form
18	Click Accounts receivable > Common > Sales orders > All sales orders.
19	Select a record.
20	On the Action Pane, on the Sales order tab, in the Maintain group, click Edit.
21	Click Tax information.
22	Click the GST tab.
23	Click the Customer tax information tab.
24	Click OK.
25	On the Action Pane, on the Sell tab, in the Tax group, click Tax document to review the calculated taxes.
26	Click Close.
Post the invoice
27	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
28	In the Quantity field, select All.
29	Select the Print invoice check box.
30	Click OK.
31	Click Yes to acknowledge the warning message.
Validate the report
 
Validate the voucher
32	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
33	Click Voucher.
Financial entries for both the intrastate and interstate transactions
 
Sale of taxable services
Free text invoices
1	Click Accounts receivable > Common > Free text invoices > All free text invoices.
2	Create a free text invoice for taxable services.
3	Save the record.
4	Click Tax information.
5	On the GST tab, in the SAC field, select a value.
6	Click the Customer tax information tab.

> [!NOTE]
> The company address and the customer address are in different states. Therefore, this transaction is an interstate transaction.
7	Click OK.
8	On the Action Pane, on the Invoice tab, in the Details group, click Tax document.
Example:
●	Taxable value: 10,000.00
●	IGST: 20 percent

9	Click Close.
Post the invoice
10	On the Action Pane, on the Invoice tab, click Post > Post.
11	Click OK.
12	Close the message.
Validate the voucher
13	On the Action Pane, on the Invoice tab, in the Related information group, click Invoice journal.
14	Click Voucher.
Financial entries for both the intrastate and interstate transactions
 
Sale of taxable goods where there is a reverse charge
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for a taxable item.
3	Save the record.
4	Click Tax information.
5	Click the GST tab.
6	Click the Customer tax information tab.
7	Click OK.
8	On the Action Pane, on the Sell tab, in the Tax group, click Tax document to review the calculated taxes.
Example:
●	Taxable value: 10,000.00
●	CGST: 10 percent
●	SGST: 10 percent
●	Reverse charge percentage: 70 percent

9	Click Close.
Post the invoice
10	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
11	In the Quantity field, select All.
12	Select the Print invoice check box.
13	Click OK.
14	Click Yes to acknowledge the warning message.
Validate the report
 
Validate the voucher
15	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
16	Click Voucher.
Financial entries for both the intrastate and interstate transactions
 
Sales of exempted item
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for an exempted item.
3	Select the record.
4	Click Tax information.
5	On the GST tab, verify that the Exempted check box is selected by default.
6	Click the Customer tax information tab.
7	Click OK.
8	On the Action Pane, on the Sell tab, in the Tax group, click Tax document.

9	Click Close.
Post the invoice
10	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
11	In the Quantity field, select All.
12	Click OK.
13	Click Yes to acknowledge the warning message.
Validate the voucher
14	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
15	Click Voucher.
 
Sale of zero-rated goods
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for a zero-rated item.
3	Select the record.
4	Click Tax information.
5	Click the GST tab.
6	Click the Customer tax information tab.
7	Click OK.
8	On the Action Pane, on the Sell tab, in the Tax group, click Tax document.

9	Click Close.
Post the invoice
10	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
11	In the Quantity field, select All.
12	Click OK.
13	Click Yes to acknowledge the warning message.
Validate the voucher
14	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
15	Click Voucher.
 
Sale of non-GST goods
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order, and define VAT tax groups.
3	Select the record.
4	Click Tax information.
5	In the Tax information field, select a value that has a Tax Identification Number (TIN) associated with it.
6	Click the GST tab.
7	Click the Customer tax information tab.
8	Click OK.
9	On the Action Pane, on the Sell tab, in the Tax group, click Sales tax.
10	Click Close.
Post the invoice
11	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
12	In the Quantity field, select All.
13	Click OK.
14	Click Yes to acknowledge the warning message.

Validate the voucher
15	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
16	Click Voucher.
 
Sale of taxable goods where there is a discount and a provisional assessment
Sales order form
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for a taxable item.
3	On the Action Pane, on the Sales order tab, in the Show group, click Header view.
4	On the Price and discount FastTab, in the Total discount % field, enter 10.00.
5	On the Action Pane, on the Sales order tab, in the Show group, click Line view.
6	On the Lines details FastTab, on the Address tab, in the Delivery address field, select a value.
7	Save the record.
8	Click Tax information.
9	Click the GST tab.
10	Click the Customer tax information tab.
11	Click OK.
12	On the Action Pane, on the Sell tab, in the Tax group, click Tax document.
13	Verify that the tax that is calculated considers the discount.
14	Click Close.
Post the invoice
15	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
16	In the Quantity field, select All.
17	Select the Print invoice check box.
18	Select the Provisional assessment check box.
19	Click OK.
20	Click Yes to acknowledge the warning message.
Validate the report
 
Validate the voucher
21	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
22	Click Voucher.
 
Sale of taxable goods where there is tax on shipping charges
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for a taxable item.
3	On the Lines details FastTab, on the Address tab, in the Delivery address field, select a value.
4	Save the records.
5	Click Tax information.
6	Click the GST tab.
7	Click the Customer tax information tab.
8	In the Location field, select the value that you selected for the delivery address in step 3.
9	Click OK.
10	On the Sales order lines FastTab, click Financials > Maintain charges.
11	Select a charges code.
12	In the Charges value field, enter a value.
13	Save the record.
14	Click Tax information.
15	Click the GST tab.

Note: The SAC field is automatically set, based on the charges code that you selected. The default setting is defined in the charges code master.
16	Click the Customer tax information tab.
17	Click OK.
18	On the Action Pane, on the Sell tab, in the Tax group, click Tax document to review the calculated taxes.
Example:
●	Line amount: 10,000.00
●	IGST: 20 percent
●	CESS: 1 percent
●	Miscellaneous charges: 1,000.00
●	IGST: 25 percent
●	CESS: 1 percent
 
19	Click Close.
Post the invoice
20	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
21	In the Quantity field, select All.
22	Select the Print invoice check box.
23	Click OK.
24	Click Yes to acknowledge the warning message.
Validate the report
 
Validate the voucher
25	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
26	Click Voucher.
 
Sales where prices include and exclude tax
Sales order form
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for taxable goods.
3	Add two sales order lines:
●	For order line 1, clear the Prices include sales tax check box.
●	For order line 2, select the Prices include sales tax check box.

4	Save the records.
5	Select order line 1.
6	Click Tax information.
7	Click the GST tab.
8	Click the Customer tax information tab.
9	Click OK.
10	Repeat steps 5 through 9 for order line 2.
11	On the Action Pane, on the Sell tab, in the Tax group, click Tax document.
Example:
●	Order line 1:
●	Taxable amount: 10,000
●	CGST: 10 percent
●	SGST: 10 percent
●	CESS: 1 percent
●	Order line 2:
●	Taxable amount: 5,000
●	CGST: 10 percent
●	SGST: 10 percent
●	CESS: 1 percent
●	Price inclusive

12	Click Close.
Post the invoice
13	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
14	In the Quantity field, select All.
15	Click OK.
16	Click Yes to acknowledge the warning message.

Validate the voucher
17	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
18	Click Voucher.
 
Debit note against the sales invoice
1	Click General ledger > Journals > General journal.
2	Create a journal, and define a journal name.
3	Click Lines.
4	In the Account type field, select Customer.
5	In the Account field, select a value.
6	In the Debit field, enter a value.
7	In the Offset account type field, select Ledger.
8	In the Offset account field, select a value.
9	On the General tab, in the Original sales invoice field group, in the Original invoice number field, select a value.
10	Verify that the Original invoice date is automatically set, based on the original invoice number that you selected.

Note: You can post a revised debit note by selecting Revised in the Invoice type field and adding a reference to the original debit note.
11	Click Tax information.
12	On the GST tab, in the HSN code field, select a value.
13	Click the Customer tax information tab.
14	Click OK.
Validate the tax details
15	Click Tax document.
16	Click Close.
17	Click Post > Post.
18	Close the message.
Validate the financial entries
19	Click Inquiries > Voucher.
 
Note: You can also create a sales debit note through a sales order and a free text invoice.
Credit note against the sales invoice
Sales order form
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales credit note for a taxable item.
3	In the Original invoice number field, select a value.
4	Verify that the Original invoice date field is automatically set, based on the original invoice number that you selected.
5	Save the record.
6	Click Tax information.
7	Click the GST tab.
8	Click the Customer tax information tab.
9	Click OK.
10	On the Action Pane, on the Sell tab, in the Tax group, click Tax document.
Example:
●	Taxable amount: -5,000
●	IGST: 20 percent
●	CESS: 1 percent

11	Click Close.
Post the invoice
12	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
13	In the Quantity field, select All.
14	On the Others tab, verify that the Invoice type field is set to Original.
Note: You can post a revised credit note by selecting Revised in the Invoice type field and adding a reference to the original credit note.
15	Click OK.
16	Click Yes to acknowledge the warning message.
Validate the voucher
17	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
18	Click Voucher.
 
> [!NOTE]
> You can also create a sales credit note through the general ledger and a free text invoice.
Sales invoice that is split based on delivery addresses
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create a sales order for taxable items.
3	On the Lines details FastTab, click the Address tab.
Order line	Taxable value	Delivery location
1	10,000	Ashoka Pillar road
Bangalore Karnataka
560030
IND
2	5,000	Barakhamba Road
Delhi
110007
IND

4	Save the records.
5	Select order line 1.
6	Click Tax information.
7	Click the GST tab.
8	Click the Customer tax information tab.
9	Click OK.
10	Select order line 2.
11	Click Tax information.
12	Click the GST tab.
13	Click the Customer tax information tab.
14	Click OK.
15	On the Action Pane, on the Sell tab, in the Tax group, click Tax document to review the calculated taxes.
Example:
-	Order line 1
-	Taxable amount: 10,000.00
-	CGST: 10 percent
-	SGST: 10 percent
-	CESS: 1 percent
-	Order line 2
-	Taxable amount: 5,000.00
-	IGST: 20 percent
-	CESS: 1 percent

16	Click Close.
Post the packing slip
17	Click the Action Pane, on the Pick and pack tab , in the Generate group, click Packing slip.
18	Click OK.
Post the invoice
19	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
20	In the Quantity field, select All.

Note: The invoice is split based on the delivery addresses.
21	Click OK.
22	Click Yes to acknowledge the warning message.
Validate the voucher
23	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
24	Select record with Invoice amount ‘12100.00’
25	Click Voucher.
26	Click Close.
27	Select record with Invoice amount ‘6050.00’
28	Click Voucher.
 




Sales return transaction
Return order form
1	Click Sales and marketing > Common > Return orders > All return orders.
2	Create a return order for a taxable item.
3	On the Line details FastTab, in the Disposition code field, select Credit only.
4	On the Action Pane, on the Return order tab, in the Send group, click Return order.
5	Click OK.
6	Close the form.
Sales order form
7	Click Accounts receivable > Common > Sales orders > All sales orders.
8	Select the record where the Order type field is set to Returned order.
9	On the Action Pane, on the Sales order tab, in the Maintain group, click Edit.
10	Click Tax information.
11	Click the GST tab.
12	Click the Customer tax information tab.
  > [!NOTE]
  > The Tax information value is automatically set, based on the original sales order that the return order is created against.
13	Click OK.
14	On the Action Pane, on the Sell tab, in the Tax group, click Tax document.
Example:
●	Taxable amount: 10,000
●	CGST: 10 percent
●	SGST: 10 percent
●	CESS: 1 percent

15	Click Close.
Post the invoice
16	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
17	In the Quantity field, select All.
18	Click OK.
19	Click Yes to acknowledge the warning message.
Validate the report
Validate the voucher
20	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
21	Click Voucher.
●	Financial entry for the Credit only/Replace and scrap/Scrap disposition code
●	Financial entry for the Credit/Replace and credit disposition code
 
Foreign transactions
Import of goods where there is GST
1	Click Accounts payable > Common > Purchase orders > All purchase orders.
2	Create a purchase order for a foreign vendor account.
3	Save the record.
4	Click Tax information.
5	Click the GST tab.
6	Click the Customs tab.
7	Click the Vendor tax information tab.
8	Click OK.
9	Click Functions > Maintain charges.
10	Select a charges code.
11	Select the Assessable value check box.
12	In the Charges value field, enter a value.
13	Save the record.
14	Click Close.

Note: The assessable value is calculated as Net amount + Misc. charges + 1% of Landing charges that are defined in Accounts payable parameters.
Validate the tax details
15	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
16	On the Tax details FastTab, review the tax calculation.
Example:
●	BCD: 10 percent
●	LOI: 100 percent
●	IGST: 20 percent
●	Import exchange rate: 1 USD = 52 INR

Note: IGST can be calculated on Assessable value + BCD tax amount, by extending the configuration. 
17	Click Close.
18	Click Confirm.
Update the invoice registration
19	On the Action Pane, on the Customs tab, in the Maintain group, click Invoice registration.
20	In the Import invoice number field, select a value.
21	Click Update.
Post the bill of entry
22	On the Action Pane, on the Customs tab, in the Generate group, click Bill of entry.
23	In the Import invoice number field, select a value.
24	In the Bill of entry number field, select a value.
25	Click Tax document.

26	Click Close.
27	Click OK.
Verify the Bill of entry journal
28	On the Action Pane, on the Customs tab, in the Journal group, click Bill of entry.
29	Click Tax document.
30	Click Close.
Correction of Bill of entry
31	Click Cancel.
32	Click Close.

Post the bill of entry
33	On the Action Pane, on the Customs tab, in the Generate group, click Bill of entry.
34	In the Import invoice number field, select a value.
35	In the Bill of entry number field, select a value.
36	Click the Lines tab.
37	In the Quantity field, enter a value.
38	Close the message.
39	Click Tax document.
40	Click Close.
41	Click OK.
Verify the Bill of entry journal
42	On the Action Pane, on the Customs tab, in the Journal group, click Bill of entry.
43	Click Tax document.
44	Click Close.

Post the product receipt
45	On the Action Pane, on the Receive tab, in the Generate group, click Product receipt.
46	In the Quantity field, select Bill of entry quantity.
47	Enter the Product receipt.
48	Click OK.


Post the purchase invoice
49	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
50	In the Default quantity for lines field, select Bill of entry quantity.
51	Enter the invoice number.
52	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
53	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
  
Import of services where there is GST
1	Click Accounts payable > Journals > Invoices > Invoice journal.
2	Create a journal.
3	Click Lines.
4	Create a purchase of services for a foreign vendor.
5	Save the record.
6	Click Tax information.
7	On the GST tab, in the SAC field, select a value.
8	Click the Vendor tax information tab.
9	Click OK.
Validate the tax details
10	Click Tax document.
Example:
●	Taxable value: 20,000.00
●	IGST: 20 percent
●	Normal exchange rate: 1 USD = 60 INR

11	Click Close.
12	Click Post > Post.
13	Close the message.
14	Click Inquiries > Voucher.
 
Export of goods that has zero-rated tax
Sales order form
1	Click Accounts receivable > Common > Sales orders > All sales orders.
2	Create an export order for a taxable item.
3	Save the record.
4	Click Tax information.
5	Click the GST tab.
6	Click the Customer tax information tab.
7	Click OK.
8	On the Action Pane, on the Sell tab, in the Tax group, click Tax document.
9	Click Close.
Post the invoice
10	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
11	In the Quantity field, select All.
12	Click OK.
13	Click Yes to acknowledge the warning message.
Validate the voucher
14	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice.
15	Click Voucher.
Post the export order
16	Click Accounts receivable > Common > Customs export order.
17	Create an export order for the posted sales order.
18	Click Shipping bill.
19	In the Shipping bill Number field, enter a value.
20	Click OK.
Validate the voucher
21	Click Inquiries > Shipping bill.
22	Click Voucher.

Export of services that has zero-rated tax
1	Click General journal > Journals > Invoices > General journal.
2	Create a journal.
3	Click Lines.
4	Create a sale of services for a foreign customer.
5	Save the record.
6	Click Tax information.
7	On the GST tab, in the SAC field, select a value.
8	Click the Customer tax information tab.
9	Click OK.
Validate the tax details
10	Click Tax document.
Example:
●	Taxable value: 10,000.00
●	IGST: 0.00 percent

11	Click Close.
12	Click Post > Post.
13	Close the message.
14	Click Inquiries > Voucher.
 

Stock transfer transaction
Stock transfer order where there is tax on the transfer price
1	Click Inventory management > Periodic > Transfer order.
2	Create a transfer order where the Transfer type field is set to Stock transfer.
  > [!NOTE]
  > For the selected item, the item cost is 10,000.00, and the transfer price is 15,000.00.
3	At the line level, click Tax information from warehouse.
4	Click the GST tab.
5	Click OK.
6	At the line level, click Tax information to warehouse.
7	Click the GST tab.
8	Click OK.
9	Click Inquiries > Tax document to verify that the tax is calculated.
For example:
●	Taxable value: 15,000.00
●	IGST: 20 percent

10	Click Close.
Post the shipment
11	Click Posting > Ship transfer order.
12	Select the Edit lines check box.
13	In the Update field, select All.
14	Click Setup > Tax document.
15	Click Close.
16	Click OK.
Validate the voucher
17	Click Inquiries > Transfer order history.
18	Select the record where the Update type field is set to Shipment.
19	Click Ledger > Voucher.
 
  > [!NOTE]
  > Tax accounts for the “from” warehouse GSTIN are posted.
Post the receipt
20	Click Posting > Receive.
21	Select the Edit lines check box.
22	In the Update field, select All.
23	Click Setup > Tax document.
24	Click Close.
25	Click OK.
Validate the voucher
26	Click Inquiries > Transfer order history.
27	Select the record where the Update type field is set to Receive.
28	Click Ledger > Voucher.
 
Note: Tax accounts for the “to” warehouse GSTIN are posted.
Customer payment transactions
Advance payment that has tax
1	Click Accounts receivable > Journals > Payments > Payment journal.
2	Create a record.
3	In the Name field, select a value.
4	On the Setup tab, select the Amounts include sales tax check box.
5	Click Lines.
6	Create a customer advance payment journal.
7	Save the record.
8	Click Tax information.
9	On the GST tab, in the HSN code field, select a value.
10	Click the Customer tax information tab.
11	Click OK.
Validate the tax details
12	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
Example: IGST: 20 percent

13	Click Close.
14	Click Post > Post.
15	Close the message.
Update the transaction ID
16	Click Functions > GST transaction Id.
17	In the Date field, enter a value.
18	In the Text field, enter a value.
19	Click Close.
Validate the financial entries
20	Click Inquiries > Voucher.
 
Advance payment that is settled during invoice posting
This section provides information about tax posted on the customer advance payment and selected for the settlement, while posting the customer invoice.
The following tables shows the tax entries that are generated for the invoice when an advance payment is settled in various scenarios.
Transaction details	Example	Tax entries that are generated during settlement
Invoice = Payment	Invoice amount: 12,000.00
Payment amount: 12,000.00	Tax on the invoice is posted.
Tax on the payment is reversed to prevent a double entry in the related voucher.
IGST payable account				Cr.		2,000.00
Related voucher
IGST interim payable account		Cr.		2,000.00
IGST payable account				Dr.		2,000.00
Invoice < Payment	Invoice amount: 6,000.00
Payment amount: 12,000.00	Tax on the invoice is posted.
Tax on the payment is reversed to the extent of the invoice amount in the related voucher.
IGST payable account				Cr.		1,000.00
Related voucher
IGST interim payable account		Cr.		1,000.00
IGST payable account				Dr.		1,000.00
Invoice > Payment	Invoice amount: 24,000.00
Payment amount: 12,000.00	Tax on the invoice is posted.
Tax on the payment is reversed to the extent of the payment amount in the related voucher
IGST payable account				Cr.		4,000.00
Related voucher
IGST interim payable account		Cr.		2,000.00
IGST payable account				Dr.		2,000.00
Manual settlement of an advance payment that has tax and an invoice that has tax
Tax is posted on both the advance payment and the sales invoice. On settling these transactions through the Open transaction editing form, the double tax entry gets reversed.
The following table shows the tax entries that are generated in various scenarios when an invoice that has tax and a payment that has tax are settled.
Transaction details	Example	Tax entries that are generated during settlement
Invoice = Payment	Invoice amount: 12,000.00
Payment amount: 12,000.00	Tax on the payment is reversed.
IGST interim payable account		Cr.		2,000.00
IGST payable account				Dr.		2,000.00
Invoice < Payment	Invoice amount: 6,000.00
Payment amount: 12,000.00	Tax on the payment is reversed to the extent of the invoice amount.
IGST interim payable account		Cr.		1,000.00
IGST payable account				Dr.		1,000.00
Invoice > Payment	Invoice amount: 24,000.00
Payment amount: 12,000.00	Tax on the payment is reversed.
IGST interim payable account		Cr.		2,000.00
IGST payable account				Dr.		2,000.00
Payment of an invoice that has tax
1	Click Accounts receivable > Journals > Payments > Payment journal.
2	Create a record.
3	In the Name field, select a value.
4	On the Setup tab, select the Amounts include sales tax check box.
5	Click Lines.
6	Create a customer advance payment journal.
7	Click Functions > Settlement.
8	In the Invoice field, select a value.
9	Close the form.
10	Save the record.
11	Click Post > Post.
12	Close the message.
Validate the financial entries
13	Click Inquiries > Voucher.

The following table shows the tax entries that are generated when an invoice payment is made in various scenarios.
Transaction details	Example	Tax entries that are generated during invoice payment
Invoice = Payment	Invoice amount: 12,000.00
Payment amount: 12,000.00 without tax	No tax entries are generated.
Invoice < Payment	Invoice amount: 6,000.00
Payment amount: 12,000.00 with tax
Note: If either an HSN code or an SAC is defined for the journal, tax is calculated and posted on the journal amount.	Tax is calculated and posted on the payment amount.
Tax on the payment is reversed to the extent of the invoice amount in the related voucher.
IGST interim payable account		Dr.		2,000.00
IGST payable account				Cr.		2,000.00
Related voucher
IGST interim payable account		Cr.		1,000.00
IGST payable account				Dr.		1,000.00
Invoice > Payment	Invoice amount: 24,000.00
Payment amount: 12,000.00 without tax	No tax entries are generated.
Revised advance payment that has tax
1	Click Accounts receivable > Journals > Payments > Payment journal.
2	Create a record.
3	In the Name field, select a value.
4	On the Setup tab, select the Amounts include sales tax check box.
5	Click Lines.
6	Create a customer advance payment journal.
7	Save the record.
8	Click Tax information.
9	On the GST tab, in the HSN code field, select a value.
10	Click the Customer tax information tab.
11	Click OK.
12	On the General tab, in the Invoice type field, select Revised.
13	In the Original transaction id field, select a value.
14	Verify that the Original transaction date field is automatically set, based on the original transaction ID that you selected.

Validate the tax details
15	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document.
Example:
IGST: 20 percent

16	Click Close.
17	Click Post > Post.
18	Close the message.
Update the transaction ID
19	Click Functions > GST transaction Id.
20	In the Date field, enter a value.
21	In the Text field, enter a value.

22	Click Close.
Validate the financial entries
23	Click Inquiries > Voucher.
 
Customer payment refund
1	Click Accounts receivable > Journals > Payments > Payment journal.
2	Create a record.
3	In the Name field, select a value.
4	On the Setup tab, select the Amounts include sales tax check box.
5	Click Lines.
6	Create a customer advance payment journal.
7	Save the record.
8	Click Tax information.
9	On the GST tab, in the HSN code field, select a value.
10	Click the Customer tax information tab.
11	Click OK.
Validate the tax details
12	Click Tax document.
For example: IGST is 20 percent

13	Click Close.
14	Click Post > Post.
15	Close the message.
Validate the financial entries
16	Click Inquiries > Voucher.
 
Direct tax transactions that have GST
Tax Deducted at Source that is calculated includes GST
Withholding tax group form
1	Click General ledger > Setup > Withholding tax > Withholding tax groups.
2	Select a withholding tax group.
3	On the General FastTab, in the Include GST tax components for TDS or TCS calculation field, select the required GST components.
4	Click Close.
Purchase order form
5	Click Accounts payable > Common > Purchase orders > All purchase orders.
6	Create a purchase order.
7	Click OK.
Validate the tax details
8	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document to review the calculated taxes.
For example: Taxable value: 10,000.00 and IGST: 20 percent

9	Click Close.
10	Click Withholding tax.
11	Click Close.
12	Click Confirm.
Post the purchase invoice
13	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
14	In the Default quantity for lines field, select Ordered quantity.
15	Enter the invoice number.
16	On the Action Pane, on the Vendor invoice tab, in the Actions group, click Post > Post.
17	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.

 

Tax Collected at Source that is calculated includes GST
Withholding tax group form
1	Click General ledger > Setup > Withholding tax > Withholding tax groups.
2	Select a withholding tax group.
3	On the General FastTab, in the Include GST tax components for TDS or TCS calculation field, select the required GST components.
4	Click Close.
Sales order form
5	Click Accounts receivable > Common > Sales orders > All sales orders.
6	Create a sales order.
7	Click OK.
Validate the tax details
8	On the Action Pane, on the Purchase tab, in the Tax group, click Tax document to review the calculated taxes.
For example: Taxable value: 10,000.00 and IGST: 20 percent

9	Click Close.
10	Click Product and supply > Withholding tax.
11	Click Close.
Post the purchase invoice
12	On the Action Pane, on the Invoice tab, in the Generate group, click Invoice.
13	Click OK.
14	Click OK.
15	On the Action Pane, on the Invoice tab, in the Journals group, click Invoice. Then, on the Overview tab, click Voucher.
 
Tax adjustments
Tax amount adjustment
1	Click General ledger > Journals > General journal.
2	Create a journal, and define a journal name.
3	Click Lines.
4	In the Account type field, select Customer.
5	In the Account field, select a value.
6	In the Debit field, enter a value.
7	In the Offset account type field, select Ledger.
8	In the Offset account field, select a value.
9	Click Tax information.
10	On the GST tab, in the HSN code field, select a value.
11	Click the Customer tax information tab.
12	Click OK.
Validate the tax details
13	Click Tax document.
14	On the Adjustment tab, in the Tax amount (Adjusted) field, modify the value to override the tax amount that the system calculates.
15	Click Apply adjustment to apply the new tax amount.
16	Click the Tax details tab.

Reset a tax adjustment
●	Click Recalculate to reset the taxes to the amounts that were originally calculated.

Adjust the tax applicability from interstate to intrastate
1	Select the GST node.
2	Click Tax applicability to override the tax applicability that the system determined.
3	Clear the IGST check box, and select the CGST and SGST check boxes.
4	Click OK.
5	Click Apply adjustment to apply your changes.

  > [!NOTE]
  > Click Recalculate to reset the tax applicability to its original value.
6	Click Post > Post.
Validate the financial entries
7	Click Inquiries > Voucher.
 
  > [!NOTE]
  > Tax adjustment functionality is available for purchase orders and sales orders at the invoicing stage.
Tax settlement process
Rule-based tax settlement
1	Click General ledger > Periodic > Sales tax payments > Sales tax payments.
2	Enter values.
3	Click Tax adjustment.

  > [!NOTE]
  > The setoff rule is applied, and excess IGST is used to set off CGST.
4	Click Close.
5	Select the Update check box.
6	Click OK.
Validate the tax settlement voucher entries
7	Click General ledger > Setup > Sales tax > Sales tax settlement periods.
8	Select the settlement period, and then click Sales tax payments.
9	Verify that the settlement for the selected registration for the period is posted successfully.
10	Click Print report.
 
GST authority payment
11	Click Accounts payable > Journals > Payments > Payment journal.
12	Create a journal.
13	Click Lines.
14	Create a journal voucher for Authority account.
15	Click Functions > Settlement.
16	Select the transaction.
17	Click Post > Post.
18	Click Inquiries > Voucher.
Update challan information
19	Click Functions > Challan information.

Manual adjustment of a tax settlement
1	Click General ledger > Periodic > Sales tax payments > Sales tax payments.
2	Enter values.
3	Click Tax adjustment.

  > [!NOTE]
  > The setoff rule is applied, and excess IGST is used to set off the balance of CGST and SGST.
Exclude transactions from the settlement
4	Expand the GST node.
5	Select the CGST node, and then click Transaction.
6	Clear the selection of the transaction to exclude from the settlement.
7	Click Update.

  > [!NOTE]
  > The tax setoff rule is recalculated, and the components are adjusted accordingly.
Partial settlement of the transactions
8	Select the SGST node, and then click Transaction.
9	Select the transaction, and then update the Recoverable amount to settle field.
10	Click Update.
  > [!NOTE]
  > The tax setoff rule is recalculated, and the components are adjusted accordingly.
  > Excess recoverable, unsettled transactions, and partially settled transactions should be part of the next settlement period.
11	Click Close.
12	Select the Update check box.
13	Click OK.
14	Click OK.
15	Close the report.
 
Validate the tax settlement voucher entries
16	Click General ledger > Setup > Sales tax > Sales tax settlement periods.
17	Select the settlement period, and then click Sales tax payments.
18	Verify that the settlement for the selected registration for the period is posted successfully.

Tax journal
The tax journal lets you post a tax adjustment journal. In the case of reverse charge transactions, where the tax credit should be claimed after the authority settlement, the tax journal lets you claim the tax credit.

1	Click General ledger > Journals > Tax journals.
2	Create a record.
3	In the Date field, enter a value.
4	On the Tax journal lines FastTab, click Add.
5	On the Tax account FastTab, in the Account type field, select Tax.
6	In the Tax type field, select GST.
7	In the Tax component field, select a value.
8	In the Tax posting type field, select Interim recoverable.
9	In the Account field, select a value.
10	In the Offset account type field, select Tax.
11	In the Tax type field, select GST.
12	In the Tax component field, select a value.
13	In the Tax posting type field, select Tax recoverable.
14	In the Account field, select a value.
15	On the journal line, in the Credit field, enter a value.
16	Click Tax information.
17	Click the GST tab.
18	Click OK.
19	Click Tax document.
20	Click Close.
21	Click Post.
22	Close the message.
23	Click Voucher.
 
Tax returns
GSTR1 report data
1	Click General ledger > Reports > India > GER export to GSTR CSV.
2	In the From date field, enter a value.
3	In the To date field, enter a value.
4	In the Registration number field, select a value.
5	In the Configuration field, select GSTR-1 CSV.
6	In the File name field, enter the file name to save the report in comma-separated values (CSV) format. Include the path of the file.
7	Click OK.
8	Use the path that you defined to go to the GSTR1 report file that you created in CSV format. This file becomes the base document that the whole compliance structure in GST is based on.

GSTR2 report data
1	Click General ledger > Reports > India > GER export to GSTR CSV.
2	In the From date field, enter a value.
3	In the To date field, enter a value.
4	In the Registration number field, select a value.
5	In the Configuration field, select a value.
6	In the File name field, enter file name to save the report in CSV format. Include the path of the file.
7	Click OK.
8	Use the path that you defined to go to the GSTR2 report file that you created in CSV format. This file becomes the base document that the whole compliance structure in GST is based on.

Tax inquiry
1	Click General ledger > Inquiries > Tax > India posted tax > Posted tax document transactions.
2	Select the registration number.
3	Click OK.
4	Click Voucher to view the financial entry that is posted for the transaction.
5	Click Close.
6	Click Tax document to view the tax that is calculated on the transaction.
7	Click Close.
8	Click Posted sales tax.
9	Click Close.
10	Click Close.



## Resources for other Microsoft Dynamics products

If you are using one of the following Microsoft Dynamics AX versions, you can use the India GST release to help you be compliant with India GST regulations.

- Microsoft Dynamics AX 2009 SP1
- Microsoft Dynamics AX 2012 R2
- Microsoft Dynamics AX 2012 R3

The India GST release leverages Microsoft Dynamics 365 for Operations (1611) with an applied hotfix to generate GST configurations that you can use in the releases listed. 

For detailed information, including documentation and release package downloads, refer to the following pages:

- [CustomerSource page for the India GST release](https://mbs.microsoft.com/customersource/global/AX/downloads/tax-regulatory-updates/GST-India)
- [PartnerSource page for the India GST release](https://mbs.microsoft.com/partnersource/northamerica/deployment/downloads/tax-regulatory-updates/GST-India) (login required)



