---
# required metadata

title: Set up the HR Recruiting app (preview)
description: This article explains how to set up the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/23/2024
ms.topic: article
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Set up the HR Recruiting app (preview)

[This article is prerelease documentation and is subject to change.]

This article explains how to set up the HR Recruiting app in Microsoft Dynamics 365 Human Resources.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can install the Recruiting app, the following prerequisites must be met:

- You have a Dynamics 365 finance and operations environment, version 10.0.40 (10.0.1935.72) or later, and the most recent quality update is installed.
- You have a Dynamics 365 Human Resources license for the finance and operations environment.  
- You're a user who has system administrator permissions for both Dynamics 365 Human Resources and Power Apps.
- One of the following Microsoft Power Platform integrations is completed:

    - If you don't yet use Microsoft Power Platform and want to expand your finance and operations environments by adding platform capabilities, see [Connect finance and operations apps with a new Microsoft Dataverse instance](../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md).
    - If you already have Dataverse and Microsoft Power Platform environments, and you want to connect them to finance and operations environments, see [Connect finance and operations apps with an existing Microsoft Dataverse instance](../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md).

- You have a license and permissions for Power Automate, Power Apps, and Office 365.
- The **Finance and Operations Virtual Entity** and **Microsoft Flow Approvals** solutions are installed. To install them, follow these steps:

    1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
    2. In the left pane, select **Resources** \> **Dynamics 365 apps**.
    3. Select **Install app**.
    4. Install the **Microsoft Flow Approvals** solution.
    5. Install the **Finance and Operations Virtual Entity** solution.

    For more information, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps#install-an-app).

## Get started

To configure the Recruiting app in Dynamics 365 Finance, follow these steps.

1. In Dynamics 365 Finance, open the **Feature management** workspace.
2. Select **Check for updates**.
3. On the **New** tab, search for the **(Preview) Enable recruitment add-on** feature.
4. Select **Enable now**.
5. Refresh the page.
6. Open the **Human resources parameters** page.
7. On the **Recruitment** tab, update the following fields:

    - Set the **Recruitment enabled** option to **Yes**.
    - In the **Recruitment experience** field, select **HR Recruitment**.
    - Set the **Integration to new recruiting app** option to **Yes**.

1. Refresh the page.

To see Recruiting requests and candidates, go to **Human Resources** > **Recruitment**.

## Install the Recruiting add-on app in Dataverse

To install the Recruiting add-on app for the first time, follow these steps.

1. Sign in to [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.hcmrecruiting-preview?flightCodes=4b09efddad8943cb82af3713c574a021) as an admin.
2. Select **Dynamics 365 Human Resources recruiting add-on**, and then select **Get it now**.
3. Select **Environments**, and then search for and select your environment.
4. Select the checkboxes to agree to the privacy statement and legal terms.
5. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
6. Select your environment, and then select the mandatory checkboxes.
7. Select **Install**.
8. To check the status of the installation, follow these steps:

    1. In the Power Platform admin center, select **Environments**, and then select your environment.
    1. Select **Resources** \> **Dynamics 365 apps**.
    1. Look in the **Status** column for **Dynamics 365 Human Resource recruiting add-on**. If installation was successful, the value is **Installed**. If the value is **Failed**, set up the app again by selecting **Retry installation**.

## Activate connections and flows for the Recruiting app

To activate connections and flows for the Recruiting app, follow these steps.

1. Sign in to [Power Apps](https://make.powerapps.com/).
2. Select the environment where you installed the Recruiting add-on app.
3. In the left pane, select **Solutions**.
4. In the list of solutions, select **Default Solution**.
5. Select **Connection reference**.
6. Search for **Recruiting**. The following solutions should be available:

    - Recruiting approvals connection
    - Recruiting dataverse connection

7. Edit each connection reference. Add a new or existing connection, and make sure that it's enabled.

    - **Recruiting approvals connection:** Add the **Approvals** connector.
    - **Recruiting dataverse connection:** Add the **Microsoft Dataverse** connector.

8. Go to **Solutions**, and select the **Managed** solution.
9. Select **HCM recruiting flows**.
10. Select **Cloud flows**, and then select **Turn on** for the cloud flows that are disabled.
11. Repeat steps 8 through 10 for **HCM Recruiting**.

    > [!NOTE]
    > Make sure that all the **HCM Recruiting** flows are active. Otherwise, issues can occur. For example, if the **Portal create candidate** flow isn't active, candidates can't create a profile.

## Activate the careers site

**Prerequisite:** The Recruiting add-on app must be installed in Dataverse.

To activate the careers site, follow these steps.

1. Sign in to [Power Pages](https://make.powerpages.microsoft.com/) as an admin.
2. Select your environment.
3. Select the **Inactive sites** tab.
> [!Note]
> If you can't view the inactive site, create a temporary site using any available template. After creating a temporary site, you'll be able to access the inactive site.”
 
4. Select **Reactivate** for **Recruiting-careers site** to activate the site.
5. Provide a name and web address for the website, and then select **Done**.

    > [!NOTE]
    > To ensure that future updates can be installed, don't modify the input of the **Reactivated website** field.

Site activation might take up to 10 minutes. After the site activated, it's available on the **Active sites** tab.

For more information, see [Reactivate sites](/power-pages/admin/reactivate-website).

> [!IMPORTANT]
> After your site is activated, confirm that the version number is at least 9.6. If it's earlier than 9.6, contact us. To find the version, execute {siteUrl}/_services/about in the browser.
