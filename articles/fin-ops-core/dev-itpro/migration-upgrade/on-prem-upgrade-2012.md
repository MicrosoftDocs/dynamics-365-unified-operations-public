---
# required metadata

title: Data upgrade process for AX2012 to D365 For Finance and Operations on-premises
description: This topic provides the process for upgrading AX2012 databases to D365 for Finance and Operations on-premises 10.0.x.  
author: faix
manager: AnnBe
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 10.0.x

---

#  Data upgrade process for AX2012 to D365 For Finance and Operations on-premises

[!include [banner](../includes/banner.md)]

This topic provides the process for upgrading Microsoft Dynamics AX 2012 databases to D365 for Finance and Operations on-premises 10.0.x. Upgrade is currently only supported from either Dynamics AX 2012 R2 or Dynamics AX 2012 R3. 

> [!IMPORTANT]
> This guide only explains the process of performing a data upgrade. For information on how to do a code upgrade please check the upgrade guides available for cloud versions. The code upgrade tooling is only available through LCS.

## AX2012 upgrade to D365 for Finance and Operations On-premise

To upgrade, there are two possible paths that are currently supported.

An overview of each path is given below:

-   **Upgrading from within VHD** - This path involves copying your database into the virtual hard disk (VHD) and executing the upgrade inside it. Overall, this is the simpler method.

-   **Upgrading with VHD pointing to your database** - This path involves pointing the VHD upgrade process to your database. The upgrade process is still executed from within the VHD.

> [!NOTE]
> The VHD does not need external network access in order to carry out the upgrade process.

### Prerequisites

1. [Sign up for a Lifecycle Services trial or partner project](./upgrade-overview-2012.md#sign-up-for-a-lifecycle-services-trial-or-partner-project)

1. For each AX 2012 release, please update to the latest available cumulative update before upgrading to the latest Finance and Operations application release.

1. Install the pre-upgrade checklist, more details can be found [here](./prepare-data-upgrade.md#installation)

1. Go through the data upgrade preparation steps. You can skip the **Setup User Mapping** step. This is only relevant for cloud hosted upgrades.   

1. Take a backup of your database (i.e. MicrosoftDynamicsAX). For more information, see [Create a Full Database Backup](https://docs.microsoft.com/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server?view=sql-server-2016)

1.  In Lifecycle Services (LCS), go to the Shared Assets Library (right side of the screen).

1.  Under **Select asset type**, choose **Downloadable VHD**, and download all parts of the VHD package that closely matches the version you will be upgrading to in your on-premises environment. The image requires a high amount of disk space, so be sure to download and extract on a drive with adequate free space. 

1.  The files that you downloaded are a self-extracting zip file. Extract the VHD to a location with a good amount of free space.

1.  Using Hyper-V, launch a virtual machine (VM) and attach the VHD. (Note that the machine must be Generation 1.)

1.  Connect to the VM. You can find the credentials in [Running the Virtual Machine (VM) locally](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/dev-tools/access-instances#running-the-virtual-machine-vm-locally).

1.  Depending on your planned on-premises target version of 10.0.x and the VHD image you downloaded, you may need to download and apply the required Application and Platform Update from the Shared Asset Library under **Select asset type** and **Software deployable package**. For more information, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

>[!IMPORTANT]
> In any case, ensure that you have applied the latest quality update to your VHD to ensure it contains the latest fixes for carrying out data upgrades. 

1.  If you have any extensions or customizations install them into the VHD now, otherwise the upgrade process will remove any data related to customizations. Check with your independent software vendor (ISV) or value-added reseller (VAR) if you need to prepare your environment before the upgrade.

### Upgrading from within VHD

1.  Restore the backup that you created into the OneBox VM. For more information, see [Restore a Database Backup Using SSMS](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms?view=sql-server-2016).

1.  Optional: If the name of your restored database is not AXDB, using PowerShell with administrator privileges, execute:
    
    ```powershell
    .\Configure-On-Premises-Upgrade.ps1 -DatabaseName '<DB-name>'
    ```
    > [!NOTE] 
    > Substitute <DB-Name> with the appropriate value in your case (for example, AXDB). If you would like to edit more values, refer to  Appendix A.

    The script will run a database connection test to check that the information you provide is valid.

1.  In the VHD, go to C:\\AOSService\\PackagesLocalDirectory\\Bin\\CustomDeployablePackage and copy the MajorVersionDataUpgrade zip file.

1.  Paste the file wherever you want and unzip it. For example: c:\\D365FFOUpgrade\\

1.  Open a Command Prompt as Administrator and change the directory to the unzipped folder in the previous step.

1.  Using the Command Prompt from the previous step, execute the following commands:

    a.  `AxUpdateInstaller.exe generate -runbookid=upgrade -runbookfile=upgrade.xml -topologyfile=defaulttopologydata.xml -servicemodelfile=defaultservicemodeldata.xml`

    b.  `AxUpdateInstaller.exe import -runbookfile=upgrade.xml`

    c.  `AxUpdateInstaller.exe execute -runbookid=upgrade`

1.  When the upgrade process has finished successfully, back up the newly upgraded database. If you have customizations from ISVs or VARs, check if you have to run some post data upgrade scripts.

1. Restore the database into your on-premises environment's SQL Server, with a different name from the production one (for example, AXDBupgraded).

1. Deploy a new D365 for Finance and Operations On-premise environment.

    1. If you have customizations:

        1.  In LCS, go to the Shared Assets Library.

        1.  Under **Select asset type**, choose **Model** and download: Dynamics 365 for Finance and Operations on-premises, Version 10.0.x Demo Data. Select the version closest to the 10.0.x environment that you will deploy as the on-premises baseline.

        1.  Use this file to create a new database (typically AXDB) using the restore backup option from SQL server. For more information, see [Restore a Database Backup Using SSMS](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms?view=sql-server-2017).
        
        1.  The database will need to be configured. Follow the steps in [Configure the Finance and Operations database](../deployment/setup-deploy-on-premises-pu12.md#configure-the-finance-and-operations-database).

        1.  In LCS, set up a new environment and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md). When you deploy, the name of the database that you specify should be the one created in the step above (typically AXDB).

        1.  Apply your own customizations as well as ISV/VAR modules, to your newly created 10.0.x environment. Otherwise, when the environment initially syncs with the database it will delete any customization or extensions related data.

        1.  Shut-down on-premises AOS, BI, and MR servers, or stop the services from the Service Fabric portal (Deactivate (Restart)).

        1.  Rename or delete the demo database (typically AXDB) used in the deploy and then rename your new database (typically AXDBupgraded) to the name that the demo database had (typically AXDB).

        1.  Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal (Activate).

        > [!NOTE]
        > The Database synchronization process will be triggered when the AOS nodes startup and your environment will be unavailable until the process is finished.

    1. If you didn't have customizations:

        a.  (Optional) Rename your old database (typically AXDBold) and then rename your new database (typically AXDB). Make sure that in the next step you input the name of the upgraded DB.

        b.  In LCS, set up a new environment and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md).

### Upgrading with VHD pointing to your database

1.  Back up your database from your on-premises environment (typically AXDB). For more information, see [Create a Full Database Backup (SQL Server)](https://docs.microsoft.com/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server?view=sql-server-2016).

1.  Restore the backup that you just created into the database server and give it a different name (AXDBtoupgrade). For more information, see [Restore a Database Backup Using SSMS](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms?view=sql-server-2016).

1.  Open a new PowerShell as Administrator and execute:
    
    ```powershell
    .\Configure-On-Premises-Upgrade.ps1 -DatabaseName '<DB-name>' -DatabaseServer '<SqlServerName>' -DatabaseUser '<User>' -DatabasePassword '<Password>'
    ```

    > [!NOTE]
    > Substitute \<\*\> with the values you require.

    > [!NOTE]
    > - Only SQL Server authentication is officially supported for this upgrade. For more information, see [Create a Database User](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/create-a-database-user?view=sql-server-2016).
    >
    > - You will need to add the Certificate Authority certificate that signed your SQL Server certificate to the OneBox trusted certificate authorities. For more information, see [Installing the trusted root certificate](https://docs.microsoft.com/skype-sdk/sdn/articles/installing-the-trusted-root-certificate).
    >
    > - Make sure the database user you use has the sysadmin server role assigned or at least All Privileges on the database you want to upgrade and has permissions to access tempDB. Step 6 of the upgrade process will fail if this is not true.
    >
    > - When you install the Certificate Authority in the OneBox, make sure you use the FQDN or IP for connecting to the database that appears there. If you can't access it by using the domain name because it doesn't point to that server, edit your hosts file and add the FQDN and the IP it should resolve to.

1.  In the VHD, go to C:\\AOSService\\PackagesLocalDirectory\\Bin\\CustomDeployablePackage and copy the MajorVersionDataUpgrade zip file.

1.  Paste the file wherever you want and unzip it. For example: c:\\D365FFOUpgrade\\

1.  Open a Command Prompt as Administrator and change the directory to the unzipped folder in the previous step.

1.  Using the Command Prompt from the previous step, execute the following commands:

    a.  `AxUpdateInstaller.exe generate -runbookid=upgrade -runbookfile=upgrade.xml -topologyfile=defaulttopologydata.xml -servicemodelfile=defaultservicemodeldata.xml`

    b.  `AxUpdateInstaller.exe import -runbookfile=upgrade.xml`

    c.  `AxUpdateInstaller.exe execute -runbookid=upgrade`

1.  If you have customizations from ISVs or VARs, verify if you have to run some post data upgrade scripts.

1. Deploy a new D365 for Finance and Operations On-premise environment.

    1. If you have customizations:

        1.  In LCS, go to the Shared Assets Library.

        1.  Under **Select asset type**, choose **Model** and download: Dynamics 365 for Finance and Operations on-premises, Version 10.0.x Demo Data. Select the version closest to the 10.0.x environment that you will deploy as the on-premises baseline.

        1.  Use this file to create a new database (typically AXDB) using the restore backup option from SQL server. For more information, see [Restore a Database Backup Using SSMS](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms?view=sql-server-2016).

        1.  The database will need to be configured. Follow the steps under [Configure the Finance + Operations database](../deployment/setup-deploy-on-premises-pu12.md#configure-the-finance--operations-database).

        1.  In LCS, set up a new environment and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md). When you deploy, the database that you should specify should be the one you configured in the step above (typically AXDB).

        1.  Apply your own customizations as well as ISV/VAR modules, to your newly created 10.0.x environment. Otherwise when the environment initially syncs with the database it will delete any customization or extensions related data.

        1.  Shut-down on-premises AOS, BI, and MR servers, or stop the services from the Service Fabric portal.

        1.  Rename or delete the demo database (typically AXDB) used in the deploy and then rename your new database (typically AXDBupgraded) to the name the demo database had (typically AXDB).

        1.  Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal.

        > [!NOTE]
        > The Database synchronization process will be triggered when the AOS nodes startup and your environment will be unavailable until the process is finished.

1. If you don't have customizations:

    a.  (Optional) Rename your old database (typically AXDBold) and then rename your new database (typically AXDB). Make sure that in the next step you input the name of the upgraded database.

    b.  Set up a new environment and deploy it with version 10.0.x. For more information, see [Set up and deploy on-premises environments (Platform update 12 and later)](../deployment/setup-deploy-on-premises-pu12.md).

### Configuring existing users

If you followed either of the procedures above, you will be able to login with the Administrator user you specified in LCS. The rest of your users however will not be able to login as they haven't been configured for the new system. Execute a Select statement against your USERINFO table and take note of the value in the NETWORKDOMAIN fied for the Admin user. Set the NETWORKDOMAIN field of all interactive users for which you want to enable logging in to the same value that the Admin user has (i.e. https://adfs.contoso.com/adfs or http://adfs.contoso.com/adfs/services/trust). The NETWORKALIAS column will also need to be modified. In Dynamics 365 for Finance and Operation we require that this field be set to the users email address (i.e. testuser@contoso.com). 

## Appendix A

### Configure-On-Premises-Upgrade.ps1 usage

> [!Important]
> This script is only meant to be run from a OneBox VHD environment.
>
> The script requires that you pass at least the DatabaseName parameter. If you don't pass it, the script will automatically request it.

If you want to pass an additional parameter like DatabaseServer, or DatabaseUser you can do so but this will cause the script to ask you for all additional parameters. This happens because the script will assume that you want to point the database connection to a machine outside the VM and those parameters will be required to correctly establish the connection.

The parameters that can be passed to the script are:

-   **-DatabaseName** - Database name that you want to upgrade.

-   **-DatabaseServer** - Database server containing Finance and Operations (on-premises) database.

-   **-DatabaseUser** - Username for SQL Authentication.

-   **-DatabasePassword** - Password for SQL Authentication.

After configuration has been passed, the script will execute a database connection test with the new parameters. If the script is unable to connect we recommend that you use Microsoft SQL Server Management Studio or some other tool to debug the connection from there.

**Configure-On-Premises-Upgrade.ps1**

```powershell
<#
.Synopsis
   Configures a OnebBox deployment to upgrade an OnPrem 7.x database to OnPrem 10.0.x 

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

-   Wrong database name or user doesn't have access to that database:
    Exception calling \"Open\" with \"0\" argument(s): \"Cannot open
    database \"AxDB1\" requested by the login. The login failed. Login
    failed for user \'axdbadmin\'.\"

-   Could not establish a connection. Check ip/fqdn and ports: Exception
    calling \"Open\" with \"0\" argument(s): \"A network-related or
    instance-specific error occurred while establishing a connection to
    SQL Server. The server was not found or was not accessible. Verify
    that the instance name is correct and that SQL Server is configured
    to allow remote connections. (provider: Named Pipes Provider, error:
    40 - Could not open a connection to SQL Server)\"

-   Login credentials are not correct. Exception calling \"Open\" with
    \"0\" argument(s): \"Login failed for user \'axdbadmin\'.\"
