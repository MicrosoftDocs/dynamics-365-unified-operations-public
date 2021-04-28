---
# required metadata

title: Incorrect tax amount after calculation
description: This topic provides troubleshooting information that helps you resolve the issue when the calculated tax amount is incorrect.
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



# Incorrect tax amount after calculation

[!include [banner](../includes/banner.md)]
 
Complete the sections in this topic if the calculated tax on a business document is incorrect. In this topic, a purchase order is used as an example.

## Verify the tax rate is correct

1. Go to **Tax** > **Setup** > **Tax configuration** > **Tax setup**.
2. On the **Tax setup** page, select the company you are working in, and then select **Setup**.

   [![Tax setup page](./media/tax-amount-wrong-Picture1.png)](./media/tax-amount-wrong-Picture1.png)

3. On the tax document, go to the **Header** > **Lines** > **GST** > **CGST** > **Rate** to find the corresponding rate node.
4. Based on the conditions, see if your transaction matches the correct rate. You can view transaction details on the Tax document by selecting **View tax input**. For more information, see [Tax isn't calculated](apac-ind-GST-troubleshooting-tax-not-calculated.md)


## Check the tax base

Complete the following steps to verify that the tax base is correct.

1. Check that the number of tax document lines matches the actual number of transaction lines. If the number of lines don't match, see [Tax isn't calculated](apac-ind-GST-troubleshooting-tax-not-calculated.md) to check if some lines don't match the condition defined in the tax configuration.
2. Check that the tax information is correctly set for all of the lines. Some settings might impact the calculation of the tax base. These settings include:

   - **Exempt**: GST will not be calculated.
   - **Prices include sales tax**: GST will be included in the price.
   - **Non-GST**: Tax with tax type other than GST (Such as VAT) will be calculated.

      [![Tax information settings](./media/tax-amount-wrong-Picture3.png)](./media/tax-amount-wrong-Picture3.png)

3. Check that the information on the **Price and discount** tab meets your requirements.

   [![Price and discount tab](./media/tax-amount-wrong-Picture4.png)](./media/tax-amount-wrong-Picture4.png)

## Check that the tax rate is correct

Open the tax document, and on the **Total** FastTab, compare the values in the **Total of Tax Amount** and **Adjusted total of Tax Amount** fields. If they are different, the adjustment was applied.

   [![Tax document page, Totals FastTab](./media/tax-amount-wrong-Picture5.png)](./media/tax-amount-wrong-Picture5.png)

## Determine whether customization exists

If you've completed the steps in the previous sections but have found no issue, determine whether customization exists. If no customization exists, create a Microsoft service request for further support.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]


