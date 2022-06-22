---
 # required metadata

title: View version history to revert pages and fragments
description: This article describes how to view the version history for a page or fragment and revert to an older version in Microsoft Dynamics 365 Commerce site builder.
author: phinneyridge
ms.date: 06/21/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2017-06-20

---

# View version history to revert pages and fragments

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article describes how to view the version history for a page or fragment and revert to an older version in Microsoft Dynamics 365 Commerce site builder.

Commerce site builder allows you to see to view the version history for a page or fragment and revert to a specific previous version of a document if needed. Selecting **Show history** on the command bar when a document is open brings up a **Version history** flyout menu that lists the history of all versions and save activities for the page or fragment on the **Version** tab. A previous version of the document can then be selected from the list, previewed, and restored as the current version. The **Activity** tab of the **Version history** flyout menu lists the full activity history of the document which includes all save, publish, unpublish events.

> [!NOTE]
> New versions of a document are created each time a site author makes changes and then selects **Finished editing** for the document. 

To view the version history for a page or fragment and revert to a previous version, follow these steps:

1. In site builder, open the page or fragment for which you want to view the version history.
1. On the command bar, select **Show history**.   

    ![Show history button.](./media/version-history-1.png)

1. On the **Versions** tab of the **Version history** flyout menu, select a previous version of the document. In the property pane on the right, you can view a thumbnail preview of a previous version as well as information on who modified that version of the document and when it was modified.

    ![Version history list view.](./media/version-history-2.png)

1. To view a full preview of a past version of the document, select **Preview** at the top of the **Version history** flyout menu. This will display a rendered preview of the selected document. To close the preview and return to the **Version history** flyout menu, select **Exit preview**.
1. To restore a previous version of a document, select it from the list, and then select **Restore**. The **Restore version \<version number\>** dialog box appears. 

    ![Restore version action.](./media/version-history-3.png)

1. To confirm and proceed with the restore action, select **Restore**. Site builder will then refresh showing the restored version of the page or fragment.
1. To publish the restored version, select **Finish editing**, and then select **Publish**.
