---
# required metadata

title: User session management
description: The user session setting represents the amount of time a user can be logged in before the user’s session expires.
author: paulliew
manager: AnnBe
ms.date: 11/11/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope:
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


The user session setting represents the amount of time a user can be logged in before the user’s session expires. Once the user’s session expires, the user is required to log in with his or her credentials. 

You can set the **Maximum session length** up to 2,160 hours (90 days) with a minimum of 1 hour.  

> [!NOTE] 
> This feature is available in Public Preview as of version 10.0.16.  To enable this feature, go to the Feature management page and emable the **(Preview) Enable session management for users** feature. 

To change the value, follow these steps: 

1. Go to **System administration > Users > User session management** page. 
2. Select **New**.  
3. In the new row, select the dropdown in the **User ID** field.  
4. In the user list, select a user. 
5. In the **Maximum session length (hours)** field, enter an hour. 
6. Click on the **Save** button. 

To update the user’s maximum session length: 

1. Select the user you want to update by clicking on the row. 
2. In the **Maximum session length (hours)** field, enter an hour. 
3. Click on the **Save** button. 

To replace the user’s maximum session length with another user: 

1. Select the user you want to update by clicking on the row. 
2. In the **User ID** field, select the dropdown and select another user. 
3. In the **Maximum session length (hours)** column, enter an hour. 
4. Click on the **Save** button. 
 
To delete the user’s maximum session length: 

1. Select the user you want to delete by clicking on the row. 
2. Click on the **Delete** button.

To delete the multiple users’ maximum session length: 

1. Check the rows you want to delete. 
2. Click on the **Delete** button. 
