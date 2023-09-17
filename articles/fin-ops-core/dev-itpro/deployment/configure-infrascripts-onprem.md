---
# required metadata

title: Configure the infrastructure scripts for your Finance + Operations (on-premises) deployment
description: This article explains how to configure the infrastructure scripts that are provided to deploy Microsoft Dynamics 365 Finance + Operations (on-premises).
author: faix
ms.date: 12/22/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: osfaixat
ms.search.validFrom:
ms.dyn365.ops.version: 
search.app:
  - financeandoperationsonprem-docs
---

# Configure the infrastructure scripts for your Finance + Operations (on-premises) deployment

This article explains how to configure the infrastructure scripts that are provided to deploy Microsoft Dynamics 365 Finance + Operations (on-premises). It describes what information is present in the different configuration files and what information must be supplied. A practical example is provided, in which Contoso Corporation must fill in the information for its production environment.

## Configuration files available in the infrastructure scripts

The infrastructure scripts use the following configuration files to drive the setup. The subsections that follow describe the contents of each file.

- infrastructure\\ConfigTemplate.xml
- infrastructure\\D365FO-OP\\NodeTopologyDefinition.xml
- infrastructure\\D365FO-OP\\DatabaseTopologyDefinition.xml
- infrastructure\\D365FO-OP\\FileShareTopologyDefinition.xml

### ConfigTemplate.xml

The ConfigTemplate.xml configuration file describes the following details. You must fill in this file to use the infrastructure scripts. For more information, see the [Filling in the ConfigTemplate.xml file](#filling-in-the-configtemplatexml-file) section of this article.

- The service accounts that are required for the application to work
- The certificates that are required to help secure communications
- The database configuration
- The Azure Service Fabric cluster configuration
- The file shares that are required for the application to work
- The SQL Server cluster information

> [!IMPORTANT]
> When you configure the Service Fabric cluster, make sure that there are three fault domains for the Primary node type (**OrchestratorType**). Also make sure that no more than one type of node is deployed on a single machine.

### NodeTopologyDefinition.xml

The NodeTopologyDefinition.xml configuration file describes the following details for each Service Fabric node type:

- The mapping between each node type and the application, domain and service accounts, and certificates
- Whether User Account Control (UAC) is enabled
- The prerequisites for Windows features and system software
- Whether strong name validation should be enabled
- The list of firewall ports that should be opened
- The permissions that an account requires for a machine
- Whether the .NET Framework should be configured to use the operating system's default Transport Layer Security (TLS) protocol
- Whether insecure TLS and Secure Sockets Layer (SSL) protocols should be disabled
- Whether insecure TLS ciphers should be disabled

> [!NOTE]
> You don't have to modify this file.

### DatabaseTopologyDefinition.xml

The DatabaseTopologyDefinition.xml configuration file describes the following details for each database:

- The database settings
- The mappings between users and roles

> [!NOTE]
> You don't have to modify this file.

### FileShareTopologyDefinition.xml

The FileShareTopologyDefinition.xml configuration file describes the following details for each file share:

- The file share settings
- The sharing permissions for the file share
- The New Technology File System (NTFS) permissions for the file share
- Additional folder-level permissions

> [!NOTE]
> You don't have to modify this file.

## Filling in the ConfigTemplate.xml file

This section describes, in detail, each configuration section in the ConfigTemplate.xml file.

### ADServiceAccounts

Although the field is named "DomainName," you must specify the network basic input/output system (NetBIOS) name of your domain, so that Active Directory objects such as **lab\svc-LocalAgent$** can be correctly built.

```xml
<DomainName>LAB</DomainName>
```

The **ADServiceAccounts** section supports two types of Active Directory service accounts: group managed service accounts (gMSAs) and domain users. However, for all newer base deployments, only gMSAs are used.

```xml
<ADServiceAccount type="gMSA" name="svc-LocalAgent$" refName="gmsaLocalAgent" disabled="false">
    <DNSHostName>svc-LocalAgent.contoso.com</DNSHostName>
</ADServiceAccount>
<ADServiceAccount type="DomainUser" name="AXServiceUser" refName="axserviceuser" disabled="true" />
```

For **ADServiceAccount** elements, you should update only the **name** attribute and the **DNSHostName** field, and only for gMSAs. If you won't be deploying Management Reporter, you can set the **disabled** attribute to **false** for the accounts. This setting ensures that configurations that are related to those accounts aren't generated.

```xml
<ADServiceAccount type="gMSA" name="svc-LA-sb$" refName="gmsaLocalAgent" disabled="false">
    <DNSHostName>svc-LA-sb.lab.local</DNSHostName>
</ADServiceAccount>
<ADServiceAccount type="DomainUser" name="AXServiceUser-sb" refName="axserviceuser" disabled="true" />
```

If your deployment is still on an old base deployment version (before Application version 10.0.20), you must continue to use an account of the **DomainUser** type. In this case, set the **disabled** attribute to **false** to ensure that the domain user account is enabled.

```xml
<ADServiceAccount type="DomainUser" name="AXServiceUser" refName="axserviceuser" disabled="false" />
```

### Certificates

Certificates can be generated through Active Directory Certificate Services (AD&nbsp;CS), or they can be self-signed. To specify how you want to generate the certificate, set the **generateSelfSignedCert** and **generateADCSCert** attributes as appropriate. We strongly recommend that you use AD&nbsp;CS certificates instead of self-signed certificates. If you're using the scripts to generate the certificate, don't specify a **Thumbprint** value for it. The scripts will automatically set the value.

```xml
<Certificate type="OnpremLocalAgent" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
    <Name>OnpremLocalAgent</Name>
    <Provider></Provider>
    <Thumbprint></Thumbprint>
    <ProtectTo></ProtectTo>
</Certificate>
```

If you've generated a certificate somewhere else, and the certificate is already provisioned on your machines, you can set the **exportable** attribute to **false**. In this case, the Export-Certificates.ps1 script won't try to export the certificate. However, you should still define the thumbprint, so that the correct access control list (ACL) can be generated and applied.

```xml
<Certificate type="" exportable="false" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
    <Name>OnpremLocalAgent</Name>
    <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
    <Thumbprint>55a4ef521a3a00f64c4ac665dbaf3f17408cfe3d</Thumbprint>
    <ProtectTo></ProtectTo>
</Certificate>
```

When the **ProtectTo** field for a certificate is set, it's common practice to specify the user who's performing the deployment. However, we don't recommend this approach. If the specified user leaves your company, you'll lose access to those exported certificates. Instead, set the **ProtectTo** field to an Active Directory group that the IT administrators for your Dynamics 365 deployment belong to. You can specify multiple groups, multiple users, or a combination of groups and users.

```xml
<Certificate type="" exportable="false" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
    <Name>OnpremLocalAgent</Name>
    <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
    <Thumbprint></Thumbprint>
    <ProtectTo>LAB\D365Admins;LAB\Domain Admins;LAB\Adminuser</ProtectTo>
</Certificate>
```

The certificate of the **ServiceFabric** type is your wildcard certificate that protects your cluster and is presented by other services that are hosted in the cluster. The **Name** field is mapped to the friendly name of a certificate. The **FileName** field is used to give the certificate a file name when it's exported. The **DNSName** field is mapped to the subject alternative names (SANs) of a certificate. The **Subject** field is mapped to the subject name (also known as the common name) of the certificate. Never update the **Provider**, **KeyUsage**, **EnhancedKeyUsage**, and **CertificateType** fields, because they're hard-coded as required to correctly generate the certificate. If you update those fields, there's no guarantee that the certificate will work, or that the scripts themselves will support the specified values.

```xml
<Certificate type="ServiceFabric" exportable="true" generateSelfSignedCert="false" generateADCSCert="true">
    <Name>star.lab.local</Name>
    <FileName>star.lab.local</FileName>
    <DNSName>ax.lab.local;sf.lab.local;*.lab.local</DNSName>
    <Subject>*.lab.local</Subject>
    <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
    <KeyUsage>DigitalSignature;KeyEncipherment</KeyUsage>
    <EnhancedKeyUsage>Server Authentication;Client Authentication</EnhancedKeyUsage>
    <Thumbprint></Thumbprint>
    <ProtectTo>LAB\D365Admins</ProtectTo>
</Certificate>
```

The certificate of the **SQLCluster** type is automatically generated by the scripts that generate the certificates. The scripts will use the information from the **SQLCluster** section later in the configuration file to automatically calculate the values. In this scenario, set the **ProtectTo** field to the appropriate users or groups.

```xml
<Certificate type="SQLCluster" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false" manualProperties="false">
    <Name></Name>
    <DNSName></DNSName>
    <Subject></Subject>
    <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
    <Thumbprint></Thumbprint>
    <ProtectTo>LAB\D365Admins</ProtectTo>
</Certificate>
```

If the logic that automatically calculates the configuration for the **SQLCluster** certificate doesn't correctly reflect your setup, you can override the automated calculation and manually specify it yourself. Set the **manualProperties** attribute to **true**, and fill in the certificate information. For this certificate, ensure that the certificate's SAN contains the name of each SQL Server and the Always On availability group listener (if you have one).

```xml
<Certificate type="SQLCluster" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false" manualProperties="true">
    <Name>LBDEN01SQLA.lab.local</Name>
    <DNSName>LBDEN01SQLA.lab.local;LBDEN01SQLA01.lab.local;LBDEN01SQLA02.lab.local</DNSName>
    <Subject>LBDEN01SQLA.lab.local</Subject>
    <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
    <Thumbprint></Thumbprint>
    <ProtectTo>LAB\D365Admins</ProtectTo>
</Certificate>
```

The certificate of the **RSAT** type is special. Because of requirements from the Performance software development kit (SDK) that the Regression suite automation tool (RSAT) is built on, this certificate **must** be self-signed. Additionally, as for the **SQLCluster** certificate, you should update only the **ProtectTo** field. By default, this certificate is disabled. Therefore, if you want it to be generated, be sure to set the **disabled** attribute to **false**.

```xml
<Certificate type="RSAT" exportable="true" generateSelfSignedCert="true" disabled="false">
    <Name>RSAT</Name>
    <FileName>RSAT</FileName>
    <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
    <Subject>127.0.0.1</Subject>
    <Thumbprint></Thumbprint>
    <ProtectTo>LAB\D365Admins</ProtectTo>
</Certificate>
```

### DbServer

When you update the user name of a user of the **SqlUser** type, you should update only the **userName** attribute.

```xml
<Security>
    <User refName="axdbadmin" type="SqlUser" userName="d365adminuser" generateUser="true" />
</Security>
```

By default, the scripts generate only the axdbadmin user. If you want the other users to be generated so that you can use additional features, set the **generateUser** attribute to **true**. The scripts can then determine that they should generate and enter details for the user.

```xml
<Security>
    <User refName="axdwadmin" type="SqlUser" userName="axdwadmin" generateUser="true" />
</Security>
```

### Databases

When you update a database entry, you can update the name of the database by updating the **dbName** attribute.

```xml
<Database refName="axdw" dbName="DataWarehouse"></Database>
```

Currently, only a single database has to be restored from a backup when the environment is created. Set the **BackupFile** field to the full path where the backup file is located. Note that the path must be accessible by the user that your SQL Server database engine is running under. We don't recommend that you modify the **DbTuning** section. However, if you do modify it, make sure that the values that you specify are the minimum values, and that you don't go lower. Otherwise, the deployment will fail.

```xml
<Database refName="axDB" dbName="AXDB">
    <BackupFile>D:\Backups\EmptyDatabase_10.0.32.bak</BackupFile>
    <DbTuning>
        <DBFileGrowthMB value="200" />
        <LogFileGrowthMB value="500" />
        <LogFileSizeGB value="5" />
    </DbTuning>
</Database>
```

### FileShares

The file shares have default share names. If you must update the name of the share, you can update the **name** attribute. This approach is important if the same file server will host the shares for multiple environments. 

```xml
<FileShare refName="agent" name="D365Agent" disabled="false">
    <Path></Path>
    <BasePath></BasePath>
    <LocalPath></LocalPath>
</FileShare>
```

By default, file shares are created in the C:\\Shares directory. However, you can override that location by specifying the full path of the folder where you want the shares to be created. If you're using the scripts to create the file shares, don't set the **LocalPath** field. Set the **LocalPath** field to the full path of the file share folder only if the share was created without using the scripts.

```xml
<FileShare refName="agent" name="agent" disabled="false">
    <Path></Path>
    <BasePath>D:\D365Shares</BasePath>
    <LocalPath></LocalPath>
</FileShare>
```

If you don't want one of the scripts to create and configure the file share for you, you can set the **disabled** attribute to **true**. The file share will then be ignored. 

```xml
<FileShare refName="agent" name="agent" disabled="true">
    <Path></Path>
    <BasePath></BasePath>
    <LocalPath></LocalPath>
</FileShare>
```

### ServiceFabricCluster

The **ClusterName** field is used only locally, to define the name of the Service Fabric cluster. You can customize it as you want.

```xml
<ClusterName>Dynamics365Operations</ClusterName>
```

The Service Fabric cluster requires that multiple **NodeType** elements be defined. The following example shows a node type definition. Don't modify the **name**, **namePrefix**, or **purpose** attributes, because they're pre-configured for each node type. You should modify the **disabled** and **primary** attributes only in specific situations.

If you won't be using a specified node type, you can set the **disabled** attribute to **true**. For example, if you want to have separate batch-only or interactive-only nodes, disable the **AOSNodeType** node type by setting **disabled** to **true**, and enable the **BatchOnlyAOSNodeType** or **InteractiveOnlyAOSNodeType** node type by setting **disabled** to **false**.

```xml
<NodeType name="AOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="false">
    <VMList>
        <VM name="aos1" ipAddress="10.179.108.12" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="aos2" ipAddress="10.179.108.13" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="aos3" ipAddress="10.179.108.14" faultDomain="fd:/fd2" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
<NodeType name="BatchOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="true">
    <VMList>
        <VM name="batchaos1" ipAddress="10.179.108.15" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="batchaos2" ipAddress="10.179.108.16" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="batchaos3" ipAddress="10.179.108.17" faultDomain="fd:/fd2" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
<NodeType name="InteractiveOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="true">
    <VMList>
        <VM name="interactiveaos1" ipAddress="10.179.108.18" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="interactiveaos2" ipAddress="10.179.108.19" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
    </VMList>
</NodeType>
```

If you want to change which node type will contain the Service Fabric system services, you can set the **primary** attribute to **true**. Keep in mind that, by default, the **OrchestratorType** node type is set as the primary node type. If you change a different node type to primary, make sure that you also update the **primary** attribute for the **OrchestratorType** node type. You should change the primary node type only if a different node type has more nodes assigned to it and can help you raise the reliability tier of your cluster.

```xml
<NodeType name="AOSNodeType" primary="true" namePrefix="AOS" purpose="AOS" disabled="false">
    <VMList>
        <VM name="aos1" ipAddress="10.179.108.12" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
        <VM name="aos2" ipAddress="10.179.108.13" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        <VM name="aos3" ipAddress="10.179.108.14" faultDomain="fd:/fd2" updateDomain="ud2" hasSSIS="false" />
        <VM name="aos4" ipAddress="10.179.108.15" faultDomain="fd:/fd0" updateDomain="ud1" hasSSIS="false" />
        <VM name="aos5" ipAddress="10.179.108.16" faultDomain="fd:/fd1" updateDomain="ud2" hasSSIS="false" />
    </VMList>
</NodeType>
<NodeType name="OrchestratorType" primary="false" namePrefix="Orch" purpose="Orchestrator" disabled="false">
    <VMList>
        <VM name="orch1" ipAddress="10.179.108.15" faultDomain="fd:/fd0" updateDomain="ud0" />
        <VM name="orch2" ipAddress="10.179.108.16" faultDomain="fd:/fd1" updateDomain="ud1" />
        <VM name="orch3" ipAddress="10.179.108.17" faultDomain="fd:/fd2" updateDomain="ud2" />
    </VMList>
</NodeType>
```

Each node type has a list of machines that belong to it. A machine is defined in the following way:

- Its **name** attribute is set to the name of the machine in the domain.
- Its **ipAddress** attribute is set to the static IP address of the machine.
- It has a fault domain that's specified by the **faultDomain** attribute.

    A fault domain is a set of hardware components that share a single point of failure. For example, a hardware host can be considered a fault domain. However, it can also be a set of hardware hosts that are connected to a single switch or router. In this case, the switch or router is the single point of failure, and anything that's connected to that switch or router is a single fault domain. In standalone Service Fabric clusters, fault domains don't play a large role, because you control the underlying infrastructure. However, they're are an important concept in the cloud. It's helpful to define a fault domain in Service Fabric, so that you know how your virtual machines (VMs) are distributed or spread out.

- It has an upgrade domain that's specified by the **updateDomain** attribute.

    Upgrade domains play a role when there's a change in the cluster (for example, a cluster configuration change or a cluster code upgrade). In this case, the change will be applied to one upgrade domain at a time. Therefore, you shouldn't set all your Application Object Server (AOS) nodes so that they're in the same upgrade domain. Otherwise, they all will go down at the same time if there's a change in your cluster.

- It might have the **hasSSIS** attribute, which indicates whether SQL Server Integration Services (SSIS) is installed on the node. The **hasSSIS** field is used for version 10.0.32 and later base deployments to help pinpoint where the Data Management Framework (DMF) service will be put if a dedicated node type isn't used.

```xml
<VM name="reportbi1" ipAddress="10.179.108.10" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
```

The **ServiceFabricSettings** section allows for customization of several Service Fabric settings. Only those settings that are explicitly required for deployments are defined. For information about what each setting does, see [Customize Service Fabric cluster settings](/azure/service-fabric/service-fabric-cluster-fabric-settings).

```xml
<ServiceFabricSettings>
    <Setting name="Setup" disabled="false">
        <Parameters>
           <Parameter name="FabricDataRoot">C:\ProgramData\SF</Parameter>
            <Parameter name="FabricLogRoot">C:\ProgramData\SF\Log</Parameter>
        </Parameters>
    </Setting>
    <Setting name="PlacementAndLoadBalancing" disabled="false">
        <Parameters>
            <Parameter name="NodeTaggingEnabled">true</Parameter>
        </Parameters>
    </Setting>
</ServiceFabricSettings>
```

If you want to customize your cluster, you can create additional settings in the template, so that they're automatically filled in when the cluster configuration is created or updated. For example, if you want to enable server restarts from Service Fabric, you can use the **EnableRestartManagement** parameter.

```xml
<Setting name="FabricHost" disabled="false">
    <Parameters>
        <Parameter name="EnableRestartManagement">true</Parameter>
    </Parameters>
</Setting>
```

### SQLCluster

The **ListenerName** field is required only if you have a SQL Server cluster. If have a single SQL Server VM, because you're deploying a sandbox environment, be sure to leave the **ListenerName** field blank.

```xml
<ListenerName></ListenerName>
```

The **SQLVMList** element should contain the name of every SQL Server machine that belongs to your cluster.

```xml
<SQLVMList>
    <SQLVM name="LBDSQLA01" />
    <SQLVM name="LBDSQLA02" />
</SQLVMList>
```

If you only have one SQL Server machine, list only that machine.

```xml
<SQLVMList>
    <SQLVM name="LBDSQLA01" />
</SQLVMList>
```

## Example ConfigTemplate.xml file for Contoso Corporation

Contoso Corporation will fill in the ConfigTemplate.xml file based on the following information:

- The Active Directory domain is **Contoso.com**, and the NetBIOS name is **Contoso**.
- Contoso is deploying its *production* environment.
- The Service Fabric Domain Name System (DNS) endpoint will be **sf.contoso.com**.
- The AOS DNS endpoint will be **ax.contoso.com**.
- The SQL Server Reporting Services (SSRS) machines are joined to a Windows Server failover cluster. The cluster is named **LBDEN01SFBI**.
- The SQL Always On availability group is **LBDEN01SQLA**.
- The Dynamics 365 Administrators group in the domain is named **contoso\\D365Admins**.
- The following machines are used.

    | Machine purpose                                   | Service Fabric node type   | Machine name   | IP address |
    |---------------------------------------------------|----------------------------|----------------|------------|
    | Domain controller                                 |                            | LBDEN01DC1     | 10.0.0.2   |
    | Active Directory Federation Services (AD&nbsp;FS) |                            | LBDEN01ADFS1   | 10.0.0.3   |
    | File server                                       |                            | LBDEN01FS01    | 10.0.0.4   |
    | SQL Server 1                                      |                            | LBDEN01SQLA01  | 10.0.0.5   |
    | SQL Server 2                                      |                            | LBDEN01SQLA02  | 10.0.0.6   |
    | SQL Always On availability group listener         |                            | LBDEN01SQLA    | 10.0.0.9   |
    | AOS 1                                             | BatchOnlyAOSNodeType       | LBDEN01SFAOS1  | 10.0.0.11  |
    | AOS 2                                             | BatchOnlyAOSNodeType       | LBDEN01SFAOS2  | 10.0.0.12  |
    | AOS 3                                             | BatchOnlyAOSNodeType       | LBDEN01SFAOS3  | 10.0.0.13  |
    | AOS 4                                             | InteractiveOnlyAOSNodeType | LBDEN01SFAOS4  | 10.0.0.14  |
    | AOS 5                                             | InteractiveOnlyAOSNodeType | LBDEN01SFAOS5  | 10.0.0.15  |
    | AOS 6                                             | InteractiveOnlyAOSNodeType | LBDEN01SFAOS6  | 10.0.0.16  |
    | Orchestrator 1                                    | OrchestratorType           | LBDEN01SFORCH1 | 10.0.0.21  | 
    | Orchestrator 2                                    | OrchestratorType           | LBDEN01SFORCH2 | 10.0.0.22  |
    | Orchestrator 3                                    | OrchestratorType           | LBDEN01SFORCH3 | 10.0.0.23  |
    | Management Reporter node 1                        | MRType                     | LBDEN01SFMR1   | 10.0.0.31  |
    | Management Reporter node 2                        | MRType                     | LBDEN01SFMR2   | 10.0.0.32  |
    | SSRS node 1                                       | ReportServerType           | LBDEN01SFBI1   | 10.0.0.41  |
    | SSRS node 2                                       | ReportServerType           | LBDEN01SFBI2   | 10.0.0.42  |
    | SSRS Windows Server failover cluster name         |                            | LBDEN01SFBI    | 10.0.0.49  |
    | SSIS node 1                                       | SSISNodeType               | LBDEN01SFSSIS1 | 10.0.0.51  |
    | SSIS node 2                                       | SSISNodeType               | LBDEN01SFSSIS2 | 10.0.0.52  |

### ADServiceAccounts section

For the **DomainName** field, the NetBIOS name of the domain is **Contoso**.

Contoso Corporation wants to use differentiated gMSAs per environment. Because they're preparing the configuration for their production environment, they've added the suffix "-Prod" to all the accounts. For each **ADServiceAccount** element of the **gMSA** type, they've updated the **name** attribute and the **DNSHostName** field. 

Contoso is deploying a base package of 10.0.29. The **axserviceuser** account remains disabled, because it won't be used.

```xml
<ADServiceAccounts>
    <DomainName>Contoso</DomainName>
    <ADServiceAccount type="gMSA" name="svc-LA-Prod$" refName="gmsaLocalAgent" disabled="false">
        <DNSHostName>svc-LA-Prod.contoso.com</DNSHostName>
    </ADServiceAccount>
    <ADServiceAccount type="gMSA" name="svc-FRAS-Prod$" refName="gmsaFRAS" disabled="false">
        <DNSHostName>svc-FRAS-Prod.contoso.com</DNSHostName>
    </ADServiceAccount>
    <ADServiceAccount type="gMSA" name="svc-FRPS-Prod$" refName="gmsaFRPS" disabled="false">
        <DNSHostName>svc-FRPS-Prod.contoso.com</DNSHostName>
    </ADServiceAccount>
    <ADServiceAccount type="gMSA" name="svc-FRCO-Prod$" refName="gmsaFRCO" disabled="false">
        <DNSHostName>svc-FRCO-Prod.contoso.com</DNSHostName>
    </ADServiceAccount>
    <ADServiceAccount type="gMSA" name="svc-AXSF-Prod$" refName="gmsaAXSF" disabled="false">
        <DNSHostName>svc-AXSF-Prod.contoso.com</DNSHostName>
    </ADServiceAccount>
    <ADServiceAccount type="gMSA" name="svc-Rep-Prod$" refName="gmsaSSRS" disabled="false">
        <DNSHostName>svc-Rep-Prod.contoso.com</DNSHostName>
    </ADServiceAccount>
    <ADServiceAccount type="gMSA" name="svc-DIXF-Prod$" refName="gmsaDIXF" disabled="false">
        <DNSHostName>svc-DIXF-Prod.contoso.com</DNSHostName>
    </ADServiceAccount>
    <ADServiceAccount type="DomainUser" name="AXServiceUser" refName="axserviceuser" disabled="true" />
</ADServiceAccounts>
```

### Certificates section

Contoso Corporation has acquired a certificate for its **ServiceFabric** certificate from a public certificate authority. Because they don't need the scripts to generate the certificate, they set the **generateADCSCert** attribute to **false**. They also fill in the thumbprint of the certificate, so that it can be exported later.

Contoso has an AD&nbsp;CS server and has decided to use it to generate all the other certificates.

Contoso doesn't want to lose access to the certificate private keys if the current IT administrator leaves. Therefore, they haven't set the **ProtectTo** field to an individual user. Instead, they've specified an Active Directory group that all their IT administrators belong to. This approach is a best practice.

As it did for the gMSAs, Contoso has added the **-prod** suffix to all its other certificates (except the **SQLCluster**, **OnpremLocalAgent**, and **RSAT** certificates), so that they're easier to distinguish.

According to the setup guide, the infrastructure scripts will automatically generate the information for the **SQLCluster** certificate, provided that the **SQLCluster** configuration is specified further down in the configuration template. Therefore, Contoso has left everything blank except the **ProtectTo** field.

Because this isn't its first environment, Contoso has already registered the **OnpremLocalAgent** certificate against its Azure Active Directory (Azure AD) tenant and doesn't have to generate a new one. Instead, they specify the thumbprint of the existing certificate and set the **generateADCSCert** attribute to **false**.

Even though Contoso wants to use RSAT, RSAT should only be used with *sandbox* environments. Because they're specifying the configuration for their *production* environment, they've left the **disabled** attribute of the **RSAT** certificate set to **true**.

```xml
<Certificates>
    <Certificate type="ServiceFabric" exportable="true" generateSelfSignedCert="false" generateADCSCert="false">
        <Name>star.contoso.com</Name>
        <FileName>star.contoso.com</FileName>
        <DNSName>ax.contoso.com;sf.contoso.com;*.contoso.com</DNSName>
        <Subject>*.contoso.com</Subject>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <KeyUsage>DigitalSignature;KeyEncipherment</KeyUsage>
        <EnhancedKeyUsage>Server Authentication;Client Authentication</EnhancedKeyUsage>
        <Thumbprint>55a4ef521a3a00f64c4ac665dbaf3f17408cfe3d</Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="ServiceFabricClient" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>client-prod.contoso.com</Name>
        <Subject>client-prod.contoso.com</Subject>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <KeyUsage>DigitalSignature;KeyEncipherment</KeyUsage>
        <EnhancedKeyUsage>Server Authentication;Client Authentication</EnhancedKeyUsage>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="ServiceFabricEncryption" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>axdataenciphermentcert-prod</Name>
        <Provider>Microsoft Enhanced Cryptographic Provider v1.0</Provider>
        <CertificateType>DocumentEncryptionCert</CertificateType>
        <KeyUsage>DataEncipherment</KeyUsage>
        <EnhancedKeyUsage>Document Encryption</EnhancedKeyUsage>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="SessionAuthentication" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>SessionAuthentication-prod</Name>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
  </Certificate>
  <Certificate type="DataEncryption" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>DataEncryption-prod</Name>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="DataSigning" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>DataSigning-prod</Name>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="FinancialReporting" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>FinancialReporting-prod</Name>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="ReportingService" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>ReportingService-prod</Name>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="Orchestrator" exportable="true" generateSelfSignedCert="false" generateADCSCert="false" disabled="false">
        <Name>OnPremLocalAgent</Name>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint>66a4ea345a3a44f6e33ac215dbaf3f34a19cee3d</Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="SSRSHTTPS" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
        <Name>LBDEN01SFBI.contoso.com</Name>
        <FileName>LBDEN01SFBI.contoso.com</FileName>
        <DNSName>LBDEN01SFBI1.contoso.com;LBDEN01SFBI2.contoso.com;LBDEN01SFBI.contoso.com</DNSName>
        <Subject>LBDEN01SFBI.contoso.com</Subject>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="SQLCluster" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false" manualProperties="false">
        <Name></Name>
        <DNSName></DNSName>
        <Subject></Subject>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Thumbprint></Thumbprint>
        <ProtectTo>contoso\D365Admins</ProtectTo>
    </Certificate>
    <Certificate type="RSAT" exportable="true" generateSelfSignedCert="true" disabled="true">
        <Name>RSAT</Name>
        <FileName>RSAT</FileName>
        <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
        <Subject>127.0.0.1</Subject>
        <Thumbprint></Thumbprint>
        <ProtectTo></ProtectTo>
    </Certificate>
</Certificates>
```

### DbServer section

Contoso Corporation will dedicate the SQL Server cluster that it has created to the exclusive use of its production instance of Finance + Operations (on-premises). Therefore, they've decided to leave the default values for the **userName** attribute.

Additionally, Contoso wants to use the Entity Store feature. Therefore, they set the **generateUser** attribute to **true** for the **axdwadmin** and **axdwruntimeuser** accounts. 

```xml
<DbServer>
    <Security>
        <User refName="axdbadmin" type="SqlUser" userName="axdbadmin" generateUser="true" />
    </Security>
    <Security>
        <User refName="axdwadmin" type="SqlUser" userName="axdwadmin" generateUser="true" />
    </Security>
    <Security>
        <User refName="axdwruntimeuser" type="SqlUser" userName="axdwruntimeuser" generateUser="true" />
    </Security>
</DbServer>
```

### Databases section

Contoso Corporation will leave the default values for its database names (**dbName** attribute). They haven't downloaded the empty or demo databases from Microsoft Dynamics Lifecycle Services. In addition, they haven't yet filled in the **BackupFile** field but will be sure to fill it in later.

```xml
<Databases>
    <Database refName="axDB" dbName="AXDB">
        <BackupFile></BackupFile>
        <DbTuning>
        <DBFileGrowthMB value="200" />
        <LogFileGrowthMB value="500" />
        <LogFileSizeGB value="5" />
        </DbTuning>
    </Database>
    <Database refName="financialReporting" dbName="FinancialReporting"></Database>
    <Database refName="orchestratorData" dbName="OrchestratorData"></Database>
    <Database refName="axdw" dbName="AXDW"></Database>
</Databases>
```

### FileShares section

Contoso Corporation has a file server that has a single node. However, they will be sure to set up a high availability solution soon, before they go live. For now, they've created a specific volume to host the **sfDiagnostics** share and a separate volume to host the remaining shares. For each file share, they've filled in only the **BasePath** field, because all the remaining fields are filled in by the infrastructure scripts.

```xml
<FileShares>
    <FileShare refName="agent" name="agent" disabled="false">
        <Path></Path>
        <BasePath>D:\Shares</BasePath>
        <LocalPath></LocalPath>
    </FileShare>
    <FileShare refName="aos" name="aos-storage" disabled="false">
        <Path></Path>
        <BasePath>D:\Shares</BasePath>
        <LocalPath></LocalPath>
    </FileShare>
    <FileShare refName="dixf" name="dixf-share" disabled="false">
        <Path></Path>
        <BasePath>D:\Shares</BasePath>
        <LocalPath></LocalPath>
    </FileShare>
    <FileShare refName="sfDiagnostics" name="diagnostics-store" disabled="false">
        <Path></Path>
        <BasePath>E:\Shares</BasePath>
        <LocalPath></LocalPath>
    </FileShare>
</FileShares>
```

### ServiceFabricCluster section

To correctly identify the cluster that it's connected to, Contoso Corporation has updated the **ClusterName** field to reflect the fact that this cluster is the production cluster.

Contoso has observed that it has resource-heavy batch jobs that run during normal operation hours. Because they don't want these jobs to affect their users, they've chosen to split batch and interactive sessions into separate nodes. Therefore, they've set the **disabled** attribute to **false** for the **BatchOnlyAOSNodeType** and **InteractiveOnlyAOSNodeType** node types, but they've set it to **true** for the **AOSNodeType** node type.

For each machine that belongs to a node type, they've filled in the name and IP address of the VM, the fault domain, and the update domain.

Contoso has a fault-tolerant setup. However, they don't have enough fault tolerance to provide three fault domains. They've chosen to randomly assign the fault tolerance values so that they're spread out across the minimum requirement of three fault domains.

Contoso doesn't expect that it will have to update its cluster often. However, they know that they must follow the best practices for updating domain definitions. Therefore, they've made sure that each node for each node type is put in a different update domain. This approach ensures that only one node of each node type will be taken down at a time if there's a cluster update or upgrade.

Contoso noticed that a new service has been introduced for DMF since Application version 10.0.32. This service removes the need to have SSIS installed and licensed on all AOS nodes. They're also aware that they can disable the **SSISNodeType** node type, and that they can instead use the **ReportServerType** node type to host the DMF service by setting the **hasSSIS** to **true** on each node of the **ReportServerType** node type. However, because they have very resource-intensive DMF operations, they don't want to disrupt report generation. Therefore, they've chosen to have dedicated nodes for the service. 

To make it easier to find the **FabricDataRoot** and **FabricLogRoot** folders, Contoso has updated the paths so that they're in the root directory.

```xml
<ServiceFabricCluster>
    <ClusterName>Contoso Production</ClusterName>
    <NodeType name="AOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="true">
        <VMList>
            <VM name="" ipAddress="" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
            <VM name="" ipAddress="" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
            <VM name="" ipAddress="" faultDomain="fd:/fd2" updateDomain="ud2" hasSSIS="false" />
        </VMList>
    </NodeType>
    <NodeType name="BatchOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="false">
        <VMList>
            <VM name="LBDEN01SFAOS1" ipAddress="10.0.0.11" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
            <VM name="LBDEN01SFAOS2" ipAddress="10.0.0.12" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
            <VM name="LBDEN01SFAOS3" ipAddress="10.0.0.13" faultDomain="fd:/fd2" updateDomain="ud2" hasSSIS="false" />
        </VMList>
    </NodeType>
    <NodeType name="InteractiveOnlyAOSNodeType" primary="false" namePrefix="AOS" purpose="AOS" disabled="false">
        <VMList>
            <VM name="LBDEN01SFAOS4" ipAddress="10.0.0.14" faultDomain="fd:/fd0" updateDomain="ud1" hasSSIS="false" />
            <VM name="LBDEN01SFAOS5" ipAddress="10.0.0.15" faultDomain="fd:/fd1" updateDomain="ud2" hasSSIS="false" />
            <VM name="LBDEN01SFAOS6" ipAddress="10.0.0.16" faultDomain="fd:/fd2" updateDomain="ud0" hasSSIS="false" />
        </VMList>
    </NodeType>
    <NodeType name="OrchestratorType" primary="true" namePrefix="Orch" purpose="Orchestrator" disabled="false">
        <VMList>
            <VM name="LBDEN01SFORCH1" ipAddress="10.0.0.21" faultDomain="fd:/fd0" updateDomain="ud2" />
            <VM name="LBDEN01SFORCH2" ipAddress="10.0.0.22" faultDomain="fd:/fd1" updateDomain="ud0" />
            <VM name="LBDEN01SFORCH3" ipAddress="10.0.0.23" faultDomain="fd:/fd2" updateDomain="ud1" />
        </VMList>
    </NodeType>
    <NodeType name="ReportServerType" primary="false" namePrefix="Rep" purpose="BI" disabled="false">
        <VMList>
            <VM name="LBDEN01SFBI1" ipAddress="10.0.0.41" faultDomain="fd:/fd0" updateDomain="ud0" hasSSIS="false" />
            <VM name="LBDEN01SFBI2" ipAddress="10.0.0.42" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
        </VMList>
    </NodeType>
    <NodeType name="MRType" primary="false" namePrefix="MR" purpose="MR" disabled="false">
        <VMList>
            <VM name="LBDEN01SFMR1" ipAddress="10.0.0.31" faultDomain="fd:/fd1" updateDomain="ud1" hasSSIS="false" />
            <VM name="LBDEN01SFMR2" ipAddress="10.0.0.32" faultDomain="fd:/fd2" updateDomain="ud2" hasSSIS="false" />
        </VMList>
    </NodeType>
    <NodeType name="SSISNodeType" primary="false" namePrefix="SSIS" purpose="SSIS" disabled="false">
        <VMList>
            <VM name="LBDEN01SFSSIS1" ipAddress="10.0.0.51" faultDomain="fd:/fd2" updateDomain="ud2" />
            <VM name="LBDEN01SFSSIS2" ipAddress="10.0.0.52" faultDomain="fd:/fd1" updateDomain="ud0" />
        </VMList>
    </NodeType>
    <ServiceFabricSettings>
        <Setting name="Setup" disabled="false">
            <Parameters>
                <Parameter name="FabricDataRoot">C:\SF</Parameter>
                <Parameter name="FabricLogRoot">C:\SF\Log</Parameter>
            </Parameters>
        <Setting>
            <Parameters>
                <Parameter name="NodeTaggingEnabled">true</Parameter>
            </Parameters>
        </Setting>
    </ServiceFabricSettings>
</ServiceFabricCluster>
```

### SQLCluster section

Contoso Corporation has created a SQL Always On cluster that has availability groups and that consists of two VMs. They've added each SQL Server VM under the **SQLVMList** element. Additionally, because they have availability groups, they've specified the **ListenerName** value of their availability group.

```xml
<SQLCluster>
    <ListenerName>LBDEN01SQLA</ListenerName>
    <SQLVMList>
        <SQLVM name="LBDEN01SQLA01" />
        <SQLVM name="LBDEN01SQLA02" />
    </SQLVMList>
</SQLCluster>
```
