---
# required metadata

title: Tax configuration errors
description: This topic privdes troubleshooting iformation that can help with tax configuration errors. 
author: qire
ms.date: 04/28/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.1
---

# Tax configuration errors

[!include [banner](../includes/banner.md)]

## RCM transactions

When RCM transactions are posted for a vendor marked as a Goods transport agency (GTA), and the transaction is marked as having a reverse charge percentage updated as 100% in the tax document, then the **Is reverse charge applicable** field isn't updated to **Yes** in the GSTR 2 report.

To resolve this issue, when you create a new posting type for a tax payable in a tax configuration, select **Tax** in the **Tax accounting provider** field and **Tax payable** in the **Tax Posting Type** field.

   [![Tax accounting provider and Tax posting type fields](./media/tax-configuration-errors-Picture1.png)](./media/tax-configuration-errors-Picture1.png)
   
For more information, see [RCM transaction for GTA vendor does not show as “Y” in RCM column in GSTR2 report](https://fix.lcs.dynamics.com/Issue/Details?bugId=515068&dbType=3).

## Model mapping error when configuring configuring CGST_TDS

2. [Details for issue 527080](https://fix.lcs.dynamics.com/Issue/Details?bugId=527080&dbType=3): IN- While configuring CGST_TDS facing model mapping error. No model mapping exists for the 'TDS TCS Registration Number' data model.

   For the specified issue, the solution has been provided. For other issue like "No model mapping exists for the 'xxx' data model", please refer to the trouble shooting guide below.

   **Symptom**: While configuring tax setup facing model mapping error. “No model mapping exists for the 'xxx' data model".

   [![Direct taxes (tab)](./media/tax-configuration-errors-Picture2.png)](./media/tax-configuration-errors-Picture2.png)

   1. Go to *Workspaces -> Electronic reporting -> Tax configurations.*

   2. Navigate to "*Taxable Document -> Taxable Document (India)"* and Click *Designer* button to open the designer of *Taxable Document (India).*

   3. Navigate to the node "*Taxable Document > Header > Lines >* **Tax Identification Number**", check whether the reference model is selected.

      [![Direct taxes (tab)](./media/tax-configuration-errors-Picture3.png)](./media/tax-configuration-errors-Picture3.png)

   4. Click *Map model to datasource*, check if exists model mapping for the Reference model.

      [![Direct taxes (tab)](./media/tax-configuration-errors-Picture4.png)](./media/tax-configuration-errors-Picture4.png)

   5. Following [Extend tax engine configurations - Finance |Dynamics 365 | Microsoft Docs ](https://docs.microsoft.com/en-us/dynamics365/finance/general-ledger/extend-tax-engine-configurations#complete-data-mapping-for-the-extended-taxable-document)to define a model mapping for **Tax Identification Number** refer to the model mapping of **GST Registration Number**.

3. When involving division in formula, the case that the divisor equals to 0     should be considered carefully.

   Here

   **Symptom:** When calculating GST, pop-up a execption with error message like *Attempted to divide by zero. Please check the formula of mapping field "xxx" for taxable document mapping "xxx" in active taxable document, it encounters an unhandled exception.* 

   **Trouble shooting guide**:  

   **Here take "Net price = @.'Net Amount'/@.Quantity" that defined on model mapping "PurchParmTable" as an example.**

   1. Go to *Workspaces -> Electronic reporting -> Tax configurations.*

   2. Navigate to "*Taxable     Document -> Taxable Document (India)"* and Click *Designer* button to open the designer of *Taxable Document (India).*

   3. Click *Map model to datasource*. 

      [![Direct taxes (tab)](./media/tax-configuration-errors-Picture5.png)](./media/tax-configuration-errors-Picture5.png)

   4. Find and select the model mapping with name *Bundler.PurchOrderParm*, and click *Designer*.

   5. In *DATA MODEL* section, expand *Header/Lines* and find the field *Net price.*

      [![Direct taxes (tab)](./media/tax-configuration-errors-Picture6.png)](./media/tax-configuration-errors-Picture6.png)

   6. Then we can see the formula of the field Net price is **@.'Net Amount'/@.Quantity**. 

   7. Please confirm with business department if the Quantity is allowed to be zero. If no, please correct the transaction and perform the operation again. If yes, please correct the formula to the format like **IF(@.Quantity = 0, @.'Net Amount', @.'Net Amount'/@.Quantity)**


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
