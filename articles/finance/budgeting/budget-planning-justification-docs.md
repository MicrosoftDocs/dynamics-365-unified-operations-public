---
title: Budget planning justification documents
description: Justification documents provide a narrative for those requesting a budget to explain why a specific budget is necessary.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/20/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form: BudgetPlanJustificationTemplate
ms.dyn365.ops.version: Version 1611
ms.assetid: 52576fad-32b9-48f2-8197-c11ec313fc29
---

# Budget planning justification documents

[!INCLUDE [banner](../includes/banner.md)]

Justification documents provide a narrative for those requesting a budget to explain why a specific budget is necessary.

The budget manager creates a budget plan template in Microsoft Word and assigns it to the current budget planning process. Budget owners can then open the template and have data automatically populated in Word based on their budget request. They can then add more text or data before saving and attaching their personalized justification document to their budget plan.

## Set up Microsoft Dynamics Office Add-in for Microsoft Word

1. Open a new Microsoft Word document.
2. On the ribbon, select **Insert**, and then select **Store**.
3. Search for Microsoft Dynamics Office Add-in and select **Add**.
4. In Word, in the right pane, select **Add server information**.
5. Type or paste the server URL and select **OK**.

### Define the Justification template in Microsoft Word

1. Select **Design** in the Microsoft Dynamics Office Add-in after you sign in.
2. For header information, use the **Add fields** button.
3. Select the entity data source of BudgetPlanJustification, and select **Next**. **Note:** This entity is required for any justification document. Other entities can be used but the upload back to Microsoft Dynamics 365 Finance fails if you don't include this entity.
4. Add the BudgetPlanName, BudgetPlanPreparer, ResponsibilityCenter, and DocumentNumber labels and values in the Word document. **Note:** You can use your own custom labels, rather than the standard labels, if needed.
5. Select **Done** to complete the header section.
6. For line level detail of budget plan amounts, select **Add table**.
7. Again, select the entity data source of BudgetPlanJustification, and select **Next**.
8. Add fields for EffectiveDate, ScenarioName, AccountDisplayValue, and AccountingCurrencyExpenseAmount. **Note:** If comments are available to add within individual budget plan lines, add those comments to the table.
9. Add any additional instructions to provide to the end user, and perform any necessary formatting or styling to the document.
10. Save the document to your local computer and close the file before continuing.

### Set up the budget planning process to use the justification template

1. Go to **Budgeting** &gt; **Setup** &gt; **Budget planning** &gt; **Justification document templates**.
2. Select **New** and browse to your newly created Word document.
3. Enter a template display name and description. Select **OK**.
4. Go to **Budgeting** &gt; **Setup** &gt; **Budget planning** &gt; **Budget planning process**.
5. Select the process where you want to use the justification template, and select **Edit**.
6. In the **Justification document template** field, select the appropriate template and save it.

### Edit and save personalized justification documents

1. Create a new budget plan or open an existing budget plan.
2. In the **Justification** dropdown menu, select **Create new justification**.
3. After filling in the details, select to upload the personalized document from the **Justification** dropdown menu.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
