---
title: Finance and operations apps archive with Dataverse long term retention FAQ
description: Access answers to frequently asked questions about archiving data in finance and operations apps with Dataverse.
author: pnghub
ms.author: brijeshjoshi
ms.topic: conceptual
ms.date: 02/12/2025
ms.custom: 
  - bap-template
ms.reviewer: twheeloc
---

# Finance and operations apps archive with Dataverse long term retention FAQ

## Does testing archiving with Dataverse long-term retention require a sandbox environment?

Yes, it requires use of a Tier-2 or greater Sandbox instance. It won't work on Tier CHE. 

## How long will my archival job take to complete?

Data archival jobs are assigned a lower priority by the application. The duration of an archival job is dependent upon the data volumes. A job can take around 7-14 days based on data volume.

## After data is archived, can I access the live data and the archived data from Dataverse long term retention?

Yes, you can use Microsoft Fabric (with the Power BI option) to query live and archived data. Dataverse makes it easy to set up Fabric.

## Can I view archived data from my finance and operations application?

Yes, an application-specific inquiry page is available so that you can view archived data. After data is permanently purged from history tables, it's no longer available for viewing. You can use Fabric (with the Power BI option) to query data from Dataverse long term retention.

## Can I restore data from Dataverse long term retention back to live tables?

No, data restore from Dataverse long term retention to live tables isn't supported. 

## Do I save the maximum database capacity if I purge data from history tables?

For full savings, users can purge data from history tables.

## Are related tables archived by this feature?

No, only the data from the live application tables that are in the scenario is archived. Dependent transactions outside the supported archive scenario aren't archived. For example, archiving of the Inventory Transaction table doesn't archive its original transactions. Administrators must set up archiving of the SalesOrder table separately.

## I linked my finance and operations environment with a Dataverse environment and ran a successful archival job from my workspace. Can I make a change to relink the finance and operations environment to a new Power Apps/CE environment?

No, changes cause data loss and shouldn't be made.

## I ran a successful archival job from my archival workspace in finance and operations apps. When I refresh the finance and operations database with new production data, is my archived data refreshed with the same production Dataverse backup?

No, Currently, a refresh of the finance and operations database doesn't automatically refresh Dataverse. You must refresh Dataverse separately from production.

## There's no inventory closing for moving average transactions. Does this mean that we can't archive these transactions?

No, the inventory transaction archival scenario isn't limited for transactions. Moving average transactions and standard cost transactions can be archived if they have closed inventory.

## How can I meet the requirement of my auditors who need to view the transactional data archived with Dataverse long term retention?

You can [view archived data](archive-view.md) in Dataverse long term retention with Microsoft Fabric.

You can also view the archived data from within the finance and operations History table for all the different scenarios. [General Ledger example](archive-gl.md#view-historical-data-from-the-history-table).

## I export finance and operations application data to my own data lake. If I archive data from my live finance and operations application tables, will the archived data be removed from my own data lake?
Dataverse long-term retention isn't supported on Bring Your Own Database (BYOD), and data preservation in BYOD isn't guaranteed.

## What should I do if the installation or upgrade of the Dynamics 365 Archive with Dataverse long term retention app from Power Platform fails?
---

## Prerequisites Before Installation

- **Complete All prerequisite Setup Steps**  
  Ensure that all prerequisite setup steps are completed. Incorrect setup can lead to installation failure.

- **Check Application Activity**  
  You must have logged into your Finance and Operations (F&O) application within the last 30 days. If the organization is marked as dormant, installation may fail.  
  - If you're logging in after more than 30 days, it may take **up to 4 hours** for your organization to be flagged as active.

---

## Common Installation failure cases and Resolutions

### Case 1: Status error code or Duplicate Key error

**Symptom 1: status error code**
   - `Status code 503: Service unavailable`
  - `Status code 500: Solution operation failed due to another import blocking the operation`
  -  Solution import progress has been stuck

**Resolution:**
- Wait a few minutes and retry the installation. Repeat until it succeeds.

**Symptom 2: Duplicate Key Error During Upgrade:**
- **Error message:** `Cannot insert duplicate key exception when executing non-query`
- **Resolution:**
  1. Go to the **Maker portal > Solutions**.
  2. Delete the solutions:
     - `ArchiveServicePermissions_PROD`
     - `ArchiveService Anchor Solution`
  3. Refresh and repeat the installation.

---

### Case 2: License Configuration key missing

**Error Message:**  
- `MCR call center config key needs to be enabled under License Configuration in order to enable change tracking for MCRSalesTableBiEntity`.

**Resolution:**
1. In **Dynamics 365 Finance and Operations**, navigate to:  `System administration > License configuration`
2. Enable the following checkboxes and sub-checkboxes:
  - `Retail channels - Call center`

---

### Case 3: Virtual entity is not eligible for archival

**Error Message:**  
`Failed to validate if retention is enabled for fno ve : generaljournalentrybientity... entity is not eligible for archival`

**Resolution:**
1. Go to **Maker portal > Tables > Available Finance and Operations Entity**.
2. Ensure the **Refresh** column is visible.
3. Refresh the mentioned entity.
> **Note:** If **custom fields** were added to the backing table of the entity (e.g., `GeneralJournalEntry`), ensure that all custom fields are added to the entity **before** refreshing it.


---

### Case 4: Data Source Configuration Issue

**Error Message:**  
`"Unable to establish connection using data source: 'Finance and Operations Virtual Data Source Configuration'. Failed to sync entity metadata."`

**Cause:**  
The user performing the installation on **PPAC** either does **not exist** or is **not an administrator** in Dynamics 365 FnO.

**Resolution:**
- Ensure the installation user exist in FnO and has administrator role granted.

---







