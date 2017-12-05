---
# required metadata

title: Troubleshoot Dynamics 365 for Finance and Operations, Enterprise edition on-premises 
description: This topic provides troubleshooting information for on-premises deployments of Dynamics 365 for Finance and Operations, Enterprise edition. 
author: sarvanisathish
manager: AnnBe
ms.date: 06/13/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: Platform Update 8

---
# Troubleshoot Dynamics 365 for Finance and Operations, Enterprise edition on-premises

[!include[banner](../includes/banner.md)]


## Service Fabric 
Service Fabric is one of the initial components to install and configure for your on-premises deployment. Service Fabric is used by the Orchestrator, AOS, SSRS and MR nodes.

## Access Service Fabric Explorer
Service Fabric Explorer can be accessed by using a browser and the default address, https://sf.d365ffo.onprem.contoso.com:19080. To verify the address, note what was used in the topic section, [Create DNS zones and add A records](setup-deploy-on-premises-environments.md#createdns). 
To access the site, the client certificate needs to be located in cert:\CurrentUser\My (Certificates - Current User > Personal > Certificates) of the machine that is accessing the site. When you access the site, select the client certificate when prompted.

## Stateful and Stateless Services, how to identify nodes for log review 
To find out what machine is the primar instance for Stateful Services, like a Local Agent, go to Service Fabric Explorer, expand **Cluster** > **Applications** > **(intended application ex) LocalAgentType** > **fabric:/LocalAgent** > **Fabric:/LocalAgent/ArtifactsManager** > **(guid)**. Note the primary node. 
For Stateless Services, or the rest of the applications, you need to check all of the nodes. 

## Timeout error received when creating a Service Fabric cluster 
Run the Test-D365FOConfiguration.ps1 as noted in [Set up a standalone Service Fabric cluster](setup-deploy-on-premises-environments.md#setupsfcluster) and note any errors. 
Verify that the Service fabric Server certificate, client certificate exists in the LocalMachine store on ALL service fabric nodes. 
Verify that the Service fabric Server certificate has the ACL for Network Service on ALL service fabric nodes.

## Time out while waiting for Installer Service to complete for machine x.x.x.x
You can only have one node type for each IP address (machine). Check to see if the nodes are being reused on same machine, for example AOS and ORCH on same machine, and that the ConfigTemplate.xml is correctly defined. 

## Remove a specific application 
We recommend that you use LCS to remove or cleanup deployments. However, if additional steps are needed, you can use Service Fabric Explorer to remove an application.  
In Service Fabric Explorer, go to **Application node** > **Applications** > **MonitoringAgentAppType-Agent**. Click the ellipses by **fabric:/Agent-Monitoring** and delete the application. Enter the full name of the application to confirm. 
You can also remove the **MonitoringAgentAppType-Agent** by clicking the ellipses and then **Unprovision Type**. Enter the full name to confirm. 

## Remove Service Fabric completely 
To remove the Service Fabric completely remove ServiceFabricCluster.ps1 -ClusterConfigFilePath "<path to working directory>\ClusterConfig.json". If this results in error, remove a specific node on that cluster from the
powershell.exe -File "C:\Program Files\Microsoft Service Fabric\bin\fabric\fabric.code\CleanFabric.ps1" 

Next, remove c:\ProgramData\SF folder, if using the default. Otherwise, remove the specified folder. 
If you receive an access denied error, restart PowerShell or restart the machine. 

## LocalAgent 
LocalAgent is the framework that is responsible for communicating with LCS, downloading components to be installed, installation, and maintaining and removing Dynamics. 

## How to find the LocalAgent values that are used 
Local Agent values can be found in Service Fabric Explorer under **Cluster** > **Applications** > **LocalAgentType** > **fabric:/LocalAgent, Details** section.

## Install, upgrade, or uninstall Local agent 
Local agent installation is discussed in the topic, [Set up and deploy on-premises environments](setup-deploy-on-premises-environments.md). You can also use the follwoing upgrade and uninstall commands: 

    LocalAgentCLI.exe Install <path of localagent-config.json> 
    LocalAgentCLI.exe Upgrade <path of localagent-config.json> 
    LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    
> [!NOTE]
    > The cleanup command doesn't remove any of the files that were placed in the file share. The file share can be reused.

## Error occurs when starting up Local agent services  
If you receive the error, "Could not load file or assembly 'Lcs.DeploymentAgent.Proxy.Contract, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies", this means that the **Strong name** verification should no longer be enabled. This is done by using Configure-PreReqs.ps1. To validate that the verification is no longer enabled, run Test-D365FOConfiguration.ps1.

## In LCS, "Validation in progress" is showing for a period of several minutes
Complete the following steps to troubleshoot general issues with local agent validation.
1. Run the Configure-PreReqs.ps1 on all the orchestrator machines to configure the machines correctly. 
2. Verify that the script Test-D365FOConfiguration.ps1 passes on all of the orchestrator machines.  
3. Verify that the installation of LocalAgentCLI.exe completed successfully. 
4. Go to Service Fabric Explorer and verify that the applications are all healthy. 
5. If the applications are not healthy, locate the primary node for the failing service. 
   Look for events in:
   
   - **Event Viewer > **Custom Views** > **Administrative Events** 
   - **Event Viewer** > **Applications and Services Log** > **Microsoft** > **Dynamics** > **AX-LocalAgent 

**Common errors**
The following are common errors that you may see:

- Receiving 'Unable to process commands' and/or 'Unable to get the channel information' messages 
- "RunAsync failed due to an unhandled exception causing the host process to crash: System.ArgumentNullException: Value cannot be null. Parameter name: certificate 

**Reason**
These errors might occur because the certificate specified for the OnPremLocalAgent certificate is not valid or is not configured correctly for the tenant. 

**Steps** 
To resolve these errors, complete the followign steps.
1. Run Test-D365FOConfiguration.ps1 on all Orchestrator nodes to ensure all checks pass. 
2. Verify that the certificate specified in local agent configuration is correct.  

- Make sure there are no special characters while specifying the thumbprint in LCS and the ConfigTemplate.xml. 
- The certificate should be the same as what is specified in infrastructure\ConfigTemplate.xml for  
    
        <Certificate type="Orchestrator" exportable="true" generateSelfSignedCert="true"> 
          <Name>OnPremLocalAgent</Name> 
          <Thumbprint></Thumbprint> 
          <ProtectTo></ProtectTo> 
        </Certificate> 
3. Ensure that the steps in [Configure LCS connectivity for the tenant](setup-deploy-on-premises-environments.md#configurelcs) section were completed using the same certificate that is specified in local agent configuration in LCS. 
4. Uninstall the local agent.  
5. Specify the correct certificate in the local agent configuration and download the configuration file again. 
6. Install the local agent again with the new configuration file. 

**Error** 
Access to the path '\\...\agent\assets\StandAloneSetup-76308-1.zip' is denied. 

**Reason**
The file share specified in local agent configuration is not valid. 

**Steps** 
1. Verify that the specified share exists. 
2. Verify that the local agent user has full permission on the share. The local agent user is the DNS name specified in ConfigTemplate.xml in the section, 
  
          <ADServiceAccount type="gMSA" name="svc-LocalAgent$" refName="gmsaLocalAgent"> 
              <DNSHostName>svc-LocalAgent.d365ffo.onprem.contoso.com</DNSHostName> 
          </ADServiceAccount> 
          
3. Ensure that the Setup file share section in setup document is completed. 
4. Uninstall the local agent.  
5. Specify the correct file share in local agent configuration and download the configuration file again. 
6. Install local agent again with the new configuration file. 

**Error** 
Login failed for user 'D365\svc-LocalAgent$'. Reason: Could not find a login matching the name provided. [CLIENT: 10.0.2.23]  

**Reason**
The local agent user is not able to connect to the orchestration database. This could happen because users may have been deleted and then recreated in the AD which means the SID of the user has changed. Any access given to the user for the SQL Server or database will no longer work. 

**Steps**
To resolve this error, complete the followign steps.
1. Run the script on the SQL server:

        .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
        
This creates an empty orchestrator database, if one does not already exist, and adds the local agent user to the database with db_owner permission 
2. The application should automatically go to healthy state after the correct permissions are provided. 
3. If any of the settings, such as the SQL FQDN, Database name, and local agent user was provided incorrectly in LCS, change the settings and reinstall local agent. 
4. If the first three steps do not resolve the issue, manually remove the local agent user from the SQL server and the database and then re-run the Initialize-Database script. 
5. If you recreate a user in AD, remember that the SID will change. Remove the previous SID for the user and add a new SID. 

**Additional scenario**
The local agent user can't connect to the SQL server or database. 

**Steps** 
1. Delete the svc-LocalAgent user from the sql server primary node databases and then remove the login from both servers.  
2. Run the following scripts: 

        .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
        .\Configure-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
        
  These scripts do not work with **always-on** setup. The database needs to be created first in the primary node and then replicated.  

**Error** 
RunAsync failed due to an unhandled exception causing the host process to crash: System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: The remote name could not be resolved: 'lcsapi.lcs.dynamics.com' 

**Reason** 
The local agent machines can't connect to lcsapi.lcs.dynamics.com. Review the AX-BridgeService eventlog for "The remote name could not be resolved: 'lcsapi.lcs.dynamics.com'".  

**Steps** 
Complete the following steps to resolve the error.
1. Run [psping lcsapi.lcs.dynamics.com:80].  
2. If you don't receive a reply, contact the IT department at your organization as the firewall is blocking access to lcsapi or proxy issues:

        Lcsapi.lcs.dynamics.com 
        <lcs azure blob storage domain> 
        <lcs azure queue domain> 

**Error**
Access to the path '\\...\agent\assets\StandAloneSetup-76308-1.zip' is denied.

**Reason** 
The local agent user can't access the file share specified in local agent configuration. 

**Steps**  
Complete the following steps to resolve the error.
1. Make sure that the file share exists and is valid. 
2. Download PsExec from https://docs.microsoft.com/en-us/sysinternals/downloads/psexec.
3. Open a command prompt and run PsExec.exe -u contoso\svc-LocalAgent$ cmd.exe. 
4. Access the file share and verify that there are no errors. 
5. Add the local agent user to the file share and give them full permissions. 
6. Check for svc-LocalAgent$ rights to path (NTFS and share permissions). 

## Error: "Unable to load DLL 'FabricClient.dll':"
If you receive this error, close and reopen PowerShell. If the error still occurrs, restart the machine. 

## What Cluster ID in Agent config should be used 
The Cluster ID can be any GUID. This GUID is used for tracking purposes. 

## Local Agent stops working after the tenant for the project from LCS is changed 
Complete the following steps to configure Local Agent with updated tenant.  
1. Remove all of the environments from LCS that already have the connector installed. 
2. Uninstall the local agent 

        .\LocalAgentCLI.exe Cleanup <path of localagent-config.json> 
        
3. Complete the steps in section [11. Configure LCS connectivity for the tenant](setup-deploy-on-premises-environments.md#configurelcs). 
4. Create a new LCS connector in the new tenant. 
5. Download the local-agent.config file. 
6. Install local agent. 
   
        .\LocalAgentCLI.exe Install <path of localagent-config.json>
        

## Monitor deployment locally 
Review the Event Viewer logs for the primary orchestrator machine and artifacts manager, and the bridge service 
AX-LocalAgent (overall installation process). 

- Modules  
    - Common 
    - Reportingservices 
    - AOS 
    - Financialreporting 
- Command 
    - Setup 
    - Dvt - Deployment verification test 
        
AX-SetupModuleEvents (additional details for Module details) 
AX-SetupInfrastructureEvents (additional details when interactions with Service Fabric) 

## AOS machines
**Event Viewer** > **Applications and Services Logs** > **Microsoft** > **Dynamics** > **AX-DatabaseSynchronize** 
**Event Viewer** > **Custom Views** > **Administrative Events** 

## Find a full error
Click on the **Details** tab to view the full error message. 

## Service Fabric failing
Note the service that is failing and open the corresponding application directory. For example, C:\ProgramData\SF\ORCH1\Fabric\work\Applications\LocalAgentType_App5\log.

## Encryption errors
Some encryption error examples include, AXBootStrapperAppType, Bootstrapper, AXDiagnostics, RTGatewayAppType, Gateway potential failure related, and Microsoft.D365.Gateways.ClusterGateway.exe.

You might receive one of these errors if the data encipherment cert is used to encrypt AOS AccountPassword was not installed on the machine. This cert could be in the Certificates (Local Computer) or it could be that the Provider type is wrong. 

To resolve the error, validate  the credentials.json file. Check if the texts there are decrypting correctly by typing in the following message (on AOS1). 

        Invoke-ServiceFabricDecryptText -CipherText 'longstring' -StoreLocation LocalMachine | clip 

This error might have also occurred if the parameter **''** is not defined in the ApplicationManifest file. To verify this, 

- Check for proper layout/structure of credentails.json file Encrypt credentials  
- Check to see if end quote is at end of line or on next line 

Go to **Event Viewer** > **Custom Views** > **Administrative Events** 
    Error on Microsoft-Service Fabric source 
    
## Can't find the certificate and private key to use for decryption (0x8009200C) 
Missing cert and/or ACL or wrong thumbprint entry (ex axdataenciphermentcert and AXSF$ AXServiceUser) 

Check for special characters 

- Also may be able to see in C:\ProgramData\SF\AOS1\Fabric\work\Applications\AXBootstrapperAppType_App9\log\ConfigureCertificates….txt 
Note any ? For thumprints  

Test via Invoke-ServiceFabricDecryptText -CipherText 'longstring' -StoreLocation LocalMachine | clip 

- If receive "Cannot find the certificate and private key to use for decryption" then verify  axdataenciphermentcert and svc-AXSF$ AXServiceUser ACL 

If changed credentials.json then delete and redeploy from LCS 

## MR
Additional logging can be done by registering providers. Attached ETWManifest.zip can be downloaded to primary orchestrator machine and following commands ran 

- Copy ETWManifest to primary orch machine and run following  
    .\RegisterETW.ps1 -ManifestsAndDll @{"C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.man" =    "C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.dll"} 
- Note if needed to unregister, use following command 
    .\RegisterETW.ps1 -ManifestsAndDll @{"C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.man" = "C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.dll"} -Unregister  

After providers are registered, additional details will be logged on new deployment that can be reviewed in Event Viewer > Applications and Services Logs > Microsoft > Dynamics 

- MR-Logger 
- MR-Sql 
    
Error encountered while executing AddAXDatabaseChangeTracking at Microsoft.Dynamics.Performance.Deployment.FinancialReportingDeployer.Utility.InvokeCmdletAndValidateSuccess(DeploymentCmdlet cmdlet) at  
- Make sure full path is correct, ex ax.d365ffo.onprem.contoso.com 

Issue could also be with star/* cert 

- Example, The remote certificate CN=*.d365ffo.onprem.contoso.com has and invalid name or does not match the host ax.d365ffo.onprem.contoso.com  

The remote name could not be resolved: 'x.d365fo.onprem.contoso.com' / There was no endpoint listening at https://x.d365fo.onprem.contoso.com/namespaces/AXSF/services/MetadataService that could accept the message. This is often caused by an incorrect address or SOAP action. See InnerException, if present, for more details. 

- Verify address is reachable by manually browsing in browser 
    
Run initialize database script and validate DBs have correct users 

If only receive AddAXDatabaseChangeTracking event, try to reach the Metadataservice of AX: 
https://ax.d365ffo.contoso.com/namespaces/AXSF/services/MetadataService 
Also check Certificates of the service in file wif.config. You find this file by log on to one of the AOS boxes 
use task manager (ex details tab), locate AxService.exe, right-click and select open file location. In wif.config file, should see 3 thumbprints. Note that: 

- They have to be different. 
- They need to be in this order 
    1. Finacialreporting Thumbprint 
    2. ReportingService Thumbprint 
    3. SessionAuthentication Thumbprint 
  If invalid then need to redeploy from LCS with proper Thumbprints. 

## Unable to resolve the xPath value 
Not being able to resolve the xPath value of [TopologyInstance/CustomizationGroup[@name='ServiceConfiguration']/Group[@name='AOSServicePrincipalUser']/Customizations/Customization[@fieldName='PrincipalUserAccountPassword']/@selectedValue is expected behavior and is not an issue. The xPath value looking for AOS runtime user information however, because of integrated security, the information is not needed. The inability to resolve the xPath is communicated in case the failure needs to be investigated for another reason.  

## ADFS
Login page is not redirecting and is still prompting for credentials. For example, if you havExample was going to URL and getting "An error occurred. Contact your administrator for more information." 

- Add ADFS link to trusted sites 
- Add D365 link to trusted sites as well as likely will be next issue 
- Try adding trailing slash '/' to see if behavior changes.  
Verify AD FS Manager > AD FS > Application Groups. Double click on Microsoft Dynamics 365 for Operations On-premises. Under Native application, double click on Microsoft Dynamics 365 for Operations On-premises - Native application 

- Note Redirect URI. This should match what DNS forward lookup zone is for AX 

Could not establish trust relationship for the SSL/TLS secure channel 

- Look in Service Fabric > Cluster > Applications > AXSFType > fabric:/AXSF > details tab and Aad_AADMetadataLocationFormat /     - Aad_FederationMetadataLocation. Browse to that URL from AOS.  
- Look in AOS Event Viewer > Applications and Services Logs > Microsoft > Dynamics > AX-SystemRuntime for details 
- Check to see if ADFS cert is trusted 
    - Verify ADFS cert by going to ADFS machine > Server Manager > Tools > AD FS Management 
    - Expand AD FS > Service > Certificates and note certs (ex. dc1.contoso.com) 
    - On AOS machine go to cert manager > Certificates (Local Computer) > Trusted Root Certification Authorities > Certificates  and verify that the ADFS cert is listed (ex. dc1.contoso.com) 

If you receive a message that states that the site isn't secure, you haven't added your AD FS SSL certificate to the Trusted Root Certification Authorities store 

Unable to connect to the remote server 

- at System.Net.HttpWebRequest.GetResponse() 
- at System.Xml.XmlDownloadManager.GetNonFileStream(Uri uri, ICredentials credentials, IWebProxy proxy, RequestCachePolicy cachePolicy) 
- at System.Xml.XmlUrlResolver.GetEntity(Uri absoluteUri, String role, Type ofObjectToReturn) go to C:\ProgramData\SF\AOS_1\Fabric\work\Applications\AXSFType_App35\log folder you get the err and out files. 

The out file contains the info: 

- System.Net.WebException: Unable to connect to the remote server ---> System.Net.Sockets.SocketException: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond x.x.x.x:443 
- Psping, IP and see if reachable  

Redirect login questions/issues 

- Verify in Service Fabric Explorer that Provisioning_AdminPrincipalName and Provisioning_AdminIdentityProvider is valid. If not then cannot proceed and will need to redeploy from LCS. 

    - Following example will reference https://DC1.contoso.com/adfs	and AXServiceUser@contoso.com 
    - Provisioning_AdminIdentityProvider would be https://DC1.contoso.com/adfs 
    - Provisioning_AdminPrincipalName would be AXServiceUser@contoso.com 

- If used Reset-DatabaseUsers.ps1 note need to restart AX Service to take effect 
- If still not working, then  
    - Note USERINFO table, specifically NETWORKDOMAIN, NETWORKALIAS 
    - NETWORKDOMAIN example https://DC1.contoso.com/adfs 
    - NETWORKALIAS example AXServiceUser@contoso.com 
    - In ADFS machine > Server Manager > Tools > AD FS Management > Service, right click on Service and Edit Federation Service Properties 
    - Note Federation Service identifier. This should match to USERINFO.NETWORKDOMAIN (https://DC1.contoso.com/adfs) 
    - Make sure both are https (ex. not http in ADFS but https in USERINFO) 

In ADFS machine go to **Event Viewer** > **Applications and Services Logs** > **AD FS** > **Admin note any errors**.

### Login issues / Reset user 
Verify in Service Fabric Explorer that Provisioning_AdminPrincipalName and Provisioning_AdminIdentityProvider is valid. If so then on    
           - SQL primary box run .\Reset-DatabaseUsers.ps1 
On each AOS, open Task Manager and end task on AXService.exe 
Can verify user has been set via running following select in SQL AXDB  

            - select SID, NETWORKDOMAIN, NETWORKALIAS, * from AXDB.dbo.USERINFO where id = 'admin' 
            
Note on SIDs 

- SID in AAD environment (online) is a hash of network alias, network domain 
- SID in AD environment (on-premises) is a hash of network alias, identify provider 

If still can't log in due to "You are not authorized to login with your current credentials. You will be redirected to the login page in a few seconds" then see ADFS section 

### System.Data.SqlClient.SqlException (0x80131904) and System.ComponentModel.Win32Exception (0x80004005)

System.Data.SqlClient.SqlException (0x80131904): A connection was successfully established with the server, but then an error occurred during the login process. (provider: SSL Provider, error: 0 - The certificate chain was issued by an authority that is not trusted.)  

System.ComponentModel.Win32Exception (0x80004005): The certificate chain was issued by an authority that is not trusted 


The certificates have not been installed or given access to the correct users 
Add the public key SQL server certificate on all the service fabric nodes 

### Keyset does not exist 
Didn’t run scripts on all machines as per instructions. Go back and review Install Certificates section. Copy the scripts in each folder to the VMs that correspond to the folder name. 

Also check csv file for correct domain being used 

## Error: RunAsync failed due to an unhandled FabricException causing replica to fault
"RunAsync failed due to an unhandled FabricException causing replica to fault: System.Fabric.FabricException: The first Fabric upgrade must specify both the code and config versions. Requested value: 0.0.0.0: 

Change ClusterConfig.json diagnosticsStore from network share to local path, ex \\server\path to default of c:\\ProgramData\\SF\\DiagnosticsStore 

## Error: Dbsync (DB sync) issues 
If you are having database sync issues, look at AOS working directory, ex C:\ProgramData\SF\AOS1\Fabric\work\Applications\AXSFType_App8\log and complete a review of the following on all AOS machines:  

- **Event Viewer** > **Custom Views** > **Administrative Events** 
- **Event Viewer** > **Applications and Services Logs** > **Microsoft** > **Dynamics** > **AX-DatabaseSynchronize** 

## Error: "Invalid algorithm specified / Cryptography"  
If you receive this error, you need to be using the Provider of Microsoft Enhanced RSA and AES Cryptographic Provider. For more information, review the certificates requirements. Additionally, verify that the structure of the Credentials.json file is correct. 

### Error: "Partition is below target replica or instance count" 
This is not a root error. This error means that the status of each node is not ready. For AXSF/AOS, the status could still be inBuild. 
Navigate to the Event Viewer to get root error. You can also find it here, c:\ProgramData\SF… 

## Error, "Unable to find certificate" when running Test-D365FOConfiguration.ps1 
If you receive this error, check to see if certs/thumbprints are being combined for multiple purposes. For example, if the client and SessionAuthentication is combined, you will receive this error. We recommend that you do not to combine certificates. For more information, see the certificate requirements and check acl.csv for domain.com\user vs. domain\user (ex. NETBIOS structure). 

## The client and server can't communicate because they do not possess a common algorithm 
Verify the star certificate requirements, example provider being used 
 
## Find a list of group managed service accounts (gMSA)
To find a list of all groups and hosts, [Get-ADServiceAccount -Identity svc-LocalAgent$ -Properties *] 
PrincipalsAllowedToRetrieveManagedPassword 

## AddCertToServicePrincipal script failing on Import-Module 
AddCertToServicePrincipal script failing on Import-Module : Could not load file or assembly 'Commands.Common.Graph.RBAC, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. Strong name validation failed. (Exception from HRESULT: 0x8013141A) may have multiple versions of the same module installed.  

To resolve this issue, run the following command in PowerShell 
        
        Uninstall-Module -Name AzureRM  
        Install-Module AzureRM 

Then, close the PowerShell window and try again.

## ReportingServicesSetup.exe Error
ReportingServicesSetup.exe Error: 0 : Application fabric:/ReportingService is not OK after 10 minutes 
Application: ReportingServicesBootstrapper.exe 
Framework Version: v4.0.30319 
Description: The process was terminated due to an unhandled exception. 

If you receive this error, the strong name validation is enabled in the Reporting server and should not be. To resolve this, run the config-PreReq script in Reporting server machine. 

## The requested operation requires elevation 
AOS users are not in the local administrator group and the UAC has not been disabled correctly. To resolve the issue, complete the following steps. 
1. Add AOS users as local admins as described in the section Join VMs to the domain 
2. Run the Config-PreReq script on all the AOS machines 
3. Make sure Test-Configuration script passes 
4. If UAC was changed, need to restart machine to take effect 

## Files in use errors
Set up exclusion rules advised by Service Fabric. For information, see [Plan and prepare your Service Fabric Standalone cluster deployment](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation).



 





 
