---
# required metadata

title: What's new or changed for India GST Localization in 10.0.13 (September 2020)
description: This topic describes new or changed functionality for APAC India GST features released in Dynamics 365 Finance version 10.0.13.
author: prabhatb
manager: annbe
ms.date: 10/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.13

---

# What's new or changed for India GST Localization in 10.0.13 (September 2020)

[!include [banner](../includes/banner.md)]

This topic includes a summary of the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.13 for India GST localization. 

## New features

### E-Invoice under GST  
On 1 January 2020, the India government made the e-invoice system available for voluntary adoption on a trial basis. Microsoft monitored the law development and undertook actions to address the new requirements. The last announcement confirmed mandatory use of electronic invoice for all companies with Rs 500-crore turnover from 1 October 2020.  Refer to the following resources to enable Electronic invoicing under GST for India with newly introduced specification v.1.03.
 
**Dynamics 365 Finance**
Information about the Finance update is in this [KB article](https://support.microsoft.com/en-us/help/4554936) 

Electronic invoice under GST is now supported in the following, or later, versions of Finance: 
  
| Dynamics 365   Finance version | App build number |
|--------------------------------|------------------|
| 10.0.13                        | 10.0.569.10002   |
| 10.0.12                        | 10.0.507.20005   |
| 10.0.11                        | 10.0.464.30031   |

**Dynamics AX 2012 R3** 
- Information about the AX2012 R3 update is in this [KB article](https://support.microsoft.com/help/4578809) 
- [Download the package](https://download.microsoft.com/download/1/a/2/1a2b209f-6b27-49f8-9e43-4db8fce7ba74/DynamicsAX2012R3-KB4578809.EXE) 
 
### TCS on sales of goods 
 
 This feature covers the following two key aspects:  
 
- PAN-based accumulation of transactions if multiple customers and vendor have the same PAN number.  
- Tax liability of TCS can accrue at the time payment is received. Per the new section,206C (1H), due to this interim acounting option of posting which is introduced with this feature, TCS should be collected at the time payment is received from a customer. The TCS amount will be posted to the interim account and added to invoice when the invoice is issued. The liability of TCS will be recorded when the payment is received. Additionally, if multiple customers have the same PAN number, an accumulated transaction value is compared with the threshold limit to determine the eligible amount of transactions for TCS deduction.  
 
 **Dynamics 365 Finance**
  
Information about the Dynamics 365 Finance update is in this [KB article](https://support.microsoft.com/en-us/help/4578799).

| Dynamics 365   Finance version | App build number |
|--------------------------------|------------------|
| 10.0.13                        | 10.0.569.10002   |
| 10.0.12                        | 10.0.507.20004   |

Customers already on 10.0.12 need to upgrade to the latest build. 
  
  **Dynamics AX 2012 R3** 
  
- Information about the update for AX2012 R3 is in this [KB article](https://support.microsoft.com/en-us/help/4574595) 
- [Download the package](https://download.microsoft.com/download/1/7/b/17b20afb-bc1a-4a2a-b385-5ccaa5f8e13c/DynamicsAX2012R3-KB4576331.EXE)  
- [LCS issue search](https://fix.lcs.dynamics.com/Issue/Details?bugId=3982561) 
- Prerequisite (AX2012R3): Install KB 4528707 before installing [TCS feature](https://download.microsoft.com/download/f/e/6/fe65747f-891f-4d11-b45c-65b2b4cea05a/DynamicsAX2012R3-KB4528707.EXE) 

  ### Credit/Debit note against an export order 
  This feature covers the following key aspects:  
  
  - Credit/Debit note against the export invoice for which the shipping bill is already posted. 
  - Credit/Debit note can be posted with the option **With the payment of tax** set to **Yes** or **No**. 
  - Shipping bill number and shipping bill date will update automatically if the credit note is posted after the shipping bill is posted  

Currently, you can't post credit or debit notes against a posted export invoice. With this feature, you can post credit notes against an export order similar to the normal sales order. Per the proposed new GSTR return, the ANX-1 report user needs to submit information related to credit and debit notes issued against an export order.  
 
  **Dynamics 365 Finance** 
  
- Information about the update for Finance is in [KB article](https://support.microsoft.com/en-us/help/4561923) 

TCS on sale of goods is now supported in following or later versions of Finance: 

| Dynamics 365   Finance version | App build number |
|--------------------------------|------------------|
| 10.0.13                        | 10.0.569.10002   |
| 10.0.12                        | 10.0.507.20004   | 
 
**Dynamics AX 2012 R3** 

- Information about the update for AX2012 R3 is in [KB article](https://support.microsoft.com/en-us/help/4579851) 
- [Download package](https://fix.lcs.dynamics.com/Issue/Details?bugId=3982391) 

  ### New GST Return offline tool (Trial Version Proto-type) for India  
  
In the proposed system of new GST Return filing, a taxpayer would have to file FORM GST RET-1 (Normal), FORM GST RET-2 (Sahaj), or FORM GST RET-3 (Sugam). These would be filed on either a monthly (only GST RET-1) or quarterly basis. Annexure of Supplies (GST ANX-1) and Annexure of Inward Supplies (GST ANX-2) will be filed as part of these returns. GST ANX-2 contains details of inward supplies that are auto-populated mainly from the suppliers’ GST ANX-1. The taxpayer is required accept or reject the entry of the details regarding inward supplies contained in Form GST ANX-2. The taxpayer can also keep the documents in a pending state by marking the documents accordingly. Based on the details uploaded in GST ANX-1 and the actions taken in GST ANX-2, by the taxpayer, the relevant fields of Form GST RET-1 will be auto-drafted. Taxpayers can view its details, enter details  in the relevant column, save it, and download it in pdf format. 
  
GSTN has released a trial version of the New Returns Offline Tool of Form GST ANX-1, Form GST ANX-2 (with Matching Tool built in it), and a template for Purchase Register,  which can be used to import data of purchase register for matching with ANX-2. Microsoft is releasing the new return offline tool GST ANX-1 and Purchase Register format to enable a user to do testing of various business scenarios and provide feedback for improvement.  

**Dynamics 365 Finance** 

- Information about the update for Dynamics 365 Finance is in [KB article](https://support.microsoft.com/en-us/help/4579850) 
  
The new offline tool for ANX-1 and the Purchase Register is now supported in the following or later versions of Finance: 

| Dynamics 365   Finance version | App build number |
|--------------------------------|------------------|
| 10.0.13                        | 10.0.569.10002   |

Make sure your application import one of the required Tax configuration versions. 

**Tax configuration name 	Version** 

 - Taxable Document. Version.82  
 - Taxable Document (India).version.82.155 
 - Tax (India GST). version.82.155.300 

**Dynamics AX 2012 R3** 

- Information about the update for AX2012 R3 is in [KB article](https://support.microsoft.com/en-us/help/4552119)
- [Download the package](https://fix.lcs.dynamics.com/Issue/Details?bugId=3981046 )
- Import one of the required Tax configuration versions  
- Import below tax configuration version  

**Tax configuration name 	Version** 

-  Taxable Document. Version.64 
- Taxable Document (India). version.64.119 
- Tax (India GST). version.	64.119.226 
- (Calculated the IGST tax when with IGST payment is Yes on SEZ/DE/Export order) 
 
### New GSTR Return format
With this feature, the GSTR -1 and GSTR-2 Return formats have been updated per new format updated by one of the GSP. The following new information is added in the existing reports:  

- **GSTR-1 Return**: The following additional columns have been added: 

     - **Sales Invoice and Bill of Supply**:  
      | Diffrential % of tax rate | Supply covered under sec.7 of IGST Act | Would you claim refund ?  | Return filling month  | Return filling Quater |

     - **Sales credit Debit note**: 
      | Applicable % of Tax rate | Supply covered under section 7  | Would you claim refund  | Type of export  | Shipping port code-Export  |
      | Shipping Bill number-Export | Shipping Bill date-Export | Return filling month | Return filling Quater  | GSTIN of E-commerce Market place  |

 - **GSTR-2 Return**: The following additional columns have been added: 

     - **Purchase Invoice and Bill of supply**:

     | Supply covered unde section 7 of IGST Act | Would you claim refund? | Return filling month | Return filling Quater |

     - **Purchase Credit and Debit note**:  

     | Supply covered unde section 7 of IGST Act | Would you claim refund? | Type of Import | Bill of entry-port code | Bill of entry No. |
     | Bill of entry Date | Bill of entry Value | Return filling month | Return filling Quater  |

**Dynamics 365 Finance** 
  
- Information about the update for Dynamics 365 Finance is in [KB article](https://support.microsoft.com/en-us/help/4578803) 
- New GSTR-1 and GSTR-2 returns are  now supported in following or later versions of Finance: 
 
| Dynamics 365   Finance version | App build number |
|--------------------------------|------------------|
| 10.0.13                        | 10.0.569.10002   |
  
Make sure your application import one of the required Tax configuration versions  
  
  **Tax configuration name Version** 

  - Taxable Document. Version.82  
  - Taxable Document (India). version.82.155 
  - Tax (India GST). version.82.155.300 

**Dynamics AX 2012 R3** 

- Information about the update for AX2012 R3 is in [KB article](https://support.microsoft.com/en-us/help/4577212) 
- [Download the package](https://fix.lcs.dynamics.com/Issue/Details?bugId=3982391)
- Import one of the required Tax configuration versions  
   (Added 'Applicable Percentage of tax' rate on CGST/SGST/IGST/CESS)  
- Import below tax configuration version: 
   
   **Tax configuration name	Version** 
   
   - Taxable Document. Version.64 
   - Taxable Document (India). version.64.119 
   - Tax (India GST). version.64.119.226 
   - (Calculated the IGST tax when with IGST payment is Yes on SEZ/DE/Export order)  


  ## Critical fixes: 

- In the intercompany transaction, when one company posts a sales order, a purchase order is generated automatically in another company. However, the location of the purchasing company in the tax information is not defaulting correctly in the auto-generated purchase order. 
- When a withholding tax transaction is posted in currency that is different than the currency used at the time of thewithholding tax settlement to the authority, an imbalance error will occur. 
- The withholding tax (TCS) is not calculated for inter-company purchase return orders even after the line details are updated. 
- When you import data using the data entity **Ledger journal line transaction tax information**, the following error occurs: “Results. Matching record with key 'Registration  Number': 29AGNPB4831B1Z1 for the data source 'GSTIN' does not exist”.  
- Vendor tax information is imported through the **Data entity** page. The system allows the user to select more than one primary tax information detail set for vendor tax information.
- When a customer is trying to import a purchase order, the value of IGST tax is not shown on the **Totals** tab after the purchase order totals are calculated and the purchase order is invoiced. 
-	The **Transaction type** field should not be enabled on the **Sales quotation** page. You can manually add and update the transaction type on the **Sales quotation** page. If it is updated to **Value** instead of **None** or **Expense**, the customer tax information will be invisible. 
- The system currently allows the HSN/SAC code to be deleted from the master setup form even if posted and opened transactions exist. 
-	While posting foreign vendor payments, the withholding tax of Non-Residence is applied. If the user changes currency rates on the transaction, a similar exchange rate is not applied for withholding tax calculation. Instead, the exchange rate is taken from the system. Because of this, there is an imbalance in posting and  it is not completed. 
-	The system is not showing the tax-adjusted amount at the time of bill of entry to the tax document form of the **Invoice posting** form. 
-	BOE (Bill of entry) number column is present on the **Product receipt** page but the BOE number is not being displayed on the page. 
-	The load on inventory tax amount is posting to the purchase expenditure for an expense account instead of the Cost of project account/Fixed asset account when a purchase order placed with a procurement category. This happens in Project and Fixed asset scenarios. 
-	The tax amount is not showing correctly on the **Purchase requisition** page. The tax amount of the first line only shows in the **Total** form instead of all the lines.   
-	When a customer is trying to work in a General journal with a project in the account type and a vendor in the offset account with a load on inventory,  after posting, when user checks project statement, the value of project cost is showing without adding the tax amount.  
-	GSTR - Customer can't select a Financial year while running the Purchase register Reports. 
-	When you post a tax journal with the combination of ledger account and customer account, an error message occurs. 
  
  ## Upcoming critical fixes in 10.0.14  
  
- When you manually adjust and apply the tax amount of India TDS withholding tax in a vendor invoice journal, you may have noticed that the adjustment is lost (reset) if you change the Invoice number in the journal before posting.  
-	GST amount is not showing correctly. The **GST amount** shows in a foreign currency whereas the **Subtotal** and **Total amount** fields are showing in INR. The GST amount should be converted and added to the subtotal to display the correct total amount.   
- The **Billing rule details** is empty for existing entries when the localization Tax Extension for India is enabled. 

