---
# required metadata

title: Set up and deploy on-premises environments (Platform updates 8 and 11)
description: This topic provides information about how to plan, set up, and deploy an on-premises environment.
author: PeterRFriis
manager: AnnBe
ms.date: 03/05/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.custom: NotInToc
# ms.search.industry: 
ms.author: perahlff
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: Platform update 8

---

# Set up and deploy on-premises environments (Platform updates 8 and 11)

[!include [banner](../includes/banner.md)]

This topic describes how to plan your deployment, set up the infrastructure, and deploy Microsoft Dynamics 365 for Finance and Operations, Enterprise edition (on-premises), Platform updates 8 and 11.

> [!IMPORTANT]
> This topic applies only to deploying on-premises environments on Platform updates 8 and 11. For information about deploying to Platform update 12, see [Set up and deploy on-premises environments (Platform update 12 and later)](setup-deploy-on-premises-pu12.md).

## Finance and Operations components

The Finance and Operations application consists of three main components:

- Application Object Server (AOS)
- Business Intelligence (BI)
- Financial Reporting/Management Reporter

These components depend on the following system software:

- Microsoft Windows Server 2016
- Microsoft SQL Server 2016 SP1, which has the following features:
  - Full-text index search is enabled.
  - SQL Server Reporting Services (SSRS) - This is deployed on BI virtual machines.
  - SQL Server Integration Services (SSIS) - This is deployed on AOS virtual machines.

    > [!WARNING]
    > Full Text Search must be enabled.

- SQL Server Management Studio
- Standalone Microsoft Azure Service Fabric
- Microsoft Windows PowerShell 5.0 or later
- Active Directory Federation Services (AD FS) on Windows Server 2016
- Domain controller

  > [!WARNING]
  > The domain controller must be Microsoft Windows Server 2012 R2 or later and must have a domain functional level of 2012 R2 or more.    For more information about domain functional levels, see the following topics:
  >   - [What Are Active Directory Functional Levels](https://technet.microsoft.com/library/cc787290(v=ws.10).aspx)
  >   - [Understanding Active Directory Domain Services Functional Levels](https://technet.microsoft.com/library/understanding-active-directory-functional-levels(v=ws.10).aspx)

## Lifecycle Services

Finance and Operations bits are distributed through Microsoft Dynamics Lifecycle Services (LCS). Before you can deploy, you must purchase license keys through the [Enterprise Agreements](https://www.microsoft.com/Licensing/licensing-programs/enterprise.aspx) channel and set up an on-premises project in LCS. Deployments can be initiated only through LCS. For more information about how to set up on-premises projects in LCS, see [Set up on-premises projects in Lifecycle Services (LCS)](../lifecycle-services/lbd-create-lcs-on-prem-project.md).

## Authentication

The on-premises application works with AD FS. To interact with LCS, you must also configure Azure Active Directory (AAD). And, to complete the deployment and configure the LCS Local agent, you will need AAD.

## Standalone Service Fabric

Finance and Operations uses standalone Service Fabric. For more information, see the [Service Fabric documentation](/azure/service-fabric/).

Setup of Finance and Operations will deploy a set of applications inside Service Fabric (SF). During deployment, each node in the cluster will be defined via configuration to have one of the following node types:

- **AOSNodeType**: Hosts the application object server (business logic).
- **OrchestratorType**: Functions as Service Fabric primary nodes, and hosts deployment- and servicing logic.
- **ReportServerType**: Hosts SSRS and reporting logic.
- **MRType**: Hosts management reporting logic.

## Infrastructure

Finance and Operations is designed to work on a Hyper-V virtualized environment that is based on Windows Servers.

 > [!WARNING]
 > On-premises deployments of Finance and Operations are not supported on any public cloud infrastructure, including Azure.

The hardware configuration includes the following components:

- Standalone Service Fabric cluster that is based on Windows Server 2016 virtual machines (VMs)
- Microsoft SQL Server (both Clustered SQL and Always-On are supported)
- AD FS for authentication
- Server Message Block (SMB) version 3 file share for storage
- Optional: Microsoft Office Server 2017

For more information, see [System requirements for on-premises deployments](../../fin-ops/get-started/system-requirements-on-prem.md) and Sizing guidelines.

### Hardware layout

Plan your infrastructure and Service Fabric cluster based on the recommended sizing in [Hardware sizing requirements for on-premises environments](../../fin-ops/get-started/hardware-sizing-on-premises-environments.md). For more information about how to plan the Service Fabric cluster, see [Plan and prepare your Service Fabric standalone cluster deployment](/azure/service-fabric/service-fabric-cluster-standalone-deployment-preparation).

The following table shows an example of a hardware layout. This example is used throughout this topic to illustrate the setup.

> [!NOTE]
> The Primary node of the Service Fabric cluster must have at least three nodes. In this example, **OrchestratorType** is designated as the Primary node type.

| Machine purpose          | SF Node type     | Machine name    | IP address    |
|--------------------------|------------------|-----------------|---------------|
| Domain controller        |                  | DAX7SQLAODC1    | 10.179.108.2  |
| AD FS                    |                  | DAX7SQLAOADFS1  | 10.179.108.3  |
| File server              |                  | DAX7SQLAOFILE1  | 10.179.108.4  |
| SQL Always-On cluster    |                  | DAX7SQLAOSQLA01 | 10.179.108.5  |
|                          |                  | DAX7SQLAOSQLA02 | 10.179.108.6  |
|                          |                  | DAX7SQLAOSQLA   | 10.179.108.9  |
| Client                   |                  | SQLAOCLIENT1    | 10.179.108.11 |
| AOS 1                    | AOSNodeType      | SQLAOSF1AOS1    | 10.179.108.12 |
| AOS 2                    | AOSNodeType      | SQLAOSF1AOS2    | 10.179.108.13 |
| AOS 3                    | AOSNodeType      | SQLAOSF1AOS3    | 10.179.108.14 |
| Orchestrator 1           | OrchestratorType | SQLAOSF1ORCH1   | 10.179.108.15 |
| Orchestrator 2           | OrchestratorType | SQLAOSF1ORCH2   | 10.179.108.16 |
| Orchestrator 3           | OrchestratorType | SQLAOSF1ORCH3   | 10.179.108.17 |
| Management Reporter node | MRType           | SQLAOSMR1       | 10.179.108.18 |
| SSRS node                | ReportServerType | SQLAOSFBIN1     | 10.179.108.10 |

## Setup

### Prerequisites

Before you start the setup, the following prerequisites must be in place. The setup of these prerequisites is out of scope for this document.

- Active Directory Domain Services (AD DS) must be installed and configured in your network.
- AD FS must be deployed.
- SQL Server 2016 SP1 must be installed on the SSRS machines.
- SQL Server Reporting Services 2016 must be installed in **Native** mode on the SSRS machines.

The following prerequisite software is installed on the VMs by the infrastructure setup scripts downloaded from LCS.

| Node type | Component | Details |
|-----------|-----------|---------|
| AOS       | SNAC – ODBC driver | <https://www.microsoft.com/download/details.aspx?id=53339> |
| AOS       | The Microsoft .NET Framework version 2.0–3.5 (CLR 2.0) | **Windows Features:** NET-Framework-Features, NET-Framework-Core, NET-HTTP-Activation, NET-Non-HTTP-Activ |
| AOS       | The Microsoft .NET Framework version 4.0–4.6 (CLR 4.0) | **Windows Features:** NET-Framework-45-Features, NET-Framework-45-Core, NET-Framework-45-ASPNET, NET-WCF-Services45, NET-WCF-TCP-PortSharing45 |
| AOS       | Internet Information Services (IIS) | **Windows Features:** WAS, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs, Web-Server, Web-WebServer, Web-Security, Web-Filtering, Web-App-Dev, Web-Net-Ext, Web-Mgmt-Tools, Web-Mgmt-Console |
| AOS       | SQL Server Management Studio 17.2 | <https://go.microsoft.com/fwlink/?linkid=854085> |
| AOS       | Microsoft Visual C++ Redistributable Packages for Microsoft Visual Studio 2013 | <https://support.microsoft.com/help/3179560> |
| AOS       | Microsoft Access Database Engine 2010 Redistributable | <https://www.microsoft.com/download/details.aspx?id=13255> |
| BI        | .NET Framework version 2.0–3.5 (CLR 2.0) | **Windows features:** NET-Framework-Features, NET-Framework-Core, NET-HTTP-Activation, NET-Non-HTTP-Activ |
| BI        | .NET Framework version 4.0–4.6 (CLR 4.0) | **Windows features:** NET-Framework-45-Features, NET-Framework-45-Core, NET-Framework-45-ASPNET, NET-WCF-Services45, NET-WCF-TCP-PortSharing45 |
| BI        | SQL Server Management Studio 17.2 | <https://go.microsoft.com/fwlink/?linkid=854085> |
| MR        | .NET Framework version 2.0–3.5 (CLR 2.0) | **Windows features:** NET-Framework-Features, NET-Framework-Core, NET-HTTP-Activation, NET-Non-HTTP-Activ |
| MR        | .NET Framework version 4.0–4.6 (CLR 4.0) | **Windows features:** NET-Framework-45-Features, NET-Framework-45-Core, NET-Framework-45-ASPNET, NET-WCF-Services45, NET-WCF-TCP-PortSharing45 |
| MR        | Visual C++ Redistributable Packages for Visual Studio 2013 | <https://support.microsoft.com/help/3179560> |

### Overview

The following steps must be completed to set up the infrastructure for Finance and Operations.

1. [Plan your domain name and DNS zones](#plandomain)
2. [Plan and acquire your certificates](#plancert)
3. [Plan your users and service accounts](#plansvcacct)
4. [Create DNS zones, and add A records](#createdns)
5. [Join VMs to the domain](#joindomain)
6. [Download setup scripts from LCS](#downloadscripts)
7. [Describe your configuration](#describeconfig)
8. [Configure certificates](#configurecert)
9. [Setup VMs](#setupvms)
10. [Set up a standalone Service Fabric cluster](#setupsfcluster)
11. [Configure LCS connectivity for the tenant](#configurelcs)
12. [Set up file storage](#setupfile)
13. [Set up SQL Server](#setupsql)
14. [Configure the databases](#configuredb)
15. [Encrypt credentials](#encryptcred)
16. [Set up SSIS](#setupssis)
17. [Set up SSRS](#setupssrs)
18. [Configure AD FS](#configureadfs)
19. [Configure a connector and install an on-premises local agent](#configureconnector)
20. [Deploy your Finance and Operations (on-premises) environment from LCS](#deploy)
21. [Connect to your Finance and Operations (on-premises) environment](#connect)

### <a name="plandomain"></a> 1. Plan your domain name and DNS zones

We recommend that you use a publicly registered domain name for your production installation of AOS. In that way, the installation can be accessed outside the network, if outside access is required.

For example, if your company's domain is contoso.com, your zone for Finance and Operations (on-premises) might be d365ffo.onprem.contoso.com, and the host names might be as follows:

- ax.d365ffo.onprem.contoso.com for AOS machines
- sf.d365ffo.onprem.contoso.com for the Service Fabric cluster

### <a name="plancert"></a> 2. Plan and acquire your certificates

Secure Sockets Layer (SSL) certificates are required in order to secure a Service Fabric cluster and all the applications that are deployed. For your production and sandbox workloads, we recommend that you acquire certificates from a certificate authority (CA) such as [DigiCert](https://www.digicert.com/ssl-certificate/), [Comodo](https://ssl.comodo.com/), [Symantec](https://www.websecurity.symantec.com/ssl-certificate), [GoDaddy](https://www.godaddy.com/web-security/ssl-certificate), or [GlobalSign](https://www.globalsign.com/en/ssl/). If your domain is set up with [Active Directory Certificate Services](https://technet.microsoft.com/library/cc772393(v=ws.10).aspx) (AD CS), you can create the certificates through AD CS. Each certificate must contain a private key that was created for key exchange, and it must be exportable to a Personal Information Exchange (.pfx) file.

Self-signed certificates can be used only for testing purposes. For convenience, the setup scripts include scripts that generate and export self-signed certificates. As we've mentioned, these certificates can be used for testing purposes only.

| Purpose                                      | Explanation | Additional requirements |
|----------------------------------------------|-------------|-------------------------|
| SQL Server SSL certificate                   | This certificate is used to encrypt data that is transmitted across a network between an instance of SQL Server and a client application. | The domain name of the certificate should match the fully-qualified domain name (FQDN) of the SQL Server instance or listener. For example, if the SQL listener is hosted on the machine DAX7SQLAOSQLA, the certificate's DNS name is DAX7SQLAOSQLA.onprem.contoso.com. |
| Service Fabric Server certificate            | <p>This certificate is used to help secure the node-to-node communication between the Service Fabric nodes.</p> <p> This certificate is also used as the Server certificate that is presented to the client that connects to the cluster.</p> | <p>You can use the SSL wild card certificate of your domain. For example, \*.contoso.com.</p><p><strong>Note:</strong> The wild card certificate allows you to secure only the first level subdomain of the domain to which it is issued.</p><p>In this example, because your service fabric domain is sf.d365ffo.onprem.contoso.com, you must include this as a Subject Alternative Name (SAN) in the certificate. You will need to work with your certificate authority to acquire the additional SANs.</p> |
| Service Fabric Client certificate            | This certificate is used by clients to view and manage the Service Fabric cluster. | |
| Encipherment Certificate                     | This certificate is used to encrypt sensitive information such as the SQL Server password and user account passwords.  | <p> The certificate must be created by using the provider **Microsoft Enhanced Cryptographic Provider v1.0**. </p><p>The certificate key usage must include Data Encipherment (10) and should not include Server authentication or Client authentication.</p><p>For more information, see [Managing secrets in Service Fabric applications](/azure/service-fabric/service-fabric-application-secret-management).</p> |
| AOS SSL Certificate                          | <p>This certificate is used as the Server certificate that is presented to the client for the AOS website. It's also used to enable Windows Communication Foundation (WCF)/Simple Object Access Protocol (SOAP) certificates.</p><p>You can use the same wild card certificate that you used as the Service Fabric Server certificate.</p> | <p>In this example, the domain name ax.d365ffo.onprem.contoso.com must be added to the Subject Alternative Name (SAN) as in the Service  Fabric Server certificate.</p> |
| Session Authentication certificate           | This certificate is used by AOS to help secure a user's session information. | This certificate is also the File Share certificate that will used at the time of deployment from LCS. |
| Data Encryption certificate | This certificate is used by the AOS to encrypt sensitive information.  | This must be created using the provider **Microsoft Enhanced RSA and AES Cryptographic Provider**. |
| Data Signing certificate | This certificate is used by AOS to encrypt sensitive information.  | This is separate from the Data Encryption certificate and must be created using the provider **Microsoft Enhanced RSA and AES Cryptographic Provider**. |
| Financial Reporting client certificate       | This certificate is used to help secure the communication between the Financial Reporting services and the AOS. |  |
| Reporting certificate                        | This certificate is used to help secure the communication between SSRS and the AOS.| **Do not reuse the Financial Reporting Client certificate.** |
| On-Premise local agent certificate           | <p>This certificate is used to help secure the communication between a local agent that is hosted on-premises and on LCS.</p><p>This certificate enables the local agent to act on behalf of your Azure AD tenant, and to communicate with LCS to orchestrate and monitor deployments.</p><p><strong>Note:</strong> Only 1 on-premise local agent certificate is needed for a tenant.</p>| |

The following is an example of a Service Fabric Server certificate combined with an AOS SSL Certificate.

#### Subject name

```Text
CN = *.d365ffo.onprem.contoso.com
```

#### Subject Alternative Names

```Text
DNS Name=ax.d365ffo.onprem.contoso.com
DNS Name=sf.d365ffo.onprem.contoso.com
DNS Name=*.d365ffo.onprem.contoso.com
```

### <a name="plansvcacct"></a> 3. Plan your users and service accounts

You must create several user or service accounts for Finance and Operations (on-premises) to work. You must create a combination of group managed service accounts (gMSAs), domain accounts, and SQL accounts. The following table shows the user accounts, their purpose, and example names that will be used in this topic.

| User account                                            | Type           | Purpose | User name |
|---------------------------------------------------------|----------------|---------|-----------|
| Financial Reporting Application Service Account         | gMSA           |         | Contoso\\svc-FRAS$ |
| Financial Reporting Process Service Account             | gMSA           |         | Contoso\\svc-FRPS$ |
| Financial Reporting Click Once Designer Service Account | gMSA           |         | Contoso\\svc-FRCO$ |
| AOS Service Account                                     | gMSA           | This user should be created for future-proofing. We plan to enable AOS to work with the gMSA in upcoming releases. By creating this user at the time of setup, you will help to ensure a seamless transition to the gMSA. | Contoso\\svc-AXSF$ |
| AOS Service Account                                     | Domain account | AOS uses this user in the general availability (GA) release. | Contoso\\AXServiceUser |
| AOS SQL DB Admin user                                   | SQL user       | Finance and Operations uses this user to authenticate with SQL\*. This user will also be replaced by the gMSA user in upcoming releases. | AXDBAdmin |
| Local Deployment Agent Service Account                  | gMSA           | This account is used by the local agent to orchestrate the deployment on various nodes. | Contoso\\Svc-LocalAgent$ |

\* The SQL user name and password for SQL authentication are secured because they are encrypted and stored in the file share.

### <a name="createdns"></a> 4. Create DNS zones and add A records

DNS is integrated with AD DS, and lets you organize, manage, and find resources in a network. Create a DNS forward lookup zone and A records for the AOS host name and the Service Fabric cluster. In this example setup, the DNS zone name is d365ffo.onprem.contoso.com, and the A records/host names are as follows:

- **ax**.d365ffo.onprem.contoso.com for AOS machines
- **sf**.d365ffo.onprem.contoso.com for the Service Fabric cluster

#### Add a DNS zone

Use the following procedure to add a DNS zone.

1. Sign in to the domain controller machine, select **Start**, and start DNS Manager by typing **dnsmgmt.msc**.
2. Right-click the domain controller name, and then select **New Zone** \> **Next**.
3. Select **Primary Zone**.
4. Leave the **Store the zone in Active Directory (available only if the DNS Server is a writeable domain controller** check box selected, and then select **Next**.
5. Select **To all DNS Servers running on Domain Controllers in this domain: Contoso.com**, and then select **Next**.
6. Select **Forward Lookup Zone**, and then select **Next**.
7. Enter the zone name for your setup, and then select **Next**. For example, enter **d365ffo.onprem.contoso.com**.
8. Select **Do not allow dynamic updates**, and then select **Next**.

#### Set up an A record for AOS

In the new DNS zone, create one A record that is named **ax.d365ffo.onprem.contoso.com** for **each** Service Fabric cluster node of the **AOSNodeType** type. Don't create A records for the other node types.

1. Right-click the new zone, and then select **New Host**.
2. Enter the name and IP address of the Service Fabric node. (For example, enter **10.179.108.12** as the IP address.) Select **Add Host**.

#### Set up an A record for the orchestrator

In the new DNS zone, create an A record that is named **sf.d365ffo.onprem.contoso.com** for **each** Service Fabric cluster node of the **OrchestratorType** type. Don't create A records for the other node types.

1. Right-click the new zone, and then select **New Host**.
2. Enter the name and IP address of the Service Fabric node. (For example, enter **10.179.108.15** as the IP address.) Select **Add Host**.

### <a name="joindomain"></a> 5. Join VMs to the domain

Join each VM to the domain by completing the steps in [How to join Windows Server 2016 to an Active Directory domain](https://www.tomsitpro.com/articles/join-windows-server-2016-to-ad-domain,2-1063.html). Alternatively, use the following Windows PowerShell script.

```powershell
$domainName = Read-Host -Prompt 'Specify domain name (ex: contoso.com)'
Add-Computer -DomainName $domainName -Credential (Get-Credential -Message 'Enter domain credential')
```

> [!IMPORTANT]
> You must restart the VMs after you join them to the domain.

After the VMs are joined to the domain, add the AOS Service Accounts, **Contoso\svc-AXSF$** and **Contoso\AXServiceUser** to the local administrators group. For more information, see [Add a member to local group](https://technet.microsoft.com/library/cc772524(v=ws.11).aspx).

### <a name="downloadscripts"></a> 6. Download setup scripts from LCS

> [!IMPORTANT]
> The scripts must be executed from a computer in the same domain that the on-premises infrastructure is in.

1. Sign in to [LCS](https://lcs.dynamics.com/v2).
2. On the dashboard, select the **Shared asset library** tile.
3. On the **Model** tab, in the grid, select the **Dynamics 365 for Operations on-premises - Deployment scripts - Latest** row.
4. Click the **Versions** button, and then select **Version 1**.
5. Right-click the zip file, and then select **Properties**. In the dialog box, select the **Unblock** check box.
6. Copy the zip file to the machine that will be used to execute the scripts.
7. Unzip the files into a folder that is named **infrastructure**.

> [!IMPORTANT]
> Ensure all edits are made to the ConfigTemplate.xml in this folder.

### <a name="describeconfig"></a> 7. Describe your configuration

The infrastructure setup scripts use the following configuration files to drive the setup.
- infrastructure\ConfigTemplate.xml
- infrastructure\D365FO-OP\NodeTopologyDefintion.xml
- infrastructure\D365FO-OP\DatabaseTopologyDefintion.xml

**infrastructure\ConfigTemplate.xml** describes:
- Service Accounts that are needed for the application to operate
- Certificates necessary for securing communications
- Database configuration
- Service Fabric cluster configuration

For each Service Fabric Node type, **infrastructure\D365FO-OP\NodeTopologyDefinition.xml** describes:

- The mapping between each node type and the application, domain and service accounts, and certificates.
- Whether to enable the UAC
- Prerequisites for Windows features and system software
- Whether strong name validation should be enabled
- List of firewall ports to be opened

For each database, **infrastructure\D365FO-OP\DatabaseTopologyDefinition.xml** describes:

- The DB settings
- The mappings between users and roles

#### Create gMSA and domain user accounts

1. Navigate to the machine that has the unzipped infrastructure scripts in the **infrastructure** folder.
2. Copy the **infrastructure** folder to the domain controller machine.
3. Start Windows PowerShell in elevated mode, change the directory to the **infrastructure** folder, and run the following commands.

    ```powershell
    Import-Module .\D365FO-OP\D365FO-OP.psd1
    New-D365FOGMSAAccounts -ConfigurationFilePath .\ConfigTemplate.xml
    ```

4. If you must make changes to accounts or machines, update the ConfigTemplate.xml file in the original **infrastructure** folder, copy it to this machine and then run the following script.

    ```powershell
    Update-D365FOGMSAAccounts -ConfigurationFilePath .\ConfigTemplate.xml
    ```

### <a name="configurecert"></a> 8. Configure certificates

1. Navigate to the machine that has the **infrastructure** folder.
2. If you must generate self-signed certificates, run the following command. The script will create the certificates, put them in the CurrentUser\My certificate store on the machine, and update the thumbprints in the XML file.

    ```powershell
    # Create self-signed certs
    .\New-SelfSignedCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

    If you must reuse any certificates and therefore don't have to generate certificates for them, set the **generateSelfSignedCert** tag to **false**.

3. If you're using SSL certificates that were already generated, skip the Certificate generation and update the thumbprints in the configTemplate.xml file. The certificates need to be installed in the CurrentUser\My store and their private keys must be exportable.

    > [!WARNING]
    > Because of a leading not-printable special character, which is difficult to determine when present, the cert manager should not be used to copy thumbprints. If the not-printable special character is present, you will get **X509 certificate not valid** error. To retrieve the thumbprints, see results from PowerShell commands or run the following commands in PowerShell.
    > ```powershell
    > dir cert:\CurrentUser\My
    > dir cert:\LocalMachine\My
    > dir cert:\LocalMachine\Root
    > ```

4. Specify a semi-colon separated list of users or groups in the **ProtectTo** tag for each certificate. Only Active directory users and groups specified in the **ProtectTo** tag will have permissions to import the certificates that are exported using the scripts. Passwords are not supported by the script to protect the exported certificates

5. Export the certificates into .pfx files.

    ```powershell
    # Exports Pfx files into a directory VMs\<VMName>, all the certs will be written to infrastructure\Certs folder.
    .\Export-PfxFiles.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

### <a name="setupvms"></a> 9. Setup VMs
1. Export the scripts that must be run on each VM.

    ```powershell
    # Exports the script files to be execute on each VM into a directory VMs\<VMName>.
    .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

2. Download the following Microsoft Windows Installers (MSIs) into a file share that is accessible by all VMs.

    | Component | Download link |
    |-----------|---------------|
    | SNAC – ODBC driver | <https://www.microsoft.com/download/details.aspx?id=53339> |
    | Microsoft SQL Server Management Studio 17.2 | <https://go.microsoft.com/fwlink/?linkid=854085> |
    | Microsoft Visual C++ Redistributable Packages for Microsoft Visual Studio 2013 | <https://support.microsoft.com/help/3179560> |
    | Microsoft Access Database Engine 2010 Redistributable | <https://www.microsoft.com/download/details.aspx?id=13255> |

#### Follow these steps for each VM

1. Copy the contents of each infrastructure\VMs\<VMName> folder into the corresponding VM, and then run the following scripts.

    ```powershell
    # Install pre-req software on the VMs.
    .\Configure-PreReqs.ps1 -MSIFilePath <path of the MSIs>
    ```

    > [!IMPORTANT]
    > Restart the machine each time you're prompted to restart it. Make sure that you rerun the `.\Configure-PreReqs.ps1` script after each restart until all the prerequisites are installed.

2. Run the following scripts, if they exist, in order to complete the VM setup.

    ```powershell
    .\Add-GMSAOnVM.ps1
    .\Import-PfxFiles.ps1
    .\Set-CertificateAcls.ps1
    ```

3. Run the following script to validate the VM setup.

    ```powershell
    .\Test-D365FOConfiguration.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

### <a name="setupsfcluster"></a> 10. Set up a standalone Service Fabric cluster

1. Download the [Service Fabric standalone installation package](https://go.microsoft.com/fwlink/?LinkId=730690) onto one of your Service Fabric nodes. After the zip file is downloaded, unblock it by right-clicking the zip file and then selecting **Properties**. In the dialog box, select the **Unblock** check box in the lower right.

2. Copy the zip file to one of the nodes in the Service Fabric cluster, and unzip it. Ensure the **infrastructure** folder has access to this folder.

3. Navigate to the **infrastructure** folder and execute the following command to generate the Service Fabric ClusterConfig.json file.

    ```powershell
   .\New-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -TemplateConfig <ServiceFabricStandaloneInstallerPath>\ClusterConfig.X509.MultiMachine.json
    ```

    For more information, see, [Step 1B: Create a multi-machine cluster](/azure/service-fabric/service-fabric-cluster-creation-for-windows-server#create-the-cluster), [Secure a standalone cluster on Windows using X.509 certificates](/azure/service-fabric/service-fabric-windows-cluster-x509-security), and [Create a standalone cluster running on Windows Server](/azure/service-fabric/service-fabric-cluster-creation-for-windows-server#create-the-cluster).

4. Copy the generated ClusterConfig.json file to the \<ServiceFabricStandaloneInstallerPath\>.

5. Navigate to the \<ServiceFabricStandaloneInstallerPath\> in Windows PowerShell by using elevated privileges. Run the following command to test ClusterConfig.

    ```powershell
    .\TestConfiguration.ps1 -ClusterConfigFilePath .\clusterConfig.json
    ```

6. If the test is successful, run the following command to deploy the cluster.

    ```powershell
    .\CreateServiceFabricCluster.ps1 -ClusterConfigFilePath .\ClusterConfig.json
    ```

7. After the cluster is created, open the Service Fabric explorer on any client machine to validate the installation.

    1. Install the Service Fabric client certificate in CurrentUser\\My if it isn't already installed.
    2. Go to **IE settings** \> **Compatibility Mode**, and clear the **Display Intranet sites in compatibility mode** check box.
    3. Go to `https://sf.d365ffo.onprem.contoso.com:19080`, where sf.d365ffo.onprem.contoso.com is the host name of the Service Fabric cluster that is specified in the zone. If DNS name resolution isn't configured, use the IP address of the machine.
    4. Select the client certificate. The **Service Fabric explorer** page appears.

### <a name="configurelcs"></a> 11. Configure LCS connectivity for the tenant

Deployment and servicing of Finance and Operations is orchestrated through LCS by using an on-premises local agent. To establish connectivity from LCS to the Finance and Operations tenant, you must configure a certificate that enables the local agent to act on behalf on your Azure AD tenant (for example, Contoso.onmicrosoft.com).

Use the on-premises agent certificate that you acquired from a CA or the self-signed certificate that you generated by using scripts.

The on-premises agent certificate can be reused across multiple sandbox and production environments per tenant.

Only user accounts that have the Global Administrator directory role can add certificates to authorize LCS. By default, the person who signs up for Microsoft Office 365 for your organization is the global administrator for the directory.

> [!IMPORTANT]
> You must configure the certificate exactly one time per tenant. All on-premises environments can use the same certificate to connect with LCS.

1. Download and install the latest version of Azure PowerShell on a client machine. For more information, see [Installing the Azure PowerShell Service Management module](https://docs.microsoft.com/powershell/azure/servicemanagement/install-azure-ps?view=azuresmps-4.0.0).
2. Sign in to the [customer's Azure portal](https://portal.azure.com) to verify that you have the Global Administrator directory role.
3. Run the following script from $(DownloadPath)\\InfrastructureScripts.
    ```powershell
    .\AddCertToServicePrincipal.ps1 -CertificateThumbprint <OnPremLocalAgent Certificate Thumbprint>
    ```

### <a name="setupfile"></a> 12. Set up file storage

You must set up the following SMB 3.0 file shares:

- A file share that stores user documents that are uploaded to AOS (for example, \\\\DAX7SQLAOFILE1\\aos-storage).
- A file share that stores the latest build and configuration files to orchestrate the deployment (for example, \\\\DAX7SQLAOFILE1\\agent).

    > [!WARNING]
    > Keep this file share path as short as possible to avoid exceeding the maximum path length on the files that will be put in the share.

For information about how to enable SMB 3.0, see [SMB Security Enhancements](https://technet.microsoft.com/library/dn551363(v=ws.11).aspx#BKMK_disablesmb1).

> [!IMPORTANT]
> - Secure dialect negotiation can't detect or prevent downgrades from SMB 2.0 or 3.0 to SMB 1.0. Therefore, we strongly recommend that you disable the SMB 1.0 server. By disabling the SMB 1.0 server, you can take advantage of the full capabilities of SMB encryption.
> - To help ensure that your data is protected while it's at rest in your environment, BitLocker Drive Encryption must be enabled on every machine. For information about how to enable BitLocker, see [BitLocker: How to deploy on Windows Server 2012 and later](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-how-to-deploy-on-windows-server).

1. On the file share machine, run the following command.

    ```powershell
    Install-WindowsFeature -Name FS-FileServer -IncludeAllSubFeature -IncludeManagementTools
    ```

2. Follow these steps to set up the \\\\DAX7SQLAOFILE1\\aos-storage file share:

    1. In Server Manager, select **File and Storage Services** \> **Shares**.
    2. Select **Tasks** \> **New Share** to create a new share. Name the share **aos-storage**.
    3. Grant **Modify** permissions for every machine in the Service Fabric cluster except OrchestratorType.
    4. Grant **Modify** permissions for the user AOS domain user (contoso\\AXServiceUser) and the gMSA user (contoso\\svc-AXSF$).

3. Follow these steps to set up the \\\\DAX7SQLAOFILE1\\agent file share:

    1. In Server Manager, select **File and Storage Services** \> **Shares**.
    2. Select **Tasks** \> **New Share** to create a new share. Name the share **agent**.
    3. Grant **Full-Control** permissions to the gMSA user for the local deployment agent (contoso\\svc-LocalAgent$).

### <a name="setupsql"></a> 13. Set up SQL Server

1. Install SQL Server 2016 SP1 with high availability. (Unless you're deploying in a sandbox environment, where one instance of SQL Server is sufficient. You may want to install SQL Server with high availability in sandbox environments to test high availability scenarios.)

    You can install SQL Server with high availability either as SQL clusters that include a Storage Area Network (SAN) or in an Always-On configuration. Verify that the Database Engine, SSRS, Full-Text Search, and Management Tools are already installed.

    > [!NOTE]
    > Make sure that Always-On is set up as described in [Select Initial Data Synchronization Page (Always On Availability Group Wizards)](/sql/database-engine/availability-groups/windows/select-initial-data-synchronization-page-always-on-availability-group-wizards), and follow the instructions in [To Prepare Secondary Databases Manually](/sql/database-engine/availability-groups/windows/select-initial-data-synchronization-page-always-on-availability-group-wizards#PrepareSecondaryDbs).

2. Run the SQL service as a domain user.
3. Get an SSL certificate from a CA to configure Finance and Operations. For testing purposes, you can create and use a self-signed certificate.

    **Self-signed certificate for a Clustered SQL instance**

    ```powershell
    New-SelfSignedCertificate -CertStoreLocation "cert:\CurrentUser\My" -DnsName "DAX7SQLAOSQLA.contososqlao.com" -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" -Subject "DAX7SQLAOSQLA.contososqlao.com"
    ```

    **Self-signed certificate for an Always-On SQL instance**

    **Manual** creation of test certificates:
    ```powershell
    # https://www.derekseaman.com/2014/11/sql-2014-alwayson-ag-pt-13-ssl.html

    # Manually create certificate for each SQL Node (i.e. 2 nodes = 2 certificates)
    # Run script on each node
    $computerName = $env:COMPUTERNAME.ToLower()
    $domain = $env:USERDNSDOMAIN.ToLower()
    $listenerName = 'dax7sqlaosqla'
    $cert = New-SelfSignedCertificate -Subject "$computerName.$domain" -DnsName "$listenerName.$domain", $listenerName, $computerName -Provider 'Microsoft Enhanced RSA and AES Cryptographic Provider'
    ```

4. Use the certificate(s) to configure SSL on SQL Server. Follow the steps in [How to enable SSL encryption for an instance of SQL Server by using Microsoft Management Console](https://support.microsoft.com/help/316898/how-to-enable-ssl-encryption-for-an-instance-of-sql-server-by-using-microsoft-management-console).
5. For each node of the SQL cluster, follow these steps. Make sure that you make the changes on the non-active node, and that you fail over to it after changes are made.

    1. Import the certificate into LocalMachine\\My, unless you are setting up Always-On, in which case the certificate already exists on the node.
    2. Grant certificate permissions to the service account that is used to run the SQL service. In Microsoft Management Console (MMC), right-click the certificate (**certlm.msc**), and then select **Tasks** \> **Manage Private Keys**.
    3. Add the certificate thumbprint to HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\*MSSQL.x*\\MSSQLServer\\SuperSocketNetLib\\Certificate.
    4. In Microsoft SQL Server Configuration Manager, set **ForceEncryption** to **Yes**.

6. Export the public key of the certificate (the .cer file), and install it in the trusted root of each Service Fabric node.

### <a name="configuredb"></a> 14. Configure the databases

1. Sign in to [LCS](https://lcs.dynamics.com/v2).

2. On the dashboard, select the **Shared asset library** tile.

3. On the **Model** tab, select the demo data for the release you want and download the zip file.

    | Release | Demo Data |
    |-------|------|
    | On-premises General Availability (GA) release | Dynamics 365 for Operations (on-premises) - Demo data |
    | On-premises Platform Update 11 Nov 2017 release | Dynamics 365 for Operations, Enterprise edition (on-premises) - Update 11 Demo data |

4. The zip file contains empty and demo data .bak files. Select .bak file, based on your requirements. For example, if you require demo data, download the AxBootstrapDB_Demodata.bak file.

5. Ensure the database section in the infrastructure\ConfigTempate.xml is configured correctly with the following:
    1. The database name.
    2. The db file and log settings. The db settings should not be lower than the defaults specified.
    3. The path to the backup file downloaded from LCS Shared Asset library. The default name for the Finance and Operations database is AXDB.

   > [!WARNING]
   > 1. The user running the SQL service and the user running the scripts should have READ access on the folder or share where the backup file is located.
   > 
   > 2. If a database with the same name exists, the database will be reused.

6. Copy the **infrastructure** folder to the SQL Server machine and navigate to it in a PowerShell window with elevate privileges.

#### Configure the OrchestratorData database

1. Execute the following script.

   ```powershell
   .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName Orchestrator
   ```

   The script will do the following:
  
   - Create an empty database named **OrchestratorData**. This database is used by the on-premises local agent to orchestrate deployments.
   - Grant the local agent gMSA (svc-LocalAgent$) **db\_owner** permissions on the database.

#### Configure the Finance and Operations database

1. Execute the following scripts.

   ```powershell
   .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName AOS
   .\Configure-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName AOS
   ```

   The **Initialize-Database.ps1** script will do the following:

   1. Restore the database from the specified backup file.
   2. Create a new user that has SQL authentication enabled (axdbadmin).
   3. Map users to database roles based on the following table for AXDB.

      | User            | Type    | Database role |
      |-----------------|---------|---------------|
      | svc-AXSF$       | gMSA    | db\_owner     |
      | svc-LocalAgent$ | gMSA    | db\_owner     |
      | svc-FRPS$       | gMSA    | db\_owner     |
      | svc-FRAS$       | gMSA    | db\_owner     |
      | axdbadmin       | SqlUser | db\_owner     |


   4. Map users to database roles based on the following table for TempDB.

      | User            | Type    | Database role |
      |-----------------|---------|---------------|
      | svc-AXSF$       | gMSA    | db_datareader, db_datawriter, db_ddladmin     |
      | axdbadmin       | SqlUser | db_datareader, db_datawriter, db_ddladmin     |

   The **Configure-Database.ps1** script will do the following:

    1. Set READ_COMMITTED_SNAPSHOT ON
    2. Set ALLOW_SNAPSHOT_ISOLATION ON
    3. Set the specified database file and log settings
    4. GRANT VIEW SERVER STATE TO axdbadmin
    5. GRANT VIEW SERVER STATE TO [contoso\svc-AXSF$]

2. Run the following command to reset the database users.

    ```powershell
    .\Reset-DatabaseUsers.ps1 -DatabaseServer '<FQDN of the SQL server>' -DatabaseName '<AX database name>'
    ```

#### Configure the Financial Reporting database

1. Execute the following script.

   ```powershell
   .\Initialize-Database.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -ComponentName MR
   ```

   The script will do the following:
   1. Create an empty database named **FinancialReporting**.
   2. Map the users to database roles based on the following table.

      | User            | Type | Database role |
      |-----------------|------|---------------|
      | svc-LocalAgent$ | gMSA | db\_owner     |
      | svc-FRPS$       | gMSA | db\_owner     |
      | svc-FRAS$       | gMSA | db\_owner     |

### <a name="encryptcred"></a> 15. Encrypt credentials

1. On any client machine, install the encipherment certificate in the LocalMachine\\My certificate store.
2. Grant the current user read access to the private key of this certificate.
3. Create the Credentials.json file, as shown here.

    ```json
    {
        "AosPrincipal": {
            "AccountPassword": "<encryptedDomainUserPassword>"
        },
        "AosSqlAuth": {
            "SqlUser": "<encryptedSqlUser>",
            "SqlPwd": "<encryptedSqlPassword>"
        }
    }
    ```

    - **AccountPassword** is the encrypted domain user password for the AOS domain user (contoso\\axserviceuser).
    - **SqlUser** is the encrypted SQL user (axdbadmin) that has access to the Finance and Operations database (AXDB), and **SqlPassword** is the encrypted SQL password.

4. Copy the .json file to the SMB file share, \\\\AX7SQLAOFILE1\\agent\\Credentials\\Credentials.json.
5. Update the Credentials.json file with encrypted values.

    ```powershell
    # Service fabric API to encrypt text and copy it to the clipboard.
    Invoke-ServiceFabricEncryptText -Text '<textToEncrypt>' -CertThumbprint '<DataEncipherment Thumbprint>' -CertStore -StoreLocation LocalMachine -StoreName My | Set-Clipboard
    ```

### <a name="setupssis"></a> 16. Set up SSIS

To enable Data management and Integration workloads, SSIS must be installed on each of the AOS virtual machines. Complete the following steps on each AOS virtual machine.

1. Verify that the machine has access to the SSIS installation and open the SSIS Setup Wizard.
2. In the **Feature Selection** window, in the **Features** pane, select the **Integration Services** and **SQL Client Connectivity SDK** check boxes.
3. Complete the setup and verify that the installation was successful.

For more information, see [Install integration services](https://docs.microsoft.com/sql/integration-services/install-windows/install-integration-services).

### <a name="setupssrs"></a> 17. Set up SSRS

1. Before you begin, make sure that the prerequisites that are listed at the beginning of this topic are installed.
2. Follow the steps in [Configure SQL Server Reporting Services for on-premises deployments](../analytics/configure-ssrs-on-premises.md).

### <a name="configureadfs"></a> 18. Configure AD FS

Before you can complete this procedure, AD FS must be deployed on Windows Server 2016. For information about how to deploy AD FS, see [Deployment Guide Windows Server 2016 and 2012 R2 AD FS Deployment Guide](/windows-server/identity/ad-fs/deployment/windows-server-2012-r2-ad-fs-deployment-guide).

Finance and Operations requires additional configuration beyond the default out-of-box configuration of AD FS. For the following steps, Windows PowerShell runs on a machine where the AD FS role service is installed. The user account must have enough permissions to administer AD FS. For example, the user must have a domain administrator account.

1. Configure the AD FS identifier so that it matches the AD FS token issuer.

    ```powershell
    $adfsProperties = Get-AdfsProperties
    Set-AdfsProperties -Identifier $adfsProperties.IdTokenIssuer
    ```

2. You should disable Windows Integrated Authentication (WIA) for intranet authentication connections, unless you've configured AD FS for mixed environments. For more information about how to configure WIA so that it can be used with AD FS, see [Configure browsers to use Windows Integrated Authentication (WIA) with AD FS](/windows-server/identity/ad-fs/operations/configure-ad-fs-browser-wia).

    ```powershell
    Set-AdfsGlobalAuthenticationPolicy -PrimaryIntranetAuthenticationProvider FormsAuthentication, MicrosoftPassportAuthentication
    ```

3. For sign-in, the user's email address must be an acceptable authentication input.

    ```powershell
    Add-Type -AssemblyName System.Net
    $fqdn = ([System.Net.Dns]::GetHostEntry('localhost').HostName).ToLower()
    $domainName = $fqdn.Substring($fqdn.IndexOf('.')+1)
    Set-AdfsClaimsProviderTrust -TargetIdentifier 'AD AUTHORITY' -AlternateLoginID mail -LookupForests $domainName
    ```

In order for AD FS to trust Finance and Operations for the exchange of authentication, various application entries must be registered in AD FS under an AD FS application group. To speed up the setup process and help reduce errors, you can use the following script for registration. Copy the Publish-ADFSApplicationGroup.ps1 script and D365FO-OP directory to a machine where the AD FS role service is installed. Then run the script by using a user account that has enough permissions to administer AD FS. (For example, use an administrator account.)

For more information about how to use the script, see the documentation that is listed in the script. Make a note of the client IDs that are specified in the output, because you will need this information in LCS in a later step. Should you lose the client IDs, log in to the machine which has AD FS installed, open **Server Manager** \> **Tools** \> **AD FS Management** \> **Application Groups** \> **Microsoft Dynamics 365 for Operations On-premises** and find the client IDs under the native applications.

```powershell
# Host URL is your DNS record\host name for accessing the AOS
.\Publish-ADFSApplicationGroup.ps1 -HostUrl 'https://ax.d365ffo.onprem.contoso.com'
```

![Application group properties](./media/OPSetup_05_ApplicatioGroupProperties.png)

Finally, make sure that you can access the AD FS OpenID Configuration URL on a Service Fabric node of the **AOSNodeType** type. To perform this check, try to open `https://<adfs-dns-name>/adfs/.well-known/openid-configuration` in a web browser. If you receive a message that states that the site isn't secure, you haven't added your AD FS SSL certificate to the Trusted Root Certification Authorities store. This step is described in the AD FS deployment guide.

If you successfully access the URL, a JavaScript Object Notation (JSON) file is returned that contains your AD FS configuration, and you will see that your AD FS URL is trusted.

You've now completed the setup of the infrastructure. The following sections describe how to navigate to [LCS](https://lcs.dynamics.com) to set up your connector and deploy your Finance and Operations environment.

### <a name="configureconnector"></a> 19. Configure a connector and install an on-premises local agent

1. Sign in to [LCS](https://lcs.dynamics.com/), and open the on-premises implementation project.
2. On the hamburger menu, select **Project settings**.

    ![Project settings command](./media/OPSetup_06_ProjectSettings.png)

3. Select **On-premises connectors**.
4. Select **Add** to create a new connector.
5. On the **Setup host infrastructure** tab, download the agent installer.

    ![Download agent installer button on the Setup host infrastructure tab](./media/OPSetup_07_DownloadAgentInstaller.png)
6. Verify that the zip file is unblocked. Right-click the file, and then select **Properties**. In the dialog box, select **Unblock**.
7. Unzip the agent installer on one of the Service Fabric nodes of the **OrchestratorType** type.
8. On the **Configure agent** tab, enter the configuration settings.
9. Save the configuration, and then select **Download configurations** to download the localagent-config.json configuration file.

    ![Download configurations button on the Configure agent tab](./media/OPSetup_08_DownloadConfigurations.png)

10. Copy the localagent-config.json file to the machine where the agent installer package is located.
11. In a **Command Prompt** window, run the following command by navigating to the folder that contains the agent installer.

    ```powershell
    LocalAgentCLI.exe Install <path of config.json>
    ```

    > [!NOTE]
    > The user who runs this command must have **db\_owner** permissions on the OrchestratorData database.

12. After the local agent is successfully installed, navigate back to your on-premises connector in LCS.
13. On the **Validate setup** tab, select **Message agent** to test for LCS connectivity to your local agent. When a connection is successfully established, the page will resemble the following illustration.

    ![Validate the agent](./media/ValidateAgent.PNG)

### <a name="deploy"></a> 20. Deploy your Finance and Operations (on-premises) environment from LCS

1. In LCS, navigate to your on-premises project, go to **Environment** > **Sandbox**, and then select **Configure**.
2. For new deployments, select your environment topology, and then complete the wizard to start your deployment.
3. If you have an existing deployment, see the topic [Redeploy on-premises environments](redeploy-on-prem.md).
4. The local agent will pick up the deployment request, start the deployment, and communicate back to LCS when the environment is ready.

If the deployment fails, the **Reconfigure** button will become available for your environment in LCS. Fix the underlying issue, click **Reconfigure**, update any configuration changes, and click **Deploy** to retry the deployment.

### <a name="connect"></a> 21. Connect to your Finance and Operations (on-premises) environment

In your browser, navigate to https://[yourD365FOdomain]/namespaces/AXSF, where yourD365FOdomain is the domain name that you defined in the [Plan your domain name and DNS zones](#plandomain) section of this document.

## Additional resources
- [Apply updates to on-premises deployments](apply-updates-on-premises.md)
- [Redeploy on-premises environments](redeploy-on-prem.md)
