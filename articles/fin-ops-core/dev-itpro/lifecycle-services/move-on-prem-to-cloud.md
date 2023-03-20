---
# required metadata

title: Move Lifecycle Services implementation projects from on-premises to the cloud
description: This article explains how to move your Microsoft Dynamics 365 Finance + Operations (on-premises) environments to the cloud.
author: ttreen
ms.date: 03/20/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: marwalke
ms.search.validFrom: 2020-09-30 
ms.dyn365.ops.version: 10.0.13
---

# Move Lifecycle Services implementation projects from on-premises to the cloud

[!include [banner](../includes/banner.md)]

This article explains how to move your Microsoft Dynamics 365 Finance + Operations (on-premises) environments that are hosted on your own infrastructure to the Azure cloud.

## Background

Previous migrations to the cloud used SQLPackage to create and restore a .bacpac file to move the on-premises database into the cloud. That approach is no longer supported. The current approach uses the Data Migration Toolkit version 1.0.8 (or later). 

## Cloud subscription licenses

If you don't already have cloud subscription licenses, work with your cloud service provider or volume license reseller to get and activate the required subscriptions on your Azure Active Directory (Azure AD) tenant. All subscriptions for users and add-on environments must be activated.

## Configure Lifecycle Services cloud implementation project

If no finance and operations cloud-named user subscription licenses have previously been activated on the Azure AD tenant, a new Microsoft Dynamics Lifecycle Services cloud implementation project is automatically provisioned. Otherwise, you must open a support request to have a Lifecycle Services cloud implementation project created. For more information, see [Multiple LCS projects and production environments on one Azure AD tenant](../../fin-ops/get-started/implement-multiple-projects-aad-tenant.md).

After your Lifecycle Services cloud implementation project has been created, you must fully configure it. As part of this configuration, you must complete the following steps (and others):

- Add users.
- Add an Azure DevOps association.
- Add subscription estimates.
- Fill in the Asset library.
- Add Business process modeler (BPM).

## Complete development and testing of updated integrations

You will have to make some changes to the integration design patterns that you used for interfaces with your Finance + Operations (on-premises) environment. These changes can be substantial, and a detailed discussion of them is beyond the scope of this article. Nevertheless, you must evaluate all your interfaces and make the appropriate changes to them.

You should consider developing your updated interfaces in such a way that they can coexist in the same code base as the original interfaces. This approach will simplify management of the code lifecycle during the period of your transition from on-premises to cloud. If this approach isn't possible, you must manage a new development branch through your cloud go-live. To simplify management of this new branch during the transition period, we recommend that you freeze other code changes as much as you can. Additionally, in your detailed cut-over plan, you should carefully document the steps for inactivating your old interfaces and activating the new interfaces.

## Prerequisites

1. Deploy a Tier-2 sandbox (UAT) self-service environment.
2. Apply the same code package that is applied in your on-premises production environment (or, as appropriate, in the current build from the cloud integration development branch that was discussed in the previous section). This code package should be a single, complete deployable package that includes any independent software vendor (ISV) solutions and licenses.

    > [!NOTE]
    > - The local business data (LBD) migration process is for finance and operations sandbox (UAT) self-service environments only. It can never be run against a production environment. A gold copy refresh is done to move the migrated data into production. 
    > - Make sure that you download the latest version of the Data Migration Toolkit for Dynamics 365 from Lifecycle Services.
    > - Don't deploy or use the linked Power Platform environment for the migration. The Power Platform environment can be deployed and used after the data upgrade is completed.

3. Download the Data Migration Toolkit for Dynamics 365 version 1.0.8 (or later) from Lifecycle Services. In the Shared asset library, select **Model** as the asset type, and then select the model file.
4. Download and install the [.NET Framework version 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471) if it isn't already installed.
5. Make sure that the replication feature is installed and enabled for the source SQL Server instance. To determine whether replication is enabled, run the following SQL script.

    ```sql
    -- If @installed is 0, replication must be added to the SQL Server installation.
    USE master;
    GO
    DECLARE @installed int;
    EXEC @installed = sys.sp_MS_replication_installed;
    SELECT @installed;
    ```

    If the replication components aren't installed, follow the steps in [Install SQL Server replication](/sql/database-engine/install-windows/install-sql-server-replication) to install them.

6. SQL Server authentication must be set to **SQL Server and Windows Authentication mode**. (This change requires a restart of the SQL Server service.) The toolkit uses native SQL logins only.
7. Enable and start the SQL Server Agent on the source database server.

    > [!NOTE]
    > A user should have the **DB\_Owner** privilege in the source database, and should have access to the master database and the source database.

## Data Migration Toolkit setup

1. Extract the zip file for the Data Migration Toolkit for Dynamics 365 version 1.0.x that you downloaded from Lifecycle Services into a folder of your choice. 

    > [!NOTE]
    > To ensure that the zip file is correctly extracted, select and hold (or right-click) the download, and then clear the **Unblock** checkbox. 

2. In the folder where you extracted the zip file, open the **DataMigrationTool.exe.config** file, and follow these steps:

    1. Find the following line:

        ```xml
        <add key="isD365OnPrem" value="false" />
        ```

    2. Change the value from **false** to **true**, as in the example below:

        ```xml
        <add key="isD365OnPrem" value="true" />
        ```

3. Optional: If you don't want some of the source database tables to be replicated in the target database, you can specify them in the **IgnoreTables.xml** file. Likewise, if you don't want some of the functions to be replicated, you can specify them in the **IgnoreFunctions.xml** file. Additionally, if you want to put specific tables in publications outside the main publications, you can use the **SpecialTables.xml** file.

    - **Path of the IgnoreTables.xml file:** Data\\IgnoreTables.xml
    - **Path of the IgnoreFunctions.xml file:** Data\\IgnoreFunctions.xml
    - **Path of the SpecialTables.xml file:** Data\\SpecialTables.xml

    The following examples show how to specify tables and functions in the XML files.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <IgnoreTables>
        <Name>
            <Table>NON_AOT_TABLE1</Table>
            <Table>NON_AOT_TABLE2</Table>
            <Table>NON_AOT_TABLE3</Table>
        </Name>
    </IgnoreTables>
    ```

    > [!NOTE]
    > The tables that you add to the ignore list shouldn't exist in the Dynamics 365 Application Object Tree (AOT). If tables that exist in the AOT are included, an error will occur during the data upgrade. These tables won't be replicated to the target database.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <IgnoreFunctions>
        <Name>
            <Function>if_WHSInventReserveUnionDelta</Function>
        </Name>
    </IgnoreFunctions>
    ```

    > [!IMPORTANT]
    > The functions that are specified in the IgnoreFunctions.xml file won't be replicated to the target database.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <SpecialTables>
        <Name>
            <Table></Table>
        </Name>
    </SpecialTables>
    ```

    > [!IMPORTANT]
    > Tables that are specified in the SpecialTables.xml file will be added to a dedicated publisher. The number of special table publishers is based on the **NumberOfPublishers** parameter. For more information, see the next step. Special table handling can be useful for very large tables that you might have to manually start the replication on during downtime hours.

4. Optional: To optimize the replication latency/performance, you can update the following distributor parameters in the **App.config** file:

    - **MaxBcpThreads** – By default, this parameter is set to **6**. If the machine has fewer than six cores, update the value to the number of cores. The maximum value that you can specify is **8**.
    - **NumberOfPublishers** – By default, this parameter is set to **2**. We recommend that you use this value. However, there might be situations where you want to increase the number of publishers, so that you can distribute fewer tables to each publisher. When it's used in conjunction with the manual snapshot start process, an increase in the number of publishers lets you run smaller initial snapshots. This approach can be useful if you have limited maintenance windows and must split the startup of the replication over several publishers.
    - **snapshotPostPublication** – This option will add a five-minute delay between starts of the automatic snapshot processes. This delay can help with loads on the source server. The toolkit also allows for manual snapshot starts. If you use that approach, you don't have to set this parameter. 

    > [!NOTE]
    > Don't set up or configure replication during peak times when system resource usage, memory usage, and disk IO operations are high. 
    >
    > When resources are being used to the maximum extent (that is, more than 90 percent is already consumed), the replication might be delayed as the system tries to find available resources. We recommend that you start the replication during off hours, when the system resources are at minimum usage (that is, during off-peak time). 
    >
    > For a go-live cutover, we recommend that you start the replication the previous weekend. 

## Migration process

### Run the DataMigrationTool.exe application

> [!IMPORTANT]
> Before you begin the migration process, ensure that the environment is in a **Deployed** state.

1. Run the **DataMigrationTool.exe** application.

    A console window will appear, where you can provide the cloud environment type.

    - **Public:** lcs.dynamics.com
    - **GCC:** gov.lcs.microsoftdynamics.us 
    - **UAE:** \[ uae.lcs.dynamics.com \] 

2. After you enter the cloud environment, you're prompted to sign in. Provide the credentials that are used to sign in to Lifecycle Services.
3. After you're successfully authenticated, in the console window, provide the **Project-Id** value and then the **Environment-Id** value.

    To validate the given values, you must sign in by using the credentials that are used to sign in to Lifecycle Services.

    > [!NOTE]
    > You can find the **Project-Id** and **Environment-Id** values on the **Manage environment** page in Lifecycle Services. You can also find the **Environment-Id** value on the **Environment details** page.

### Complete the data replication and migration

After the validation is successful, the application presents a set of menu options that correspond to the steps in the data upgrade process. To complete the data replication and upgrade, you should perform the steps in the following order.

1. **Environment preparation: Environment setup activity**

    This step prompts you for the following information:

    - Details of the source database:

        - Source server (in the format *servername\\serverinstance*)
        - Source database name
        - User name
        - Password

    - IP address of the source database server (for the allowlist)
    - Distribution database path (for example, **D:\\SQLServer\\Data**)
    - Replication snapshot path (for example, **D:\\SQLServer\\Snapshot**)

    > [!IMPORTANT]
    > You must use SQL Server authentication. You can't use a domain sign-in.
    > 
    > The specified distribution database and replication snapshot paths should have enough space. We recommend that the amount of space be at least the size of the source database. If you've used compression in your Dynamics 365 database, more space will be required, because the snapshot is uncompressed. The paths should be on the local disk of the machine. (Avoid using shared paths.)
    > 
    > We recommend that you have a static IP address for the virtual machine (VM) or machine (for the allowlist in step 1). In this way, you help prevent connection issues with the target database.

    This step performs the following actions:

    - It validates the connection to the source database.
    - It validates the version of the Dynamics 365 LBD database.
    - It authorizes the source IP address.
    - It validates the target databases.

2. **Environment preparation: Prepare the target environment for the data upgrade**

    This step changes the state of the Lifecycle Services environment from **Deployed** to **Ready for replication**.

3. **Replication: Cleanup Target Database**

    This step performs the following actions:

    1. It changes the state of the Lifecycle Services environment from **Ready for replication** to **Replication in progress**.
    2. It deletes all Dynamics AX product tables, views, stored procedures, and user-defined functions in the target database.

4. **Replication: Setup Distributor**

    This step creates a distribution database under the **System Databases** folder on the source server. This distribution database is used for replication.

5. **Replication: Setup Publication for Primary Key (PK) Tables**

    This step creates publications for primary key tables under the **Replication** folder on the source server and replicates them in the target database. If any **ignore-table** entries were specified, the specified tables are exempted from replication. If any **special-table** entries were added, they will be added to additional special tables publications. 
    
    You will receive the following prompt: "Do you want the snapshot to start automatically? Continue by giving Y (Yes) for Automatic, else N (No) for manual (If No you have to manually start the snapshots from replication monitor)." If you select **Yes**, the snapshot replication will be started automatically. If you select **No**, you will have to open SQL Server Management Studio (SSMS), open the replication monitor, and manually start each snapshot. The advantage of manually starting snapshots is that you can control the load on the source SQL Server instance. This approach can be useful if you have limited low-usage periods or maintenance windows to start the replication. Additionally, it lets you split up when you start the snapshot process. 

    **Created publishers:** AX\_PUB\_PkTable\_\[\*\]

    > [!NOTE]
    > After this replication configuration step is completed, actual data replication will occur as a SQL job that runs in the background. This job will take some time to be completed. You can view the status of the replication by providing the **'rs'** option. To learn more about the **'rs'** option, see the [Reporting section of the application](#reporting-section-of-the-application) section later in this article.

6. **Replication: Setup Publication for Other Objects (functions)**

    This step creates a publication for other objects (functions) and replicates them in the target database. If you don't want some of the functions to be replicated, you can specify them in the IgnoreFunctions.xml file.

    **Created publisher:** AX\_PUB\_OtherObjects

    > [!IMPORTANT]
    > Don't move on to the next step until the **DataReplicationStatus** property for this step is shown as completed.

    > [!NOTE]
    > The replication will take some time to be completed. You can view the replication status by providing the **'rs'** option.
    >
    > If there are no functions to replicate, the publication won't be created.

7. **Cutover: Set up publication for non-primary key tables**

    This step creates two publications: 

    - One publication is used to replicate non-primary key tables.
    - One publication is used to replicate locked tables.

    As in step 5, you will be prompted to specify whether you want the snapshot to be started automatically or manually. 
    
    > [!NOTE]
    > If there are no locked tables, the publication won't be created.

    **Publication names:** AX\_PUB\_NoPKTable, AX\_PUB\_TABLE\_LockedTable

    If the AX service acquires a schema lock during the creation of the primary key publication, those tables will be ignored and omitted from the publication. They will be added to temporary tables and marked for replication during the creation of the cutover publication.

    > [IMPORTANT]
    > Don't move on to next step until the **DataReplicationStatus** property for this step is shown as completed.

    > [!NOTE]
    > You can validate the replicated data by using the **'dv'** option. If there are mismatched tables, this step lets you create publications for them. If you want to exclude any mismatched tables for replication, close the app, and add those tables in the **Data/IgnoreTables.xml** field. Then rerun the app, and use the **'dv'** option. To learn more about the **'dv'** option, see the [Reporting section of the application](#reporting-section-of-the-application) section later in this article.
 
8. **Cutover: Remove replication setup**

    This step deletes all the publications that were created in the source database, the distribution database, and the replication snapshot.

    > [!NOTE]
    > To remove the **Snapshot** folder without causing an exception, run the following script in the source database. Even if you don't run this script, you can ignore the exception message that you receive.
    >
    > ```sql
    > EXEC master.dbo.sp_configure 'show advanced options', 1
    > RECONFIGURE WITH OVERRIDE
    > EXEC master.dbo.sp_configure 'xp_cmdshell', 1
    > RECONFIGURE WITH OVERRIDE
    > ```

9. **Post-replication: Update environment state to Replicated**

    This step changes the state of the Lifecycle Services environment from **Replication in progress** to **Replication completed**.

10. **Data synchronize: Trigger transformation**

    This step triggers a servicing step in Lifecycle Services that will update the database for the cloud. When the action is successful, the state of the Lifecycle Services environment changes from **Replication completed** to **Data upgrade in progress**.

    If data migration is successful, the environment will be set to a **Deployed** status in Lifecycle Services. 

11. **Data synchronize: Trigger rollback**

    This step triggers a rollback of the data upgrade. This action rolls back the data to the point before the transformation was triggered and sets the Lifecycle Services environment state to **Replicated**. These actions will change the environment from **Failed** to the **Replicated** state.

    At this point, you have only triggered the rollback. To view the rollback status, use the **'rbs'** option. To learn more about this option, see the [Reporting section of the application](#reporting-section-of-the-application) section later in this article.

    If rollback is successful, the **'rbs'** option is shown as **D365 upgrade topology(LCS) status: Replicated**.

    If rollback fails, the **'rbs'** option is shown as **D365 upgrade topology(LCS) status: Failed**.

## Reporting section of the application

You can use the following options to review the reports of the replication validation, replication status, data upgrade status, and rollback data upgrade status.

- **dv) Report** – Validate the replication.

    This option compares the number of tables and records in the source server database and the target server database, and then shows the report. You should use this option only after step 7 is completed.
    
    If there are mismatched tables, this step lets you create a publication for them. If you want to exclude any mismatched tables for replication, close the app, and add those tables in the **Data/IgnoreTables.xml** file. Then rerun the app, and use the **'dv'** option.

    You can find the report data at **output/PostValidationInfo.csv**.

- **rs) Report** – Get the replication status.

    This option shows the report of the replication process for the publications that were created. You should use this option only after step 5 is started (during the replication process for any publication).

- **rbs) Report** – Get the rollback status.

    This option shows the report of the rollback process. You should use this option only after step 11 is started.

## Tooling section of the application

- **Reset-rep** – Reset the replication setup by removing all the replication configurations. Publications and the distribution database are deleted. The status of all **Replication** and **Cutover** menu options is reset from **Completed** mode to **Reset** mode to help you redo the replication from the beginning.
- **Reset-all** – Reset all the menu options, and remove the replication configurations. The status of all the options is changed to **Reset**.
- **Clear** – Clear the environment setup activity. All information is cleared from the cache, such as the **project-Id** value, the **Environment-Id** value, and source database details.
- **Help** – Show the data upgrade migration options with the updated status.
- **Exit** – Close the application.
- **Set-failed** – If you want to delete the environment, and if the environment is in the **PreparingForReplication**, **ReadyForReplication**, or **Replicating & Replicated)** state, use this option to set the environment state to **Failed**. The environment can then be deleted from Lifecycle Services.

## Post-migration tasks

1. If necessary, reimport all other users, and assign the appropriate security roles. Users must now be assigned to Azure AD accounts.
2. Direct printing in a cloud environment is done by using the Document routing agent (DRA). Set up sandbox DRAs as described in [Install the Document routing agent to enable network printing](../analytics/install-document-routing-agent.md), so that regression testing can include your printing scenarios.
3. Copy document handling attachments to the cloud. Document handling attachments aren't stored in the database. If they must be preserved, you must move them separately. For more information, see the [Migrate document handling attachments to your sandbox](#migrate-document-handling-attachments-to-your-sandbox) section in this article.
4. Run a complete regression test cycle. This cycle should include testing of integrations.
5. Fix any issues that are discovered during testing. For each issue, document and keep track of the correcting adjustments that you make in the sandbox, and repeat those adjustments in the on-premises source. If any change must **not** be made in the on-premises environment, because it's incompatible with the correct functioning of that environment, we recommend that you create a DMF data package for it instead of manually applying it for each iteration of the migration process.
6. Repeat steps 2 through 10 until all tests have been passed, and no further changes are being made to code or the configuration.

## Repeat the migration to production

Follow all previous steps to migrate data, and then follow the instructions in [Golden configuration promotion - Copy the sandbox database to production](../database/dbmovement-scenario-goldenconfig.md#copy-the-sandbox-database-to-production).

1. Deploy the new production environment. Note that the regular prerequisites apply. For example, you must have an active subscription estimator, complete the LCS methodology phases before the operate phase, and complete the FastTrack readiness review. For more information, see [Prepare for go-live](../../fin-ops/imp-lifecycle/prepare-go-live.md).
2. Apply the final version of the software deployable package to production.
3. Stop making data changes to the on-premises production environment.
4. Repeat steps 3 through 6 in the [Do a trial migration and resolve issues](#prerequisites) section to copy the final/up-to-date on-premises production database to the cloud sandbox.
5. Repeat step 8 in the [Do a trial migration and resolve issues](#prerequisites) section to copy the final/up-to-date document handling attachments to the cloud sandbox.
6. Request a database refresh from sandbox to production. (The process is the same as the process that is used to promote a golden configuration database to production.)
7. Open a support request to have Dynamics Support Engineering copy the document handling attachments from the sandbox storage account to the production storage account and update the references in the production database's DocuValue and DocuDeletedValue tables. After the request has been completed, validate that the attachments are available for a sample of document handling records. 
> [!NOTE]
> The support request for copying the document handling attachments **must be submitted 72 hours in advance** for scheduling. Requests made without advance notice cannot be honored.

8. Set up DRAs for production. If you're reusing any of the DRAs that were previously installed as part of your trial migration, remember to update their configuration so that they connect to the production URL instead of the sandbox URL.
9. Reconcile your cloud and on-premises production environments, as detailed in your cut-over plan.
10. Obtain sign-off for the go-live.
11. Activate cloud production interfaces, batch jobs, and so on.
12. Start to transact in your cloud production environment.


## Migrate document handling attachments to your sandbox

Document handling attachments for Finance + Operations (on-premises) environments are stored in a file share. However, the cloud version doesn't support this file share. You can use the following procedure to copy the attachments to the Azure storage account for your sandbox environment and update the corresponding metadata in the database. For subsequent promotion to production, you can request that Dynamics Support Engineering copy the attachments from your sandbox to production.

1. Upload a copy of the document handling attachment files from the on-premises production file share to a temporary folder on one of the sandbox instances of Application Object Server (AOS). For example, you can upload a zip file of the attachments and unpack it on the target. If you don't have remote desktop access (for example, for a self-service environment), you can use a different virtual machine (VM) instead. For reasonable conversion performance, this VM should be in the same Azure datacenter as the target sandbox. If you aren't using the AOS instance, you must add the VM to an allow list for access to the sandbox's SQL database instance.
2. Open a support request to get the name of the sandbox Azure storage account and a time-limited shared access signature token for the documents container. Update the corresponding placeholders in the Windows PowerShell script that is run in the next step. Also update the placeholders for your temporary folder, and for your finance and operations transactional database, by using the environment details in Lifecycle Services.
3. Run the following Windows PowerShell script on the sandbox AOS instance or other VM to upload the document handling files to the storage account and create the required metadata for each file.

    ```powershell
    #Upload F&O on-prem document handling attachments to Azure storage account
    #
    $filesPath = "<TEMP_ATTACHMENTS_FOLDER_PATH>"
    $dBHostName = "<DATABASE_SERVER>.database.windows.net"
    $dBName = "<DATABASE_NAME>"
    $dBUsername = "<DATABASE_USER>"
    $dBPassword  = "<DATABASE_PASSWORD>"
    $storageAccountName = "<STORAGE_ACCOUNT_NAME>"
    $sasToken = "<SAS_TOKEN>"

    [Reflection.Assembly]::LoadWithPartialName("System.Security.Cryptography") #Load crypto
    $cryptoObj = [System.Security.Cryptography.SHA256]::Create()
    $StorageContext = New-AzStorageContext -StorageAccountName $storageAccountName -SasToken $sasToken
    foreach ($file in Get-ChildItem $filesPath) 
    {
        try
        {
            $blob = (Set-AzStorageBlobContent -Context $StorageContext -Container documents -File $file.FullName -Blob "$($file.Name)" -Force).ICloudBlob
        }
        catch
        {
            Write-Host "Could not upload $($file.Fullname) to blob"
            Write-Host $_
        }
        if($blob)
        {
            #Write-Host "Processing $($file.Fullname)..."
            #FileHash:
            $fileBytes = [System.IO.File]::ReadAllBytes($file.FullName)
            $hashBytes = $cryptoObj.ComputeHash($fileBytes)
            $encodedHash = [System.Convert]::ToBase64String($hashBytes)
            #FullFileName:
            $origFileName = (Invoke-Sqlcmd -Query "SELECT ORIGINALFILENAME FROM DOCUVALUE WHERE FILEID = '$($file.Name)'" -ServerInstance $dBHostName -Database $dBName -Username $dBUsername -Password $dBPassword).ORIGINALFILENAME
            if ($origFileName.Length -eq 0)
            {
                $origFileName = (Invoke-Sqlcmd -Query "SELECT ORIGINALFILENAME FROM DOCUDELETEDVALUE WHERE FILEID = '$($file.Name)'" -ServerInstance $dBHostName -Database $dBName -Username $dBUsername -Password $dBPassword).ORIGINALFILENAME
            }
            if ($origFileName.Length -eq 0)
            {
                Write-Host "Missing DOCUVALUE $($file.Name)"
            }
            else
            {
                $nameBytes  = [System.Text.Encoding]::UTF8.GetBytes($origFileName)
                $encodedName =  [System.Convert]::ToBase64String($nameBytes)
                #Write-Host "Base64 encoded original filename $encodedName."
                $blob.Metadata["FileHash"] = $encodedHash
                $blob.Metadata["FileSize"] = $file.Length
                $blob.Metadata["FullFileName"] = $encodedName
                $blob.SetMetadata()
                Write-Host "Uploaded $($file.Fullname)"
            }
        }
    }
    ```

4. In SSMS, run the following T-SQL commands to update the DocuValue and DocuDeletedValue records so that they reference the target storage location.

    ```sql
    update DOCUVALUE
    set ACCESSINFORMATION = replace(ACCESSINFORMATION, 'file://<SOURCE_PREFIX>/documents/', 'https://<STORAGE_ACCOUNT>.blob.core.windows.net/documents/'), STORAGEPROVIDERID = 1
    where STORAGEPROVIDERID = 4 --4 for LBD filesystem, 1 for Azure blob
    and ACCESSINFORMATION like 'file://<SOURCE_PREFIX>/documents/%'

    update DOCUDELETEDVALUE
    set ACCESSINFORMATION = replace(ACCESSINFORMATION, 'file://<SOURCE_PREFIX>/documents/', 'https://<STORAGE_ACCOUNT>.blob.core.windows.net/documents/'), STORAGEPROVIDERID = 1
    where STORAGEPROVIDERID = 4 --4 for LBD filesystem, 1 for Azure blob
    and ACCESSINFORMATION like 'file://<SOURCE_PREFIX>/documents/%'
    ```

5. Test a sample of the document handling attachments to make sure that they can now be accessed in the sandbox environment.

## Troubleshooting

For troubleshooting information, see [Troubleshoot upgrades to Dynamics 365 finance and operations self-service environments](../migration-upgrade/troubleshoot-self-service-env.md).

## Learn about the replication configuration and status via SSMS

In SSMS, if Object explorer includes a **Replication** folder, the replication feature is installed on the server and available.

After step 3 of the data upgrade process is completed, you should find the publisher configured under the **Replication** folder. To learn the replication status, select and hold (or right-click) the **Replication** folder, and then select **Launch replication monitor**.

- In the replication monitor, you can view all the publishers that have been created for replication.
- On the **Snapshot** tab, you can view the status of the snapshot.
- To view the detail log/transaction, double-tap (or double-click) a grid item.
- To view the data replication to the target, on the **All subscription** tab, double-tap (or double-click) the subscription from the grid item.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
