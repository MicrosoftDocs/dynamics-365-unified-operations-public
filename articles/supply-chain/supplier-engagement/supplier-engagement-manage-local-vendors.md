---
title: Manage local vendors (preview)
description: Manage local vendors by releasing global vendors to legal entities and maintaining local details, contacts, bank accounts, and tax data.
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

# Manage local vendors (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Local vendor management in the Supplier Engagement app lets you create, update, and control vendor accounts at the legal entity level. You can release a global vendor to a legal entity, maintain local vendor details, and add supporting records such as contacts and bank accounts. All supported updates sync automatically between the Supplier Engagement app and Supply Chain Management.

## Release a global vendor to a legal entity

When a supplier is ready for operational use, release the global vendor to a legal entity and create the local vendor account.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record).
1. On the command bar, select **Release vendor**. Then select **OK** in the confirmation dialog.
1. Enter the following values in the **Release vendor** dialog:
    - **Global vendor** – Read-only reference to the selected global vendor
    - **Legal entity** – Select the legal entity (company) to create the local vendor for.
    - **Vendor group** – Select the vendor group for the local account.
    - **Vendor number** – Enter a vendor number for the local account.
    - **Currency code** – Select the currency used by the local vendor. Leave blank to use the default currency for the selected legal entity.
    - **Vendor hold** – If the vendor should be on hold, select the appropriate hold type. Leave blank if the vendor is not on hold. Learn more in [Global and local vendor holds (preview)](supplier-engagement-vendor-holds.md).
1. Select **Release**.

## <a name="open-local-vendor"></a>View and edit local vendor information

Use the local vendor record when you need to maintain legal entity–specific settings.

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record).
1. Open the **Lifecycle** tab.
1. The **Vendors** section lists the currently defined local vendors. To open a local vendor record so you can view and edit its details, select the link in the **Vendor account** column.
1. Update any fields that are required.
1. Select **Save**.

After you save the record, the updated information syncs automatically to Supply Chain Management.

## Add a contact for a local vendor

You can add vendor contacts for a local vendor in the Supplier Engagement App. The contact must already exist as a [global vendor contact](supplier-engagement-global-vendor-contacts.md). To add a local vendor contact, follow these steps:

1. [Open the relevant global vendor record](supplier-engagement-global-vendor-info.md#open-a-global-vendor-record).
1. Open the **Contacts** tab.
1. Open a contact record by selecting the link in the **Full name** column.
1. On the **Summary** tab, in the **Contact for legal entities** section, select **New Vendor Contact** from the toolbar.
1. Select the **Vendor account** for the local vendor to add the contact to.
1. On the command bar, select **Save & close**.

## Maintain bank information for local vendors

To view, add, or edit bank account details for a local vendor, follow these steps:

1. [Open the local vendor record](#open-local-vendor).
1. Open the **Bank information** tab. Each existing bank detail record is summarized in the grid. You can do the following actions:
    - To open an existing bank account record, select the **Go to record** button in the right column of the row.
    - To add a new bank account, select **New vendor bank account** in the toolbar.
1. View, enter, and edit bank account details as needed.
1. On the command bar, select **Save & close**.

## View approved categories

Approved categories determine which products or services the vendor is authorized to supply. To see which categories are approved for a local vendor, follow these steps:

1. [Open the local vendor record](#open-local-vendor).
1. Open the **Approved Categories** tab.
1. Review the categories that are assigned to the vendor.

## View certificates

Certificates that are managed at the global vendor level are inherited by local vendors, so you can review them from the local record.

1. [Open the local vendor record](#open-local-vendor).
1. Open the **Certifications** tab.
1. Review the inherited certificate records.

## Add state tax IDs to local vendors

Use the state tax ID section when you're working with a United States legal entity that requires state-specific tax registration details.

1. [Open the local vendor record](#open-local-vendor).
1. Open the **State Tax Id** tab.
1. Select **Add State Tax Id**.
1. Enter the required tax ID details.
1. On the command bar, select **Save & close**.

> [!NOTE]
> State tax IDs are available only for supported United States localization scenarios.

## Localization

Some local vendor fields and sections appear only for specific countries/regions. The app automatically shows or hides these areas based on the local vendor's legal entity configuration.

Country/region-specific sections can include the following examples:

- **Ownership profile**
- **Business information**
- **State tax ID**

## Related information

- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
- [Global vendor management overview](supplier-engagement-global-vendors-overview.md)
- [Supplier Engagement overview](supplier-engagement-overview.md)
