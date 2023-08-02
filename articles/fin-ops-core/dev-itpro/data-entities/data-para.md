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

This article describes the Data import/export framework parameters and options for data import and export.


##  Data import/export framework parameters

In Dynamics 365 finance and operations, go to **Data Management** > **Framework parameters**. 
On the **Bring your own database** tab, the following parameter is available:
-   **Enable all company export** - If you require export to Bring your own database for all companies, select the **Export across all companies** option.

 On the **Compatibility options** tab, the following parameters are available:
-   **Enable header for fixed width file**:
    -   select **No** if the exported file will not contain headers.
    -   select **Yes** if the exported file will contain headers.  
-   **Validate file format with file extension** -
    -   select **No** if the file will always be added if there is a mismatch between the file types.
    -   Select **Yes** if the file will not be added to the project if there is a mismatch between the file types.  
-   **XML file format compatibility**
    -   select **Yes** to export empty fields with default values. Example: <AmountCur>0.0000</AmountCur> 
    -   Select **No** to get null values in exported file. Example: <AmountCur/> 
-   **Entity names in non-upper case**
    -   select **No** to display entity names in upper case.
    -   Select **Yes** to display entity names in non-upper case. 
-   **Attribute names in non-upper case** (applies to simple entity)
      -   select **No** to display attribute names in upper case.
      -   Select **Yes** to display the attribute names in non upper case and regenerate the target mapping. Create a new data project by adding the entity or remove and add the entity back to the data project. The exported file will then contain the attribute names in non-upper case. 
-   **Attribute names in non-upper case for initial mapping** (applies to simple entity)
      -   select **No** to display the Attribute(column) names in upper case. The initial mapping will be generated for all entities when you click **Refresh entity list**.
      -   Select **Yes** to display the Attribute(column) names in non-upper case, and refresh the entity list. If this option is set to **No**, the target mapping will be generated in upper case for all entities.


To update attribute names to non-upper case for simple entities, follow these steps: 
1. Select **Yes** for the **Attribute names in non-upper case for initial mapping (applies to simple entities only)**.
2. Select **Refresh the entity list**. In the **Modify target mapping** page, the data is displayed in non-upper case.
3. Create a new data project by adding an entity or remove and add the entity back to data project. The exported file will contain attribute names in lower case. 

-   **Data project and job compatibility**
    -   select **No** to use the same executionId for multiple export requests that are sent in parallel.
    -   Select **Yes** to have a unique execution ID. 

-   **Run data package export API synchronously** 
    -   select **Yes** to have the ExportToPackage a synchronous call.
    -   Select **No** to have the ExportToPackage API method run an async call to the exporter. 

-   **Enhanced parallel package import**
    -   select **Yes** to avoid mapping errors during parallel import requests.
    -   Select **No** when multiple, parallel, import requests are sent, the import will fail with mapping error. 

-   **Skip reprocessing in process recurring integration messages**
    -   select **No** to automatically update the statuses of a stuck messages from **Processing** to **“Queued** in the next execution.
    -   Select **Yes** to prevent changing the statuses of messages during the next execution.   


 

 

