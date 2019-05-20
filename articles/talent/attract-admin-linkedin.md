---
# required metadata

title: Set up integration with LinkedIn for Microsoft Dynamics 365 for Talent - Attract
description: Configure LinkedIn integration for Microsoft Dynamics 365 for Talent - Attract so you can easily post jobs to LinkedIn from Attract and so your recruiters can sync their recruiting information with a candidate's LinkedIn profile.
author: andreabichsel
manager: AnnBe
ms.date: 05/20/2019
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
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-05-20
ms.dyn365.ops.version: Talent October 2018 update

---

# Set up integration with LinkedIn

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Talent: Attract provides two ways to integrate with LinkedIn to help you source candidates from this popular career site:

- Post jobs from Attract to LinkedIn
- Source candidates from LinkedIn to Attract

> [!NOTE]
> You need the Comprehensive hiring add-on and LinkedIn Recruiter seats to be able to use LinkedIn Recruiter integration with Attract. For more information, see [Which version of Attract?](./attract-comprehensive-hiring.md).

## Configure job posting to LinkedIn

Before you can post jobs from Attract to LinkedIn, you need a LinkedIn Company ID. Your LinkedIn Company ID is a string of numbers that uniquely identifies your company within LinkedIn. For more information, see [Associating your LinkedIn Company ID with the LinkedIn Job Board - Frequently Asked Questions](https://aka.ms/findID).

1. On the **Setup** menu (the gear symbol) in the upper-right corner, select **Admin center**.

2. Select the **LinkedIn Integration** tab.

3. Under **Company name**, enter the name of your company.

4. Under **Company ID**, enter your LinkedIn Company ID.

5. Select **Save**.

> [!NOTE]
> Keep in mind the following about posting jobs to LinkedIn:
> 1. Without further configuration, Attract posts jobs to LinkedIn as Limited Listing jobs. These are free job postings that candidates can see on LinkedIn while they're activily searching for jobs or while viewing your company page on LinkedIn. You can't promote Limited Listing jobs on LinkedIn. If you want to promote Limited Listings, you need to work with LinkedIn to enable Job Wrapping. For more information about Job Wrapping, see [Limited Listings vs Premium Job Slots for Job Wrapping](https://www.linkedin.com/help/recruiter/answer/79049/limited-listings-vs-premium-job-slots-for-job-wrapping) and [Job Wrapping Plus - FAQs](https://www.linkedin.com/help/recruiter/answer/79050/job-wrapping-frequently-asked-questions).
>
> 2. When posting jobs to LinkedIn, Attract provides the Microsoft 365 organization with the job. LinkedIn links the job to a company based on the organization name provided. If your job is listed with the wrong company on LinkedIn, check that your Microsoft 365 organization name matches the company name on LinkedIn. If you need to change any information for your organization, see [Change your organization's address, technical contact, and more](https://docs.microsoft.com/en-us/office365/admin/manage/change-address-contact-and-more). If you still have problems, contact [LinkedIn support](https://www.linkedin.com/help/linkedin).
>
> 3. Jobs posted to LinkedIn appear on the live LinkedIn site. LinkedIn doesn't have a test environment for posting jobs. 
>
> 4. It can take up to 24 hours for posted jobs to appear on LinkedIn, due to LinkedIn's process for batch job posting.

## Set up LinkedIn Recruiter with Attract 

To allow recruiters to source jobs through LinkedIn Recruiter, you need to configure integration with LinkedIn Recruiter in Attract. To complete the configuration process, you must work with the user who is an admin on your organization's LinkedIn Recruiter contract.

1. On the **Setup** menu (the gear symbol) in the upper-right corner, select **Admin center**.

2. Select the **LinkedIn Integration** tab.

[![Attract Admin view to start LinkedIn Recruiter integration](./media/LinkedInConnect.png)](./media/LinkedInConnect.png)

3.  Select **Connect** to start the setup, which will guide you through the LinkedIn sign-in process.

4.  If you have seats on multiple LinkedIn contracts, select the contract that you would like to connect to the Attract system. If you have a seat on only one LinkedIn contract, you can skip this step.

5.  Under **Recruiter System Connect (RSC)**, select **Request**.

[![Attract Admin view to Request LinkedIn Recruiter integration](./media/RequestLinkedInRSC.png)](./media/RequestLinkedInRSC.png)

6.  The **Recruiter System Connect (RSC)** setting should now show as **Partner ready**. and is ready to be turned on from the admin settings in LinkedIn Recruiter. If you see **Notify partner** on this page, wait a few seconds, click **Notify partner**, and then refresh the page. It should now show as **Partner ready**.

[![Attract Admin view to indicate Attract side of requests have been completed](./media/PartnerReadyRSC.png)](./media/PartnerReadyRSC.png)

7. To complete the following steps, you need to have admin privileges on your LinkedIn Recruiter Contract.

    a.  Sign in to LinkedIn using the your admin account and go to LinkedIn Recruiter on the top right. 

    b. On the **More** menu at the top of the screen, click **Admin Settings**, and then click the **ATS** Tab.

    c. To enable one-click export for just one contract, turn on **Contract Level access (for every seat on this contract**. If you want to enable it for the entire company, turn on **Company Level access (for every contract in your company**.

[![Turn on Attract integration from LinkedIn Recruiter Admin view](./media/EnableRSC.png)](./media/EnableRSC.png)

9. In the Attract Admin center, select the **LinkedIn integration** tab. The **Recruiter System Connect (RSC)** setting should now display as **Enabled**.

[![LinkedIn Recruiter integration complete](./media/RSCSetupComplete.png)](./media/RSCSetupComplete.png)

## See also

[Post jobs to external sites from Attract](./posting-jobs-external.md)
[Source candidates with LinkedIn Recruiter](./attract-linked-in-recruiter.md)
[Create jobs](./creating-jobs-attract.md)

