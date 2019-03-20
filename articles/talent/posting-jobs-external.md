---
# required metadata

title: Posting jobs to external career sites from Attract
description: This topic describes how to post jobs to external career sites from Attract
author: pganapmsft
manager: AnnBe
ms.date: 03/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
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
ms.search.validFrom: 2018-10-18
ms.dyn365.ops.version: AX 7.0.0
---


Posting jobs to external sites from Attract
===========================================

[!include [banner](../includes/banner.md)]

This article provides an overview of the posting jobs to external career site
functionality in Microsoft Dynamics 365 for Talent: Attract. It also explains
how to set up this functionality.

Overview
--------

We understand that hiring teams want to get their open positions in front of as
many qualified candidates as possible. Job sites are one of the key ways to
reach a lot of potential qualified candidates, at scale. Attract provides the
functionality to post jobs to external career sites. We are always looking to
expand the set of partners we support in this area. You will find below the
details about how to setup and post jobs to the partner we currently support

>  [!NOTE]
>
>  -   Posting to external job boards feature is available only with the
>      Comprehensive hiring add-on.
>  -   Some of the integrations below might be in public preview as noted
>      below. To enable an integration in public preview, an admin must turn on
>      the preview options for them. In the Admin center, on the **Feature
>      management** tab, make sure that the **Preview features** option is set
>      to **On**.

Post Jobs Broadbean
-------------------

### Setup Broadbean integration

To set the values for the below items, sign in to Attract as an administrator,
select **Admin center** on the **Settings** menu (the gear symbol), and then
select the **Job board settings** tab.

-   **Enable Broadbean integration:** Please turn this setting on. Once this is
    turned on, you will get to view the below fields for setting up the
    integration.

-   **Username, Client ID, Encryption Token:** Please contact Broadbean and work
    with them to get the values for these 3 settings.

>   [!WARNING] The Broadbean specific credentials are sensitive and
>   confidential. Please store and share them responsibly. Any person having
>   Administrator role in Attract can view these credentials.

>   [!NOTE] Microsoft and Attract just use these values provided here and do not
>   have any direct involvement in creating and maintaining these values. It is
>   the customer’s responsibility to keep these credentials up to date in
>   co-ordination with Broadbean.

### Post a job to Broadbean

After a job is activated, it can be posted. Only recruiters and admins can post
jobs. To post a job to Broadbean, an apply URL must be generated for the job.
Once logged into Attract, open the job that you would like to post to Broadbean
and navigate to the **Postings** section. Select the **Post Now** button
corresponding to the Broadbean item. At this point a new browser tab/window is
opened and Broadbean posting flow is initiated. You can continue to the post the
job to Broadbean through this page. The following information is passed to
Broadbean from Attract.

-   Req ID

-   Job Title

-   Job Description

-   Job Location

-   Apply URL

-   Recruiter information

Once the posting has successfully completed to on the Broadbean side, the
Broadbean item in postings section shows the status as “Posted”.

>   [!NOTE]
>
>   -   Industry is a required field presented in a list format in the Broadbean
>       job post flow. Currently, this is defaulted to “IT” and can be changed
>       to the right industry in the Broadbean job post flow.
>
>    -  The time taken for this status update depends on when Broadbean finished
>       posting to all the job boards the job was posted to. Hence there might
>       be a slight delay between the user finishing posting on Broadbean page
>       and seeing the status updates in Attract.

### View a Broadbean job post

Once a job has been posted to Broadbean, the broadbean page specific to this job
can be viewed from within attract. Once logged into Attract, open the job that
you would like to view on Broadbean and navigate to the **Postings** section.
Select the **…** option corresponding to the Broadbean item and select **View**
to see the Broadbean job posting page. At this point a new browser tab/window is
opened and the Broadbean job posting page is shown.

### Update a Broadbean job post

Once a job has been posted to Broadbean, the job post can be updated in two
scenarios. Firstly if the job data has changed in attract, open the job that you
would like to update on Broadbean, navigate to the **Postings** section and
select the **Update Post** button corresponding to the Broadbean item. This
would take you through the same flow as posting a job to Broadbean. Secondly, if
you would like to change any of the fields specific to Broadbean, follow the
instruction to view a job post posted to Broadbean. Once on the Broadbean page,
you can choose to edit the job details in that page and repost a job. This will
not change the job details or job posting details on the Attract application.

### Remove a Broadbean job post

Once a job has been posted to Broadbean, the job post can be removed from
broadbean. Open the job that you would like to remove from Broadbean, navigate
to the **Postings** section and select the **…** option corresponding to the
Broadbean item and select **Remove Post.** This would trigger an action to
remove the job post from Broadbean and the **Post Now** button is displayed
corresponding to the Broadbean item indicating that the job has be removed, but
can be posted again.

### Troubleshooting Broadbean integration

If one or more scenarios above does not work as described, please follow the
steps below.

1.  Please verify that the Broadbean credentials entered in Attract are valid
    and correct.

2.  If the credentials are valid and correct, please contact [Broadbean
    support](https://www.broadbean.com/resources/support/)

3.  If the above steps do not help resolve the issue, please contact [Microsoft
    support.](./talent-support#talent-support--attract-and-onboard)
