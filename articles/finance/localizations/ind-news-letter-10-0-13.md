---
# required metadata

title: What's new or changed for the Indian GST localization in 10.0.13 (September 2020)
description: This article describes new or changed functionality that was released in Microsoft Dynamics 365 Finance version 10.0.13 for the APAC India Goods and Services Tax (GST) features.
author: prabhatb
ms.date: 10/08/2020
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
ms.dyn365.ops.version: 10.0.13

---

# What's new or changed for the Indian GST localization in 10.0.13 (September 2020)

[!include [banner](../includes/banner.md)]

This article provides a summary of the new features and critical bug fixes that were released in Microsoft Dynamics 365 Finance version 10.0.13 for the Indian Goods and Services Tax (GST) localization.

## New features

### Electronic invoice under GST

On January 1, 2020, the Indian government made the electronic invoice (e-invoice) system available for voluntary adoption on a trial basis. Microsoft monitored the development of the law and took action to address the new requirements. The last announcement confirmed the mandatory use of e-invoices for all companies that have turnover of Rs 500 crore starting October 1, 2020. Use the following information to turn on the Electronic invoice under GST feature for India together with the newly introduced specification v.1.03.

#### Dynamics 365 Finance

- For information about the update for Finance, see the following Knowledge Base (KB) article: [A country/region-specific hotfix to support Electronic invoice under GST for India in Microsoft Dynamics 365 Finance](https://support.microsoft.com/help/4554936).
- The Electronic invoice under GST feature is supported in the following versions of Finance and later versions.

    | Finance version | App build number |
    |-----------------|------------------|
    | 10.0.13         | 10.0.569.10002   |
    | 10.0.12         | 10.0.507.20005   |
    | 10.0.11         | 10.0.464.30031   |

#### Dynamics AX 2012 R3

- For information about the update for Dynamics AX 2012 R3, see the following KB article: [A country/region-specific hotfix to support Electronic invoice under GST for India in Microsoft Dynamics AX 2012 R3](https://support.microsoft.com/help/4578809).
- [Download the package](https://download.microsoft.com/download/1/a/2/1a2b209f-6b27-49f8-9e43-4db8fce7ba74/DynamicsAX2012R3-KB4578809.EXE).

### TCS on sales of goods

This feature covers the accumulation of transactions that is based on permanent account numbers (PANs) if multiple customers and vendors have the same PAN.

Tax liability of TCS can accrue when payment is received. Per the new section, 206C (1H), because of the interim accounting option for posting that is introduced in this feature, TCS should be collected when payment is received from a customer. The TCS amount will be posted to the interim account and added to the invoice when the invoice is issued. The liability of TCS will be recorded when the payment is received. Additionally, if multiple customers have the same PAN, an accumulated transaction value is compared with the threshold limit to determine the eligible number of transactions for TCS deduction.

#### Dynamics 365 Finance

- For information about the update for Finance, see the following KB article: ["Tax collection at Source" (TCS) on sale of goods for India in Dynamics 365](https://support.microsoft.com/help/4578799).
- The TCS on sales of goods feature is supported in the following versions of Finance and later versions.

    | Finance version | App build number |
    |-----------------|------------------|
    | 10.0.13         | 10.0.569.10002   |
    | 10.0.12         | 10.0.507.20004   |

- Customers who are already using version 10.0.12 must upgrade to the latest build.

#### Dynamics AX 2012 R3

- For information about the update for AX 2012 R3, see the following KB article: ["Tax collection at Source" (TCS) on sale of goods for India in Dynamics AX2012R3](https://support.microsoft.com/help/4574595).
- [Download the package](https://download.microsoft.com/download/1/7/b/17b20afb-bc1a-4a2a-b385-5ccaa5f8e13c/DynamicsAX2012R3-KB4576331.EXE).
- Use [Issue search in Microsoft Dynamics Lifecycle Services (LCS)](https://fix.lcs.dynamics.com/Issue/Details?bugId=3982561).
- Prerequisite for AX 2012 R3: Install KB 4528707 before you install the [TCS feature](https://download.microsoft.com/download/f/e/6/fe65747f-891f-4d11-b45c-65b2b4cea05a/DynamicsAX2012R3-KB4528707.EXE).

### Credit/Debit note against an export order

This feature covers the following key aspects:

- A credit or debit note is issued against an export invoice that a shipping bill is already posted for.
- When the credit or debit note is posted, the **With the payment of tax** option can be set to **Yes** or **No**.
- The shipping bill number and shipping bill date are automatically updated if the credit note is posted after the shipping bill is posted.

Currently, you can't post credit or debit notes against a posted export invoice. This feature lets you post credit notes against an export order, similarly to the way that you post credit notes against regular sales orders. Per the proposed new GST return, users of the ANX-1 report must submit information that is related to credit and debit notes that were issued against an export order.

#### Dynamics 365 Finance

- For information about the update for Finance, see the following KB article: [Credit/Debit note against export order for India in Dynamics 365](https://support.microsoft.com/help/4561923).
- The Credit/Debit note against an export order feature is supported in following versions of Finance and later versions.

    | Finance version | App build number |
    |-----------------|------------------|
    | 10.0.13         | 10.0.569.10002   |
    | 10.0.12         | 10.0.507.20004   |

#### Dynamics AX 2012 R3

- For information about the update for AX 2012 R3, see the following KB article: [Credit/Debit note against Export order for India in Dynamics AX2012 R3](https://support.microsoft.com/help/4579851).
- [Download the package](https://fix.lcs.dynamics.com/Issue/Details?bugId=3982391).

### New GST Return offline tool (trial version prototype) for India

In the proposed system for new GST return filing, the taxpayer will have to file Form GST RET-1 (Normal), Form GST RET-2 (Sahaj), or Form GST RET-3 (Sugam). These forms will be filed either monthly (in the case of GST RET-1 only) or quarterly.

Annexure of Supplies (GST ANX-1) and Annexure of Inward Supplies (GST ANX-2) will be filed as part of these returns. GST ANX-2 contains details of inward supplies. These details are automatically filled in, mainly from the suppliers' GST ANX-1. The taxpayer must either accept or reject the entry of details about inward supplies in GST ANX-2. The taxpayer can also keep the documents in a pending state by marking them accordingly. Based on the details that are uploaded in GST ANX-1 and the actions that the taxpayer takes in GST ANX-2, the relevant fields of Form GST RET-1 will be automatically drafted. The taxpayer can view the details of this form, enter details in the relevant column, save the form, and download it in PDF format.

The Goods and Service Tax Network (GSTN) has released a trial version of the new Returns Offline Tool of Form GST ANX-1, Form GST ANX-2 (with the Matching Tool built into it), and a template for Purchase Register, which can be used to import Purchase Register data for matching with ANX-2. Microsoft is releasing the new GST Return offline tool GST ANX-1 and Purchase Register format so that users can test various business scenarios and provide feedback about improvements.

#### Dynamics 365 Finance

- For information about the update for Finance, see the following KB article: [New GSTR Offline Tool (ANX-1 and Purchase Register) for India in Dynamics 365](https://support.microsoft.com/help/4579850).
- The new offline tool for ANX-1 and the Purchase Register is supported in the following versions of Finance and later versions.

    | Finance version | App build number |
    |-----------------|------------------|
    | 10.0.13         | 10.0.569.10002   |

- Make sure that your application imports follow tax configuration versions.

   The new configuration version will allow you to post Export/SEZ/Deemed export transactions.

    **Tax configuration name and version:**

    - Taxable Document. Version.82
    - Taxable Document (India).version.82.155
    - Tax (India GST). version.82.155.300
    
    If you want to de-couple GST posting from inventory posting and add Interim transit for stock transfer transaction posting, download the following configuration file"

    - Tax (India GST).version.82.155.301


#### Dynamics AX 2012 R3 

- For information about the update for AX 2012 R3, see the following KB article: [New GSTR Offline Tool (ANX-1 and Purchase Register) for India in Dynamics AX2012R3](https://support.microsoft.com/help/4552119).
- [Download the package](https://fix.lcs.dynamics.com/Issue/Details?bugId=3981046).

- Import the following tax configuration version:

    - Taxable Document. Version.64
    - Taxable Document (India). version.64.119
    - Tax (India GST). version. 64.119.226
     
 These configurations provide the following options:
    
  - Post export order 
   
       - With payment of tax option 
       - Without payment of tax option 
    
  - Post SEZ (Special economic Zone) order 
        
       - With payment of tax option 
       - Without payment of tax option 
            
  - Post DE (Deemed Export) Order 
        
       - With payment of tax option 
       - Without payment of tax option 
    
### New GST return format

The GSTR-1 and GSTR-2 return formats have been updated based on the new format that was updated by one of the GST Suvidha Providers (GSPs). The following new information has been added in the existing reports:

- **GSTR-1 return:** The following additional columns have been added:

    - **Sales invoice and bill of supply file:**

        - Differential % of tax rate
        - Supply covered under sec. 7 of IGST Act
        - Would you claim refund?
        - Return filing month
        - Return filing quarter

    - **Sales credit and debit note file:**

        - Applicable % of tax rate
        - Supply covered under sec. 7 of IGST Act
        - Would you claim refund?
        - Type of export
        - Shipping port code - Export
        - Shipping bill number - Export
        - Shipping bill date - Export
        - Return filing month
        - Return filing quarter
        - GSTIN of E-commerce marketplace
        
- **GSTR-2 return:** The following additional columns have been added:

    - **Purchase invoice and bill of supply file:**

        - Supply covered under section 7 of IGST Act
        - Would you claim refund?
        - Return filing month
        - Return filing quarter

    - **Purchase credit and debit note file:**

        - Supply covered under sec. 7 of IGST Act
        - Would you claim refund?
        - Type of import
        - Bill of entry port code
        - Bill of entry number
        - Bill of entry date
        - Bill of entry value
        - Return filing month
        - Return filing quarter

#### Dynamics 365 Finance

- For information about the update for Finance, see the following KB article: [New GSTR -1 and GSTR-2 return format for India in Dynamics 365](https://support.microsoft.com/help/4578803).
- New GSTR-1 and GSTR-2 return formats are supported in following versions of Finance and later versions.

    | Finance version | App build number |
    |-----------------|------------------|
    | 10.0.13         | 10.0.569.10002   |

- Make sure that your application imports the following tax configuration versions.

    **Tax configuration name and version:**

    - Taxable Document. Version.82
    - Taxable Document (India). version.82.155
    - Tax (India GST). version.82.155.300

#### Dynamics AX 2012 R3

- For information about the update for AX 2012 R3, see the following KB article: [New GSTR -1 and GSTR-2 return format for India in AX2012R3](https://support.microsoft.com/help/4577212).
- [Download the package](https://fix.lcs.dynamics.com/Issue/Details?bugId=3982391).
- Import one of the required tax configuration versions.

    (In these tax configuration versions, the **Applicable Percentage of tax** rate has been added on Central GST \[CGST\], State GST \[SGST\], Integrated GST \[IGST\], and CESS.)

- Import the following tax configuration version:

    - Taxable Document. Version.64
    - Taxable Document (India). version.64.119
    - Tax (India GST). version.64.119.226
    - (Calculated the IGST tax when with IGST payment is Yes on SEZ/DE/Export order)

## Critical fixes

- For intercompany transactions, when one company posts a sales order, a purchase order is automatically generated in the other company. However, the location of the purchasing company in the tax information isn't entered correctly in the purchase order that is automatically generated.
- When a withholding tax transaction is posted in a currency that differs from the currency that was used at the time of the withholding tax settlement to the authority, an imbalance error occurs.
- The withholding tax (TCS) isn't calculated for intercompany purchase return orders, even after the line details are updated.
- When you import data by using the **Ledger journal line transaction tax information** data entity, the following error occurs: "Results. Matching record with key 'Registration Number': 29AGNPB4831B1Z1 for the data source 'GSTIN' does not exist."
- Vendor tax information is imported through the **Data entity** page. The system allows the user to select more than one set of primary tax information details for vendor tax information.
- When a customer tries to import a purchase order, the value of IGST isn't shown on the **Totals** tab after the purchase order totals are calculated and the purchase order is invoiced.
- The **Transaction type** field should not be available on the **Sales quotation** page. You can manually add and update the transaction type on the **Sales quotation** page. If it's updated to **Value** instead of **None** or **Expense**, the customer tax information will be invisible.
- The system currently allows the Harmonized System of Nomenclature (HSN) code or Service Accounting Code (SAC) to be deleted from the master setup page, even if posted and opened transactions exist.
- When foreign vendor payments are posted, the withholding tax on non-residence is applied. If the user changes the currency rates on the transaction and then posts the transaction, the voucher imbalance included as part of the logic to calculate exchange gain is not executing. After this fix, the system will calculate the difference in the **Exchange gain and loss** account.
- If a user creates an import purchase order, and then adjusts the customs duty in **Tax document** page, when the bill of entry is created, those adjustments are not reflected during invoicing.
- The **Product receipt** page includes a column for the BOE number, but no BOE number is shown on the page.
- When a purchase order is placed and the order has a procurement category, the load on inventory tax amount is posted to the purchase expenditure for an expense account instead of the  Cost of project account or Fixed asset account. This issue occurs in project and fixed asset scenarios.
- The tax amount isn't shown correctly on the **Purchase requisition** page. The **Total** form shows the tax amount of only the first line, not all the lines.
- When the user is posting a general journal with a debit project account and a (offset) credit vendor account, and the marking tax is **Load on inventory**, 
  after posting checks the project statement, the tax amount isn't included in the project cost value.
- GSTR: Customer can't select a financial year while they are running the Purchase Register reports.
- When you post a tax journal that has a combination of a ledger account and a customer account, an error occurs.

## Upcoming critical fixes in version 10.0.14

- When you manually adjust and apply the tax amount of Indian Tax Deducted at Source (TDS) withholding tax in a vendor invoice journal, you might have noticed that the adjustment is lost (reset) if you change the invoice number in the journal before you post.
- The GST amount isn't shown correctly. The **GST amount** value is shown in a foreign currency, whereas the **Subtotal** and **Total amount** values are shown in Indian rupees (INR). The GST amount should be converted and added to the subtotal, so that the correct total amount is shown.
- Customer has recently enabled the India localization, India GST feature on their India .Entity 104.
- After enabling the India localization, the value is not displayed for the billing rule type **Milestone** on the **Project contract** page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]