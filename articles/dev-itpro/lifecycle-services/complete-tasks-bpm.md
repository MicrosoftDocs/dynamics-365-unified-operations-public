---
title: Complete tasks in BPM
description: This topic provides information about additional tasks that you can complete in Business process modeler (BPM). For example, you can publish a BPM library, export a methodology, and distribute a BPM library.
author: kfend
manager: AnnBe
ms.date: 09/17/2017
ms.topic: article
ms.prod: 
ms.service:  dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 13301
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ntecklu
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Complete tasks in Business process modeler

[!include[banner](../includes/banner.md)]

## Upload a task recording

1. In Microsoft Dynamics Lifecycle Services (LCS), in your project, on the **Business process libraries** page, select the library to upload the task recording to.

    ![Libraries on the Business process libraries page](./media/choose-library.PNG "Libraries on the Business process libraries page")

2. Select the process to upload the task recording to. 

    ![Selecting a process](./media/select-upload.PNG "Selecting a process")

3. In the right pane, select **Upload**. Select **Browse** to find and select the file to upload, and then select **Upload**.

    ![Upload AXTR dialog box](./media/upload.PNG "Upload AXTR dialog box")

## Export a methodology to Word

1. In your LCS project, on the **Business process libraries** page, select the library to export.
2. Select the process to export, and then, in the right pane, select **Doc** to begin the download.

    > [!NOTE]
    > The methodology will begin from the process step that you selected.

## Publish a BPM library

- In your LCS project, on the **Business process libraries** page, on the tile for the library that you want to copy, select the ellipsis button (…), and then select **Publish**.

    ![Publishing a BPM library](./media/PUB_DIS.png "Publishing a BPM library")

## Distribute a BPM library

When you distribute a BPM library, the library will be available to all users who are a part of your organization. In other words, it will be available to all users who sign in to LCS by using your organization's domain (for example, all users who have an @contoso.com account).

1. Ask the customer to invite you to his or her project.
2. Sign in to the customer's LCS project by using your organization's account.
3. On the **Business process libraries** page, copy the library from the **Corporate libraries** pane to the customer's project.
