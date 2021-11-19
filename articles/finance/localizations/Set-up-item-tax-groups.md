---
# required metadata 

title: Set up item tax groups
description: This topic explains how to set up item tax groups in Tax Calculation Service. 
author: wangchen
ms.date: 11/17/2021
ms.topic: business-process 
ms.prod:  
ms.technology:  

# optional metadata 

ms.search.form: TaxTable, TaxData   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-10-26 
ms.dyn365.ops.version: Version 10.0.21 
---
# Set up item tax groups

This topic explains how to set up item tax groups in Tax Calculation service, including the initialization of item tax group applicability matrix and configure lines in the matrix.

Item tax group in Tax Calculation Service has the similar concept as item sales tax group in Dynamics 365 Finance. It's a group of tax codes. Tax Calculation Service will use the intersection of tax group and item tax group to determine the tax codes.

> [!IMPORTANT]
> Item tax group setup in Tax Calculation Service is legal entity agnostic. You can complete this setup in Regulatory Configuration Service only once. Item tax groups will be synchronized to Dynamics 365 Finance automatically when you enable Tax Calculation service in Dynamics 365 Finance for the selected legal entity.



### Initial item tax group

This section explains the essential setups for a item tax group.

1. Open the **Item tax group** tab, click **Manage Column** button (If it's your first time configure Item tax group, the Manage Column form will be populated automatically)

2. Select **Item tax group** field under **Lines**
![select-item-tax-group](media\select-item-tax-group.png)

3. Click **Add** arrow to add this field into the **Selected Columns**
![add-item-tax-group](media\add-item-tax-group.png)

4. Click **OK**



### Configure item tax group

After you complete above steps, the item tax group applicability rule matrix should be initiated.

![initial-item-tax-group](media\initial-item-tax-group.png)



You can add lines here to configure item tax group

1. Click **Add**
2. Key in **Item tax Group** name. 
> [!IMPORTANT]
> **We strongly recommend you to control the length of item tax group name within 10 characters**, as this name will be synchronized back to Dynamics 365 Finance and maximum 10 characters of item sales tax group name is allowed in Dynamics 365 Finance.
3. Select **Tax codes** belong to this item tax group
> [!NOTE]
> You can select multiple tax codes under one item tax group by ticking the radio before tax code name

![multiple-tax-codes-selection](media\multiple-tax-codes-selection.png)

4. Repeat step 1 to step 3 to add multiple item tax groups

