---
# required metadata

title: Project migration manager
description: This article explains how to use the Project Migration Manager to move your project from one Microsoft Dynamics 365 Lifecycle Services geography to another.
author: LaneSwenka
ms.date: 10/05/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form:
# ROBOTS:
audience: IT Pro, Developer
# ms.devlang:
ms.reviewer: sericks
# ms.tgt_pltfrm:
ms.custom: 257614
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
# ms.search.industry:
ms.author: laswenka
ms.search.validFrom: 2016-09-30
ms.dyn365.ops.version: AX 7.0.0

---

# Project migration manager

[!include [banner](../includes/banner.md)]

The Microsoft Dynamics 365 Lifecycle Services (LCS) project migration manager utility allows you to move your project data from one geography to another geography that LCS supports. This article describes the terminology, the supported scenarios, and frequently asked questions for this functionality.

## Move projects to new geographies
It is important to understand why you might want to move your LCS project from one "geo" or geography to another. Originally, LCS only supported a single instance - https://lcs.dynamics.com/ - which was the global endpoint for all customers. With recent regulatory requirement trends across the industry for customers and software vendors to keep data within a geographic boundary, LCS has started to deploy geographic-specific instances of LCS so that customers can have all of their project data in a desired location. For more information on different geographies available, visit [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](/dynamics365/fin-ops-core/dev-itpro/deployment/deployment-options-geo).

With this capability, you can now move your project from one geographic location to another that meets your requirements. There are some limitations in terms of all of the data that is automatically transferred which we will cover below.  

## Data transfer between instances
The following data is transferreable between instances, using the actions shown below.

|Migration method| Project types| Capabilities|
|----------------|--------------|-------------|
|Automated| Cloud implementation project, on-premise implementation project, partner project| Business process modeler<br/>Methodologies<br/>Project onboarding<br/>Project settings<br/>Support</br>Work Items<br/>|
|Manual migration| Cloud implementation project, on-premise project, partner project| Asset library<br/>Commerce<br/>Self-service environments(support ticket)<br/>Cloud-hosted environments (CHE)<br/>|
|Not supported| All | Configuration and Data Manager (CDM)<br/>Sharepoint Online integration<br/>System diagnostics<br/>Upgrade analysis<br/>Globalization<br/>Code upgrade<br/>Translation service<br/>Non-project features|

Data that requires manual migration must be done by you. You are not required to migrate any or all of this data, and you may elect to migrate your most recent assets from the asset library, or re-create developer cloud-hosted environments for example in the target project.

## Start your project migration
To start your project migration, follow these steps.

1. Use the navigation menu to select **Project migration manager**.

> [!NOTE]
> You must be a Project owner to perform a migration.

1. Use the **New** button to start a new migration request.
1. In the Schedule Migration slider, choose a **target geo** that meets your specifications.
3. Choose a **migration start time** which is in the future. This will begin the migration for your project and several aspects of the project will become read-only.
4. Click the checkbox to agree to the terms and continue.

After the migration is scheduled, you may cancel it by highlighting it from the Project migration manager list page and clicking the **Delete** button.  

### Validations
There are several validations that take place with the Project migration manager.  These are listed below.

- All migrations must be scheduled in the future.
- Migrations are only allowed for certain project types.  Please see the table above for what is allowed under Automated migration.
- Deleting or cancelling a migration can only be done on a migration that is not yet started.

### During migration
When the migration is in progress, a banner will be shown across the source and target projects that indicates it is participating in a migration.  The projects will be locked for changes until the migration completes successfully or fails and is rolled back.  

## Frequently asked questions (FAQ)
Below are several common questions that we would like to answer.  

### My Sandbox and Production environments are already in my desired geography (Europe for example).  Why is there downtime when I move my LCS project to EU?
Finance and Operations apps have metadata stored that includes their connection to the LCS project from which they were created.  When we migrate your project to a new geography, such as LCS Europe, it will need to update this connection information in those environments.  This requires at minimum an environment restart which can take up to an hour.

### What geographies are available for me to choose from?
For more information on different geographies available, visit [Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies](/dynamics365/fin-ops-core/dev-itpro/deployment/deployment-options-geo).

### What happens to the source project after migration is completed?
We will keep the source project available for up to one year, in read-only mode.  You will be able to download assets, but you will not be able to make any other changes nor manage the environments from the source project.  After one year, we will delete all of the source project and its data.

You are always welcome to delete the project earlier than one year, if you have moved all of your required data to the target project and wish to no longer have data residing in the source geography.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
