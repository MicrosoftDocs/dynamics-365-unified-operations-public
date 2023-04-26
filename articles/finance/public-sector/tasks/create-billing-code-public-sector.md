--- 
# required metadata 
 
title: Create a billing code for the public sector
description: Billing code custom fields allow you to collect values for billing code fields when free text invoices are created. 
author: twheeloc
ms.date: 02/14/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustCustomField   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Public sector
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a billing code for the public sector

[!include [banner](../../includes/banner.md)]

Billing code custom fields allow you to collect values for billing code fields when free text invoices are created. After you assign the custom field to billing codes, users can access the field when the billing code is selected on a free text invoice line. This procedure was created using the PSUS demo company data in the public sector partition.

1. Go to **Accounts receivable > Setup > Billing code custom fields**.
2. Click **New**.
3. In the **Name** field, type a value.
4. In the **Type** field, select an option.
    * When you select an option, the fields in the **Description** section will change to the settings available for that option.  
    * In the **Details** section, enter the default value for this custom field and any other values that are needed.  
5. Open the **Description** section.
6. Optional: In the **Usage description** field, describe how the custom field should be used. This information is for internal purposes only. It is not visible to the user.
7. Open the **Billing code references** section. When you assign this custom field to a billing code, the billing code will be listed here.
8. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
