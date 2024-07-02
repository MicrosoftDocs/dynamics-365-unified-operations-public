---
# required metadata

title: Set up Recruiting app 
description: This article describes how to set up the Recruiting app in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 07/01/2024
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

# Set up Recruiting app 

[This article is prerelease documentation and is subject to change.]

This article describes how to set up the Recruiting app in Dynamics 365 Human Resources.

## Prerequisites
Before you can install the recruiting app, the following prerequisites must be met: 
 - Dynamics 365 finance and operations environment version 10.0.40 or higher, and you must have the most recent quality update installed.
 - A finance and operations environment with a Dynamics 365 Human Resources license.
 - A user with system administrator permissions for both Dynamics 365 Human Resources and Power Apps.
 - Complete the following Power Platform integration:
            - If you don't yet use Microsoft Power Platform and want to expand your finance and operations environments by adding platform capabilities, see Connect finance and operations apps with a new
   Microsoft Dataverse instance.
           - If you already have Dataverse and Power Platform environments, and want to connect them to finance and operations environments, see Connect finance and operations apps with an existing Microsoft
   Dataverse instance.
 - A license and permissions for Power Automate, Power Apps and Office 365.
 - Sign in to the Power Platform admin center. (Manage Dynamics 365 apps that run on Microsoft Dataverse - Power Platform | Microsoft Learn)
        •	Select Resources > Dynamics 365 apps from the left-side menu.
        •	Select Install App from the top menu bar.
        •	Install Microsoft Flow Approvals solution.
        •	Install Finance and Operations Virtual Entity solution.
 
### Getting started

To configure the recruiting app in Dynamics 365 Finance, follow these steps: 
 
1.	In Dynamics 365 Finance, go to **Feature management**.
2.	Click **Check for updates**.
3.	On the **New** tab, search for **(Preview) Enable recruitment add-on** feature.
4.	Click **Enable now**.
5.	Refresh the Page.
6.	Go to **Human resources parameters** > **Recruitment** tab, update the following fields: 
 - Set the **Recruitment enabled** field to **Yes**.
 - In the **Recruitment experience** field, select **HR Recruitment**.
 - Set the **Integration to new recruiting app** to **Yes**.
7. Refresh the page.

The **Recruiting** workspace is now available in Dynamics 365 Finance.


### Install the Recruiting add-on App in Dataverse

To install the Recruiting add-on app for the first time, follow these steps:
 
1.	Sign in to App source as an admin. 
2.	Select **Dynamics 365 Human Resources recruiting add-on**, select **Get it now**.
3.	Select **Environments**, search for and select your environment.
4.	Check all the Privacy statement and legal terms.
5.	Sign in to Power Platform admin centre, select your environment, select the mandatory checkboxes.
6.  Select **Install**.
7.  To check the status of the installation, follow these steps:
 - In the Power Platform admin centre, select **Environments** > your environment.
 - Select **Resources** > **Dynamics 365 apps**. 
When the installation is successful, the **Status** column for Dynamics 365 Human Resource recruiting add-on shows **Installed**.
If the installation shows **Failed**, you can set up the app again by choosing **Retry installation** in the Power Platform admin center.

### Activate connections and flows for Recruiting app
To activate connection and flow for the recruiting app, follow these steps: 
1.	Sign in to Power Apps and choose the environment where you installed your Recruiting add-on app.
2.	In the left pane, select **Solutions**. From the list of solutions, select the **Default solution**.
3.	Select **Connection reference**.
4.	Search for **Recruiting**. The below solutions are available: 
 - **Recruiting approvals connection**
 - **Recruiting dataverse connection**
5.	Edit the above connection references, add a new/existing connection and make sure they're enabled.
 - **Recruiting approvals connection** - add the **Approvals** connector.
 - **Recruiting dataverse connection** - add the **Microsoft Dataverse connector**.
6.	Go to **Solutions**, click **Managed** solution.
7.	Click **HCM recruiting flows**.
8.	Select **Cloud flows** and click **Turn on** for the cloud flows are disabled.
9.	Repeat steps 6, 7, and 8 for **HCM Recruiting**.
 
>[!Note]
> Confirm all HCM Recruiting flows are active. If the flows aren't active, it might cause problems. For example, if the **Portal create candidate** flow isn't active, Candidates won't be able to create their
> profile.

### Activate careers site

Prerequisite: You need to have the Dynamics 365 Human Resources recruiting add-on installed in dataverse.

To activate the career site, follow these steps:
1.	Go to Power Page and login as admin. 
2.	Select your environment.
3.	Select the **Inactive site**.
4.	Click **Reactivate** for **Recruiting-careers site** to activate the site.  
5.	Provide website name and web address and click Done.
Note: Don't modify the input of **Reactivated website** field to ensure that future updates can be installed. 
6.	The site might need up to 10 minutes to activate. Once the site activated, the site will be available under **Active sites**. 

For more information, see Visit Reactivate sites | Microsoft Learn

>[!Important]
> Verify the version of your site after it's activated. It should be at least version 9.6. If the version is lower than 9.6, contact us.





