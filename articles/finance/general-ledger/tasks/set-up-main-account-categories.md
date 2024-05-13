--- 
title: Set up main account categories
description: Learn how to set up main account categories in Dynamics 365 Finance, including outlines on creating a main account category and link main accounts. 
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 04/18/2024
ms.custom:
ms.reviewer: twheeloc   
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: MainAccountCategory, MainAccountCategoryLink
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up main account categories

[!include [banner](../../includes/banner.md)]

This article explains how to set up main account categories. Main account categories are used for the default reports in financial reporting and in Power BI. Main account categories that are created by default can be renamed but not deleted. Additional account categories can be created and used for reporting and analysis purposes. This article uses the USMF demo company.

When defining the main account category, consider the most detailed grouping level necessary for effective financial reporting, data analysis, and decision-making. Some examples of granular account categories include Cash, Fixed Assets, Short-term Investments, Accounts Receivable, and Accounts Payable.

>[!NOTE] 
>The **Main account type** determines the general classification of an account, such as Balance Sheet, Profit & Loss, Asset, or Liability. In contrast, the **Main account category** provides a more detailed grouping for accounts within these classifications.

## Create a main account category
1. Go to **General Ledger > Chart of accounts > Accounts > Main account categories**.
2. Select **New**.
3. In the **Main account category** field, enter a unique name.
4. In the **Description field**, enter a description for the main account category.
5. In the **Main account type** field, select the main account type that will be linked to the category.

## Link main accounts to account category
1. Click **Link main accounts**.
2. In the list, select the main accounts to assign to the main account category by checking the boxes in the **Linked** column. Assigning main accounts to a main account category will aggregate the balances of the accounts when that category is used for financial reporting and analysis.  
3. Select or clear the **Linked** option to choose the main accounts.
4. Select **OK**.
5. Select **Yes**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
