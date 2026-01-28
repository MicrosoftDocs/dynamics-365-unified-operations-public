---
title: Complete tasks in Business process modeler (BPM)
description: Learn about additional tasks that you can complete in Business process modeler (BPM), including the process of uploading a task recording.
author: AngelMarshall
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom:
ms.search.form:
ms.dyn365.ops.version: 2012
ms.custom: sfi-image-nochange
---

# Complete tasks in Business process modeler (BPM)

[!include [banner](../includes/banner.md)]

## Upload a task recording

1. In Microsoft Dynamics Lifecycle Services, in your project, on the **Business process libraries** page, select the library to upload the task recording to.

    :::image type="content" source="./media/choose-library.PNG" alt-text="Screenshot of libraries on the Business process libraries page.":::

1. Select the process to upload the task recording to.

    :::image type="content" source="./media/select-upload.png" alt-text="Screenshot of selecting a process.":::

1. On the **Overview** pane, select **Upload**. Select **Browse** to find and select the file to upload, and then select **Upload**.

## Download a task recording

You can download a task recording (AXTR file) that you uploaded to a BPM process.

1. In your Lifecycle Services project, on the **Business process libraries** page, select the library to download the task recording.

1. Select a process that has a task recording uploaded.

1. On the **Overview** pane, select **Download** to save the task recording (AXTR).

    :::image type="content" source="./media/Download%20AXTR.png" alt-text="Screenshot of the Download AXTR option.":::

## Export a methodology to Word

1. In your Lifecycle Services project, on the **Business process libraries** page, select the library to export.
1. Select the process to export. In the right pane, select **Doc** to start the download.

    > [!NOTE]
    > The methodology starts from the process step that you selected.

## Publish a BPM library

- In your Lifecycle Services project, on the **Business process libraries** page, on the tile for the library that you want to copy, select the ellipsis button (...), and then select **Publish**.

    :::image type="content" source="./media/PUB_DIS.png" alt-text="Screenshot of publishing a BPM library.":::

## Distribute a BPM library

When you distribute a BPM library, all users in your organization can access the library. In other words, all users who sign in to Lifecycle Services by using your organization's domain (for example, all users who have an @contoso.com account) can access the library.

1. Ask the customer to invite you to their project.
1. Sign in to the customer's Lifecycle Services project by using your organization's account.
1. On the **Business process libraries** page, copy the library from the **Corporate libraries** pane to the customer's project.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
