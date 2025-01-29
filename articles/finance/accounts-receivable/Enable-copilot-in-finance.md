---
# required metadata

title: Enable Copilot in Dynamics 365 Finance
description: This article explains how to enable the functionality that's related to Microsoft Copilot in Dynamics 365 Finance. 
author: JodiChristiansen
ms.date: 01/21/2025
ms.topic: article
ms.collection: bap-ai-copilot

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
# Enable Copilot in Dynamics 365 Finance

This article describes the features that are available through the **Copilot in Microsoft Dynamics 365 Finance** app. This app is installed by default in the Microsoft Power Platform admin center.

## Prerequisites

To enable Copilot capabilities in Dynamics 365 Finance, you must be running Finance version 10.0.38 or later.

> [!NOTE]
> In version 10.0.40 and later, and in the proactive quality updates (PQUs) for versions 10.0.39 and 10.0.38, the **Copilot in Microsoft Dynamics 365 Finance** app is installed in the Dataverse environment that's associated with the organization where you're running Finance.

## Country/region and language availability

For information about the languages that this Copilot feature was validated for, see [Explore Copilot features by geography and languages](https://go.microsoft.com/fwlink/?linkid=2270154). Although the feature can be used in other languages, it might not work as intended. Language quality might vary, based on the user's interactions or system settings, and might therefore affect accuracy and the user experience.

### Step 1: Connect your Finance app to a Dataverse environment

The subscription for your Finance app includes a Dataverse environment that's deployed in your tenant. To support copilots, your Finance app environment must be associated with a Dataverse environment. Typically, this association is automatically enabled. However, in some situations, the tenant admin must enable it.

Confirm that Power Platform Integration is enabled in Microsoft Dynamics Lifecycle Services. For more information, see [Enable Power Platform Integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md) and [Lifecycle Services (LCS) user guide](../../fin-ops-core/dev-itpro/lifecycle-services/lcs-user-guide.md). You don't have to enable dual-write for this feature.

### Step 2: Turn on Copilot in Dynamics 365 Finance

> [!NOTE]
> Copilots and generative AI features that are generally available are turned on by default.

If you must turn on any of the features from this section in your environment, you might also have to redeploy the Copilot app.

Depending on the availability of Copilot and generative AI back-office services in your region, you might have to turn on copilots and generative AI features in your Dataverse environment. You must complete the steps in the Dataverse environment that's connected to the environment where you're running your Finance app.

## Allow cross-region data movement for your Dataverse environment

Depending on the availability of Copilot and generative AI back-office services in your region, your Dataverse environment might have to be set up to support cross-region calls. For more information, see [Enable Copilot capabilities in finance and operations apps](../../fin-ops-core/dev-itpro/copilot/enable-copilot.md).

> [!IMPORTANT]
> If cross-region data movement is required, but it isn't selected, deployment of the Copilot app will fail, users won't be able to see the copilot summary, or the copilot summary won't provide answers, depending on the situation.

If the **Move data across regions** checkbox is available, but it isn't selected, review the terms of use, and then select the checkbox.

For information about the capabilities and limitations of AI-powered Copilot features in Microsoft Dynamics 365 Finance, see [Responsible AI FAQs for Dynamics 365 Finance](../transparency-note.md).

## Enable the required security role

Users who should have access to the functionality must be assigned the **Finance and Operations AI** security role in Dataverse.

1. In the detail view of the environment, in the **Access** field, select **Users** or **Teams**.
1. Select the users or teams that should have access, and assign the **Finance and Operations AI** security role.
