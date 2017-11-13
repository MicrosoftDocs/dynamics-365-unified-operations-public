---
# required metadata

title: Install network printer devices in on-premises environments
description: This articles describes the process for connecting a Dynamics 365 for Finance and Operations on-premises deployment to existing network printer devices. 
author: TJVass
manager: AnnBe
ms.date: 11/13/2017
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

This articles describes the process for connecting a Dynamics 365 for Finance and Operations on-premises deployment to existing network printer devices. Network printing in the on-premises application is supported by the [Print and Document Services](https://technet.microsoft.com/en-us/library/hh831468(v=ws.11).aspx) feature in Windows Server 2016, which allows you to centralize printer management tasks.  Installing and configuring Print and Document Services requires administrative access to the server hosting the primary AOS instance.

There are two roles associated with configuring the network printing services:
-  <b>Service Administrator</b> - This person is responsible for installing and configuring the platform infrastructure components.  Traditionally, an active directory account with elevated domain privileges, this role has sufficient privileges to install Windows Server components.

-  <b>Organization Administrator</b> - This person manages application security privileges.  This active directory account is assigned to the System Administrator role in Finance and Operations.

Before the Organization Administrator can begin adding network printers, the Service Administrator must install and configure Print and Document Services on the server hosting the primary AOS instance.  Once that is complete, the Organization Administrator can begin using built-in tools to configure network printer devices.

## Install and configure Print and Document Services

The following section is used by the environment administrator to enable network printing services.

1.  Use the [instructions here](https://technet.microsoft.com/en-us/library/jj134159(v=ws.11).aspx) to install Print and Document Services.
2.  Use the [instructions here](https://technet.microsoft.com/en-us/library/jj134163(v=ws.11).aspx) to configure Print and Document Services.


> [!Important]
> Perform the following actions for each server used to host the application "AXService".

1.  Start the <b>Local Users and Groups</b> manager on the local server.
2.  Select the <b>Groups</b> node.
3.  Select <b>Print Operators</b>, then right + click and select <b>Add to Group</b>
        ![](media/3048eae34e89e7f3c1a26119a9f7b103.png)
4.  Add the network active directory account used to run the AXService to the group.
5.  Install network printers by using the AXService user account. This step ensures the printer driver is available to the AXService user account.
6.  Print a test page with installed printers to make sure all the connections are configured correctly.
7.  Restart the AXService application to ensure the user’s profile is loaded correctly to look up printer driver.

## Manage network printers
The following section is used by the system administrator of Finance and Operations to define network printers.

1.  Open the **Network printers** page (**Organization administration > Setup > Network printers**).
2.  Add new printers by providing the **Name**, **Description**, **Path**, and **Status**. Make sure the printer path matches the network path of the installed printer.


Items marked <b>Active</b> will immediately become available for application users to begin printing document-style reports on network printer devices.
