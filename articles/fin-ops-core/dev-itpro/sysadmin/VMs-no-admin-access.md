---
title: Development and build VMs that don't allow admin access FAQ
description: Access answers to frequently asked questions (FAQs) about virtual machines that don't allow administrator access.
author: yukonpeegs
ms.author: epegors
ms.topic: article
ms.date: 10/09/2019
ms.custom:  
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2017-11-30
ms.search.form:
ms.dyn365.ops.version: Platform update 12 

---

# Development and build VMs that don't allow admin access FAQ

[!include [banner](../includes/banner.md)]

This article provides answers to frequently asked questions (FAQ) about virtual machines (VMs) that don't allow administrator access. 

## How can I install a deployable package?
Whenever possible, use Microsoft Dynamics Lifecyle Services (LCS) to install a deployable package. You can install a deployable package by using the **-devinstall** option. Remember that this option requires manual database synchronization.

For more information about how to install a deployable package, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

## Is the finance and operations website accessible when Visual Studio isn't running?
Yes, you can access the finance and operations website when Microsoft Visual Studio isn't running. Microsoft Internet Information Services (IIS) Express is an .exe file that runs as the user. However, when you close Visual Studio, the XPPC agent starts regular IIS (not IIS Express) before it closes. This behavior helps to ensure that you can remotely access the Application Object Server (AOS) instance and the website, even when you sign out or the machine is restarted. We recognize that many people use these developer machines as test machines, and that they expect the AOS instance always to be running. However, IIS Express doesn't support this behavior.

## What about the other services?
You can restart Microsoft Windows services such as Microsoft SQL Server, SQL Server Reporting Services (SSRS), SQL Server Integration Services (SSIS), SQL Server Analysis Services (SSAS), Batch, Financial reporting (formerly Management Reporter), and IIS. (For IIS, you must restart the World Wide Web Publishing Service because you can't use iisreset.exe.)

## Can I clean up the service volume drive?
Yes, you have full access to the service volume drive. Therefore, you can clean up the monitoring data, and so on.

## What are the alternatives to VMs that don't allow administrator access?
Both a Microsoft Azure environment on a private Azure subscription and a local virtual hard disk (VHD) allow administrator access. However, you must run Visual Studio as an administrator. This requirement applies because the administrator has access to these alternatives only through the **administrator** group, not explicitly.

## Can I run Visual Studio as an administrator?
You are not required to run Visual Studio as an administrator. You cannot use the Remote Desktop Protocol (RDP) to connect as an administrator to VMs that are under a Microsoft-owned Azure subscription. These VMs include the Tier 1 VM that is included in the subscription and Tier 1 add-on VMs. However, if you're connecting as an administrator to a VM that isn't under a Microsoft-owned subscription, you must still run Visual Studio as an administrator.

## A "get latest" operation in Visual Studio failed because files are blocked by the AOS instance. How do I start and stop IIS?
You must use IIS Express. See the next question for more information.

## What are the instructions for using IIS Express?
When IIS Express is started, an icon appears in the notification area (near the clock). When you right-click on the IIS Express icon, all the running sites are listed. You can stop IIS Express from that menu. Some actions in Visual Studio cause IIS Express to be started, but you can also explicitly start IIS Express from Visual Studio by selecting **Restart IIS Express** on the **Dynamics 365** menu.

To ensure that debugging functions properly with IIS Express and finance and operations Visual Studio projects, we recommend the following Internet Options settings:

- Go to **Control Panel** > **Internet Options** > **Security** tab > **Internet**, and clear the **Enable Protected Mode** check box.
- Go to **Control Panel** > **Internet Options** > **Security** tab > **Restricted sites**, and clear the **Enable Protected Mode** check box.

## Can I install additional development tools (such as Fiddler and Pepper)?
No, you can't install additional development tools.

## Is there a way to run Windows PowerShell and command prompt commands as an administrator?
No, you can't run Windows PowerShell commands and commands at a prompt command as an administrator.

## Is the Trace Parser supported?
Trace Parser currently requires the user to be an administrator. It is not supported on dev/test environments that are managed by Microsoft that do not allow administrator access.

## Is the Admin user provisioning tool supported?
The **Admin user provisioning** tool currently requires the user to be an administrator. The **Admin user provisioning** tool is typically used to change the tenant of the environment, but that should not be necessary. You can update the sign in information in the database for the Admin user or any other user. You only need the SID and network alias (email address) from a user that can access the environment or another environment on the same tenant. In many cases, the SID and network alias can be found in the database that came with the environment originally. Run the following commands to get the good SID and network alias from the source environment and update them in the target environment, respectively.

```Console
-- get value from source env.
select ID, SID, NETWORKALIAS from USERINFO where ID = 'Admin'

-- update value in target env.
update USERINFO set SID = 'new_SID', NETWORKALIAS = 'new_NetworkAlias' where ID = 'Admin'
```

## Can the system be put into maintenance mode?
You can put the system into maintenance mode to change the license configuration. However, the procedure that is described in [Maintenance mode](maintenance-mode.md) isn't supported. Self-service support for maintenance mode in all environments will be added to LCS in the future. Until this support is available in LCS, you can follow these steps to put a system into maintenance mode.

1. Establish an RDP connection to the developer machine.
2. On the developer machine, sign in to SQL Server by using the credentials for the axdbadmin user from LCS. Then switch to the AXDB database, and run the following command.

    ```Console
    update SQLSYSTEMVARIABLES SET VALUE = 1 where PARM = 'CONFIGURATIONMODE'
    ```

3. Restart the **World Wide Web Publishing Service** to reset IIS.

    After the service is restarted, the system will be in maintenance mode.

4. When you've completed your maintenance mode activities, repeat steps 2 and 3, but set the value to **0** in step 2.

## Can I install a license deployable package?
### Development environments
Use LCS to install a license deployable package on any cloud development environment.
### Build environments
LCS does not allow AOT or license deployable packages to be installed on build environments. To work around this, remote into the VM and use the **-devinstall** option to install a license deployable package from the command line as described in the article, [Install deployable packages from the command line](../deployment/install-deployable-package.md). This command line install works as of platform update 17. If you are running on a platform version that is older than Platform update 17, and you do not have admin access to your build environment, create a support request and ask Microsoft to install your license deployable package.

## Is licensing Visual Studio by entering a product key supported?
Entering a product key directly in Visual Studio is not supported. Instead, use Visual Studio subscription licensing and sign in to Visual Studio with the email address (user account) associated with the license. You can link a Visual Studio license to a user account by assigning an MSDN license to the user account or by assigning a license to the user account by using https://www.visualstudio.com/subscriptions-administration.

## Can I upgrade my database to a new application release?
As of the February 2018 release of Lifecyle Services (LCS), you can execute the data upgrade package from the LCS environment page of a development environment. Executing the data upgrade package from LCS does not require you to be an administrator on the VM.

The process described in [Upgrade data in development or demo environments](../migration-upgrade/upgrade-data-to-latest-update.md) runs the data upgrade package from the command line. This requires you to be an administrator on the VM.

## What do I need to know if I am developing for Commerce?
If you are developing for Dynamics 365 Commerce, configuration steps and other important information is described in [Development in cloud-hosted development environments without admin access](../../../commerce/dev-itpro/cloud-dev-box.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
