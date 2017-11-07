---
# required metadata

title: Install network printer devices in on-premises environments
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: TJVass
manager: AnnBe
ms.date: 11/07/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: AX 7.3.0

---

# Install network printer devices in on-premises environments

[!include[banner](../includes/banner.md)]


Provisioning Administrator:

1.  Follow [this
    link](https://technet.microsoft.com/en-us/library/jj134159(v=ws.11).aspx) to
    install Print and Document Services.

2.  Follow [this
    link](https://technet.microsoft.com/en-us/library/jj134163(v=ws.11).aspx) to
    configure Print and Document Services.

3.  For each VM running with AXService application:

    1.  Add AXService domain account to “Print Operators” user group via lusrmgr

        ![](media/3048eae34e89e7f3c1a26119a9f7b103.png)

    2.  Install network printers by using AXService user account. This step
        ensures the printer driver is available to AXService user account.

    3.  Print a test page with installed printers to make sure all the
        connections are configured correctly.

    4.  Restart AXService application to ensure the user’s profile is loaded
        correctly to look up printer driver.

AX Administrator:

1.  Open the Manage network printers page (Organization administration \> Setup
    \> Network printers).

2.  Add new printers by providing printer Name, Description, Path and Status.
    Make sure the printer path matches the network path of the installed
    printer.
