---
title: Post-deployment validation checklist (preview)
description: Validate installed solutions, cloud flows, and sync configuration records after Supplier Engagement deployment.
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

# Post-deployment validation checklist (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

After deployment is complete, validate the environment before you hand it over to business users or suppliers. These checks help you confirm that the expected solutions are available, automation is turned on, and synchronization data was created correctly. Running the checklist early makes troubleshooting much easier if something is missing.

## Confirm Power Apps solutions are available

Review the managed solutions in the Power Apps maker portal to make sure that the Supplier Engagement package finished installing.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/).
1. Go to **Solutions**.
1. Open the **Managed** tab.
1. Confirm that the the following Supplier Engagement solutions are listed:
    - Supplier Engagement Anchor
    - Supplier Engagement Portal
    - Supplier Engagement Plugins
    - Supplier Engagement Core
    - Supplier Engagement Controls
    - Supplier Engagement Consignment Inventory
    - Supplier Engagement Vendor Invoice
    - Supplier Engagement Request for Quotation
    - Supplier Engagement Purchase Order
    - Supplier Engagement Vendor Onboarding
    - Supplier Engagement Contact Person Entity
    - Supplier Engagement Vendor Entity
    - Supplier Engagement Base

> [!NOTE]
> If any expected solutions are missing, reinstall the Supplier Engagement package.

## Confirm cloud flows are enabled

Check both managed solutions that contain cloud flows so that you can confirm that automation is active.

1. Sign in to the [Power Apps maker portal](https://make.powerapps.com/) and select your environment.
1. On the navigation pane, select **Solutions**.
1. Find and open the solution that has a **Display name** of *Supplier Engagement Core*.
1. On the navigation pane, select **Objects** > **Cloud flows**.
1. Verify that every flow has a **Status** of *On*.
1. On the navigation pane, select **Back to solutions**.
1. Find and open the solution that has a **Display name** of *Supplier Engagement Portal*.
1. On the navigation pane, select **Objects** > **Cloud flows**.
1. Verify that every flow has a **Status** of *On*.

> [!NOTE]
> If any flow status is *Off*, follow the instructions in [Enable supporting cloud flows](deploy-configure-power-platform.md#enable-supporting-cloud-flows).

## Confirm sync configurations are available

The Supplier Engagement app should contain the sync configuration records created when you deployed the solution.

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Configuration** area.
1. On the navigation pane, go to **Data Sync** \> **Sync Configs**.
1. Confirm that the sync configuration mappings listed in the following table exist on your system.

    | Source Table                               | Destination Table                           |
    |--------------------------------------------|---------------------------------------------|
    | mserp_vrmpersonentity                      | contact                                     |
    | mserp_vrmglobalvendorentity                | msdyn_globalvendor                          |
    | msdyn_vrmpartycontact                      | mserp_vrmpartycontactentity                 |
    | msdyn_vrmvendorpostaladdress               | mserp_vrmpartylocationpostaladdressentity   |
    | contact                                    | mserp_vrmpersonentity                       |
    | mserp_vrmportaluserrequestentity           | msdyn_globalvendorportalaccess              |
    | mserp_vrmpartycontactentity                | msdyn_vrmpartycontact                       |
    | msdyn_globalvendor                         | mserp_vrmglobalvendorentity                 |
    | mserp_vrmpartylocationpostaladdressentity  | msdyn_vrmvendorpostaladdress                |

1. If sync configuration records are missing or the record count doesn't match expectations, follow the instructions in [How can I resolve sync configuration issues?](deploy-questions.md#how-can-i-resolve-sync-configuration-issues).

## Confirm sync config table mappings are current

Use the **Modified On** value to confirm that the sync configuration records were refreshed during the latest deployment.

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Configuration** area.
1. On the navigation pane, go to **Data Sync** \> **Sync Configs**.
1. Select **Edit columns**.
1. In the **Edit columns** dialog, select **Add columns**.
1. Select **Modified On**, and then select **Close**.
1. Select **Apply**.
1. Verify that the **Modified On** value for each sync configuration matches the date when you last deployed the Supplier Engagement solution.
1. If the dates aren't correct, follow the instructions in [How can I resolve sync configuration issues?](deploy-questions.md#how-can-i-resolve-sync-configuration-issues).

## Related information

- [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md)
- [Install the Supplier Engagement app and supplier portal on Power Platform](deploy-install-power-platform.md)
- [Onboard using the onboarding guide](deploy-onboarding-guide.md)
- [Configure Supplier Engagement elements in Power Platform](deploy-configure-power-platform.md)
- [Configure Supplier Engagement features in Supply Chain Management](deploy-configure-scm.md)
- [Deployment FAQs](deploy-questions.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
