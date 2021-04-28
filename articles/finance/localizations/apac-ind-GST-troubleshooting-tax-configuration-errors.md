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

When you are configuring the CGST_TDS, you might receive a model mapping error that says no model mapping exists for the **TDS TCS Registration Number** data model. To resolve this issue, see [While configuring CGST_TDS facing model mapping error](https://fix.lcs.dynamics.com/Issue/Details?bugId=527080&dbType=3).

   [![Model mapping error](./media/tax-configuration-errors-Picture2.png)](./media/tax-configuration-errors-Picture2.png)

 If you receive similar errors, such as "No model mapping exists for the 'xxx' data model", complete the following steps.

1. Go to **Workspaces** > **Electronic reporting** > **Tax configurations**.
2. Select **Taxable Document**, select **Taxable Document (India)**, and then select **Designer** to open the designer for the **Taxable Document (India)**.
3. Go to the **Taxable Document** node, and then expand **Header** > **Lines** > **Tax Identification Number**, and check if the reference model is selected.

      [![Taxable Document (India) page, Tax Identification Number field](./media/tax-configuration-errors-Picture3.png)](./media/tax-configuration-errors-Picture3.png)

4. Select **Map model to datasource**, and check if the model mapping for the reference model exists.

      [![Taxable Document (India) page, Map model to data source button](./media/tax-configuration-errors-Picture4.png)](./media/tax-configuration-errors-Picture4.png)

5. Define a model mapping for the tax identification number that refers to the model mapping of the **GST registration number**. For more information, see [Extend tax engine configurations](extend-tax-engine-configurations.md#complete-data-mapping-for-the-extended-taxable-document)..

## Error occurs when calculating GST

When you use division in a formula, pay close attention when the divisor is equal to zero as it might cause an error when calculating GST. A pop-up execption with error message similar to the following might occur, *Attempted to divide by zero. Please check the formula of mapping field "xxx" for taxable document mapping "xxx" in active taxable document, it encounters an unhandled exception.* 

In this section, **Net price = @.'Net Amount'/@.Quantity**, which is defined on the model mapping **PurchParmTable** is used as an example.

1. Go to **Workspaces** > **Electronic reporting** > **Tax configurations**.
2. Select the **Taxable Document** > **Taxable Document (India)**, and the select **Designer**.
3. On the **Taxable Document (India)** page, select **Map model to datasource**. 

      [![Taxable Document (India) page, Map model to data source](./media/tax-configuration-errors-Picture5.png)](./media/tax-configuration-errors-Picture5.png)

4. Find and select the model mapping, **Bundler.PurchOrderParm**, and then select **Designer**.
5. In the **Data model** section, expand **Header** > **Lines** and find **Net price**.

      [![Data model, Net price](./media/tax-configuration-errors-Picture6.png)](./media/tax-configuration-errors-Picture6.png)

   You can see that the formula of the **Net price** field is **@.'Net Amount'/@.Quantity**.
   
7. Confirm with business department if a quantity of zero is allowed. If it's not, correct the transaction and perform the operation again. If it's allowed, correct the formula to the format like **IF(@.Quantity = 0, @.'Net Amount', @.'Net Amount'/@.Quantity)**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
