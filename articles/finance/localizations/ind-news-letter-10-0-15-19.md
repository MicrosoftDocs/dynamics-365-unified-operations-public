---
# required metadata

title: What's new or changed for the Indian GST localization in 10.0.15-10.0.19
description: This article describes new or changed functionality for Indian Goods and Services Tax (GST) features in Microsoft Dynamics 365 Finance versions 10.0.15 through 10.0.19.
author: prabhatb
ms.date: 06/28/2021
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

# What's new or changed for the Indian GST localization in 10.0.15-10.0.19

[!include [banner](../includes/banner.md)]

This article provides a summary of the new features and critical bug fixes that were released in Microsoft Dynamics 365 Finance versions 10.0.15 through 10.0.19 for the Indian Goods and Services Tax (GST) localization.

## New features

### TCS on sale of goods

> [!NOTE]
> This feature update is based on Central Board of Direct Taxes (CBDT) circular number 17, dated September 30, 2020.

According to the new information that was originally provided, tax would be collected when the following conditions were met:

- When the amount of the sale and the amount that was received as a sale consideration exceed 50 lakh rupees (Rs. 50 lakh) during the previous year
- When the amount of the sale exceeds Rs. 50 lakh, regardless of the amount of the sale consideration that was received during the previous year
- When the amount that was received as a sale consideration exceeds Rs. 50 lakh, regardless of the amount of the sale that was made during the previous year

The initial solution that was delivered in Finance was based on the first item in the preceding list. That solution was released in September 2020. However, because of confusion about the correct implementation of the feature and doubts about the applicability of the new Tax Collected at Source (TCS) provisions, the CBDT issued circular number 17, dated September 30, 2020. That circular clarified that the third item in the list is a more convenient, realistic, and reasonable way to get the expected result.

Therefore, to make the solution compliant with circular number 17, the following changes were incorporated into the existing feature for TCS on sales of goods in Finance:

- **Initial achieved threshold value:** The CBDT clarification states, "It may be noted that this TCS shall be applicable only on the amount received on or after 1st October 2020. However, the threshold is based on the yearly receipt, it may be noted that only for calculation of this threshold of Rs. 50 lakhs, the receipt from the beginning of the financial year i.e., from 1st April 2020 shall be taken into account."

    For example, a seller received 1 crore rupee (Rs. 1 crore) from a buyer before October 1, 2020, and then receives Rs. 5 lakh after October 1, 2020. This seller must collect tax only on the Rs. 5 lakh, not on Rs. 55 lakh (that is, Rs. 1.05 crore – Rs. 50 lakh \[the threshold\]). However, the threshold calculation amount that was received before October 1 is also considered.

- **TCS on the collection of payment from the customer against a sales consideration:** The CBDT clarification states, "It may be noted that this TCS applies only in cases where the receipt of sale consideration exceeds Rs. 50 lakh in a financial year."

    For example, a seller made sales of Rs. 1 crore from a buyer before October 1, 2020, but received only Rs. 10 lakh after October 1, 2020. This seller doesn't have to collect tax on the Rs. 10 lakh, because the payment amount didn't cross the threshold value of Rs. 50 lakh. A new feature that can be turned on in Feature management enables TCS deduction on the collection of payment from a customer against a sales consideration.

- **Direct voucher posting of TCS amounts on payment and invoice transactions:** In the initial solution that was provided for TCS deduction, the posting was made through related vouchers. However, based on the CBDT press note, the solution was redesigned and now lets you post TCS amounts directly in the ledger. You no longer have to post them through a related voucher.

For more information about the update for Finance, see, [TCS on sales of goods](apac-ind-gst-tcs-on-sale-of-goods-section-206c-(1h).md) and [LCS issue search](https://fix.lcs.dynamics.com/issue/results/?q=4599032).

For more information about the update for Dynamics AX 2012, see [IN-TCS on Sales of Goods ( Changes based on CBDT circular 17 dated 30 Sept.,2020)](https://support.microsoft.com/topic/in-tcs-on-sales-of-goods-changes-based-on-cbdt-circular-17-dated-30-sept-2020-779e4ab1-8768-0943-a093-960d48a467c3) and [LCS issue search](https://fix.lcs.dynamics.com/issue/results/?q=4598394). To download the update package, see [Withholding tax 206C (1H) law changes as per CBDT circular - Part 2](https://fix.lcs.dynamics.com/Issue/Details?bugId=3983659&dbType=0&qc=7807022dae80c0021a2453e76d1fb2b4d78a87641ed1e2d69ad6a26460299593).

### Dynamic QR codes on B2C invoices

This feature lets you print a dynamic QR code on business-to-consumer (B2C) customer invoices, based on the invoice and bank account details. This functionality follows the legislation as required, according to notification number 14/2020 – Central Tax and circular number 146/02/2021-GST.

**Prerequisites:**

- The primary address of the legal entity must be in India.
- In the **Feature management** workspace, turn on the feature that is named **(India) Dynamic QR Code on the customer invoice**. For more information, see [Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).
- Import the following versions or later of these Electronic reporting (ER) configurations:

    -	Invoice model mapping (IN).version.249.11.xml
    -	Dynamic QR Code (IN).version.249.4.xml

During tax invoice generation, the dynamic QR code is printed on the invoice layout and can be scanned by the customer. The QR code contains information about the required bank account, company, and invoice details.

The values of the **Print dynamic QR code** and **Method of payment** fields can be updated, as required, on the header of the document that the tax invoice is generated from. If a bank account is selected in the **Method of payment** field, the QR code contains details of that bank account. Otherwise, the default value for the Goods and Services Tax Identification Number (GSTIN) registration number is used.

This feature is released in versions 10.0.15 through 10.0.19.

### Dynamics QR codes in Point of sale

For more information about this feature, see [Generate QR codes and print them on receipts](../../commerce/localizations/ind-generate-qr-code-print-receipt.md).

### GST e-invoices: Export orders, deemed export, and SEZ

This fix supports the changes that are required to register invoices that are related to export orders, deemed export, or delivery to special economic zones (SEZs).

**Prerequisites**

- The primary address of the legal entity must be in India.
- In the **Feature management** workspace, turn on the feature that is named **(India) Electronic invoice under the GST**. For more information, see [Feature management overview](/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).
- Configure your environment to use electronic invoicing. For more information, see [A country/region-specific hotfix to support Electronic invoice under GST for India in Microsoft Dynamics 365 Finance](https://support.microsoft.com/topic/a-country-specific-hotfix-to-support-electronic-invoice-under-gst-for-india-in-microsoft-dynamics-365-finance-b557920d-93f9-1e6d-3af5-139efc3cb147).
- Import the following versions or later of these ET configurations:

    - Electronic messages framework model, version 34
    - E-Invoice model mapping, version.34.22
    - E-Invoice format (IN), version 34.5
    - E-Invoice data import format (IN), version 34.12
    - Invoice model, version 249
    - Invoice model mapping (IN), version 249.10
    - GST Invoice format (IN), version 249.11

- From the Shared asset library in Microsoft Dynamics Lifecycle Services (LCS), import the **Indian IRP integration setup v4** data package. This package includes a predefined electronic messaging setup.

This feature is released in versions 10.0.15 through 10.0.19.

### TDS on the purchase of goods under section 194Q

This feature is for buyers who are responsible for making payments to a resident for the purchase of goods when the value or aggregate of either a purchase from a supplier or a payment (whichever occurs earlier) is Rs. 50 lakh during the previous year. If a transaction with a supplier causes your aggregate purchase from that supplier, or your aggregate payment for a purchase from that supplier, to exceed Rs. 50 lakh, Tax Deducted at Source (TDS) will be deducted from that transaction at a rate of 10 percent of either the purchase transaction or the payment for it (whichever occurs earlier).

The following new changes were introduced:

- Enable the feature that is named **Initial threshold value under section 194Q** in the **Feature management** workspace. This feature helps users include the value of transactions that were executed between April 1 and June 30, 2021, and drive the achieved threshold value.
- Automatically enable the feature that is named **Reversal of vendor TDS at the time of settlement when deducted on invoice and payment**.

Per the income tax rule, TDS should be deducted from either the invoice or the payment (whichever occurs earlier). If you accidentally deduct from both transactions, the system reverses the TDS that was deducted from the later transaction, up to the lower transaction value, during invoice settlement.
 
For more information about the update for Finance, see [TDS on purchase of goods under Section 194Q](https://support.microsoft.com/topic/tds-on-purchase-of-goods-under-section-194q-4641db94-9324-4354-9837-7209e5d5d26b) and [KB article 4619159](https://fix.lcs.dynamics.com/Issue/Details?bugId=587591&dbType=3&qc=88c3bab4c44229ca1e1b4dc48e3c5fafc79ee6a2730b96f6a4290623b60ea1db).

For more information about the update for Dynamics AX 2012 R3, see [KB article 461766](https://fix.lcs.dynamics.com/Issue/Details?bugId=3984343&dbType=0&qc=7b69fc7455089ae54499b4438d52d42c30e02b8b9227a9b6b891e733d30b795f).

### TDS at a higher rate

- **Section 206AB:** This section is applicable when a person fails to file returns for two years. TDS will be applied at a higher rate, as described here:

    - Twice the rate that is specified in the relevant provision of the Income Tax Act
    - Twice the rate or rates that are in effect
    - A rate of 5 percent

- **Section 206CCA:** TCS will be applied at a higher rate, as described here:

    - Twice the rate that is specified in the relevant provision of the Act
    - A rate of 5 percent

The existing TDS and TCS functionality addresses the new requirements through the following options:

- Create multiple threshold definitions for each TDS and TCS type.
- Create multiple withholding tax codes and withholding tax groups for each TDS and TCS type.

For more information, see [TDS/TCS on non-filer at a higher rate of tax](https://support.microsoft.com/topic/tds-tcs-on-non-filer-at-a-higher-rate-of-tax-8b0efbde-93d2-4840-9709-ae03e9220c3d).

## Released critical fixes

### 10.0.15

- If you change the adjusted withholding tax amount on the **Withholding tax** page in the invoice journal, the adjusted withholding tax amount isn't updated after you close and reopen the page. This update fixes this issue.
- If a purchase requisition is created in a foreign currency, and the subtotal and total amounts are in the Indian currency, the GST amount isn't shown correctly on the **Total** page for the purchase requisition. This update fixes this issue.
- After you post a payment to the GST authority vendor and update challan details, you receive the following warning message: "The bank reference number constraint must be between 17 and 20 digits." However, you can't update the details. After this update, the system will update the Corporate Identity Number (CIN) with the challan number: 14 numeric digits, plus a four-digit 4 Alpha bank code.

### 10.0.17

- The **InventTransId** value for shipment and receipt is the same for a transfer order in **TaxTrans\_IN** for a posted stock transfer, and you can't get the line tax for reports from **TaxTrans\_IN**. Therefore, you can't get the correct information from the **Invent** table and the **TaxTrans** table, and you can't do any report customization. After this release, the **InventTransId** value for shipment and receipt is different. It's now the same as in **InvetTransferJourLine** for shipment and receipt.

### 10.0.19

- When you update the **Delivery location** value on the **Purchase order** page header, the Tax Deduction and Collection Account Number (TAN) isn't automatically updated in the purchase order tax information. This release enables the TAN to be automatically updated in purchase order tax information.
- The assessable value isn't updated and is shown as 0 (zero) when a project fee journal is copied or reversed. After this release, the assessable value is automatically updated when the project fee journal is copied or reversed.
- An imbalance error occurs when a vendor payment is settled with a vendor invoice where withholding tax is applied on the invoice transaction and an exchange rate is applied on the payment. The updates in this release let you complete an invoice settlement that has withholding tax where an exchange rate also exists.
- You can't select or clear the **Shared** checkbox in the company. The updates in this release let you select and clear the **Shared** checkbox. When you import data through the data entity in the requisite company for a customer or vendor, the **Shared** checkbox is cleared. To work around this issue for older data, import the data through an entity in the requisite company again. The system will then identify the data as newly imported data, and you will be able to select or clear the **Shared** checkbox for the company.
- When you create a purchase requisition that uses a procurement category, the **Tax rate** field isn't filled in with the tax rate type from the procurement category. However, when you create a purchase order that uses a procurement category, the **Tax rate** field is filled in from the procurement category. After this release, the option for the tax rate type is enabled on the **Purchase requisition** page for the procurement category.

## Upcoming critical fixes in 10.0.20

### TDS/TCS inquiry enhancement

To provide a better performance experience, TDS and TCS inquiries will be included on the **Posted Withholding tax** inquiry page.

### Assessable value update issue for item-type BOMs

The upcoming release will fix an issue where the system selects the base value of a sale price at the item level but doesn't select the net amount value of the assessable value for an item-type bill of materials (BOM).

### Vendor invoice line issue

When you select the plus sign (**+**) to create vendor invoice lines, GST might not be applied when a vendor invoice is posted. The upcoming release will fix this issue.

### Sales return order with TCS issue

When a sales return order that is posted has TCS, the posted withholding tax is blank. If a sales return invoice is posted at a time other than the transaction date of the source document, the issue occurs. For example, if the source document is posted on February 25, 2021, and the sales return is invoiced today, the sales return transactions on the **Posted withholding tax** page are blank. The upcoming release will enable TCS to be posted on sales return orders.

### Delimiter conflict

The chart of accounts delimiter in the General ledger parameters for cross-company affects Indian entities if customers change the delimiter in a US entity. Because the Global Tax Engine (GTE) hierarchy can't be updated in the USMF legal entity, an error occurs.

### TDS and foreign vendors

When a customer sets up default exchange rates and TDS exchange rates, the TDS amount is calculated on an updated exchange rate instead of the TDS exchange rate that is defined in the setup. The upcoming release will fix this issue.

### Different tax information for order lines and charges

When a purchase order is created that has item details and quantity information, the tax information for the purchase is included on the order line. If you add charges and validate the tax information, details of the company tax are shown instead of the warehouse tax information. After this release, purchase order charges, sales order charges, and order lines will have the same tax information.

### Accounting currency and reporting currency issues on project invoice proposals

When you create a project contract in a foreign currency and then create a project invoice proposal that has a different invoice date, a balance issue occurs for the posting, accounting, and reporting currencies. Additionally, there are issues that are related to multiple funding sources for a fee journal and tax rates on credit notes.

### Port ID information on shipping bill and BOE header

Currently, the **Port ID** field is located in the **Export incentive schemes** section on the **BOE** header of the **Shipping bill** page. Because incentive schemes are no longer supported in the application, the **Port ID** field and product group fields should be removed from the **Export incentive scheme** section. You should be able to select the port ID for import and export transactions without having to enable the other functionality. Additionally, because port ID information is provided at the level of the shipping bill line, the information should be moved from the line level to the level of the **BOE** header and **Shipping Bill** header. In that way, all the lines on a bill of exchange (BOE) and a shipping bill will have the same port ID information.