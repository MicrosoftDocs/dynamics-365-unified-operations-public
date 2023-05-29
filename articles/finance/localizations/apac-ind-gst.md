---
title: India Goods and Services Tax (GST) overview
description: This article provides detailed information about India Goods and Services Tax (GST) for Microsoft Dynamics 365 Finance.
author: EricWangChen
ms.date: 05/20/2021
ms.topic: overview
ms.prod: 
ms.technology: 
audience: IT Pro, Application User
ms.reviewer: kfend
ms.search.region: India
ms.author: wangchen
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3
ms.custom: 1587884
ms.collection: get-started
---
# India Goods and Services Tax (GST) overview


[!include [banner](../includes/banner.md)]

This article provides detailed information about India Goods and Services Tax (GST). For an overview of the tax engine using India GST examples, watch the following videos.

- [Tax engine overview (YouTube video)](https://www.youtube.com/watch?v=jAFpEBOtNWI&feature=youtu.be)
- [GST overview (Tech Talk)](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-gst-gte-part-1---overview-of-features-roadmap-july-8-2019)
- [GTE overview (Tech Talk)](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-gst-gte-part-2---global-tax-engine-july-10-2019)
- [How to extend GTE (Tech Talk)](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-gst-gte-part-3---extending-gte-july-12-2019)
- [GSTR report overview (Tech Talk)](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-gst-gte-part-4---gstr-reporting-capabilities-july-16-2019)
- [How to extend GER (Tech Talk)](https://community.dynamics.com/365/b/techtalks/posts/finance-and-operations-gst-gte-part-5)

For more information, download the following topics:

 - [Dynamics 365 India GST installation and setup](https://download.microsoft.com/download/4/f/4/4f4607a4-9d07-4f8d-a615-2d36ac7b8608/India_GST_Installation.pdf)
 - [Dynamics 365 India GSTR report extension guide](https://download.microsoft.com/download/9/c/d/9cd9086a-a339-465e-968f-10c0c3080d59/GSTRReportsExtensionguidesJan2020.docx)
 - [Dynamics 365 India tax engine integration](https://download.microsoft.com/download/7/0/5/70541416-72ca-42be-9b1a-f063e2f27d10/Tax_Engine_Integration.pdf)
 - [Dynamics 365 India tax engine demo scripts](https://download.microsoft.com/download/2/1/8/218d7cec-8498-43ed-9ffb-881d8620ab1b/TaxEngineDynamics365forOperations.pdf)
 - [Dynamics 365 India tax engine extension guide](https://download.microsoft.com/download/7/3/4/734cb45b-84b0-4381-92da-7bc0c8d11d36/GTEExtensionguides.pdf)
 
## Prerequisites

<table>
<thead>
<tr>
<th>Prerequisite</th>
<th>Details</th>
</tr>
</thead>
<tbody>
<tr>
<td>Set up business verticals.</td>
<td>On the <strong>Business verticals</strong> page (<strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>India</strong> &gt; <strong>Business verticals</strong>), create business verticals. For more information, see <a href="apac-ind-GST-create-business-vertical.md">Create a business vertical</a>.</td>
</tr>
<tr>
<td>Set up state codes and the union territory designation for Indian states.</td>
<td>On the <strong>Address setup</strong> page (<strong>Organization administration</strong> &gt; <strong>Global address book</strong> &gt; <strong>Addresses</strong> &gt; <strong>Address setup</strong>), be sure to enter state codes for each Indian state. Additionally, if the state is a union territory, set the <strong>Union territory</strong> option to <strong>Yes</strong>. For more information, see <a href="apac-ind-GST-update-state-code-union-territory.md">Update the state code and union territory</a>.</td>
</tr>
<tr>
<td>Set up enterprise tax registration numbers.</td>
<td>
<p>On the <strong>Enterprise tax registration numbers</strong> page (<strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Enterprise tax registration numbers</strong>), create enterprise tax registration numbers for companies, vendors, and customers.</p>
<ul>
<li><strong>Companies:</strong> Create an entry for the Goods and Services Taxpayer Identification Number (GSTIN) for every company, and specify casual registration periods.</li>
<li><strong>Vendors:</strong> Define state GST type registration numbers for vendors.</li>
<li><strong>Customers:</strong> Define state GST type registration numbers for customers.</li>
</ul>
 For more information, see <a href="apac-ind-GST-create-gstin-master.md">Create a GSTIN master</a>.</td>
</tr>
<tr>
<td>Set up GST reference number groups.</td>
<td>GST transactions are differentiated through a unique number sequence. If different number sequence is required for every warehouse or for the addresses of legal entities, you can create a reference number sequence group and assign it to the addresses. For more information, see <a href="apac-ind-gst-reference-groups.md">Set up GST reference number groups</a>.</td>
</tr>
<tr>
<td>Enter GST information for legal entities, warehouses, vendors, or customers.</td>
<td>
<p>For each legal entity, warehouse, vendor, and customer, you can enter a GSTIN. For each legal entity and warehouse, you can select the GST reference number sequence group.</p>
<ul>
<li><strong>Legal entities:</strong> Go to <strong>Organization administration</strong> &gt; <strong>Organizations</strong> &gt; <strong>Legal entities</strong>. On the <strong>Addresses</strong> FastTab, select <strong>More options</strong> &gt; <strong>Advanced</strong>, and then expand the <strong>Tax information</strong> FastTab.</li>
<li><strong>Warehouses:</strong> Go to <strong>Inventory management</strong> &gt; <strong>Setup</strong> &gt; <strong>Inventory</strong> &gt; <strong>Inventory breakdown</strong> &gt; <strong>Warehouses</strong>. On the <strong>Addresses</strong> FastTab, select <strong>Advanced</strong>, and then expand the <strong>Tax information</strong> FastTab.</li>
<li><strong>Vendors:</strong> Go to <strong>Accounts payable</strong> &gt; <strong>Vendors</strong> &gt; <strong>All vendors</strong>, and select a vendor. On the <strong>Addresses</strong> FastTab, select <strong>More options</strong> &gt; <strong>Advanced</strong>, and then expand the <strong>Tax information</strong> FastTab.</li>
<li><strong>Customers:</strong> Go to <strong>Accounts receivable</strong> &gt; <strong>Customers</strong> &gt; <strong>All customers</strong>, and select a customer. On the <strong>Addresses</strong> FastTab, select <strong>More options</strong> &gt; <strong>Advanced</strong>, and then expand the <strong>Tax information</strong> FastTab.</li>
</ul>
</td>
</tr>
<tr>
<td>Create Harmonized System of Nomenclature (HSN) and Services Accounting Code (SAC) codes.</td>
<td><p>Create HSN and SAC codes for all goods and services. The GST rates that are applied depend on the HSN or SAC codes that are assigned to the goods or services.</p>
<ul>
<li><strong>HSN:</strong> Go to <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>HSN code</strong>.</li>
<li><strong>SAC:</strong> Go to <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Service accounting codes</strong>.</li>
</ul>
<p>You can assign HSN and SAC codes to products in the <strong>GST</strong> field group of the <strong>Released products</strong> page. Products of the <strong>Item</strong> item type should have an HSN code, and products of the <strong>Service</strong> item type should have an SAC code.</p>
<p>
<strong>IMPORTANT</strong></br>
The item sales tax group should be removed on products that are assigned an HSN or SAC code.
</p>
</td>
</tr>
<tr>
<td>Assign an SAC code to miscellaneous charges.</td>
<td>
<ol>
<li>Go to <strong>Accounts payable</strong> &gt; <strong>Setup</strong> &gt; <strong>Charges</strong> &gt; <strong>Charges code</strong>, and select a charges code.</li>
<li>On the <strong>Tax information</strong> FastTab, in the <strong>SAC</strong> or <strong>HSN code</strong> field, enter a value.</li>
<li>In the <strong>Service category</strong> or <strong>ITC category</strong> field, enter a value.</li>
<li>Select the <strong>Exempt</strong> check box to exempt these charges from the calculation of GST.</li>
<li>Select <strong>Save</strong>.</li>
</ol>
<p>When this charges code is selected for a transaction, the defined tax information is automatically entered, and GST is calculated accordingly.</p>
<ol>
<li>Go to <strong>Accounts receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Charges</strong> &gt; <strong>Charges code</strong>, and select a charges code.</li>
<li>On the <strong>Tax information</strong> FastTab, in the <strong>SAC</strong> or <strong>HSN code</strong> field, enter a value.</li>
<li>Select the <strong>Exempt</strong> check box to exempt these charges from the calculation of GST.</li>
<li>Select <strong>Save</strong>.</li>
</ol>
<p>When this charges code is selected for a transaction, the defined tax information is automatically entered, and GST is calculated accordingly.</p>
</td>
</tr>
<tr>
<td>Create main accounts for the GST posting type.</td>
<td><p>Go to <strong>General ledger</strong> &gt; <strong>Common</strong> &gt; <strong>Main accounts</strong>, and create a main account for each state-wide ledger account that is required. On the <strong>Setup</strong> FastTab, be sure to select <strong>GST</strong> as the posting type.</p>
<p>For more information, see <a href="../general-ledger/tasks/create-main-account.md">Create a main account</a>.</p>
</td>
</tr>
<tr>
<td>Create a GST authority.</td>
<td>
<ol>
<li>Go to <strong>Accounts payable</strong> &gt; <strong>Vendors</strong> &gt; <strong>All vendors</strong>, and create a vendor record for the GST authority.</li>
<li>Go to <strong>Tax</strong> &gt; <strong>Indirect taxes</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Sales tax authorities</strong>, and create a sales tax authority by using the GST authority vendor account.</li>
</ol>
</td>
</tr>
<tr>
<td>Create a tax period for GST.</td>
<td>Go to <strong>Tax</strong> &gt; <strong>Indirect taxes</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Sales tax settlement periods</strong>, and create a sales tax period for GST.</td>
</tr>
<tr>
<td>Create a GST tax registration group.</td>
<td>Go to <strong>Tax</strong> &gt; <strong>Setup</strong> &gt; <strong>Sales tax</strong> &gt; <strong>Tax registration group</strong>, create a tax registration group, and add GSTIN information.</td>
</tr>
</tbody>
</table>

## Import the configuration and deploy it to a specific company

Before you complete this task, be sure to save all the configuration files in a location that you can access from Dynamics 365 Finance.

Follow these steps to load the configurations and map them to a legal entity.

### Tax configurations

Follow the process in the article, [Tax engine import configuration](../general-ledger/tax-engine-import-configuration.md) to import the tax configurations and report configurations.

### GST configurations

| Version                                                                                                                                     | Details                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <ul><li>Taxable Document.version.61.xmlTaxable</li><li>Document (India).version.61.112.xml</li><li>Tax (India GST).version.61.113.213.xml</li></ul>  | Microsoft Dynamics 365 Finance, Enterprise edition (7.3) GA configuration                                                                                                                                                                                                                                                                                                                                                                                              |
| <ul><li>Taxable Document.version.62.xml</li><li>Taxable Document (India).version.62.115.xml</li><li>Tax (India GST).version.62.115.217.xml</li></ul> | KB#4094699                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| <ul><li>Taxable Document.version.63.xml</li><li>Taxable Document (India).version.63.116.xml</li><li>Tax (India GST).version.63.116.218.xml</li></ul> | Support GST on project module Microsoft Dynamics 365 Finance (8.0) GA configuration 7.3 with KB#4094699 and KB#4135145                                                                                                                                                                                                                                                                                                                                                 |
| <ul><li>Taxable Document.version.64.xml</li><li>Taxable Document (India).version.64.117.xml</li><li>Tax (India GST).version.64.117.221.xml</li></ul> | Support GST on Bank charge 7.3 with KB#4094699, KB#4135145 and KB#4457539 8.0 with KB#4458726                                                                                                                                                                                                                                                                                                                                                                                             |
| <ul><li>Taxable Document.version.71.xml</li><li>Taxable Document (India).version.71.120.xml</li><li>Tax (India GST).version.71.120.225.xml</li></ul> | Add several new fields into taxable documents, Ship from/to xxx, Product Category, Customer group, Vendor group, Prepayment 7.3 + KB#4094699 + KB#4135145 + KB#4457539 8.0 + KB#4458726 8.1.1                                                                                                                                                                                                                                                                                             |
| <ul><li>Taxable Document.version.81.xml</li><li>Taxable Document (India).version.81.138.xml</li><li>Tax (India GST).version.81.138.247.xml</li></ul> | Add invoice date into GST, Rate lookup Enable Non-GST, if Non-GST is marked trans tax information, GST will not be applicable Microsoft Dynamics 365 Finance (10.0)                                                                                                                                                                                                                                                                                                    |
| <ul><li>Taxable Document.version.82.xml</li><li>Taxable Document (India).version.82.143.xml</li><li>Tax (India GST).version.82.143.263.xml</li></ul> | Solve the issue of zero tax base for tax exempt transaction Support CGST&SGST for intra-state stock transfer order between warehouses with different GST registrations Support VAT Support Tax Rate Type Microsoft Dynamics 365 Finance (10.0.5)                                                                                                                                                                                                                       |
| <ul><li>Taxable Document.version.82.xml</li><li>Taxable Document (India).version.82.143.xml</li><li>Tax (India GST).version.82.143.264.xml</li></ul> | Remove the tax rate type from Tax Document which should be used by customers who have not updated their terminal to 10.0.5 Microsoft Dynamics 365 Finance (10.0.5)                                                                                                                                                                                                                                                                                                      |
| <ul><li>Taxable Document.version.82.xml</li><li>Taxable Document (India).version.82.143.xml</li><li>Tax (India GST).version.82.143.267.xml</li></ul> | <ul><li>Support Applicable % of tax rate. The configuration can only be used in 10.0.9.</li><li>If you are retail customers, you need to make sure the retail has a version of Microsoft.Dynamics365.Tax.dll equal to or above 10.0.4006 and the HQ has a version of Microsoft.Dynamics365.Tax.dll equal to 10.0.9007.</li><li>The configuration is created on version 82.143.263, if you have configuration extension on 82.143.264, you have to re-extend based on 82.143.267.</li></ul> |
| <ul><li>Taxable Document.version.82.xml</li><li>Taxable Document (India).version.82.155.xml</li><li>Tax (India GST).version.82.155.300.xml</li></ul> | <ul><li>Support the IGST tax calculation when the <b>with IGST payment</b> option is set to <b>Yes</b> on the SEZ/DE/Export order. The configuration can be used only in version 10.0.14 and later.</li></ul> |
| <ul><li>Taxable Document.version.82.xml</li><li>Taxable Document (India).version.82.155.xml</li><li>Tax (India GST).version.82.155.301.xml</li></ul> | <ul><li>Support decoupling of GST posting from inventory posting and the addition of **Interim transit** as a stock transfer posting type. The configuration can be used only in version 10.0.14 and later.</li></ul> |
| <ul><li>Taxable Document.version.82.xml</li><li>Taxable Document (India).version.82.156.xml</li><li>Tax (India GST).version.82.156.302.xml</li></ul> | <ul><li>Support calculation of GST-TDS in vendor and customer payment journals. The configuration can be used only in version 10.0.18 and later.</li></ul> |

### Report configurations

| Version                                                                                                                                                                                                                                                                                                                          | Details                                                                                                                                                                                                                                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>**GST offline tool format**:</p><ul><li>GSTReturnsGovt.version.4.xml</li><li>GST Returns govt. model mapping.xml</li><li>GSTR1GovtCSV.version.4.9.xml</li></ul><p>**GSTR1/GSTR2**:</p><ul><li>GSTReturns.version.12.xml</li><li>GSTReturns.ModelMapping.version.12.3..xml</li><li>GSTR1CSV.version.12.25.xml</li><li>GSTR2CSV.version.12.29.xml</li></ul> | Microsoft Dynamics 365 Finance, Enterprise edition (7.3) GA configuration                                                                                                                                                                          |
| <ul><li>GSTReturns.version.14.xml GST</li><li>Returns model mapping.version.14.5.xml</li><li>GSTR1CSV.version.14.28.xml</li><li>GSTR2CSV.version.14.32.xml</li></ul>                                                                                                                                                                     | Total Item Discount Amount is not coming in GSTR. Item Unit Of Measurement should show both the unit and description. Service item should be **Nos**. No customer billing name for stock transfer in GSTR. Microsoft Dynamics 365 Finance (10.0.1) |
| <p>**GST offline tool format**:</p><ul><li>GSTReturnsGovt.version.19.xml</li><li>GST Returns govt. model mapping.19.12.xml</li><li>GST ANX-1 Govt. offline tool.version.19.22.xml</li><li>GSTR1GovtCSV.version.19.10.xml</li><li>Purchase Register.version.19.7.xml</li></ul><p>**GSTR1/GSTR2**:</p><ul><li>GSTReturns.version.16.xml</li><li>GSTReturns.ModelMapping.version.16.7.xml</li><li>GSTR-1 for Old Return 16.32.xml</li><li>GSTR-1 for New Return 16.41.xml</li><li>GSTR-2 for Old Return 16.36.xml</li><li>GSTR-2 for New Return 16.40.xml</li></ul> | GSTR for New Return, ANX-1 Govt. offline tool, and Purchase register. Dynamics 365 Finance version 10.0.14.                                                                                                                                                                |

### Map configurations to the Legal entity

1. Go to **Tax** \> **Setup** \> **Tax configuration** \> **Tax setup**.
2. Select **New**.
3. In the **Tax setup** field, enter a value.
4. In the **Description** field, enter a value.
5. Select **Configurations**.
6. On the **Tax configuration** FastTab, under **Available configurations**, select the ellipsis button (**...**), and then select **New**.
7. In the **Configuration version** field, select a value. The new tax configuration is listed in the **Available configurations** grid.
8. Select the ellipsis button (**...**), and then select **Synchronize**.
9. Select **Activate**. The activated configuration is updated as the current configuration.

   ![Current configuration.](media/apac-ind-gst-Current-Configuration.png)

10. On the **Report configuration** FastTab, under **Select report configurations**, select the **Select** checkbox.
11. In the **Report controller** field, select a value.
12. Repeat step 10 and 11, to map the report configurations.

    ![Report configuration.](media/apac-ind-gst-Reportconfiguration2-configuration.png)

13. Close the page.
14. On the **Companies** FastTab, create a record.
15. In the **Companies** field, select a value, and then select **Save**.
16. On the **Companies** FastTab, select **Activate**. The tax setup is now active for the selected company.

    ![Tax setup status.](media/apac-ind-gst-tax-setup-status.png)

## Update the configuration version

1. Go to **Tax** &gt; **Setup** &gt; **Tax configuration** &gt; **Tax setup**.
2. Select a tax setup.
3. On the **Companies** FastTab, select **Deactivate**.
4. Repeat steps 2 through 13 in the previous section, [Import the configuration and deploy it to a specific company](#import-the-configuration-and-deploy-it-to-a-specific-company), to load the configuration, deploy it to the company, and synchronize the new version.

   ![Two configurations.](media/apac-ind-gst-Available2-configuration.png)

5. Select the new version, and then select **Activate**.
6. Complete the tasks in the **Tax setup** section to update data for the new version.

   > [!IMPORTANT]
   > If the tasks in the [Tax setup](#tax-setup), section were previously completed for the old configuration version, the data is retained after you synchronize to the new configuration version. You just have to review the setup and update it according to the new changes.

## Tax setup

This section walks you through defining the GST and Customs tax setup.

### Map configuration tax types to ERP tax types (Customs)

1. Go to **Tax** &gt; **Setup** &gt; **Tax configuration** &gt; **Tax setup**.
2. Select a tax setup, and then select a company.
3. Select **Setup**.
4. Select the **Customs** node.
5. On the **Tax type mapping** tab, in the **Tax type** field, select **Customs**.
6. Define a tax period:

   1. Select the node for the tax component.
   2. On the **Tax period mapping** tab, in the **Period** field, select a value.

7. Define main accounts:

   1. On the **Accounting** tab, on the **Conditions** FastTab, select **Add**.
   2. In the **Import Order** field, select a value.
   3. In the **Export order** field, select a value.
   4. Save the record.
   5. On the **Values** FastTab, in the **Main account** field, select a value.

      > [!NOTE]
      > The list of accounts is generated dynamically, based on the posting profile from the configuration. The posting type of the selected main account should be **Customs**.

   6. Select the **IGST CUS** node.
   7. On the **Values** FastTab, in the **Main account** field, select a value.

      > [!NOTE]
      > The main account that you selected for **Customs duty accrual** should be the same account that you selected as the Customs duty accrual account for the **GST** &gt; **IGST** node.

### Map configuration tax types to ERP tax types (GST)

1. Go to **Tax** &gt; **Setup** &gt; **Tax configuration** &gt; **Tax setup**.
2. Select a company.
3. Select **Setup**.
4. Select the **GST** node.
5. On the **Tax type mapping** tab, in the **Tax type** field, select **GST**.
6. Define a tax period:

   1. Select the node for the tax component.
   2. On the **Tax period mapping** tab, in the **Period** field, select a value.

7. Define main accounts:

   1. On the **Accounting** tab, on the **Conditions** FastTab, select **Add**.
   2. In the **GST Registration Number** field, select a value.
   3. Save the record.
   4. On the **Values** FastTab, in the **Main account** field, select a value.

      > [!NOTE]
      >
      > - The list of accounts is generated dynamically, based on the posting profile from the configuration.
      > - Tax main accounts can be defined at the level of either the tax type or the tax component. The value at the tax component level overrides the value at the tax type level. If the field is left blank for a posting type at the tax component level, the corresponding value from the tax type level is used for posting. We recommend that you set up the tax accounts at the tax component level for each registration.

8. Set up rate and percentage tables:

   1. Expand the node for the tax component.
   2. Select the **Rate** node, and then, in the **Value** field, define the tax rates.
   3. Select the **Reverse Charge Percentage** node, and then, in the **Value** field, define the reverse charge percentage.
   4. Select the **Load on Inventory Percentage** node, and then, in the **Value** field, define the load on inventory percentage.
   5. Select **Close**.
   6. Select **Parameters**.
   7. In the **Tax journal name** field, select a value. (This step is required in order to post the tax adjustments.)
   8. In the **Tax journal voucher series** field, select a value.
   9. Select **OK**.

9. Set up a sales tax hierarchy, and maintain setoff rule profiles:

   1. Go to **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Sales tax hierarchies**.
   2. Select **New**.
   3. In the **Name** field, enter a value.
   4. In the **Structure** field, select **GTE hierarchy**.
   5. Select **OK**.
   6. On the **Versions** FastTab, select **Synchronize**.
   7. Close the message.
   8. Select **View**. The **Sales tax hierarchy designer** page shows the tax type and tax components, based on the configuration.

      ![Sales tax hierarchy designer.](media/apac-ind-gst-salestaxdesigner.png)

   9. Select **Setoff rules for sales tax hierarchy**.
   10. Select **New**.
   11. In the **Name** field, enter a value.
   12. Save the record.
   13. On the **Recoverable** FastTab, select the tax components, and then adjust the **Priority** values.
   14. On the **Payable** FastTab, select the tax components, and then adjust the **Priority** values.
   15. Define the setoff rules according to the legal requirement.

       ![Setoff rule.](media/apac-ind-gst-View-Setoffrule.png)

   16. Select **Close**.
   17. Close the **Sales tax hierarchy designer** page.
   18. Select **Activate**.
   19. Select **Close**.

### Maintain setoff hierarchy profiles

1. Go to **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **Maintain setoff hierarchy profiles**.
2. Select **New**.
3. In the **Effective date** field, enter a value.
4. In the **Hierarchy** field, select a value.
5. Select **OK**.
6. Select **Activate**.
7. Select **Yes** in the message.
8. Close the message.
9. Close the page.

### Create GST minor codes

1. Go to **Tax** &gt; **Setup** &gt; **Sales tax** &gt; **India** &gt; **GST minor codes**.
2. Select **New**.
3. In the **Tax component** field, select a value.
4. In the **Minor code** field, enter a value.
5. In the **Description** field, enter a value.

## Print management

Complete the following procedures to select the India GST report formats for customer and vendor invoices.

### Accounts payable

1. Go to **Accounts payable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**.
2. On the **General** tab, select **Print management**.
3. Expand the **Vendor invoice** node, and select **Original**.
4. Select **VendInvoiceDocument_IN.Report** as the report format.

### Accounts receivable

1. Go to **Accounts receivable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**.
2. On the **General** tab, select **Print management**.
3. Expand the **Customer invoice** node, and select **Original**.
4. Select **SalesInvoice_IN.Report** as the report format.
5. Expand the **Free text invoice** node, and select **Original**.
6. Select **FreeTextInvoice.ReportIN** as the report format.

## Trouble shooting guide

The tax engine is a highly configurable engine handling tax applicability, calculation, posting, and settlement. Please refer to [trouble shooting guide](tax-engine-trouble-shooting.md) first whenever you encounter any issues.

## Resources for other Microsoft Dynamics products

If you're using one of the following versions of Microsoft Dynamics AX, you can use the India GST release to help you be compliant with India GST regulations:

- Microsoft Dynamics AX 2009 SP1
- Microsoft Dynamics AX 2012 R2
- Microsoft Dynamics AX 2012 R3

The India GST release takes advantage of Microsoft Dynamics 365 for Operations (1611) together with an applied hotfix to generate GST configurations that you can use in your release of Microsoft Dynamics AX.

For more detailed information, see the following documentation and downloads for release packages.

 - **Releases**
 
    -  [Dynamics AX 2012 R3 India GST Zip file](https://download.microsoft.com/download/B/1/5/B153F120-80F4-44B9-B195-D5640F7E3809/AX2012R3KB4019353.zip) and [KB 4038381](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4038381&bugId=3848435&qc=8ef1680f3dd0d4fbb43a091f5613572d23b97fefb71a7cbab0fe6ee95b3d1b31)
    -  [Dynamics AX 2012 R2 India GST Zip file](https://download.microsoft.com/download/D/8/5/D853E47A-8947-41AF-A61A-66000B1F850C/AX2012R2KB4019353.zip) and [KB 4032545](https://fix.lcs.dynamics.com/Issue/Resolved?kb=4032545&bugId=3839206&qc=fd7ed4f0a46eef63eef7b02da5c3a3562ba09dfca6ce5f430887c64bf8d73fa5)
    -  [Dynamics AX 2009 SP1 update](https://download.microsoft.com/download/E/F/A/EFAD7102-43BF-4ADD-AB01-94F74CC12C1F/DynamicsAX2009-KB4032546-SP1.zip), [Dynamics AX 2009 SP1 India GST hotfix 1](https://download.microsoft.com/download/8/F/0/8F0819F1-DD0E-49FC-8D87-AD48E30DAA1D/AX2009SP1KB4019353.zip), and [Dynamics AX 2009 SP India GST hotfix 2](https://download.microsoft.com/download/6/6/E/66E4305D-9266-4E46-A0A8-86448A6CC78F/DynamicsAX2009-KB4033207-SP1.EXE)
 
 - **Release notes**

    - [Dynamics AX 2009 SP1, AX 2012 R2, and AX 2012 R3 India GST release notes](https://download.microsoft.com/download/1/0/1/101e86d1-ad6b-4005-a098-56ded753125d/ReleaseNote_India_GST.pdf)
    - [Dynamics AX 2012 R3 India GST update 1 release notes](https://download.microsoft.com/download/f/8/3/f8334213-e5d1-4fce-be47-05cf4f28ddc0/India-GST-Update-ReleaseNote.pdf)
    - [Dynamics AX 2009 SP1, AX 2012 R2, and AX 2012 R3 India GST update 2 release notes](https://download.microsoft.com/download/2/7/6/276e0aa8-35a4-4b9d-a9a1-970692b7c91c/Release-Note-India-GST-Update-2.pdf)

 - **Install and setup**

    - [Dynamics AX 2009 SP1 India GST update 1 installation guide](https://download.microsoft.com/download/3/6/9/369dfc13-a0ae-4c5d-9003-6667a51d1991/Installation-India-GST-Update1-AX2009SP1.pdf)
    - [Dynamics AX 2012 R2 India GST update 1 installation guide](https://download.microsoft.com/download/2/2/5/225a37a8-4c0d-4204-9059-340a1e5b5bba/Installation-India-GST-Update1-AX2012R2.pdf)
    - [Dynamics AX 2012 R3 India GST update 1 installation guide](https://download.microsoft.com/download/d/c/7/dc77331a-ce82-4733-81e9-1c7397295502/Installation-India-GST-Update1-AX2012R3.pdf)
    - [Dynamics AX 2009 SP1 India GST update 2 installation guide](https://download.microsoft.com/download/f/4/f/f4fd3a67-2284-4b69-82e6-ca52d6131e1d/AX2009SP1-Install-India-GST-Update2.pdf)
    - [Dynamics AX 2012 R2 India GST update 2 installation guide](https://download.microsoft.com/download/2/c/b/2cbb982f-a288-457d-9cd7-9f682d395e79/AX2012R2-Install-India-GST-Update2.pdf)
    - [Dynamics AX 2012 R3 India GST update 2 installation guide](https://download.microsoft.com/download/0/0/b/00bc4bd3-4a02-4cab-8415-c21fcbeac7e6/AX2012R3-Install-India-GST-Update2.pdf)

 - **Tax engine**

    - [Dynamics AX 2009 India tax engine demo scripts](https://download.microsoft.com/download/2/f/e/2fed3e11-83d6-46c9-8413-fe3730d4d0eb/TaxEngineAX2009SP1.pdf)
    - [Dynamics AX 2012 India tax engine demo scripts](https://download.microsoft.com/download/3/5/5/355216d8-75d5-4df9-bdc6-d7a68fbfa02a/TaxEngineAX2012.pdf)
    - [Dynamics AX 2012 India tax](https://download.microsoft.com/download/3/0/e/30eada2a-6ab8-44c6-b0cf-d28df8ddf14f/Whitepaper_TaxEngineAX2012.pdf)

  - **E-way bill**

    - [Dynamics AX 2009 E-way bill ](https://download.microsoft.com/download/1/0/d/10d3a95a-69d3-4630-bcc6-5f1a3a01efd0/E-WaybillUserguideAX2009.pdf)
    - [Dynamics AX 2012 E-way bill ](https://download.microsoft.com/download/1/3/b/13b719ee-1e8d-4436-8915-16be7bb57081/E-WaybillDemoScriptAX2012.pdf)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

