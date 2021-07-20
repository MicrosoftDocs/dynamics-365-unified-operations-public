---
# required metadata

title: AX 2009 migration - Install the Data migration tool 
description: This topic explains how to set up the Data migration tool (DMT) so that you can migrate your data from Microsoft Dynamics AX 2009.
author: kfend
ms.date: 09/13/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: kfend
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Install the Data migration tool

[!include [banner](../includes/banner.md)]

This topic explains how to set up the Data migration tool (DMT) so that you can migrate data from Microsoft Dynamics AX 2009 to Finance and Operations. 

> [!IMPORTANT]
> At this time, the DMT is in private preview. If you are interested you can sign up for the [Preview Program](https://microsoft.qualtrics.com/jfe/form/SV_brOLCioQ7mmeykB). The public release date for the DMT has not been set. 

## Prerequisites

- Microsoft SQL Server 2008/2012/2014/2016.
- The Microsoft .NET Framework version 4.5 or later.
- Microsoft SQL Server machine that has Microsoft SQL 2012 Native Client installed.
- The Microsoft SQL Server Integration Services (SSIS) service is installed and running on the machine where the DMT service will be installed.
- SQL Server authentication must support both SQL authentication and Microsoft Windows authentication.
- Microsoft Access database engines that follows the version guidance in the following table.

    | Office version                    | SQL Server 2008                 | SQL Server 2012 and later |
    |-----------------------------------|---------------------------------|---------------------------|
    | **No Microsoft Office on the VM** | Access engine 32-bit            | Access engine 64-bit      |
    | **Microsoft Office 32-bit**       | Access engine 32-bit            | Access engine 64-bit      |
    | **Microsoft Office 64-bit**       | Access engine 32-bit and 64-bit | Access engine 64-bit      |

- Microsoft Dynamics AX 2009 SP1 5.0.1000.52 or later.
- The prerequisite patch (axpatch.exe) installed. To find the patch, from the location where you downloaded and extracted the zip file, go to <pre-requisiteforpatch\>\<application\>.

## Install DIXF service

1. Go to the location where you extracted the zip file, and then, in the **DIXF msi** folder, right-click **DIXF\_Service\_x64.msi**, and select **Run**.
2. When the wizard starts, select **Next**.
3. Accept the license terms, and then select **Next**.
4. Select an account for the service, and then select **Next**. The account should have admin rights. If you select the **Network Service** check box, verify that the network service account has admin rights. Otherwise, clear the check box, and enter an admin account user name and password. Then select **Next**.
5. Select the SQL Server version, and then select **Next**.
6. Select **Install**, and then, when the wizard is completed, select **Finish**.

## Copy binaries
Go to the location where you extracted the zip file, and copy the following files to the **Program Files (x86)\\Microsoft Dynamics AX\\50\\Client\\Bin** folder:

- Microsoft.Dynamics.AX.Framework.Tools.DMT.dll
- Interop.Shell32.dll

## Install DMT components for AX 2009
There are two ways to install the DMT. You can use the combined XPO file or an application hotfix. If you're using a Microsoft Dynamics Lifecycle Services (LCS) Implementation project, use the application hotfix. Installation takes approximately seven hours.

### Combined XPO file
1. Extract the combined XPO file from **DMT_V1.0\CombinedXPO**.
2. Import the combined XPO file into AX 2009.
3. Copy the label file from **DMT_V1.0\Label file** to the **Program Files\\Microsoft Dynamics AX\\50\\Application\\Appl\\<NameOfYourDeployment\>** folder.
4. Restart the Application Object Server (AOS) instance.
5. In AX 2009, select **Data migration** \> **Setup** \> **Compile and synchronize DMT application**.

Note that the combined XPO file is imported into the layer that the user is signed in to.

### Application hotfix
1. Go to **DMT_V1.0\\ApplicationHotfix\\DynamicsAX2009-KB4010403-SP1**, right-click **setup.exe**, and then select **Run**.
2. In AX 2009, in the Application Object Tree (AOT), notice that the **LegalEntityId** field has been added to the **DMTCustomerAddressView** and **DMTVendorAddressView** views.
3. Select **Data migration** \> **Setup** \> **Compile and synchronize DMT application**.

## Parameter setup
Go to the location to where you extracted the zip file, and find **defaultvalue.xlsx**.

> [!NOTE]
> The file is saved in .xlsx format. Don't change the extension. When you provide this file as input for the **Default configuration** parameter, select **All Files** so that you can select the .xlsx format. If you don't select this format, errors will occur when you start to generate mappings.

1. In AX 2009, select **Data migration** \> **Setup** \> **Configure default maps**, and enter the appropriate information in the following fields:

    - **Default configuration** – Enter the path of the Microsoft Excel file.
    - **Export file path** – Enter the server path that can be accessed by the service.
    - **SQL Server user and password** – Enter the SQL authentication credentials for the AX 2009 database.

2. Close the form.
3. Under **Setup**, select **Configure connections**, and enter the appropriate information on the following fields:

    - **DIXF service host** – Enter the host name of the DIXF service installation.
    - **Tenant URL** – Enter the URL for the application tenant. If you aren't sure of the tenant, see the web.config file for the Finance and Operations application.

    > [!NOTE}
    > In the Azure Portal, when you create a new app in the Azure Active Directory (AAD), you can select from two options. **Web API** and **Native**. In this instance, select **Native** and grant permissions to native AAD app.

## Multi-box setup
For a multi-box setup, you must have the following machines:

- Machine A, where the AX 2009 database and DIXF service are installed
- Machine B, where the AX 2009 AOS instance is installed
- Machine C, where the AX 2009 client is installed

In this three-machine setup, machine C is configured to connect to the AOS instance on machine B. Machine B is connected to the database that is configured on machine A.

### DIXF service machine prerequisites (machine A)
The DIXF service on machine A has the following prerequisites:

- SQL Server 2008/2012/2014
- The .NET Framework version 4.5
- Access database engines

    - **For SQL Server 2008:** Access engine 32-bit and 64-bit (if Microsoft Excel is 64-bit)
    - **For SQL Server 2012 or later:** Access engine 64-bit

- AX 2009 database (configured on SQL Server)

### AOS machine prerequisites (machine B)
The AOS installation on machine B has the following prerequisites:

- AX 2009 AOS Server
- Application files

### Client machine prerequisites (machine C)
The client installation on machine C has the following prerequisites:

- AX 2009 client

### Shared folder permissions

The path of the default configuration file and the export package file should be shared, and client users and the DIXF service should have read/write access to these files. To grant this access, select **Data migration** \> **Setup** \> **Configure and generate maps**, and then select **Validate path** to verify that the required access is available.

### Set up parameters

1. Select **Data migration** \> **Setup** \> **Configure connections**.
2. In the **DIXF service host** field, enter the name of the remote machine where the DIXF service is installed. By default, the name is **localhost**.
3. Select **Validate** to validate that the client can access the DIXF service.

### Workarounds
If you receive an error message that states, "DIXF service is unavailable," complete the following workaround to enable a service connection for port 7000.

1. Open port 7000, and then, for inbound rules on the DMT service machine, select **Firewall settings**, and then select **Run** \> **wf.msc**.
2. Select **Inbound Rules** \> **New rule**, and then, on the **Rule Type** tab, select **Port**, and then select **Next**.
3. In the **Specific local ports** field, enter **7000**, and then select **Next**.
4. Select **Allow the connection**, and then select **Next**.
5. Select all three check boxes to apply all the rules, and then select **Next**.
6. Enter the name of the rule, and then select **Finish**.
7. Repeat these steps for outbound rules.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]