---
# required metadata

title: Create email templates in Attract
description: This topic provides information about the email templates that you can create and use in Microsoft Dynamics 365 Talent - Attract.
author: andreabichsel
manager: AnnBe
ms.date: 10/19/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Create email templates in Attract

[!include [banner](includes/banner.md)]

By using the email template library, admins can create a uniform theme and branding for all emails that are sent through Microsoft Dynamics 365 Talent: Attract and Offer. Admins can also curate a collection of email content templates that other users can consume. The hiring team can use these templates in their workflow to send emails more efficiently. Some emails are configured to be sent automatically, and the admin can use the email template library to customize the content for those emails.

> [!NOTE]
> To use Email templates, your organization must have the Comprehensive Hiring add-on.

## Global template configurations

To create consistent branding for all email communications, the admin must first set the global header and footer for all email templates. In the Admin center, on the **Email template settings** tab, in the **Header** section, the admin can upload an image to use as the header or banner for all emails. The image might be a company logo, a letterhead, or any other representative image. We recommend that the width be between 25 and 800 pixels, and that the height be between 25 and 150 pixels, because these dimensions are optimal for most email clients, such as Microsoft Outlook. The image must be a JPEG, JPG, PNG, or SVG file, and the file size must be less than 1 megabyte (MB). After an image is uploaded, a preview of the header is generated and shown. If the header image must be removed or replaced, the admin can use the **Remove** option above the preview.

In the **Footer** section, the admin can provide links to the company's privacy policy for communications, and to the terms and conditions. These links are incorporated into a footer that is automatically generated. A preview of this footer is then shown. The admin can also choose a particular language in which email footers will be sent as part of all emails. The same language configuration will also be used for putting together the interview summary table. 

Be sure to save your changes before you close the Admin center.

> [!NOTE] 
> The header and footer are global settings for all emails. Therefore, they will appear in all emails that are sent through Attract. If the settings aren't configured, the header and footer will be left out of all emails.

## Email template library 

After the global template configurations are set up, the admin can start to create and curate templates for all emails that are sent from Attract and Offer. The email template library is available only to admins. To open the library, on the main navigation menu, select the **Email templates** tab. The library is categorized by the various activities in Attract that emails must be sent for, such as scheduling, assessment, job creation and offer. The admin can select any category to view all the email types that are associated with the activity. For example, select **Scheduling** to view the various types of email that are sent during the scheduling process and all the templates that are available for each type of email. Each subsection in a category represents a type of email.

Some types of email can have more than one recipient. For example, in the **Scheduling** category, the emails that are sent when the interview schedule summary is needed, are sent to both candidates and interviewers. Each section has two main columns: **Template Title** and **Recipient**. Each row in a section represents a single template for a type of email. At first, a lock symbol will appear in the row for every template. This symbol indicates that the template is the standard template that is provided with Attract, and that it can't be deleted. For any template, the admin can use the ellipsis button (**...**) to duplicate the template, set it as a default template, or delete it. When a template is set as a default template, one of two behaviors can occur. The behavior is indicated by the badge or badges that appear in the row for the template:

- **Default** – This badge indicates that the template is the default template for email that is sent, and that information will be entered in it when a user sends email of that specific type.
- **Default** + **Autosent** – This combination of badges indicates that the template is the active template for system-generated emails that are sent automatically.

To edit a template, select the row, and make changes to the template.

> [!NOTE]
> Each recipient of a specific type of email has a default template. All the standard Attract templates are set as default templates until the admin creates a new template for a specific type of email and sets it as the default template.

## Create a template

To create a template, in the upper-right corner of the email template library, select **+ New template**. To select the type of email that you're creating the template for, select the recipient, the process, and the event that email must be sent for. Then select **Create**.

The template is opened in editing view, and you can name the template. For example, if the template is intended for candidates from a US university, but the content is written in French, you might enter **University\_US\_Francais** as the title. The title, subject line, and body content for any template can support languages besides English.

The **To** field for a template can't be edited, because you already selected the recipient when you first created the template.

You can add personas such as **Recruiter** or **Hiring Manager** to the carbon copy (Cc) line. When the email is sent, these roles are automatically replaced with the appropriate users, based on the context of the job.

The subject line and body content support placeholders. You can insert placeholders by typing **\#** and then selecting the appropriate placeholder in the autocomplete drop-down list. The list of available placeholders appears on the right side of the page. When the email is sent, the placeholders are automatically replaced, based on the context of the job and the recipient. For example, a template for an email that is sent to candidates contains the placeholder \#{Candidate\_Name}. When the email is sent to a candidate who is named Cameron, that placeholder will be replaced with Cameron's name.

The body content editor is a rich text editor that lets you style and format text. It also lets you insert hyperlinks and anchors.

After a template is created for a specific type of email, select the ellipsis button (**...**) in the row for the template, and set it as the default template.

## Consume templates

When the hiring team sends an email, it can use the templates that the admin created. If multiple templates have been created for the email that a user is sending, a drop-down list appears in the email composition workflow. The default template is entered automatically, but the user can select a different template.

> [!NOTE] 
> For emails that are sent automatically, multiple templates can be created. However, only one template can be set as the active template. Because this process is triggered by events, only the admin can determine which template should be used, based on the combination **Default** and **Autosent** badges in the template library.
