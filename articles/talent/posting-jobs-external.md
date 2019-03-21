---
# required metadata

title: Post jobs to external career sites from Attract
description: Use Dynamics 365 for Talent: Attract to post jobs to external recruiting sites
author: pganapmsft
manager: AnnBe
ms.date: 03/20/2019
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


# Post jobs to external sites from Attract

[!include [banner](../includes/banner.md)]

You want to get your open positions in front of as many qualified candidates as possible. Recruiting sites like Broadbean help you accomplish this goal. Microsoft Dynamics 365 for Talent: Attract now lets you post jobs to Broadbean, and we're constantly providing new offerings in this area. 

## Post jobs to Broadbean

Before you can post jobs to Broadbean, you need to configure Broadbean integration.

> [!NOTE]
>
> - You need the [Comprehensive hiring add-on](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/attract-comprehensive-hiring) to post jobs to external sites.
> - This feature is currently in preview. If you want to try it out, please [enable it in Attract's **Admin settings**](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/access-preview-feature).

### Configure Broadbean integration

1. Sign in to Attract as an administrator.

2. Select **Settings** > **Admin center** > **Job board settings**.

3. Turn on integration in **Enable Broadbean integration:**.

4. Contact Broadbean and enter your information in **Username, Client ID, Encryption Token:**.

> [!WARNING] Your Broadbean credentials are sensitive and confidential. Please store and share them responsibly. Anyone who has an Administrator role in Attract can view these credentials.

> [!NOTE] Microsoft and Attract aren't involved in creating and maintaining these values. It's your responsibility to keep them up to date in Attract and to work with Broadbean for any issues with your credentials.

### Post a job to Broadbean

Recruiters and admins can post a job to Broadbean after activating it. You will need an apply URL for the job.

1. In Attract, open the job you want to post to Broadbean.

2. In **Postings**, select the **Post Now** button that corresponds to Broadbean. Follow the instructions in the pop-up window.

Attract passes the following information to Broadbean:

- Req ID

- Job Title

- Job Description

- Job Location

- Apply URL

- Recruiter information

When Broadbean successfully completes the posting, the **Postings** section in the Attract job displays the Broadbean status as **Posted**.

> [!NOTE]
>
> - Broadbean requires the **Industry** field. It currently defaults to **IT**, but you can change it to the correct industry in the Broadbean job post pop-up window.
>
> - It takes some time for Broadbean to finish posting your job to all of the job boards you selected, so there might be a slight delay before Attract provides a status update for the job. 

### View a Broadbean job post

After you post a job to Broadbean, you can view it from within Attract.

1. In Attract, open the job you want to view on Broadbean.

2. In **Postings**, select the **...** option that corresponds to Broadbean, and then select **View**. 

The Broadbean job posting appears in a new window.

### Update a Broadbean job post

You can update a Broadbean job two ways:

1. Open the job you want to update.

2. In **Postings**, select the **Update Post** button that corresponds to the Broadbean item. Edit your posting in the pop-up window.

- or -

1. Open the job you want to view on Broadbean.

2. In **Postings**, select the **...** option that corresponds to Broadbean, and then select **View**. On the Broadbean page, edit the job details and repost the job. This won't change the job details in Attract.

### Remove a Broadbean job post

You can remove a job post from Broadbean when needed.

1. In Attract, open the job you want to remove.

2. In **Postings**, select the **...** option that corresponds to Broadbean, and then select **Remove Post**.

After Broadbean removes the job, the Broadbean item in Attract displays the **Post Now** button, indicating the job has been removed and can be posted again.

### Troubleshooting Broadbean integration

If you're having trouble posting a job to Broadbean, please try the following:

1.  Verify the Broadbean credentials entered in Attract are valid and correct.

2.  If the credentials are valid and correct, contact [Broadbean support](https://www.broadbean.com/resources/support/).

3.  If you still have a problem, contact [Microsoft support](./talent-support#talent-support--attract-and-onboard).
