---
# required metadata

title: Creating, approving, and signing offers
description: This topic details how to create, approve, and sign an offer for a candidate using Dynamics 365 for Talent.
author: 
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
ms.reviewer: josaw
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2018-10-19
ms.dyn365.ops.version: Talent October 2018 update

---

# Creating, approving, and signing offers

[!include[banner](../includes/banner.md)]

In many cases, preparing an offer package for a candidate needs to be a very quick process.
Using the templates set up by the Attract administrator will cut down the time and
effort for the offer creators to prepare and send offers out to a candidate.

## Create an offer

When the Offer management app is turned on, any user with the role of hiring manager or recruiter can prepare an offer package for the candidate. To prepare the offer, do the following.

1.  Navigate to the job and the candidate application you are creating the offer for.

1.  Go to **Offer stage** and click **Prepare offer**.

    You will be redirected to the Offer app where you can see the candidate with the status of **New**. You can also see other offers that you are contributing to, either as a creator or an approver.

1.  Click **Prepare Offer**. 
    
    You will see a choice of different offer packages that have been made available by the administrator.

1.  Select a package and click **Done** to start preparing the offer.

    The offer package template loads with the corresponding job and candidate details populated in the offer.

1.  All the offer data placeholders that are part of the offer package are visible in the landing page. You can populate
    all the values across the package on this page.

    On the landing page, you can also see all the offer document templates that are part of the offer package.

1.  You may now be able to edit the content of the offer, depending on how the template was configured by the administrator.

1.  If you need to remove documents marked as non-required, you can do so.

1. Once all the offer data placeholders are populated, you can click **Save** to save a draft of the offer.

>[!NOTE]
> After a draft is saved, you can delete the draft version of the offer or select a new package template, if necessary.


## Approve an offer

Most offers need to go through an approval process to make sure it meets the
necessary standards. If an offer were made non-standard, i.e., the offer creator
did not follow the offer data rules and overrode the values in the offer, the
approval process is mandated. Steps to send an offer for approval:

1.  When the offer is in a draft state, use the **approver panel** on the screen
    to add approvers. **Hiring Managers are added as approver by default**. You
    can choose any user from your organization as an approver for the offer.

2.  Depending on the approval configuration by the admin, you can have approvers
    in a sequential or on a parallel approval method.

3.  If the approval process is sequential, you can choose to edit the sequence
    of approvers

4.  Once the approval chain is identified, click **Send to approvers**

5.  If the offer was non-standard, the offer creators needs to justify the
    non-standard nature of the offer.

6.  You can now edit the content of the approval email and send the notification
    out to the approvers.

7.  The offer creator is returned If the recruiter chooses to **skip an
    approver**, they can record a note and skip them to the next approver.

Next-up, the approvers will receive an email for them to approve the offer. They
can click the link in the email to open the offer approver view, look at the
entire offer package and approve or send the offer back to the offer creator.
Offer approvers also need to add an additional note if the offer package was
being rejected for further edits. If the offer creator had created a new version
of the offer before the approver could act, they won’t be able to approve or
reject the offer.

Offer versioning 
-----------------

Once the offer has been approved or sent back to make further edits, offer
creator can choose the **Enable editing** option to create a new version of the
offer. The new offer version has all the offer data values and the list of
approvers carried over from the last version. Users can switch back and forth
between different offer versions if they are the creator or as an approver, that
version was shared with them for approval. Users can also choose to **delete a
specific draft offer version** to go back to the previous state.

Send offer to candidate 
------------------------

When the offer is saved and approved and ready to be sent to the candidate, the
offer creator can click **Send to candidate**.

1.  You can view the list of documents that are part of the offer package that
    will be sent to the candidate.

2.  You can also specify an offer expiration date at this point. Candidates are
    expected to accept or decline the offer before the end of expiration date.
    They will be given a reminder 48 hours before the offer expires.

3.  There maybe additional documents that you may want as part of the offer
    acceptance process. Choose this step to list the document type required.

4.  Lastly, you can view and edit the email template as necessary for candidates
    to view.

5.  When ready, click Send to Candidate. At this point, the candidate receives
    an email that an offer is waiting for them!

Candidate’s offer actions 
--------------------------

Once the candidate has been notified that the offer has been shared with them,
they can click the link in their email and go to their application dashboard and
view the offer.

1.  They can view the application dashboard for their incomplete activities.

2.  To view the offer, candidate can choose the View offer option to go the
    offer package view. They can read through all the offer package documents

3.  Candidates are also able to download the offer package in a zip format.

4.  To accept the offer, candidates can click **Jump to signature** for each
    document that’s part of the offer package.

5.  Once all the documents have been individually signed and accepted, candidate
    can choose to finish the acceptance process by clicking **Accept Offer** at
    the top of the screen.

6.  If the candidate chooses to decline the offer, candidate can click **Decline
    the offer** button on the top and select an appropriate reason, add a
    comment as necessary and click Decline.

7.  Once they have accepted or declined the offer, they can continue to stay on
    the offer view or get back to the application dashboard.

8.  If there were other documents requested as part of the offer acceptance
    process, candidate can choose to **upload documents** as necessary and tag
    them to the document type requested.

9.  Once all the documents have been uploaded and the offer package signed,
    offer creator has been notified of the candidate accepting or declining the
    offer.

Withdrawing an offer
--------------------

An offer can be withdrawn from a candidate at any point in time for various
reasons. Offer creators can choose to withdraw the offer by using the option
under **…** options and clicking **Withdraw the offer**. Offer creators is given
an option whether they have already contacted the candidate about this change in
status. If they hadn’t contacted the candidate yet, they can send an e-mail to
the candidate informing them of further actions. The offer will no longer
accessible by the candidate.

Closing an offer 
-----------------

Once an offer has been accepted, declined or withdrawn with no further actions
needed, offer creator can choose to **close the offer** so that no further edits
can be made to this offer package.
