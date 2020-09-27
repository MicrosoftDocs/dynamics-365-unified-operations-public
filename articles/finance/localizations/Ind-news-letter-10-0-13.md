---
# required metadata

title: What's new or changed for India GST Localization in 10.0.13 (September 2020)
description: This topic describes new or changed functionality for APAC India GST features released in Dynamics 365 Finance version 10.0.13.
author: prabhatb
manager: annbe
ms.date: 26/09/2020
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

### E-Invoice under GST :   

- On 1 January 2020, the India government made available e-invoice system for voluntary adoption on a trial basis. Microsoft was monitoring law development and was
  undertaking actions to address new requirements. The last announcement confirmed mandatory use of electronic invoice for all companies with Rs 500-crore 
  turnover from 1 October 2020. 
- Please refer to the below resources to enable Electronic invoicing under GST for India with newly introduced specification v.1.03
 
 **Dynamics 365 Finance**
  The information about the update for Dynamics 365 Finance in KB article:
  (https://support.microsoft.com/en-us/help/4554936) 
  Electronic invoice under GST is now supported in following or later versions of Finance: 
  
  Dynamics 365 Finance version       	App build number 
  10.0.13 	                           10.0.569.10002 
  10.0.12 	                           10.0.507.20005 
  10.0.11 	                           10.0.464.30031 

**Dynamics AX 2012 R3** 
 The information about the update for AX2012 R3 in KB article: 
 (https://support.microsoft.com/help/4578809) 
  RL to download the package:
 (https://download.microsoft.com/download/1/a/2/1a2b209f-6b27-49f8-9e43-4db8fce7ba74/DynamicsAX2012R3-KB4578809.EXE) 
 
 ### TCS on Sales of Goods : 
 
 This feature will  cover the following two key aspects of this feature  :  
 (1) PAN-based accumulation of transaction if multiple customers/vendor have the same PAN number  
 (2) Tax liability of TCS can accrue at the time of receipt of payment 
 As per newly introduced section 206C (1H) TCS should be collected at the time of receipt of payment from a customer given this interim accounting option of
 posting is  introduced for this feature. Where TCS amount will be posted to the interim account and added to invoice value at the time of issuance of the invoice, 
 the liability of TCS will be recorded in the books at the time of receipt of payment. Another important aspect of this feature is that if multiple customers
 have the same PAN  number than accumulate transaction value will be taken to compare with the threshold limit to determine the eligible amount of transaction 
 for TCS deduction.  
 
 **Dynamics 365 Finance**
  
  Please find information about the update for Dynamics 365 Finance in KB article: (https://support.microsoft.com/en-us/help/4578799)

  Dynamics 365 Finance version         App build number  
  10.0.13                               10.0.569.10002 
  10.0.12                               10.0.507.20004 
  (Customer already on 10.0.12 need to upgrade on latest build)  
  
  **Dynamics AX 2012 R3** 
  
  Please find information about the update for AX2012 R3 in KB article: 
  (https://support.microsoft.com/en-us/help/4574595) 
  URL to download the package:
  (https://download.microsoft.com/download/1/7/b/17b20afb-bc1a-4a2a-b385-5ccaa5f8e13c/DynamicsAX2012R3-KB4576331.EXE)  
  LCS issue search:
  (https://fix.lcs.dynamics.com/Issue/Details?bugId=3982561) 
  Prerequisite  (AX2012R3) :  
  User need to install KB 4528707 before installing TCS feature  
  (https://download.microsoft.com/download/f/e/6/fe65747f-891f-4d11-b45c-65b2b4cea05a/DynamicsAX2012R3-KB4528707.EXE) 

  ### Credit/Debit note against an export order  : 
  
  This feature will  cover the following key aspects:  
  - Credit/Debit note against the export invoice for which shipping bill has already been posted. 
  - Credit/Debit note can be posted with the option “With the payment of tax” – Yes/No  
  - Shipping bill number and shipping bill date will update automatically if credit note posted after posting of shipping bill  

  Currently, the user is not allowed to post credit note/Debit note against posted export Invoice. With the release of this feature, the user will be
  allowed to post credit  note against export order similar to the normal sales order.  
  As per proposed new GSTR return, ANX-1 report user need to submit information related to  Credit and Debit note issued against Export order.  
 
  **Dynamics 365 Finance** 
  
  Please find information about the update for Dynamics 365 Finance in KB article:
  (https://support.microsoft.com/en-us/help/4561923) 
  TCS on sale of goods is now supported in following or later versions of Finance: 
  Dynamics 365 Finance version           App build number    
   10.0.13                                 10.0.569.10002 
   10.0.12                                 10.0.507.20004 

 **Dynamics AX 2012 R3** 
  Please find information about the update for AX2012 R3 in KB article:
  (https://support.microsoft.com/en-us/help/4579851) 
  URL to download the package:
  (https://fix.lcs.dynamics.com/Issue/Details?bugId=3982391) 

  ### New GST Return offline tool (Trial Version Proto-type) for India  
  
  In the proposed system of new GST Return filing, a normal taxpayer would have to file FORM GST RET-1 (Normal) or FORM GST RET-2 (Sahaj)
  or FORM GST RET-3 (Sugam), on either   monthly (only GST RET-1) or quarterly basis. Annexure of Supplies (GST ANX-1) and Annexure of Inward 
  Supplies (GST ANX-2) will be filed as part of these returns. 
  GST ANX-2 will contain details of inward supplies auto-populated mainly from the suppliers’ GST ANX-1.  
  The taxpayer will be required to take action on details of inward supplies contained in Form GST ANX-2, by accepting or rejecting the entries. 
  The taxpayer can also keep the documents pending by marking the documents accordingly. Based on details uploaded in GST ANX-1 and the actions taken 
  in GST ANX-2, by the taxpayer, the relevant fields of their Form GST RET-1 will be auto-drafted. Taxpayers can now view its details, enter details 
  in the relevant column, save it and download it in pdf format. 
  
  GSTN has released a trial version of the New Returns Offline Tool of Form GST ANX-1, Form GST ANX-2 (with Matching Tool built in it) and a template
  for Purchase Register,  which can be used to import data of purchase register for matching with ANX-2. 
  Microsoft is releasing the new return offline tool GST ANX-1 and Purchase Register format to enable a user to do testing of various business 
  scenarios and provide feedback for improvement.  

**Dynamics 365 Finance** 

  Please find information about the update for Dynamics 365 Finance in KB article:
  (https://support.microsoft.com/en-us/help/4579850) 
  New offline tool for ANX-1 and Purchase Register is now supported in following or later versions of Finance: 

  Dynamics 365 Finance version           App build number   
  10.0.13                                10.0.569.10002 
  Make sure your application import one of the required Tax configuration versions  

**Tax configuration name 	Version** 

 Taxable Document. Version.82  
 Taxable Document (India).version.82.155 
 Tax (India GST). version.82.155.300 

**Dynamics AX 2012 R3** 

 Please find information about the update for AX2012 R3 in KB article:
 https://support.microsoft.com/en-us/help/4552119 
 URL to download the package:  
 https://fix.lcs.dynamics.com/Issue/Details?bugId=3981046 
  
 Import one of the required Tax configuration versions  
 Import below tax configuration version  

**Tax configuration name 	Version** 
 Taxable Document. Version.64 
 Taxable Document (India). version.64.119 
 Tax (India GST). version.	64.119.226 
 (Calculated the IGST tax when with IGST payment is Yes on SEZ/DE/Export order) 
