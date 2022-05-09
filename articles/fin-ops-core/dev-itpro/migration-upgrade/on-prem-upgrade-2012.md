---
# required metadata

title: Data upgrade process for AX 2012 to Dynamics 365 Finance + Operations (on-premises)
description: This topic describes the process for upgrading Microsoft Dynamics AX 2012 databases to Dynamics 365 Finance + Operations (on-premises) version 10.0.x.
author: faix
ms.date: 12/16/2020
ms.topic: article
ms.prod: dynamics-365
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2020-06-30 
ms.dyn365.ops.version: 10.0.0

---

# Data upgrade process for AX 2012 to Dynamics 365 Finance + Operations (on-premises)

[!include [banner](../includes/banner.md)]

This topic describes the process for upgrading Microsoft Dynamics AX 2012 databases to Dynamics 365 Finance + Operations (on-premises) version 10.0.x. Currently, upgrade is supported only from either Dynamics AX 2012 R2 or Dynamics AX 2012 R3. 

> [!IMPORTANT]
> This topic explains the process for doing a data upgrade only. For information about how to do a code upgrade, see the upgrade guides that are available for cloud versions. The code upgrade tooling is available only through Microsoft Dynamics Lifecycle Services (LCS).

## AX 2012 upgrade to Dynamics 365 Finance + Operations (on-premises)

Two upgrade methods are currently supported:

- **Upgrade from inside the VHD** – This method involves copying your database into the virtual hard disk (VHD) and running the upgrade from inside the VHD. Overall, this method is easier.
- **Upgrade where the VHD points to your database** – This method involves pointing the VHD upgrade process to your database. The upgrade process is still run from inside the VHD.

> [!NOTE]
> The VHD doesn't require external network access to run the upgrade process.

### Prerequisites

1. [Sign up for a preview subscription](upgrade-overview-2012.md#sign-up-for-a-preview-subscription).
1. For each AX 2012 release, update to the most recent cumulative update that is available before you upgrade to the most recent Finance + Operations application release.
1. Install the pre-upgrade checklist. For more information, see [Installation](prepare-data-upgrade.md#installation).
1. Go through the data upgrade preparation steps. You can skip the "Set up user mapping" step. This step is relevant only for cloud-hosted upgrades.
1. Make a backup of your database (MicrosoftDynamicsAX). For more information, see [Create a Full Database Backup](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server).
1. In LCS, go to the Shared asset library by selecting the tile on the right side of the page. Then, under **Select asset type**, select **Downloadable VHD**, and download all parts of the VHD package that most closely matches the version that you will upgrade to in your on-premises environment. The image requires a large amount of disk space. Therefore, be sure to download and extract the package on a drive that has enough free space. 
1. The files that you downloaded are a self-extracting zip file. Extract the VHD to a location that has a good amount of free space.
1. Use Hyper-V to start a virtual machine (VM) and attach the VHD. (Note that the VM must be Generation 1.)
1. Connect to the VM. For information about the credentials, see [Running the Virtual Machine (VM) locally](../dev-tools/access-instances.md#running-the-virtual-machine-locally).
1. Depending on your planned on-premises target version of 10.0.x and the VHD image that you downloaded, you might have to download and apply the required application update and platform update from the Shared asset library. Under **Select asset type**, select **Software deployable package**. For more information, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

    > [!IMPORTANT]
    > In any case, make sure that you've applied the most recent quality update to your VHD, to ensure that it contains the most recent fixes for doing data upgrades. 

1. If you have any extensions or customizations, install them on the VHD now. Otherwise, the upgrade process will remove any data that is related to customizations. If you must prepare your environment before the upgrade, check with your independent software vendor (ISV) or value-added reseller (VAR).

### Upgrade from inside the VHD

1. Restore the backup that you created to the OneBox VM. For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).
1. Optional: If the name of your restored database isn't **AXDB**, open Windows PowerShell as an administrator, and run the following script.

    ```powershell
    .\Configure-On-Premises-Upgrade.ps1 -DatabaseName '<DB-name>'
    ```

    > [!NOTE] 
    > Replace **\<DB-name\>** with the name of your database (for example, **AXDB**). If you want to edit more values, see the [appendix](#appendix) later in this topic.

    The script will run a database connection test to verify that the information that you provided is valid.

1. In LCS, go to the Shared asset library. Under **Select asset type**, select **Software deployable package**, and then select **AX2012DataUpgrade-10-0-8** to download the **MajorVersionDataUpgrade.zip** file.
1. Copy the file, paste it in the desired location (for example: **c:\\D365FFOUpgrade\\**), and unzip it.
1. Open a Command Prompt window as an administrator, change the directory to the folder that you just unzipped, and run the following commands.

    1. `AxUpdateInstaller.exe generate -runbookid=upgrade -runbookfile=upgrade.xml -topologyfile=defaulttopologydata.xml -servicemodelfile=defaultservicemodeldata.xml`
    2. `AxUpdateInstaller.exe import -runbookfile=upgrade.xml`
    3. `AxUpdateInstaller.exe execute -runbookid=upgrade`

1. After the upgrade process is successfully completed, back up the newly upgraded database. If you have customizations from ISVs or VARs, check whether you must run some post–data upgrade scripts.
1. Restore the database into your on-premises environment's SQL Server, but give it a name that differs from the name of the AX 2012 database (for example, name it **AXDBupgraded**). The restored database must be configured. Follow the steps in [Configure the Finance + Operations database](../deployment/setup-deploy-on-premises-pu12.md#configure-the-finance--operations-database).
1. Deploy a new Dynamics 365 Finance + Operations (on-premises) environment.

    - If you have customizations, follow these steps:

        1. In LCS, go to the Shared asset library.
        1. Under **Select asset type**, select **Model**, and then download **Dynamics 365 Finance + Operations on-premises, Version 10.0.x Demo Data**. Select the version that is closest to the 10.0.x environment that you will deploy as the on-premises baseline.
        1. Use the restore backup option for SQL Server to create a new database from this file. (Typically, this database is named **AXDB**.) For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).
        1. The demo database must be configured. Follow the steps in [Configure the Finance + Operations database](../deployment/setup-deploy-on-premises-pu12.md#configure-the-finance--operations-database).
        1. In LCS, set up a new environment, and deploy it with version 10.0.x. For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md). When you deploy the environment, the name of the database that you specify should be the name of the database that you created earlier (typically **AXDB**).
        1. Apply your own customizations, and ISV and VAR modules, to the newly created 10.0.x environment. Otherwise, when the environment is initially synced with the database, it will delete any customization-related or extension-related data.
        1. Shut down on-premises Application Object Server (AOS), Business Intelligence (BI), and Management Reporter (MR) servers, or stop the services from the Azure Service Fabric portal by selecting **Deactivate (Restart)**.
        1. Rename or delete the demo database (typically **AXDB**) that you used for deployment, and then rename your new database (typically **AXDBupgraded**) to the name that the demo database had (typically **AXDB**).
        1. The renamed database must be configured. Follow the steps in [Configure the Finance + Operations database](../deployment/setup-deploy-on-premises-pu12.md#configure-the-finance--operations-database).
        1. Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal by selecting **Activate**.

            > [!NOTE]
            > The Database synchronization process will be triggered when the AOS nodes start up, and your environment will be unavailable until the process is completed.

    - If you don't have customizations, follow these steps:

        1. Optional: Rename your old database (typically **AXDBold**), and then rename your new database (typically **AXDB**). In the next step, make sure that you enter the name of the upgraded database.
        2. In LCS, set up a new environment, and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md).

### Upgrade where the VHD points to your database

1. Back up the database from your on-premises environment (typically **AXDB**). For more information, see [Create a Full Database Backup (SQL Server)](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server).
1. Restore the backup that you just created into the database server, and give it a different name (for example, **AXDBtoupgrade**). For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).
1. Open Windows PowerShell as an administrator, and run the following script.

    ```powershell
    .\Configure-On-Premises-Upgrade.ps1 -DatabaseName '<DB-name>' -DatabaseServer '<SqlServerName>' -DatabaseUser '<User>' -DatabasePassword '<Password>'
    ```

    > [!NOTE]
    > - Replace **\<DB-name\>**, **\<SqlServerName\>**, **\<User\>**, and **\<Password\>** with the values that you require.
    > - Only SQL Server authentication is officially supported for this upgrade. For more information, see [Create a Database User](/sql/relational-databases/security/authentication-access/create-a-database-user).
    > - You must add the certificate authority certificate that signed your SQL Server certificate to the trusted certificate authorities store in your Onebox VHD. For more information, see [Installing the trusted root certificate](/skype-sdk/sdn/articles/installing-the-trusted-root-certificate).
    > - Make sure that the database user that you use has the **sysadmin** server role, or at least **All Privileges**, assigned on the database that you want to upgrade. Also make sure that the user has permissions to access tempDB. Step 6 of the upgrade process will fail if these conditions aren't met.
    > - When you install the certificate authority certificate in the OneBox VHD, make sure that you use the fully qualified domain name (FQDN) or IP address to connect to the database that appears there. If you can't access the database by using the domain name, because it doesn't point to that server, edit your hosts file, and add the FQDN and the IP address that the FQDN should be resolved to.

1. In LCS, go to the Shared asset library. Under **Select asset type**, select **Software deployable package**, and then select **AX2012DataUpgrade-10-0-8** to download the **MajorVersionDataUpgrade.zip** file.
1. Copy the file, paste it in the desired location (for example: **c:\\D365FFOUpgrade\\**), and unzip it.
1. Open a Command Prompt window as an administrator, change the directory to the folder that you just unzipped, and run the following commands.

    1. `AxUpdateInstaller.exe generate -runbookid=upgrade -runbookfile=upgrade.xml -topologyfile=defaulttopologydata.xml -servicemodelfile=defaultservicemodeldata.xml`
    2. `AxUpdateInstaller.exe import -runbookfile=upgrade.xml`
    3. `AxUpdateInstaller.exe execute -runbookid=upgrade`

1. If you have customizations from ISVs or VARs, check whether you must run some post–data upgrade scripts.
1. Run the **Configure-OnpremUpgrade.ps1** script by using the values that are stated in the [Resetting the VHD database (Optional)](#resetting-the-vhd-database-optional) section later in this topic.
1. Configure your upgraded database for Finance + Operations by following the steps in [Configure the Finance + Operations database](../deployment/setup-deploy-on-premises-pu12.md#configure-the-finance--operations-database).
1. Deploy a new Dynamics 365 Finance + Operations (on-premises) environment.

    - If you have customizations, follow these steps:

        1. In LCS, go to the Shared asset library.
        1. Under **Select asset type**, select **Model**, and then download **Dynamics 365 Finance + Operations on-premises, Version 10.0.x Demo Data**. Select the version that is closest to the 10.0.x environment that you will deploy as the on-premises baseline.
        1. Use the restore backup option for SQL Server to create a new database (typically **AXDB**) from this file. For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).
        1. The demo database must be configured. Follow the steps in [Configure the Finance + Operations database](../deployment/setup-deploy-on-premises-pu12.md#configure-the-finance--operations-database).
        1. In LCS, set up a new environment, and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md). When you deploy the environment, the database that you should specify should be the database that you configured earlier (typically **AXDB**).
        1. Apply your own customizations, and ISV and VAR modules, to the newly created 10.0.x environment. Otherwise, when the environment is initially synced with the database, it will delete any customization-related or extension-related data.
        1. Shut down on-premises AOS, BI, and MR servers, or stop the services from the Service Fabric portal.
        1. Rename or delete the demo database (typically **AXDB**) that you used for deployment, and then rename your new database (typically **AXDBupgraded**) to the name that the demo database had (typically **AXDB**).
        1. Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal.

            > [!NOTE]
            > The Database synchronization process will be triggered when the AOS nodes start up, and your environment will be unavailable until the process is completed.

    - If you don't have customizations, follow these steps:

        1. Optional: Rename your old database (typically **AXDBold**), and then rename your new database (typically **AXDB**). In the next step, make sure that you enter the name of the upgraded database.
        2. Set up a new environment, and deploy it with version 10.0.x. For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md).

### Configuring existing users

If you followed either of the previous procedures, you can sign in by using the Administrator user that you specified in LCS. However, none of your other users can sign in until they have been configured for the new system. Run a **Select** statement against your USERINFO table, and make a note of the value in the **NETWORKDOMAIN** field for the Administrator user (for example, `https://adfs.contoso.com/adfs` or `http://adfs.contoso.com/adfs/services/trust`). Then, for all interactive users who should be able to sign in, set the **NETWORKDOMAIN** field to the same value that the Administrator user has. The **NETWORKALIAS** field must also be modified. In Finance + Operations, this field is set to the user's email address (for example, `testuser@contoso.com`).

### Resetting the VHD database (Optional)

If you used the **Configure-On-Premises-Upgrade.ps1** script, run the following command to reset your database to the default configuration.

```powershell
.\Configure-OnPremUpgrade.ps1 -DatabaseName 'AxDB' -DatabaseServer 'localhost' -DatabaseUser 'axdbadmin' -DatabasePassword 'AOSWebSite@123'
```

## Appendix

### Using the Configure-On-Premises-Upgrade.ps1 script

> [!IMPORTANT]
> This script is intended to be run only from a OneBox VHD environment.
>
> The script requires that you pass at least the **DatabaseName** parameter. If you don't pass this parameter, the script automatically requests it.

You can pass an additional parameter, such as **DatabaseServer** or **DatabaseUser**, if you want. However, in this case, the script will request all additional parameters. This behavior occurs because the script will assume that you want to point the database connection to a machine outside the VM. Therefore, those parameters are required to correctly establish the connection.

The following parameters can be passed to the script:

- **-DatabaseName** – The name of the database to upgrade.
- **-DatabaseServer** – The database server that contains the Finance + Operations database.
- **-DatabaseUser** – The user name for SQL Server Authentication.
- **-DatabasePassword** – The password for SQL Server Authentication.

After the configuration has been passed, the script uses the new parameters to run a database connection test. If the script can't connect to the database, we recommend that you debug the connection from SQL Server Management Studio or another tool.

**Configure-On-Premises-Upgrade.ps1**

```powershell
<#
.Synopsis
    Configures a OneBox deployment to upgrade an OnPrem 7.x database to OnPrem 10.0.x 

.DESCRIPTION
    This must be executed before the upgrade process is carried out.

.EXAMPLE
    .\Configure-OnPremUpgrade.ps1 -DatabaseName 'AxDB'

    .\Configure-OnPremUpgrade.ps1 -DatabaseName 'AxDB' -DatabaseServer '127.0.0.1' -DatabaseUser 'axdbadmin' -DatabasePassword 'secretPass'
#>
[CmdletBinding()]
param
(
    # Database server containing Microsoft Dynamics 365 for Operations, on-premises database.
    [AllowNull()]
    [string] $DatabaseServer,

    # Database name that you want to upgrade.
    [Parameter(Mandatory = $true)]
    [string] $DatabaseName,

    # Username for SQL Authentication.
    [AllowNull()]
    [string] $DatabaseUser,

    # Password for SQL Authentication.
    [AllowNull()]
    [string] $DatabasePassword
)

$webroot = "C:\AOSService\webroot"

$commandParameter = " -decrypt `"$webroot\web.config`""

$command = Resolve-Path "$webroot\bin\Microsoft.Dynamics.AX.Framework.ConfigEncryptor.exe"

Start-Process $command $commandParameter -PassThru -Wait

if([string]::IsNullOrEmpty($DatabaseUser) -and [string]::IsNullOrEmpty($DatabasePassword) -and [string]::IsNullOrEmpty($DatabaseServer)) { 

    [xml]$web = Get-Content $webroot\web.config

    $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.Database']").value = [string]$DatabaseName

}
else { 

    if([string]::IsNullOrEmpty($DatabaseServer)){

        $DatabaseServer = if($value = Read-Host 'What is the IP or FQDN of the Database server? [127.0.0.1]') {$value} else {'127.0.0.1'}

    }

    if([string]::IsNullOrEmpty($DatabaseUser)){

        $DatabaseUser = if($value = Read-Host 'What is the SQL Authentication username? [axdbadmin]') {$value} else {'axdbadmin'}

    }

    if([string]::IsNullOrEmpty($DatabasePassword)){

        $dbPassEn = if($value = Read-Host 'What is the SQL Authentication password?' -AsSecureString) {$value} else {''}

        $BSTR = [System.Runtime.InteropServices.Marshal]::SecureStringToBSTR($dbPassEn) 

        $DatabasePassword = [System.Runtime.InteropServices.Marshal]::PtrToStringAuto($BSTR)

    } 

    [xml]$web = Get-Content $webroot\web.config

    $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.DbServer']").value = [string]$DatabaseServer

    $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.Database']").value = [string]$DatabaseName

    $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.SqlUser']").value = [string]$DatabaseUser

    $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.SqlPwd']").value = [string]$DatabasePassword

}
#Save Configuration to webroot config
$web.Save("$webroot\web.config")

#Reloading the configuration to run test
[xml]$web = Get-Content $webroot\web.config

$TestDbServer = $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.DbServer']").value

$TestDbName = $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.Database']").value

$TestDbUser = $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.SqlUser']").value

$TestDbPass = $web.SelectSingleNode("configuration/appSettings/add[@key='DataAccess.SqlPwd']").value

#Setting up connection test.

$dbConn = New-Object System.Data.SqlClient.SqlConnection

$dbConn.ConnectionString = "Data Source=$TestDbServer;User ID=$TestDbUser;Password=`"$TestDbPass`";Database=$TestDbName"

try{

    $dbConn.Open()

    $result = $true

}

catch{

    $result = $_.Exception.Message

}
Finally{

    $dbConn.Close()

}

$commandParameter = " -encrypt `"$webroot\web.config`""

Start-Process $command $commandParameter -PassThru -Wait

if($result -ne $true){

    Write-Host "`nThe connection to the Database Server failed:" -ForegroundColor Red
    Write-Host $result -ForegroundColor Red

}
else{

    Write-Host "`nThe connection to the Database Server was successful!" -ForegroundColor Green

}
```

### Troubleshooting

- Exception calling "Open" with "0" argument(s): "Cannot open database "AxDB1" requested by the login. The login failed. Login failed for user 'axdbadmin'." You supplied the Wrong database name or the user doesn't have access to that database. 
- Exception calling "Open" with "0" argument(s): "A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server)". The script could not establish a connection with the SQL Server specified. Check the ip/fqdn and port that you used.  
- Exception calling "Open" with "0" argument(s): "Login failed for user 'axdbadmin'." The supplied login credentials are not correct.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
