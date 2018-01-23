---
# required metadata

title: Install network printer devices in on-premises environments
description: This topic explains how to connect an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, to existing network printer devices.
author: TJVass
manager: AnnBe
ms.date: 11/13/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: SysCorpNetPrinterList
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Install network printer devices in on-premises environments

[!include[banner](../includes/banner.md)]

This topic explains how to connect an on-premises deployment of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, to existing network printer devices. Network printing in the on-premises application is supported by the [Print and Document Services](https://technet.microsoft.com/en-us/library/hh831468(v=ws.11).aspx) feature in Microsoft Windows Server 2016. This feature lets you centralize tasks that are related to printer management. To install and configure Print and Document Services, you must have administrative access to the server that hosts the primary instance of Application Object Server (AOS).

Two roles are associated with the configuration of network printing services:

- **Service Administrator** – The person who has this role is responsible for installing and configuring components of the platform infrastructure. Traditionally, this role is an Active Directory account that has elevated domain privileges. It has enough privileges to install components of Microsoft Windows Server.
- **Organization Administrator** – The person who has this role manages application security privileges. This Active Directory account is assigned to the **System Administrator** role in Finance and Operations.

Before the organization administrator can begin to add network printers, the service administrator must install and configure Print and Document Services on the server that hosts the primary AOS instance. The organization administrator can then begin to use built-in tools to configure network printer devices.

## Install and configure Print and Document Services

The environment administrator uses the information in this section to enable network printing services.

1. Install Print and Document Services by following the instructions in [Install Print and Document Services](https://technet.microsoft.com/en-us/library/jj134159(v=ws.11).aspx).
2. Configure Print and Document Services by following the instructions in [Configure Print and Document Services](https://technet.microsoft.com/en-us/library/jj134163(v=ws.11).aspx).
3. Follow these steps for each server that is used to host the AXService application:

    1. On the local server, start the **Local Users and Groups** manager.
    2. Select the **Groups** node.
    3. Right-click **Print Operators**, and then select **Add to Group**.
    4. Add the network Active Directory account that is used to run the AXService application to the group.
    5. Install network printers by using the AXService user account. This step helps guarantee that the printer driver is available to the AXService user account.
    6. Print a test page on the installed printers to make sure that all the connections are correctly configured.
    7. Restart the AXService application to help guarantee that the user's profile is correctly loaded so that it can look up the printer driver.

## Manage network printers

The system administrator of Finance and Operations uses the information in this section to define network printers.

1. Go to **Organization administration** > **Setup** > **Network printers**.
2. On the **Network printers** page, add new printers. For each printer, specify a name, description, path, and status. Make sure that the printer path matches the network path of the installed printer.

Items that are marked **Active** immediately become available to application users, so that they can begin to print document-style reports on network printer devices.
