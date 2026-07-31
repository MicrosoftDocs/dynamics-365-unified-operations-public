---
title: Synchronize data between Supplier Engagement and Supply Chain Management (preview)
description: Learn how data synchronization works between the Supplier Engagement app and Supply Chain Management, including the sync configuration manager, virtual entities, and OData.
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

# Synchronize data between Supplier Engagement and Supply Chain Management (preview)

[!include [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Data synchronization keeps supplier-related information consistent between Supply Chain Management and the Supplier Engagement app. It uses event-driven processes and configurable sync logic to support full create, read, update, and delete (CRUD) operations on data that resides in Supply Chain Management while maintaining the data in its original location. These synchronization features are available both during initial installation and day-to-day use of the solution.

> [!TIP]
> We recommend that you always use the Supplier Engagement application to create and maintain aggregated supplier information across legal entities. System synchronization logic ensures that supplier data is synced to the respective legal entities within Dynamics 365 Supply Chain Management.

## Prerequisites

Before you can start synchronizing data, your systems must meet the following requirements:

- Your Supply Chain Management environment must be connected to Dataverse. Learn more in [Microsoft Power Platform integration with finance and operations apps](/dynamics365/fin-ops-core/dev-itpro/power-platform/overview).
- The Supplier Engagement app must be installed. Learn more in [Install the Supplier Engagement app and supplier portal on Power Platform](deploy-install-power-platform.md).
- The *Supplier Engagement* feature must be turned on in Supply Chain Management. Learn more in [Enable the Supplier Engagement feature](deploy-configure-scm.md#enable-the-supplier-engagement-feature).
- You must complete all configuration steps described in the deployment guide. Learn more in [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md).

## Data synchronization overview

The Supplier Engagement app uses the following components to synchronize data between the systems:

- **Sync configuration manager** – Uses plugin triggers and field mappings to keep Dataverse tables and virtual entities in sync.
- **Virtual entities** – Represent Supply Chain Management data in Dataverse without duplicating it.
- **Supplier portal Web API** – Allows the supplier portal to perform CRUD operations on Dataverse tables and virtual entities.
- **Open Data Protocol (OData)** – Provides standardized web service access to Supply Chain Management data and processes.

The system uses virtual entities from Supply Chain Management and Dataverse tables to maintain data between both systems. The sync configuration manager uses plugin triggers on both virtual entities and Dataverse tables. These plugins use the mappings from the sync configuration manager to synchronize data between both systems.

The following illustration shows the integration architecture between the Dataverse environment and Supply Chain Management.

:::image type="content" source="media/data-sync-architecture.svg" alt-text="Diagram of the integration architecture between Dataverse and Supply Chain Management, showing virtual entities, native entities, plugin triggers, and OData connections." lightbox="media/data-sync-architecture.svg":::

You can learn more about how synchronization is implemented in Dataverse in the following articles:

- [Use plug-ins to extend business processes](/power-apps/developer/data-platform/plug-ins)
- [Data synchronization in Dataverse](/power-apps/developer/data-platform/data-synchronization)

## Sync configuration manager

The sync configuration manager ensures that data remains consistent between Supply Chain Management and the Supplier Engagement app. It uses the data stored in the Supplier Engagement app to determine which records require synchronization and triggers updates on both Supply Chain Management and Supplier Engagement tables. The supplier portal also uses this system to keep data updated between the two platforms.

Key capabilities of the sync configuration manager include:

- **Real-time synchronization** – Keeps data aligned between Supply Chain Management and the Supplier Engagement app, reducing manual updates and errors.
- **Configurable sync logic** – Administrators can define which tables and fields are synchronized, allowing for tailored integration scenarios.
- **Event-driven updates** – Changes in either system trigger synchronization, ensuring timely data updates.

### Synchronized entities

The following table lists the entities that are exposed for use by the sync configuration manager. Entities with the *(mserp)* suffix are virtual entities from Supply Chain Management that are exposed in Dataverse. Entities without the suffix are native Dataverse tables. The names shown here are the display names, which you can search for in Power Platform.

| Dataverse table | Virtual entity (mserp) |
|---|---|
| Global Vendor | Global Vendors (mserp) |
| Contact | Person for VRM (mserp) |
| Contact Method | Contact information for VRM (mserp) |
| Address | Addresses for Supplier Portal (mserp) |
| Global Vendor Portal Access | Supplier Portal user requests (mserp) |

### Data flows

This section describes the data flow for each synchronized entity pair. Each entity supports bidirectional synchronization between the Supplier Engagement app (or supplier portal) and Supply Chain Management, using plugin triggers and the sync configuration manager mappings. Records are linked between systems using the `VERecordGuid` field, which stores the Supply Chain Management record ID in Dataverse.

#### Global vendor

When you create, update, or delete a global vendor record in the Supplier Engagement app, plugins trigger on the `msdyn_globalvendor` Dataverse table and synchronize the changes to the `mserp_vrmglobalvendorentity` virtual entity in Supply Chain Management.

When you update the virtual entity in Supply Chain Management, an `OnExternalUpdate` plugin triggers and synchronizes the changes back to Dataverse.

The following illustration shows the data flow between the Supplier Engagement app and Supply Chain Management for global vendor records.

:::image type="content" source="media/data-sync-global-vendor-app.svg" alt-text="Diagram of the data flow between the Supplier Engagement app and Supply Chain Management for global vendor records." lightbox="media/data-sync-global-vendor-app.svg":::

When you update a global vendor through the supplier portal, the updated data synchronizes to Supply Chain Management using the sync configuration manager mappings via the Web API.

The following illustration shows the data flow from the supplier portal to Supply Chain Management for global vendor records.

:::image type="content" source="media/data-sync-global-vendor-portal.svg" alt-text="Diagram of the data flow from the supplier portal to Supply Chain Management for global vendor records." lightbox="media/data-sync-global-vendor-portal.svg":::

#### Address

When you create, update, or remove an address for a global vendor that is qualified or approved, plugins trigger on the `msdyn_vrmvendorpostaladdress` Dataverse table and synchronize the changes to the `mserp_vrmpartylocationpostaladdressentity` virtual entity in Supply Chain Management.

When you create, update, or delete the virtual entity record in Supply Chain Management, the corresponding `OnExternalCreate`, `OnExternalUpdate`, or `OnExternalDelete` plugin triggers and synchronizes the changes back to Dataverse. If you delete a record in Supply Chain Management, the corresponding Dataverse record is also deleted.

The following illustration shows the data flow between the Supplier Engagement app and Supply Chain Management for address records.

:::image type="content" source="media/data-sync-address-app.svg" alt-text="Diagram of the data flow between the Supplier Engagement app and Supply Chain Management for address records." lightbox="media/data-sync-address-app.svg":::

You can also create or update addresses through the supplier portal. Changes synchronize to Supply Chain Management using the sync configuration manager mappings via the Web API.

The following illustration shows the data flow from the supplier portal to Supply Chain Management for address records.

:::image type="content" source="media/data-sync-address-portal.svg" alt-text="Diagram of the data flow from the supplier portal to Supply Chain Management for address records." lightbox="media/data-sync-address-portal.svg":::

#### Contact method

When you create, update, or delete a contact method record, plugins trigger on the `msdyn_vrmpartycontact` Dataverse table and synchronize the changes to the `mserp_vrmpartycontactentity` virtual entity in Supply Chain Management.

When you create, update, or delete the virtual entity record in Supply Chain Management, the corresponding plugin triggers and synchronizes the changes back to Dataverse. If you delete a record in Supply Chain Management, the corresponding Dataverse record is also deleted.

The following illustration shows the data flow between the Supplier Engagement app and Supply Chain Management for contact method records.

:::image type="content" source="media/data-sync-contact-method-app.svg" alt-text="Diagram of the data flow between the Supplier Engagement app and Supply Chain Management for contact method records." lightbox="media/data-sync-contact-method-app.svg":::

You can also create, update, or delete contact method records through the supplier portal. Changes synchronize to Supply Chain Management by using the sync configuration manager mappings via the Web API.

The following illustration shows the data flow from the supplier portal to Supply Chain Management for contact method records.

:::image type="content" source="media/data-sync-contact-method-portal.svg" alt-text="Diagram of the data flow from the supplier portal to Supply Chain Management for contact method records." lightbox="media/data-sync-contact-method-portal.svg":::

#### Contact

When you create, update, or delete a contact record, plugins trigger on the `contact` Dataverse table and synchronize the changes to the `mserp_vrmpersonentity` virtual entity in Supply Chain Management.

When you create, update, or delete the virtual entity record in Supply Chain Management, the corresponding plugin triggers and synchronizes the changes back to Dataverse. If you delete a record in Supply Chain Management, the corresponding Dataverse record is also deleted.

The following illustration shows the data flow between the Supplier Engagement app and Supply Chain Management for contact records.

:::image type="content" source="media/data-sync-contact-app.svg" alt-text="Diagram of the data flow between the Supplier Engagement app and Supply Chain Management for contact records." lightbox="media/data-sync-contact-app.svg":::

You can also create, update, or delete contacts through the supplier portal. Changes are synchronized to Supply Chain Management using the sync configuration manager mappings via the Web API.

The following illustration shows the data flow from the supplier portal to Supply Chain Management for contact records.

:::image type="content" source="media/data-sync-contact-portal.svg" alt-text="Diagram of the data flow from the supplier portal to Supply Chain Management for contact records." lightbox="media/data-sync-contact-portal.svg":::

#### Portal access

When you update a supplier portal user request record in Supply Chain Management, an `OnExternalUpdate` plugin triggers on the `mserp_vrmportaluserrequestentity` virtual entity and synchronizes the changes to the `msdyn_globalvendorportalaccess` Dataverse table.

The following illustration shows the data flow from Supply Chain Management to the Supplier Engagement app for portal access records.

:::image type="content" source="media/data-sync-portal-access-app.svg" alt-text="Diagram of the data flow from Supply Chain Management to the Supplier Engagement app for portal access records." lightbox="media/data-sync-portal-access-app.svg":::

You can also create global vendor portal access records from the supplier portal. The records are synchronized to Supply Chain Management using the sync configuration manager mappings via the Web API.

The following illustration shows the data flow from the supplier portal to Supply Chain Management for portal access records.

:::image type="content" source="media/data-sync-portal-access-portal.svg" alt-text="Diagram of the data flow from the supplier portal to Supply Chain Management for portal access records." lightbox="media/data-sync-portal-access-portal.svg":::

> [!NOTE]
> For portal access records, the link between Dataverse and Supply Chain Management uses the Entra ID and User ID fields (rather than `VERecordGuid`).

### Mapping components

The sync configuration manager uses two related tables to manage field-level mappings:

- **VRM Sync Config** – The parent table. Each record defines a synchronization configuration that specifies the source table and the destination table.
- **VRM Sync Mappings** – The child table. Each record specifies how individual fields from the source table are mapped to fields in the destination table. Each mapping record is linked to a parent record in the VRM Sync Config table.

In summary, VRM Sync Config defines *what* is synchronized (which tables), and VRM Sync Mappings defines *how* the data is synchronized (which fields are mapped). Each sync configuration can have multiple attribute mappings associated with it.

### Configure sync mappings

When you install the Supplier Engagement app, it creates data for the VRM Sync Config and VRM Sync Mappings tables. Only users with the *Supplier Engagement Admin* role can modify these tables. Users with other roles have read-only access.

> [!WARNING]
> Changes to the sync configuration manager setup affect data synchronization for all configured entities. Only make changes as part of post-deployment steps, and only if required. Only administrators should perform these activities.

To add a new sync configuration mapping, follow these steps:

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Configuration** area.
1. On the navigation pane, select **Data Sync** \> **Sync Config**.
1. On the command bar, select **New**.
1. In the **Source Table** field, enter the logical name of the source entity in text format.
1. In the **Destination Table** field, enter the logical name of the destination entity in text format.
1. On the command bar, select **Save**. A **Field Mappings** area appears on the record.
1. On the toolbar, select **New Field Mappings** to add a field mapping.
1. In the new mapping window, set the following fields:
    - **Source field** – Enter the source field logical name in text format.
    - **Destination field** – Enter the destination field logical name in text format.
    - **Type** – Select the field type. Allowed types are *Text*, *Whole Number*, *Decimal*, *Lookup*, *Choice*, and *Date and Time*.
1. Select **Save**.
1. Go back to the parent record, set **Generate Config** to *Yes*, and select **Save** on the command bar.

The system creates a JSON file on the backend that the sync configuration manager uses to synchronize records between the source and destination tables.

To remove a sync configuration mapping, follow these steps:

1. Open the Supplier Engagement app, and at the bottom of the navigation pane, select the **Configuration** area.
1. On the navigation pane, select **Data Sync** \> **Sync Config**.
1. Open the record from which you want to remove a mapping.
1. In the **Field Mappings** area, select the mapping that you want to remove.
1. On the toolbar, select **Delete Sync Config Mapping**.
1. Go back to the parent record, set **Generate Config** to *Yes*, and select **Save** on the command bar.

You can also activate or deactivate individual sync config mappings in the same way. Always select **Generate Config and Save** after making changes to update the configuration with the latest settings.

### Relation to dual-write

The custom sync logic in Supplier Engagement is distinct from the standard dual-write functionality in Supply Chain Management. While dual-write provides out-of-the-box data integration, the sync configuration manager offers more tailored and granular control over which fields are synchronized.

> [!IMPORTANT]
> If you enable both dual-write and the sync configuration manager for the same entities, the system might create duplicate records. Don't configure both systems to synchronize the same data.

## Virtual entities

You can integrate Supply Chain Management with Microsoft Dataverse as a virtual data source. This integration makes Supply Chain Management entities, such as vendors, purchase orders, and contacts, available in Dataverse as virtual entities. These virtual entities act as a bridge, so users and applications in Dataverse and the broader Microsoft Power Platform can perform CRUD operations on Supply Chain Management data.

Key points about virtual entities:

- **Data location** – The actual data stays in Supply Chain Management. Dataverse only references this data and doesn't store it.
- **Enablement** – Before you can perform CRUD operations from Dataverse, you must expose the relevant Supply Chain Management entities as virtual entities. This step requires configuration. Learn more in [Enable Microsoft Dataverse virtual entities](../../fin-ops-core/dev-itpro/power-platform/enable-virtual-entities.md).
- **Operations** – Once enabled, you can interact with Supply Chain Management data from Dataverse and Power Platform tools, just as you would with native Dataverse tables.

Learn more about virtual entities in [Virtual entities overview](../../fin-ops-core/dev-itpro/power-platform/virtual-entities-overview.md).

## Open Data Protocol

Open Data Protocol (OData) actions enable external systems and applications to interact with Supply Chain Management data and processes using standard web services. By using OData, you can securely and consistently create, update, or retrieve business data.

The following entities in the Supplier Engagement solution expose OData actions:

- Supplier Portal users
- Vendor-approved procurement categories for Supplier Portal
- Vendor category request headers for Supplier Portal
- Purchase order response headers for Supplier Portal
- Purchase order response lines for Supplier Portal
- RFQ reply headers for Supplier Portal
- Request for quotation reply lines for Supplier Portal
- Pending vendor invoice headers for Supplier Portal
- Request for quotation questionnaires for Supplier Portal

To support OData actions within the Supply Chain Management user security context, each of these entities exposes two key fields:

- `ActionParameters` – Specifies the input data for the OData action.
- `ActionName` – Identifies the specific OData action to execute.

## Related information

- [Supplier Engagement overview](supplier-engagement-overview.md)
- [Supplier Engagement deployment overview, prerequisites, and licensing](deploy-overview.md)
- [Configure the Supplier Engagement app overview](configure-app-overview.md)
- [Work with the Supplier Engagement app](supplier-engagement-app-overview.md)
- [Work with Supplier Engagement data in Supply Chain Management](supplier-engagement-data-in-scm.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
