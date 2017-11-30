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
Service Fabric is one of the initial components to install and configure for your on-premises deployment. Service Fabric is used by Orchestrator, AOS, SSRS and MR nodes.

### How to access Service Fabric Explore
Service Fabric Explorer can be accessed via browser (default address of) https://sf.d365ffo.onprem.contoso.com:19080. To verify address note what was used in 4. Create DNS zones and add A records 
To access site, the client certificate needs to be in cert:\CurrentUser\My (Certificates - Current User > Personal > Certificates) of the machine accessing this site 
When accessing site, select the client certificate when prompted

### Stateful and Stateless Services, how to identify nodes for log review 
For Stateful Services (ex. Local Agent), to find out what machine is the primary instance, go to Service Fabric Explorer, expand Cluster > Applications > (intended application ex) LocalAgentType > fabric:/LocalAgent > Fabric:/LocalAgent/ArtifactsManager > (guid). Note primary node 
For Stateless Services (rest of applications), need to check all nodes 

### Receiving timeout error when creating Service Fabric cluster 
Run Test-D365FOConfiguration.ps1 as noted in Set up a standalone Service Fabric cluster and note any errors 
Ensure the Service fabric Server certificate, client certificate exists in LocalMachine store on ALL service fabric nodes 
Ensure the Service fabric Server certificate has the ACL for Network Service on ALL service fabric nodes 

### Time out waiting for Installer Service to complete for machine x.x.x.x
Can only have 1 node type for each IP address (machine). Check to see if nodes are being reused on same machine (ex AOS and ORCH on same machine) and ConfigTemplate.xml is incorrectly defined. 

### How to remove a specific application 
Advised to use LCS to remove or cleanup deployments but if additional steps are needed can use Service Fabric Explorer to remove an application having issues.  
In Service Fabric Explorer, go to Application node, ex. Cluster > Applications > MonitoringAgentAppType-Agent. Click ellipse by fabric:/Agent-Monitoring and Delete Application. Enter in full name to confirm. 
Can also remove MonitoringAgentAppType-Agent by clicking on ellipse and Unprovision Type. Enter in full name to confirm. 

### How to remove Service Fabric completely 
RemoveServiceFabricCluster.ps1 -ClusterConfigFilePath "<path to working directory>\ClusterConfig.json" 
If results in error removing a specific node of cluster from following on that cluster 
powershell.exe -File "C:\Program Files\Microsoft Service Fabric\bin\fabric\fabric.code\CleanFabric.ps1" 

Remove c:\ProgramData\SF folder (if using default, otherwise manually specified folder) 
If receive access denied error, restart PowerShell and try otherwise restart machine 

## LocalAgent 
LocalAgent is the framework that is responsible for communicating with LCS, downloading components to install, installing, maintaining and removing Dynamics. 

### How to find LocalAgent values used 
Values can be found in Service Fabric Explorer > Cluster > Applications > LocalAgentType > fabric:/LocalAgent, Details section

### Install, Upgrade, Uninstall Local agent 
Local agent install is discussed in deployment guide. Additionally can use upgrade and uninstall commands. 
    LocalAgentCLI.exe Install <path of localagent-config.json> 
    LocalAgentCLI.exe Upgrade <path of localagent-config.json> 
    LocalAgentCLI.exe Cleanup <path of localagent-config.json> 
Note cleanup command does not remove any of the files that were placed in the file share. File share can be reused 

### On startup of Local agent services and error  
Could not load file or assembly 'Lcs.DeploymentAgent.Proxy.Contract, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies 
Strong name verification needs to be disabled. This is done via Configure-PreReqs.ps1 
Run Test-D365FOConfiguration.ps1 to validate 

### LCS is showing Validation in progress for a period of time (ex. several minutes) 
General steps to troubleshoot issues with local agent validation.
1. Run the Configure-PreReqs.ps1 on all the orchestrator machines to configure the machines correctly. 
2. Ensure that the script Test-D365FOConfiguration.ps1 passes on all the orchestrator machines  
3. Ensure that the LocalAgentCLI.exe install completed successfully 
4. Go to Service Fabric Explorer and make sure that the applications are all Healthy 
5. If the applications are not healthy, Locate the primary node for the failing service. 
   Look for events in:  
   Event Viewer > Custom Views > Administrative Events 
   Event Viewer -> Applications and Services Log -> Microsoft -> Dynamics -> AX-LocalAgent 

**Common errors**
Receiving 'Unable to process commands' and/or 'Unable to get the channel information' messages 
 
"RunAsync failed due to an unhandled exception causing the host process to crash: System.ArgumentNullException: Value cannot be null. Parameter name: certificate 

**Reason**
The certificate specified for OnPremLocalAgent certificate is invalid or not configured correctly for the tenant. 

**Steps** 
1. Run Test-D365FOConfiguration.ps1 on all Orchestrator nodes to ensure all checks pass 
2. Verify that the certificate specified  in local agent configuration is correct.  
Make sure there are no special characters while specifying the thumbprint in LCS and the ConfigTemplate.xml 
The certificate should be the same as what is specified in infrastructure\ConfigTemplate.xml for  
    <Certificate type="Orchestrator" exportable="true" generateSelfSignedCert="true"> 
      <Name>OnPremLocalAgent</Name> 
      <Thumbprint></Thumbprint> 
      <ProtectTo></ProtectTo> 
    </Certificate> 
3. Ensure that the steps in Configure LCS connectivity for the tenant section were completed using the same certificate specified in local agent configuration in LCS. 
4. Uninstall the local agent  
5. Specify the correct certificate in local agent configuration and download the configuration file again 
6. Install local agent again with the new configuration file. 

**Error event:** 
Access to the path '\\...\agent\assets\StandAloneSetup-76308-1.zip' is denied 

**Reason**
The file share specified in local agent configuration is invalid. 

**Steps** 
1. Ensure that the share specified exists 
2. Ensure that the local agent user has Full permission on the specified share. The local agent user is the DNS name specified in ConfigTemplate.xml in the section, 
  <ADServiceAccount type="gMSA" name="svc-LocalAgent$" refName="gmsaLocalAgent"> 
      <DNSHostName>svc-LocalAgent.d365ffo.onprem.contoso.com</DNSHostName> 
  </ADServiceAccount> 
3. Ensure that the Setup file share section in setup document is completed. 
4. Uninstall the local agent  
5. Specify the correct file share in local agent configuration and download the configuration file again 
6. Install local agent again with the new configuration file. 

**Error event:** 
Login failed for user 'D365\svc-LocalAgent$'. Reason: Could not find a login matching the name provided. [CLIENT: 10.0.2.23]  

**Reason**
The local agent user is unable to connect to the orchestration database. Possibly users may have been deleted and recreated in the AD. The SID of hte user has changed. Any access given to the user for the SQL Server or database will no longer work. 

**Steps**
1. Run the script on the SQL server 
   .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
  This creates an empty orchestrator database if it does not exist and adds the local agent user to the database with db_owner permission 
2. The application should automatically go to healthy state once the right permissions are provided. 
3. If any of the settings such as the SQL FQDN, Database name and local agent user was provided incorrectly in LCS, change the settings and reinstall local agent. 
4. If step 1,2 does not solve the issue, manually remove the local agent user from the SQL server and the database and re-run the Initialize-Database script. 
5. If recreating users in AD, SID changing. Need to remove old user/SID and add new user/SID 

**Additional scenario**
Local agent user is unable to connect to the SQL server or database. 

**Steps** 
1. Deleted the svc-LocalAgent user from the sql server primary node databases and then removed the login from both servers.  
2. Run the following scripts in  
    .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
    .\Configure-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator 
  These scripts does not work with always-on setup. The database needs to created first in the primary node and then replicated.  

**Error event:** 
RunAsync failed due to an unhandled exception causing the host process to crash: System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: The remote name could not be resolved: 'lcsapi.lcs.dynamics.com' 

**Reason** 
The local agent machines are unable to connect to lcsapi.lcs.dynamics.com. Review AX-BridgeService eventlog for possible "The remote name could not be resolved: 'lcsapi.lcs.dynamics.com'".  

**Steps** 
1. Run [psping lcsapi.lcs.dynamics.com:80].  
2. If unable to receive reply then contact the IT department at your organization as the firewall is blocking access to lcsapi or proxy issues 
    Lcsapi.lcs.dynamics.com 
    <lcs azure blob storage domain> 
    <lcs azure queue domain> 

**Error event:**
Access to the path '\\...\agent\assets\StandAloneSetup-76308-1.zip' is denied 

**Reason** 
The local agent user is unable to access the file share specified in local agent configuration 

**Steps**  
1. Make sure that the file share is valid and it exists. 
2. Download PsExec https://docs.microsoft.com/en-us/sysinternals/downloads/psexec 
3. Open command prompt and  run PsExec.exe -u contoso\svc-LocalAgent$ cmd.exe 
4. Access the file share in the resulting window. Make sure that this completes without errors 
5. Add the local agent user to the file share and give full permissions 

Check for svc-LocalAgent$ rights to path (NTFS and share permissions) 

 


 










 


