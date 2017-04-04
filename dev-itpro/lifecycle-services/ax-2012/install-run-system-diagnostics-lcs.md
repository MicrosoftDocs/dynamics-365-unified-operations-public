---
# required metadata

title: Install and run System diagnostics (AX 2012)
description: In Microsoft Dynamics Lifecycle Services, System diagnostics includes an on-premises component that must be installed before you can use the service to discover Microsoft Dynamics AX environments and collect data.
author: kfend
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18861
ms.assetid: 075b4e28-162f-47ae-8713-392d711bdaff
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Install and run System diagnostics (AX 2012)

In Microsoft Dynamics Lifecycle Services, System diagnostics includes an on-premises component that must be installed before you can use the service to discover Microsoft Dynamics AX environments and collect data.

Install the System diagnostics on-premises component
----------------------------------------------------

To install the System diagnostics on-premises component, the following is required:

-   A service account with specific permissions on the local computer and the Microsoft Dynamics AX business database.
-   An X509 certificate . You can either use an existing certificate, or have the installer create one for you. Each X509 certificate is associated with a single project. Diagnostics from an environment can be uploaded to only one project.
-   Microsoft .NET 4.5 or 4.5.1

### Configure the service account for System diagnostics

This section describes the permissions that are required for the service account that the Lifecycle Services Diagnostic Service (LCSDiagFXService.exe) runs as.

-   The service account must be a domain account that is a user in Microsoft Dynamics AX and a member of the **BusinessConnector** role.We strongly recommend that, if possible, the account be the same account used for the .NET Business Connector proxy. For more information, see [Specify the .NET Business Connector proxy account](http://technet.microsoft.com/library/3e46dc0a-2ff4-4a06-ae61-041e52dcc774(AX.60).aspx) and [Assign users to security roles](http://technet.microsoft.com/library/214ee45b-5b99-4ea8-9454-f4297f68e38c(AX.60).aspx).

    | **Note**                                                                                                                     |
    |------------------------------------------------------------------------------------------------------------------------------|
    | If you reuse the .NET Business connector proxy account, you must still add it as a member of the **BusinessConnector** role. |

-   The service account must have read access to specific registry keys in the HKEY\_LOCAL\_MACHINE hive on all of the computers that run AOS instances and host Microsoft Dynamics AX business databases, so that the Lifecycle Services Diagnostic Service can discover environments and collect data.
-   The service account must be a member of the **Event Log Readers** local group on each server in the environment, so that the Lifecycle Services Diagnostic Service can read the Windows event logs.
-   The service account must have read access to the Microsoft Dynamics AX business database (**db\_datareader**), and must have VIEW SERVER STATE permission for the SQL Server instance, so that Lifecycle Services Diagnostic Service can run default dynamic management views in SQL Server.

#### Configure read permissions to the registry

On each server in your environment that hosts an AOS instance or Microsoft Dynamics AX SQL Server business database, you must grant read access to a registry key in the HKEY\_LOCAL\_MACHINE hive to the service account for the System diagnostics.

| **Caution**                                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The following procedure includes editing the Windows Registry. Editing the registry incorrectly can cause serious problems that may require you to reinstall Windows. Microsoft cannot guarantee that problems resulting from incorrectly editing the registry can be solved.You should make a backup copy of the registry files (System.dat and User.dat) before you edit the registry. |

To grant access to collect data from the Windows registry on the server that hosts the SQL Server business database:
1.  Click **Start**, click **Run**, type **regedit**, and then press **Enter**.
2.  Expand **HKEY\_LOCAL\_MACHINE**, navigate to the subkey **SystemCurrentControlSetControlPriorityControl**, right-click it and select **Permissions**.
3.  Add the user that you want to associate with the Lifecycle Services Diagnostic Service.
4.  Select the user that you added, and then allow read permissions.
5.  Click **Advanced Security Settings**, and then ensure that the permissions are inherited by the child objects.

To grant access to collect data from the Windows registry on a server that hosts one or more AOS instances:
1.  Click **Start**, click **Run**, type **regedit**, and press **Enter**.
2.  Expand **HKEY\_LOCAL\_MACHINE**, navigate to the subkey **SystemCurrentControlSetServicesDynamics Server6.0**, right-click it and select **Permissions**.
3.  Add the user that you want to associate with the Lifecycle Services Diagnostic Service.
4.  Select the user that you added, and then allow read permissions.
5.  Click **Advanced Security Settings**, and then ensure that the permissions are inherited by the child objects.
6.  Repeat for all AOS instances in each environment that you want to collect data from.

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Important</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>As you are configuring rights in the registry, do not reduce account privileges that already exist.For more information about Advanced security settings, see:
<ul>
<li><a href="http://technet.microsoft.com/en-us/library/jj134043.aspx">Windows Server 2012 Access Control and Authorization Overview</a></li>
<li><a href="http://technet.microsoft.com/en-us/library/cc730772.aspx">Windows Server 2008 R2 Advanced Security Settings Properties Page - Permissions Tab</a></li>
</ul></td>
</tr>
</tbody>
</table>

#### Edit the Group Policy on the AOS

You must make the services of the AOS remotely accessible in Group Policy.

1.  On the computer running the AOS instance, click **Start** &gt; **Run**, type **gpedit.msc**, and then press **Enter**.
2.  In the left pane, expand **Computer Configuration** &gt; **Windows settings** &gt; **Security settings** &gt; **Local policies** &gt; **Security options**.
3.  In the right pane, double-click **Network access: Remotely accessible registry paths and sub-paths**.
4.  If the following paths are not in the list, add them to the end of the list and then click **OK**.
    -   SystemCurrentControlSetControlPriorityControl
    -   SystemCurrentControlSetservicesDynamics Server6.0

#### Configure Windows event log and WMI permissions

The service account must be able to read the Windows event logs on each server in the environment, and must be able to monitor remote Windows Management Instrumentation connections. For more information, see [Add a member to a local group](http://technet.microsoft.com/en-us/library/cc772524(v=WS.10).aspx).

-   On each server in the environment, add the service account to the **Event Log Readers** local group, the **Distributed COM Users** local group and the **Performance Monitor Users** local group.

#### Secure the remote Windows Management Instrumentation connections

On each server in your environment that hosts an AOS instance or Microsoft Dynamics AX SQL Server business database, ensure that you secure the remote Windows Management Instrumentation (WMI) connection.

1.  Click **Start** &gt; **Run**, type **DCOMCNFG**, and then click **OK**.
2.  In the **Component Services** dialog box, expand **Component Services**, expand **Computers**, and then right-click **My Computer** and click **Properties**.
3.  In the **My Computer Properties** dialog box, click the **COM Security** tab.
4.  Under **Launch and Activation Permissions**, click **Edit Limits**.
5.  In the **Launch Permission** dialog box, follow these steps if your name or your group does not appear in the **Groups or user names** list:
    1.  In the **Launch Permission** dialog box, click **Add**.
    2.  In the **Select Users, Computers, or Groups** dialog box, in the **Enter the object names to select** box, type **Distributed COM Users**, click **Check Names**, and then click **OK**.
    3.  Click **Add**.
    4.  In the **Enter the object names to select** box, type **Performance Monitor Users**, click **Check Names**, and then click **OK**.
    5.  Select **Allow** for each of the permissions (Local Launch, Remote Launch, Local Activation, Remote Activation) for each of these groups, and then click **OK**.

6.  Apply the WMI control security settings to all namespaces:
    1.  Click **Start** &gt; **Run**, type **wmimgmt.msc**, and then click **OK**.
    2.  Right-click **WMI Control (Local)**, and then click **Properties**.
    3.  On the **Security** tab, click **Root**, click **Security**, and then click **Add**.
    4.  Under **Enter the object names to select**, type Distributed COM users, click **Check Names**, and then click **OK**.
    5.  Click **Advanced**.
    6.  Select **Distributed COM Users** and then click **Edit**.
    7.  Select **This namespace and subnamespaces**.
    8.  Select **Allow** for the following permissions: Execute Methods, Enable Account, and Remote Enable, and then click **OK**.

7.  Repeat step 6 for the Performance Monitor Users group, and then close all windows.

For more information, see [Securing a Remote WMI Connection](http://msdn.microsoft.com/en-us/library/windows/desktop/aa393266(v=vs.85).aspx).

#### Configure SQL Server permissions

The service account must be able to read the data in the Microsoft Dynamics AX business database and must have access to the default dynamic management views in SQL Server.

1.  Add the service account as a login to the SQL Server instance where the Microsoft Dynamics AX business database is installed.For information about how to perform this step, see [Create a Login](http://msdn.microsoft.com/en-us/library/aa337562.aspx).
2.  Add the account as a user of the business database.For information about how to perform this step, see [How to: Create a Database User](http://msdn.microsoft.com/en-us/library/aa337545.aspx).
3.  Add the service account to the db\_datareader role in the business database.For information about how to perform this step, see [Join a Role](http://msdn.microsoft.com/en-us/library/ff877886.aspx).
4.  Grant the service account the VIEW SERVER STATE permission in the SQL Server instance.
    1.  In SQL Server Management Studio, expand **Databases**, right-click the **Microsoft Dynamics AX** database, and then click **Properties**.
    2.  Click **Permissions**, and then click **View server permissions**.
    3.  In the **Logins or Roles** list, click the user to whom you want to grant the permission.
    4.  In the **Explicit permissions for user** list, select the **Grant** check box next to **View server state permission**.

### Verify that the .NET Business connector service is running in the environment

The Business Connector service must be running on the host where the Lifecycle Services Diagnostic Service is installed. If more than one environment is to be discovered, the .Net Business Connector proxy account must be the same for each server that is running a Microsoft Dynamics AX Application Object Server (AOS) instance. For more information, see [Install the .NET Business Connector](http://technet.microsoft.com/library/c67944e8-73c5-4434-94d6-84484c810333(AX.60).aspx).

### Install the Microsoft Dynamics Lifecycle Services System diagnostics

To install the on-premises component of System diagnostics, you must be a member of the Administrator group on the local computer.

1.  [Go to Lifecycle Services](https://lcs.dynamics.com).
2.  Open a project and click the **System diagnostics** tile.
3.  On the **Admin** page, download the compressed installer (**LCSDiagFX\_x64.zip.**).
4.  Extract the installer to a computer that is running a Microsoft Dynamics AX client.The computer must have network access to all other servers in the environment, and must be running the .NET Business Connector if you are using the NET Business Connector proxy account as a service account.

    | **Important**                                                                                                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | In a production environment, we recommend that you install the on-premises component on a computer that is running only a client, not on computers that are also running an AOS instance or a SQL Server instance. |

5.  Run **Setup.exe**.
    
    | **Note**                           |
    |------------------------------------|
    | Do not run the .msi file directly. |

6.  Accept the license terms.
7.  If you have an existing local X509 certificate, on the **Select the certificate type** page, click **Use existing**. If you do not have an X509 certificate, perform the following steps:
    1.  On the **Select the certificate type** page, click **Create new**.
    2.  Enter a prefix to be used in the certificate name.
    3.  Click **Next** to create the certificate.
    4.  Verify that the new certificate has been created in the specified location.

8.  Return to the **System diagnostics** page, browse to the location of the certificate, and click **Upload**.
9.  Return to the **Upload the new certificate** page of the **Microsoft Dynamics Lifecycle Services Diagnostic Service Setup Wizard**, select **Certificate file has been uploaded**, and click **Next**.
10. On the **Select private certificate** page, the name of the certificate is displayed. Click **Next**.
11. On the **Specify service account** page, enter the service account and password, and then click **Next**.
12. On the **Change destination folder** page, enter the location where you want to store the logs that were collected by the System diagnostics, and then click **Next**.
13. Click **OK** to install and start the System diagnostics, and then click **Finish**.

Two executable programs are installed: LCSDiagFXDiscovery.exe and LCSDiagFXCollector.exe.

## Discover environments
1.  Click **Start**, and then click **Microsoft Dynamics AX Lifecycle Services Diagnostic Service Discovery.**
2.  In the **Environment Discovery** window, enter a name for the environment, the fully-qualified name of the SQL Server instance and database, and then click **Discover**.
3.  At the bottom of the Window, click the **Test permissions** button ![Test permissions button for System diagnostics](./media/testpermissions.jpg) at the bottom of the page.
4.  On the **Change destination folder** page, enter the location where you want to store the logs that were collected by the System diagnostics, and then click **Next**.

## Collect data
You can collect data on demand from the **Environment Discovery** window. We recommend that you schedule a job to collect data regularly. Data collection typically takes between 5 and 15 minutes. Errors that are encountered during data collection are logged in the Windows Application event log, as well as in a log file in the location that you specified during installation.

1.  To run an initial data collection in the **Environment Discovery** window, click **Collect now**. We recommend that you run an initial collection immediately after discovering an environment for the first time.
2.  To generate a collection command that you can use to schedule collection jobs, click **Generate collection command**.
3.  Copy the generated command to the clipboard.
4.  Schedule the command to run by using a scheduling engine, such as **Windows Task Scheduler**. For more information about using **Task Scheduler**, see [Schedule a task](http://technet.microsoft.com/en-us/library/cc766428.aspx).

## Use same X509 certificate for all environments
 
1.  First time let setup generate certificate as usual
2.  Run MMC (Microsoft management console) as admin
3.  File -&gt; "**Add or Remove Snap-ins**"
4.  Double click **Certificates** item and choose computer account then next-&gt;finish-&gt;ok
5.  Expand Certificates (Local Computer)-&gt;**Personal**-&gt;Certificates:
6.  Right click on certificate generated on first step -&gt; All tasks -&gt; Export -&gt; Next -&gt; Choose "**Yes, export the private key**"
7.  Leave default values in \*.pfx export setup
8.  In security step Use domain account or password for securing your exported file
9.  Export files in next steps
10. Copy exported file to new environment click it and choose **Install PFX**
11. Choose **Local Machine**
12. Click next -&gt; And in following screen make sure that **Mark this key as exportable** is set. Click next and finish
13. Now when running Lifecycle services system diagnostics setup choose on new environment use an existing certificate
14. Certificate generated in first step should be present in client certificates lookup choose it and continue as usual:



