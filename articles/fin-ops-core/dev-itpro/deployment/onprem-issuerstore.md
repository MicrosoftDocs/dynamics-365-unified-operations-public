---
title: Migrate to issuer store validation and dedicated cluster certificate for Service Fabric
description: Learn how to migrate your on-premises Service Fabric cluster to the issuer store validation model and a dedicated cluster certificate.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.custom:
  - bap-template
ms.date: 05/12/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.service: dynamics-365-op
---

# Migrate to issuer store validation and dedicated cluster certificate for Service Fabric

This article explains how to migrate an existing Finance + Operations (on-premises) Service Fabric cluster from the pinned certificate issuer validation model to the issuer store model, and how to adopt the new dedicated **ServiceFabricCluster** certificate. Together, these changes provide more reliable certificate validation, simplify certificate rotations (no more hardcoded or pinned issuer), and prepare your cluster for the upcoming public CA restriction on dual EKU certificates.

> [!NOTE]
> This guide applies only to clusters that were deployed with infrastructure scripts earlier than version 3.0.0. Clusters deployed with version 3.0.0 or later already have the issuer store model and the dedicated cluster certificate configured.

## Overview

Service Fabric supports multiple models for restricting which certificate issuers are trusted:

- **Legacy model (CertificateInformation issuer stores)**: The trusted issuer is specified in the `CertificateInformation` section of the cluster configuration using the `ClusterCertificateIssuerStores`, `ServerCertificateIssuerStores`, and `ClientCertificateIssuerStores` properties. Each entry references the issuer's common name (the CA that issued the certificate) and the X509 store where the issuer certificate is located (typically `Root`).

- **Issuer store model (FabricSettings issuer stores)**: The trusted issuers are specified as FabricSettings entries under `Security/ClusterCertificateIssuerStores`, `Security/ServerCertificateIssuerStores`, and `Security/ClientCertificateIssuerStores`. Each entry maps a certificate's subject common name to a custom certificate store (for example, `ServiceFabric_IssuerTrust`) that contains the issuer CA certificates. This model allows Service Fabric to validate certificates by checking if the issuing CA certificate is present in the designated store.

The issuer store model is the recommended approach because:

- It decouples certificate validation from the direct issuer's common name, which can change when CAs are renewed.
- It makes certificate rotations easier, because you only need to ensure the new issuer CA certificate is in the issuer store.
- It provides a clear, auditable location for trusted issuer certificates on each node.

### Dedicated cluster certificate

As part of this migration, the cluster also moves to using a dedicated **ServiceFabricCluster** certificate for node-to-node communication, separate from the **ServiceFabric** certificate that is used for server authentication. Previously, both purposes shared the same certificate.

This separation is required because the cluster certificate needs both Server Authentication and Client Authentication enhanced key usages (EKUs). Starting in the summer of 2026, public certificate authorities will stop issuing certificates with this dual EKU combination, as outlined in the [CA/Browser Forum guidelines](https://github.com/microsoft/service-fabric/blob/master/release_notes/Resources/ClientEKURemoval.md). The dedicated **ServiceFabricCluster** certificate must be issued by your own PKI (such as AD&nbsp;CS) or be self-signed.

## Prerequisites

Before you begin the migration, ensure the following:

- Your infrastructure scripts are updated to version 3.0 or later.
- Your `ConfigTemplate.xml` has been upgraded to schema version 1.13 or later (run `Update-ConfigTemplate.ps1` if needed).
- The `IssuerStore` section in your `ConfigTemplate.xml` is configured with the name of the issuer trust store and the issuer CA certificate information.

```xml
<IssuerStore>
    <Name>ServiceFabric_IssuerTrust</Name>
    <IssuerCAs export="true">
        <FolderPath></FolderPath>
        <Thumbprints>a1b2c3d4e5f6a1b2c3d4e5f6a1b2c3d4e5f6a1b2</Thumbprints>
    </IssuerCAs>
</IssuerStore>
```

The **IssuerCAs** section specifies where to find the issuer CA certificates. This is the certificate of the CA that directly issued your Service Fabric certificates. In a multi-level trust chain, this is the intermediate CA. If there's only one level (no intermediates), this is the root CA certificate. You can specify thumbprints, a folder path containing .cer files, or a combination of both.

> [!IMPORTANT]
> The new version of the infrastructure scripts has added the possibility of splitting the certificate used for Finance + Operations and Service Fabric into separate certificates. It is not necessary to split the certificates for this migration. It is not recommended that you use this migration as the vehicle for splitting the certificates.

## Migration for existing Service Fabric Clusters

1. Infrastructure scripts version 3.0.0 introduces two new ADCS certificate templates (**D365FinOpsLBDServerTemplate** and **D365FinOpsLBDClientTemplate**) in addition to the existing templates. Run the following command on your AD&nbsp;CS server to create the new templates. The script skips any templates that already exist.

```powershell
.\New-ADCSCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -CreateTemplates
```

1. Generate the new **ServiceFabricCluster** certificate and any other certificates that need to be regenerated.

```powershell
.\New-ADCSCertificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```

1. Run the export scripts to ensure all certificates (including the issuer CA certificates) are exported and distributed to the correct VM folders.

```powershell
.\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
.\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```

1. Run the following script to ensure that all prerequisites are completed (including the certificates). Perform this step as an administrator.

```powershell
# If remoting, only execute
# .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml 

.\Complete-PreReqs.ps1
```

The import script automatically creates the issuer trust store (for example, `ServiceFabric_IssuerTrust`) if it doesn't exist and imports each certificate into its designated store.

1. Validate that the configuration related to your certificates is correctly applied. The script will validate that the necessary intermediate issuing certs are present for the certificates that require it.

```powershell
# If remoting, only execute
# .\Test-D365FOConfiguration-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml 

.\Test-D365FOConfiguration.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```


1. Before you can upgrade to the issuer store model, you must remove the legacy issuer store entries from the cluster configuration. Run the following command from one of your Service Fabric nodes:

> [!NOTE]
> If you originally created your cluster with the `-DoNotRestrictCertificateIssuers` flag, your cluster configuration doesn't have legacy issuer store entries. You can skip this step and proceed directly to the next one.

```powershell
.\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -RemoveOldIssuers
```

This generates a new cluster configuration file with the old issuer entries removed. Apply the configuration upgrade to your cluster by following the [Service Fabric cluster configuration upgrade](onprem-update-sfcluster.md) process.

> [!IMPORTANT]
> Wait for the cluster configuration upgrade to complete successfully before proceeding to the next step. You can monitor the upgrade status in Service Fabric Explorer.

1. After the old issuers have been removed and the configuration upgrade is complete, run the following command to upgrade to the issuer store model:

```powershell
.\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpgradeToIssuerStore
```

This command updates the certificate common names in the cluster configuration to match the current `ConfigTemplate.xml` (including the separate **ServiceFabricCluster** certificate), adds the `Security/*IssuerStores` FabricSettings entries that map each certificate's subject name to the issuer trust store, and sets the Security parameters to enable issuer store validation. Apply the generated cluster configuration to your cluster by following the [Service Fabric cluster configuration upgrade](onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration) process.

> [!NOTE]
> The Service Fabric cluster will initiate more than one upgrade process as it needs to go through multiple intermidiate steps to reach the desired state. So you may see the cluster finish an upgrade and proceed to start another upgrade almost immediately.

1. After the configuration upgrade completes, verify the migration was successful. Open Service Fabric Explorer and confirm the cluster is healthy.

## Troubleshooting

### The upgrade script throws an error about old issuer stores

If you see the error "The cluster configuration still has old issuer stores defined in CertificateInformation," you must run `Update-SFClusterConfig.ps1 -RemoveOldIssuers` first and complete the cluster configuration upgrade before you can run `-UpgradeToIssuerStore`.

### The RemoveOldIssuers script warns that there are no issuers to remove

This warning means the legacy issuer store entries have already been removed from the cluster configuration. You can proceed directly to the `-UpgradeToIssuerStore` step.

### Certificate validation fails after the upgrade

If certificate validation fails after the upgrade, verify the following:

- The issuer CA certificate is present in the issuer trust store on every node. You can check by running `Get-ChildItem Cert:\LocalMachine\ServiceFabric_IssuerTrust` on each node.
- The issuer CA certificate in the store is the direct issuer of your Service Fabric certificates. In a multi-level chain, this should be the intermediate CA, not the root CA.
- The certificate subject names in the cluster configuration match the subjects in your `ConfigTemplate.xml`.
