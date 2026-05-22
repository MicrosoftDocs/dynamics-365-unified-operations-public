---
title: AX 2009 migration - Install the Data migration tool
description: Learn about how to set up the Data migration tool (DMT) so that you can migrate your data from Microsoft Dynamics AX 2009.
author: pnghub
ms.author: johnmichalak
ms.topic: install-set-up-deploy
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 migration – Install the Data migration tool

[!include [banner](../includes/banner.md)]

This article explains how to set up the Data migration tool (DMT) so that you can migrate data from Microsoft Dynamics AX 2009 to finance and operations.

> [!IMPORTANT]
> Currently, the DMT is in private preview. If you're interested, you can sign up for the [Preview Program](https://microsoft.qualtrics.com/jfe/form/SV_brOLCioQ7mmeykB). The public release date for the DMT isn't set.

## Prerequisites

- Microsoft SQL Server 2008, 2012, 2014, or 2016.
- The Microsoft .NET Framework version 4.5 or later.
- Microsoft SQL Server machine that has Microsoft SQL 2012 Native Client installed.
- The Microsoft SQL Server Integration Services (SSIS) service installed and running on the machine where you install the DMT service.
- SQL Server authentication that supports both SQL authentication and Microsoft Windows authentication.
- Microsoft Access database engines that follow the version guidance in the following table.

    | Office version                    | SQL Server 2008                 | SQL Server 2012 and later |
    |-----------------------------------|---------------------------------|---------------------------|
    | **No Microsoft Office on the VM** | Access engine 32-bit            | Access engine 64-bit      |
    | **Microsoft Office 32-bit**       | Access engine 32-bit            | Access engine 64-bit      |
    | **Microsoft Office 64-bit**       | Access engine 32-bit and 64-bit | Access engine 64-bit      |

- Microsoft Dynamics AX 2009 SP1 5.0.1000.52 or later.
- The prerequisite patch (axpatch.exe) installed. To find the patch, from the location where you downloaded and extracted the zip file, go to <pre-requisiteforpatch\>\<application\>.

## Install DIXF service

1. Go to the location where you extracted the zip file. In the **DIXF msi** folder, right-click **DIXF\_Service\_x64.msi**, and select **Run**.
1. When the wizard starts, select **Next**.
1. Accept the license terms, and then select **Next**.
1. Select an account for the service, and then select **Next**. The account should have admin rights. If you select the **Network Service** check box, verify that the network service account has admin rights. Otherwise, clear the check box, and enter an admin account user name and password. Then select **Next**.
1. Select the SQL Server version, and then select **Next**.
1. Select **Install**, and then, when the wizard is completed, select **Finish**.

## Copy binaries

Go to the location where you extracted the zip file. Copy the following files to the **Program Files (x86)\\Microsoft Dynamics AX\\50\\Client\\Bin** folder:

- Microsoft.Dynamics.AX.Framework.Tools.DMT.dll
- Interop.Shell32.dll

## Install DMT components for AX 2009

There are two ways to install the DMT. You can use the combined XPO file or an application hotfix. If you're using a Microsoft Dynamics Lifecycle Services Implementation project, use the application hotfix. Installation takes approximately seven hours.

### Combined XPO file

1. Extract the combined XPO file from **DMT_V1.0\CombinedXPO**.
1. Import the combined XPO file into AX 2009.
1. Copy the label file from **DMT_V1.0\Label file** to the **Program Files\\Microsoft Dynamics AX\\50\\Application\\Appl\\<NameOfYourDeployment\>** folder.
1. Restart the Application Object Server (AOS) instance.
1. In AX 2009, select **Data migration** \> **Setup** \> **Compile and synchronize DMT application**.

The combined XPO file is imported into the layer that the user signs in to.

### Application hotfix

1. Go to **DMT_V1.0\\ApplicationHotfix\\DynamicsAX2009-KB4010403-SP1**, right-click **setup.exe**, and then select **Run**.
1. In AX 2009, in the Application Object Tree (AOT), notice that the **LegalEntityId** field is added to the **DMTCustomerAddressView** and **DMTVendorAddressView** views.
1. Select **Data migration** \> **Setup** \> **Compile and synchronize DMT application**.

## Parameter setup

Go to the location where you extracted the zip file, and find **defaultvalue.xlsx**.

> [!NOTE]
> The file is saved in .xlsx format. Don't change the extension. When you provide this file as input for the **Default configuration** parameter, select **All Files** so that you can select the .xlsx format. If you don't select this format, errors occur when you start to generate mappings.

1. In AX 2009, select **Data migration** \> **Setup** \> **Configure default maps**, and enter the appropriate information in the following fields:

    - **Default configuration** – Enter the path of the Microsoft Excel file.
    - **Export file path** – Enter the server path that the service can access.
    - **SQL Server user and password** – Enter the SQL authentication credentials for the AX 2009 database.

1. Close the form.
1. Under **Setup**, select **Configure connections**, and enter the appropriate information in the following fields:

    - **DIXF service host** – Enter the host name of the DIXF service installation.
    - **Tenant URL** – Enter the URL for the application tenant. If you're not sure of the tenant, see the web.config file for the finance and operations applications.

    > [!NOTE]
    > In the Azure portal, when you create a new app in Microsoft Entra (Microsoft Entra ID), you can select from two options: **Web API** and **Native**. In this instance, select **Native** and grant permissions to native Microsoft Entra app.

## Multibox setup

For a multibox setup, you need the following machines:

- Machine A, where you install the AX 2009 database and DIXF service
- Machine B, where you install the AX 2009 AOS instance
- Machine C, where you install the AX 2009 client

In this three-machine setup, you configure machine C to connect to the AOS instance on machine B. You connect machine B to the database that you configure on machine A.

### DIXF service machine prerequisites (machine A)

The DIXF service on machine A requires the following prerequisites:

- SQL Server 2008, 2012, or 2014
- The .NET Framework version 4.5
- Access database engines

  - **For SQL Server 2008:** Access engine 32-bit and 64-bit (if Microsoft Excel is 64-bit)
  - **For SQL Server 2012 or later:** Access engine 64-bit

- AX 2009 database (configured on SQL Server)

### AOS machine prerequisites (machine B)

The AOS installation on machine B requires the following prerequisites:

- AX 2009 AOS Server
- Application files

### Client machine prerequisites (machine C)

The client installation on machine C requires the following prerequisite:

- AX 2009 client

### Shared folder permissions

You need to share the path of the default configuration file and the export package file. Client users and the DIXF service need read/write access to these files. To grant this access, select **Data migration** \> **Setup** \> **Configure and generate maps**, and then select **Validate path** to verify that the required access is available.

### Set up parameters

1. Select **Data migration** \> **Setup** \> **Configure connections**.
1. In the **DIXF service host** field, enter the name of the remote machine where you installed the DIXF service. By default, the name is **localhost**.
1. Select **Validate** to check that the client can access the DIXF service.

### Workarounds

If you receive an error message that states, "DIXF service is unavailable," complete the following workaround to enable a service connection for port 7000.

1. Open port 7000. For inbound rules on the DMT service machine, select **Firewall settings**, and then select **Run** \> **wf.msc**.
1. Select **Inbound Rules** \> **New rule**. On the **Rule Type** tab, select **Port**, and then select **Next**.
1. In the **Specific local ports** field, enter **7000**, and then select **Next**.
1. Select **Allow the connection**, and then select **Next**.
1. Select all three check boxes to apply all the rules, and then select **Next**.
1. Enter the name of the rule, and then select **Finish**.
1. Repeat these steps for outbound rules.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
