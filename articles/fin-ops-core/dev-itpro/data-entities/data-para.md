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

On the **Bring your own database** tab, the **Enable all company export** following parameter is available:
  **Enable all company export** - Select **Yes** to export all companies. 

On the **Compatibility options** tab, the following parameters are available:
-   **Enable header for fixed width file**:
    -   select **No** if the exported file doesn't contain headers.
    -   select **Yes** if the exported file contains headers.  
-   **Validate file format with file extension**: 
    -   select **No** to always add files when there's a mismatch between the file types.
    -   Select **Yes** if the file will not be added to the project if there's a mismatch between the file types.  
-   **XML file format compatibility**:
    -   select **Yes** to export empty fields with default values. Example: <AmountCur>0.0000</AmountCur> 
    -   Select **No** to export empty fields with null values. Example: <AmountCur/> 
-   **Entity names in non uppercase**:
    -   select **No** to display entity names in uppercase.
    -   Select **Yes** to display entity names in non uppercase. 
-   **Attribute names in non uppercase** (applies to simple entity):
      -   select **No** to display attribute names in uppercase.
      -   Select **Yes** to display attribute names in non uppercase. Create a new data project by adding the entity or remove and add the entity back to the data project. The exported file displays the attribute names in non uppercase. 
-   **Attribute names in non uppercase for initial mapping** (applies to simple entity):
      -   select **No** to display the Attribute(column) names in uppercase. The initial mapping is generated for all entities when you click **Refresh entity list**.
      -   Select **Yes** to display the Attribute(column) names in non uppercase, and refresh the entity list.

To update attribute names to non uppercase for simple entities, follow these steps: 
1. Select **Yes** for the **Attribute names in non uppercase for initial mapping (applies to simple entities only)**.
2. Select **Refresh the entity list**. On the **Modify target mapping** page, the data is displayed in non uppercase.
3. Create a new data project by adding an entity or remove and add the entity back to data project. The exported file displays attribute names in lower case. 

-   **Data project and job compatibility**
    -   select **No** to use the same executionId for multiple export requests that are sent in parallel.
    -   Select **Yes** to have a unique execution ID. 

-   **Run data package export API synchronously** 
    -   select **Yes** to have the ExportToPackage a synchronous call.
    -   Select **No** to have the ExportToPackage API method run an async call to the exporter. 

-   **Enhanced parallel package import**
    -   select **Yes** to avoid mapping errors during parallel import requests.
    -   Select **No** when multiple, parallel, import requests are sent, the import fails with a mapping error. 

-   **Skip reprocessing in process recurring integration messages**
    -   select **No** to automatically update the statuses of stuck messages from **Processing** to **“Queued** during the next execution.
    -   Select **Yes** to prevent changing the statuses of messages during the next execution.   


 

 

