---
# required metadata

title: Troubleshoot Store Commerce extension issues
description: This topic explains how to troubleshoot Microsoft Dynamics 365 Commerce Store Commerce app extension issues.
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

This topic explains how to troubleshoot Microsoft Dynamics 365 Commerce Store Commerce app extension issues.

## Extensions packages are not loading

### Extensions packages not appearing on the POS \> Settings page

Commerce runtime (CRT) triggers may not have been updated to include the extension package, or are not deployed. For more information, see [Commerce runtime (CRT) extensibility and triggers](../dev-itpro/commerce-runtime-extensibility-trigger.md).

### Extensions packages appearing on the POS \> Settings page, but manifest is not loading

Check to see if the extensions packages exist in the **C:\Program Files\Microsoft Dynamics 365\10.0\Store Commerce\Extensions** folder. If the packages do exist, there should be a POS folder there that contains the manifest.  

If there is no POS folder, check that the Store Commerce project is properly referencing the point of sale (POS) extension project. Validate the project reference path and make sure that it exists. 

The following example illustration shows that the installer project is having issues with the referenced extension project. 

![Store Commerce installer project reference not valid](media/ReferenceNotValid.png)
 
If the reference for the extension project is added correctly there will not be any warning or dependency issue in the installer project, as shown in the following example illustration.

![Store Commerce installer project reference valid](media/ReferenceValid.png)
 
