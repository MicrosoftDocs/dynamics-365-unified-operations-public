---
# required metadata

title: Configuration data projects
description: This topic provides an overview of configuration data projects, configuration data templates, and the process for using them to move company configuration data between instances of Dynamics 365 for Finance and Operations.
author: mfalkner
manager: AnnBe
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 77523
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2017-07-31
ms.dyn365.ops.version: Platform update 7

---
# Configuration data projects

## Overview
Configuration data projects are used to manage the movement of company configuration data between instances of Microsoft Dynamics 365 for Finance and Operations. They are intended to support the following scenarios:
- **Export of configurations** – Create configurations of entities, and  use the data management framework to export them to a package.
- **Import of configurations** – Upload a configuration package, and use the data management framework to import the package.

Configuration data packages are created by using data import and export projects in the **Data management** workspace. The **Data import** and **Data export** pages let you add and remove the entities that you require in order to manage the movement of company and shared data. After you create the list of entities in your configuration, you can export or import the configuration by using the data management framework to create a package. You can export packages locally and then move them to another instance for import.

Configuration data templates are predefined lists of entities for each module area that can be used in a data project. You can create, view, and modify these templates by using the **Template** page in the **Data management** workspace.

> [!IMPORTANT]
> Default configuration templates are on the roadmap for the July 2017 release of Dynamics 365 for Finance and Operations, Enterprise edition. The Configuration data project feature is available in Platform update 7. You can create and use your own templates in the current product release.

## Process for working with configuration data projects
We recommend that you follow this process when you start to use configuration data projects.

1. Set up your system by getting the new data configuration user interface (UI) and setting default file extensions.
2. Set up configuration templates for both export and import.
3. Create and run a configuration data project for export.
4. Create and run a configuration data project for import.

The rest of this topic describes the **Data management** workspace and explains how to set up your system for data configuration projects.

If you're ready to set up a configuration template, see [Configuration data templates](configuration-data-templates.md). If you're ready to create and run a configuration data project, see [Copy configuration data from one company to another](copy-configuration.md).

## Data management workspace overview
The **Data management** workspace provides access to important tasks for data management. It also provides information about projects and project execution tasks.

After you've created a configuration data project, it appears in the **Data projects** grid in the **Data management** workspace. For each project, the type of configuration (import or export) and a project category (**Project**, **Configuration**, **Integration**, or **Other**) is shown. Use the selections to the left of the grid to filter by the appropriate project.

To open a project, select the project, and then click **Load project** to open the **Import or export** page. Use the **Delete** button to delete the selected projects. You can also download the project definitions by using the **Download** button.

Use **Job history** to find more details about the projects that you've run. Use the data range filters to filter by the dates when data projects were run. You can view  execution details by selecting a job and then clicking the **Execution details** menu.

For export tasks, you can download the data from the workspace by using the **Download page** button.

## Set up your system to manage configuration data projects
Before you begin, make sure that you have access to the new data configuration UI, and that you've set up the default data sources.

### Get the new UI
We have updated the **Data management** workspace, the **Template** page, and the **Data export** and **Data import** pages to support  configuration management. However, the updated pages are available only in the Enhanced view. The Standard view hasn't been updated from previous releases.

#### Change to the new UI for a single user

The system's default view settings can be changed to save settings for each user per each legal entity. To switch the view for a single user, the user must click the **Enhanced view** button on each page in the **Data management** workspace.

#### Change to the new UI for all users in all legal entities

1. In the **Data management** workspace, click the **Framework parameters** tile.
2. Change the **View default** setting from **Standard** to **Enhanced** for all users and legal entities.

### Set file extensions for default data sources
The **Template** page and the **Import/export** page let you add entities by selecting a file that was created by using the data management framework. We have added some default file extensions for the following data sources:

- XLSX for the Microsoft Excel data source
- ZIP for the package data source
- XML for the XML data source
- CSV for the comma-separated values (CSV) data source
- TXT for the delimited data source

If you have other file extensions that you want to use, you must update your data sources so that they have a default file extension that will be used as the target data format.

1. In the **Data management** workspace, click the **Configure data sources** tile, and then click **Data sources**.
2. Add a default file extension to the appropriate data source.
