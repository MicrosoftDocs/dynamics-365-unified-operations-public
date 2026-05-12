---
title: Migrate to issuer store certificate validation for Service Fabric
description: Learn how to migrate your on-premises Service Fabric cluster from the legacy issuer validation model to the issuer store model for certificate validation.
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

# Migrate to issuer store certificate validation for Service Fabric

This article explains how to migrate an existing Finance + Operations (on-premises) Service Fabric cluster from the legacy certificate issuer validation model to the issuer store model. The issuer store model provides more reliable certificate validation and simplifies certificate management, especially during certificate rotations.

## Overview

Service Fabric supports two models for restricting which certificate issuers are trusted:

- **Legacy model (CertificateInformation issuer stores)**: The trusted issuer is specified in the `CertificateInformation` section of the cluster configuration using the `ClusterCertificateIssuerStores`, `ServerCertificateIssuerStores`, and `ClientCertificateIssuerStores` properties. Each entry references the issuer's common name (the CA that issued the certificate) and the X509 store where the issuer certificate is located (typically `Root`).

- **Issuer store model (FabricSettings issuer stores)**: The trusted issuers are specified as FabricSettings entries under `Security/ClusterCertificateIssuerStores`, `Security/ServerCertificateIssuerStores`, and `Security/ClientCertificateIssuerStores`. Each entry maps a certificate's subject common name to a custom certificate store (for example, `ServiceFabric_IssuerTrust`) that contains the issuer CA certificates. This model allows Service Fabric to validate certificates by checking if the issuing CA certificate is present in the designated store.

The issuer store model is the recommended approach because:

- It decouples certificate validation from the issuer's common name, which can change when CAs are renewed.
- It makes certificate rotations easier, because you only need to ensure the new issuer CA certificate is in the issuer store.
- It provides a clear, auditable location for trusted issuer certificates on each node.

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

## Step 1: Export and distribute certificates

Run the export scripts to ensure all certificates (including the issuer CA certificates) are exported and distributed to the correct VM folders.

```powershell
.\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
.\Export-ImportCertificatesScript.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```

The export scripts automatically:

- Export issuer CA certificates from the specified folder path or thumbprints.
- Include them in the per-VM certificate packages targeted at the issuer trust store.
- Generate a CSV file per VM that includes store-specific entries for each certificate.

## Step 2: Import certificates on each node

On each Service Fabric node, run the import script from the VM-specific folder:

```powershell
.\Import-Certificates.ps1
```

The import script automatically:

- Creates the issuer trust store (for example, `ServiceFabric_IssuerTrust`) if it doesn't exist.
- Imports each certificate into its designated store (PFX into `LocalMachine\My`, CER into `LocalMachine\Root` or the issuer trust store).
- Handles issuer CA certificates that don't have a thumbprint in the CSV.

## Step 3: Remove old issuer stores from the cluster configuration

Before you can upgrade to the issuer store model, you must remove the legacy issuer store entries from the cluster configuration. These are the `ClusterCertificateIssuerStores`, `ServerCertificateIssuerStores`, and `ClientCertificateIssuerStores` properties in the `CertificateInformation` section.

Run the following command from one of the Orchestrator nodes:

```powershell
.\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -RemoveOldIssuers
```

This generates a new cluster configuration file with the old issuer entries removed. Apply the configuration upgrade to your cluster by following the standard [Service Fabric cluster configuration upgrade](/azure/service-fabric/service-fabric-cluster-config-upgrade-windows-server) process.

> [!IMPORTANT]
> Wait for the cluster configuration upgrade to complete successfully before proceeding to the next step. You can monitor the upgrade status in Service Fabric Explorer.

## Step 4: Upgrade to the issuer store model

After the old issuers have been removed and the configuration upgrade is complete, run the following command to upgrade to the issuer store model:

```powershell
.\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpgradeToIssuerStore
```

This command:

- Updates the certificate common names in the cluster configuration to match the current `ConfigTemplate.xml` (including the separate **ServiceFabricCluster** certificate if applicable).
- Adds `Security/ServerCertificateIssuerStores`, `Security/ClusterCertificateIssuerStores`, and `Security/ClientCertificateIssuerStores` FabricSettings entries that map each certificate's subject name to the issuer trust store.
- Sets the `EnforcePrevalidationOnSecurityChanges` Security parameter to `false` and `EnableExtendedCertificateValidation` to `true`, which enables the issuer store validation model.

Apply the generated cluster configuration to your cluster by following the standard configuration upgrade process.

## Step 5: Verify the upgrade

After the configuration upgrade completes, verify the migration was successful:

1. Open Service Fabric Explorer and confirm the cluster is healthy.
2. Verify that the `Security/ClusterCertificateIssuerStores`, `Security/ServerCertificateIssuerStores`, and `Security/ClientCertificateIssuerStores` entries are present in the FabricSettings of the cluster configuration.
3. On each node, verify that the issuer trust store (for example, `Cert:\LocalMachine\ServiceFabric_IssuerTrust`) contains the expected issuer CA certificate.

You can also run the certificate compatibility validation script to verify that all certificates are valid and their issuers are present in the issuer store:

```powershell
.\Test-CertificateCompatibility.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```

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
