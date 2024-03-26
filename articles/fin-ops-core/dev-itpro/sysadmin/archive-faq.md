---
title: Dynamics 365 Finance archive with Dataverse long term retention FAQ (preview)
description: This article answers frequently asked questions about archiving data in Microsoft Dynamics 365 Finance with Dataverse.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom: 
  - bap-template
---

# Dynamics 365 Finance archive with Dataverse long term retention FAQ (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

## Does testing archiving with Dataverse long-term retention require a sandbox environment?

Yes, it requires use of a Tier-2 or greater Sandbox instance. It will not work on Tier CHE. 

## After data is archived, can I access the live data and the archived data from Dataverse long term retention?

Yes, you can use Microsoft Fabric (with the Power BI option) to query live and archived data. Dataverse makes it easy to set up Fabric.

## Can I view archived data from my Dynamics 365 Finance application?

Yes, an application-specific inquiry page is available so that you can view archived data. After data is permanently purged from history tables, it's no longer available for viewing. You can use Fabric (with the Power BI option) to query data from Dataverse long term retention.

## Can I restore data from Dataverse long term retention back to live tables?

No, data restore from Dataverse long term retention to live tables isn't supported. 

## What if I don't want to use long-term retention? I just need to delete data from the Finance database.

Purge history is planned for a future release.

## Will I save the maximum database capacity if I purge data from history tables?

For full savings, users can purge data from history tables.

## Does this feature archive related tables?

No. Only the data from the live application tables that are in the scenario is archived. Dependent transactions outside the supported archive scenario aren't archived. For example, archiving of the Inventory Transaction table doesn't archive its original transactions. Administrators must set up archiving of the SalesOrder table separately.

## I linked my Finance environment with a Dataverse environment and ran a successful archival job from my workspace. Can I make a change to relink the Finance environment to a new Power Apps/CE environment?

No, changes cause data loss and shouldn't be made.

## I ran a successful archival job from my archival workspace in Finance. When I refresh the Finance database with new production data, is my archived data refreshed with the same production Dataverse backup?

No. Currently, a refresh of the Finance database doesn't automatically refresh Dataverse. You must refresh Dataverse separately from production.

## There's no inventory closing for moving average transactions. Does this mean that we can't archive these transactions?

No, the inventory transaction archival scenario isn't limited for transactions. Moving average transactions and standard cost transactions can be archived if they have closed inventory.

## What if I don't want to use long term retention? I just need to delete data from the Finance database.

Purge history is planned for a future release.
