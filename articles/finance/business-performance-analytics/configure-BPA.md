---
# required metadata

title: Configure business performance analytics
description: This article describs how to configure business performance analytics
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 04/24/2023
ms.topic: conceptual
ms.prod: 
ms.technology:
ms.custom:

---

# Configure business performance analytics

>[!NOTE]
>The functionality noted in this article is available as part of a preview release. The content and the functionality are subject to change. 
>For more information about participating in public preview for business performance analytics, contact bpateam@microsoft.com. 

This article describes how to configure business performance analytics.

## Configuration of business performance analytics 

To successfully set up business performance analytics, follow the steps below. 

You must have System administrator and System customizer access in [Power platform admin center](https://admin.powerplatform.microsoft.com). The user must also have system administrator access in Dynamics 365 Finance, and access to create environments in Microsoft Dynamics Lifecycle Services (LCS). 

### Configure Dataverse 

To configure Dataverse for business performance analytics, follow these steps:
1. Go go LCS, open the environment page. Verify that the Power Platform integration is set up.
2. If the Dataverse has already been set up, the Dataverse environment name that is linked to the Finance environment will be listed. 
3. If Dataverse hasn't yet been set up, select **Setup**. After the setup has been successfully completed, the Dataverse environment name that is linked to in the 
Finance environment should be listed. 
If this integration was set up with an existing Microsoft Power Platform environment, contact your administrator to make sure that the linked environment isn't in the 
disabled state. For more information, see [Enable Power Platform integration](//fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration). 
To access the Microsoft Power Platform admin center, go to [Power Platform admin center](https://admin.powerplatform.microsoft.com).

### Configure your Azure AD tenant 

Azure Active Directory (Azure AD) must be configured so that it can be used with Dataverse and the Microsoft Power Platform applications. This configuration requires 
the project owner role or the environment manager role be assigned to the user in the Project security role field in LCS. Verify that the following setup is completed: 
 1. You have System administrator and System customizer access in the Power Portal admin center. 
 2. A Dynamics 365 Finance or equivalent license is applied to the user who is installing business performance analytics.

### Move data from production to sandbox environment 
To move data from production to sandbox, follow these steps, [Data movement](//fin-ops-core/dev-itpro/database/dbmovement-operations). 
This data will be loaded in business performance analytics and is a prerequisite before installing business performance analytics.   

### Required configurations  

The following configurations are required in the environment before installing business performance analytics and are required for record to report.  
 - Sql row version change tracking (preview) 
 - General ledger
 - Budget
 - Reversing entries

 These settings can be confirmed in Dynamics 365 Finance. Go to **System administration > Setup > License configuration**. 
 If any these configuration aren't enabled, confirm that they are enabled before installing. To enable the configurations, the system must be in maintenance
 mode.  
 
 ### Turn on maintenance mode using LCS  

1. Go to LCS.  
2. Go to your environment, click **Maintain**. 
3. Click **Enable maintenance mode**. 
 



