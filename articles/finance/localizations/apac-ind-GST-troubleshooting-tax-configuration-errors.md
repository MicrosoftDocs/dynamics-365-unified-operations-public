---
# required metadata

title: The tax configuration errors
description:
author: hailxu
manager: beya
ms.date: 02/04/2021
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



# The tax configuration errors

[!include [banner](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/finance/includes/banner.md)]

1. [Details for issue 515068](https://fix.lcs.dynamics.com/Issue/Details?bugId=515068&dbType=3): RCM transaction for GTA vendor does not show as “Y” in RCM col[India GST calculation]     Centralize the tax configuration errorsumn in GSTR2 report

   **Symptom**: RCM transactions is posted for a vendor marked as GTA and in tax document the transaction is having Reverse charge percentage updated as 100% then in the GSTR 2 report > Invoice and Bill of Supply > Is reverse charge applicable field is not updated as Yes

   **Solution**: When creating new posting type for tax payable in tax configuration, make sure set the *Tax* *accounting provided* as "Tax" and *Tax Posting Type* as "Tax Payable".

   [![Direct taxes (tab)](./media/tax-configuration-errors-Picture1.png)](./media/tax-configuration-errors-Picture1.png)

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



[!INCLUDE[footer-include](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/live/articles/includes/footer-banner.md)]