---
# required metadata 

title: Set up tax groups
description: This topic explains how to set up tax groups in Tax Calculation Service. 
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
# Set up tax groups

This topic explains how to set up tax groups in Tax Calculation service, including the initialization of tax group applicability matrix and configure lines in the matrix.

Tax group in Tax Calculation Service has the similar concept as sales tax group in Dynamics 365 Finance. It's a group of tax codes. Tax Calculation Service will use the intersection of tax group and item tax group to determine the tax codes.

However, the difference is that there is no additional parameter like Use Tax, Exempt Tax on tax group in Tax Calculation Service. These parameters are now available at tax code level.

> [!IMPORTANT]
> Tax group setup in Tax Calculation Service is legal entity agnostic. You can complete this setup in Regulatory Configuration Service only once. Tax groups will be synchronized to Dynamics 365 Finance automatically when you enable Tax Calculation service in Dynamics 365 Finance for the selected legal entity.



### Initial tax group

This section explains the essential setups for a tax group.

1. Open the **Tax group** tab, click **Manage Column** button (If it's your first time configure Tax group, the Manage Column form will be populated automatically)

2. Select **Tax group** field under **Lines**
![select-tax-group](media\select-tax-group.png)

3. Click **Add** arrow to add this field into the **Selected Columns**
![add-tax-group](media\add-tax-group.png)

4. Click **OK**



### Configure tax group

After you complete above steps, the tax group applicability rule matrix should be initiated.

![initial-tax-group](media\initial-tax-group.png)



You can add lines here to configure tax group

1. Click **Add**
2. Key in **Tax Group** name. 
> [!IMPORTANT]
> **We strongly recommend you to control the length of tax group name within 10 characters**, as this name will be synchronized back to Dynamics 365 Finance and maximum 10 characters of sales tax group name is allowed in Dynamics 365 Finance.
3. Select **Tax codes** belong to this tax group
> [!NOTE]
> You can select multiple tax codes under one tax group by ticking the radio before tax code name

![multiple-tax-codes-selection](media\multiple-tax-codes-selection.png)

4. Repeat step 1 to step 3 to add multiple tax groups

