---
# required metadata

title: Move LCS implementation projects from on-premises to the cloud
description: This topic explains how to move your Microsoft Dynamics 365 Finance + Operations (on-premises) environments to the cloud.
author: MartinWalkerDynSA
ms.date: 02/02/2021
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

This topic explains how to move your Microsoft Dynamics 365 Finance + Operations (on-premises) environments that are hosted on your own infrastructure to the Azure cloud.

## Cloud subscription licenses

If you don't already have cloud subscription licenses, work with your cloud service provider or volume license reseller to get and activate the required subscriptions on your Azure Active Directory (Azure AD) tenant. All subscriptions for users and add-on environments must be activated.

## Configure LCS cloud implementation project

If no Finance and Operations cloud-named user subscription licenses have previously been activated on the Azure AD tenant, a new Microsoft Dynamics Lifecycle Services (LCS) cloud implementation project is automatically provisioned. Otherwise, you must open a support request to have an LCS cloud implementation project created. For more information, see [Multiple LCS projects and production environments on one Azure AD tenant](../../fin-ops/get-started/implement-multiple-projects-aad-tenant.md).

After your LCS cloud implementation project has been created, you must fully configure it. As part of this configuration, you must add users, an Azure DevOps association, and subscription estimates, fill in the Asset library and Business process modeler (BPM), and more.

> [!NOTE]
> While you're onboarding your project, you must select **AX 2012 Upgrade** as the source system, so that a singleton Azure SQL database will be used for your sandbox instead of an elastic pool. Eventually, a more appropriate option will be available, such as **On-premises Finance and Operations**.

## Complete development and testing of updated integrations

You will probably have to make some changes to the integration design patterns that you used for interfaces with your Finance + Operations (on-premises) environment. These changes can be substantial, and a detailed discussion of them is beyond the scope of this topic. Nevertheless, you must evaluate all your interfaces and make the appropriate changes to them.

You should consider developing your updated interfaces in such a way that they can coexist in the same code base as the original interfaces. This approach will simplify code lifecycle management during the period of your transition from on-premises to cloud. If this approach isn't possible, you must manage a new development branch through your cloud go-live. To simplify management of this new branch during the transition period, we recommend that you freeze other code changes as much as you can. Additionally, in your detailed cut-over plan, you should carefully document the steps for inactivating your old interfaces and activating the new interfaces.

## Do a trial migration and resolve issues

1. Deploy a tier-2 environment.
2. Apply the same code package that is applied in your on-premises production environment (or, as appropriate, in the current build from the cloud integration development branch that was discussed in the previous section). This code package should be a single, complete deployable package that includes any independent software vendor (ISV) solutions and licenses.
3. In SQL Server Management Studio (SSMS), run the following Transact-SQL (T-SQL) commands against the sandbox database to preserve the current Admin account, Azure AD tenant ID information, and Data management framework (DMF) shared working directory in that database. Save the results.

    ```sql
    SELECT SID,NETWORKALIAS,NETWORKDOMAIN,IDENTITYPROVIDER from USERINFO WHERE ID = 'Admin'
    SELECT VALUE from SYSSERVICECONFIGURATIONSETTING where name = 'TENANTID'
    SELECT TENANTID from POWERBICONFIG
    SELECT TENANTID from PROVISIONINGMESSAGETABLE
    SELECT TENANTID from B2BINVITATIONCONFIG
    SELECT TENANTID from RETAILSHAREDPARAMETER
    SELECT SHAREDFOLDERPATH from DMFPARAMETERS
    ```

4. Copy the database from on-premises to online. The export and import process that you use is the same process that is described in the [Golden configuration promotion](../database/dbmovement-scenario-goldenconfig.md) database movement tutorial. However, in this case, the source database is the existing on-premises production SQL database, and you must use the sqlpackage.exe approach that is described for importing into a developer environment. If you use the LCS self-service database import option instead, some data won't be imported, as noted in the warnings about data elements that are cleaned up. The target database information that is available in the LCS environment details must be used instead of the placeholders that are shown in the following code.

    ```powershell
    SqlPackage.exe /a:import /sf:D:\BacpacToImport\my.bacpac /tsn:<Azure SQL database server> /tdn:<target database name> /tu:<axdbadmin user from LCS> /tp:<axdbadmin password from LCS> /p:CommandTimeout=1200
    ```

5. Restore the Admin account, Azure AD tenant ID, and DMF shared directory values. Also remove the **SF** schema and its tables, if they are present.

    ```sql
    UPDATE USERINFO SET SID='<preserved SID>', NETWORKALIAS='<preserved NETWORKALIAS>', NETWORKDOMAIN='<preserved NETWORKDOMAIN>', IDENTITYPROVIDER='<preserved IDENTITYPROVIDER>' WHERE ID = 'Admin'
    UPDATE SYSSERVICECONFIGURATIONSETTING set VALUE='<preserved VALUE>' where name = 'TENANTID'
    UPDATE POWERBICONFIG SET TENANTID='<preserved TENANTID>'
    UPDATE PROVISIONINGMESSAGETABLE SET TENANTID='<preserved TENANTID>'
    UPDATE B2BINVITATIONCONFIG SET TENANTID='<preserved TENANTID>'
    UPDATE RETAILSHAREDPARAMETER SET TENANTID='<preserved TENANTID>'
    UPDATE DMFPARAMETERS SET SHAREDFOLDERPATH='<preserved SHAREDFOLDERPATH>'
    DROP TABLE IF EXISTS SYNCLOG
    DROP TABLE IF EXISTS SYNCLOCK
    DROP SCHEMA IF EXISTS SF
    ```

6. Reimport all other users, and assign the appropriate security roles.
7. Direct printing in a cloud environment is done via the Document Routing Agent (DRA). Set up sandbox DRAs as described in [Install the Document Routing Agent to enable network printing](../analytics/install-document-routing-agent.md), so that regression testing can include your printing scenarios.
8. Copy document handling attachments to the cloud. Document handling attachments aren't stored in the database. If they must be preserved, you must move them separately. For instructions, see the [Migrate document handling attachments to your sandbox](#migrate-document-handling-attachments-to-your-sandbox) section later in this topic.
9. Run a complete regression test cycle. This cycle should include testing of integrations.
10. Resolve any issues that are discovered during testing. For each issue, document and keep track of the correcting adjustments that you make in the sandbox, and repeat them in the on-premises source. If any change must not be made in the on-premises environment, because it's incompatible with the correct functioning of that environment, we recommend that you create a DMF data package for it instead of manually applying it for each iteration of the migration process.
11. Repeat steps 2 through 10 until all tests have been passed, and no further changes are being made to code or the configuration.

## Repeat the migration to production

1. Deploy the new production environment. Note that the regular prerequisites apply. For example, you must have an active subscription estimator, complete the LCS methodology phases before the operate phase, and complete the FastTrack readiness review. For more information, see [Prepare for go-live](../../fin-ops/imp-lifecycle/prepare-go-live.md).
2. Apply the final version of the software deployable package to production.
3. Stop making data changes to the on-premises production environment.
4. Repeat steps 3 through 6 in the [Do a trial migration and resolve issues](#do-a-trial-migration-and-resolve-issues) section to copy the final/up-to-date on-premises production database to the cloud sandbox.
5. Repeat step 8 in the [Do a trial migration and resolve issues](#do-a-trial-migration-and-resolve-issues) section to copy the final/up-to-date document handling attachments to the cloud sandbox.
6. Request a database refresh from sandbox to production. (The process is the same as the process that is used to promote a golden configuration database to production.)
7. Open a support request to have Dynamics Support Engineering copy the document handling attachments from the sandbox storage account to the production storage account and update the references in the production database's DocuValue and DocuDeletedValue tables. After the request has been completed, validate that the attachments are available for a sample of document handling records.
8. Set up DRAs for production. If you're reusing any of the DRAs that were previously installed as part of your trial migration, remember to update their configuration so that they connect to the production URL instead of the sandbox URL.
9. Reconcile your cloud and on-premises production environments, as detailed in your cut-over plan.
10. Obtain sign-off for the go-live.
11. Activate cloud production interfaces, batch jobs, and so on.
12. Start to transact in your cloud production environment.

## Migrate document handling attachments to your sandbox

Document handling attachments for Finance + Operations (on-premises) environments are stored in a file share. However, the cloud version doesn't support this file share. You can use the following procedure to copy the attachments to the Azure storage account for your sandbox environment and update the corresponding metadata in the database. For subsequent promotion to production, you can request that Dynamics Support Engineering copy the attachments from your sandbox to production.

1. <!--HERE-->Upload a copy of the document handling attachment files from the on-premises production file share to a temporary folder on one of the sandbox instances of Application Object Server (AOS). For example, you can upload a zip file of the attachments and unpack it on the target. If you don't have remote desktop access (for example, for a self-service environment), you can use a different virtual machine (VM) instead. For reasonable conversion performance, this VM should be in the same Azure datacenter as the target sandbox. If you aren't using the AOS instance, you must add the VM to an allow list for access to the sandbox's SQL database instance.
2. Open a support request to get the name of the sandbox Azure storage account and a time-limited shared access signature token for the documents container. Update the corresponding placeholders in the Windows PowerShell script that is run in the next step. Also update the placeholders for your temporary folder, and for your Finance and Operations transactional database, by using the environment details in LCS.
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


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
