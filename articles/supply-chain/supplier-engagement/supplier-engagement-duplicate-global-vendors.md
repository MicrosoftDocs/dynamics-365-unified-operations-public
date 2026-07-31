---
title: Detect and manage duplicate global vendors (preview)
description: Detect potential duplicate global vendors during creation and qualification so you can review and manage matching records.
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

# Detect and manage duplicate global vendors (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The Supplier Engagement app includes duplicate detection features that help you identify possible duplicate supplier records before they move too far through onboarding. The validation checks both existing global vendors in Dataverse and vendor party records in Supply Chain Management. Duplicate detection warns you, but doesn't automatically block record creation, so you can review the warning and decide how to proceed.

## How duplicate detection works

Duplicate detection can run at two points in the process:

1. During manual global vendor creation, by using Dataverse duplicate detection rules.
1. During qualification, by checking unlinked vendor party records in Supply Chain Management.

These checks help reduce duplicate supplier identities while still allowing you to make an informed decision when a match needs manual review.

## Detect duplicates in the Supplier Engagement app

When you create a global vendor manually, the app uses standard Power Platform duplicate detection rules in Dataverse. If the system finds a potential match, it shows a warning so that you can compare the records before continuing.

Because these rules exist in Dataverse, administrators can update the matching logic in the Power Platform admin center to align with organizational policies. The warning is informational rather than blocking, so you can still continue if you can see that the new record is required.

> [!NOTE]
> Duplicate detection helps you review possible matches, but it doesn't stop you from creating the record.

## Detect duplicates against vendor parties in Supply Chain Management

During qualification, the system checks vendor party records in Supply Chain Management that aren't already linked to a global vendor. This validation helps you avoid qualifying a new global vendor when a matching party already exists.

The following table shows the matching criteria that the system uses during qualification.

| Field | Matching logic |
|---|---|
| Company name | Contains |
| Vendor name | Contains |
| Primary email | Exact match |
| Primary phone | Exact match |

If the system finds possible matches, a dialog box shows the list of vendor parties so that you can choose the most appropriate action.

## Choose an action when duplicates are found

When the system detects possible duplicates during qualification, select one of the following actions.

| Action | What it does | Typical use |
|---|---|---|
| **Merge** | Associates the global vendor with the existing vendor party. The system merges party information, and links released vendor records that belong to that party to the new global vendor. | Use this option when the vendor already exists in Supply Chain Management and the records represent the same supplier. |
| **Keep anyway** | Continues qualification without linking to the matched vendor party. The global vendor receives its own party ID. | Use this option when the records look similar but actually represent different suppliers. |
| **Cancel** | Closes the duplicate review without making a change. The vendor remains in *Prospect* status. | Use this option when you need more validation before continuing. |

Choosing the right action is important because it determines whether the supplier reuses an existing party structure or creates a new one for downstream processes.

## Related information

- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Create a global vendor](supplier-engagement-create-global-vendor.md)
- [Manage global vendor information](supplier-engagement-global-vendor-info.md)
- [Synchronize data between Supplier Engagement and Supply Chain Management](supplier-engagement-data-sync.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
