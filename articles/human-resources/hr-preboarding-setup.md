---
# required metadata

title: Install and set up preboarding in Dynamics 365 Human Resources (preview)
description: Learn how to set up preboarding in Microsoft Dynamics 365 Human Resources after you set up the HR Recruiting app.
author: ramagadu
ms.date: 10/23/2026
ms.topic: how-to
ms.reviewer: twheeloc
# optional metadata

ms.search.form: HRMParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ramagadu
ms.search.validFrom: 2026-10-23
ms.dyn365.ops.version: Human Resources

---

# Install and set up preboarding in Dynamics 365 Human Resources (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article describes how to set up preboarding in Microsoft Dynamics 365 Human Resources after you set up the HR Recruiting app.
Preboarding in Dynamics 365 Human Resources (preview) is part of the Dynamics 365 Human Resource recruiting add-on and Dynamics 365 Human Resources careers. Set up the Recruiting app first, and then complete the steps in this article. For the requirements, see [Prerequisites for preboarding](hr-preboarding-prerequisites.md).

## Set up the Recruiting app

Follow these articles:

1. [Set up the HR Recruiting app](hr-recruit-setup.md). It describes the prerequisites and
recruitment feature.

1. [Set up the careers site in the HR Recruiting app](hr-recruit-career.md) - describes the installation of the **Dynamics 365 Human Resources careers** app and the activation of the site.

If you already installed the Recruiting app and the careers site, update both apps to the latest version. For more information, see [Power Platform admin center](https://admin.powerplatform.microsoft.com/). Go to **Resources** > **Dynamics 365 apps**. Preboarding is included in them.

> [!NOTE]
> The first installation or update that includes preboarding also creates the Dynamics 365 Human Resources virtual tables that preboarding uses, so it can take longer than usual. If the installation fails, select **Retry installation**.

### Turn on preboarding in Dynamics 365 Human Resources

1. In Dynamics 365 Human Resources, open the **Feature management** workspace, and select **Check for updates**.
1. Turn on these two features, in this order:

   1. **Enhanced recruiting candidate experience (preview)**. It adds the **Candidates (preview)** page.
   1. **Preboarding (preview)**. It adds the **Preboarding (preview)** tabs on the **Human resources parameters** page and in the **Onboarding** workspace.

1. Go to **Human resources** > **Setup** > **Human resources parameters**.
1. On the **Preboarding (preview)** tab, set **Enable preboarding** to **Yes**, and then select **Save**.

Set preboarding for each legal entity. Repeat steps 3 and 4 in each legal entity that uses preboarding.
For more information about configuration, see [Configure preboarding](hr-preboarding-configuration.md).

> [!IMPORTANT]
> If the legal entity already has candidates, don't run **Process candidate statuses** until you finish configuring preboarding. For more information, see [Update existing candidates](hr-preboarding-configuration.md#update-existing-candidates).

### Set up the connection reference

The Recruiting setup covers every connection reference that preboarding uses except one. Preboarding uses the **Recruiting FinOps connection** to attach the documents that candidates upload to the candidate in Dynamics 365 Human Resources.

1. In [Power Apps](https://make.powerapps.com/), select **Solutions** > **Default solution** > **Connection references**.
1. Open **Recruiting FinOps connection**, add a new or existing **Fin & Ops apps (Dynamics 365)** connection, and make sure that it's turned on.

### Preboarding flows

The Recruiting setup turns on the flows in **HCM Recruiting flows**, which include the preboarding flows. In **HCM Recruiting flows** > **Cloud flows**, search for **Preboarding**, and turn on any flow that's off.

### Candidate sign in

Candidates who don't have an account on the careers site yet accept their invitation by creating one. We recommend that you let them sign up with a trusted identity provider, such as Microsoft Entra External ID, Microsoft, Google, or LinkedIn. For more information, see [Configure external identity providers](hr-recruit-career.md#configure-external-identity-providers).

In Power Pages, under **Set up** > **Site visibility**, make sure that the site is **Public**. If it's private, candidates can't reach the sign-in page.

#### User access

You don't need to assign new security roles. Dynamics 365 Human Resources adds preboarding access to the existing **Human resource manager**, **Human resource assistant**, **Recruiter**, and **Recruiting application** roles.

### Confirm setup

1. In Dynamics 365 Human Resources, go to **Human resources** > **Recruitment** > **Candidates (preview)**, and select a test candidate whose status is **Ready for preboarding** and who has a primary email address.
1. On the **Preboarding** tab, select **Initiate**, and confirm.
1. Check that the invitation email arrives, and that its link opens the careers site.

If it doesn't arrive, in Power Apps, check the run history of **Preboarding Flow A - Initiate**. On the **Human resources parameters** page, check the **Career portal URL** on the **Preboarding (preview)** tab.

## Related information

- [Prerequisites for preboarding](hr-preboarding-prerequisites.md)
- [Configure preboarding](hr-preboarding-configuration.md)
- [Set up the HR Recruiting app](hr-recruit-setup.md)
- [Set up the careers site in the HR Recruiting app](hr-recruit-career.md)
