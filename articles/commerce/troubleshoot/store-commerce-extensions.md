---
# required metadata

title: Troubleshoot Store Commerce extension issues
description: This topic explains how to troubleshoot extension issues in the Microsoft Dynamics 365 Commerce Store Commerce app.
author: mugunthanm
ms.date: 05/27/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2017-06-20

---

# Troubleshoot Store Commerce extension issues

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This topic explains how to troubleshoot extension issues in the Microsoft Dynamics 365 Commerce Store Commerce app.

## Extensions packages aren't loaded

### Extensions packages don't appear on the POS \> Settings page

Commerce runtime (CRT) triggers might not have been updated to include the extension package, or they aren't deployed. For more information, see [Commerce runtime (CRT) extensibility and triggers](../dev-itpro/commerce-runtime-extensibility-trigger.md).

### Extensions packages appear on the POS \> Settings page, but the manifest isn't loaded

Confirm that the extensions packages exist in the **C:\\Program Files\\Microsoft Dynamics 365\\10.0\\Store Commerce\\Extensions** folder. If the packages exist, there should be a **POS** folder there that contains the manifest.

If there is no **POS** folder, confirm that the Store Commerce project correctly references the point of sale (POS) extension project. Validate the project reference path, and make sure that it exists. 

In the following example illustration, the installer project is having issues with the referenced extension project.

![Store Commerce installer project reference isn't valid.](media/ReferenceNotValid.png)

If the reference for the extension project is correctly added, there won't be any warning or dependency issue in the installer project, as shown in the following example illustration.

![Store Commerce installer project reference is valid.](media/ReferenceValid.png)
