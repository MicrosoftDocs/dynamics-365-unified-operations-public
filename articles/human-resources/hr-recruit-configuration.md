---
# required metadata

title: Configuration in the HR Recruiting app (preview)
description: This article explains how to configure the HR Recruiting app in Microsoft Dynamics 365 Human Resources.
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

# Configuration in the HR Recruiting app (preview)

[This article is prerelease documentation and is subject to change.]

This article explains how to configure the HR Recruiting app in Microsoft Dynamics 365 Human Resources.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Set up an email account

**Prerequisites:**

- Confirm that you have at least permission as a conditional access administrator role or equivalent permissions.
- Users and emails should be available in the tenant.
- In the Power Platform admin center, confirm that the added user and email account belongs to the Microsoft Power Platform environment and has the basic user role.
- Ensure that the email account has a valid Office license.

To enable users and email accounts to receive and send messages, follow these steps.

1. Sign in to the Recruiting add-on app.
1. Go to **Settings** \> **Advanced settings**.
1. Select **Settings** \> **Email configuration**.
1. Select **Mailboxes**. You can ignore the pop-up message about approving the email.
1. Select **All mailboxes**.
1. Search for the user or email account, and select it.
1. Select **Approve email**. 
1. Select **Test and enable mailbox**.
1. Confirm that the incoming and outgoing email status is **Success**.

    If the status isn't **Success** after you refresh the page, go to **Name** \> **Common** \> **Alerts** to find the error message.

1. The user that you assigned must follow these steps to allow other users to send email on their behalf:

    1. Sign in to the Recruiting add-on app.
    1. Go to **Settings** \> **Personalization settings** \> **Email**.
    1. Select **Allow other Microsoft Dynamics 365 users to send email on your behalf**. This step enables the Power Automate flows to send notification emails on behalf of this user.

## Update settings in the Recruiting add-on

To update the settings in the Recruiting add-on, follow these steps.

1. Sign in to Recruiting add-on app as the recruiting administrator.
1. Go to **Configurations** \> **Email account configurations**.
1. Add the user account that the mailbox is enabled for.
1. Add email accounts for **Category – application**, **Prospect**, and **Rejection**.

## Customize the email account by creating a new category

1. Sign in to [Power Apps](https://make.powerapps.com/).
1. Select the environment.
1. In the left pane, select **Solutions**.
1. In the list of solutions, select **Default Solution**.
1. In the left pane, select **Tables**.
1. Select **Email account configuration**.
1. Under **Schema**, select **Columns**.
1. Edit the **Category** column, and add the new category.
1. To configure the new email account category in the Recruiting add-on app, go to **Configurations** \> **Email accounts configurations**.

## Use email templates

The recruiting administrator or system administrator role can set up email templates. Use the information in this section to set up email templates for prospects, rejections, and applications.

1. Sign in to the Recruiting add-on app.
1. Go to **Configurations**.
1. The **Email templates** command bar shows the templates that are available for recruiting solutions.
1. Enter a description, subject, and body for the email template, and then save this information.

For more information about how to create an email template in model-driven apps, see [Create email templates](/power-apps/user/email-template-create).

### Customize email templates with a new template type

1. On the **Email templates** command bar, select **New**, and then select **Start with a blank template**.
1. Enter the following details:

    - **Template name** – Enter a detailed name for the email template, so that you can identify it later.
    - **Permission level** – To share the email template with other users, select **Organization**.
    - **Category** – The default value is **User**. Categories determine which dynamic text fields are available in your template.
    - **Language** – This field shows the installed language packs. The language helps categorize your templates.
    - **Create** – Open one of two editors where you can build your template.

1. Set up a new flow for the new mail category/template.

    The **Email notification** flow is responsible for sending emails for the standard scenarios. This flow can be triggered through the following input parameters:

    - Record ID
    - Account category (email account category)

1. Select the trigger point for the custom scenario.
1. To use the configured template to send emails, call the **Email notification** flow as a child flow.
1. Update the **Email notification** flow with the new category/template. Add the new case condition for the new email template and category.

## Set up a company logo

Each company can have a logo that appears when the job is posted. The logo is visible to candidates on the careers site.

To set up a company logo, follow these steps.

1. In the left pane, select **Company logos**.
1. Select **New**.
1. In the **Company** field, use the search button to search for the company.
1. Select the company in the list.
1. Select **Save** to upload a logo.
1. Select **Choose file**, select the logo to upload, and then select **Open**. The company logo is saved.

## Create a hiring template

A hiring template is a template that a recruiter can use for multiple job postings. You can adjust the stages and steps to suit your needs. A *stage* is a round that a recruiter wants to conduct for each candidate. A *step* is an additional action that might be needed under a stage.

To create a hiring template, follow these steps.

1. In the left pane, select the hiring template. All available templates are shown.
1. To create a new template, select **New**.
1. Enter a name and description for the template.
1. Save your changes.

After you save the hiring template, a section for stages and steps becomes available.

### Add a stage

1. In the stage and step section, select **New**.
1. In the dialog box, enable the **Is stage** option.
1. Enter a name for the stage.
1. Select **Save** and then **Close**.

### Add steps

1. In the stage and step section, select **New**.
1. In the dialog box, enter a name for the step.
1. Select the stage that you want to create the step under.
1. Select **Save** and then **Close**.

### Screening template
A screening template is a template that recruiters use to store one or more questions. Templates can be used in multiple job ads so new questions don't need to be created for every job ad. 

### How to create screening template

To create a screening template, follow these steps:
1. Select the screening template from the left-side menu.
2. To generate a new template, click **+ New**.
3. Enter a name and description for your template.
4. After the template is saved, you'll have the option to add questions.

### Add questions to a screening template

1. Click **+ New** and a sidebar pops up.
2. Enter your question.
3. Select the **Answer type**:
 - For **Yes/No**, **Single-select**, or **Numeric answer** types, select **Qualifying** checkbox to require a preferred answer for the question.
 - If the candidate gives the preferred answer, they pass the screening; if not, they fail.
 - There can be more than one qualifying question.
