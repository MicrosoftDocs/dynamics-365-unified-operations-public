---
title: Complete tasks in Business process modeler (BPM)
description: This article provides information about additional tasks that you can complete in Business process modeler (BPM).
author: AngelMarshall 
ms.date: 06/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Complete tasks in Business process modeler (BPM)

[!include [banner](../includes/banner.md)]

## Upload a task recording

1. In Microsoft Dynamics Lifecycle Services (LCS), in your project, on the **Business process libraries** page, select the library to upload the task recording to.

    ![Libraries on the Business process libraries page.](./media/choose-library.PNG "Libraries on the Business process libraries page")

2. Select the process to upload the task recording to. 

    ![Selecting a process.](./media/select-upload.PNG "Selecting a process")

3. On the **Overview** pane, select **Upload**. Select **Browse** to find and select the file to upload, and then select **Upload**.

    ![Upload AXTR dialog box.](./media/upload.PNG "Upload AXTR dialog box")
    
## Download a task recording

You can download a task recording (AXTR file) that has been uploaded to a BPM process. 

1. In your LCS project, on the **Business process libraries** page, select the library to download the task recording.

2. Select a process that has task recording uploaded. 

3. On the **Overview** pane, select **Download** to save the task recording (AXTR). 

    ![Download AXTR.](./media/Download%20AXTR.png "Donload AXTR")
    
## Export a methodology to Word

1. In your LCS project, on the **Business process libraries** page, select the library to export.
2. Select the process to export, and then, in the right pane, select **Doc** to begin the download.

    > [!NOTE]
    > The methodology will begin from the process step that you selected.

## Publish a BPM library

- In your LCS project, on the **Business process libraries** page, on the tile for the library that you want to copy, select the ellipsis button (…), and then select **Publish**.

    ![Publishing a BPM library.](./media/PUB_DIS.png "Publishing a BPM library")

## Distribute a BPM library

When you distribute a BPM library, the library will be available to all users who are a part of your organization. In other words, it will be available to all users who sign in to LCS by using your organization's domain (for example, all users who have an @contoso.com account).

1. Ask the customer to invite you to their project.
2. Sign in to the customer's LCS project by using your organization's account.
3. On the **Business process libraries** page, copy the library from the **Corporate libraries** pane to the customer's project.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]