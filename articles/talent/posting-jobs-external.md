---
# required metadata

title: Post jobs to Broadbean from Attract
description: This topic explains how to use Dynamics 365 Talent - Attract to post jobs to Broadbean
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
# ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-03-19
ms.dyn365.ops.version: Platform update 24
---


# Post jobs to Broadbean from Attract

[!include [banner](includes/banner.md)]

Microsoft Dynamics 365 Talent: Attract helps you get the talent you need by letting you post your jobs directly from Attract to Broadbean. After you [create a job](./creating-jobs-attract.md), all you have to do is click a button to put your job in front of all the potential job candidates on Broadbean.

Posting jobs to Broadbean requires an appropriate Broadbean license. Broadbean offers various products and plans. For more information about Broadbean licensing and pricing, [contact Broadbean](https://www.broadbean.com/contact-us/).

If you're an admin who needs more information about how to configure Broadbean integration with Attract, see [Enable Broadbean integration in Microsoft Dynamics 365 Talent - Attract](./attract-admin-job-board-settings.md).

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

If you're having trouble posting a job to Broadbean, try these steps.

1. Verify that the Broadbean credentials that you entered in Attract are valid and correct.
2. If the credentials are valid and correct, contact [Broadbean support](https://www.broadbean.com/resources/support/).
3. If the issue persists, contact [Microsoft support](./talent-support.md).

## See also

[Create, approve, and post jobs in Attract](./creating-jobs-attract.md)

[Enable Broadbean integration in Microsoft Dynamics 365 Talent - Attract](./attract-admin-job-board-settings.md)
