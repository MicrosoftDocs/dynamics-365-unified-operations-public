---
title: Global vendor onboarding lifecycle (preview)
description: Understand lifecycle stages for global vendors and learn how status changes affect onboarding and Supply Chain Management.
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

# Global vendor onboarding lifecycle (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Global vendor onboarding lifecycle management helps you move suppliers from early prospecting through qualification, approval, and end-of-relationship decisions. Each lifecycle stage reflects the vendor's current readiness, compliance standing, and operational status. The lifecycle also controls when data is synchronized to Supply Chain Management and when portal access is allowed.

## Lifecycle stages overview

Global vendors move through lifecycle stages as onboarding and review activities progress.

| Status reason | Supplier Engagement app | Supply Chain Management |
|---|---|---|
| *Prospect* | Initial vendor record is created manually or through registration and is used for onboarding and data collection. | No vendor record exists in Supply Chain Management. Data is stored only in Dataverse. |
| *Qualified* | Vendor has passed initial validation and due diligence and is ready for release to legal entities. | A global vendor party record is created in Supply Chain Management. Contact methods, contact person relationships, and addresses are synchronized. |
| *Approved* | Vendor has met all compliance, risk, and performance criteria and is considered a preferred vendor. | Vendor is ready for transactional use and can be released to legal entities as a local vendor. |
| *Disqualified* | Vendor failed onboarding or due diligence, and the record is made inactive. Portal access is blocked. | No vendor record is created in Supply Chain Management. |
| *Disapproved* | Vendor failed to meet performance or compliance standards after qualification and can be reactivated to qualified status. | The vendor record is marked as disapproved. Portal access is blocked. |
| *Terminated* | The vendor relationship is formally ended, the record is blocked, and access is revoked. The status can't be reactivated. | The vendor and related parties are placed on hold. Portal access is blocked. |

## Status change tracking

The system logs each lifecycle status change so you can review how and why a vendor moved to a new state. To see this information, [open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record) and go to the **Lifecycle** tab. Tracked values include the following details:

- **Status reason** – The status that was applied
- **Last updated by** – The user who made the change
- **Last updated on** – The date and time of the change
- **Status change comments** – The comment that explains the change

## Qualify or disqualify a global vendor

You can qualify or disqualify a vendor when it's in *Prospect* status. Qualification confirms that the vendor has passed initial validation and due diligence, while disqualification indicates that the vendor failed onboarding or due diligence. When you qualify a vendor, key data synchronizes to Supply Chain Management, as shown in the following table.

| Data category | Information synchronized to Supply Chain Management |
|---|---|
| Basic information | Name, status, global vendor hold, and feedback level |
| Contact methods | Primary email address, primary phone number, primary URL, and additional contact methods |
| Addresses | Primary address and any additional addresses, including purpose and country/region-specific formatting |
| Contacts | Contact person party relationships and their corresponding contact methods |
| Company details | Number of employees, organization number, and DUNS number |
| Portal access | If portal access is enabled, the portal user for the primary contact is mapped to the synchronized contact person in Supply Chain Management, and the user's role changes from *Prospective User* to *Supplier Portal Administrator* |

To qualify a prospect, follow these steps.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record), which must have *Prospect* status.
1. On the command bar, select **Qualify**.
1. In the confirmation dialog box, enter a comment.
1. Select **OK**.

When you qualify the vendor, the status changes to *Qualified*, a global vendor party is created in Supply Chain Management, and supported data is transferred.

To disqualify a prospect, follow these steps.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record), which must have *Prospect* status.
1. On the command bar, select **Disqualify**.
1. In the confirmation dialog box, enter a comment.
1. Select **OK**.

When you disqualify the vendor, the status changes to *Disqualified*, the record becomes inactive, portal access is blocked, and all portal roles are removed.

## Approve or disapprove a global vendor

You can approve or disapprove a vendor after the vendor reaches *Qualified* status. Approval confirms that the vendor has passed all required assessments. Disapproval blocks further use until the issue is resolved.

To approve a qualified vendor, follow these steps:

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record), which must have *Qualified* status.
1. On the command bar, select **Approve** \> **Approve**.
1. Confirm the operation and enter a comment to explain why you approved the vendor.
1. Select **OK**.

When you approve the vendor, the status changes to *Approved*, and the vendor becomes eligible for release to legal entities.

To disapprove a qualified vendor, follow these steps:

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record), which must have *Qualified* status.
1. On the command bar, select **Approve** \> **Disapprove**.
1. Select the required hold type and reason code.
1. Enter any comments that are needed.
1. Confirm the action.

When you disapprove the vendor, the status changes to *Disapproved*, the record becomes inactive, portal access is blocked, a vendor hold is applied, and the update synchronizes to Supply Chain Management.

## Request and approve global vendor termination

Termination uses a two-step process where one user requests the action and an authorized user approves it.

### Request termination

You can request termination when a vendor is in *Qualified* or *Approved* status.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record), which must have *Qualified* or *Approved* status.
1. On the command bar, select **Terminate Request**.
1. Enter a comment that explains why termination is requested.
1. Confirm the action.

After you submit the request, **Terminate Review** is set to *Initiated*. You can see this information on the **Lifecycle** tab of the global vendor record, in the **Termination details** section. The termination request is sent to an authorized user for review and approval.

### Approve termination

An authorized user completes the termination review and applies the final status.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record), which must have a pending termination request.
1. Review the request details and comments.
1. On the command bar, select **Terminate** \> **Approve** to approve the termination request. Select **Terminate** \> **Disapprove** to reject the request.

When you approve the termination request, **Status reason** updates to *Terminated*, the record becomes inactive, a vendor hold is applied to all local vendors, portal access is blocked, and all portal roles are removed.

If you disapprove a termination request, **Status reason** remains *Approved*, and the record remains active. On the **Lifecycle** tab, the **Termination details** section shows that the request was disapproved and includes any comments that you entered.

> [!IMPORTANT]
> You can't reactivate a terminated vendor. If you want to work with the supplier again, you must start a new onboarding process.

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Global vendor contacts](supplier-engagement-global-vendor-contacts.md)
- [Global vendor feedback](supplier-engagement-global-vendor-feedback.md)
- [Risk management and corrective actions](supplier-engagement-risk-corrective-actions.md)
- [Manage local vendors](supplier-engagement-manage-local-vendors.md)
