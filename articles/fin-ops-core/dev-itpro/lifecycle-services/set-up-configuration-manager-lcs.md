---
title: Set up Configuration manager
description: This article provides information about how to set up the Configuration manager.
author: gianugo
ms.date: 10/16/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 
ms.dyn365.ops.version: 2012
ms.assetid: 0845ab95-9597-4813-9967-e4f3815849ba
---

# Set up Configuration manager

[!include [banner](../includes/banner.md)]
[!include [LCS deprecation](../includes/lcs-deprecation.md)]

> [!IMPORTANT]
> This feature is **not** supported for production use. Configuration manager (beta) relies on entities from the Data Import/Export Framework in your environment. Because these entities do not currently include all the functionality in AX 2012 R3, some configuration data is not copied between environments.

## Before you begin
Before you begin, your environment must include the following components:

- A running version of AX 2012 R3 that has been configured for your business. For more information about how to install AX 2012 R3, see [Install Microsoft Dynamics AX 2012](/dynamicsax-2012/appuser-itpro/install-microsoft-dynamics-ax-2012).
- A running instance of the Data Import/Export Framework. For more information about how to install the Data Import/Export Framework, see [Install the Data import/export framework (AX 2012 R#)](/dynamicsax-2012/appuser-itpro/install-the-data-import-export-framework-ax-2012-r3). 

    > [!IMPORTANT]
    > You must deploy the DMFEntityExecutionStatusService and DMFService service groups to enable to Configuration manager (beta) to connect to Data Import/Export Framework.

- An AX 2012 R3 project in Lifecycle Services. 

    > [!WARNING]
    > Copying configurations between environments can be a destructive operation. All project owners have the right to configure and perform these operations. Make sure that only trusted individuals are set as project owners.

## Create Data Import/Export Framework source data formats in AX 2012 R3
You must create both a Dynamics AX and a CSV source data format to manage configurations in all environments where you intend to export and import configurations.

### Create an AX source data format

Complete the following procedure in the environment that you intend to export a configuration from.

1.  Click **Data import export framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**, and name the source AX.
3.  Verify that the type is **AX.**
4.  Repeat this procedure in the environment that you intend to import the configuration to.

### Create a CSV source data format

Complete the following procedure in the environment that you intend to export a configuration from.

1. Click **Data import export framework** &gt; **Setup** &gt; **Source data formats**.
2. Click **New**, and name the source CSV.
3. Verify that the type is **File**.
4. On the **General** tab, set the following values.

   |                  Setting                  |     Value      |
   |-------------------------------------------|----------------|
   |       <strong>File format</strong>        |   Delimited    |
   |     <strong>First row header</strong>     |    Selected    |
   |      <strong>Row delimiter</strong>       |    {CR}{LF}    |
   |     <strong>Column delimiter</strong>     | Vertical bar { |
   |      <strong>Text qualifier</strong>      |       @@       |
   |         <strong>Skip row</strong>         |       0        |
   |        <strong>Code page</strong>         |      1252      |
   |     <strong>Language locale</strong>      |     EN-US      |
   | <strong>Multiple value separator</strong> |       ;        |

   ![DIXF settings for Configuration manager.](./media/dixfconfigurationmanager.png)

5. Repeat this procedure in the environment that you intend to import the configuration to.

## Install and configure the local component of the System diagnostics (Lifecycle Services)
Complete the following procedure in the environment that you intend to export a configuration from. 

> [!IMPORTANT]
> If you have already installed the local component of the System diagnostics for your project and environment, you must uninstall it by using **Add/Remove programs**. Only one instance of Microsoft Dynamics AX Application Object Server (AOS) per environment can be used with Configuration management, regardless of the number of instances that are discovered.

1.  Install the local component of the System diagnostics. For details, see [Install and run System diagnostics](/dynamicsax-2012/appuser-itpro/install-run-system-diagnostics). Important: For this beta release, we require that you add the service account for the System diagnostics to the sysadmin role in AX 2012 R3.
2.  Click **Start** &gt; **Microsoft Dynamics AX Lifecycle Services Diagnostic Service Discovery**.
3.  In the **Environment Discovery** window, enter a name for the environment, and the fully-qualified name of the Microsoft SQL Server instance and database. Then click Discover environment.
4.  After discovery is completed, enter the values in the **Configuration management (Beta)** section, click **Save**, and then click **Upload environment**.

    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Option</th>
    <th>Value</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><span class="ui">Enable configuration overwrites</span></td>
    <td>Select this option to enable configurations to be copied and overwritten for the specified AOS instance.
    <p><strong>Important:</strong> We strongly recommend that you disable configuration overwrites when you have fully configured an environment.</p>
    </td>
    </tr>
    <tr class="even">
    <td><span class="ui">AOS instance</span></td>
    <td>Specify the AOS instance that can be copied from or overwritten.</td>
    </tr>
    <tr class="odd">
    <td><span class="ui">Storage location</span></td>
    <td>Specify the location where configurations are stored locally. The AOS service account and the Data Import/Export Framework service account must have read and write access to this location.
    <p><strong>Important:</strong> We strongly recommend that you use the same directory that is used for the Data Import/Export Framework.Be aware that the shared directory might contain sensitive data, depending on what you are importing and exporting. Make sure that as few users as possible, in addition to the AOS service account and the Data Import/Export Framework service account, have access to the location.</p>
    </td>
    </tr>
    </tbody>
    </table>

    ![System diagnostic discovery for Config manager.](./media/systemdiagnosticconfigurationmanagerdiscoverysettings.png)

5.  Repeat this procedure in the environment that you intend to import a configuration to.

## Next steps
The environment is now ready for you to copy and manage configurations. For more information, see [Copy configurations by using Configuration manager](copy-configuration-lcs.md).





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
