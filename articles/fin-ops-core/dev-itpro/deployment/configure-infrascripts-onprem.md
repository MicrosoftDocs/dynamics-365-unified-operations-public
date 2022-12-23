---
# required metadata

title: Configure the Infrastructure Scripts for your Microsoft Dynamics 365 Finance + Operations (on-premises) deployment
description: This article explains how to configure the infrastructure scripts provided to deploy Microsoft Dynamics 365 Finance + Operations (on-premises).
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

---

# Configure the Infrastructure Scripts for your Microsoft Dynamics 365 Finance + Operations (on-premises) deployment

This article explains which information is present in the different configuration files and which information needs to be provided. At the end there is also a scenario where a practical example is given in which a company needs to fill out the information for their production environment.

## Configuration files available in the infrastructure scripts

The infrastructure setup scripts use the following configuration files to drive the setup:

- infrastructure\\ConfigTemplate.xml
- infrastructure\\D365FO-OP\\NodeTopologyDefinition.xml
- infrastructure\\D365FO-OP\\DatabaseTopologyDefinition.xml
- infrastructure\\D365FO-OP\\FileShareTopologyDefinition.xml

### ConfigTemplate.xml

You must fill out this file to be able to use the infrastructure scripts. The ConfigTemplate.xml configuration file describes the following details:

- The service accounts that are required for the application to work
- The certificates that are required to help secure communications
- The database configuration
- The Service Fabric cluster configuration
- The file shares that are required for the application to work
- The SQL cluster information 

    > [!IMPORTANT]
    > When you configure the Service Fabric cluster, make sure that there are three fault domains for the Primary node type (**OrchestratorType**). Also make sure that no more than one type of node is deployed on a single machine.

### NodeTopologyDefinition.xml

For each Service Fabric node type, the NodeTopologyDefinition.xml configuration file describes the following details:

- The mapping between each node type and the application, domain and service accounts, and certificates
- Whether User Account Control (UAC) is enabled
- The prerequisites for Windows features and system software
- Whether strong name validation should be enabled
- The list of firewall ports that should be opened
- Which permissions an account requires for a machine
- Whether the .NET Framework should be configured to use the operating system's default Transport Layer Security (TLS) protocol.
- Whether insecure TLS and SSL protocols should be disabled.
- Whether insecure TLS ciphers should be disabled.

> [!NOTE]
> You do not need to modify this file.

### DatabaseTopologyDefinition.xml

For each database, the DatabaseTopologyDefinition.xml configuration file describes the following details:

- The database settings
- The mappings between users and roles

> [!NOTE]
> You do not need to modify this file.

### FileShareTopologyDefinition.xml

For each fileshare, the FileShareTopologyDefinition.xml configuration file describes the following details:

- The fileshare settings
- The fileshare share permissions
- The fileshare NTFS permissions
- Additional folder level permissions

> [!NOTE]
> You do not need to modify this file.

## Filling out your ConfigTemplate.xml

### Section explanations

In this section we will explain in detail what the different configurations for each part of the configuration file do.

#### ADServiceAccounts

Despite being called DomainName, we actually you need you to specify the NETBIOS name of your domain so that we can correctly build the AD objects like **lab\svc-LocalAgent$**.

```xml
<DomainName>LAB</DomainName>
```

In this section we currently support two types of ADServiceAccounts, group Managed Service Account (gMSA) and domain users. However, for all newer base deployments only gMSA accounts are used.

```xml
<ADServiceAccount type="gMSA" name="svc-LocalAgent$" refName="gmsaLocalAgent" disabled="false">
    <DNSHostName>svc-LocalAgent.contoso.com</DNSHostName>
</ADServiceAccount>
<ADServiceAccount type="DomainUser" name="AXServiceUser" refName="axserviceuser" disabled="true" />
```

For an ADServiceAccount, you should only be updating the **name** and **DNSHostName** (only for gMSA accounts). If you do not want to use Management Reporter and will not be deploying it, then you can set **disabled** to false for those accounts. This will ensure that configuration related to those accounts are not generated.

```xml
<ADServiceAccount type="gMSA" name="svc-LA-sb$" refName="gmsaLocalAgent" disabled="false">
    <DNSHostName>svc-LA-sb.lab.local</DNSHostName>
</ADServiceAccount>
<ADServiceAccount type="DomainUser" name="AXServiceUser-sb" refName="axserviceuser" disabled="true" />
```

If your deployment is still on an old base deployment version (prior to Application version 10.0.20), you will need to keep using the DomainUser. As such, make sure that it is enabled by setting **disabled** to false.

```xml
  <ADServiceAccount type="DomainUser" name="AXServiceUser" refName="axserviceuser" disabled="false" />
```

#### Certificates

Certificates can be generated through Active Directory Certificate Services (ADCS) or can be self-signed. To set how you want to generate the certificate set **generateSelfSignedCert** or **generateADCSCert** appropriately. We strongly recommend that you use ADCS certificates over self-signed certificates. Do not fill in the **Thumbprint** of the certificate if you are using the scripts to generate the certificate as they will get auto populated.

```xml
 <Certificate type="OnpremLocalAgent" exportable="true" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
      <Name>OnpremLocalAgent</Name>
      <Provider></Provider>
      <Thumbprint></Thumbprint>
      <ProtectTo></ProtectTo>
</Certificate>
```

If you have generated a certificate elsewhere and already have the certificate provisioned in your machines, you can set **exportable** to false, and then the Export-Certificates.ps1 script will not attempt to export it. However you should still be defining the thumbprint so that the correct ACL can be generated and applied.

```xml
 <Certificate type="" exportable="false" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
      <Name>OnpremLocalAgent</Name>
      <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
      <Thumbprint>55a4ef521a3a00f64c4ac665dbaf3f17408cfe3d</Thumbprint>
      <ProtectTo></ProtectTo>
</Certificate>
```

When specifying the ProtectTo field for a certificate, it is common to set the user that is carrying out the deployment. However, this is a bad idea as if that user leaves the company you will lose access to those exported certificates. Instead, set the ProtectTo to  an active directory group that IT administrators for your D365 deployment belong to. You can specify multiple groups, users, or a combination of both.

```xml
 <Certificate type="" exportable="false" generateSelfSignedCert="false" generateADCSCert="true" disabled="false">
      <Name>OnpremLocalAgent</Name>
      <Provider>Microsoft Enhanced RSA and AES Cryptographic Provider</Provider>
      <Thumbprint></Thumbprint>
      <ProtectTo>LAB\D365Admins;LAB\Domain Admins;LAB\Adminuser</ProtectTo>
</Certificate>
```

The certificate of type **ServiceFabric** is your wildcard certificate that protects your cluster and is presented by other services hosted in the cluster. The **Name** field is mapped to the Friendly Name of a certificate. The **FileName** field is used when exporting the certificate to give the exported certificate a file name. The **DNSName** field is mapped to the Subject Alternative Names of a certificate. The **Subject** field is mapped to the Subject Name (also known as Common Name) of the certificate. Never update the **Provider**, **KeyUsage**, **EnhancedKeyUsage** or **CertificateType** fields as these fields are hardcoded where necessary to generate the certificate correctly. If you update them there is no guarantee that the certificate will work, or that the scripts themselves would support the option specified.

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

The certificate of type **SQLCluster** will be automatically generated by the scripts that generate the certificates. The scripts will use the information from the SQLCluster section later in the configuration file to automatically calculate the values. In such a scenario, simply set the **ProtectTo** field to the appropriate users or groups.

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

In the cases where the logic that automatically calculates the configuration for the **SQLCluster** certificate does not correctly reflect your setup you can override the automated calculation and set it to manually specify it yourself. Simply set **manualProperties** to true and fill out the certificate information. For this certificate, ensure that the certificate SAN contains the name of each SQL server as well as the always on availability group listener (if you have one).

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

The certificate of type **RSAT** is a special certificate as it can only be self-signed due to requirements from the Performance SDK that the Regression Suite Automation Tool (RSAT) is built on. Additionally, similar to the **SQLCluster** certificate you should only update the **ProtectTo** field. By default this certificate is disabled, so if you want it to be generated make sure you set **disabled** to false.

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

#### DbServer

When updating the username of a Sql user, you should only update the **userName** field.

```xml
    <Security>
      <User refName="axdbadmin" type="SqlUser" userName="d365adminuser" generateUser="true" />
    </Security>
```

By default only the axdbadmin user is generated by the scripts. If you want to generate the other users because you want to make use of additional features, set **generateUser** to true so that the scripts know to generate and populate the user.

```xml
<Security>
    <User refName="axdwadmin" type="SqlUser" userName="axdwadmin" generateUser="true" />
</Security>
```

#### Databases

When updating a database entry you can update the name of the database by updating **dbName** field.

```xml
<Database refName="axdw" dbName="DataWarehouse"></Database>
```

Currently only, a single database needs to be restored from a backup when creating the environment. Set the **BackupFile** field to the full path where the backup file is located. Note that the path needs to be accessible by the user that your SQL Server database engine is running under. We don't recommend tweaking the **DbTuning** section, however if you do make sure those are the minimum values that you specify and you don't go lower. The deployment will fail otherwise.

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

#### FileShares

The fileshares have default share names, if you need to update the name of the share you can update the **name** field.

```xml
<FileShare refName="agent" name="D365Agent" disabled="false">
    <Path></Path>
    <BasePath></BasePath>
    <LocalPath></LocalPath>
</FileShare>
```

By default, fileshares will be created in the C:\Shares directory, however if you want to override that location you can do so by specifying the full path to the folder that you would like the shares to be created in.

```xml
<FileShare refName="agent" name="agent" disabled="false">
    <Path></Path>
    <BasePath>D:\D365Shares</BasePath>
    <LocalPath></LocalPath>
</FileShare>
```

In case that you don't want one of the scripts to create/configure the fileshare for you, you can set **disabled** to true and that fileshare will be ignored. 

```xml
<FileShare refName="agent" name="agent" disabled="true">
    <Path></Path>
    <BasePath></BasePath>
    <LocalPath></LocalPath>
</FileShare>
```

#### SQLCluster

The **ListenerName** field is only necessary if you have a SQL cluster. If have a single SQL VM because you are deploying a sandbox environment make sure that you leave it blank.

```xml
<ListenerName></ListenerName>
```

The **SQLVMList** should contain the name of all the SQL machines that belong to your cluster.

```xml
<SQLVMList>
    <SQLVM name="LBDSQLA01" />
    <SQLVM name="LBDSQLA02" />
</SQLVMList>
```

Alternatively, if you only have one SQL machine then just have that single machine.

```xml
<SQLVMList>
    <SQLVM name="LBDSQLA01" />
</SQLVMList>
```

### Filling out a ConfigTemplate.xml for Contoso Corporation

Contoso Corporation will fill out the ConfigTemplate.xml based on the following information:

- The Active Directory domain is Contoso.com and the NETBIOS name is Contoso.
- Contoso Corporation is deploying their production environment.
- The service fabric DNS endpoint will be sf.contoso.com
- The AOS DNS endpoint will be ax.contoso.com
- The SSRS machines are joined to a Windows Server Failover Cluster. The name of the cluster is: LBDEN01SFBI
- The SQL Always-On availability group is: LBDEN01SQLA
- The D365 Administrators group in the domain is called: contoso\D365Admins

| Machine purpose           | Service Fabric node type   | Machine name    | IP address |
|---------------------------|----------------------------|-----------------|------------|
| Domain controller         |                            | LBDEN01DC1      | 10.0.0.2   |
| AD FS                     |                            | LBDEN01ADFS1    | 10.0.0.3   |
| File server               |                            | LBDEN01FS01     | 10.0.0.4   |
| SQL 1                     |                            | LBDEN01SQLA01   | 10.0.0.5   |
| SQL 2                     |                            | LBDEN01SQLA02   | 10.0.0.6   |
| SQL Always-on AG listener |                            | LBDEN01SQLA     | 10.0.0.9   |
| AOS 1                     | BatchOnlyAOSNodeType       | LBDEN01SFAOS1   | 10.0.0.11  |
| AOS 2                     | BatchOnlyAOSNodeType       | LBDEN01SFAOS2   | 10.0.0.12  |
| AOS 3                     | BatchOnlyAOSNodeType       | LBDEN01SFAOS3   | 10.0.0.13  |
| AOS 4                     | InteractiveOnlyAOSNodeType | LBDEN01SFAOS4   | 10.0.0.14  |
| AOS 5                     | InteractiveOnlyAOSNodeType | LBDEN01SFAOS5   | 10.0.0.15  |
| AOS 6                     | InteractiveOnlyAOSNodeType | LBDEN01SFAOS6   | 10.0.0.16  |
| Orchestrator 1            | OrchestratorType           | LBDEN01SFORCH1  | 10.0.0.21  | 
| Orchestrator 2            | OrchestratorType           | LBDEN01SFORCH2  | 10.0.0.22  |
| Orchestrator 3            | OrchestratorType           | LBDEN01SFORCH3  | 10.0.0.23  |
| Management Reporter node 1| MRType                     | LBDEN01SFMR1    | 10.0.0.31  |
| Management Reporter node 2| MRType                     | LBDEN01SFMR2    | 10.0.0.32  |
| SSRS node 1               | ReportServerType           | LBDEN01SFBI1    | 10.0.0.41  |
| SSRS node 2               | ReportServerType           | LBDEN01SFBI2    | 10.0.0.42  |
| SSRS WSFC cluster name    |                            | LBDEN01SFBI     | 10.0.0.49  |
| SSIS node 1               | SSISNodeType               | LBDEN01SFSSIS1  | 10.0.0.51  |
| SSIS node 2               | SSISNodeType               | LBDEN01SFSSIS2  | 10.0.0.52  |

#### ADServiceAccounts

For DomainName the NETBIOS name of the domain has been used: Contoso.

Contoso wants to use differentiated gMSA accounts per environment. As they are preparing the configuration for their production environment, they have added the **-Prod** suffix to all of the accounts. Foreach of the ADServiceAccounts that are of type gMSA Contoso has updated the name of the account and also the DNSHostName. 

As Contoso is deploying a base package of 10.0.29, the axserviceuser account is left as disabled since it will not be used.

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

#### Certificates

Contoso corporation has acquired a certificate from a public certificate authority for their ServiceFabric certificate. Since Contoso does not need the scripts to generate the certificate, they set **generateADCSCert** to false. Additionally, they fill in the thumbprint of the certificate so that it can be exported later on.

Contoso corporation has an Active Directory Certificate Services (ADCS) server and has decided to use it to generate all of the other certificates.

As Contoso corporation does not want to lose access to the certificate private keys if their IT administrator leaves, they have set the **ProtectTo** field to an Active Directory group that all of their IT administrators are a part of. This is a best practice instead of specifying a single user.

As they did previously with the gMSA accounts, Contoso corporation has chosen to add the **-prod** suffix to all of their other certificates (except the SQLCluster, OnpremLocalAgent and RSAT certificates) to be able to distinguish them better.

According to the setup guide, the infrastructure scripts will autogenerate the information for the SQLCluster certificate as long as the SQLCluster configuration is specified further down in the configuration template. So they have left everything blank except for the **ProtectTo** field.

As this is not their first environment, Contoso corporation has already registered the OnpremLocalAgent certificate against their Azure AD tenant and don't have to regenerate a new one. They instead specify the thumbprint of the existing certificate and set **generateADCSCert** to false.

Eventhough Contoso corporation wants to use the Regression suite automation tool (RSAT), they have left the **disabled** filed of the RSAT certificate as false. They have done this because they are specifying the configuration for their production environment and RSAT should only be used with sandbox environments.

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
    <EnhancedKeyUsage>DocumentEncryption</EnhancedKeyUsage>
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

#### DBServer

Contoso corporation will dedicate the SQL Server cluster they have created to be used exclusively by their production instance of Dynamics 365 for Finance + Operations (on-premises). As such, they have opted to leave the default values for the **userName** field.

Additionally, Contoso wants to make use of the Entity Store feature so they set **generateUser** to true for the axdwadmin and axdwruntimeuser accounts. 

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

#### Databases

Contoso corporation will leave the default values for their database names (dbName). As they have not downloaded the empty or demo databases from LCS, they have not yet filled out the **BackupFile** field, but will ensure they fill it out later.

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

#### Fileshares

Contoso corporation has a file server with a single node, but will ensure that they setup a High Availability solution in the near future before they go live. For now, they have created specific volume to host the sfDiagnostics share and a separate volume to host the remaining shares. They have only filled out the BasePath field for each fileshare as the rest of the fields are filled out by the infrastructure scripts.

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

#### ServiceFabricCluster

To be able to correctly identify the cluster they are connected to Contoso coporation has updated the **ClusterName** to reflect that this is their production cluster.

Contoso corporation has observed that they have resource heavy batch jobs that run during normal operation hours. Since they don't want their users to be impacted they have chosen to split batch and interactive sessions into separate nodes. To accomplish this they have added the **BatchOnlyAOSNodeType** and **InteractiveOnlyAOSNodeType** node types and set the disabled field for the **AOSNodeType** to true.

Foreach machine that belongs to a nodetype they have filled in the VM name, the ip address of the VM as well as the fault domain and update domain.

Contoso corporation has a fault tolerant setup, however they don't have enough fault tolerance to provide 3 fault domains. As such, they have chosen to randomly assign the fault tolerance values so they are spread out across the minimum requirement of 3 fault domains.

Eventhough Contoso does not expect to need to update their cluster often, they know they must follow the best practices for update domain definition. They have ensured that each of the nodes for each node type are placed in different update domains. This ensures that if there is a cluster update/upgrade only one node of each nodetype will be taken down simultaneously.

Contoso has noticed that since Application version 10.0.32 a new service has been introduced for the Data Management Framework. This removes the need to have SSIS installed and licensed on all AOS nodes. They are also aware that they could disable the **SSISNodeType** node type, and use the **ReportServerType** node type to host the DMF service instead. They could do this by setting the **hasSSIS** to true on each **ReportServerType**. However, they have very resource intensive DMF operations so they would not want to disrupt their report generation. As such, they have opted for having dedicated nodes for this service. 

To make it easier to find the **FabricDataRoot** and **FabricLogRoot** folders, Contoso corporation has updated the paths so they are in the root directory.

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
        <VM name="LBDEN01SSSIS1" ipAddress="10.0.0.51" faultDomain="fd:/fd2" updateDomain="ud2" />
        <VM name="LBDEN01SSSIS2" ipAddress="10.0.0.52" faultDomain="fd:/fd1" updateDomain="ud0" />
      </VMList>
    </NodeType>
    <ServiceFabricSettings>
      <Setting name="Setup" disabled="false">
        <Parameters>
          <Parameter name="FabricDataRoot">C:\SF</Parameter>
          <Parameter name="FabricLogRoot">C:\SF\Log</Parameter>
        </Parameters>
      </Setting>
      <Setting name="PlacementAndLoadBalancing" disabled="false">
        <Parameters>
          <Parameter name="NodeTaggingEnabled">true</Parameter>
        </Parameters>
      </Setting>
    </ServiceFabricSettings>
  </ServiceFabricCluster>
```

#### SQLCluster

Contoso corporation has created a SQL Always on cluster with availability groups that consists of 2 VMs. They have added each SQLVM under the SQLVMList. Additionally, since they have availability groups, they have specified the listername of their availability group.

```xml
<SQLCluster>
  <ListenerName>LBDEN01SQLA</ListenerName>
  <SQLVMList>
    <SQLVM name="LBDEN01SQLA01" />
    <SQLVM name="LBDEN01SQLA02" />
  </SQLVMList>
</SQLCluster>
```
