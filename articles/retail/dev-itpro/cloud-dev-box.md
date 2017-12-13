---
# required metadata

title: Configuration steps for Retail developers working on cloud-hosted development boxes
description: This topic demonstrates the configuration steps for Retail developers working on cloud-hosted development boxes.
author: mugunthanm 
manager: AnnBe
ms.date: 12/08/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Retail, Operations 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: 
ms.search.validFrom: 2017-12-08
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Configuration steps for Retail developers working on cloud-hosted development boxes

Because developer cloud virtual machine (VMs) do not have admin access to the VMs, Modern POS (MPOS) development is possible if you use Cloud POS. Before starting the development for any retail application, configure Cloud POS as follows:

1. Open  Visual Studio and click **View** > **Application Explorer**. Wait for Internet Information Services (IIS) Express to start with all the Retail websites deployed. You should see the IIS tray icon in the task bar with all the Retail websites running, such as Cloud POS and Retail Server.
4. To debug CRT/RS extensions, attach the CRT/RS project to the IIS Express process.
5. When you open the Cloud POS project from the Retail SDK, the Configuration IIS Express may fail with the following error. 
    ```
    Filename: redirection.config
    Error: Cannot read configuration file
    ``` 
    To resolve this issue, follow these steps:
    1. Close Visual Studio.
    2. Rename the **%userprofile%\Documents\IISExpress\config** folder. Do not delete the files because you will copy the **applicationhost.config** file to a new location in step 4.
    3. Start Visual Studio again with the Cloud POS project. The **%userprofile%\Documents\IISExpress\config** folder will be recreated with the default config files.
    4. Copy the **applicationhost.config** file from the folder that you renamed in step 2, to the folder created in step 3. 

