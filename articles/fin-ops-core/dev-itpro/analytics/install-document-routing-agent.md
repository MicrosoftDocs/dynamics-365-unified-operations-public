---
title: Install the Document Routing Agent to enable network printing
description: This article describes how to install and configure the Document Routing Agent for deployments of Microsoft Dynamics 365 Finance.
author: RichdiMSFT
ms.date: 09/01/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: richdi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: cd017bfd-2eba-4e8a-ab9b-a0ce393c2108
ms.search.form: SysCorpNetPrinterList
---

# Install the Document Routing Agent to enable network printing

[!include [banner](../includes/banner.md)]

This article describes how to install and configure the Document Routing Agent.  The Document Routing Agent is a downloadable application that you can use to enable network printing scenarios. You can enable network printers for specific companies by using in-client administrative pages.

## Preparing to install the Document Routing Agent

- Supported on Windows 8.1, Windows 10, Microsoft Windows Server 2012 R2, Microsoft Windows Server 2016, or Microsoft Windows Server 2019.
- Access to network printing resources requires Active Directory Domain Services (AD DS) authentication.
- When installing the Document Routing Agent, make sure you are logged in as the Admin user.
- The Microsoft Azure Active Directory (Azure AD) account that is used to configure the Document Routing Agent must share the same domain as the Azure tenant.
- The Document Routing Agent requires .NET 4.7.2 or later and Adobe Acrobat Reader 32-bit or 64-bit on the client.
- Configure Adobe client print settings to prevent document scaling.

Network printers that are registered for applications can be used by all legal entities (also known as companies) that are defined in the environment. Network printer settings are company-specific. Therefore, administrators can restrict access, based on the user's active company. For example, users in the active company might have access to all the network printers that are registered by the Document Routing Agent. However, users in another company won't have access to those printers until access is explicitly enabled for that company.

## Key concepts
This article will help you with the following tasks:

- Identify the key components that are involved in the support for network printing in applications.
- Learn about the function of the Document Routing Agent.
- Configure the Document Routing Agent to work against an existing application.
- Use administration pages to manage access to network printers.

## Install the Document Routing Agent
Applications use the Document Routing Agent to manage the spooling of documents to network printer devices. You can obtain the client by using direct links that are embedded in the web application. Use the following procedure to download the application to your local computer. You will then be able to access both local and network printers that are connected to your computer, from a single deployment.

1. Open the **Manage network printers** page (**Organization administration** &gt; **Setup** &gt; **Network printers**).
2. On the **Options** tab, in the **Application** group, click **Download document routing agent installer**.

    [![download-document-routing-agent-installer.](./media/download-document-routing-agent-installer.png)](./media/download-document-routing-agent-installer.png)

3. Run the downloaded file to begin the installation process.
4. Complete the setup process.

After the application is installed, you can begin to register local printers as network printers for the applications.

## Configure the Document Routing Agent
Use the following procedure to configure the client application so that it can communicate with the Azure services that host the documents that are in-flight.

1. Close all browser instances that are running the application. This resets the local Azure authentication tokens.
2. On your desktop, run the Document Routing Agent.
3. On the toolbar, click **Settings**.

    [![the-document-routing-agent-window.](./media/the-document-routing-agent-window.png)](./media/the-document-routing-agent-window.png)

4. Add the following settings:

    - **Application ID** – The ID that is unique to the application and should be entered automatically.
    - **finance and operations URL** – The base URL of the application.
    - **Azure AD tenant** – The domain name of the Azure AD.

5. Click **OK**.
6. Click **Sign In** to sign in to your account.

    > [!NOTE]
    > The account must share the same domain as the Azure AD that is associated with the application. The Document Routing Agent is now ready to process documents.

After you've successfully signed in, the **Printers** button becomes available on the toolbar.

## Register network printers
Before you complete this procedure, make sure that you've installed all the network printers on the local host computer. All the printer devices that are installed will be available for service registration. Be sure to select only the printers that you want to expose in the applications.

1. On the toolbar, click **Printers**.
2. Select the printers to make available in the applications.

    [![printers-to-add.](./media/printers-to-add.png)](./media/printers-to-add.png)

3. Specify a default name for the printer.
4. Click **OK**.

After you've completed this procedure, the selected printer devices are registered in the application's network printer catalog. System administrators can now enable the printers for access from within the application.

## Administer network printers
Use client pages to manage access to the network printers that have been registered by one or more Document Routing Agents. Network printers are uniquely identified by their path. Therefore, printers are listed one time, even if they have been registered by more than one Document Routing Agent. Use the following procedure to activate the Application Object Server (AOS) network printers.

1. Open the **Manage network printers** page (**Organization administration** &gt; **Setup** &gt; **Network printers**).

    [![manage-network-printers-page.](./media/manage-network-printers-page.png)](./media/manage-network-printers-page.png)

2. Edit the existing entries that are mapped to each network printer. As part of your changes, edit the connection path.
3. To include a printer as an option in the **Print Destinations** field, set the **Active** field to **Yes**.

The network printers can now be used in the application.

> [!NOTE]
> Ensure that your network printer destinations are kept up to date, and that document routing is properly configured with printers that are registered against Document Routing Agents. If documents are sent to a printer that no longer exists, the print queue will continue to grow and slow down queries that poll the print queue.
    
## Adjust the document routing history cleanup batch job
There is a cleanup batch job for document routing history that is enabled by default and runs daily. This batch job purges document routing history older than 7 days. This history is intended to be used by the customer for troubleshooting or traceability if there are issues with printing. Depending on how you intend to access this historical data, you should be able to reduce the retention period from the default value of 7 days, which is considered an upper limit. Having fewer records in this table will ensure that printing has optimal performance. You can configure this at `https://[host_adress]/?mi=DocumentRoutingHistoryCleanupConfig`. Configure the value for **JobHistoryHours** (number of hours to retain history). 

As part of the Document Routing Agent polling, a query is executed against this table. This query should execute quickly, but if there are a lot of records in this table, a large print job can be very slow. Ensure that this batch job is running daily, and configure this to reduce how much print history you retain. 

## Excluding printers with stuck print jobs
The **Enable excluded printers** setting has been added to handle problematic printers and drivers. When this setting is enabled, if a print job has been sent to the printer spool and hasn't returned with a **Pending** status, the Document Rourting Agent will add the printer to an excluded list after the time specified in the **Abort a stuck print job at** field. (The default time is five mintues). The **Reset this printer every x minutes** field, which has a default value of 30 minutes, adds the printer back after the specified time and attempts sending print jobs. 

The administrator can also see any excluded printers in the **Network printers** section in the **Spooler status** column. Any excluded printer can be reset by selecting the **Reset** icon in the **Reset** column. In addition, a test page can be sent to the printer using the **Print test page** button. 

## Frequently asked questions
### Does the Document Routing Agent have to be installed on each computer where a user connects by using a browser?

No. Client installations of the Document Routing Agent can be shared by individuals who access the provisioned environment. We recommend that you install agents on one or more Print Servers or other domain-hosted clients that have access to network printers.

### If the Document Routing Agent belongs on a network Print Server, why doesn't the client run as a service?

The Document Routing Agent now supports running in the background as a service. You need to ensure that you have downloaded the latest version of the client. For more information, see [Run the Document Routing Agent as a Windows service](run-document-routing-agent-as-windows-service.md).

### Do I need to update credentials or refresh Azure authentication tokens on a recurring basis?

Yes. The Azure Active Directory token must be refreshed every 90 days. Failing to do so will prevent the Document Routing Agent from being able to authenticate and retrieve printing instructions applications.

### Is the Document Routing Agent supported on Microsoft Windows Server 2019?

Yes. The Document Routing Agent is supported on Microsoft Windows Server 2019.

> [!NOTE]
> If the server is configured to prevent background service, the Document Routing Agent client will not be able to run as a service. For more information, see [Run the Document Routing Agent as a Windows service](run-document-routing-agent-as-windows-service.md).

### Will Microsoft add support for Microsoft Windows Server 2008 servers?

No, not at this time. There are several dependencies on Azure capabilities that are available only in Microsoft Windows Server 2012 R2 and Microsoft Windows Server 2016.

### Does the user who installs the Document Routing Agent have to be part of a finance and operations apps security group?

Yes. To access the agent installation links, the user must be part of the **Document routing client** security role.

### How many network printers can the Document Routing Agent support?

The number of supported network printers depends on the number of legal entities and the number of network printers deployed. If you have fifty printers and one legal entity, a single Document Routing Agent can handle the load (although you'd want more than one to ensure high availability). If you have a large number of printers and legal entities, we recommend that you do some performance testing to determine the number of Document Routing Agents that you'll need.

### How many Document Routing Agents should be configured per printer?

Multiple Document Routing Agents should be configured for your printers to ensure high availability. However, you should limit the number of agents per printer to no more than most three agents. Each Document Routing Agent poll needs to query the queue to pick up documents sent to printers registered in that Document Routing Agent client. The more printers that are associated with a Document Routing Agent, the slower the query will be. This is especially true when there are a large number of pending jobs in the queue. It is better to have a smaller number of printers across two to three Document Routing Agents, than a large number of printers across three or more Document Routing Agents.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

