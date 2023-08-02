---
title: Data import and export framework parameters
description: This article describes the parameters and options for data import and export.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 8/02/2023
ms.custom:

---

# Data import and export framework parameters

[!include [banner](../includes/banner.md)]

This article describes the parameters and options for data import and export.

1. Enable all company export: 

Data Management->Framework Parameters ->Bring your own database. 
If you require export to BYOD for all companies, you should enable this option. 
Enabling this option will ensure that the “Export across all companies” option is available as highlighted below.  


2. Enable header for fixed width file.  
Data Management->Framework Parameters ->Compatibility options->Flat File compatibility options. 
If the option is set to “No”, the exported file will not contain the headers. 
If the option is set to “Yes”, the exported file will contain the headers.  

3. Validate file format with file extension: 

Data Management->Framework Parameters ->Compatibility options->Flat File compatibility options. 
If the option is set to “NO”, the file is always added, even when there is a mismatch between the file types as indicated by the warning message.  
If the option is set to “Yes”, the file will not be added to the project when there is any mismatch between the file types.  

4. As part of full export, this setting enables the empty values to export with default values. 
Data Management->Framework Parameters ->Compatibility options->XML file format compatibility. 

If you enable this option, then for xm file format, you will get the default value for the field instead of null values in exported file. 

Example: <AmountCur>0.0000</AmountCur> 

If you disable this option, then for xm file format, you will get the null values in exported file. 
Example: <AmountCur/> 

5) Entity names in non-upper case. 

Data Management->Framework Parameters ->Compatibility options->XML file format compatibility. 
When this option is disabled, entity names in exported xml file will be in upper case. 
You can change the entity names to non-upper case by enabling the option - Entity names in non-upper case. 

6) Attribute names in non-upper case (applies to simple entity). 

Data Management->Framework Parameters ->Compatibility options->XML file format compatibility. 
When this option is disabled, attribute names in exported xml file will be in upper case. 
The exported file will contain attribute names in upper case. 

You can change the attribute names in target mapping to non-upper case by enabling the option Attribute names in non-upper case to Yes and re generating the target mapping. 
Create a new data project by adding the entity or remove and add the entity back to the data project. The exported file will then contain the attribute names in non-uuper case. 

7) Attribute names in non-upper case for initial mapping (applies to simple entities only) 

Data Management->Framework Parameters ->Compatibility options-> XML file format compatibility 

The initial mapping will be generated for all entities when you click on "Refresh entity list". If "Attribute names in non-upper case" is set to "No", the Attribute(column) names will be populated in upper case 
for all simple entities. If you require the Attribute(column) names to be in non-upper case, set the option to Yes and refresh the entity list 

If this option is set to No then target mapping will be generated in upper case for all entities when Refresh entity list is performed.A screenshot of a computer
The exported file will contain attribute names in upper case. 


If you require attribute names in non-upper case for all simple entities, follow the below 3 steps. 

i. First, enable the option Attribute names in non-upper case for initial mapping (applies to simple entities only). 
ii.  Refresh the entity list  - In the modify target mapping form, it should display the data in non-upper case. 
iii. Create a new data project by adding an entity or remove and add the entity back to data project. The exported file will contain attribute names in lower case. 

9) Ensure unique execution ID for export process  

Data Management->Framework Parameters ->Compatibility options-> Data project and job compatibility 

Default is No. 
If this flag is No, when multiple export requests are sent in parallel, there is a probability that on rare occasions, the export process will generate and use the same executionId for all the requests. When 
this flag is switched to Yes, the export process will ensure a unique execution ID. 

10) Run data package export API synchronously. 

Data Management->Framework Parameters ->Compatibility options-> Data project and job compatibility 
When this option set to No, the ExportToPackage API method usually runs an async call to the exporter. If set to Yes, the ExportToPackage becomes a synchronous call. 


11) Enhanced parallel package import 
Data Management->Framework Parameters ->Compatibility options-> Data project and job compatibility 
If this flag is No, when multiple import requests are sent in parallel, there is a probability that on rare occasions, the import will fail with mapping error. The recommendation is to set it to Yes to avoid
mapping errors during parallel import requests.  

12) Skip reprocessing in process recurring integration messages 
Data Management->Framework Parameters ->Compatibility options à Recurring Integrations compatibility 
When the flag “SkipResetRecurringIntegrationInProcessMessages” is disabled, the system will automatically update the status of a stuck message from “Processing” to “Queued” in the next execution. Enabling this
flag will prevent the system from changing the status of messages during the next execution. By default it is set to No.  

13) Create error file  
Data Management->Framework Parameters ->General 
The setting - <Create error file> is not used anymore in the cloud environment. It is not supported and will be deprecated from the UI. 

 

 

