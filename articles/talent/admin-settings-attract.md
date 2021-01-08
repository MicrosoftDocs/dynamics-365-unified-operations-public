---
# required metadata

title: Configure company information in Attract
description: This topic explains how to configure company information and branding for Microsoft Dynamics 365 Talent - Attract.
author: andreabichsel
manager: AnnBe
ms.date: 12/07/2018
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

# Configure company information in Attract

[!include [banner](includes/banner.md)]

The Admin center in Microsoft Dynamics 365 Talent: Attract contains configuration settings, integration options, and setup options for the Attract application.

## Company information

Enter a display name for the company, and add a company logo. The display name and logo can then be used on job posts and during the onboarding experience.

## LinkedIn Integration

Set up the integration with LinkedIn Recruiter System Connect (RSC). After you connect to LinkedIn by using your LinkedIn credentials, you can sync a candidate's LinkedIn profile, applications, interview feedback, and hiring team notes. A full LinkedIn recruiter license is required. For more information about LinkedIn Recruiter, see [Recruiter System Connect (RSC) – FAQ](https://www.linkedin.com/help/recruiter/answer/90483).

## User permissions

Assign roles to users in your organization. The following roles are available: **Admin**, **Recruiter**, **Hiring manager**, and **Read-only**. For more information about user permissions, see [Security and role management in Attract](./security-attract.md).

## Feature management

As new features are added, they might be released in a public preview. Public preview features don't meet all service requirements. By receiving them, you agree to share your data with external systems. You might find that your organization doesn't require all the new features that are released. You can turn public preview features off and on, depending on your organization's needs.

## Template management

A process template contains all the activities that should be included as part of the hiring process for a job. Your organization can allow either all team members or just admins to create hiring process templates. To allow team members to create their own hiring process templates, turn on the Template management functionality. For more information about process templates, see [Create a process template in Attract](./process-templates-attract.md).

## Email template settings

Organizations can create email templates for various scenarios. You can select the header image to include in the email templates. The selected header will then appear in all email templates. In the template footer, you can add a link to your organization's privacy statement and terms of use for communications. For more information, see [Email templates](./email-templates.md).

## Offer process

You can configure the approval process for job offers. For example, you can specify whether an offer must be approved before it's sent to a candidate. You can also require that approvers leave a comment with their offer decision.

Two approval workflows are available: **Parallel** and **Sequential**.

- **Parallel** – Approvals are sent to all approvers at the same time.
- **Sequential** – Approvals are sent to the approvers in a specific order.

You can also configure options that are related to the candidate experience. For example, one option lets you specify whether candidates can decline an offer without additional discussion. If you set the **Allow candidates to decline an offer without additional discussion** option to **No**, the **Decline offer** button is available to candidates. If you set this option to **Yes**, candidates can decline the offer by selecting a reason and then selecting **Decline offer**.

You can also set and enforce an expiration date for offers. If you set the **Require an expiration date for all offers** option to **Yes**, offers expire after the number of hours or days that you specify.

For more information about offer management, see [Set up offer management](./offer-setup.md).
