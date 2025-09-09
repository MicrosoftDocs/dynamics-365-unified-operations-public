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
The Import/Export Cubes and Dimensions feature in Business performance planning allows partners and customers to package Cube and Dimension definitions and migrate them across environments. This extensibility
framework eliminates the need to manually recreate planning schema for each environment, enabling faster setup and consistent deployment across industry-specific planning solutions.

This feature is designed to:
•	Accelerate deployment by reusing pre-built planning structures.
•	Enable partners to provide baseline Cube and Dimension frameworks.
•	Provide customers with a flexible starting point for further customization.
•	Support a variety of industry scenarios by making BPP schema transportable and extensible.

### Availability
This feature is available starting with Business performance planning version 1.13.
Ensure your environment is updated to version 1.13 or later to use Import/Export for Cubes and Dimensions.
This feature is available starting with Business performance planning version 1.13.
To update your environment to the latest version:
1.	Sign in to the Power Platform admin center.
2.	Select the environment where Business performance planning is installed.
3.	Open Dynamics 365 apps.
4.	Choose Business performance planning and trigger the update to version 1.13 or later.

### Prerequisites
Before using the Import/Export functionality, ensure:
•	You have System Administrator or Planning Administrator privileges in the source and target environments.
•	The Business performance planning solution is installed.
•	Permissions required: Only System Admin and Planning Admin user can Import and Export cubes and Dimension.
•	Dimension metadata in the target environment is reviewed to avoid conflicts.

### Key Use Cases
•	ISVs and Partners can create reusable Cube and Dimension templates for vertical-specific solutions (e.g., Retail, Hospitality, Healthcare).
•	Multi-environment customers can migrate specific planning models from development to production without the need for migrating the entire environment
•	Consultants and integrators can fast-track onboarding for new implementations using standard planning schema.

### How the Feature Works
The Import/Export functionality is built around a metadata-driven, extensible framework that includes:
•	Cubes: Representing planning entities and drivers.
•	Dimensions: Representing hierarchies and master data used within the Cubes.
•	A package format (JSON) that includes all schema components and configuration metadata.
•	A guided import/export wizard interface in the Business performance planning application to help executing this operation.
•	Support for schema validation and dependency checks before importing.

#### Exporting a Cube Schema
The Export feature allows you to select one or more Cubes and generate a downloadable JSON file that contains the Cube schema and related Dimension metadata.
Note: Only metadata is exported. The Cube does not contain or export any actual data.
1.	Navigate to the Business performance planning Application 
Open the Business performance planning in Dynamics 365.
2.	Open the Cubes Section
Go to the Cubes section on the left side panel to view existing Cube definitions.
3.	Click 'Export Cube'
Click the Export cube button.  
4.	Select Cube(s) to Export
Within the right side panel, choose one or more Cubes that you want to export. Click Export.
5.	Download JSON File
A JSON file is automatically generated and downloaded. This file contains:
o	The selected Cube metadata.
o	Associated Dimension metadata.
 

#### Importing a Cube Schema
Use the Import functionality to bring Cube and Dimension metadata into another environment using a previously exported JSON file.
1.	Navigate to the Business performance planning Application
In the target environment, open the Business performance planning application in Dynamics 365.
2.	Open the Cubes Section and Click 'New'
Go to the Cubes section on the left side panel and click New and Import Cube to initiate the import wizard.
3.	Upload JSON File
Use the file picker in the wizard to upload the exported JSON file.
4.	Select Cubes to Import
The wizard displays all Cubes available in the uploaded file. You can:
o	Import all Cubes, or
o	Select specific Cubes to import.
5.	Dimension Handling
o	If a Dimension with the same name already exists in the target environment, it will be skipped and not overwritten.  
o	New Dimensions in the JSON will be created automatically.
6.	Complete the Import
Confirm your selections. The system will validate the schema and create the Cube(s) and any new Dimension(s) as specified.   

### Considerations and Best Practices
Avoid Conflicting Dimension Definitions
It is not recommended to import Cubes that reference Dimensions with the same names but different definitions between environments. This can lead to metadata conflicts or data inconsistencies that may affect 
planning logic and data integrity.
Example scenario:
•	Environment 1: A Cube named WorkforcePlanning uses Dimensions called Department and JobRole.
•	Environment 2: Already contains a JobRole Dimension, but with a different column structure (for example, different attributes or hierarchy levels).
If a user imports the WorkforcePlanning Cube from Environment 1 into Environment 2, and the JobRole Dimension is skipped (because it already exists), the Cube may not function correctly due to schema mismatches 
or missing expected attributes.
To prevent this, ensure that shared Dimensions across environments are aligned before importing new Cubes.

Recommended Usage Guidelines
•	Perform imports as part of initial environment setup to minimize schema conflict risk.
•	Review existing Dimensions in the target environment before importing.
•	Use naming conventions or version identifiers (e.g., JobRole_v1) to distinguish variants when needed.
•	Avoid editing, creating, or deleting Cubes or Dimensions during the import process.
•	Limit imports to one session at a time to ensure schema consistency and avoid overlapping edits.

Performance Consideration
The import process duration depends on the number of tables being processed.
Estimated duration: approximately 1 minute per table.
During the import:
•	Do not modify Cubes or Dimensions.
•	Avoid simultaneous schema changes by other users.

