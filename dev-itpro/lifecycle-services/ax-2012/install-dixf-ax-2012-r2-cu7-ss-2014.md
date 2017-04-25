---
# required metadata

title: Install the AX 2012 R2 CU7 Data import/export framework for SQL Server 2014

description: To use the Data import/export framework for Microsoft Dynamics AX 2012 R2 cumulative update 7 (CU7) with SQL Server 2014 Integration Services or later, you must install AX 2012 R2 CU7, and then apply update KB 3018235KB 3018235.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 71103
ms.assetid: ee28572c-e38d-4c2a-a191-f2631f291e5f
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Install the AX 2012 R2 CU7 Data import/export framework for SQL Server 2014

[!include[banner](../includes/banner.md)]


To use the Data import/export framework for Microsoft Dynamics AX 2012 R2 cumulative update 7 (CU7) with SQL Server 2014 Integration Services or later, you must install AX 2012 R2 CU7, and then apply the update <a href="https://mbs2.microsoft.com/Knowledgebase/KBDisplay.aspx?scid=kb;en-us;3018235">KB 3018235</a>.

The following instructions apply for an environment in which SQL Server 2014 or a later version is installed. If you are running SQL Server 2008 or SQL Server 2012 Integration Services, you can install the Data Import/Export Framework for Dynamics AX 2012 R2 CU7 by using the update installer. For more information, see [Install the Data Import/Export Framework binary updates (CU7)](https://technet.microsoft.com/en-us/library/hh538446.aspx#DIXFInstall). To see which versions of Integration Services are supported with the Data Import/Export Framework, see the [Microsoft Dynamics AX 2012 System Requirements](http://go.microsoft.com/fwlink/?LinkId=165377).

## Before you begin
1.  Download the CU7 hotfix package, and extract it to a local folder. To extract the download, follow the instructions in the [Download and extract an update from CustomerSource, PartnerSource, or Lifecycle Services](https://technet.microsoft.com/en-us/library/hh538446.aspx#Download)**.**
2.  Download the hotfix package for [KB 3018235](https://mbs2.microsoft.com/Knowledgebase/KBDisplay.aspx?scid=kb;en-us;3018235), and extract it to a local folder.

## Install the AX 2012 R2 CU7 Data import/export framework for use with SQL Server 2014 Integration Services
On the computer that is running Integration Services, follow these steps.

1.  Run Windows PowerShell.
2.  Navigate to the Support folder of the hotfix package.
3.  Run the following script:

        Install-DIXFService.ps1.

4.  Follow the on-screen instructions.
5.  You will be asked to locate the Data Import/Export Framework service MSI from Microsoft Dynamics AX 2012 R2 CU7. This file can be found in the **MSI\\DIXF\_Service\_x64** or **MSI\\DIXF\_Service\_x86** folder. If the script is unable to locate the corresponding MSP, you will be asked to locate it. The MSP can be found in the **MSI\\DIXF\_Service\_x64** or **MSI\\DIXF\_Service\_x86** folder in the hotfix package folder ([KB 3018235](https://mbs2.microsoft.com/Knowledgebase/KBDisplay.aspx?scid=kb;en-us;3018235)). You will be asked if you want the Data Import/Export Framework Service to be installed under the **Network Service** account. If you answer **No**, you will be asked to enter the username (DOMAIN\\username format) and password to run the service. Installation should start.

## Verify installation
By default the script’s log will be written to a file that is named **InstallDIXFService-&lt;date&gt;\_&lt;time &gt;.log**. Verify that the file reports a successful installation. If the installation fails, the log produced by the MSI is named **DIXFService\_install -&lt;date&gt;\_&lt;time &gt;.log**. Search for it, and investigate the listed issues.

## Install the Data import/export framework Client and Server Components
After installation of pw\_DMF Service component has completed, install the Data Import/Export Framework Client and AOS components the ordinary way.

1.  Install the CU7 version of the components on the appropriate computers. See [Install the Data Import/Export Framework binary updates (CU7)](https://technet.microsoft.com/en-us/library/hh538446.aspx#DIXFInstall).
2.  Apply hotfix [KB 3018235](https://mbs2.microsoft.com/Knowledgebase/KBDisplay.aspx?scid=kb;en-us;3018235) on the appropriate computers.

## Optional: Create a silent installation Windows PowerShell script
If you supply the **Install-DIXFService.ps1** script with the appropriate parameters you can use the script to do a silent installation. The following table provides a brief description of the parameters that are available and how to use them.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Parameter name</td>
<td>Description</td>
</tr>
<tr class="even">
<td>UseNetworkService</td>
<td>This is a switch:
<ul>
<li>If you want to install the service under the Network Service account, include <strong>UseNetworkService</strong> in your command.</li>
<li>If <strong>UseNetworkService</strong> is specified, any value specified for <strong>ServiceAccount</strong> and <strong>ServicePassword</strong> will be ignored.</li>
</ul></td>
</tr>
<tr class="odd">
<td>ServiceAccount</td>
<td>Specifies the account the service will be run under. This parameter must be supplied if UseNetworkService is not used. This should be in DOMAIN\username format.</td>
</tr>
<tr class="even">
<td>ServicePassword</td>
<td>Specifies the password for account that the service will run under. This parameter must be supplied if <strong>UseNetworkService</strong> is not used.</td>
</tr>
<tr class="odd">
<td>MSIFileName Required</td>
<td>The path of the <strong>dixf_service_</strong><em>&lt;architecture&gt;</em><strong>.msi</strong> file from the Microsoft Dynamics AX 2012 R2 CU7 hotfix. This can be a relative or absolute path.</td>
</tr>
<tr class="even">
<td>MSPFileName</td>
<td>The path of the <strong>dixf_service_</strong><em>&lt;architecture&gt;</em><strong>.msp</strong> file. If the Install-DIXFService.ps1 script is run from the Support folder in a hotfix package, this parameter is not required, because the script should be able to find the file automatically.</td>
</tr>
<tr class="odd">
<td>LogFileName</td>
<td>The path of the log file for the script. If this parameter is not set, the current directory is used.</td>
</tr>
<tr class="even">
<td>MSIExecLogFileName</td>
<td>The path of the log file for MSIExec, which is where the actual installation log can be found. If this parameter is not set, the current directory is used.</td>
</tr>
</tbody>
</table>

 

### Example 1: Install under Network Service and use default log file paths

    Install-DIXFService.ps1 -UseNetworkService -MSIFileName "C:\CU7Package\MSI\dixf_service_x64\dixf_service_x64.msi"

### Example 2: Install as a specific user and specify log file paths

    Install-DIXFService.ps1 -ServiceAccount "MYDOMAIN\myuser" -ServicePassword "VerySecure.1234" 
    -MSIFileName "C:\CU7Package\MSI\dixf_service_x64\dixf_service_x64.msi" 
    –LogFileName "C:\MyLogs\DIXFService-script-log.txt" -MSIExecLogFileName "C:\MyLogs\DIXFService-MSIExec-log.txt"

See also
--------

[Configure the version of SQL Server Integration Services used by the Data import/export framework in an environment with multiple versions (DIXF)](configure-sql-server-integration-services-multiple-versions-dixf.md)


