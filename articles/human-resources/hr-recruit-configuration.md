---
# required metadata

title: Configuration in the Recruiting app (preview)
description: This article describes how to configure the Human Resources Recruiting app.
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

# Configuration in the Recruiting app (preview)

This article describes how to configure the Recruiting app.

[This article is prerelease documentation and is subject to change.]

## Set up an email account

To enable users and email accounts for incoming and outgoing messages, follow these steps:
 
Prerequisites:
 - Confirm that you have permission as at least a conditional access administrator role or equivalent permissions.
 - Users and emails should be available in the tenant. 
 - Verify that the added user and email account belongs to the power platform environment by using Power platform admin center and has the basic user role.
 - Ensure the email account has a valid office license before setting it up.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

For users and email accounts to receive and send messages, follow these steps:
 
1.	In the Recruiting add-on app, go to **Settings** > **Advanced settings**.
2.	Select **Settings** > **Email configuration**.
3.	Select **Mailboxes**. You can ignore the pop-up regarding approving the email.
4.	Select **All mailboxes**.
5.	Search for the user or email and select it.
7.	Click **Approve email**. 
8.	Click **Test and enable mailbox**.
9.	Verify that the incoming and outgoing email status is showing **Success**. 
 
If the status doesn't display **Success** after refreshing the screen, go to **Name** > **Common** > **Alerts** to find the error message.
 
10.	The users assigned above must sign in and allow other users to send emails on their behalf, follow these steps:
   1.	Sign in to the Recruiting add-on App.
   2.	Go to **Settings** > **Personalization settings** > **Email**.
   3.	Select **Allow other Microsoft Dynamics 365 users to send email on your behalf**. This enables the power automated flows to send notification emails on behalf of this user.
 
               
### Settings in Recruiting add-on

To update the settings in the recruiting add-on, follow these steps: 
1. As the recruiting administrator, log in to Recruiting add-on app.
2. Go to **Configurations** > **Email account configurations**.
3. Add the user account that has the mailbox enabled.
4. Add email accounts for **Category – application**, **Prospect**, and **Rejection**.
 
 
### Customize the email account by creating new category

1.	Log in to https://make.preview.powerapps.com
2.	Select **Environment**.
3.	Go to **Solutions** > **Default solution**.
4.	Select **Tables** from left pane.
5.	Select **Email account configuration**.
6.	Select **Column** under **Schema**.
7.	Edit **Category** column and add the new choice.
8.	To configure the newly created email account category in the Recruiting add-on app, go to **Configurations** > **Email accounts configurations**.


### How to use email templates

The recruiting administrator or system administrator roles can set up email templates. This section lets you set up email templates for prospect, rejection, and application.
 
1.	Log in to the Recruiting add-on app, go to **Configurations**.
2.	The **Email templates** command bar shows you the templates that are available for recruiting solutions.   
3.	Fill in the description, subject, and body for the email template and save this information. 
For more information about how to create an email template in model-driven apps, see [Power Apps](/power-apps/user/email-template-create). 
    

### Customize email templates with new template type

1.	On the **Email templates** command bar, select **New** > select **Start with a blank template**.  
2.	Enter the following details:  
 - **Template name**  - Give your email template a detailed name to help you identify it later.
 - **Permission level** - Select **Organization** to share your template with others.
 - **Category** - The default value is **User**. Categories determine which dynamic text fields are available for use in your template.
 - **Language** - Display installed language packs. Language also helps to categorize your templates.
 - **Create** - Opens one of two editors where you can build your template.  
 
3.	Set up a new flow for newly created email category/template. 
The Email notification flow is responsible for sending emails for the standard scenarios. This flow can be triggered with the following input parameters. 
 - Record ID
 - Account category (email account category) 
Select the trigger point for the custom scenario.
Call the email notification flow as a child flow to send the emails with the configured template.
  
4.	Update the **Email notification flow** with the new category/template: 
 - Add the new case condition for newly added email template and category. 

### Company logos

Each company can have a logo that appears when the job is posted. The logo is visible to the candidate on the career site.
To set up a logo, follow these steps:
1. From the left menu pane, select **Company logos**.
2. Click **+New**.
3. Select Company by clicking on the search icon in **Company**.
4. Choose Company from the list.
5. Click **Save** to upload a logo.
6. Click **Choose file**, select the logo to upload, and click **Open**. This saves the company logo.

### Hiring template
A hiring template is a template that a recruiter can use for multiple job postings. You can adjust the stages and steps to suit your needs. A stage is a round that a recruiter wants to conduct for each candidate.
A step is an additional that may be needed under a stage.

To create a hiring template, follow these steps:
1. Select the hiring template from the left menu panel. Any available templates are shown.
2. To create a new template, select **+New**.
3. Enter a template name and description.
4. After saving, the following section of stage and steps are available:

#### Add stage
1. Select **+New** in the stage and step section. A pop-up appears.
2. Enable the toggle is stage.
3. Enter a stage name.
4. Click **Save** and **Close**.

#### Add steps
1.	Choose +New in the stage and step section. A pop-up appears.
2.	Enter a **Step** name.
3.	Select the stage under which you want to create the step.
4.	Click **Save** and **Close**.
