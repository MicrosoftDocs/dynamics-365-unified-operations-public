---
# required metadata

title: Post jobs to external career sites from Attract
description: This topic explains how to use Dynamics 365 for Talent - Attract to post jobs to external recruiting sites
author: pganapmsft
manager: AnnBe
ms.date: 05/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-03-19
ms.dyn365.ops.version: Platform update 24
---


# Post jobs to external career sites from Attract

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 for Talent: Attract helps you get the talent you need by letting you post your jobs to external sites directly from Attract. After you [create a job](./creating-jobs-attract.md), all you have to do is push a button to put your job in front of thousands of potential candidates.


## Post jobs to LinkedIn

1. In Attract, open the job that you want to post to LinkedIn.
2. On the **Postings** tab, select the **Post Now** button that corresponds to LinkedIn.
[![Attract post job to LinkedIn](./media/attract-post-job-to-linkedin.png)](./media/attract-post-job-to-linkedin.png)
3. In the **Create an "Apply now" web address** window, select an option under **Candidates can apply using a**. We recommend you select **Link in Attract**.
4. Select **Done**.
5. In the **Submit for posting** window, select **Confirm**.

After LinkedIn successfully completes the posting, the **Postings** section of the job in Attract shows the LinkedIn status as **Posted**.

It can take up to 24 hours for your job to appear in LinkedIn. All job postings done with attract are Limited Listings. For more information about Limited Listings in LinkedIn, see [Limited Listings vs Premium Job Slots for Job Wrapping](https://www.linkedin.com/help/recruiter/answer/79049).

### Troubleshoot job posting to LinkedIn

If you're having trouble posting a job to LinkedIn, try these steps:

1. Verify that the LinkedIn credentials that you entered in Attract are valid and correct.
2. If the credentials are valid and correct, contact [LinkedIn support](https://www.linkedin.com/help/linkedin).
3. If the issue persists, contact [Microsoft support](./talent-support.md).


## Post jobs to Broadbean

After Broadbean has been turned on, recruiters and admins can post a job to it. You must have an apply URL for the job.

1. In Attract, open the job that you want to post to Broadbean.
2. In the **Postings** section, select the **Post Now** button that corresponds to Broadbean.
3. Follow the instructions in the Broadbean window.

Attract passes the following information to Broadbean:

- Request ID
- Job title
- Job description
- Job location
- Apply URL
- Recruiter information

After Broadbean successfully completes the posting, the **Postings** section of the job in Attract shows the Broadbean status as **Posted**.

> [!NOTE]
> - Broadbean requires the **Industry** field. Currently, this field is set to **IT** by default. However, you can change the value to the correct industry in the window for Broadbean job posting.
> - It takes some time for Broadbean to finish posting your job to all the job boards that you selected. Therefore, there might be a slight delay before Attract provides a status update for the job.

### View a Broadbean job posting

After you post a job to Broadbean, you can view it from Attract.

1. In Attract, open the job that you want to view on Broadbean.
2. On the **Postings** tab, select the ellipsis button (**...**) that corresponds to Broadbean, and then select **View**.

The Broadbean job posting appears in a new window.

### Update a Broadbean job posting

You can update a Broadbean job posting in two ways.

1. In Attract, open the job that you want to update.
2. In the **Postings** section, select the **Update Post** button that corresponds to Broadbean.
3. Edit the posting in the Broadbean window.

–or–

1. In Attract, open the job that you want to view on Broadbean.
2. In the **Postings** section, select the ellipsis button (**...**) that corresponds to Broadbean, and then select **View**.
3. In the Broadbean window, edit the job details, and then repost the job. The job details in Attract aren't changed.

### Remove a Broadbean job posting

You can remove a job posting from Broadbean as you require.

1. In Attract, open the job that you want to remove.
2. In the **Postings** section, select the ellipsis button (**...**) that corresponds to Broadbean, and then select **Remove Post**.

After Broadbean removes the job, the Broadbean item in Attract has a **Post Now** button. The presence of this button indicates that the job has been removed and can be posted again.

### Troubleshoot job posting to Broadbean

If you're having trouble posting a job to Broadbean, try these steps:

1. Verify that the Broadbean credentials that you entered in Attract are valid and correct.
2. If the credentials are valid and correct, contact [Broadbean support](https://www.broadbean.com/resources/support/).
3. If the issue persists, contact [Microsoft support](./talent-support.md).

## See also

[Set up integration with LinkedIn](./attract-admin-linkedin.md)<p></p>
[Create jobs](./creating-jobs-attract.md)
