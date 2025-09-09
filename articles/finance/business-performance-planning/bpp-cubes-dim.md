---
title: Import and export cubes and dimensions 
description: Learn how to import and export cubes in Business performance planning.
author: twheeloc
ms.author: romainpham
ms.topic: article 
ms.date: 09/09/2025
ms.update-cycle: 180-days
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.collection:
---

# Import and export cubes and dimensions 
Import and export Business performance planning cubes and dimensions in Dynamics 365 Finance.

## Overview
The **Import/Export cubes and dimensions** feature in Business performance planning allows partners and customers to package cube and dimension definitions and migrate them across environments. This extensibility
framework eliminates the need to manually recreate planning schema for each environment, enabling faster setup and consistent deployment across industry-specific planning solutions.

This feature is designed to:
•	Accelerate deployment by reusing pre-built planning structures.
•	Enable partners to provide baseline cube and dimension frameworks.
•	Provide customers with a flexible starting point for further customization.
•	Support a variety of industry scenarios by making BPP schema transportable and extensible.

### Availability
This feature is available starting with Business performance planning version 1.13.

To update your environment to the latest version, follow these steps:
1.	Sign in to the Power Platform admin center.
2.	Select the environment where Business performance planning is installed.
3.	Open Dynamics 365 apps.
4.	Choose Business performance planning and trigger the update to version 1.13 or later.

### Prerequisites
Before using the Import/Export functionality, ensure:
•	You have System administrator or Planning administrator privileges in the source and target environments.
•	The Business performance planning solution is installed.
•	Permissions required: Only System Admin and Planning Admin user can import and export cubes and dimensions.
•	Dimension metadata in the target environment is reviewed to avoid conflicts.

### Key Use Cases
•	ISVs and Partners can create reusable cube and dimension templates for vertical-specific solutions (e.g., Retail, Hospitality, Healthcare).
•	Multi-environment customers can migrate specific planning models from development to production without the need for migrating the entire environment.
•	Consultants and integrators can fast-track onboarding for new implementations using standard planning schema.

### How the feature works
The Import/Export functionality is built around a metadata-driven, extensible framework that includes:
•	Cubes: Representing planning entities and drivers.
•	Dimensions: Representing hierarchies and master data used within the cubes.
•	A package format (JSON) that includes all schema components and configuration metadata.
•	A guided import/export wizard interface in the Business performance planning application to help executing this operation.
•	Support for schema validation and dependency checks before importing.

#### Export
The Export feature allows you to select one or more cubes and generate a downloadable JSON file that contains the cube schema and related dimension metadata.
>[!Note]
> Only metadata is exported. The cube doesn't contain or export any actual data.
1.	Open Business performance planning in Dynamics 365.
2.	Go to the **Cubes** section on the left side panel to view existing Cube definitions.
3.	Click **Export cube**.   
4.	Choose one or more cubes to export.
5.	Click **Export**.
6.	A JSON file is automatically generated, downloaded, and contains the selected cube and associated dimension metadata.
 

#### Importing a Cube Schema
You can use the import functionality to bring cube and dimension metadata into another environment using a previously exported JSON file.
1.	In the target environment, open the Business performance planning application in Dynamics 365.
2.	Go to the **Cubes** section.
3.	Click **New**
4.	Click **Import cube** to initiate the import wizard.
5.	Select cubes to import:
 - all cubes
   or
 - specific cubes
If a dimension with the same name already exists in the target environment, it's skipped and not overwritten.  
New dimensions in the JSON are created automatically.
6.	Confirm your selections. The schema is validated and the cubes and any new dimensions are created.   

#### Best practices

It's not recommended to import cubes that reference dimensions with the same names but different definitions between environments. This leads to metadata conflicts or data inconsistencies that may affect 
planning logic and data integrity.

Example scenario:
•	Environment 1: A WorkforcePlanning cube uses Department and JobRole dimensions.
•	Environment 2: Contains a JobRole dimension, but with a different column structure (for example, different attributes or hierarchy levels).
If a user imports the WorkforcePlanning cube from environment one into environment two, and the JobRole dimension is skipped, the cube may not function correctly due to schema mismatches or missing expected attributes. To prevent this, confirm shared dimensions across environments are aligned before importing new cubes.

#### Usage guidelines
•	Perform imports as part of initial environment setup to minimize schema conflict risk.
•	Review existing dimensions in the target environment before importing.
•	Use naming conventions or version identifiers (e.g., JobRole_v1) to distinguish variants when needed.
•	Avoid editing, creating, or deleting cubes or dimensions during the import process.
•	Limit imports to one session at a time to ensure schema consistency and avoid overlapping edits.

#### Performance 
The import process duration depends on the number of tables being processed.
Estimated duration is approximately 1 minute per table.
During the import:
•	Don't modify cubes or dimensions
•	Avoid simultaneous schema changes by other users

