---
# required metadata

title: Vendor collaboration mobile workspace
description: With the vendor collaboration mobile workspace, your vendors can stay up-to-date on the purchase orders that have been sent to them for approval and view information about new and updated purchase orders and contacts.
author: mkirknel 
manager: AnnBe
ms.date: 06/16/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 267074
ms.assetid: 1d293b3a-2fa2-418d-9347-78c2809d67fe
ms.search.region: global
# ms.search.industry: 
ms.author: mkirknel
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Vendor collaboration mobile workspace

[!include[banner](../includes/banner.md)]


This topic provides information about the **Vendor collaboration** mobile workspace. With this mobile workspace, your vendors can stay up-to-date on the purchase orders that have been sent to them for approval and view information about new and updated purchase orders and contacts.

This mobile workspace is for use with the Microsoft Dynamics 365 for Unified Operations mobile app.

## Overview 
The **Vendor collaboration** mobile workspace keeps vendors informed about new purchase orders so that they can see and respond to purchase orders in the web client. 

>[!NOTE]
> The mobile workspace should be used as a supplement to the vendor collaboration web interface, but not a replacement. 

With the **Vendor collaboration** mobile workspace, your vendors can view new purchase orders that are sent for approval. It displays purchase order information, such as products, quantity, and requested delivery dates. Price information is available, depending on the configuration for each vendor. 

When a user logs in as a vendor, they will see which purchase orders have been responded to, or which purchase orders are still awaiting customer action. The vendor might have suggested another delivery date that is not yet agreed with the customer so the purchase order is awaiting customer action. The vendor will also see a list of purchase orders that are confirmed but not yet delivered. 

To respond to a purchase order, the vendor has to use the vendor collaboration web interface that is available in the Dynamics 365 for Operations web client. This is also where the vendor will get more information about the order, such as document attachments, delivery address per line, and charges that are associated with the vendor. 

With a special security role, the vendor can view which contact persons are registered for a vendor account. With the same security role, the vendor can view the status of any user request that has been submitted. 

Creating new contacts and submitting new user requests must be done in the vendor collaboration interface that is available in the Dynamics 365 for Operations web client. 

With the mobile workspace, your vendor can:

-   View new purchase orders sent to the vendor.
-   View purchase orders that the vendor has responded to and are awaiting customer action.
-   View purchase orders that are in a confirmed state and have not been fully received.
-   View contact person information that is registered for the vendor account (requires an additional security role).
-   View information and follow the status of a user request submitted by the vendor (requires an additional security role).

## Prerequisites
The prerequisites differ, based on the version of Microsoft Dynamics 365 that has been deployed for your organization.

### Prerequisites if you use Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update 
If Microsoft Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update has been deployed for your organization, the system administrator must publish the **Vendor collaboration** mobile workspace. For instructions, see [Publish a mobile workspace](/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace).

### Prerequisites if you use Microsoft Dynamics 365 for Operations version 1611 with platform update 3 or later
If Microsoft Dynamics 365 for Operations version 1611 with platform update 3 or later has been deployed for your organization, the system administrator must complete the following prerequisites. 

<table>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Role</th>
<th>Description</th>
</tr>
</thead>
<tbody>

<tr class="odd">
<td>KB 3216943 must be implemented if you are using platform update 3.</td>
<td>System administrator</td>
<td>KB 3216943 is a binary update that is required if you are using platform update 3. To implement this KB, the system administrator must:
<ol>
<li>Download KB 3216943 from Microsoft Dynamics Lifecycle Services (LCS).</li>
<li>Install the binary update, which is delivered as a deployable package. For instructions on how to apply a deployable package see <a href="/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system">Apply a deployable package</a>.</li>
</ol></td>
</tr>
<tr class="even">
<td>KB 4013633 must be implemented.</td>
<td>System administrator</td>
<td>KB 4013633 is an X++ update or metadata hotfix that contains the <strong>Inventory on-hand</strong> mobile workspace. To implement KB 4013633, your system administrator must follow these steps.
<ol>
<li><a href="/dynamics365/operations/dev-itpro/migration-upgrade/download-hotfix-lcs">Download the metadata hotfix from Microsoft Dynamics Lifecycle Services (LCS)</a>.</li>
<li><a href="/dynamics365/operations/dev-itpro/migration-upgrade/install-metadata-hotfix-package">Install the metadata hotfix</a>.</li>
<li><a href="/dynamics365/operations/dev-itpro/deployment/create-apply-deployable-package">Create a deployable package</a> that contains the <strong>SCMMobile</strong> model, and then upload the deployable package to LCS.</li>
<li><a href="/dynamics365/operations/dev-itpro/deployment/apply-deployable-package-system">Apply the deployable package</a>.</li>
</ol></td>
</tr>
<tr class="odd">
<td>The <strong>Vendor collaboration</strong> mobile workspace must be published.</td>
<td>System administrator</td>
<td>See <a href="/dynamics365/operations/dev-itpro/mobile-apps/publish-mobile-workspace">Publish a mobile workspace</a>.</td>
</tr>
<tr class="even">
<td>The vendor user must have access to the vendor collaboration web interface in Dynamics 365 for Operations and set up a vendor collaboration user.</td>
<td>Purchasing professionals and the system administrator</td>
<td>Follow the steps described in the following topics to set up and work with the vendor collaboration web interface.
<ul>
<li><a href="https://ax.help.dynamics.com/en/wiki/using-vendor-collaboration-to-work-with-external-vendors/">Use vendor collaboration to work with external vendors</a></li>
<li><a href="https://ax.help.dynamics.com/en/wiki/manage-vendor-collaboration-users/">Manage vendor collaboration users</a></li>
<li><a href="https://ax.help.dynamics.com/en/wiki/set-up-and-maintain-vendor-collaboration/">Set up and maintain vendor collaboration</a></li>
<li><a href="https://ax.help.dynamics.com/en/wiki/using-vendor-collaboration-to-work-with-customers-in-dynamics-365-for-operations/">Use vendor collaboration to work with customers in Dynamics 365 for Operations</a></li>
</ul></td>
</tr>
</tbody>
</table>

## Download and install the mobile app

Download and install the Dynamics 365 for Unified Operations mobile app:

-   [For Android phones](https://go.microsoft.com/fwlink/?linkid=850662)
-   [For iPhones](https://go.microsoft.com/fwlink/?linkid=850663)


## Sign in to the Dynamics 365 for Operations mobile app
1.  Start the app on your mobile device.
2.  Enter your Dynamics 365 for Operations URL.
4.  The first time that you sign in, you’re prompted for the user name and password for your Dynamics 365 for Operations account. Enter your credentials.
5.  After you sign in, you see the available workspaces for your company. Note that if your system administrator later publishes a new workspace, you can pull to refresh the list of mobile workspaces. 

    [![Pull to refresh](./media/pull-to-refresh-list-of-workspaces-183x300.png)](./media/pull-to-refresh-list-of-workspaces.png)

## Use the Vendor collaboration mobile workspace
When you select the **Vendor collaboration** workspace, you’ll see the following options:

    [![Vendor collaboration mobile workspace](./media/vendor-collaboration-mobile-app.png)]

The **Vendor collaboration** workspace includes the following pages:

## Contacts
The **Contacts** page lets you see all the contacts that have been set up for the vendor account. It shows the contact person name, primary email, and the users alias, if available. It also shows whether the contact person's user account is active. When you select a contact, you see contact details, such as which legal entities the person is a contact for, and contact information such as phone number or a different email address.

### User requests
The **User requests** page lets you see all the user requests that you have submitted via the vendor collaboration web interface and follow the status. When you select a user request, you can see what was requested, add or inactivate a user, change security, and see which security roles were requested for the user.

### Purchase orders ready for review
The **Purchase orders ready for review** page lets you see all the purchase orders that were sent by the customer and have not been answered. You can view selected information about the order, such as which products have been requested and when to deliver. Price information is only available if this is configured for the vendor. You can see whether the purchase order has notes or attachments. To open attachments, you need to use vendor collaboration in the web client. Select **Purchase order line** to see all the lines with details. Note that for each line, an indicator will show whether there are notes or attachments or if there's a delivery address that's different than what's shown on the header. To respond to the purchase order, you must use the vendor collaboration web client.

### Awaiting customer action
The **Awaiting customer action** page lets you find purchase orders that you, or someone in your company who also has access to vendor collaboration, have responded to. The purchase orders are only visible in this list if the customer needs to perform one of the following actions on the purchase order.

-   If the purchase order was rejected, the customer would either need to update the sent order and send again, or cancel the order and resend. When the purchase order is sent again, it will disappear from the **Awaiting customer action** page.
-   If the purchase order was accepted with changes, the customer would need to update the original order and resend for review, or update it according to the changes and confirm it immediately. In both cases, the purchase order will disappear from the **Awaiting customer action** page.
-   If the purchase order was accepted and appears in the **Awaiting customer action** page, it is because the purchase order was not automatically confirmed when the acceptance was done. It is waiting for a purchasing agent to change the order to Confirmed. Typically, the purchase order would be regarded as an agreement between the customer and vendor as soon as the vendor accepts the order. Moving the purchase order to the Confirmed state would be a formality.

By selecting the purchase order, additional details appear about the response. You can see the line details and response for every line. The line status shows which of the following responses has been given.

-   Accepted
-   Rejected
-   Accepted with changes
-   Substituted/Substitute
-   Split into schedule/Schedule line

Note that an indicator shows **Delivering**=yes/no, which is used to indicate that the lines will not be delivered. This could be because the line was rejected, or substituted where the original lines are not expected to be delivered, or a line that has been split into multiple schedule lines and the original line is not expected to be delivered as requested in the received order. Any changes made to the order line response are displayed, except for the uploaded notes and attachments, which you can see by using the vendor collaboration web interface.

### Open confirmed orders
When the purchase order is confirmed by the customer, which means the purchase order is changed to the Confirmed state, it will appear in the open confirmed order. It will stay in the list until it is registered as received by the customer.




