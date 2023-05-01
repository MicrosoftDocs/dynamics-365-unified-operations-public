---
# required metadata

title: In-place upgrade process for on-premises environments
description: This article provides the detailed process for upgrading on-premises environments from versions 7.x to 10.0.x.  
author: laneswenka
ms.date: 01/14/2021
ms.topic: article
ms.prod: dynamics-365
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: laswenka
ms.search.validFrom: 2018-10-31 
ms.dyn365.ops.version: 10.0.x
search.app:
  - financeandoperationsonprem-docs
---

# In-place upgrade process for on-premises environments

[!include [banner](../includes/banner.md)]

This article provides the detailed process for upgrading on-premises environments of Finance + Operations (on-premises) from version 7.x to 10.0.x.  

> [!NOTE]
> Please perform the upgrade with your sandbox environment before upgrading your production environment.

## On-premises upgrade from version 7.x to 10.0.x

> [!NOTE]
> Be aware that this upgrade process takes time to complete and Finance + Operations will be inaccessible for the entire duration of the data upgrade.

To upgrade from version 7.x to 10.0.x, there are two possible paths that are currently supported.

An overview of each path is given below:

-   **Upgrading from within VHD** - This path involves copying your database into the virtual hard disk (VHD) and executing the upgrade inside it. Overall, this is the simpler method.

-   **Upgrading with VHD pointing to your database** - This path involves pointing the VHD upgrade process to your database. The upgrade process is still executed from within the VHD.

> [!NOTE]
> The VHD does not need external network access in order to carry out the upgrade process.

### Prerequisites

1.  In Lifecycle Services (LCS), go to the Shared Assets Library (right side of the screen).

2.  Under **Select asset type**, choose **Downloadable VHD**, and download all parts of the VHD package that closely matches the version you will be upgrading to in your on-premises environment. The image requires a high amount of disk space, so be sure to download and extract on a drive with adequate free space. 

3.  The files that you downloaded are a self-extracting zip file. Extract the VHD to a location with a good amount of free space.

4.  Using Hyper-V, launch a virtual machine (VM) and attach the VHD. (Note that the machine must be Generation 1.)

5.  Connect to the VM. You can find the credentials in [Running the Virtual Machine (VM) locally](../dev-tools/access-instances.md#running-the-virtual-machine-locally).

6.  Depending on your planned on-premises target version of 10.0.x and the VHD image you downloaded, you may need to download and apply the required Application and Platform Update from the Shared Asset Library under **Select asset type** and **Software deployable package**. For more information, see [Install deployable packages from the command line](../deployment/install-deployable-package.md).

7.  If you have any extensions or customizations install them into the VHD now, otherwise the upgrade process will remove any data related to customizations. Check with your independent software vendor (ISV) or value-added reseller (VAR) if you need to prepare your environment before the upgrade.

### Upgrading from within VHD

1.  Shut-down on-premises AOS, BI, and MR servers or stop the Service Fabric Host Service in each of the nodes and set to disabled.

2.  Back up your database from your on-premises environment (typically AXDB). For more information, see [Create a Full Database Backup](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server).

3.  In the VHD, go to C:\\AOSService\\PackagesLocalDirectory\\Bin\\CustomDeployablePackage and copy the MinorVersionDataUpgrade zip file.

4.  Paste the file wherever you want and unzip it. For example: c:\\D365FFOUpgrade\\

5.  Open a Command Prompt as Administrator and change the directory to the unzipped folder in step 4.

6.  Restore the backup that you created into the OneBox VM. For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).

7.  Optional: If the name of your restored database is not AXDB, using PowerShell with administrator privileges, execute:
    
    ```powershell
    .\Configure-On-Premises-Upgrade.ps1 -DatabaseName '<DB-name>'
    ```
    > [!NOTE] 
    > Substitute `<DB-Name>` with the appropriate value in your case (for example, AXDB). If you would like to edit more values, refer to the appendix of this article.

    The script will run a database connection test to check that the information you provide is valid.

8.  Using the Command Prompt from step 5, execute the following commands:

    a.  `AxUpdateInstaller.exe generate -runbookid=upgrade -runbookfile=upgrade.xml -topologyfile=defaulttopologydata.xml -servicemodelfile=defaultservicemodeldata.xml`

    b.  `AxUpdateInstaller.exe import -runbookfile=upgrade.xml`

    c.  `AxUpdateInstaller.exe execute -runbookid=upgrade`

    During the execution of cleanup for data upgrade you may encounter an error: 
    
    `Stack trace: Call to TTSCOMMIT without first calling TTSBEGIN.\' on category \'Error\'.`
    
    To resolve this, re-run the step with this command: 
    
    `AxUpdateInstaller.exe execute -runbookid=upgrade -rerunstep=\<failed-step\>`

9.  When the upgrade process has finished successfully, back up the newly upgraded database. If you have customizations from ISVs or VARs, check if you have to run some post data upgrade scripts.

10. Restore the database into your environment with a different name from the production one (for example, AXDBupgraded).

11. Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal.

12. In LCS, open the project, and then, in the **Environments** section, delete the deployment. The applications should start to disappear from Service Fabric Explorer in the environment. This process may take longer depending on the number of nodes that you have. Check the service fabric explorer to verify that all applications have been deleted before deploying a new environment. Note that LCS might indicate that the environment is deleted before the actual process is finished.

13. If you had customizations:

    a.  In LCS, go to the Shared Assets Library.

    b.  Under **Select asset type**, choose **Model** and download: Dynamics 365 Finance + Operations (on-premises), Version 10.0.x Demo Data. Select the version closest to the 10.0.x environment that you will deploy as the on-premises baseline.

    c.  Use this file to create a new database (typically AXDB) using the restore backup option from SQL server. For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).
     
    d.  The database will need to be configured. Follow the steps in [Configure the Finance + Operations (on-premises) database](../deployment/setup-deploy-on-premises-latest.md#configure-the-finance--operations-on-premises-database).

    e.  In LCS, set up a new environment and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments](../deployment/setup-deploy-on-premises-latest.md). When you deploy, the database that you specify should be the one created in step 13c (typically AXDB).

    f.  Apply your own customizations as well as ISV/VAR modules, to your newly created 10.0.x environment. Otherwise, when the environment initially syncs with the database it will delete any customization or extensions related data.

    g.  Shut-down on-premises AOS, BI, and MR servers, or stop the services from the Service Fabric portal.

    h.  Rename or delete the demo database (typically AXDB) used in the deploy and then rename your new database (typically AXDBupgraded) to the name that the demo database had (typically AXDB).

    i.  Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal.

14. If you didn't have customizations:

    a.  (Optional) Rename your old database (typically AXDBold) and then rename your new database (typically AXDB). Make sure that in the next step you input the name of the upgraded DB.

    b.  In LCS, set up a new environment and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments](../deployment/setup-deploy-on-premises-latest.md).

15. (Optional) If deployment fails because the financial reporting module failed, on the database that you are using for the new environment (typically AXDB), run the following command:

    ```sql
    ALTER TABLE RETAILTERMINALTABLE ADD CONSTRAINT PK_RecId PRIMARY KEY
    CLUSTERED (RECID)
    ```

### Upgrading with VHD pointing to your database

1.  Shut-down on-premises AOS, BI, and MR servers, or stop the services from the Service Fabric portal.

2.  Back up your database from your on-premises environment (typically AXDB). For more information, see [Create a Full Database Backup (SQL Server)](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server).

3.  Restore the backup that you just created into the database server and give it a different name (AXDBtoupgrade). For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).

4.  Once connected, go to C:\\AOSService\\PackagesLocalDirectory\\Bin\\CustomDeployablePackage and copy the MinorVersionDataUpgrade zip file.

5.  Paste the file wherever you want and unzip it. For example: C:\\D365FFOUpgrade\\

6.  Open a Command Prompt as Administrator and change the directory to the unzipped folder from step 5.

7.  Open a new PowerShell as Administrator and execute:
    
    ```powershell
    .\Configure-On-Premises-Upgrade.ps1 -DatabaseName '<DB-name>' -DatabaseServer '<SqlServerName>' -DatabaseUser '<User>' -DatabasePassword '<Password>'
    ```

    > [!NOTE]
    > Substitute \<\*\> with the values you require.

    > [!NOTE]
    > - Only SQL Server authentication is officially supported for this upgrade. For more information, see [Create a Database User](/sql/relational-databases/security/authentication-access/create-a-database-user).
    >
    > - You will need to add the Certificate Authority certificate that signed your SQL Server certificate to the OneBox trusted certificate
    authorities. For more information, see [Installing the trusted root certificate](/skype-sdk/sdn/articles/installing-the-trusted-root-certificate).
    >
    > - Make sure the database user you use has the sysadmin server role assigned or at least All Privileges on the database you want to upgrade and has permissions to access tempDB. Step 6 of the upgrade process will fail if this is not true.
    >
    > - When you install the Certificate Authority in the OneBox, make sure you use the FQDN or IP for connecting to the database that appears there. If you can't access it by using the domain name because it doesn't point to that server, edit your hosts file and add the DN and the IP it should resolve to.

8.  Using the Command Prompt from step 6, execute the following
    commands:

    a.  `AxUpdateInstaller.exe generate -runbookid=upgrade -runbookfile=upgrade.xml -topologyfile=defaulttopologydata.xml -servicemodelfile=defaultservicemodeldata.xml`

    b.  `AxUpdateInstaller.exe import -runbookfile=upgrade.xml`

    c.  `AxUpdateInstaller.exe execute -runbookid=upgrade`

    During the execution of Cleanup for data upgrade you may encounter an error: `Stack trace: Call to TTSCOMMIT without first calling TTSBEGIN.\' on category \'Error\'.`

    To resolve this, re-run the step with this command: `AxUpdateInstaller.exe execute -runbookid=upgrade -rerunstep=\<failed-step\>`

9.  If you have customizations from ISVs or VARs, verify if you have to run some post data upgrade scripts.

10. Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal.

11. In LCS, open the project, and then, in the **Environments** section, delete the deployment. The applications should start to disappear from Service Fabric Explorer in the environment. This process may take longer depending on the number of nodes you have.

12. If you had customizations:

    a.  In LCS, go to the Shared Assets Library.

    b.  Under **Select asset type**, choose **Model** and download: Dynamics 365 Finance + Operations (on-premises), Version 10.0.x Demo Data. Select the version closest to the 10.0.x environment that you will deploy as the on-premises baseline.

    c.  Use this file to create a new database (typically AXDB) using the restore backup option from SQL server. For more information, see [Restore a Database Backup Using SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms).

    d.  The database will need to be configured. Follow the steps under [Configure the Finance + Operations (on-premises) database](../deployment/setup-deploy-on-premises-latest.md#configure-the-finance--operations-on-premises-database).

    e.  In LCS, set up a new environment and deploy it with version 10.0.x (Redeploy). For more information, see [Set up and deploy on-premises environments](../deployment/setup-deploy-on-premises-latest.md). When you deploy, the database that you should specify should be the one created in step 12c (typically AXDB).

    f.  Apply your own customizations as well as ISV/VAR modules, to your newly created 10.0.x environment. Otherwise when the environment initially syncs with the database it will delete any customization or extensions related data.

    g.  Shut-down on-premises AOS, BI, and MR servers, or stop the services from the Service Fabric portal.

    h.  Rename or delete the demo database (typically AXDB) used in the deploy and then rename your new database (typically AXDBupgraded) to the name the demo database had (typically AXDB).

    i.  Start on-premises AOS, BI, and MR servers, or start the services from the Service Fabric portal.

13. If you didn't have customizations:

    a.  (Optional) Rename your old database (typically AXDBold) and then rename your new database (typically AXDB). Make sure that in the next step you input the name of the upgraded database.

    b.  Set up a new environment and deploy it with version 10.0.x. For more information, see [Set up and deploy on-premises environments](../deployment/setup-deploy-on-premises-latest.md).

14. (Optional) If deployment fails because the financial reporting module failed, on the database that you are using for the new environment (typically AXDB), run the following command:

    ```sql
    ALTER TABLE RETAILTERMINALTABLE ADD CONSTRAINT PK_RecId PRIMARY KEY
    CLUSTERED (RECID)
    ```

## Appendix

### Configure-On-Premises-Upgrade.ps1 usage

> [!Important]
> This script is only meant to be run from a OneBox VHD environment.
>
> The script requires that you pass at least the DatabaseName parameter. If you don't pass it, the script will automatically request it.

If you want to pass an additional parameter like DatabaseServer, or DatabaseUser you can do so but this will cause the script to ask you for all additional parameters. This happens because the script will assume that you want to point the database connection to a machine outside the VM and those parameters will be required to correctly establish the connection.

The parameters that can be passed to the script are:

-   **-DatabaseName** - Database name that you want to upgrade.

-   **-DatabaseServer** - Database server containing Finance + Operations (on-premises) database.

-   **-DatabaseUser** - Username for SQL Authentication.

-   **-DatabasePassword** - Password for SQL Authentication.

After configuration has been passed, the script will execute a database connection test with the new parameters. If the script is unable to connect we recommend that you use Microsoft SQL Server Management Studio or some other tool to debug the connection from there.

**Configure-On-Premises-Upgrade.ps1**

```powershell
<#
.Synopsis
   Configures a Onebox deployment to upgrade an OnPrem 7.x database to OnPrem 10.0.x 

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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

