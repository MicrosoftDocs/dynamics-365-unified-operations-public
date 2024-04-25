---
title: Run the Document Routing Agent as a Windows service
description: Learn how to select the execution mode that is used by the Document Routing Agent, including an overview of service applications and troubleshooting tips.
author: sericks007
ms.author: sericks
ms.topic: article
ms.date: 02/11/2021
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2
ms.assetid: 7adc7228-4360-4a54-8a3e-4d916e727dd2
---

# Run the Document Routing Agent as a Windows service

[!include [banner](../includes/banner.md)]

The Document Routing Agent includes an option that lets you select the mode of execution. The process can run as either a desktop application or a Microsoft Windows service. When the application runs as a Windows service, it can be started automatically after a computer restart. It can also be configured to run under the security context of a specific user account. This enhancement lets customers host the Document Routing Agent on secured domain resources such as network print servers.

This article provides important information that will help you select the correct execution mode.

## Service applications
An application is a program that a user interacts with on the desktop. A service is a process that runs in the background and doesn't have an active window. The Document Routing Agent now supports both execution modes. It's important that you understand why you might select one mode instead of the other and the steps that are involved in running the process as a service. For more information about Windows services, see [Introduction to Windows Service Applications](/dotnet/framework/windows-services/introduction-to-windows-service-applications). Here are some of the main benefits of running the Document Routing Agent as a background service:

- The service can be configured to start automatically after a computer restart. No user intervention is required.
- The service runs in the background. No active application runs in the notification area.
- The service routes documents without requiring that a user sign in by using cached credentials.

Although there are many benefits of running the Document Routing Agent as a Windows service, there are also limitations. The next section discusses an issue that affects the handling of document reports, such as checks, that require custom page margins.

## Documents that require custom margins
When the Document Routing Agent runs as a Windows service, document reports, such as checks, that require custom margins can't be printed directly to network printers. Instead, the Document Routing Agent automatically routes those document to a target folder. New configuration properties in the application's **Settings** dialog box let you define the target location for document reports that require custom margins.

When the Document Routing Agent runs as a desktop application, it continues to take advantage of Adobe Reader to spool the document to the shared printer device that is selected in finance and operations. To handle scenarios where documents that have custom margins must be printed, we recommend that you install the Document Routing Agent in multiple locations. Then install the printers that will handle those documents only on the Document Routing Agents that will run in desktop application mode. Alternatively, use a post-execution process to pick up the files in the target directory and direct them in the appropriate manner.

## Install the latest build
1. Save a copy of the current Document Routing Agent configuration file. This file is located at C:\\Users\\&lt;UserID&gt;\\AppData\\Local\\Microsoft\\Microsoft Dynamics 365 Finance Document Routing\\Microsoft.Dynamics.AX.Framework.DocumentRouting.config. In this path, &lt;UserID&gt; is the Active Directory Domain Services (AD DS) user name that the Document Routing Agent was installed under.
2. Uninstall the current version of the Document Routing Agent.
3. Install the latest version of the Document Routing Agent by following the instructions in [Install the Document Routing Agent to enable network printing](install-document-routing-agent.md).

    > [!NOTE]
    > Although you install the application at this point, don't run it yet.

4. Copy the configuration file from step 1, and paste it into the following directory: C:\\ProgramData\\Microsoft\\Microsoft Dynamics 365 Finance Document Routing. This step helps guarantee that all your previous configuration settings are used for the new version of the Document Routing Agent application.
5. Run the Document Routing Agent.
6. Sign in by using your Microsoft Entra ID (Azure AD) or your credentials for your finance and operations apps.
7. View and verify your settings and printers by clicking the appropriate menu items.

The next section provides detailed instructions for selecting the Windows service execution mode.

## Change the default execution mode
By default, the Document Routing Agent runs as a desktop application. To run the process as a Windows service, make sure that you're familiar with the process for [installing the Document Routing Agent to enable network printer devices](install-document-routing-agent.md). Then complete the following tasks.

### Update the execution mode for the Document Routing Agent
1. Start the Document Routing Agent by using the desktop icon.
2. Select the **Sign In** option, and sign in by using your Azure AD credentials.
3. On the ribbon, select **Settings**.
4. Enable the **Run as a Windows Service** option.
5. Provide a target folder for PDF files that are produced for documents that have custom margins.
6. Select **OK**, and close the Document Routing Agent window.

### Configure and start the Windows service
1. In Windows, start Service Manager.
2. In the list, select **Microsoft Dynamics 365 Finance Document Routing Service**.
3. Right-click the name, and then select **Properties**.
4. On the **Log On** tab, select the **This account** option, and then supply the AD DS credentials that are used to run the service.

    > [!NOTE]
    > The selected account must have access to the shared network devices.
    > The windows domain account ( or local machine account) used to run the windows service must be same as the account that starts the Document Routing Agent desktop app.

5. Select **OK**.
6. Start the service.

The Document Routing Agent is now running as a Windows service.

## Troubleshooting tips
### Verify the network printer connection
- Verify that the active account has enough access rights to the network printer.
- Verify that the user account can successfully print to the network device by using Notepad or another local application.

### Verify security roles
- To access the application links that are used to install the Document Routing Agent, the user must be part of the **Document routing client** security role.

### Review the service account's access rights
- Verify that the **DocumentRoutingService** service is running as a domain account that has access to the network devices.

### Refresh the Azure service token
- Azure authentication tokens must be **refreshed every 90 days** while the Document Routing Agent is running as a Windows service. To refresh the service token, start the client, and then sign out and sign back in by using the menu items.

### Disable shared printers for remote access
- When you connect to the host machine by using Microsoft Remote Desktop, make sure that you clear the **Printers** option in the **Local devices and resources** section on the **Local Resources** tab.

### Review the event logs
1. On the host machine, start Event Viewer.
2. Review the logs at **Application and Services Logs** \> **Microsoft** \> **Dynamics** \> **AX-DocumentRouting**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]