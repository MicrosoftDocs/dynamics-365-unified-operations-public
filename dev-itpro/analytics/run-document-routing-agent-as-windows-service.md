---
# required metadata

title: Run the Document Routing Agent as a Windows service
description: The Document Routing Agent can be run as either a desktop application or a Microsoft Windows service. This topic provides important information that will help you select the correct execution mode.
author: TJVass
manager: AnnBe
ms.date: 09/11/2017
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
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 191133
ms.assetid: 7adc7228-4360-4a54-8a3e-4d916e727dd2
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2

---

# Run the Document Routing Agent as a Windows service

[!include[banner](../includes/banner.md)]


The Document Routing Agent can be run as either a desktop application or a Microsoft Windows service. This topic provides important information that will help you select the correct execution mode.

The Document Routing Agent includes an option that lets you select the mode of execution. The process can run as either a desktop application or a Windows service. When the application runs as a Windows service, it can be started automatically after a computer restart. It can also be configured to run under the security context of a specific user account. This enhancement lets customers host the Document Routing Agent on secured domain resources such as network print servers.

## Service applications
An application is a program that a user interacts with on the desktop. A service is a process that runs in the background and doesn't have an active window. The Document Routing Agent now supports both execution modes. It's important that you understand why you might select one mode instead of the other and the steps that are involved in running the process as a service. For more information about Windows services, see [Introduction to Windows Service Applications](https://docs.microsoft.com/en-us/dotnet/framework/windows-services/introduction-to-windows-service-applications). Here are some of the main benefits of running the Document Routing Agent as a background service:

-   The service can be configured to start automatically after a computer restart. No user intervention is required.
-   The service runs in the background. No active application runs in the notification area.
-   The service routes documents without requiring that a user sign in by using cached credentials.

Although there are many benefits of running the Document Routing Agent as a Windows service, there are also limitations. The next section discusses an issue that affects the handling of document reports, such as checks, that require custom page margins.

## Documents that require custom margins
When the Document Routing Agent runs as a Windows service, document reports, such as checks, that require custom margins can't be printed directly to network printers. Instead, the Document Routing Agent automatically routes those document to a target folder. New configuration properties in the application's **Settings** dialog box let you define the target location for document reports that require custom margins. 

When the Document Routing Agent runs as a desktop application, it continues to take advantage of Adobe Reader to spool the document to the shared printer device that is selected in Finance and Operations. To handle scenarios where documents that have custom margins must be printed, we recommend that you install the Document Routing Agent in multiple locations. Then install the printers that will handle those documents only on the Document Routing Agents that will run in desktop application mode. Alternatively, use a post-execution process to pick up the files in the target directory and direct them as appropriate.

## Instal the latest build
1.  Save a copy of the current Document Routing Agent configuration file. This file is located at C:\\Users\\&lt;UserID&gt;\\AppData\\Local\\Microsoft\\Microsoft Dynamics 365 for Finance and Operations Document Routing\\Microsoft.Dynamics.AX.Framework.DocumentRouting.config, where &lt;UserID&gt; is the Active Directory Domain Services (AD DS) user name that the Document Routing Agent was installed under.
2.  Uninstall the current version of the Document Routing Agent.
3.  Install the latest version of the Document Routing Agent by following the instructions in [Install the Document Routing Agent to enable network printer devices](install-document-routing-agent.md). 

    > [![Note]
    > Although you install the application at this point, don't run it yet.

4.  Copy the configuration file from step 1, and paste it into the following directory: C:\\ProgramData\\Microsoft\\Microsoft Dynamics 365 for Finance and Operations Document Routing. This step helps guarantee that all your previous configuration settings are used for the new version of the Document Routing Agent application.
5.  Run the Document Routing Agent.
6.  Sign in by using your Microsoft Azure Active Directory (Azure AD)/Finance and Operations credentials.
7.  View and verify your settings and printers by clicking the appropriate menu items.

The next section provides detailed instructions for selecting the Windows service execution mode.

## Change the default execution mode
By default, the Document Routing Agent runs as a desktop application. To run the process as a Windows service, make sure that you are familiar with the process for [installing the Document Routing Agent to enable network printer devices](install-document-routing-agent.md), and then complete the following tasks.

### Task 1: Update the execution mode for the Document Routing Agent

1.  Start the Document Routing Agent by using the desktop icon.
2.  Select the **Sign In** option, and sign in by using your Azure AD credentials.
3.  On the ribbon, click **Settings**.
4.  Enable the **Run as a Windows Service** option.
5.  Provide a target folder for PDF files that are produced for documents that have custom margins.
6.  Click **OK**, and close the Document Routing Agent window.

### Task 2: Configure and start the Windows service

1.  Open Service Manager in Windows.
2.  Select the **Microsoft Dynamics 365 for Finance and Operations Document Routing Service** item in the list.
3.  Right-click the name, and then click **Properties**.
4.  On the **Log On** tab, select the **This account** option, and then supply the AD DS credentials that are used to run the service. **Note:** Make sure that the selected account has access to the shared network devices.
5.  Click **OK**.
6.  Start the service.

The Document Routing Agent is now running as a Windows service.

## TROUBLESHOOTING
#### 1.  Verify the network printer connection
-   Check to make sure the active account has sufficient access rights with the **Network Printer**
-   Verify that the user account is able to print successfully on the network device using Notepad or other local application
    
#### 2. Dynamics 365 Security Roles
-   To access the application links to install the Document Routing Agent, the user must be part of the **Document routing client security role**
    
#### 3.  Review the service account's access rights
-   Ensure that the **DocumentRoutingService** service is running as a domain account that has access to the network devices
    
#### 4.  Refresh Azure Service Token  
-   Azure authentication tokens must be **refreshed every 90 days** while the Document Routing Agent is running as a Windows Service
-   Open the client and use the menu item commands to **Sign Out** and then **Sign In** to refresh the service token
    
#### 5.  Disable shared printers for Remote Access
-   When connecting to the host machine using Remote Desktop, ensure that you uncheck the **Printers** option in the Local devices and resources section on the Local Resources tab 
    
#### 6.  Check the Event logs
-   Open the system Event Viewer on the host machine 
-   Review logs under:  **Application and Services Logs > Microsoft > Dynamics > AX-SSRSReportsShared**

