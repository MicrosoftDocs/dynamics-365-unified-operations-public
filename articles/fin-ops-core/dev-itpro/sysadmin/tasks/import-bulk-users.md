--- 
# required metadata 
 
title: Import users from Azure Active Directory
description: This procedure can be used by system administrators to manually import selected users or to import a large number of users from Azure Active Directory. 
author: peakerbl
ms.date: 07/07/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Import users from Azure Active Directory

[!include [banner](../../includes/banner.md)]

## Import select users

This procedure can be used by system administrators to import select users from Azure Active Directory (Azure AD).

1. User will be imported with the current session company as their default company. Change current company if applicable before importing users.
2. Go to **System administration > Users > User**s.
3. Click **Import users**.
4. Select the users that should be imported and select **Import users**.

After import is completed it will be required to assign roles to users.

## Import users in bulk

This procedure can be used by system administrators to import a large number of users from Azure Active Directory.
Note that it is not possible to select users when using the Batch import option.

## Run the import as a batch job
1. User will be imported with the current session company as their default company. Change current company if applicable before importing users.
2. Go to **System administration > Users > Users**.
3. Click **Batch import**.
4. Expand the **Run in the background** section.
4. Select **Yes** in the **Batch processing** field.
6. In the **Batch group** field, enter or select a value. This is an optional step.  
7. Select **Yes** in the **Private** field. This is an optional step.  
8. Select **Yes** in the **Critical job** field. This is an optional step.  
9. In the **Monitoring category** field, select an option.
10. Click **OK**.

After import is completed, it will be required to assign roles to users.

## Run in a sandbox environment
1. Select **Batch import**.
2. Select **OK**.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]