---
# required metadata

title: Configure Common Data Service integration 
description: This topic explains how to turn the integration between Microsoft Dynamics 365 Talent and Common Data Service on and off.
author: andreabichsel
manager: AnnBe
ms.date: 11/08/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-10-08
ms.dyn365.ops.version: Talent October 2019 update

---

# Configure Common Data Service integration

You can turn integration between Common Data Service and an instance of Microsoft Dynamics 365 Talent on or off. You can also view the synchronization details, clear tracking data, and resync an entity to help troubleshoot data issues between the two environments.

When you turn off integration, users can make changes in Talent or Common Data Service, but those changes aren't synced between the two environments.

By default, integration between Talent and Common Data Service is turned either off or on, depending on the presence of demo data in the environments:

- **Off** for new environments that don't include demo data
- **On** for new environments that include demo data

New environments that include demo data will start to sync data when they are provisioned.

You might want to turn off integration in these situations:

- You're filling in data through the Data Management Framework and must import the data multiple times to get it into a correct state.

- There are issues with data in either Talent or Common Data Service. If you turn off integration, you can delete a record in one environment without deleting it in the other. When you turn integration back on, the record in the environment where it wasn't deleted will be synced back to the environment where it was deleted. Synchronization begins the next time the **Common Data Service integration missed request sync** batch job runs.

> [!WARNING]
> When you turn off data integration, make sure that you don't edit the same record in both environments. When you turn integration back on, the record that you last edited will be synced. Therefore, if you didn't make the same changes to the record in both environments, data loss can occur.

## Access the Common Data Service integration page

1. In the Talent instance where you want to view or configure settings for the integration with Common Data Service, select the **System administration** tile.

    [![System administration tile](./media/hr-select-system-administration.png)](./media/hr-select-system-administration.png)

2. Select the **Links** tab.

    [![Links tab](./media/hr-system-administration-links.png)](./media/hr-system-administration-links.png)

3. Under **Integrations**, select **Common Data Service configuration**.

    [![Common Data Service configuration link](./media/hr-select-common-data-service-configuration.png)](./media/hr-select-common-data-service-configuration.png)

## Turn data integration between Talent and Common Data Service on or off

- To turn on integration, set the **Enable the integration to the Common Data Service** option to **Yes**.

    > [!NOTE]
    > When you turn on integration, data will be synced the next time that the **Common Data Service integration missed request sync** batch job runs. All data should be available after the batch job is completed.

- To turn off integration, set the option to **No**.

[![Turning the Common Data Service integration on or off](./media/hr-enable-or-disable-common-data-service-integration.png)](./media/hr-enable-or-disable-common-data-service-integration.png)

## View data integration details

On the **Administration** FastTab of the **Common Data Service integration** page, you can see how records are linked together between Talent and Common Data Service.

- To view the records for an entity, select the entity in the **CDS entity name** field. The grid shows all the records that are linked to the selected entity.

[![Viewing the records for an entity](./media/hr-common-data-service-configuration-view-entity.png)](./media/hr-common-data-service-configuration-view-entity.png)

> [!NOTE]
> Not all Common Data Service entities are currently listed. Only entities that support the use of custom fields appear in the grid. New entities become available through continuous releases of Talent.

The grid includes the following fields:

- **CDS entity name** – The name of the entity in Common Data Service.
- **CDS entity reference** – The identifier that Common Data Service uses to identify a record. This value is equivalent to a Talent **RecId** value. You can find the identifier when you open the Common Data Service entity in Microsoft Excel.
- **Talent entity name** – The entity that last synced data to Common Data Service. The entity can have either the Common Data Service prefix or another prefix.
- **Talent reference** – The **RecId** value that is associated with the record in Talent.
- **Was deleted from CDS** – A value that indicates whether the record was deleted from Common Data Service.

## Remove the association of a record in Talent from Common Data Service

If you experience issues during data synchronization between Talent and Common Data Service, you might be able to resolve them by clearing the tracking and letting the tracking table be resynced. If you remove the association, and then change or delete a record in Common Data Service, the changes won't be synced to Talent. If you make changes in Talent, a new tracking record is created, and the record is updated in Common Data Service.

- To remove the association of a record between Talent and Common Data Service, select the entity in the **CDS entity name** field, and then select **Clear tracking information**.

[![Clearing tracking information](./media/hr-common-data-service-configuration-clear-tracking.png)](./media/hr-common-data-service-configuration-clear-tracking.png)

To run a full synchronization on the entity after you clear the tracking, see the next procedure.

## Sync an entity between Talent and Common Data Service

Use this procedure if changes from Common Data Service are taking too long to appear in Talent, or if you must refresh the tracking table after you clear the tracking.

- To run a full synchronization on an entity between Talent and Common Data Service, select the entity in the **CDS entity name** field, and then select **Sync now**.

[![Running a full synchronization](./media/hr-common-data-service-configuration-sync-now.png)](./media/hr-common-data-service-configuration-sync-now.png)
