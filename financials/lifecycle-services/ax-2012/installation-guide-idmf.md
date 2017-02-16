---
# required metadata

title: Installation Guide for the Intelligent Data Management Framework (AX 2012)
description: This topic describes the system requirements and steps to install the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF). 
author: kfend
manager: AnnBe
ms.date: 2015-12-04 23 - 30 - 00
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18361
ms.assetid: c2f2c2d4-9b15-4742-984d-827f2c9a1261
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: 
ms.dyn365.ops.version: 2012

---

# Installation Guide for the Intelligent Data Management Framework (AX 2012)

This topic describes the system requirements and steps to install the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF). 

Overview of the Intelligent Data Management Framework
-----------------------------------------------------

IDMF lets system administrators optimize the performance of Microsoft Dynamics AX installations. The framework assesses the health of the Microsoft Dynamics AX application, analyzes current usage patterns, and helps reduce database size. IDMF lets you analyze the Microsoft Dynamics AX database and maintain an optimal database size. You can use tools such as the analysis dashboard, database health check, and index defragmentation to monitor the database. Use the purge and archive functionalities to maintain the database size. The purge function deletes data from a set of related entities, or tables, from the production database. The archive function moves data from a set of related tables in the production database to a standby database. This standby database, called the archive database, can be used for reporting purposes but cannot be updated. The framework and this topic use the term offlining interchangeably with archiving, and purge interchangeably with recycle.

## Prerequisites
To benefit from this topic, you must have knowledge in the following areas:

-   Microsoft Dynamics AX application and system administration
-   Microsoft SQL Server database administration, backup, recovery, and performance tuning
-   Microsoft Windows Server administration, backup, recovery, and performance tuning

## Before you begin
During the installation, you are prompted to provide information about the following databases:

-   The production database. The production database is the Microsoft Dynamics AX database in the production environment.
-   The production replica database. The application health analysis requires many queries to be run to capture information from the Microsoft Dynamics AX modules. These application queries are extensive and, if applied to a production database, adversely affect the response time for online users. Therefore, by default, these queries are run against the production replica database. The accuracy of the application health check depends on how well the application data in the production replica database mirrors that in the production database. Verify that you have a production replica database in place with relevant application data before you begin the installation process. Develop a synchronization strategy to keep your production replica database as close to the production database as possible.
-   The management database. The Setup program creates a new database, referred to as the management database, based on the information you provide during installation. The framework uses this database for internal use. You must provide a unique name for this database. We recommend that you use a name that easily identifies this database as the management database for the framework. The AOS service account must have **datareader**, **datawriter** and **ddladmin** rights on the management database. **Note:** IDMF stores the Microsoft Dynamics AX metadata information in the management database. When you run the post-installation tasks, IDMF synchronizes the metadata information from the production database with the management database. You must synchronize the production database with the management database whenever you change the metadata in your Microsoft Dynamics AX application. To synchronize the databases, follow the instructions in the [Post-installation tasks](#PostInstallation) section.
-   The Setup program creates a new database, referred to as the archive database, based on the information you provide during installation. The framework uses the archive database to store records that are moved from the production database by the archive tasks. **Caution:** You must configure an Application Object Server (AOS) instance to connect with the archive database to view archived transactions. Make sure that users have only read access to the archive database. Modifying archived transactions causes data inconsistency. IDMF cannot restore data from an archive database that has been modified.
-   You must have an AOS configured to run as a batch server before you can use the IDMF archive functionality. For more information, see [Configure an AOS instance as a batch server](http://technet.microsoft.com/library/74687f8d-fd55-4a99-bea9-835655905fb4(AX.60).aspx).

Determine the location and initial size of the data files and log files for the archive, management, and production replica databases. Make sure that the initial size is sufficient for optimal performance, and that the location provides resources for future growth. For more information about database configuration, see [Configure SQL Server and storage settings](http://technet.microsoft.com/library/83931d0a-2d75-4cc8-b29b-129ebd5b27e5(AX.60).aspx).

## System requirements
This section lists the system requirements for IDMF. Before installing the framework, make sure that the system you are working with meets or exceeds the minimum hardware and software requirements.

### Network requirements

Install IDMF on a local area network (LAN) computer. Installing on a computer connected across a wide area network (WAN) causes slower performance because of increased latency, and is not recommended.

### Hardware requirements

The following table provides the minimum hardware requirements to install and run IDMF.

| Hardware        | Minimum requirements                                                                                                       |
|-----------------|----------------------------------------------------------------------------------------------------------------------------|
| Processor       | Intel Pentium/Celeron family or compatible Pentium III Xeon or higher processor; 1.1 gigahertz (GHz) or higher recommended |
| Memory (RAM)    | 1 GB or more recommended                                                                                                   |
| Hard disk space | 70 megabytes (MB) for IDMF                                                                                                 |
| Monitor         | Super VGA (1024x768) or higher resolution                                                                                  |
| Pointing device | Microsoft Mouse or compatible pointing device                                                                              |

### 

### Supported operating systems

IDMF is currently supported on 32-bit and 64-bit versions of the following operating systems.
-   Windows Server 2008 Standard Edition, Enterprise Edition, or Datacenter Edition
-   Windows Server 2008 R2 Standard Edition, Enterprise Edition, or Datacenter Edition
-   Windows Server 2012 Standard Edition, Enterprise Edition, or Datacenter Edition
-   Windows 7 Professional Edition or Ultimate Edition
-   Windows 8 Pro Edition or Enterprise Edition

## Software requirements
You must have the following software installed on the computer before you install IDMF.
| Software                                                           | Comment                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft .NET Framework 4.5                                       |                                                                                                                                                                                                                                                                  |
| Windows Installer 3.1 or a later version                           |                                                                                                                                                                                                                                                                  |
| Microsoft Dynamics AX Windows client                               | For your version of Microsoft Dynamics AX.                                                                                                                                                                                                                       |
| Microsoft Dynamics AX .NET Business Connector                      | AX 2009, Microsoft Dynamics AX 2012 up to AX 2012 R2                                                                                                                                                                                                             |
| SQL Server Integration Services runtime, and the client components | The same version, including service packs, as the SQL Server database that is used.Use the SQL Server Setup program to install these components on the computer. You do not have to install other SQL Server components, such as the SQL Server database engine. |
| Microsoft Office 2007 or later (optional)                          | Only required if you use the export to Excel functionality.                                                                                                                                                                                                      |
| Microsoft Distributed Transaction Coordinator (MSDTC)              | Configuration details are provided in the next section.                                                                                                                                                                                                          |

| **Note**                                                                                                                                                                                                              |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IDMF uses the business connector to work with the Microsoft Dynamics AX application. Be sure that the business connector can connect with the Microsoft Dynamics AX application successfully before you install IDMF. |

### 

### Configure MSDTC

You must install and configure MSDTC on the SQL Server host, and on the computer where you install IDMF. Follow these steps to open the Local DTC Properties dialog box. For details about Windows 7, Windows Vista, Windows Server 2008, and Windows Server 2008 R2, see [Enable Network DTC Access](http://technet.microsoft.com/en-us/library/cc753510(WS.10).aspx).
1.  Click **Start**, click **Run**, type dcomcnfg, and then click **OK** to open **Component Services**.
2.  In the console tree, expand **Component Services**, click **Computers**, expand **My Computer**, click **Distributed Transaction Coordinator**, and then click **Local DTC**.
3.  Right-click **Local DTC**, and then click **Properties** to open the **Local DTC Properties** dialog box.
4.  Click the **Security** tab.
5.  Set the following options on the **Security** tab, and then click **OK**.

    | Configuration option              | Recommended value |
    |-----------------------------------|-------------------|
    | Network DTC Access                | Enabled           |
    | Client and Administration         |                   |
    | Allow Remote Clients              | Enabled           |
    | Allow Remote Administration       | Enabled           |
    | Transaction Manager Communication |                   |
    | Allow Inbound                     | Enabled           |
    | Allow Outbound                    | Enabled           |
    | No Authentication Required        | Enabled           |

### Database server requirements

The following table lists the database server requirements. Both 32-bit and 64-bit versions of SQL Server are supported. For the system requirements to install SQL Server, see the [SQL Server web site](http://www.microsoft.com/sql/default.mspx).
| Database server version                            |
|----------------------------------------------------|
| SQL Server 2008, Enterprise or Standard edition    |
| SQL Server 2008 R2, Enterprise or Standard edition |
| SQL Server 2012, Enterprise or Standard edition    |
| SQL Server 2014, Enterprise or Standard edition    |

#### 

#### Database requirements

During installation, Setup creates the following databases:
-   Archive database
-   Management database

During installation, Setup connects to the following databases:
-   Microsoft Dynamics AX production database
-   Production replica database

## Installation prerequisites
Be sure that the following prerequisites are in place before you install IDMF:
-   The Microsoft Dynamics AX database must be on an instance of SQL Server 2008 or later.
-   IDMF is only supported on AX 2009, and on Microsoft Dynamics AX 2012 up to AX 2012 R2.
-   The computer where you install IDMF must meet the hardware and software requirements detailed in [Software requirements](#Software).
-   You must update the cross-reference information in the Microsoft Dynamics AX database:
    -   In the Microsoft Dynamics AX 2012 Windows client, in the Development workspace, click **Tools** &gt; **Cross-reference** &gt; **Periodic** &gt; **Update**. In the **Update cross-reference (w/recompile)** form, verify that the **Update data model** field is selected. Click **OK**.
    -   In earlier versions of the Microsoft Dynamics AX Windows client, click **Microsoft Dynamics AX** &gt; **Tools** &gt; **Development Tools** &gt; **Cross-reference** &gt; **Periodic** &gt; **Update**. In the **Update cross-reference (w/recompile)** form, verify that the **Update Data Model** and **Update type hierarchy** fields are selected. Click **OK**. Wait for the Infolog message, and verify that the cross-reference update is successful.

### Rights required for installation

Before you install IDMF, make sure that the account that you log on with has appropriate permissions. Work with a system administrator to make sure that you have these rights.
| **Note**                                                                                                            |
|---------------------------------------------------------------------------------------------------------------------|
| If you install IDMF using a domain account other than your own, that account must have the appropriate permissions. |

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Action</th>
<th>Permissions required for the account</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Install IDMF.</td>
<td>The system administrator performing the installation must be a:
<ul>
<li>Member of the administrators group on the local computer.</li>
<li>Member of database creator (dbcreator) role on the server instance of SQL Server.</li>
</ul></td>
</tr>
<tr class="even">
<td>Create a service account.</td>
<td>The installation process requires you to enter an account name and password for the scheduler service. This service account must:
<ul>
<li>Be a member of the Admin group in the Microsoft Dynamics AX application.</li>
<li>Be a member of the public server role. Use the <strong><span class="ui">SQL Server Login Properties</span></strong> &gt; <span class="ui"><strong>Server Roles</strong></span> page to grant this permission.</li>
<li>Have the following user mappings for the production, production replica, archive, and management databases. Use the <strong><span class="ui">SQL Server Login Properties</span></strong> &gt; <strong><span class="ui">User Mapping</span></strong> page to grant these permissions:
<ul>
<li>db_owner</li>
<li>public</li>
</ul>
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The <strong>Setup Wizard</strong> creates the management and archive databases during installation of IDMF. Be sure to provide the service account with the user mappings for the management and archive databases after the <strong>Setup Wizard</strong> is completed successfully.</td>
</tr>
</tbody>
</table>
</div></li>
<li>Have the permission to view any database and to view the server state. Use the <strong><span class="ui">SQL Server Properties</span></strong> &gt; <strong><span class="ui">Permissions</span></strong> page to grant these permissions.</li>
<li>Have read, write, and modify permissions to the folder, including subfolders, where you install IDMF.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Use IDMF console.</td>
<td>The system administrator using IDMF must:
<ul>
<li>Be a member of the Admin group in the Microsoft Dynamics AX application.</li>
<li>Have read, write, and modify permissions to the folder, including subfolders, where you install IDMF.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The <strong>Setup Wizard</strong> creates this folder during installation. Be sure to provide users with the read and write permissions for the installation folder after the <strong>Setup Wizard</strong> is completed successfully.</td>
</tr>
</tbody>
</table>
</div></li>
<li>Have the following user mappings for the production, production replica, archive, and management databases. Use the <strong><span class="ui">SQL Server Login Properties</span></strong> &gt; <strong><span class="ui">User Mapping</span></strong> page to grant these permissions:
<ul>
<li>db_owner</li>
<li>public</li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

## Install IDMF
Check the following settings and services before you start the installation process:
1.  On the computer where you plan to install IDMF:
    1.  Check the connection to Application Object Server (AOS). IDMF connects to the AOS instance specified in the active configuration in the Microsoft Dynamics AX configuration utility (**Start** &gt; **Administrative Tools** &gt; **Microsoft Dynamics AX 2012 Configuration**).
    2.  Start the Microsoft Dynamics AX Windows client, and verify successful access to the Microsoft Dynamics AX application.
    3.  Verify that the SQL Server Integration Services service and the Distributed Transaction Coordinator service are running.

2.  Verify that the SQL Server service is running on the database server.

Follow these steps to install IDMF:
1.  Double-click **IDMF-2.0.exe**.
2.  On the **Welcome** page, click **Next to continue**.
3.  On the M**icrosoft Software License Terms** page, read the license terms, click **I accept the license terms**, and then click **Next**.
4.  On the **Setup components** page, click **Next** to accept the default installation location. To change the installation location, click **Browse**. Click **Next** to continue.
5.  On the **Select Microsoft Dynamics AX version** page, select the version of Microsoft Dynamics AX that you are using, and then click **Next**.
6.  On the **Create new management database** page, in the SQL Server instance field, enter the name of the SQL Server instance where you plan to create the management database. In the **Database name** field, type a name for the management database. You must provide a name to create a new database. If you use the name of an existing database, the installation fails with an error.
7.  On the **Specify Microsoft Dynamics AX production database** page, in the **SQL Server instance** field, enter the name of the SQL Server instance that contains the production database. In the **Database name** field, enter the name of the production database for your Microsoft Dynamics AX implementation. Click **Next**.
    | **Caution**                                                                                                                              |
    |------------------------------------------------------------------------------------------------------------------------------------------|
    | The production database name you enter here must match the database name used in the Microsoft Dynamics AX server configuration utility. |

8.  On the **Specify Microsoft Dynamics AX production replica database** page, in the **SQL Server instance** field, type the name of the SQL Server instance that contains the production replica database. In the **Database name** field, type the name of the production replica database. This must be an existing database. Click **Next**.
9.  On the **Create new archive database** page, in the **SQL Server instance** field, enter the name of the SQL Server instance where you plan to create the archive database. In the Database name field, type a name for the archive database. You must provide a name to create a new database. If you use the name of an existing database, the installation fails with an error.
10. The **Specify e-mail settings** page captures the information required for e-mail alerts functionality. You are not required to provide this information at installation time and can configure e-mail alerts later. Optionally enter values for the following fields, and then click **Next**.
    1.  In the **SMTP (outbound) server** field, specify the IP address or DNS name of a valid SMTP server.
    2.  In the **SMTP port** field, specify the port number that is used to send e-mail messages.
    3.  In the **From address** field, specify the e-mail address that appears as the source of the mail.
    4.  In the **Username** field, specify the user name that is used to access the SMTP server.
    5.  In the **Password** field, specify the password that is used to access the SMTP server.
    6.  In the **Recipient list** field, specify one or more e-mail addresses for recipients. Separate multiple e-mail addresses with a semicolon.
    7.  In the **Company name** field, specify the name of your organization. IDMF displays this name in the About dialog box.

11. The Setup program installs a scheduler as a Windows service. On the **Specify service account** page, in the **Account name (DomainUserName)** and **Password** fields, enter the account name and password for the scheduler service account. Click Next.
    | **Note**                                                                                                                                                                                                                |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | The account name you enter here must belong to the Admin group in the Microsoft Dynamics AX application, and it must have database permissions as specified in the [Rights required for installation](#Rights) section. |

12. On the **Ready to install** page, click **Install** to continue.
13. Wait for setup to complete the installation. Click **Finish** to close the wizard.

## Postinstallation tasks
You must complete the post-installation tasks before you start IDMF console. The post installation tasks include the following actions:

1.  Copy the label files from the installation folder to the Microsoft Dynamics AX application folder.
2.  Update the SQL Server Integration Services (SSIS) package connection manager.
3.  Check that the Microsoft Distributed Transaction Coordinator (MSDTC) is installed and configured correctly.
4.  Check that Microsoft Excel is installed. Excel is an optional component. However, if you do not have Excel on the computer, the post-installation task displays a warning message. Excel is required for the Export to Excel command to be available.
5.  Update the SQL Server Integration Services (SSIS) packages with the locale information of the database.
6.  Validate the e-mail settings that are provided during the installation.
7.  Start the Microsoft Dynamics AX client to import an X++ project (XPO) and create classes that are required for the operation of IDMF.
8.  Synchronize the metadata in the management database with the metadata in the Microsoft Dynamics AX application.

Follow these steps to complete the post-installation tasks:

1.  Verify that the Microsoft Dynamics AX client starts and opens the Microsoft Dynamics AX application successfully.
2.  Verify that you have updated the cross-reference system in the Microsoft Dynamics AX application. Without an updated cross-reference system, the post-installation process fails with an error message. See [Installation prerequisites](#Prereq) for instructions.
3.  | **Note**                                                      |
    |---------------------------------------------------------------|
    | You must run the post-installation tasks as an administrator. |

    Click **Start** &gt; **All Programs** &gt; **Microsoft Dynamics AX Intelligent Data Management Framework**. Right-click **Post-installation tasks**, and click **Run as Administrator** to complete the post-installation tasks. You can also navigate to the installation location, right- click **PostInstallSetup.exe**, and click **Run as Administrator**. The default installation location is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework.

The post-installation checklist application runs in a Command Prompt window. The application displays prompts in white. You must respond to the questions in white. Each starting step is displayed in yellow. Optional missing configuration details are also displayed in yellow. Each successfully completed step is displayed in green. Each unsuccessfully completed step is displayed in red. The post-installation checklist application performs the following actions:

1.  Opens a Command Prompt window that is used to capture necessary information.
2.  Copies label files to the Microsoft Dynamics AX application folder. These label files follow the Microsoft Dynamics AX development best practices and provide labels for the classes that are imported by the imported projects, or XPOs.
3.  Updates the package connection manager. The package connection manager is used to run the SQL Server Integration Services packages.
4.  Validates the correct configuration of the Microsoft Distributed Transaction Coordinator (MSDTC). The post-installation checklist displays an error message if the configuration is invalid. For configuration instructions, see [Software requirements](#Software).
5.  Validates that Excel is installed. Excel is an optional component. However, if you do not have Excel on the computer, the post-installation task displays a warning message. Excel is required for the Export to Excel command to be available.In this step, the pre-installation application queries the registry for the installed version of Excel and the existence of the Microsoft Office Primary Interop Assemblies (PIAs) for Excel. If the post-installation application does not find Excel or the Excel PIAs, it displays this message: "Verify that Microsoft Office Excel and Microsoft Office Primary Interop Assemblies (PIAs) are installed."To use the export to Excel functionality, you must have Excel and the Excel PIAs installed on the computer. If necessary, download and install the PIAs after the post-installation application closes. For Excel 2003, see [Office 2003 Update: Redistributable Primary Interop Assemblies](http://www.microsoft.com/downloads/details.aspx?familyid=3c9a983a-ac14-4125-8ba0-d36d67e0f4ad&displaylang=en). For Excel 2007, see [2007 Microsoft Office System Update: Redistributable Primary Interop Assemblies](http://www.microsoft.com/downloads/details.aspx?FamilyID=59daebaa-bed4-4282-a28c-b864d8bfa513&displaylang=en).
6.  Validates the configuration of e-mail settings. E-mail settings are optional during the installation. In case of missing or invalid e-mail configuration settings, the application displays a message informing you to configure the settings later. IDMF sends a test e-mail for the valid e-mail configuration.
7.  Starts the scheduler service. IDMF uses a service called the Microsoft Dynamics AX Intelligent Data Management Framework service. This service is also called the scheduler service, and this term is used interchangeably with the service name. The post-installation application tries to start the scheduler service, and displays a message indicating the success or failure of this attempt. Click **Start** &gt; **Administrative Tools** &gt; **Services** to verify that the service is running, or start the service manually.
8.  Imports an X++ project (XPO) that is used to create classes that are used by IDMF. The post-installation application imports the XPO to the layer that is specified in the Microsoft Dynamics AX client configuration. For the name of the XPO, see [Manually running the post-installation tasks](#Manual).
    | **Caution**                                                                                                                                                                                                                                                                                          |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | Make sure that the business connector points to the same layer that you plan to import the XPO into. Verify that the Application layer object to open list in the Microsoft Dynamics AX client configuration window points to the same layer for both the business connector and the Windows client. |

9.  Prompts you to enter a response to import the XPO. Enter Y to import the XPO now, and wait until you get a message indicating that the metadata synchronization is complete. The post-installation application imports the XPO to the layer that is specified in the Microsoft Dynamics AX client configuration, as detailed in step 8. Enter N to import the project manually. For instructions to manually import the XPO, see [Manually running the post-installation tasks](#Manual).You must import this XPO successfully before you can start IDMF.
10. If you entered N in the previous step, asks you whether you want to synchronize the metadata. Enter Y to synchronize the metadata now or N to manually synchronize the metadata later.
    | **Caution**                                                         |
    |---------------------------------------------------------------------|
    | You must complete this step successfully before you can start IDMF. |

11. Prompts you to press any key on the keyboard to continue. This is the last step, and when you press a key, the post-installation application closes the Command Prompt window.

## Framework checklist
After the successful completion of the post-installation tasks, start IDMF from **Start** &gt; **All Programs** &gt; **Intelligent Data Management Framework** &gt; **Microsoft Dynamics AX Intelligent Data Management Framework**. When you start the application for the first time, the **Framework checklist** shows two sets of checklists, the tasks that you must have completed successfully before starting the application, and the tasks that you must complete the first time you start it. Click **Close** if you have not successfully completed the necessary tasks. Restart the application after completing the following tasks:
1.  Update cross-reference in the Microsoft Dynamics AX application. For instructions, see [Installation prerequisites](#Prereq).
2.  Complete the post-installation tasks described in the previous section.
3.  Verify that IDMF for Microsoft Dynamics AX service is running.

You see the **Framework checklist** dialog box every time you start the framework, until you successfully complete the following checklist. Click **OK** to complete the following checklist in the **Scheduled tasks** window:
1.  Successfully complete the baseline analysis snapshot of the production database.On the menu bar, click **Schedule**. Follow these steps in the **Scheduled tasks** window to create a baseline analysis snapshot of the database. For detailed instructions on scheduling tasks, see [Using the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF)](http://ax.help.dynamics.com/en/wiki/using-the-microsoft-dynamics-ax-intelligent-data-management-framework-idmf/).
    1.  In the **Task details** pane, enter values in the **Name** and **Description** fields for the task.
    2.  On the **Schedule** tab, select **One time only** from the **Frequency** list. Select or enter values in the **Start date** and **Time** fields.
    3.  Click **Save**.
    4.  When prompted to validate the health check queries, click **No**.
    5.  Click **Status** &gt; **Refresh** to refresh the task. Wait for the task to be completed with a **Pass** status.You are ready to use the **Analysis** menu for the database analysis.

2.  Schedule and complete the health check analysis. Follow these steps to create the baseline health check analysis. For more information about health check analysis, see [Using the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF)](http://ax.help.dynamics.com/en/wiki/using-the-microsoft-dynamics-ax-intelligent-data-management-framework-idmf/).
    1.  Click **Administer** &gt; **Application health check** to work with the health check queries. In the **Application health check queries** window, click **Validate queries**, and wait for the validation to be completed. Upon successful validation, the **Validate queries** button becomes hidden, and all the queries in the **Queries** node appear in black.
    2.  Click **Schedule** &gt; **Ledger periods** to create the ledger periods for the health check analysis. Enter the required information in the **Task details** pane of the **Scheduled tasks** window, and then click **Save**. For this task, select **One time only** from the **Frequency** list. Wait for the ledger periods schedule to be completed successfully before going to the next step.
    3.  Click **Schedule** &gt; **System health check** to create the baseline health check analysis task. This task must start after successful completion of the ledger periods task that you created in the previous step. Enter the required information in the **Task details** pane of the **Scheduled tasks** window, and then click **Save**. For this task, select **One time only** from the **Frequency** list.
    4.  Click **Status** &gt; **Refresh** to refresh the task. Verify that both the ledger periods task and the baseline health check analysis tasks have been completed with a **Pass** status. You are now ready to use the **Analysis** menu for health check analysis. For instructions, see [Using the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF)](http://ax.help.dynamics.com/en/wiki/using-the-microsoft-dynamics-ax-intelligent-data-management-framework-idmf/).

3.  **Note: **Skip this step if you do not plan to use the archive functionality. Synchronize metadata with the archive database. The metadata synchronization task copies the metadata from the production database to the archive database. For more information, see [Using the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF)](http://ax.help.dynamics.com/en/wiki/using-the-microsoft-dynamics-ax-intelligent-data-management-framework-idmf/). You must complete the metadata synchronization task successfully before going to the next step. Follow these steps to create a metadata synchronization task:
    1.  Click **Schedule** &gt; **Metadata** to work with the metadata synchronization task. Enter the required information in the **Task details** pane of the **Scheduled tasks** window, and then click **Save**. For this task, select **One time only** from the **Frequency** list.
        | **Note**                                                                                                                                                         |
        |------------------------------------------------------------------------------------------------------------------------------------------------------------------|
        | Consider creating a recurring task to synchronize the metadata between the production and archive databases, to keep the archive database in a consistent state. |

    2.  Click **Status** &gt; **Refresh** to refresh the task. Verify that the metadata synchronization task has been completed with a **Pass** status.

4.  **Note: **Skip this step if you do not plan to use the archive functionality. Replicate master data from the production database to the archive database. You must complete the previous step before creating a master data replication task. The master data replication task copies the master data tables from the production database to the archive database. For more information, see [Using the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF)](http://ax.help.dynamics.com/en/wiki/using-the-microsoft-dynamics-ax-intelligent-data-management-framework-idmf/). Follow these steps to create a master data replication task:

    1.  Click **Schedule** &gt; **Master data** to work with the master data replication task. Enter the required information in the **Task details** pane of the **Scheduled tasks** window, and then click **Save**. For this task, select **One time only** from the **Frequency** list.
        | **Note**                                                                                                                                                                   |
        |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
        | Consider creating a recurring task to synchronize the master data tables between the production and archive databases, to keep the archive database in a consistent state. |

    2.  Click **Status** &gt; **Refresh** to refresh the task. Verify that the master data replication task has been completed with a **Pass** status.

5.  Verify that the tasks from the previous steps are completed successfully with a **Pass** status. Now you are ready to work with IDMF.

## Removing IDMF
IDMF can be uninstalled by using the **Control Panel**. The uninstall program does not delete the management database, production replica database, or archive database. Optionally, you can back up and then delete these databases manually.

## Troubleshoot installation issues
This section provides information to help you troubleshoot issues you may encounter when running the **Setup Wizard**.
### Location of log files

IDMF creates all the log files in the &lt;installation folder&gt;Logs folder, where the default path of &lt;installation folder&gt; is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework.

### Create and view the installation log file

By default, the Setup program does not create an installation log file. Optionally, you can create the installation log file to capture the steps used by Setup and any errors generated. Follow these steps to create the installation log file:
1.  Open a Command Prompt window.
2.  Run the following command.

        "<Path of the exe file>IDMF-2.0.exe" /L*v "<Path of the log file>AXDataManagementToolSetupLog.txt"

3.  Open the log file, and search for "error." The following message is an example of the types of message contained in the log file.

        CreateDatabase: Error 0x80040e14: failed to create to database: '<<Database name>>', error: Database '<<Database name>>' already exists. Choose a different database name.

4.  Use the Windows event viewer to examine system logs containing any messages from IDMF.

### Common error messages generated by Setup

You may encounter the following common error messages when running Setup:
-   Database creation error. If a database exists in SQL Server with the same name that you entered for the management or archive database, Setup fails with an error message.
-   Data type mismatch error. If you attempt to connect to SQL Server 2000, you get a SQL script error because the data type mismatch.
-   Missing prerequisites. If you start Setup without the prerequisites, it displays an error message listing the missing components. Install the prerequisites, and then run Setup again.

### IDMF fails to start

When starting IDMF, you may encounter the following error: "An unhandled exception occurred and has been logged. Please contact support." This error message is a generic message that IDMF displays when the error condition is caused by an environmental issue such as permissions. This particular error condition typically occurs when the user does not have read, write, and modify permissions on the folder where you installed IDMF. To fix the error condition, apply read, write, and modify permissions to the installation folder of IDMF and its subfolders. The default path is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework.

### Common error messages generated by the post-installation tasks

You may encounter the following common error messages from the post-installation tasks:
-   If you have not completed the cross-reference update before starting the post-installation tasks, you encounter the message, "You must update the cross-references in the Microsoft Dynamics AX application." Update the cross-reference system, and then start the post-installation step. For instructions on updating the cross-reference system, see [Installation prerequisites](#Prereq).
-   The post-installation tasks fail in case of connectivity or security issues with the database or Application Object Server (AOS). The following error messages are typical:
    -   XPO import completed with error(s), please contact administrator.
    -   XPO import failed.
    -   Metadata synchronization failed.

    Fix the connectivity or security issues, and verify that you can connect to the database server and AOS. Then restart the post-installation tasks. Alternatively, you can run the post-installation tasks manually. For instructions, see [Manually running the post-installation tasks](#Manual).
-   The post-installation application may fail to start IDMF scheduler service with the message, "Unable to restart the Data Management scheduler service. Restart the service manually (Control Panel &gt; Administrative Tools &gt; Services)." This error occurs when the password you used for the service account is incorrect. Use the Services management console to restart the service manually, and reset the password for the service account.
-   The post-installation tasks may fail with the error message, "Ax32.exe is not recognized as an internal or external command, operable program or batch file. XPO import failed." Run the post-installation tasks manually. For instructions, see [Manually running the post-installation tasks](#Manual).

### Metadata synchronization fails

You may encounter the error message, "Inner exception: The operation failed. The class &lt;xxxx&gt; does not exist. Metadata synchronization failed." Here, &lt;xxxx&gt; is the name of the class. This issue is caused by the Microsoft Dynamics AX application cache, called Axapta Object Cache (AOC), on the Windows clients in a three-tier configuration. You must clear the cache, and then follow the instruction provided in the [Manually running the post-installation tasks](#Manual). **Clear the cache**
1.  Start the Microsoft Dynamics AX Windows client.
2.  For Microsoft Dynamics AX 2012, on the **Tools** &gt; **Caches** menu, click each of the following menu items: **Refresh Dictionary**, **Refresh Data**, **Refresh AOD**.
3.  For earlier versions of Microsoft Dynamics AX, on the **Microsoft Dynamics AX** &gt;**Tools** &gt; **Development Tools** &gt; **Application objects** menu, click each of the following menu items: **Refresh Dictionary**, **Refresh Data**, **Refresh AOD**.

### ODBC operation fails

You may encounter the message, "ODBC operation failed. Unable to log on to the database. \[Microsoft\] \[ODBC Driver Manager\] Data source name not found and no default driver specified. Object 'ODBC Connection' could not be created. Metadata synchronization failed." This error usually occurs when the Microsoft Dynamics AX client is installed with SQL Server 2008 client components. The post-installation program fails during the metadata synchronization and displays this error message. To resolve this error, install the ODBC driver SQLCLI.DLL from SQL Server 2005 Setup. This file is available from &lt;SQL Server 2005 installation media&gt;ServersSetup folder. Use sqlncli.msi for 32-bit systems or sqlncli\_64.msi for 64-bit systems. This file is required by Application Object Server (AOS) to establish the database connection.
Manually running the post-installation tasks
--------------------------------------------

Follow these steps to run the post-installation tasks manually:
1.  Copy all the label files in the folder from &lt;Data Management Framework installation folder&gt;XPOLabels&lt; version&gt; to the Microsoft Dynamics AX application folder.The default IDMF installation folder is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework.
2.  After the XPO is successfully imported, modify the job **DMTPopulateMetadataJob** in the Application Object Tree (AOT). Enter appropriate values for the management database server name and management database name, and then run the job. This job retrieves metadata and system information from the Microsoft Dynamics AX application and stores it in the management database. IDMF retrieves metadata information from the management database for its use.
    | **Note**                                                                                                                                                |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | You must run this job when the Microsoft Dynamics AX application metadata changes, to synchronize the management database with the production database. |

3.  If the job in the previous step has been completed successfully, the following tables contain records. Query the management database to verify that these tables are not empty.
    -   **AXAOTENUMINFO**
    -   **AXAOTTABLEINFO**
    -   **AXAOTFIELDSINFO**
    -   **AXAOTINDEXINFO**
    -   **AXAOTTABLERELATION**

4.  Open and run the job **DMTAddEnumValue** in the Application Object Tree (AOT). This job adds an enum value, **DMTArchiveSummary**, to the enums **LedgerTransType** and **InventTransType**. IDMF uses the enum **DMTArchiveSummary** during the archival process.
    | **Note**                                                           |
    |--------------------------------------------------------------------|
    | You must perform this step before you continue with the next step. |

5.  Synchronize the database. In the Microsoft Dynamics AX Windows client, click **Application Object Tree** on the toolbar. In the AOT window, right-click the **Data Dictionary** node, and then select **Synchronize**.
6.  Navigate to C:Program FilesMicrosoft Dynamics AX Intelligent Data Management FrameworkXPO. This folder contains X++ project (XPO). Using the Microsoft Dynamics AX client, import the Summation XPO file. IDMF uses the Summation XPO file when archiving data or restoring archived data, to make adjusting entries to Ledger, Inventory and Bank transactions.



