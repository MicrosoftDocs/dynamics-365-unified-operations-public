---
# required metadata

title: Configuration data projects
description: This topic provides an overview of configuration data projects, configuration data templates, and the process for using them  to move company configuration data between instances of Dynamics 365 for Operations.
author: mfalkner
manager: AnnBe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
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

Configuration data projects are used to manage the movement of company configuration
data between instances of Dynamics 365 for Finance and Operations. They are intended to support the following scenarios:
-   Exporting configurations: Creating configurations of
    entities and using the data management framework to export them to a package.
-   Importing configurations: Uploading a configuration package and using the data management
    framework to import the package.

Configuration data packages are created using data import and export projects in the Data management workspace. The Data import and Data export pages let you add and remove the entities that you need to manage the movement of company and shared data. Once you create the list of entities in your configuration, you can export or import the configuration using the data management framework to create a package. You can export packages locally and move them to another instance for import. 

*Configuration data templates* are a predefined list of entities for each module area that can be used in a data project. You can create, view and modify these templates using the Template page in the Data management workspace.

> [!IMPORTANT]
> Default configuration templates are on the roadmap for the July release of Dynamics 365 for Finance and Operations. The Configuration data project feature is available in Platform update 7. You can create and use your own templates with the current product release.  

## Process of working with configuration data projects
We recommend that you follow this process when you start to use configuration data projects. 
1. Set up your system by getting the new data configuration user interface, and setting default file extensions.
2. Set up configuration templates for both export and import. 
3. Create and run a configuration data project for export.
4. Create and run a configuration data project for import.

This topic describes the data management workspace, and how to set up your system for data configuration projects. 

If you are ready to set up a configuration template, see [Configuration data templates](congifuration-data-templates.md).
If you are ready to create and run a configuration data project, see [Copy configuration data from one company to another](copy-configuration.md)

## Set up your system to manage data configurations
Before you begin, you should make sure that you have access to the new user data configurations interface (UI), that you've set up the default data sources 

### Get the new UI

We have updated the Data management workspace, the Template page, and the Data export and Data import
pages to support managing configurations. However, the updated pages are only available in Enhanced view.
The standard view has not been updated from prior releases. 

**Change to the new UI for a single user**
The system default view settings can also be changed to save settings for each user per each legal entity.
If you use that setting, you must switch to the Enhanced
view menu button on each page for configurations.

**Change to the new UI for all users in all legal entities**
1. On the Data management workspace, click the Framework parameters tile. 
2. Change the view default from standard to enhanced for all users and legal entities.

### Set file extensions for default data sources

The Template page and Import/export page allows you to add entities
by selecting a file that was created by the data management framework. We have populated some default file extensions with 
the following data sources. 
-   XLSX for the Excel data source
-   ZIP for the package data source
-   XML for the XML data source
-   CSV for the comma separated values data source
-   TXT for the delimited data source

If you have additional file extensions that you want to use, you must update your data sources with
a default file extension that will be used as the target data format.
1. On the Data management workspace, click the Configure data sources tile, and click Data sources.
2. Add a default file extension to the appropriate data source. 

# Data management workspace overview
The data management workspace provides access to key tasks for data management while providing information on projects
and project execution tasks. 

After you have created a configuration data project, it appears in the Data projects list in the Data management workspace.
Each project is displayed with the type of configuration (import or export) and a project category (Project, Configuration, Integration, and Other). Use the selections to the left of the grid to filter by the appropriate project. 

To open a project, select the project and click **Load project** to launch the **Import or export** form. Use the **Delete** button to delete the selected projects. You can also download the project definitions with the **Download** button.

Use **Job history** to find more details about the projects that you have executed. Use the data range filters to filter by the dates that data projects were executed. You can view  execution details by selecting a job and clicking the **Execution details** menu.
For export tasks, you can download the data from the workspace using the **Download page** button.

