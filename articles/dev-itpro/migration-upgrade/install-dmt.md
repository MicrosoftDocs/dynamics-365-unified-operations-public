---
# required metadata

title: AX 2009 upgrade - Install the Data migration tool 
description: This topic provides information about how to set up the Data Migration Tool (DMT) so that you can migrate your data from Microsoft Dynamics AX 2009 to Dynamics 365 for Finance and Operations.
author: kfend
manager: AnnBe
ms.date: 06/30/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: kfend
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 upgrade – Install the data migration tool

[!include [banner](../includes/banner.md)]

This topic provides information about how to set up the Data Migration Tool (DMT) so that you can migrate data from Microsoft Dynamics AX 2009 to Dynamics 365 for Finance and Operations.

## Prerequisites

- Microsoft SQL Server 2008/2012/2014/2016
- Microsoft .NET Framework 4.5 or higher
- Microsoft SQL server machine with SQL 2012 Native client installed 
- Microsoft SQL SSIS service installed and running on the machine where the DMT service will be installed
- Microsoft SQL server authentication must support both SQL authentication and windows authentication 
- Access to database engines following the version guidance in the following table:
  
    |                 | Microsoft SQL Server 2008   |   Microsoft SQL Server 2012 and above   |
    |-----------------|-----------------------------|-----------------------------------------|
    | No office on VM | Access engine 32bit         | Access engine 64bit                     |
    | Office 32bit    | Access engine 32bit         | Access engine 64bit                     |
    | Office 64bit    | Access engine 32bit + 64bit | Access engine 64bit                     |

- Access data base engine installed
- Dynamics AX 2009 SP1 - 5.0.1000.52 or higher
- Pre-req patch (axpatch.exe) installed. To locate the patch, from where you downloaded the zip and extracted the file, go to <pre-requisiteforpatch\application>.

## Install the Dynamics 365 for Finance and Operations DIXF service

1. Navigate to the location where you extracted the zip file, and in the “DIXF msi” folder, right-click DIXF_Service_x64.msi and select **Run**.
2. When the Wizard opens, click **Next**.
3. Accept the license terms, and click **Next**.
4. Select the account, for the service with Admin rights, and click **Next**. If you select the **Network Service** check box, verify that the Network Service account has admin rights. Otherwise, clear the check box and enter an admin account user name and password, and then click **Next**.
5. Select the SQL version, and then click **Next**.
6. Click **Install** and when the Wizard is complete, click **Finish**.
                     
## Copy binaries
Navigate to the location where you extracted the zip file and copy the following files to the folder, [Program Files (x86)\Microsoft Dynamics AX\50\Client\Bin]

- Microsoft.Dynamics.AX.Framework.Tools.DMT.dll
- Interop.Shell32.dll

## Install DMT components for Dynamics AX 2009
There are two ways to install the DMT tool. You can use the combined XPO or an application hotfix. If you are using a Lifecycle Services (LCS) Implementation project, install the DMT tool using the application hotfix. Installation will take approximately seven hours.

### Combined XPO 
1.	Extract the combined XPO file from DMT December_2017_Release\CombinedXPO.
2.	Import the combined XPO file to Dynamics AX 2009. 
3.	Copy the label file from DMT-December_2017_Release\Label file to Application folder [Program Files\Microsoft Dynamics AX\50\Application\Appl\(NameOfYourDeployment)].
4.	Restart the AOS.
5.	In Dynamics AX 2009, click **Data migration** > **Setup** > **Compile and synchronize DMT application**. 

Note that the combined XPO is imported to the layer that the user is logged in to.  

### Application hotfix 
1.	Go to **DMT-December_2017_Release\ApplicationHotfix\DynamicsAX2009-KB4010403-SP1**, right-click **setup.exe**, and then click **Run**.
2.	In Dynamics AX 2009, in the AOT, notice that the **LegalEntityId** field has been added to the views, **DMTCustomerAddressView** and **DMTVendorAddressView**.
3.	Click **Data migration** > **Setup** > **Compile and synchronize DMT application**.                  

## Import the Dynamics 365 for Finance and Operations project 
Complete this procedure only if you are using Platform Update 4 or an earlier version. If you are using Platform Update 5 or later, you can skip this section. 
1.	From where you extracted the zip file, look for **AX7 service\AX 7.0 Latest.axpp**. 
2.	Import the project to the target Finance and Operations machine, and then build and synchronize the solution.

## Parameter setup 
Navigate to where you extracted the zip file, and locate **defaultvalue.xlsx**. 

  >[!NOTE]
  > The file is saved as .xlsx. Do not change the extension. When you provide this file as an input to the Default configuration parameter, select **All Files** so that you can select the .xlsx format. If you don’t select this format, errors will occur later when you start to generate mappings. 
1.	In Dynamics AX 2009, click **Data migration** > **Setup** > **Configure default maps** and enter the appropriate information in the following fields:

- **Default configuration**: Excel file path
- **Export file path**: Server path that can be accessed by the service
- **SQL user and password**: Dynamics AX 2009 database SQL authentication credentials 

2. Close the form.
3. Under **Setup**, click **Configure connections** and enter the appropriate information on the following fields:

- **DIXF service host**: DIXF service installation host name
- **Tenant URL**: Finance and Operations URLRefer to the Finance and Operations web.config file if not sure of the tenant.

## Multi-box setup
With a multi-box setup, you will need the following:
•	Machine A with the Dynamics AX 2009 Database & DIXF service installed
•	Machine B with the Dynamics AX 2009 AOS installed
•	Machine C with the Dynamics AX 2009 Client installed

With this three-machine setup,  Machine C is configured to connect to the AOS in Machine B. Machine B is connected to the database that is configured in Machine A.
 
 
### DIXF service machine prerequisite: Machine A perquisites
The following prerequisites are required for the DIXF service on machine A.
•	SQL Server 2008/2012/2014
•	Microsoft .NET Framework 4.5
•	Access database engines 
•	For SQL 2008 - Access engine 32 bit and 64 bit(if Microsoft Excel is 64 bit)
•	For SQL 2012 or higher - Access engine 64 bit
•	Dynamics AX 2009 database (configured on SQL server) 

### AOS machine prerequisite: Machine B prerequisites
The following prerequisites are required for the AOS installation on machine B. 
•	Dynamics AX 2009 AOS Server
•	Application files
 
### Client machine prerequisite: Machine C
The following prerequisites are required for the Client installation on machine C. 
•	Dynamics AX 2009 Client
  
### Shared folder permissions 
 
The default configuration file and the export package file path should be shared and read/write access to these should be provided for the DIXF Service & Client users. To provide this access, got to **Data migration** > **Setup** > **Configure and generate maps** and click **Validate path** to verify that the required access is available.
 
### Set up parameters 
 
1.	Click **Data migration** > **Setup** > **Configure connections**.
2.	In the **DIXF service host** field, enter the remote machine name where the DIXF service is installed. By default, it is **localhost**.
3.	Click **Validate**, to validate that the client is able to access the DIXF service.
 
### Workarounds
If you receive the error, “DIXF service is unavailable”, complete the following workaround to allow a service connection for the port, 7000.
1. Open port 7000, and for Inbound rules on the DMT Service machine, go to **Firewall settings**, and then click **Run** > **wf.msc**.
2. Click **Inbound Rules** > **New rule**, and on the **Rule Type**, select **Port**, and then click **Next**. 
3. In the **Specific local ports** field, enter 7000 and click **Next**.
4. Select **Allow the connection**, and then click **Next**. 
5. Mark all three check boxes to apply all the rules, and then click **Next**.
6. Enter the name of the rule and click **Finish**. 
7. Repeat these steps for Outbound Rules.


