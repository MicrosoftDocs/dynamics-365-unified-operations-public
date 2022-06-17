---
 # required metadata

title: View version history to roll back pages and fragments
description: This article describes how to view the version history for a page or fragment and roll back to an older version in Microsoft Dynamics 365 Commerce site builder.
author: phinneyridge
ms.date: 06/17/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2017-06-20

---

# View version history to roll back pages and fragments

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to view the version history for a page or fragment and roll back to an older version in Microsoft Dynamics 365 Commerce site builder.

Commerce site builder's visual page builder interface for pages and fragments displays a **Show history** button on the command bar that when selected lists a history of all versions and save activities for the page or fragment. Site authors can then roll back to a specific previous version of the document being edited. 

To view the version history for a page or fragment and roll back to a previous version, follow these steps:

1. In site builder, open the page or fragment that you want to view the version history for.
1. On the command bar, select **Show history**.   

    ![Show history button.](./media/version-history-1.png)

1. On the **Versions** tab of the **Version history** flyout menu, a version history of the document is displayed. Select a previous version of the document. 

    ![Version history list view.](./media/version-history-2.png)

    > [!NOTE]
    > - Versions are created each time an editor makes changes and selects **Finished editing** for the document. 
    > - In the right property panel, you can view a thumbnail preview of a previous version of a document along with information on who modified that version of the document and when it was modified.
    > - The activity tab of the **Version history** flyout menu lists the full activity history of the document. Activity events are created for all save, publish, unpublish events.

1. To view a full preview of a past version, select **Preview** at the top of the **Version history** flyout menu. This will display a rendered preview of the selected document. To close the preview, select the **X** in the upper right corner or **Exit preview** on the lower left.
1. If you find a version that you would like to restore, select it in the list view and then select **Restore** on the command bar. The **Restore version \<version number\>** dialog box appears. To confirm and proceed with the restore action, select **Restore**.

    ![Restore version action.](./media/version-history-3.png)

1. The visual page builder will refresh with the restored version of the page or fragment.
1. To publish the restored version, select **Finish editing**, and then select **Publish**.
