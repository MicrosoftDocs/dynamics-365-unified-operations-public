---
# required metadata

title: Create, approve, and sign offers in Attract
description: This topic details how to create, approve, and sign an offer for a candidate using Dynamics 365 Talent - Attract.
author: andreabichsel
manager: AnnBe
ms.date: 02/26/2019
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
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-19
ms.dyn365.ops.version: Talent October 2018 update

---

# Create, approve, and sign offers in Attract

[!include [banner](includes/banner.md)]

In many cases, preparing an offer package for a candidate needs to be a very quick process.
Using the templates set up by the Attract administrator will cut down the time and
effort for the offer creators to prepare and send offers to a candidate.

## Create an offer

When the Offer management app is turned on, any user with the role of hiring manager or recruiter can prepare an offer package for the candidate. To prepare the offer, do the following.

1.  Navigate to the job and the candidate application that you are creating the offer for.

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

1. When all the offer data placeholders are populated, click **Save** to save a draft of the offer.

>[!NOTE]
> After a draft is saved, you can delete the draft version of the offer or select a new package template, if necessary.


## Approve an offer

Most offers need to go through an approval process to make sure the offer meets the necessary standards. If an offer does not meet standards, for example if the offer creator didn't follow the offer data rules and overrode the values in the offer, the approval process will be mandated. To send an offer for approval, do the following.

1.  When the offer is in a draft state, add approvers on the **Approver panel**. 
    >[!NOTE]
    > Hiring Managers are added as approver by default. You can choose any user from your organization as an approver for the offer.

1.  If needed, assign approvers in a sequential approval method or on a parallel approval method. This option will only be available if it was configured as such by the administrator.
    >[!NOTE]
    > If the approval process is sequential, you can edit the sequence of approvers if needed.

1.  When you are done defining the approval chain, you can edit the content of the approval email and then send the notification to the approvers. Click **Send to approvers**.
    >[!NOTE]
    > If the offer was non-standard, you are required to provide a justification.

1.  If the offer creator chooses to skip an approver, they can enter a note and skip to the next approver.

Approvers will receive an email asking them to approve the offer. They can click the link in the email to open the offer, review the
entire offer package, and either approve it or send it back to the offer creator. Offer approvers will need to add an additional note if they are rejecting the offer package for further edits. 

In cases where there is a new version of the offer created before the approver acts, the approver won’t be able to approve or reject the offer.

## Offer versioning 

When the offer has been approved or sent back for further edits, you can choose the **Enable editing** option to create a new version of the offer. The new version of the offer version has all the offer data values and the list of approvers carried over from the last version. 

Approvers can switch between different offer versions if the versions were shared with them for approval. Also, an approver or offer creator can choose to delete a specific draft offer version to go back to the previous state.


## Send an offer to a candidate 

When the offer is saved, approved, and ready to be sent to the candidate, click **Send to candidate**.

There are several actions you can take before sending the offer to the candidate.
-  You can view the list of documents that are part of the offer package that will be sent to the candidate.

-  You can specify an offer expiration date. Candidates are expected to accept or decline the offer before the expiration date.  The candidate will be sent a reminder 48 hours before the offer expires.

-  There may be additional documents that you want to include in the offer acceptance process. You will have the option to list the document type required.

- e-Signature option: There are two ways to connect the e-signature provider of your choice. Go to **User Settings** in **Offer**, under **Connections**, connect to **Adobe Sign** or **DocuSign**. Alternatively, you will be asked to connect the **Send offer to the candidate** page if the connection wasn't already established based on the user settings. The e-signature account only needs to be connected once. The same user license is used for all future offer packages that will be sent out by the same user. 

### Adobe Sign
If Adobe Sign was chosen as the preferred e-sign method, offer creators need to connect their Adobe Sign license at this step. 

### DocuSign
If DocuSign was chosen as the preferred e-sign method, offer creators need to connect their DocuSign license. Once signed in, the default account and permissions associated with the user's DocuSign profile are connected to Talent: Attract. 

-  You can view and edit the email template as needed.

When the offer is ready and you click **Send to candidate**, the candidate will receive an email that an offer is waiting for review.

>[!NOTE]
> If you are using Adobe Sign or DocuSign and you run into an error while sending the offer to the candidate, try disconnecting and reconnecting the e-signature user account from **User Settings**. If the issue persists, please contact our support using the **Report a problem** link.

## Candidate’s actions after receiving an offer

After the candidate has been notified that an offer has been shared with them, they can click the link in their email to go to the application dashboard and view the offer. The dashboard will show the candidate any activities that they still need to complete.

1.  To view the offer and all related documents, the candidate must click **View offer**.

    Candidates can also download the offer package in a .zip format.

1.  To accept the offer, the candidates must click **Jump to signature** for each
    document that’s part of the offer package.

1.  When all of the documents have been individually signed and accepted, the candidate
    must choose to finish the acceptance process by clicking **Accept Offer** at
    the top of the page.

1.  To decline the offer, the candidate must click **Decline the offer** on the top of the page, select an appropriate reason, add a
    comment as necessary, and then click **Decline**.

1.  After they have accepted or declined the offer, the candidate can continue to stay in the offer view or go back to the application dashboard.

1.  If there were other documents requested as part of the offer acceptance process, the candidate should choose to upload the documents as necessary and tag them to the document type requested.

1.  The offer creator will be notified when all the documents have been uploaded and the offer package has been signed.


## Withdrawing an offer

An offer can be withdrawn from a candidate at any point in time for various reasons. 
1.  Withdraw the offer by clicking the ellipsis button (**…**), and then click **Withdraw the offer**. 

2. A message will appear asking whether the candidate has been contacted about the change in status. If the candidate hasn't been contacted yet, you will have the option to send an email to the candidate informing them of further actions. 

   The offer will no longer accessible by the candidate.


## Closing an offer 

When an offer has been accepted, declined, or withdrawn with no further actions needed, you can close the offer so that no further edits can be made to this offer package.
