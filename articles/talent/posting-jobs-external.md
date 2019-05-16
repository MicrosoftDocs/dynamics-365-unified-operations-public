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

You want to get your open positions in front of as many qualified candidates as possible. Recruiting sites such as Broadbean help you accomplish this goal. Microsoft Dynamics 365 Talent: Attract now lets you post jobs to Broadbean, and Microsoft is constantly providing new offerings in this area.

## Post jobs to Broadbean

Before you can post jobs to Broadbean, you must configure the Broadbean integration.

> [!NOTE]
> - To post jobs to external sites, you must have the [Comprehensive hiring add-on](https://docs.microsoft.com/dynamics365/unified-operations/talent/attract-comprehensive-hiring).
> - To post jobs to Broadbean through Attract, you must have a Broadbean subscription.
> - This feature is currently in preview. If you want to try it, you must [turn it on in the Attract admin settings](https://docs.microsoft.com/dynamics365/unified-operations/talent/access-preview-feature).

### Configure Broadbean integration

1. Sign in to Attract as an admin.
2. Select the **Settings** button (the gear symbol) in the upper-right corner of the page, and then select **Admin center**.
3. On the **Job board settings** tab, in the **Enable Broadbean integration** section, turn on the integration.
4. Contact Broadbean, and enter your information in **Username, Client ID, Encryption Token**.

> [!WARNING]
> Your Broadbean credentials are sensitive and confidential. Therefore, store and share them responsibly. Anyone who has an Administrator role in Attract can view these credentials.

> [!NOTE]
> Microsoft and Attract aren't involved in creating and maintaining these values. It's your responsibility to keep them up to date in Attract and to work with Broadbean to resolve any issues that involve your credentials.

### Post a job to Broadbean

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
2. In the **Postings** section, select the ellipsis button (**...**) that corresponds to Broadbean, and then select **View**.

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

### Troubleshoot the Broadbean integration

If you're having trouble posting a job to Broadbean, try these steps.

1. Verify that the Broadbean credentials that you entered in Attract are valid and correct.
2. If the credentials are valid and correct, contact [Broadbean support](https://www.broadbean.com/resources/support/).
3. If the issue persists, contact [Microsoft support](./talent-support.md).
