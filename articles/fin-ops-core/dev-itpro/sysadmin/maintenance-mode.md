---
# required metadata

title: Maintenance mode
description: This article describes maintenance mode, which is a system-wide setting that lets system administrators make system changes that can affect system functionality.
author: laneswenka
ms.date: 08/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysConfiguration
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 70292
ms.assetid: c11a35e8-40bb-4005-adf3-cfd998a418fc
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Maintenance mode

[!include [banner](../includes/banner.md)]

This article provides information about maintenance mode in finance and operations apps. When maintenance mode is turned on, it provides a safe way for system administrators to make system changes that might affect system functionality. For example, configuration keys can be enabled or disabled. While maintenance mode is on, only system administrators and users who have the **Maintenance mode user** role can sign in to the system. By default, maintenance mode is turned off. When maintenance mode is off, you can't edit the **License configuration** page.

> [!Note]
> After enabling maintenance mode on an environment, only one interactive AOS and one non-interactive AOS (batch AOS) will be available for use.

## Turn maintenance mode on and off on sandbox and production environments through Lifecycle Services 
You can now turn maintenance mode on and off directly through Microsoft Dynamics 365 Lifecycle Services on your sandbox and production environments. 

To turn maintenance mode on and off directly through Lifecycle Services, follow these steps.

1. Go to the environment details page and on the **Maintain** menu, click **Enable Maintenance Mode**. 
2. In the slider, set **Turn maintenance mode on** for the environment and select **Confirm**.
3. A servicing operation will begin and your system  will go into maintenance mode.
4. On completion, the environment state will be **In Maintenance**. At this point, only the system administrator will have access to the environment.
5. After you are done making system-wide changes, you can turn off maintenance mode by clicking **Disable Maintenance Mode** under the **Maintain** menu.
6. A servicing operation starts and takes your environment out of maintenance mode. You can see the progress of the operation in the environment details page.
7. After this is complete, your environment goes back to the **Deployed** state. Now all users can sign in to the environment.
8. You can check the environment history page to see when the maintenance mode was turned on or turned off. To get to the environment history page, select **History** and **Environment changes** on the environment details page.

Turning maintenance mode on and off for your sandbox and production environment is very similar to a servicing operation. If turning maintenance mode on or off fails, you will see options such as **Resume**, **Rollback**, and **Abort**. You can also **download the logs** to troubleshoot why the operation failed.

## Turn maintenance mode on and off in DevTest/Demo environments hosted in Customer's subscription
1. Establish an RDP connection to the developer machine.
2. On the developer machine, sign in to SQL Server by using the credentials for the axdbadmin user from Lifecycle Services. Then switch to the AXDB database, and run the following command.

    ```Console
    update SQLSYSTEMVARIABLES SET VALUE = 1 where PARM = 'CONFIGURATIONMODE'
    ```

3. Restart the **World Wide Web Publishing Service** to reset IIS.
4. After the service is restarted, the system will be in maintenance mode.
5. When you've completed your maintenance mode activities, repeat steps 2 and 3, but set the value to 0 in step 2.

## Turn maintenance mode on and off for VHD-based environments hosted by customers

You can turn on maintenance mode locally by running the following command. 

> [!Note]
> On some virtual machines (VMs), the exact location of the Deployment.Setup.exe tool might differ. Check AosServiceWebRootbin.

```Console
J:\AosService\PackagesLocalDirectory\Bin\Microsoft.Dynamics.AX.Deployment.Setup.exe --metadatadir J:\AosService\PackagesLocalDirectory --bindir J:\AosService\PackagesLocalDirectory\Bin --sqlserver . --sqldatabase axdb --sqluser axdbadmin --sqlpwd ********* --setupmode maintenancemode --isinmaintenancemode true
```
After running the command, you will want to restart the **World Wide Web Publishing Service** to reset IIS. The system will then be in maintenance mode.  

The following table describes the parameters that are used in this command.

| Parameter name              | Description  |
|-----------------------------|------|
| --setupmode maintenancemode | Use this parameter to inform the setup tool that the system will be put into or taken out of maintenance mode.    |
| --metadatadir               | Use this parameter to specify the metadata directory. You should use the default packages directory.              |
| --bindir                    | Use this parameter to specify the binaries directory. You should use the default packages directory.              |
| --sqlserver                 | Use this parameter to specify the Microsoft SQL Server. For one-box environments, use a period (**.**).           |
| --sqluser                   | Use this parameter to specify the SQL Server user. You should use **AOSUser**.                                    |
| --sqlpwd                    | Use this parameter to specify the SQL Server password.                                                            |
| --isinmaintenancemode       | Use this parameter to turn configuration mode on or off. Use **true** to turn it on and **false** to turn it off. |


## Turn maintenance mode on and off in Finance + Operations (on-premises) environments

Ensure you have at least version 2.18.2 of the infrastructure scripts. For more information on obtaining the scripts, see [Obtain the infrastructure scripts for your Finance + Operations (on-premises) deployment](../deployment/obtain-infrascripts-onprem.md).

1. To enable maintenance mode, run the following script from any node in your Service Fabric cluster.
```powershell
.\Set-MaintenanceMode.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Enable
```
> [!IMPORTANT]
> The script will restart all of your Application Object Server (AOS) instances.

1. After your AOS instances are running again, the system will be in maintenance mode.
1. When you've completed your maintenance mode activities, run the following script from any node in your Service Fabric cluster.
```powershell
.\Set-MaintenanceMode.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Disable
```


## Enable (or disable) configuration keys

After the instance of Application Object Server (AOS) is restarted, the system will be in maintenance mode. You can then enable configuration keys, as shown in the following screenshot. 

[![License configuration page when not in maintenance mode.](./media/license-configuration-page-when-not-in-maintenance-mode.png)](./media/license-configuration-page-when-not-in-maintenance-mode.png) 

If you try to access the system while in maintenance mode, but you aren't a system administrator or a user who has the **Maintenance mode user** role, you may receive an error message. 

You can turn off maintenance mode by running the following command.

```Console
J:\AosService\PackagesLocalDirectory\Bin\Microsoft.Dynamics.AX.Deployment.Setup.exe --metadatadir J:\AosService\PackagesLocalDirectory --bindir J:\AosService\PackagesLocalDirectory\Bin --sqlserver . --sqldatabase axdb --sqluser axdbadmin --sqlpwd ********* --setupmode maintenancemode --isinmaintenancemode false
```
After running the command, you will want to restart the **World Wide Web Publishing Service** to reset IIS. The system will then be out of maintenance mode.  


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

