---
# required metadata

title: Move LCS implementation projects from on-premises to the cloud
description: This article explains how to move your Microsoft Dynamics 365 Finance + Operations (on-premises) environments to the cloud.
author: ttreen
ms.date: 03/09/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: marwalke
ms.search.validFrom: 2020-09-30 
ms.dyn365.ops.version: 10.0.13
---

# Move LCS implementation projects from on-premises to the cloud

[!include [banner](../includes/banner.md)]

This article explains how to move your Microsoft Dynamics 365 Finance + Operations (on-premises) environments that are hosted on your own infrastructure to the Azure cloud.

## Background
Previous migrations to the cloud would use SQLPackage to create and restore a bacpac file to move the on-premises database into the cloud. That is no longer supported, and the approach now is to use the Data Migration Toolkit 1.0.8 (or higher). 

## Cloud subscription licenses

If you don't already have cloud subscription licenses, work with your cloud service provider or volume license reseller to get and activate the required subscriptions on your Azure Active Directory (Azure AD) tenant. All subscriptions for users and add-on environments must be activated.

## Configure LCS cloud implementation project

If no finance and operations cloud-named user subscription licenses have previously been activated on the Azure AD tenant, a new Microsoft Dynamics Lifecycle Services (LCS) cloud implementation project is automatically provisioned. Otherwise, you must open a support request to have an LCS cloud implementation project created. For more information, see [Multiple LCS projects and production environments on one Azure AD tenant](../../fin-ops/get-started/implement-multiple-projects-aad-tenant.md).

After your LCS cloud implementation project has been created, you must fully configure it. As part of this configuration, you must add users, an Azure DevOps association, and subscription estimates, fill in the Asset library and Business process modeler (BPM), and more.

## Complete development and testing of updated integrations

You will have to make some changes to the integration design patterns that you used for interfaces with your Finance + Operations (on-premises) environment. These changes can be substantial, and a detailed discussion of them is beyond the scope of this article. Nevertheless, you must evaluate all your interfaces and make the appropriate changes to them.

You should consider developing your updated interfaces in such a way that they can coexist in the same code base as the original interfaces. This approach will simplify code lifecycle management during the period of your transition from on-premises to cloud. If this approach isn't possible, you must manage a new development branch through your cloud go-live. To simplify management of this new branch during the transition period, we recommend that you freeze other code changes as much as you can. Additionally, in your detailed cut-over plan, you should carefully document the steps for inactivating your old interfaces and activating the new interfaces.

## Prerequisites

1. Deploy a Tier-2 Sandbox (UAT) Self-Service environment.
1. Apply the same code package that is applied in your on-premises production environment (or, as appropriate, in the current build from the cloud integration development branch that was discussed in the previous section). This code package should be a single, complete deployable package that includes any independent software vendor (ISV) solutions and licenses.

    > [!NOTE]
    > Keep the following points in mind:
    > 
    > - The LBD migration process is for finance and operations self-service sandbox (UAT) environments only. It can never be run against a production environment. A gold copy refresh is performed to move the migrated data into production. 
    > - Make sure you download the latest version of the **Data Migration Toolkit for Dynamics 365** from LCS.
    > - Do not deploy or use the linked Power Platform environment for the migration. The Power Platform environment can be deployed and used after the data upgrade is completed.

1. Download the **Data Migration Toolkit for Dynamics365 Version 1.0.8 (or higher)** from Microsoft Dynamics Lifecycle Services (LCS). In the Shared asset Library, select **Model** as the asset type, and then select the model file.
1. Download and install the [.NET Framework version 4.7.1](https://dotnet.microsoft.com/download/dotnet-framework/net471) if it isn't already installed.
1. Make sure that the replication feature is installed and enabled for the source SQL Server instance. To determine whether replication is enabled, run the following SQL script.

    ```sql
    -- If @installed is 0, replication must be added to the SQL Server installation.
    USE master;
    GO
    DECLARE @installed int;
    EXEC @installed = sys.sp_MS_replication_installed;
    SELECT @installed;
    ```

    If the replication components aren't installed, follow the steps in [Install SQL Server replication](https://learn.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-replication.md) to install them.

1. SQL Server authentication must be set to **SQL Server and Windows Authentication mode**. (This change requires a restart of the SQL Server service.) The toolkit uses native SQL logins only.
1. Enable and start the SQL Server Agent on the source database server.

    > [!NOTE]
    > A user should have the **DB\_Owner** privilege in the source database and should have access to the master database and the source database.

## Migration Toolkit Setup

1. Extract the **Data Migration Toolkit for Dynamics365 Version 1.0.x** you downloaded from LCS into a folder of your choosing. 

    > [!NOTE]
    > Right click on the download, and uncheck the unblock check box, to ensure the zip file extracts correctly. 

1. In the folder where the zip was extracted, open the **DataMigrationTool.exe.config** file.
   - In the file locate the following line:
   ```XML
   <add key="isD365OnPrem" value="false" />
   ```
   - change the value from **false** to **true**, as in the example below:
   ```XML
   <add key="isD365OnPrem" value="true" />
   ```
2. **[Optional]** If you don't want some of the source database tables to be replicated in the target database, you can specify them in the IgnoreTables.xml file. Likewise, if you don't want some of the functions to be replicated, you can specify them in the IgnoreFunctions.xml file. Additionally, if you would like to put some specific tables in publications outside of the main publications, you can use the SpecialTables.xml file. 

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
    > The tables added to the ignore list should only be tables that do not exist in the Microsoft Dynamics AX 2012 Application Object Tree (AOT). Including tables that exist in the AOT will result in an error during the data upgrade. These tables won't be replicated to the target database.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <IgnoreFunctions>
        <Name>
            <Function>if_WHSInventReserveUnionDelta</Function>
        </Name>
    </IgnoreFunctions>
    ```

    > [!IMPORTANT]
    > The functions that are specified in the XML file won't be replicated in the target database.


   ```
   <?xml version="1.0" encoding="utf-8"?>
   <SpecialTables>
     <Name>
       <Table></Table>
     </Name>
   </SpecialTables>
   ```
   
    > [!IMPORTANT]
    > Tables specified in the SpecialTables file, will be added to a dedicated publisher. The number of special table publishers is based on the NumberOfPublishers parameter, see the step below. Special table handling can be useful for very large tables that you may need to manually start the replication on during downtime hours.
    
9. **[Optional]** To optimize the replication latency/performance, you can update the following distributor parameters in the **App.config** file:

    - **MaxBcpThreads** – By default, this parameter is set to **6**. If the machine has fewer than six cores, update the value to the number of cores. The maximum value that you can specify is **8**.
    - **NumberOfPublishers** – By default, this parameter is set to **2**. The recommendation is to use this value. However, there can be situations where you may want to increase the number of publishers, to distribute smaller numbers of tables to each publisher. This in conjunction with the manual snapshot start process, allows you to run smaller initial snapshots, that can be useful if you have limited maintenance windows and need to split the start up of the replication over several.
    - **snapshotPostPublication** - This option will add in a 5-minute delay between automatic snapshot processes starting, that can assist with loads on the source server. The toolkit also allows for manual snapshot starts, if you choose that option, you don't need to set this. 

   > [!NOTE]
   > Do not set up or configure replication during peak times when the system resources/memory usage/IO operations are high. 
   >
   > When resources are being used to the max (greater than 90% is already consumed) then the replication may be delayed as the system tries to find available resources. We recommend that you start the replication during off hours, when the system resources are at minimum usage (during off-peak time). 
   >
   > Additionally, it is recommended for a go-live cutover that you start the replication the prior weekend. 

## Migration Process

### Run the DataMigrationTool.exe application

 > [!IMPORTANT]
 > Before you begin the migration process, ensure that the environment is in a **Deployed** state.

1. Run the **DataMigrationTool.exe** application.

    A console window will open where you can provide the cloud environment type.  
   - Public : **lcs.dynamics.com**
   - GCC : **gov.lcs.microsoftdynamics.us**   
   - UAE : **\[ uae.lcs.dynamics.com \]**    

   > [!NOTE]
    After you enter the cloud environment, you will receive a prompt to sign in.

1. Provide the credentials that are used to sign in to LCS.
1. After you're successfully authenticated, in the console window, provide the **Project-Id** value and then the **Environment-Id** value.

    To validate the given values, you will need to sign in using the credentials that are used to sign in to LCS.

    > [!NOTE]
    > You can find the **Project-Id** and **Environment-Id** values on the **Manage environment** page in LCS. You can also find the **Environment-Id** value on the **Environment details** page.

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
    > The specified distribution database and replication snapshot paths should have enough space. We recommend that the amount of space be at least the size of the source database. If you have used compression in your AX 2012 database, then the space needed will be larger as the snapshot is uncompressed. The paths should be in the local disk of the machine. Avoid using shared paths.
    > 
    > We recommend that you have a static IP address for the virtual machine (VM) or machine (for the allowlist in step 1). In this way, you help prevent connection issues with the target database.

    This step performs the following actions:

    - It validates the connection to the source database.
    - It validates the version of the D365 LBD database.
    - It authorizes the source IP address.
    - It validates the target databases.

2. **Environment preparation: Prepare the target environment for the data upgrade**

    This step changes the state of the LCS environment from **Deployed** to **Ready for replication**.

3. **Replication: Cleanup Target Database**

    This step performs the following actions:

    1. Change the state of the LCS environment from **Ready for replication** to **Replication in progress**.
    2. Delete all AX product tables, views, stored procedures, and user-defined functions in the target database.

4. **Replication: Setup Distributor**

    This step creates a distribution database under the **System Databases** folder on the source server. This distribution database is used for replication.

5. **Replication: Setup Publication for Primary Key (PK) Tables**

    This step creates publications for primary key tables under the **Replication** folder on the source server and replicates them in the target database. If any **ignore-table** entries were specified, the specified tables are exempted from replication. Any **special-table** entries were added, these will be added to additional special tables publications. 
    
    You will be prompted with: **Do you want the snapshot to start automatically ? Continue by giving Y(Yes) for Automatic, else N(No) for manual(If No you have to manually start the snapshots from replication monitor)**. Selecting **Yes** will start the snapshot replication automatically, **No** will require that you go into SQL Management Studio, launch the Replication Monitor and manually start each snapshot. The advantage of manually starting snapshots allows you to control the load on the source SQL Server. This can use useful if you have limited low-usage periods or maintenance windows to start the replication. Additionally, it allows you to split up when you start the snapshot process. 


    **Created publishers:** AX\_PUB\_PkTable\_\[\*\]

    > [!NOTE]
    > After this replication configuration step is completed, actual data replication will occur as a SQL job that runs in the background. This job will take some time to be completed. You can view the status of the replication by providing the **'rs'** option. To learn more about the **'rs'** option, see the [Reporting section of the application] section later in this article.

6. **Replication: Setup Publication for Other Objects (functions)**

    This step creates a publication for other objects (functions) and replicates them in the target database. If you don't want some of the functions to be replicated, you can specify them in the IgnoreFunctions.xml file.

    **Created publisher:** AX\_PUB\_OtherObjects

    > [!NOTE]
    > The replication will take some time to be completed. You can view the replication status by providing the **'rs'** option.
    >
    > If there are no functions to replicate, the publication won't be created.
    > 
    > Don't move on to the next step until the **DataReplicationStatus** property for this step is shown as completed.

7. **Cutover: Set up publication for non-primary key tables**

     This step creates two publications: one used to replicate non-primary key tables, and the other one used to replicate locked tables. Again, you will be prompted as in the PK table step if you want to automatically or manually start the snapshot. 
    
    > [!NOTE]
    > If there are no locked tables, then publication will not be created.

    **Publication names:** AX\_PUB\_NoPKTable, AX\_PUB\_TABLE\_LockedTable

    If AX Service acquires a schema lock during creation of the primary key publication, those tables will be ignored and omitted from the publication. They will be added to temporary tables and marked for replication during creation of the cutover publication.

    > [IMPORTANT]
    > Don't move on to next step until the **DataReplicationStatus** property for this step is shown as completed.
   
    > [!NOTE]
    > You can validate the replicated data by using the **'dv'** option. If there are mismatched tables, this step lets you create publications for them. If you want to exclude any mismatched tables for replication, close the app, and add those tables in **Data/IgnoreTables.xml**. Then rerun the app, and use the **'dv'** option.
    > 
    > To learn more about the **'dv'** option, see the [Reporting section of the application](data-upgrade-self-service.md#reporting-section-of-the-application) section later in this article.
 
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

    This step changes the state of the LCS environment from **Replication in progress** to **Replication completed**.

10. **Data Synchronise: Trigger Transformation**

    This step triggers a servicing step within LCS that will update the database for the cloud. When the action is successful, the state of the LCS environment changes from **Replication completed** to **Data upgrade in progress**.

    If data migration is successful the environment will be set to a **deployed** status in LCS. 

11. **Data Synchronise: Trigger Rollback**

    This step triggers the rollback of data upgrade. This rolls back the data to the point before the transformation is triggered and sets the LCS environment state to **Replicated**. This will change the environment from **Failed** to the **Replicated** state.
    
    At this point, you have only triggered the rollback. To see the rollback status, use the **'rbs'** option. To learn more about this option, see the [Reporting section of the application](data-upgrade-self-service.md#reporting-section-of-the-application) later in this article.
    
    If rollback is successful, the **'rbs'** option is shown as **AX 2012 upgrade topology (LCS) status: Replicated**.

    If rollback fails, the **'rbs'** option is shown as **AX 2012 upgrade topology (LCS) status: Failed**.

## Reporting section of the application

You can use the following options to review the reports of the replication validation, replication status, data upgrade status, and rollback data upgrade status.

- **dv) Report:** Validate the replication.

    This option compares the number of tables and records in the source server database and the target server database, and then shows the report. You should use this option only after step 7 is completed.
    
    If there are mismatched tables, this step lets you create a publication for them. If you want to exclude any mismatched tables for replication, close the app, and add those tables in **Data/IgnoreTables.xml**. Then rerun the app, and use the **'dv'** option.

    You can find the report data at **output/PostValidationInfo.csv**.

- **rs) Report:** Get the replication status.

    This option shows the report of the replication process for the publications that were created. You should use this option only after step 5 is started (that is, during the replication process for any publication).
   
- **rbs) Report:** Get the rollback status.

    This option shows the report of the rollback process. You should use this option only after step 11 has started.

## Tooling section of the application

- **Reset-rep:** Reset the replication setup by removing all the replication configurations. Publications and the distribution database are deleted. The status of all **Replication** and **Cutover** menu options is reset from **Completed** mode to **Reset** mode to help you redo the replication from the beginning.
- **Reset-all:** Reset all the menu options, and remove the replication configurations. The status of all the options is changed to **Reset**.
- **Clear:** Clear the environment setup activity. All information is cleared from the cache, such as the **project-Id** value, **Environment-Id** value, and source database details.
- **Help:** Show the data upgrade migration options with the updated status.
- **Exit:** Close the application.
- **Set-failed:** If you want to delete the environment—and if the environment is in the **PreparingForReplication**, **ReadyForReplication**, or **Replicating & Replicated)** state—use this option to set the environment state to **Failed**, and then the environment can be deleted from  LCS.

## Post Migration Tasks

1. If needed, reimport all other users, and assign the appropriate security roles. Users now need to be assigned to Azure AD accounts.
1. Direct printing in a cloud environment is done via the Document Routing Agent (DRA). Set up sandbox DRAs as described in [Install the Document Routing Agent to enable network printing](../analytics/install-document-routing-agent.md), so that regression testing can include your printing scenarios.
1. Copy document handling attachments to the cloud. Document handling attachments aren't stored in the database. If they must be preserved, you must move them separately. For instructions, see the [Migrate document handling attachments to your sandbox](#migrate-document-handling-attachments-to-your-sandbox) section later in this article.
1. Run a complete regression test cycle. This cycle should include testing of integrations.
1. Resolve any issues that are discovered during testing. For each issue, document and keep track of the correcting adjustments that you make in the sandbox, and repeat them in the on-premises source. If any change must not be made in the on-premises environment, because it's incompatible with the correct functioning of that environment, we recommend that you create a DMF data package for it instead of manually applying it for each iteration of the migration process.
1. Repeat steps 2 through 10 until all tests have been passed, and no further changes are being made to code or the configuration.

## Repeat the migration to production

Follow all previous steps to migrate data, but follow this document: [Golden configuration promotion - Copy the sandbox database to production](../../fin-ops-core/dev-itpro/database/dbmovement-scenario-goldenconfig#copy-the-sandbox-database-to-production) 

## Migrate document handling attachments to your sandbox

Document handling attachments for Finance + Operations (on-premises) environments are stored in a file share. However, the cloud version doesn't support this file share. You can use the following procedure to copy the attachments to the Azure storage account for your sandbox environment and update the corresponding metadata in the database. For subsequent promotion to production, you can request that Dynamics Support Engineering copy the attachments from your sandbox to production.

1. <!--HERE-->Upload a copy of the document handling attachment files from the on-premises production file share to a temporary folder on one of the sandbox instances of Application Object Server (AOS). For example, you can upload a zip file of the attachments and unpack it on the target. If you don't have remote desktop access (for example, for a self-service environment), you can use a different virtual machine (VM) instead. For reasonable conversion performance, this VM should be in the same Azure datacenter as the target sandbox. If you aren't using the AOS instance, you must add the VM to an allow list for access to the sandbox's SQL database instance.
2. Open a support request to get the name of the sandbox Azure storage account and a time-limited shared access signature token for the documents container. Update the corresponding placeholders in the Windows PowerShell script that is run in the next step. Also update the placeholders for your temporary folder, and for your finance and operations transactional database, by using the environment details in LCS.
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

For troubleshooting information, see [Troubleshoot upgrades to Dynamics 365 Finance + Operations self-service environments](troubleshoot-self-service-env.md).

## Learn about the replication configuration and status via SQL Server Management Studio

In SSMS, if Object Explorer includes a **Replication** folder, the replication feature is installed on the server and available.

After step 3 of the data upgrade process is completed, you should find the publisher configured under the **Replication** folder. To learn the replication status, select and hold (or right-click) the **Replication** folder, and then select **Launch Replication Monitor**.

- In the replication monitor, you can view all the publishers that have been created for replication.
- On the **Snapshot** tab, you can view the status of the snapshot.
- To view the detail log/transaction, double-tap (or double-click) a grid item.
- To view the data replication to the target, on the **All Subscription** tab, double-tap (or double-click) the subscription from the grid item.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

