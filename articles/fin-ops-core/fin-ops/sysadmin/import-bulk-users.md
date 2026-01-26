--- 
title: Import users from Microsoft Entra ID
description: This procedure can be used by system administrators to manually import selected users or to import a large number of users from Microsoft Entra ID. 
author: pnghub
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
ms.custom:
ms.reviewer: johnmichalak     
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0 
---

# Import users from Microsoft Entra ID

[!include [banner](../../../finance/includes/banner.md)]

## Import select users

This procedure can be used by system administrators to import select users from Microsoft Entra ID.

1. Import users by using the current session company as their default company. Change the current company if applicable before importing users.
1. Go to **System administration > Users > User**s.
1. Select **Import users**.
1. Select the users that should be imported and select **Import users**.

After import is completed, you must assign roles to users.

## Import users in bulk

This procedure can be used by system administrators to import a large number of users from Microsoft Entra ID.
It isn't possible to select users when using the Batch import option.

## Run the import as a batch job

1. Import users by using the current session company as their default company. Change the current company if applicable before importing users.
1. Go to **System administration > Users > Users**.
1. Select **Batch import**.
1. Expand the **Run in the background** section.
1. Select **Yes** in the **Batch processing** field.
1. Enter or select a value in the **Batch group** field. This step is optional.  
1. Select **Yes** in the **Private** field. This step is optional.  
1. Select **Yes** in the **Critical job** field. This step is optional.  
1. Select an option in the **Monitoring category** field.
1. Select **OK**.

After the import finishes, assign roles to users.

## Run in a sandbox environment

1. Select **Batch import**.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
