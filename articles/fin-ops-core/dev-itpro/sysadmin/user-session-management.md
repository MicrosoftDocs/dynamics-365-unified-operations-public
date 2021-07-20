---
# required metadata

title: User session management
description: The user session setting represents the amount of time a user can be signed in before the user’s session expires.
author: paulliew
ms.date: 11/13/2020
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: paulliew
ms.search.validFrom: 2020-11-30
ms.dyn365.ops.version: 10.0.16
---

# User session management

[!include[banner](../includes/banner.md)]


The user session setting represents the amount of time a user can be signed in before the user’s session expires. After the user’s session expires, the user is required to sign in with their credentials.

The **Maximum session length** can be up to 2,160 hours (90 days), with a minimum of 1 hour.  

> [!NOTE] 
> This feature is available in public preview as of version 10.0.16. To enable this feature, go to the Feature management page and enable the **(Preview) Enable session management for users** feature. 

To change the maximum session length, follow these steps: 

1. Go to **System administration > Users > User session management**. 
2. Select **New**.  
3. In the new row, select the drop-down menu in the **User ID** field.  
4. In the user list, select a user. 
5. In **Maximum session length (hours)**, enter a value. 
6. Select **Save**. 

To update the user’s maximum session length: 

1. Select the user that you want to update by selecting the row. 
2. In **Maximum session length (hours)**, enter a value. 
3. Select **Save**. 

To delete a user’s maximum session length and replace it with another user’s session: 

1. Select the user that you want to delete by selecting the row. 
2. In the **User ID** field, select the drop-down menu and select another user. 
3. In the **Maximum session length (hours)** column, enter an hour. 
4. Select **Save**. 
 
To delete the user’s maximum session length: 

1. Select the user that you want to delete by selecting the row. 
2. Select **Delete**.

To delete the multiple users’ maximum session length: 

1. Select the rows that you want to delete. 
2. Select **Delete**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]