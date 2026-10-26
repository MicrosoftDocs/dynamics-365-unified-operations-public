---
# required metadata

title: Preboarding in Dynamics 365 Human Resources (preview)
description: Learn how to preboard new hires in Microsoft Dynamics 365 Human Resources.
author: ramagadu
ms.date: 10/23/2026
ms.topic: overview
ms.reviewer: twheeloc
# optional metadata

ms.search.form: HRMParameters, HcmPreJoiningCandidateHub
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

# Preboarding in Dynamics 365 Human Resources (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Preboarding in Dynamics 365 Human Resources (preview) covers the time between a hiring decision and a new hire's first day. HR invites the candidate from Dynamics 365 Human Resources. This article describes preboarding in Microsoft Dynamics 365 Human Resources, which lets new hires complete their personal details and documents on the careers site before their first day. The candidate signs in to your careers site and completes a guided form with their personal details, address, contacts, dependents, emergency contacts, identification, experience, education, skills, certifications, screenings, and documents. The candidate then submits the form with their consent for a pre-employment check. HR reviews the submission, asks for corrections if needed, and records the pre-employment check. The information that the candidate entered is written to the candidate record in Human Resources, so it's ready when you hire them.

Preboarding is part of the HR Recruiting app (**Dynamics 365 Human Resource recruiting add-on**) and its careers site (**Dynamics 365 Human Resources careers**). It uses Microsoft Dataverse, Power Pages, and Power Automate cloud flows to move data between the careers site and Human Resources.

You can use preboarding on its own, for candidates that you create in Human Resources, without using any other Recruiting app features. Or you can use it with the Recruiting app, so that applicants, offers, and preboarding create one candidate lifecycle. Choosing whether preboarding comes before or after the offer is available only when you use the Recruiting app.

## Key capabilities

- Invite in one step – HR selects **Initiate** for a candidate. The candidate receives an email with an invitation link to the careers site.
- Guided candidate experience – The candidate completes the data collection steps and a review step on the careers site, at their own pace. You decide which steps are shown and which are mandatory, per legal entity.
- Data written back to Human Resources – When the candidate submits, the information is written to the candidate record in Human Resources. Documents are attached to the candidate.
- Review and rework – HR approves the submission or requests rework on specific sections, with instructions. The candidate sees which sections to update.
- Pre-employment check tracking – HR records the pre-employment check vendor and outcome, or skips the check with a reason. The candidate sees the progress on the careers site.
- One lifecycle across recruiting, offer, and preboarding – A lifecycle status on the candidate in Human Resources shows where each candidate is, and the applicant in the Recruiting app is kept in step. You can run preboarding before or after the offer.
- Keeps everyone informed – The candidate receives an email at each stage. HR receives Microsoft Teams notifications and can send the candidate messages from Human Resources.
- Extensible – You can add your own fields to the candidate form and map them to fields in Human Resources.

### How preboarding works

:::image type="content" source="./media/hr-preboarding-process.svg" alt-text="Diagram of the preboarding process in seven steps: create the candidate, invite, candidate completes the steps, candidate submits with consent, HR reviews, pre-employment check, and ready to onboard." lightbox="./media/hr-preboarding-process.svg":::

1. A recruiter moves an applicant to **Ready to hire** in the Recruiting app, which creates a candidate in Human Resources. HR can also [create a candidate directly in Human Resources](hr-preboarding-for-hr.md#create-a-candidate-in-human-resources).
1. HR selects **Initiate** on the **Preboarding** tab of the **Candidates (preview)** page. The candidate receives an invitation email.
1. The candidate redeems the invitation, creates an account on the careers site, and completes the preboarding steps.
1. The candidate reviews their information, gives consent for the pre-employment check, and submits.
1. HR reviews the submission in Human Resources, and then approves it, requests rework on specific sections, or disqualifies the candidate.
1. HR starts the pre-employment check and records its outcome, or skips the check.
1. When preboarding and the offer are both complete, the candidate is **Ready to onboard**, and HR hires them in Human Resources.

At each stage, the candidate's status on the careers site, the candidate record in Human Resources, and the applicant in the Recruiting app are kept up to date.

### Preboarding and the offer

You choose, per legal entity, whether preboarding happens before or after the offer:

- **Preboarding first** – The candidate completes preboarding and the pre-employment check first. The offer follows.
- **Offer first** – The candidate accepts the offer first. Preboarding follows.

If you use **Offer management** in the Recruiting app, the offer outcome is reported to Human Resources automatically. If you don't use **Offer management**, the offer phase is completed automatically.

> [!NOTE]
> **Offer management** in the Recruiting app isn't released yet. The offer phase is completed automatically until it's released, regardless of which option you choose.

### Use preboarding with another recruiting solution

If you use a third-party recruiting solution instead of the HR Recruiting app, you can still use preboarding. Create the candidates in Human Resources, and run preboarding for them. In this case, preboarding always comes first, and there's no offer phase in Human Resources. When preboarding is complete, the candidate is **Ready to onboard**. You still install the HR Recruiting app and its careers site, because preboarding is delivered with them. For more information, see [Prerequisites for preboarding](hr-preboarding-prerequisites.md).

## Related information

- [Prerequisites for preboarding](hr-preboarding-prerequisites.md)
- [Install and set up preboarding](hr-preboarding-setup.md)
- [Configure preboarding](hr-preboarding-configuration.md)
- [Manage preboarding as HR](hr-preboarding-for-hr.md)
- [Complete preboarding as a candidate](hr-preboarding-for-candidates.md)
- [Add custom fields to preboarding](hr-preboarding-custom-fields.md)
- [Preboarding FAQ](hr-preboarding-faq.md)
