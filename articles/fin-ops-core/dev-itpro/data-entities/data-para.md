---
title: Data import/export framework parameters
description: This article describes the parameters and options for data import and export.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 8/09/2023
ms.custom:

---

# Data import/export framework parameters

[!include [banner](../includes/banner.md)]

This article describes the Data import/export framework parameters and options for data import and export.

To access the parameters, in finance and operations apps, go to **Data Management** \> **Framework parameters**.

On the **Bring your own database** tab, the following parameter is available:

- **Enable all company export**:

    - Select **No** to export only selected companies.
    - Select **Yes** to export all companies.

On the **Compatibility options** tab > **Flat file compatability options**, the following parameters are available:

- **Enable header for fixed width file**:

    - Select **No** if the exported file isn't required to contain headers.
    - Select **Yes** if the exported file is required to contain headers.

- **Validate file format with file extension**:

    - Select **No** if files should always be added to the project when there's a mismatch between the file types.
    - Select **Yes** if files should not be added to the project when there's a mismatch between the file types.

On the **Compatibility options** tab > **XML file compatability options**, the following parameters are available:
- **Full export**:
    - Select **No** to export empty fields with null values. Here's an example: `<AmountCur/>`
    - Select **Yes** to export empty fields with default values. Here's an example: `<AmountCur>0.0000</AmountCur>`

- **Entity names in non uppercase**:

    - Select **No** to show entity names in uppercase letters.
    - Select **Yes** to show entity names in non-uppercase letters.

- **Attribute names in non uppercase (applies to simple entities only)**:

    - Select **No** to show attribute names in uppercase letters.
    - Select **Yes** to show attribute names in non-uppercase letters. Create a new data project by adding the entity, or remove the entity and add it back to the data project. The exported file shows the attribute names in non-uppercase letters.

- **Attribute names in non uppercase for initial mapping (applies to simple entities only)**:

    - Select **No** to show Attribute(column) names in uppercase letters. The initial mapping is generated for all entities when you select **Refresh entity list**.
    - Select **Yes** to show Attribute(column) names in non uppercase letters. Then refresh the entity list.

    To update attribute names for simple entities to non uppercase letters, follow these steps.
    1. Set the **Attribute names in non uppercase for initial mapping (applies to simple entities only)** parameter to **Yes**.
    2. Select **Refresh the entity list**. On the **Modify target mapping** page, the data is shown in non uppercase letters.
    3. Create a new data project by adding an entity, or remove the entity and add it back to the data project. The exported file shows attribute names in non uppercase letters.

On the **Compatibility options** tab > **Data project and job compatibility option**, the following parameters are available:
- **Ensure unique execution id**:

    - Select **No** to use the same execution ID for multiple export requests that are sent in parallel.
    - Select **Yes** to use a unique execution ID for every export request.

- **Run data package export API synchronously**:

    - Select **No** to have the `ExportToPackage` API method run an asynchronous call to the exporter.
    - Select **Yes** to have the `ExportToPackage` API method run a synchronous call to the exporter.

- **Enhanced parallel package import**:

    - Select **No** if import should fail with a mapping error when multiple, parallel, import requests are sent.
    - Select **Yes** to avoid mapping errors during parallel import requests.

On the **Compatibility options** tab > **Recurring integrations compatibility**, the following parameter is available:
- **Skip reprocessing in process recurring integration messages**:
  
    - Select **No** to automatically update the status of stuck messages from **Processing** to **Queued** during the next execution.
    - Select **Yes** to prevent the status of messages from being changed during the next execution.
