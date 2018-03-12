---
# required metadata

title: Upgrade the Document Routing Agent
description: TBD
author: TJVass
manager: AnnBe
ms.date: 03/12/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: tjvass
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Upgrade the Document Routing Agent

[!include[banner](../includes/banner.md)]

The below steps needs to be performed on **each of the machines with DRA
installed** one by one.

1.  **Important**: **If the DRA is running as windows service**, please make
    sure that the service account information (user name and password) is
    available. This will need to be used after DRA is upgraded. The service
    account information can be obtained by open “Services” window and find the
    “Microsoft Dynamics 365 Document Routing Service”.

    ![](media/0ead6f8d15e287ff0de9dbbc8e3f5cbd.png)

2.  Uninstall existing Document Routing Agent (DRA)

    Open the “Programs and Features” window, and then find and uninstall the
    “Microsoft Dynamics 365 for Finance and Operations: **Document Routing**”.

    During the uninstallation, the below window might be shown, please choose
    “Automatically close applications and attempt to restart them after setup is
    complete.”

![cid:image003.png\@01D39B46.C7814470](media/1ae8c98a774df5d3ccaec83368be0270.png)

1.  Reinstall the latest DRA.

    Go to the “Network Printers” page of Dynamics 365 F&O. Download the latest
    DRA and install it to the DRA machine.

    ![](media/2e707cfcc1b4d1032c4dd3a60d8979c0.png)

2.  Start the “Document Routing Agent” from the link on the desktop and sign in.
    Then click the “Printers” menu to make sure it shows correct printers.

3.  If the DRA is running as a windows service, please change the service
    account to the same account used previously (noted in step 0).
