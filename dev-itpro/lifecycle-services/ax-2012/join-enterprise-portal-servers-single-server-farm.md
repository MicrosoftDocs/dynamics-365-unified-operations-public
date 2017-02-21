---
# required metadata

title: Join Enterprise Portal servers into a single server farm (AX 2012)
description: This article explains how to join Enterprise Portal servers (for Microsoft Dynamics AX 2012) into a single server farm. 
author: aneesmsft
manager: AnnBe
ms.date: 2015-12-13 05 - 34 - 41
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 27431
ms.assetid: 05316e9d-818e-4f4b-901c-2e67fe8edfd1
ms.search.region: Global
# ms.search.industry: 
ms.author: aneesa
ms.dyn365.ops.intro: 
ms.dyn365.ops.version: 2012

---

# Join Enterprise Portal servers into a single server farm (AX 2012)

This article explains how to join Enterprise Portal servers (for Microsoft Dynamics AX 2012) into a single server farm. 

When Microsoft Dynamics Lifecycle Services (LCS) deploys Enterprise Portal (EP) servers, each EP server is deployed into its own server farm. The steps in this article show how to join all EP servers into a single server farm. The basic idea is to keep the server farm on one EP server and join all the other EP servers to that farm. The information in this article is based on the following assumptions:

-   *N* EP servers are deployed by LCS, and these servers are labeled EP-01, EP-02, EP-03...EP-0*N*.
-   The load balancer is named AzureILB01.
-   You're using EP-01 as the single server farm, and all the other EP servers will join that farm.

## Overview
The following image shows the process for joining EP servers into a single server farm. [![ProcessFlow\_ConfigureEPServersInFarm](./media/processflow_configureepserversinfarm.png)](./media/processflow_configureepserversinfarm.png)

## Put EP servers into a single server farm
1.  Log on to EP-01 by using the Dynamics Installer User service account.
2.  Start Microsoft SharePoint 2013 Central Administration.
3.  Go to **System settings** &gt; **Configure alternate access mappings**.
4.  Click **Add Internal URLs**. The following screen shot shows how to add a mapping for EP-02 on port 81, which is the port that the EP site is created on. Repeat this step for every EP server that is deployed by LCS.[![AddInternalURLs](./media/addinternalurls.png)](./media/addinternalurls.png)
5.  Click **Edit Public URLs**, and enter appropriate values:
    -   **Default:** Use the load balancer URL + port 81.
    -   **Intranet:** Use EP-01 (the SharePoint server farm virtual machine) + port 81.
    -   **Internet:** Use the publicly registered URL + port 81.

    [![EditPublicZoneURLs](./media/editpubliczoneurls.png)](./media/editpubliczoneurls.png)
6.  Open Registry Editor (regedit), and create the following registry key:
    -   **Path:** HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Contro\\Lsa\\MSV1\_0
    -   **Key details, key value:** The load balancer name and the fully qualified name

    [![EditMultiString](./media/editmultistring.png)](./media/editmultistring.png)
7.  Open a **Command Prompt** window, and get the IP address of the local machine by running the **ipconfig** command.
8.  In Notepad, open the C:\\Windows\\System32\\drivers\\etc\\hosts file, and map the load balancer name to the local machine IP address. This mapping is used to test that the local EP server is working.[![NotePad](./media/notepad.png)](./media/notepad.png)
9.  Repeat steps 6 through 8 on every EP server that is deployed by LCS.
10. Log on to the EP-02 server by using the Dynamics Installer User service account.
11. Go to the drive where the Dynamics installer is stored (this drive is most likely drive F). Right-click **Setup**, click **Run as administrator**, and then follow these steps:
    1.  Click **Install Microsoft Dynamics AX components**.
    2.  On the **Welcome** page, click **Next**.
    3.  Click **Add or modify components**, and then click **Next**.
    4.  Under **Web server components**, select the **Enterprise Portal** check box. Click **OK** to acknowledge that you want to install EP, and then click **Next**.
    5.  Make sure that there are no validation errors, and then click **Next**.
    6.  Enter the BC proxy user password, and then click **Next**.
    7.  On the **Configure a Web site for Enterprise Portal **page, select the web application.
    8.  Select the **Configure for Windows SharePoint Services** check box.
    9.  Select the **Restart IIS after installation is completed** check box, and then click **Next**.

    [![Configure a Web site for EP](./media/configure-a-web-site-for-ep.png)](./media/configure-a-web-site-for-ep.png)
12. Click **Next** until the installation is completed.
13. Repeat steps 10 through 12 on servers EP-03 through EP-0*N*. (You must re-install EP on every EP server, except the single server where the farm is configured. In our example, this server is EP-01.)
14. Follow these steps on every EP server, EP-01 through EP-0*N*:
    1.  Open the Internet Information Services (IIS) administration console (inetmgr).
    2.  Go to **Sites** &gt; **SharePoint – 81**.
    3.  Right-click, and then click **Edit bindings**.
    4.  Double-click the binding to open the **Edit Site Binding** dialog box.
    5.   In the **Host name** field, enter the load balancer name.

    [![Edit Site Binding](./media/edit-site-binding.png)](./media/edit-site-binding.png)
15. Follow these validation steps on every EP server:
    1.  In a **Command Prompt** window, run the **iisreset** command.
    2.  Start Internet Explorer, and go to **http://AzureILB01:81/sites/DynamicsAx**.
    3.  Make sure that the Role Center page is rendered without error.

## Configure AppFabric cache
1.  Log on to the EP-01 server by using the Dynamics Install User service account.
2.  Open a Microsoft Windows PowerShell **Command Prompt** window as an administrator.
3.  Run the **Use-CacheCluster** command to set the context of your Windows PowerShell session to a specific cache cluster.
4.  Run the **New-Cache** command to create a new named cache. Make a note of the name that you specify. (You'll enter this cache name in the next procedure.)
5.  Run the **Grant-CacheAllowedClientAccount** command, and specify the .NET Business Connector proxy. (This is the account that is used by the EP application pool).
6.  Run the following command: **Set-CacheConfig -Secondaries 1**
    1.  When you're prompted for the cache name, enter the name from step 4.
    2.  When you're asked whether you want to continue, enter **Y**.

7.  If step 6 causes an error, try to run the commands in the following order:
    1.  stop-cachecluster
    2.  Set-CacheConfig -Secondaries 1

8.  Export the configuration by running the **Export-CacheClusterConfig** command. Specify a name for the file. This file can be saved anywhere on the local computer.
9.  Open the file that you just created, and add the following configuration to the **&lt;advancedProperties&gt;** section.

        <transportProperties maxBufferSize="1000000000" />

10. Import the configuration by running the following command: **Import-CacheClusterConfig c:\\newConfig.xml** When you're asked whether you want to continue, enter **Y**.
11. Run the **Start-CacheCluster** command to start the cache.
12. In Notepad, open the web.config file (C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\81\\web.config) in admin mode.
13. Locate the **&lt;configSections&gt;** section. Add the following **section** element.

    ```
    <section name="dataCacheClient" type="Microsoft.ApplicationServer.Caching.DataCacheClientSection, Microsoft.ApplicationServer.Caching.Core, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" allowLocation="true" allowDefinition="Everywhere" />
    ```

14. Add the following **dataCacheClient** element to the web.config file after the **&lt;/configSections&gt;** tag.

    1.  Replace every instance of “Host\_server\_name” with the name of an EP server.
    2.  Replace “default” with the name that you specified when you ran the **New-Cache** command.

    <!-- -->

        <!-- velocity -->
        <dataCacheClient dataCacheServiceAccountType="DomainAccount">
        <localCache isEnabled="false" />
        <hosts>
        <!--List of hosts -->
        <!-- Replace highlighted with your own EP server name -->
        <host name="EP-01" cachePort="22233" /> 
        <host name="EP-02" cachePort="22233" />  
        <host name="EP-03" cachePort="22233" /> 
        <host name="EP-0N" cachePort="22233" /> 
        </hosts>
        </dataCacheClient>
        <Microsoft.Dynamics>
        <AppFabricCaching CacheName="default" />
        </Microsoft.Dynamics>
        <!-- velocity -->

15. Repeat steps 12 through 14 on every EP server that is deployed by LCS.
16. On the EP-01 server, in a Windows PowerShell window, run the **stop-cachecluster** command.
17. Run the **start-cachecluster** command.

## Validate AppFabric
1.  On one of the EP servers, in the Windows Services console, verify that AppFabricCachingService is running.
2.  Open a Windows PowerShell **Command Prompt** window as an administrator.
3.  Run the **Get-CacheStatistics** default command. The result should show all zeros.
4.  Restart the web service on the EP server by running the **iisereset** command.
5.  Open EP, and go to **Sales**.
6.  Run the **Get-CacheStatistics** default command again, and verify that the cache shows values. This result indicates that cache distribution is working.

## Clean up
Because every EP server was deployed into its own server farm, after you join all the servers into a single farm, the databases that were created for other EP server farms must be removed from SQL.

-   Spfarm\_admincontent\_ep-02
-   Spfarm\_admincontent\_ep-03
-   …
-   Spfarm\_admincontent\_ep-0*N*
-   Spfarm\_config\_ep-02
-   Spfarm\_config\_ ep-03
-   …
-   Spfarm\_config\_ep-0*N*
-   WSS\_Content\_\*

To learn the name of the WSS\_Content\_\* database for a particular site, follow these steps.

1.  Start SharePoint Central Administration.
2.  Go to **Application management** &gt; **View site collection**.
3.  In the upper-right corner, select the site that is hosted on port 81. The result screen should indicate which database is used for the selected site.
4.  Delete all WSS\_Content\_\* databases that aren't used by the server that site 81 is created on. In this case, keep the WSS\_Content\_\* database that is used by EP-01, and delete every other database that has a name that starts with WSS\_Content\_\*.


