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

This topic provides troubleshooting information for on-premises deployments of Dynamics 365 for Finance and Operations, Enterprise edition.

## Service Fabric 
Service Fabric is one of the initial components to install and configure for your on-premises deployment. Service Fabric is used by the Orchestrator, Application Object Server (AOS), SSRS and MR nodes.

## Access Service Fabric Explorer
Service Fabric Explorer can be accessed by using a browser and the default address, https://sf.d365ffo.onprem.contoso.com:19080. 

To verify the address, note what was used in the topic, [Create DNS zones and add A records](setup-deploy-on-premises-environments.md#createdns). 
To access the site, the client certificate needs to be in cert:\CurrentUser\My (**Certificates - Current User** > **Personal** > **Certificates**) of the machine that is accessing the site. When you access the site, select the client certificate when prompted.

## Stateful and stateless services, how to identify nodes for log review 
To determine what machine is the primary instance for stateful services, like a local agent, go to Service Fabric Explorer, expand **Cluster** > **Applications** > **(intended application ex) LocalAgentType** > **fabric:/LocalAgent** > **Fabric:/LocalAgent/ArtifactsManager** > **(guid)**. 

Note the primary node. For stateless services, or the rest of the applications, you need to check all of the nodes. 

## Timeout error received when creating a Service Fabric cluster 
Run Test-D365FOConfiguration.ps1 as noted in [Set up a standalone Service Fabric cluster](setup-deploy-on-premises-environments.md#setupsfcluster) and note any errors. 
Verify that the Service Fabric Server client certificate exists in the LocalMachine store on all service fabric nodes. 
Verify that the Service Fabric Server certificate has the ACL for Network Service on all service fabric nodes.

## Time out while waiting for Installer Service to complete for machine x.x.x.x
You can only have one node type for each IP address (machine). Check to see if the nodes are being reused on the same machine. For example, AOS and ORCH must be on the same machine and ConfigTemplate.xml must be correctly defined. 

## Remove a specific application 
We recommend that you use Lifecycle Services (LCS) to remove or clean up deployments. However, if additional steps are needed, you can use Service Fabric Explorer to remove an application.  

In Service Fabric Explorer, go to **Application node** > **Applications** > **MonitoringAgentAppType-Agent**. Click the ellipses by **fabric:/Agent-Monitoring** and delete the application. Enter the full name of the application to confirm. 
You can also remove the **MonitoringAgentAppType-Agent** by clicking the ellipses and then **Unprovision Type**. Enter the full name to confirm. 

## Remove Service Fabric 
To remove the Service Fabric completely, remove ServiceFabricCluster.ps1 -ClusterConfigFilePath "<path to working directory>\ClusterConfig.json". If this results in an error, remove a specific node on that cluster from the
powershell.exe -File "C:\Program Files\Microsoft Service Fabric\bin\fabric\fabric.code\CleanFabric.ps1. 

Next, remove the folder c:\ProgramData\SF, if using the default. Otherwise, remove the specified folder. 
If you receive an access denied error, restart PowerShell or restart the machine. 

## Local agent 
Local agent is the framework that is responsible for communicating with LCS, downloading components to be installed, installation, and maintaining and removing Dynamics 365 for Finance and Operations, Enterprise edition. 

## How to find the local agent values that are used 
Local agent values can be found in Service Fabric Explorer under **Cluster** > **Applications** > **LocalAgentType** > **fabric:/LocalAgent, Details**.

## Install, upgrade, or uninstall local agent 
Local agent installation is discussed in the topic, [Set up and deploy on-premises environments](setup-deploy-on-premises-environments.md). You can also use the following upgrade and uninstall commands: 

    LocalAgentCLI.exe Install <path of localagent-config.json> 
    LocalAgentCLI.exe Upgrade <path of localagent-config.json> 
    LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    
> [!NOTE]
    > The cleanup command doesn't remove any of the files that were placed in the file share. The file share can be reused.

## Error occurs when starting up local agent services  
If you receive the error, "Could not load file or assembly 'Lcs.DeploymentAgent.Proxy.Contract, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies", this means that the **Strong name** verification should no longer be enabled. This is done by using Configure-PreReqs.ps1. To validate that the verification is no longer enabled, run Test-D365FOConfiguration.ps1.

## "Validation in progress" message displays for several minutes in LCS
Complete the following steps to troubleshoot general issues with local agent validation.
1. Run Configure-PreReqs.ps1 on all the Orchestrator machines to configure the machines correctly. 
2. Verify that the script Test-D365FOConfiguration.ps1 passes on all of the Orchestrator machines.  
3. Verify that the installation of LocalAgentCLI.exe completed successfully. 
4. Go to Service Fabric Explorer and verify that the applications are all healthy. 
5. If the applications are not healthy, locate the primary node for the failing service. 
   Look for events in:
   
   - **Event Viewer** > **Custom Views** > **Administrative Events** 
   - **Event Viewer** > **Applications and Services Log** > **Microsoft** > **Dynamics** > **AX-LocalAgent** 

**Common errors**

The following are common errors that you may encounter:

- "Unable to process commands" or "Unable to get the channel information"
- "RunAsync failed due to an unhandled exception causing the host process to crash: System.ArgumentNullException: Value cannot be null. Parameter name: certificate" 

**Reason**
These errors may occur because the certificate specified for the OnPremLocalAgent certificate is not valid or is not configured correctly for the tenant. 

**Steps** 
Complete the following steps to resolve the error.
1. Run Test-D365FOConfiguration.ps1 on all Orchestrator nodes to ensure all checks pass. 
2. Verify that the certificate specified in local agent configuration is correct.  

- Make sure there are no special characters while specifying the thumbprint in LCS and the ConfigTemplate.xml. 
- The certificate should be the same as what is specified in infrastructure\ConfigTemplate.xml for the following.
    
        <Certificate type="Orchestrator" exportable="true" generateSelfSignedCert="true"> 
          <Name>OnPremLocalAgent</Name> 
          <Thumbprint></Thumbprint> 
          <ProtectTo></ProtectTo> 
        </Certificate> 
3. Ensure that the steps in [Configure LCS connectivity for the tenant](setup-deploy-on-premises-environments.md#configurelcs) were completed using the same certificate that is specified in the local agent configuration in LCS. 
4. Uninstall the local agent.  
5. Specify the correct certificate in the local agent configuration and download the configuration file again. 
6. Install the local agent again with the new configuration file. 

**Error** 
Access to the path '\\...\agent\assets\StandAloneSetup-76308-1.zip' is denied. 

**Reason**
The file share specified in local agent configuration is not valid. 

**Steps** 
Complete the following steps to resolve the error.
1. Verify that the specified share exists. 
2. Verify that the local agent user has full permission on the share. The local agent user is the DNS name specified in ConfigTemplate.xml in the following section. 
  
          <ADServiceAccount type="gMSA" name="svc-LocalAgent$" refName="gmsaLocalAgent"> 
              <DNSHostName>svc-LocalAgent.d365ffo.onprem.contoso.com</DNSHostName> 
          </ADServiceAccount> 
          
3. Ensure that the Setup file share section in the setup document is completed. 
4. Uninstall the local agent.  
5. Specify the correct file share in local agent configuration and download the configuration file again. 
6. Install local agent again with the new configuration file. 

**Error** 
Login failed for user 'D365\svc-LocalAgent$'. Reason: Could not find a login matching the name provided. [CLIENT: 10.0.2.23]  

**Reason**
The local agent user is not able to connect to the orchestration database. This could happen because users may have been deleted and then recreated in the AD, which means the SID of the user has changed. Any access given to the user for the SQL Server or database will no longer work. 

**Steps**
Complete the following steps to resolve the error.
1. Run the script on the SQL server.

        .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
        
This creates an empty Orchestrator database, if one does not already exist, and adds the local agent user to the database with db_owner permission.

2. The application should automatically go to healthy state after the correct permissions are provided. 
3. If any of the settings, such as the SQL FQDN, database name, and local agent user was provided incorrectly in LCS, change the settings and reinstall local agent. 
4. If the first three steps do not resolve the issue, manually remove the local agent user from the SQL server and the database, and then re-run the Initialize-Database script. 
5. If you recreate a user in AD, remember that the SID will change. Remove the previous SID for the user and add a new SID. 

**Additional scenario**
The local agent user can't connect to the SQL server or database. 

**Steps** 
Complete the following steps to resolve the error.
1. Delete the svc-LocalAgent user from the SQL server primary node databases and then remove the login from both servers.  
2. Run the following scripts. 

        .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
        .\Configure-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
        
  These scripts do not work with **always-on** setup. The database needs to be created first in the primary node and then replicated.  

**Error** 
RunAsync failed due to an unhandled exception causing the host process to crash: System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: The remote name could not be resolved: 'lcsapi.lcs.dynamics.com' 

**Reason** 
The local agent machines can't connect to lcsapi.lcs.dynamics.com. Review the AX-BridgeService event log for "The remote name could not be resolved: 'lcsapi.lcs.dynamics.com'".  

**Steps** 
Complete the following steps to resolve the error.
1. Run [psping lcsapi.lcs.dynamics.com:80].  
2. If you don't receive a reply, contact the IT department at your organization. The firewall is blocking access to lcsapi or proxy issues.

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

## Error "Unable to load DLL 'FabricClient.dll'"
If you receive this error, close and reopen PowerShell. If the error still occurs, restart the machine. 

## What Cluster ID in Agent config should be used 
The Cluster ID can be any GUID. This GUID is used for tracking purposes. 

## Local agent stops working after the tenant for the project from LCS is changed 
Complete the following steps to configure local agent with updated tenant.  
1. Remove all of the environments from LCS that already have the connector installed. 
2. Uninstall the local agent. 

        .\LocalAgentCLI.exe Cleanup <path of localagent-config.json> 
        
3. Complete the steps in step [11. Configure LCS connectivity for the tenant](setup-deploy-on-premises-environments.md#configurelcs). 
4. Create a new LCS connector in the new tenant. 
5. Download the local-agent.config file. 
6. Install local agent. 
   
        .\LocalAgentCLI.exe Install <path of localagent-config.json>
        
## Monitor deployment locally 
Review the event viewer logs for the primary orchestrator machine and artifacts manager, and the bridge service 
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

## To view the entire error message
Click the **Details** tab to view the full error message. 

## Service Fabric failing
Note the service that is failing and open the corresponding application directory. For example, C:\ProgramData\SF\ORCH1\Fabric\work\Applications\LocalAgentType_App5\log.

## Encryption errors
Some encryption error examples include, AXBootStrapperAppType, Bootstrapper, AXDiagnostics, RTGatewayAppType, Gateway potential failure related, and Microsoft.D365.Gateways.ClusterGateway.exe.

You might receive one of these errors if the data encipherment certificate is used to encrypt AOS AccountPassword was not installed on the machine. This certificate could be in the certificates (local computer) or it could be that the provider type is incorrect. 

To resolve the error, validate the credentials.json file. Verify that the text is decrypting correctly by entering the following message (on AOS1). 

        Invoke-ServiceFabricDecryptText -CipherText 'longstring' -StoreLocation LocalMachine | clip 

This error may also occur if the parameter **''** is not defined in the ApplicationManifest file. To verify this, go to **Event Viewer** > **Custom Views** > **Administrative Events** and check for the following:

- Proper layout/structure of credentails.json file encrypt credentials. For more information, see [Encrypt credentials](setup-deploy-on-premises-environments.md#encryptcred). 
- An end quote at the end of the line or on the next line. 
- Error on Microsoft-Service Fabric source.
    
## Can't find the certificate and private key to use for decryption (0x8009200C) 
If you are missing a certificate and ACL, or you have the wrong thumbprint entry, check for special characters and check in C:\ProgramData\SF\AOS1\Fabric\work\Applications\AXBootstrapperAppType_App9\log\ConfigureCertificates….txt for thumbprints.  

You can also test by using the Invoke-ServiceFabricDecryptText -CipherText 'longstring' -StoreLocation LocalMachine | clip. If you receive the message, "Cannot find the certificate and private key to use for decryption", verify axdataenciphermentcert and svc-AXSF$ AXServiceUser ACL. 
If the credentials.json have changed, delete and redeploy from LCS. 

## MR
Additional logging can be done by registering providers. Download the [ETWManifest.txt](https://go.microsoft.com/fwlink/?linkid=864672) to the primary orchestrator machine and run the following commands.  

    .\RegisterETW.ps1 -ManifestsAndDll @{"C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.man" =    "C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.dll"} 

If you need to un-register, use the following command.

    .\RegisterETW.ps1 -ManifestsAndDll @{"C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.man" = "C:\Files\ETWManifest\Microsoft.Dynamics.Reporting.Instrumentation.dll"} -Unregister  

After providers are registered, additional details will be logged about the new deployment in **Event Viewer** > **Applications and Services Logs** > **Microsoft** > **Dynamics**. 

- MR-Logger 
- MR-Sql 
    
### Error while executing AddAXDatabaseChangeTracking
If you encounter an error while executing AddAXDatabaseChangeTracking at Microsoft.Dynamics.Performance.Deployment.FinancialReportingDeployer.Utility.InvokeCmdletAndValidateSuccess(DeploymentCmdlet cmdlet), verify that the full path is correct. For example, ax.d365ffo.onprem.contoso.com.
The error may have also occurred because of an issue with the star/* certificate. For example, the remote certificate CN=\*.d365ffo.onprem.contoso.com has a name that is not valid or does not match the host ax.d365ffo.onprem.contoso.com.  

### Remote name can't be resolved
The remote name could not be resolved: 'x.d365fo.onprem.contoso.com' / There was no endpoint listening at https://x.d365fo.onprem.contoso.com/namespaces/AXSF/services/MetadataService that could accept the message. This is often caused by an incorrect address or SOAP action. Verify that the address is reachable by manually browsing to the URL. See InnerException, if present, for more details. 
  
### Run initialize database script and validate DBs have correct users 
If you only receive the AddAXDatabaseChangeTracking event, try to reach the Metadataservice of Dynamics 365 for Finance and Operations by going to 
https://ax.d365ffo.contoso.com/namespaces/AXSF/services/MetadataService. 
Next, check the certificates of the service in the wif.config file. To find the file, log on to one of the AOS boxes and, using Task manager, locate **AxService.exe**, right-click and select **Open file location**. In the wif.config file, you should see 3 thumbprints. Note the following requirements for these thumbprints: 

- They need to be different. 
- They need to be in this order: 
    1. Financialreporting Thumbprint 
    2. ReportingService Thumbprint 
    3. SessionAuthentication Thumbprint 
    
If the thumbprints do not follow the list of requirements, you must redeploy from LCS with proper thumbprints. 

## Unable to resolve the xPath value 
Not being able to resolve the xPath value of [TopologyInstance/CustomizationGroup[@name='ServiceConfiguration']/Group[@name='AOSServicePrincipalUser']/Customizations/Customization[@fieldName='PrincipalUserAccountPassword']/@selectedValue is expected behavior and is not an issue. The xPath value is looking for AOS runtime user information, however, because of integrated security, the information is not needed. The inability to resolve the xPath is communicated in case the failure needs to be investigated for another reason.  

## ADFS
### Login page not redirecting
If the Login page is not redirecting and is still prompting for credentials, or you are being redirected but receive the message, "An error occurred. Contact your administrator for more information.", you can do the following to resolve the issue:

- Add ADFS link to trusted sites.
- Add Dynamics 365 link to trusted sites.
- Try adding a trailing slash '/' to see if the behavior changes.

Verify the AD FS Manager by going to **ADFS** > **Application groups**. Double-click **Microsoft Dynamics 365 for Operations on-premises**. Under **Native application**, double-click **Microsoft Dynamics 365 for Operations on-premises - Native application**.
- Note the Redirect URI. It should match the DNS forward lookup zone for Finance and Operations. 

### Error "Could not establish trust relationship for the SSL/TLS secure channel"
If you receive the error, "Could not establish trust relationship for the SSL/TLS secure channel", do the following: 

1. Go to **Service Fabric** > **Cluster** > **Applications** > **AXSFType** > **fabric:/AXSF** > **Details** tab and Aad_AADMetadataLocationFormat / - Aad_FederationMetadataLocation. Next, browse to that URL from AOS.  
2. Go to **AOS Event Viewer** > **Applications and Services Log**s > **Microsoft** > **Dynamics** > **AX-SystemRuntime** for details. 
3. Check to see if ADFS certificate is trusted:
    1. Verify ADFS certificate by going to **ADFS machine** > **Server Manager** > **Tools** > **AD FS Management**. 
    2. Expand **AD FS** > **Service** > **Certificates** and note the certificates. For example, ex. dc1.contoso.com. 
    3. On the AOS machine, go to the Cert manager, **Certificates** (Local Computer) > **Trusted Root Certification Authorities** > **Certificates**  and verify that the ADFS certificate is listed.
If you receive a message that the site isn't secure, this is because you haven't added your AD FS SSL certificate to the Trusted Root Certification Authorities store. 

### Can't connect to remove server in some locations
If you are unable to connect to the remote server at the following places:

- System.Net.HttpWebRequest.GetResponse() 
- System.Xml.XmlDownloadManager.GetNonFileStream(Uri uri, ICredentials credentials, IWebProxy proxy, RequestCachePolicy cachePolicy) 
- System.Xml.XmlUrlResolver.GetEntity(Uri absoluteUri, String role, Type ofObjectToReturn) 
Go to the C:\ProgramData\SF\AOS_1\Fabric\work\Applications\AXSFType_App35\log folder where you get the error and out files. 
The out file contains the following information: 

- System.Net.WebException: Unable to connect to the remote server ---> 
- System.Net.Sockets.SocketException: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond x.x.x.x:443 

You can also use Psping to try to reach the remove server. For information about Psping, see [Psping](https://docs.microsoft.com/en-us/sysinternals/downloads/psping).  

### Redirect login questions and issues 
If you are having issues with login, verify in Service Fabric Explorer that the **Provisioning_AdminPrincipalName** and **Provisioning_AdminIdentityProvider** are valid. For example,

- **Provisioning_AdminPrincipalName** would be AXServiceUser@contoso.com 
- **Provisioning_AdminIdentityProvider** would be https://DC1.contoso.com/adfs 
   
If they are not valid, you will not be able to proceed and you will need to redeploy from LCS. 

If you used **Reset-DatabaseUsers.ps1**, you will need to restart the Dynamics Service for your changes to take effect. If you are still having login issues, in the **USERINFO** table, note the **NETWORKDOMAIN** and **NETWORKALIAS**. For example, 

-  NETWORKDOMAIN example https://DC1.contoso.com/adfs 
- NETWORKALIAS example AXServiceUser@contoso.com 

In the ADFS machine, go to **Server Manager** > **Tools** > **AD FS Management** > **Service**. Right-click **Service and Edit Federation Service Properties**. Note the Federation Service identifier, which should match the **USERINFO.NETWORKDOMAIN (https://DC1.contoso.com/adfs)**. Verify that both are HTTPS in **USERINFO**. 

In the ADFS machine, go to **Event Viewer** > **Applications and Services Logs** > **AD FS** > **Admin** and note any errors.

## Login issues 
If you or others are experiencing login issues, verify in Service Fabric Explorer that Provisioning_AdminPrincipalName and Provisioning_AdminIdentityProvider is valid. If it is valid, then on the primary SQL Server machine, run the following.    

            - .\Reset-DatabaseUsers.ps1 
On each AOS, open Task Manager, select AXService.exe, and then click **End task**. 
To verify that a user has been reset, run the following select query in the SQL AXDB. 

            - select SID, NETWORKDOMAIN, NETWORKALIAS, * from AXDB.dbo.USERINFO where id = 'admin' 
            
  > [!NOTE] SID in AAD environment (online) is a hash of network alias and network domain. SID in AD environment (on-premises) is a hash of network alias and identify provider.

If you are still unable to log in and you are receiving the error, "You are not authorized to login with your current credentials. You will be redirected to the login page in a few seconds", see the section, [ADFS](#ADFS) in this topic. 

## System.Data.SqlClient.SqlException (0x80131904) and System.ComponentModel.Win32Exception (0x80004005)
If you receive one of the following errors: 

- System.Data.SqlClient.SqlException (0x80131904): A connection was successfully established with the server, but then an error occurred during the login process. (provider: SSL Provider, error: 0 - The certificate chain was issued by an authority that is not trusted.)  
- System.ComponentModel.Win32Exception (0x80004005): The certificate chain was issued by an authority that is not trusted 

The certificates have not been installed or given access to the correct users. To resolve this error, add the public key SQL server certificate to all of the Service Fabric nodes. 

## Keyset doesn't exist 
If you find that the keyset doesn't exist, this means that scripts were not run on all machines. Review and complete [Set up VMs](setup-deploy-on-premises-environments.md#setupvms). Copy the scripts in each folder to the VMs that correspond to the folder name. 

Also check the .csv file to verify that the correct domain is being used. 

## Error "RunAsync failed due to an unhandled FabricException causing replica to fault"
If you receive this error, "RunAsync failed due to an unhandled FabricException causing replica to fault: System.Fabric.FabricException: The first Fabric upgrade must specify both the code and config versions. Requested value: 0.0.0.0:", change the ClusterConfig.json diagnosticsStore from network share to local path such as, \\server\path to default of c:\\ProgramData\\SF\\DiagnosticsStore. 

## Error Dbsync (DB sync) issues 
If you are having database sync issues, look at AOS working directory, ex C:\ProgramData\SF\AOS1\Fabric\work\Applications\AXSFType_App8\log and complete a review of the following on all AOS machines:  

- **Event Viewer** > **Custom Views** > **Administrative Events** 
- **Event Viewer** > **Applications and Services Logs** > **Microsoft** > **Dynamics** > **AX-DatabaseSynchronize** 

## Error "Invalid algorithm specified / Cryptography"  
If you receive this error, you need to be using the Microsoft Enhanced RSA and AES Cryptographic Provider. For more information, review the certificates requirements. Additionally, verify that the structure of the credentials.json file is correct. 

### Error "Partition is below target replica or instance count" 
This is not a root error. This error means that the status of each node is not ready. For AXSF/AOS, the status could still be inBuild. 
Navigate to the Event Viewer to get root error. You can also find it here, c:\ProgramData\SF… 

## Error "Unable to find certificate" when running Test-D365FOConfiguration.ps1 
If you receive this error, check to see if certificates/thumbprints are being combined for multiple purposes. For example, if the client and SessionAuthentication is combined, you will receive this error. We recommend that you do not to combine certificates. For more information, see the certificate requirements and check acl.csv for domain.com\user vs. domain\user (ex. NETBIOS structure). 

## Client and server can't communicate because they do not have a common algorithm 
If this occurs, verify that the certificates created are using the specified provider as explained in step [2. Plan and acquire your certificates](setup-deploy-on-premises-environments.md#plancert).
 
## Find a list of group managed service accounts (gMSA)
To find a list of all groups and hosts, see [Get-ADServiceAccount -Identity svc-LocalAgent$ -Properties] 
PrincipalsAllowedToRetrieveManagedPassword 

## AddCertToServicePrincipal script failing on Import-Module 
AddCertToServicePrincipal script failing on Import-Module : Could not load file or assembly 'Commands.Common.Graph.RBAC, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. Strong name validation failed. (Exception from HRESULT: 0x8013141A) may have multiple versions of the same module installed.  

To resolve this issue, run the following command in PowerShell. 
        
        Uninstall-Module -Name AzureRM  
        Install-Module AzureRM 

Close the PowerShell window and try again.

## ReportingServicesSetup.exe Error
ReportingServicesSetup.exe Error: 0 : Application fabric:/ReportingService is not OK after 10 minutes 
Application: ReportingServicesBootstrapper.exe 
Framework Version: v4.0.30319 
Description: The process was terminated due to an unhandled exception. 

If you receive this error, the strong name validation is enabled in the Reporting server and should not be. To resolve this, run the config-PreReq script on the Reporting server machine. 

## Requested operation requires elevation 
AOS users are not in the local administrator group and the UAC has not been disabled correctly. To resolve the issue, complete the following steps. 
1. Add AOS users as local admins as described in the section "Join VMs to the domain." 
2. Run the Config-PreReq script on all the AOS machines. 
3. Make sure Test-Configuration script passes. 
4. If UAC was changed, you need to restart the machine to take effect. 

## Files in use errors
Set up exclusion rules that are advised by Service Fabric. For information, see [Plan and prepare your Service Fabric Standalone cluster deployment](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation).

