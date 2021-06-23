---
# required metadata

title: What's new or changed for the Indian GST localization in 10.0.15 - 10.0.19
description: This topic describes new or changed functionality for India GST features released in Dynamics 365 Finance versions 10.0.15 - 10.0.19.
author: prabhatb
ms.date: 06/23/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.15, 10.0.16, 10.0.17, 10.0.18, 10.0.19

---

# What's new or changed for the Indian GST localization in 10.0.15 - 10.0.19

[!include [banner](../includes/banner.md)]

This topic provides a summary of the new features and critical bug fixes that were released in Microsoft Dynamics 365 Finance version 10.0.15 - 10.0.19 for the Indian Goods and Services Tax (GST) localization.

## New features
### TCS on sale of goods 

> [!NOTE]
> This feature update is based on CBDT circular number 17 dated 30 September, 2020.

Initially, the following new information regarding when tax would be collected was provided:     

   - When the amount of sale and the amount received as sale consideration exceeds Rs. 50 lakhs during the previous year.  
   - When the amount of sale exceeds Rs. 50 lakhs regardless of the amount of sale consideration received during the previous year.  
   - When the amount received as sale consideration exceeds Rs. 50 lakhs regardless of the amount of sale made during the previous year.   

The initial solution was delivered based on the first bullet in Dynamics 365 Finance, and was released in September 2020. Because of the confusion about the correct implementation of this feature and doubts about the applicability of the new TCS provisions, the CBDT issued Circular No. 17, dated 30-09-2020. The circular clarified that the bullet three is more convenient, realistic, and reasonable to get the expected result.  

To make the solution compliant with the circular, the following changes were incorporated into the existing TCS on sale of goods feature in Finance:    

   - **Initial achieved threshold value**: Per the CBDT clarification, “it may be noted that this TCS shall be applicable only on the amount received on or after 1st October 2020. However, the threshold is based on the yearly receipt, it may be noted that only for calculation of this threshold of Rs. 50 lakhs, the receipt from the beginning of the financial year i.e., from 1st April 2020 shall be taken into account." For example, a seller who has received Rs. 1 crore before 1st October, 2020 from a buyer and receives Rs. 5 lakhs after 1st October, 2020 would be required to collect tax on Rs. 5 lakhs only and not on Rs. 55 lakhs [i.e. Rs.1.05 crore - Rs. 50 lakhs (threshold)]. However the threshold calculation amount received before 1st October will also be considered.    
   - **TCS on the collection of payment from the customer against sales consideration**: Per CBDT clarification “It may be noted that this TCS applies only in cases where the receipt of sale consideration exceeds Rs. 50 lakh in a financial year." For example, a seller who has made sales of Rs. 1 crore before 1st October, 2020 from a buyer and receives only Rs. 10 lakh after 1st October, 2020 wouldn't be required to collect tax on 10 lakh as the payment amount hasn't crossed the threshold value of Rs. 50 lakh. A new fetures can be enabled in **Feature management** to allow TCS deduction on the collection of payment from a customer against a sales consideration.  
   - **Direct voucher posting of TCS amount on payment and invoice transaction**: In the initial solution provided for TCS deduction, the posting was made through related vouchers. Based on the CBDT press note, a re-design enables you to post TCS amounts directly in the ledger without posting through a related voucher.  

For more information about the update for Finance, see, [TCS on sales of goods](apac-ind-gst-tcs-on-sale-of-goods-section-206c-(1h).md) and [LCS issue search](https://fix.lcs.dynamics.com/issue/results/?q=4599032).

For more information about the update for Microsoft Dynamics AX 2012, see [IN-TCS on Sales of Goods ( Changes based on CBDT circular 17 dated 30 Sept.,2020)](https://support.microsoft.com/en-us/topic/in-tcs-on-sales-of-goods-changes-based-on-cbdt-circular-17-dated-30-sept-2020-779e4ab1-8768-0943-a093-960d48a467c3) and [LCS issue search](https://fix.lcs.dynamics.com/issue/results/?q=4598394). To download the update package, see [Withholding tax 206C (1H) law changes as per CBDT circular - Part 2](https://fix.lcs.dynamics.com/Issue/Details?bugId=3983659&dbType=0&qc=7807022dae80c0021a2453e76d1fb2b4d78a87641ed1e2d69ad6a26460299593).

### Dynamic QR code on B2C invoices
With this feature, you can print a dynamic QR code on B2C customer invoices based on the invoice and bank account details. This functionality follows the legislation as required, according to Notification No. 14/2020– Central Tax and Circular no. 146/02/2021-GST.  
 
**Prerequisites:**
 
  - The primary address of the legal entity must be in India.  
  - In the **Feature management** workspace, enable the feature, **(India) Dynamic QR Code on the customer invoice**. For more information, see the [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).  
  - Import the following or higher, GER configurations versions: 

       •	Invoice model mapping (IN).version.249.11.xml  
       •	Dynamic QR Code (IN).version.249.4.xml  
 
During tax invoice generation, the Dynamic QR code would be printed on the invoice layout. The QR code contains information about the required bank account, company, and invoice details which can be further be scanned by the customer. If required, the **Print dynamic QR code** and **Method of payment** field values can be updated on the header of the document from which tax invoice is generated. The QR code contains details of the bank account selected in the **Method of payment**, if provided. Otherwise, the default value for the GSTIN registration number is used.  

This feature is released in versions 10.0.15 - 10.0.19.   

### Dynamics QR code on point of sale
For mor einformation about this feature, see [Generate QR codes and print them on receipts](../../commerce/localizations/ind-generate-qr-code-print-receipt.md).

### GST e-invoices: Export orders, deemed export, and SEZ
This fix supports the changes required to register invoices related to the export orders, demmed export, or delivery to SEZ.

**Prerequisites**
  - The primary address of the legal entity must be in India.
  - In the **Feature management** workspace, enable the feature, **(India) Electronic invoice under the GST**. For more information, see the [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).
  - Configure your environment to use electronic invoicing. For more information, see [A country-specific hotfix to support Electronic invoice under GST for India in Microsoft Dynamics 365 Finance](https://support.microsoft.com/en-us/topic/a-country-specific-hotfix-to-support-electronic-invoice-under-gst-for-india-in-microsoft-dynamics-365-finance-b557920d-93f9-1e6d-3af5-139efc3cb147).
  - Import the following or higher GET configurations:
  
      - Electronic messages framework model, version 34
      - E-Invoice model mapping, version.34.22  
      - E-Invoice format (IN), version 34.5  
      - E-Invoice data import format (IN), version 34.12  
      - Invoice model, version 249  
      - Invoice model mapping (IN), version 249.10  
      - GST Invoice format (IN), version 249.11  

  - From the LCS Share asset library, import the **Indian IRP integration setup v4** data package which includes a predefined electronic messaging setup.

This feature is released in versions 10.0.15 - 10.0.19.   

### TDS on purchase of goods under Section 194Q
This feature is for buyers who are responsible for making payments to a resident for the purchase of goods when the value or aggregate of a purchase from a supplier or payment whichever is earlier, is Rs.50 lacs during the previous year. The transaction with any supplier with the addition of which your aggregate purchase/payment for a purchase from that supplier exceeds Rs.50 lacs, will be the transaction from which TDS is deducted at 10% of the purchase transaction or payment, whichever is earlier. 
  
The following new changes were introduced:  

   - Enable the feature, **Initial threshold value under section 194Q** in the **Feature management** workspace. This feature helps users to include the value of transactions that were executed between 1st April to 30 June, 2021 and drive the achieved threshold value.     
   - Automatically enable the feature, **Reversal of vendor TDS at the time of settlement when deducted on invoice and payment**.  

Per the income tax rule, TDS should be deducted from the invoice or payment, whichever happens earlier. If the user accidentally deducts from both transactions, then during the invoice settlement, the system will reverse the TDS deducted on the later transaction up to the lower transaction value.   
 
For more information about the update for Finance, see [TDS on purchase of goods under Section 194Q](https://support.microsoft.com/en-us/topic/tds-on-purchase-of-goods-under-section-194q-4641db94-9324-4354-9837-7209e5d5d26b) and [KB article 4619159](https://fix.lcs.dynamics.com/Issue/Details?bugId=587591&dbType=3&qc=88c3bab4c44229ca1e1b4dc48e3c5fafc79ee6a2730b96f6a4290623b60ea1db).   

For more information about the update for Dynamics AX 2012 R3, see [KB article 461766](https://fix.lcs.dynamics.com/Issue/Details?bugId=3984343&dbType=0&qc=7b69fc7455089ae54499b4438d52d42c30e02b8b9227a9b6b891e733d30b795f). 

### TDS at a higher rate

**Section 206AB**: This section is applicable when a person fails to file returns for two yars. TDS at a higher rate will apply as follows:

  - Twice the rate specificed in the relevant provision of the Act
  - Twice the rate or rate in force
  - At the rate of 5%

**Section 206CCA**: In this section, TCS is at a higher rate:

  - Twice the rate specified in the relevant provision of the Act
  - A rate of 5%

The existing existing TDS and TCS functionality addresses the new requirements through the following options:  

   - Create multiple threshold definitions for each TDS and TCS type  
   - Create multiple withholding tax codes and withholding tax groups for each TDS and TCS type   

For more information, see [TDS/TCS on non-filer at a higher rate of tax](https://support.microsoft.com/en-us/topic/tds-tcs-on-non-filer-at-a-higher-rate-of-tax-8b0efbde-93d2-4840-9709-ae03e9220c3d).

## Critical fixes

### 10.0.15

- In case the User changed the adjusted withholding tax amount on the Withholding Tax form in the invoice journal, but after close the Withholding Tax form and open it again, the adjusted withholding tax amount does not update. This change will fix this issue.   
- GST amount not showing correctly in the Purchase requisition " Total form " when Purchase requisition created in foreign currency's amount showing in foreign currency whereas Subtotal and Total amount showing in Indian currency. This update will resolve this issue.               
- After posting a payment to the GST authority vendor and updating challan details the system is throwing a warning “the bank reference number constraint must be between 17 and 20 digits” and not allowing to update the details. After this update system will update the CIN number with Challan Number: 14 numeric plus four-digit 4 Alpha bank code.   

### 10.0.17  

- InventTransId for Shipment and Receive is the same for Transfer Order in TaxTrans_IN for posted stock transfer. Users are unable to get the Line wise Tax for Reports from TaxTrans_IN as the InventTransId is the same for shipment and Receipt in TaxTrans_IN. Due to this user unable to get the correct information from Invent table and Tax Trans table and unable to do any report customization. After this update, InventTransId for Shipment and Receive would be different and would be the same as in InvetTransferJourLine for shipment and receipt.   

### 10.0.19  

- When the user goes to the purchase order header and updates the delivery location in the tax information. The TAN number is not getting updated automatically in the PO tax information. This new change will enable TAN details to update automatically in PO tax information.  
- Assessable value is not updating, and it is showing value zero on copying or reversal of Project fee Journal. After this change, the Assessable value will update automatically on copying or reversal of the project fee journal.   
- Vendor payment settles with vendor invoice where withholding tax is applied on Invoice transaction and exchange rate on payment, causing imbalance error. This new change will allow doing invoice settlement with Withholding tax where exchange rate also exists.   
- Users cannot mark or unmark the ‘Shared’ button in the company. This new enhancement will allow the user to mark and unmark the shared button. when user Import data through data entity in the requisite company were for certain customer /Vendor shared checkbox is not marked.  

    - Workaround for old data: Import data through an entity in the requisite company again, then the system will identify this as newly imported data and allow the customer to mark or unmark the ‘Shared’ button in the company  

- Tax rate type from Procurement category is not populating in Tax information in Purchase requisition form. When the user creates a Purchase Requisition using the procurement category Tax rate is not being populated in the tax information. However, when a user creates a Purchase order directly using the procurement category the Tax rate is populated from the Procurement category. After this enhancement tax rate type option will enable in the purchase requisition form for the procurement category.   

## Upcoming critical fixes in 10.0.20

### TDS/TCS inquiry enhancement 
To provide a better performance experience, TDS and TCS inquiries will be included on the **Posted Withholding tax** inquiry page. 
  
### Assessable value update issue for item type BOM  
The upcoming release will resolve the issue of the system selecting the base value of a sale price at the item level but not selecting the net amount value to the assessable value for an item type BOM.  

### Vendor invoice line issue   

When creating vendor invoice lines by selecting **+**, a vendor invoice might be posted without GST applied. The upcoming release will resolve this issue.   

### Sales return order with TCS issue 

When a sales return order is posted with TCS, the posted withholding tax is blank. If a sales return invoice is posted at a time other than the source document transaction date, the issue occurs. For example, if the source document is posted on 25th Feb, 2021 and the sales return is invoiced today, the sales return transactions on the **Posted withholding tax** page are blank. The upcoming release will enable the posting of TCS on sales return orders.    

### Delimiter conflict 

The chart of accounts delimiter in the **General ledger parameters** for cross-company is impacting Indian entities if customers change the delimiter in a US entity. Because the GTE hierarchy can't be updated in USMF, an error will occur. 
 
### TDS and a foreign vendor   

When a customer sets up default exchange rates and TDS exchange rates, the TDS amount is calculated on an updated exchange rate instead of the TDS exchange rate defined in setup. The upcoming release will resolve this issue.  

### Different tax information for order line and charges 

When a purchase order is created with item details and quantity information, the tax information for the purchase is included on the order line. If you add the charges and validate the tax information, details on the company tax are shown instead of the warehouse tax information. After this release, purchase order charges, sales order charges, and order lines will have the same tax information.  

### Accounting currency and reporting currency issues on project invoice proposals

When you create a project contract in a foreign currency, and then create a project invoice proposal with a different invoice date, a balance issue occurs on the posting, accounting, and reporting currencies. Additionally, there are issues with having multiple funding sources for a fee journal and other issues related to tax rates on credit notes.   
 
### Port ID information on shipping bill and BOE header 

Currently, the **Port ID** field is located on the **Shipping bill** page, on the **BOE** header in the **Export incentive schemes** field group. Because incentive schemes are no longer supported in the application, the **Port ID** field and product group fields should be removed from the **Export incentive scheme** field group. You should be able to select the port ID for import and export transactions without enabling the other functionality. Also, because port ID information is provided at the Shipping bill line level, the information should be move from line level to BOE header and Shipping Bill header level so that all the lines in BOE and Shipping bill have
the same Port ID information.   

