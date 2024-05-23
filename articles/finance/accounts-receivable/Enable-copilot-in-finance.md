---
# required metadata

title: Terminate schedule lines
description: This topic describes how to enable the copilot functionality in Microsoft Dynamics 365 Finance. 
author: JodiChristiansen
ms.date: 05/23/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24


---
# Enable Copilot in Microsoft Dynamics 365 Finance
This article describes the features available using the app **Copilot in Microsoft Dynamics 365 Finance**. The app is installed by default in the Power Platform Admin Center. 

## Prerequisites 

To enable Copilot capabilities in Microsoft Dynamics 365 Finance, you must be running version 10.0.38 or later in Microsoft Dynamics 365 Finance.  

> [!NOTE]
> As of version 10.0.40, and in the proactive quality updates (PQUs) for version 10.0.39 and 10.0.38, the required app **Copilot in Microsoft Dynamics 365 Finance** is deployed in the Dataverse environment that’s associated with the organization where you’re running Microsoft Dynamics 365 Finance.   

## Country/region and language availability 

This copilot feature was validated for [these languages](https://go.microsoft.com/fwlink/?linkid=2270154/). While it can be used in other languages, it may not function as intended. Language quality may vary based on the user’s interaction or system settings, which may impact accuracy and the user experience. 

### Step 1: Connect your Microsoft Dynamics 365 Finance app to a Dataverse environment 

The subscription for your Dynamics 365 Finance app includes a Dataverse environment that's deployed in your tenant. To support copilots, your Dynamics 365 Finance app environment must be associated with a Dataverse environment. Typically, this association is automatically enabled. However, in some situations, the tenant admin must enable it. 

Confirm that [Power Platform Integration is enabled](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration/) in [Microsoft Dynamics Lifecycle Services](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide/). You don't have to enable dual-write for this feature. 

### Step 2: Turn on Copilot in Microsoft Dynamics 365 Finance 

> [!NOTE]
> Copilots and generative AI features that are generally available are turned on by default.  

If you have to turn on any of the features from this section in your environment, you might also have to redeploy the Copilot application.  

Depending on the availability of Copilot and generative AI back-office services in your region, you may may have to turn on copilots and generative AI features in your Dataverse environment. You must complete the steps in the Dataverse environment that's connected to the environment where you're running your Finance app. 

## Allow cross-region data movement for your Dataverse environment 

Depending on the availability of Copilot and generative AI back-office services in your region, your Dataverse environment might also have to be set up to support cross-region calls. For more information, see [Enable copilots and generative AI features](https://learn.microsoft.com/en-us/power-platform/admin/geographical-availability-copilot/). 

> [!Important]
> If cross-region data movement is required, but it’s not selected, deployment of the Copilot app will fail, users won’t be able to see the copilot summary, or the copilot summary will not provide answers, depending on the situation.  

If the **Move data across regions** checkbox is available, but it’s not selected, review the terms of use, then select the checkbox.  

For information about the capabilities and limitations of AI-powered Copilot features in Microsoft Dynamics 365 Finance, see the [Transparency FAQs](https://learn.microsoft.com/en-us/dynamics365/finance/transparency-note/) for Microsoft Dynamics 365 Finance. 

## Enable the required security role 

Users who should have access to the functionality must be assigned the **Finance and Operations AI** security role in Dataverse. 
- In the detail view of the environment, in the Access field, select Users or Teams. 
- Select the users or teams that should have access and assign the **Finance and Operations AI** security role to them. 
