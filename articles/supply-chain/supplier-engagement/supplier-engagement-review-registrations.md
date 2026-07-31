---
title: Review and approve incoming vendor registrations (preview)
description: Review incoming supplier registration requests and approve or reject them to start onboarding in the Supplier Engagement app.
author: ShriramSivasankaran
ms.author: shriramsiv
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 07/27/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Review and approve incoming vendor registrations (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Prospective suppliers can use the supplier portal to submit a supplier registration request, even without an invitation. Before a prospective supplier can access the supplier portal, authorized internal users must use the Supplier Engagement app to review and approve the supplier's registration request. During review, you can assess the submitted organization details, move requests into review, and decide whether to approve or reject them. Approval starts global vendor creation and onboarding activities.

<a name='open-request'></a>

## View new registration requests in the Supplier Engagement app

Internal users such as global vendor managers and procurement professionals can access registration requests. Each request typically shows key details such as supplier name, contact information, company type, country or region, status, owner, and submission date.

To open the list of submitted requests, follow these steps:

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Menu** area.
1. On the navigation pane, select **Portal registrations** \> **Registration requests**.
1. Use the search field, column filters, sorting options, view selector, and other tools to find the request that you want to review. You might often want to use the view selector or filter by **Status Reason** to focus on requests that are in one of the following states:
    - *New* – Recently submitted requests that are waiting for action
    - *In review* – Requests that are currently being assessed
    - *Approved* – Accepted requests that triggered vendor creation and onboarding
    - *Rejected* – Declined requests that won't move forward
1. Open the registration request that you want to inspect.

## Start reviewing a request

When a prospective supplier first submits a registration, its **Status Reason** is *New*. Move the request to *In review* when you're ready to begin evaluation.

1. [Find and open the registration request](#open-request) that you want to review. It should have a **Status Reason** of *New*.
1. On the command bar, select **Review**.
1. In the confirmation dialog box, select **OK**.

After you complete these steps, the **Status Reason** changes from *New* to *In review*.

## Reject a registration request

If the submitted information doesn't meet your organization's requirements, you can reject the request and stop the onboarding process.

1. [Find and open the registration request](#open-request) that you want to review. It should have a **Status Reason** of *In review*.
1. On the command bar, select **Reject**.
1. In the confirmation dialog box, select **OK**.

After the request is rejected, the **Status Reason** changes to *Rejected*, and the supplier is notified by email that the application wasn't approved.

## Approve a registration request

Approve the request when the supplier should move forward into onboarding and vendor creation.

1. [Find and open the registration request](#open-request) that you want to review. It should have a **Status Reason** of *In review*.
1. On the command bar, select **Approve**.
1. In the confirmation dialog box, select **OK**.
1. The [system checks for duplicate records](supplier-engagement-duplicate-global-vendors.md) to make sure that it doesn't create overlapping supplier data. It looks for existing global vendor records that match the registration by name, website, or primary email. It also checks for existing contact records that use the same primary email address. If the system finds a possible duplicate, it informs you and blocks the approval until you review the existing global vendor data and decide how to proceed.

When approval succeeds, the system completes several actions automatically to start the supplier onboarding flow:

- The registration request **Status Reason** changes to *Approved*.
- The registration contact receives an email that confirms approval.
- A new global vendor record is created with a **Status Reason** of *Prospect*.
- A contact record is created and linked to the global vendor as the primary contact.
- The primary contact's portal access status is set to *Invited*, and prospective user provisioning starts.
- The primary contact is assigned the *Global Vendor Admin* role, and a *Portal User* request is generated in Supply Chain Management.
- After user provisioning finishes, the supplier's primary contact receives onboarding instructions by email.

## Related information

- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)
