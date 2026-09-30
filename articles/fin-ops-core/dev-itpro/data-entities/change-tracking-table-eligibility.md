---
title: Table eligibility for change tracking
description: Check which Dynamics 365 finance and operations tables can use SQL or row version change tracking, including exclusions and feature-specific requirements.
author: ethanrimes
ms.author: ethankallett
ms.topic: article
ms.date: 09/26/2026
ms.custom:
  - bap-template
audience: Developer, IT Pro
ms.search.region: Global
---

# Table eligibility for change tracking

[!INCLUDE [banner](../includes/banner.md)]

This article describes how to check whether a Dynamics 365 finance and operations application table can participate in change tracking. The exclusion lists in this article are shorter than a catalog of supported tables and apply to both standard and custom tables. Check the effective table metadata, including extensions, in your application version.

## Check the correct mechanism

SQL change tracking and row version change tracking have separate eligibility settings. Enabling one doesn't enable the other.

| Mechanism and existing guidance | Table property to check | Where to enable it |
| --- | --- | --- |
| [SQL change tracking](entity-change-track.md) | **Allow Change Tracking** | **Change tracking** in the **Data management** workspace, including BYOD publishing. |
| [Row version change tracking](rowversion-change-track.md) | **Allow Row Version Change Tracking** | Follow the linked table and configuration-key setup, then the setup for the feature that consumes the changes. |

For example, `DimensionAttributeSet` has **Allow Change Tracking** set to **No** and **Allow Row Version Change Tracking** set to **Yes**. It illustrates why you must check the property for the intended mechanism; it isn't an exhaustive list of excluded tables.

If your requirement is an audit history rather than incremental synchronization, see [Configure and manage database logging](../sysadmin/configure-manage-database-log.md). Database logging has separate configuration and limitations.

## SQL change tracking

The **Allow Change Tracking** table property defaults to **Yes**. The following exclusions determine which tables can't be tracked:

| Excluded tables or objects | What to check |
| --- | --- |
| Tables whose **Allow Change Tracking** property is **No** | Check the table's effective property value, not whether an entity that uses it appears in Data management. |
| Derived tables with an ancestor whose **Allow Change Tracking** property is **No** | Follow the table's **Extends** hierarchy. The derived table and every ancestor must allow SQL change tracking. |
| Objects that aren't persistent SQL tables, or tables without a primary key | Views and temporary tables (**InMemory** or **TempDB**) aren't eligible application tables for SQL change tracking. A physical table must have a primary key. |

Selecting **Enable entire entity** or **Enable custom query** doesn't override these exclusions. An excluded table doesn't become a source of tracked changes just because it's included in the entity or query. Choose the tracking scope using [Enable SQL change tracking for data entities](entity-change-track.md#enable-change-tracking-for-byod).

### Tables that you shouldn't track for export performance

For tables to omit from SQL change tracking queries for export performance, see [Data entity export performance tips](data-export-perform.md#implement-defaultctquery-to-specify-which-tables-changes-are-tracked-for-and-to-limit-the-amount-of-change-data-that-must-be-processed). These recommendations are separate from table eligibility restrictions and aren't blanket exclusions from row version change tracking.

## Row version change tracking

A table must have **Allow Row Version Change Tracking** set to **Yes**. If the value is **No**, the table isn't currently enabled in metadata; that value alone doesn't mean the table can never support row version change tracking. Before enabling it, check these exclusions:

| Excluded tables | What to check |
| --- | --- |
| Temporary tables | **Table Type** must be **Regular**, not **InMemory** or **TempDB**. |
| Staging tables | **Table Group** must not be **Staging**. A regular table can still be a staging table. |
| Derived tables whose ancestors don't allow row version change tracking | The derived table and every table in its **Extends** hierarchy must have **Allow Row Version Change Tracking** set to **Yes**. |

For an eligible table, follow [Enable row version change tracking for tables](rowversion-change-track.md#enable-row-version-change-tracking-for-tables) and the [configuration-key and database synchronization prerequisites](rowversion-change-track.md#enable-row-version-change-tracking-functionality). For guidance on enabling additional standard or custom tables through extensions for Synapse Link, see [Add finance and operations tables in Azure Synapse Link](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data#add-finance-and-operations-tables-in-azure-synapse-link).

### Check data entities and consuming features separately

Table eligibility doesn't guarantee that a data entity or consuming feature supports the table.

Runtime enablement can also require an index that starts with `RecId`. Framework-managed tables can have additional restrictions: for example, `AifChangeTrackingDeletedObject`, which the framework uses for [deletion tracking](rowversion-change-track.md#track-deletions-and-cleanup), can be rejected as a tracked source even when **Allow Row Version Change Tracking** is **Yes**. These runtime checks depend on the application version and feature configuration. They aren't a blanket exclusion of framework tables.

| Scenario | Additional check |
| --- | --- |
| Data entities | The entity must enable row version change tracking, all underlying tables must allow it, and the entity must pass the [data entity validation rules](rowversion-change-track.md#enable-row-version-change-tracking-for-data-entities). Use that version-specific rule list for joins, ranges, views, date-effective data sources, and other entity restrictions. |
| Azure Synapse Link | Check the [Synapse Link limitations](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data#known-limitations-and-changes-to-behavior), including the exclusion of deprecated `DEL_` tables and the separately listed kernel tables that refresh without change tracking. The Synapse Link table selector shows availability for that feature, not a universal list of row version-enabled tables. |
| Dataverse virtual tables | Complete the [virtual-table prerequisites and Track changes setup](../power-platform/track-changes-fin-ops-virtual-table.md). Enabling SQL change tracking in Data management isn't a substitute. |

## Check a table in your environment

1. In Visual Studio, locate the table in Application Explorer and inspect its effective properties, including installed extensions. Check **Table Type**, **Table Group**, and the change tracking property for your mechanism.
1. If **Extends** is set, check the corresponding change tracking property on every ancestor.
1. Apply the exclusions for your mechanism and verify that the table is enabled by its configuration key, if it has one. Then check the requirements for your data entity and consuming feature. Don't use the presence of a table in one feature's selector as evidence that it supports the other mechanism.
1. After making any supported metadata changes, build and synchronize the database as required by the setup instructions. Verify incremental synchronization in a sandbox before deploying the change to production.

Use the documented application and metadata configuration paths. Don't bypass table restrictions by enabling change tracking directly in the finance and operations SQL database.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
