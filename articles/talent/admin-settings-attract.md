---
# required metadata

title: Admin settings in Attract
description: This topic provides information about enabling feature functionality for organizations and users in Attract.
author: 
manager: AnnBe
ms.date: 10/15/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-15
ms.dyn365.ops.version: Talent October 2018 update

---

# Admin settings in Attract
[!include[banner](../includes/banner.md)]

The Attract **Admin center** contains configuration settings, integration options, and setup for the Attract application.

## Company information

Add a company display name and logo that can be used on job posts and in the **Onboarding experience**.

## LinkedIn integration

Set up the **LinkedIn Recruiter System Connect (RSC) Integration**. Connect to LinkedIn by using your LinkedIn credentials to sync a candidate's LinkedIn profile, applications, interview feedback, and hiring team notes. A full LinkedIn recruiter license is required. For more informationabout the LinkedIn recruiting system, see [Recruiter System Connect (RSC) – FAQ](https://www.linkedin.com/help/recruiter/answer/90483).

## User permissions

Assign roles to users within your organization. The role options avaialble are **Admin**, **Recruiter**, **Hiring manager**, and **Read-only**. To learn more about user permissions, see [Security and Role Management in Attract](./security-attract.md).

## Feature management

As new features are added, they may be released in a public preview. Public preview features do not meet all service requirements. By receiving preview functionality, you consent to share your data with external systems. You may find that not all of the new features are needed for your organization. If this is the case, you can turn the **Released public preview features** off and on depending on your organization’s needs.

## Template management

A **Process** template contains all of the activities that should be included as part of the hiring process for a job. Your organization can choose to allow team members to create hiring process templates or only allow the Admin to create the templates. To allow team members to create their own hiring process templates, enable the **Template management** functionality. To learn more about process templates, see [Process templates in Attract](./process-templates-attract.md).


## Email template settings

In the **Email template settings** you can select a header image to be included in the email templates. The selected header will show on all email templates. You can also add a link to your organization's privacy and terms of use for communications to the footer of the template. This section also allows organizations to create email templates for various scenarios.
For more information, see [Email templates in Attract](./email-templates.md).

## Offer Process

You can configure the approval process for job offers including whether the offer must be approved before it is sent to a candidate. Approvers can also be required to leave a comment with their offer decision.

There are two approval workflows to choose from, **Parallel** and **Sequential**. 

- **Parallel** - Approvals are sent to all approvers at the same time. 
- **Sequential** - Approvals are routed to the approvers in a specific order.

Additional options related to the candidate experience can also be configured. You can select to allow candidates to decline an offer without additional discussion. If this option is set to **No**, candidates will not have access to the **Decline offer** button. If this option is set to **Yes**, candidates can decline the offer by selecting a reason and then selecting **Decline offer**.

Lastly, you can enforce an expiration to an offer. If this is set to **Yes**, offers will expire based on a selected date selected.

For more information, see To learn more about offer management see [Set up offer management](./offer-setup/md).
