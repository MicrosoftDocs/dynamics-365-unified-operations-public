---
# required metadata

title: Troubleshoot Store Commerce extension issues
description: This topic explains how to troubleshoot Store Commerce extension issues.
author: Mugunthan-Mani
ms.date: 12/05/2022
ms.topic: Troubleshooting
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgriffin
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2022-05-12
ms.dyn365.ops.version: 10.0.25

---


### Troubleshoot Store Commerce extension issues

This topic explains how to troubleshoot Store Commerce extension issues.

### Extensions are not loading

# Extensions are packages not showing up in the POS > Setting page
CRT Triggers is not updated to include the extension package or not deployed, refer this doc to update the CRT trigger.

Extensions are showing up in the POS > Settings page but manifest is not loading Check the **C:\Program Files\Microsoft Dynamics 365\10.0\Store Commerce\Extensions** to see if extension package exists in the folder. 

If the packages do exist, there should be a POS folder that contains the manifest.  

If there is no POS folder, check the Store Commerce project is properly referencing the POS extension project. Validate the project reference path and make sure it exists, the below image shows the installer project is having issues with the referenced extension project. 
![Store Commerce deployment options.](media/ReferenceNotValid.png)
 
If the reference for the extension project is added correctly then there will not be any warning or dependency issue in the installer project.
![Store Commerce deployment options.](media/ReferenceValid.png)
 
