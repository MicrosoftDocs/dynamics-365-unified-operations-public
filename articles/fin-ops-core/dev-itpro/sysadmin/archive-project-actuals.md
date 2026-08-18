---
title: Archive Dynamics 365 Project Operations actuals staging data (preview)
description: Learn how to archive Dynamics 365 Project Operations project actuals staging data by using Microsoft Dataverse long term retention.
author: ryansandness
ms.author: ryansandness
ms.reviewer: johnmichalak
ms.search.form:
ms.topic: how-to
ms.date: 08/18/2026
ms.custom:
  - bap-template
ms.search.region: Global
ms.search.validFrom: 2026-08-17
---

# Archive Dynamics 365 Project Operations actuals staging data (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]


_**Applies To:** Project Operations Integrated with ERP_

This article explains how to archive project actuals staging data by using Microsoft Dataverse long-term retention.

The staging table represents a copy of the actuals table from Dataverse that then generates the project subledger entries and general ledger entries after integration journal posting. After you create and post integration journals, you can archive this data because standard business logic doesn't use cost staging records.

> [!IMPORTANT]
> This feature archives only posted, processed **cost transaction** records from the project actuals staging table. Records that are unprocessed, of a transaction type other than cost, or associated with an integration journal line that isn't in the posted status aren't eligible for archival. You can't archive sales transaction records.

When you archive actuals staging transactions, the system moves data from the following tables to history tables:

- ProjCDSActualsImport
- ProjCDSTransactionRelationshipImport

## Prerequisites

Before you set up an archival job for project actuals staging data, ensure you meet the following prerequisites:

1. Install the **Dynamics 365 Archive with Dataverse Long Term Retention** app in the Microsoft Power Platform admin center, under **Dynamics 365 Apps**.
1. Set the environment to **Managed** in Power Platform admin center.
1. Turn on the **Archival Service** feature in **Feature management**.
1. Turn on the **Archive with Dataverse long term retention** feature in **Feature management**. Project actuals staging archival depends on this feature.
1. Turn on the **(Preview) Archive project actuals staging table with long term retention** feature in **Feature management**.
1. Make the necessary virtual entities visible in Dataverse.
    - In the Maker Portal, go to **Tables**, and find the **Available Finance and Operations Entity** table.
    - Ensure that **Visible** is turned on and **Change Tracking** is enabled for the **ProjActualsImportEntity** and **ProjCDSTransactionRelationshipImportBIEntity** tables.
    - Set **Visible** for the **ProjAdvancedJournalLineBIEntity** table.
1. Turn on long-term retention for the entities. In the Maker Portal, go to **Tables**, search for your entities, open **Properties**, expand **Advanced options**, and turn on **Long-term retention** for the first two tables listed in the previous step.

For more information about how to set up the archive feature, see [Set up and manage archive data in finance and operations apps](archive-setup-manage.md).

## Set up an archival job

To set up an archival job, follow these steps:

1. Go to **System administration** \> **Archive with Dataverse long term retention**.
1. In the workspace, select **Project actuals staging**.
1. Select **New long term retention** to open a wizard that you can use to schedule a new **Project actuals staging long term retention** job.
1. Enter a name for the job, and then select **Next**.
1. On the **Define criteria** page, specify the following information:

    - **Transaction type** – Select **Cost**. Only cost actuals are supported for archival.
    - **From date** and **To date** – Specify the date range. Records whose modified date and time fall within this range are eligible for archival.
    - **Legal entity** – Select one or more legal entities to include. The system creates one job per legal entity.

1. Select **Next**.
1. Select the type of scheduling. Two types are supported:

    - **Single run** – The long-term retention and **Save to history** processes run continuously until both are completed. The system always archives data in Dataverse long-term retention first. Then the save to history tables occurs.
    - **Daily during allotted time** – The long-term retention runs continuously until it's completed. The **Save to history** process runs only during the specified start and stop archiving time.

1. Select **Finish** to schedule the job.
1. Select the link in the **Results** column to view progress or detailed logs.

## View historical data from the history table

To view archived records, select an archive job, and then select **View history data**. The **Archived project actuals** page shows the records that were moved to the history table.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
