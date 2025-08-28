---
# required metadata

title: Set up the HR Recruiting app 
description: This article explains how to set up the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/15/2025
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-12-03
ms.dyn365.ops.version: Human Resources

---

# Set up the HR Recruiting app 

This article explains how to set up the HR Recruiting app in Microsoft Dynamics 365 Human Resources.

## Prerequisites

Before you can install the Recruiting app, the following prerequisites must be met:

- You have a Dynamics 365 finance and operations environment, version 10.0.45 or later, and the most recent quality update is installed.
>[!NOTE]
> If you are on version 10.0.44, see [Known issues and limitations](hr-recruit-known.md). 
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
3. Select **Environments** and then search for and select your environment.
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
    - Recruiting content conversion connection
    - Recruiting office 365 outlook connection
    - Recruiting teams connection 

7. Edit each connection reference. Add a new or existing connection, and make sure that it's enabled.

    - **Recruiting approvals connection:** Add the **Approvals** connector.
    - **Recruiting dataverse connection:** Add the **Microsoft Dataverse** connector.
    - **Recruiting content conversion connection:** using the Content Conversion (preview) connector.
    - **Recruiting office 365 outlook connection:** using the Office 365 outlook connector.
    - **Recruiting teams connection:** using the Microsoft Teams connector. 


8. Go to **Solutions** and select the **Managed** solution.
9. Select **HCM recruiting flows**.
10. Select **Cloud flows**, and then select **Turn on** for the cloud flows that are disabled.
11. Repeat steps 8 through 10 for **HCM Recruiting**.

> [!NOTE]
> Make sure that all the **HCM Recruiting** flows are active. Otherwise, issues can occur. For example, if the **Portal create candidate** flow isn't active, candidates can't create a profile.

### Recruiting flows

|Name|	Description |
|-----|--------|
|Email notification flow 	|The primary process for dispatching email notifications utilizes predefined email templates. Used in different workflows based on the scenario.|
|Job ad approval flow	|Notify approvers via Teams/Outlook for job ad approval.|
|Job ad in app approval flow	|Manages in-app approvals and automatically completes the Teams or Outlook workflows if they have already been initiated.|
|Publish candidate to Dynamics 365 finance and operations	|When **Ready to hire** is clicked, the candidate's details are forwarded to the Dynamics 365 Human Resources.|
|When a candidate status changes in Dynamics 365 finance and operations	|Syncs candidate status from Dynamics 365 Human Resources back to the recruiting add-on app.|
|Prospect invite to apply	|When a candidate is added as a prospect and invited to apply, an email notification is sent asking them to apply for the job.|
|On delete of applicant |	Deletes applicant and clears related Hire table records.|
|When an applicant is deleted|	Delete candidate information in Dynamics 365 Human Resources when an applicant is removed.|
|When an application is created	|When an application is created, it triggers the email notification flow to send a confirmation email to the candidate.|
|When an application is rejected or withdrawn|	When an application is either rejected or withdrawn, the email notification flow is triggered to inform the candidate of their application status.|
|Portal create attachments in note table|	This process is initiated when a resume is attached to create a record in the note table. It is used in the recruitment add-on.|
|Portal create candidate flow|	When users sign up, the flow creates a record in the candidate table, and their personal information is populated based on that.|
|Portal update candidate type|	This process identifies whether a candidate is external or internal at sign-in and updates the candidate type column accordingly.|
|Portal update contact from candidate	|This flow updates the contact table when the first name, last name, middle name, and email fields in the candidate table are filled.|
|Post adaptive card flow	|This flow allows panel members to select and submit their preferred slots for interview scheduling.|
|Retrieve feature control setting	|This flow retrieves the feature control value using the namespace and feature control name.|
|Resume parse flow	|Upon uploading a resume, the flow triggers a plugin that parses the resume and returns parsed data to populate candidate details automatically.|
|Pass panel time slots|	Tracks the slots chosen for different panel members for a job.|
|Send meeting invite|	Sends meeting invitations to candidates and interviewers.|
|Create intermediate table candidate slots	| Monitors the slots that are sent to candidates.|
|Email lots to candidate and send to plugin|	Send email with options to candidates.|


