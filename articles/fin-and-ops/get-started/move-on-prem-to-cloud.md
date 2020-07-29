---
# required metadata

title: Move implementation project from on-premises to cloud
description: This topic explains how to move your Dynamics 365 for Finance and Operations from on-premises to the cloud.
author: Martin Walker
manager: AnnBe
ms.date: 07/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: 
ms.search.scope:  Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: marwalke
ms.search.validFrom: 2020-07-28 
ms.dyn365.ops.version: AX 7.0
---

# Move LCS implementation projects from on-premises to cloud

[!include [banner](../includes/banner.md)]

You can move your Microsoft Dynamics 365 for Finance and Oeprations environments from on-premises, i.e. hosted on your infrastucture, to the Azure cloud. The following are the steps needed to do so.

## Cloud subscription licenses

If you do not already have cloud subscriptino licenses, work with your cloud service provider or volume license reseller to acquire and activate the required subscriptions against your Azure AD tenant. All subscriptions for users, and for add-on environments, must be activated.

## Configure LCS cloud implementation project

If these are the first Dynmics 365 for Finance and Operations cloud named user SLs being activated on the AAD tenant, a new LCS cloud inplementation project will be provisioned automatically. If these are not the first SLs on the tenant, you will need to open a Support Request to have a cloud LCS implementation project created. See the article on multiple LCS project's in an AAD tenant.
Once your LCS cloud implemntation project has been created, you will need to fully configure it. As part of this configuration, you must add users, a Microsoft Azure DevOps association, subscription estimates, the Asset library, Business process modeler (BPM), and so on.

## Complete development and testing of updated integrations

It is likely that you will need to make some changes to the integration design patterns you used for interfaces with your on-premises Finance and Operations environment. These changes could be substantial, and it is beyond the scope of this article to discuss them in detail. Nevertheless, you must evaluate each of your interfaces and make the appropriate changes to them. You should consider developing your updated interfaces such that they can coexist in the same code base as the originals, which will simplify code lifecycle management during your on-premises to cloud transition period. If this is not possible, then you will need to manage a new development branch through your cloud go-live. To simplify managmement of such a new branch during the transition period, it would be advisable to freeze other code changes to the maximum extent possible. You should also document carefully the steps for de-activation of your old interfaces and activation of the new ones, in your detailed cut-over plan.

## Conduct trial migration and resolve issues

1.	Deploy a tier-2 environment.
2.	Apply the same code package as in your on-prem production environment (or if appropriate, the current build from the cloud integrations development branch discussed above). This should be a single, complete deployable package, including any ISV solutions and licenses.
3.  Preserve the current Admin account and AAD tenant ID information in the sandbox database, by running the following T-SQL against the sandbox database in SSMS and saving the results:
  ```sql
SELECT SID,NETWORKALIAS,NETWORKDOMAIN,IDENTITYPROVIDER from USERINFO WHERE ID = 'Admin'
SELECT VALUE from SYSSERVICECONFIGURATIONSETTING where name = 'TENANTID'
SELECT TENANTID from POWERBICONFIG
SELECT TENANTID from PROVISIONINGMESSAGETABLE
SELECT TENANTID from B2BINVITATIONCONFIG
SELECT TENANTID from RETAILSHAREDPARAMETER
  ```
4.	Copy the database from on-prem to online. The export and import process is as described in the golden configuration promotion tutorial at https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/database/dbmovement-scenario-goldenconfig, except that the source database is the existing on-premises, production SQL database. For the import, it recommended to use the sqlpackage.exe approach. The target database credentials available in LCS will have to be provided.
SqlPackage.exe /a:import /sf:D:\BacpacToImport\my.bacpac /tsn:[Azure SQL database server] /tdn:[target database name] /tu:[axdbadmin user from LCS] /tp:[axdbadmin password from LCS] /p:CommandTimeout=1200
5.  Restore the Admin account and AAD tenant ID information.
  ```sql
UPDATE USERINFO SET SID='[preserved SID]', NETWORKALIAS='[preserved NETWORKALIAS]', NETWORKDOMAIN='[preserved NETWORKDOMAIN]', IDENTITYPROVIDER='[preserved IDENTITYPROVIDER]' WHERE ID = 'Admin'
UPDATE SYSSERVICECONFIGURATIONSETTING set VALUE='[preserved VALUE]' where name = 'TENANTID'
UPDATE POWERBICONFIG SET TENANTID='[preserverd TENANTID]'
UPDATE PROVISIONINGMESSAGETABLE SET TENANTID='[preserverd TENANTID]'
UPDATE B2BINVITATIONCONFIG SET TENANTID='[preserverd TENANTID]'
UPDATE RETAILSHAREDPARAMETER SET TENANTID='[preserverd TENANTID]'
  ```
6.  Re-import all other users.
7.	Set up Document Routing Agent(s).
8.  Copy document handling attachments to the cloud. Document handling attachments are not stored in the database, and must be moved separately, if there is a need to preserve them. See the section below for a detailed description of how to do this.
9.	Run complete regression test cycle, including of integrations.
10.	Resolve any issues. For any discovered during testing, document and keep track of correcting adjustments in Sandbox and repeat them in the on-premises source. If any change may not be made in the on-prem environment (i.e. would be incompatible with its correct functioning), it is recommended to create a DMF data package for it, rather than to apply it manually for each iteration of the migration process.
11. Iterate steps 2-10, until all tests have passed, and no further changes are being made to code or configuration.

## Repeat migration to Production 

1.	Deploy Production environment. Note that the normal prerequisites apply, including an active subscription estimator, completion of the LCS methodology phases priori to Operate, and completion of the FastTrack readiness review.
2.	Apply the final version of the software deployable package to Production.
3.	Stop making any further data changes to the on-premises Production environemnt.
4.	Repeat steps 3-6 of the trial migration to copy the final / up-to-date on-premises production database to the cloud sandbox.
5.  Repeat step 5 of the trial migration to copy the final / up-to-date document handling attachments to the cloud sandbox.
6.	Request a DB refresh from sandbox to Production (i.e. the same process as promoting a golden configuration database to production).
7.  Open a support request to have Dynamics Support Engineering copy the document handling attachments from the sandbox storage account to the production storage account and update the references in DocuValue and DocuDeletedValue.
8.	Set up Document Routing Agent(s).
9.	Reconcile as required with the on-premises production environment and obtain sign off on the go-live
10. Activate cloud production interfaces, batch jobs, etc.
11.	Start transacting in cloud production environemnt.

## Migrating document handling attachments

Document handling attachments for Dynamics 365 for FInance and Operations on-premises are stored in a file share, which the cloud version does not support. With the following procedure you can copy the attachments to the Azure storage account for your sandbox environment and update the corresponding metadata in the database.

1. Upload a copy of the document handling attachment files from the on-premises production file share to a temporary folder on one of the sandbox AOSs. You can do this by, e.g. uploading a zip of the attachments and unpacking it on the target. If you do not have remote desktop access (e.g. for a self-service environment), then you can use a different VM instead, which for reasonable conversion performance, should be in the same Azure Data Center as the target sandbox. If you are notusing the AOS, you will need to whitelist your VM for access to the sandbox's Azure SQL.
2. Get the storage account connection string for the sandbox, from the AzureStorage.StorageConnectionString key in the web.config file in the AOS webroot of the sandbox. Note that this config file is encrypted, so you will need to decrypt a copy of it to get the connection string. If you are unable to get this information (e.g. for a self-service envvironment), open a Support Request to get a (time-limited) SAS token for the documents container of the sandbox Azure storage account. You can then use this, instead of a connection string, to create tge storage context inthe PowerShell script below.
3. Execute the following PowerShell script on the sandbox AOS (or other VM) to upload the document handling files to the storage account and create the required metadata for each file.
  ```powershell
#Upload F&O on-prem document handling attachments to Azure storage account
#
$filesPath = "<TEMP_ATTACHMENTS_FOLDER_PATH>"
$dBHostName = "<DATABASE_SERVER>.database.windows.net"
$dBName = "<DATABASE_NAME>"
$dBUsername = "<DATABASE_USER>"
$dBPassword  = "<DATABASE_PASSWORD>"
$storageAccountConnectionString = "AccountName=<STORAGE_ACCOUNT_NAME>;AccountKey=<STORAGE_ACCOUNT_KEY>;DefaultEndpointsProtocol=https;EndpointSuffix=core.windows.net"

[Reflection.Assembly]::LoadWithPartialName("System.Security.Cryptography") #Load crypto
$cryptoObj = [System.Security.Cryptography.SHA256]::Create()
$StorageContext = New-AzStorageContext -ConnectionString $storageAccountConnectionString
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
4. Update the DocuValue and DocuDeletedValue records to reference the target storage location by running the following T-SQL commands in SSMS.
  ```sql
update DOCUVALUE
  set ACCESSINFORMATION = replace(ACCESSINFORMATION, 'file://<SOURCE_PREFIX>/documents/', 'https://<STORAGE_ACCOUNT>.blob.core.windows.net/documents/'), 
  STORAGEPROVIDERID = 1
where STORAGEPROVIDERID = 4 --4 for LBD filesystem, 1 for Azure blob
  and ACCESSINFORMATION like 'file://<SOURCE_PREFIX>/documents/%'

update DOCUDELETEDVALUE
  set ACCESSINFORMATION = replace(ACCESSINFORMATION, 'file://<SOURCE_PREFIX>/documents/', 'https://<STORAGE_ACCOUNT>.blob.core.windows.net/documents/'), 
  STORAGEPROVIDERID = 1
where STORAGEPROVIDERID = 4 --4 for LBD filesystem, 1 for Azure blob
  and ACCESSINFORMATION like 'file://<SOURCE_PREFIX>/documents/%'
  ```
5. Test a sample of the document handling attachments to ensure they are now accessible in the target environment.
