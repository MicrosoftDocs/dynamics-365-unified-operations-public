---
title: Independent software vendor (ISV) licensing
description: Learn about the independent software vendor (ISV) licensing feature, including on outline of the feature's capabilities.
author: pnghub
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 90ae4ae6-f19a-4ea5-8bd9-1d45729b0636
ms.custom: sfi-image-nochange
---

# Independent software vendor (ISV) licensing

[!include [banner](../includes/banner.md)]

This article describes the independent software vendor (ISV) licensing feature. It includes information about benefits and capabilities of the ISV licensing feature, and explains how to enable licensing for an ISV solution, create a package and generate a customer-specific license, and create self-signed certificates for test purposes.

The Microsoft Dynamics ecosystem provides tools and frameworks that let independent software vendors (ISVs) build, deploy, sell, and monetize vertical industry solutions that can be repackaged. The ISV licensing feature provides the following benefits:

- It provides a safer licensing mechanism for ISV solutions for customers and partners. ISV solutions are enabled only if the customer purchases a valid license key from the ISV.
- It aligns how customers handle licenses for ISV solutions from different ISVs, and therefore lowers the total cost of ownership (TCO).
- ISVs can independently generate, manage, and distribute ISV licenses by using industry standard frameworks.

This feature doesn't provide ISV competitor copycat protection (that is, source-based protection).

> [!IMPORTANT]
> Starting with Dynamics 365 Finance version 10.0.43, all licenses are issued at the tenant level. This means a single license can potentially be used across multiple environments that share the same tenant ID. Licenses generated in Dynamics 365 Finance version 10.0.43 and later aren't compatible with older versions of the application.

## Capabilities

This section describes various capabilities of the ISV licensing feature.

### ISVs can generate their own licenses

ISVs can independently generate their own licenses, apply them to solutions, and deliver those solutions to partners and customers. Each ISV license enables run-time features that help protect the ISV solution. Additionally, each ISV license ties to an ISV Authenticode certificate, which ensures that the software was distributed by the ISV.

### A run-time check makes sure that an ISV-generated license key exists in the customer's environment

Each ISV solution that is tied to a license runs only when a valid license key exists in the customer's environment. Therefore, if an ISV ties its solution to a license, but the customer doesn't have a valid license key, the solution doesn't run.

### License types: Boolean and Number

ISVs can create two types of licenses: **Boolean** and **Number**. ISVs can associate an expiration date with either type of license. This expiration date applies only to the ISV licenses and is independent of the system expiration date. A Boolean license is a simple activation license. Set the type of license (**Boolean** or **Number**) through a property in the license code node. ISVs can write their own custom logic to check the count that the ISV license provides, to make sure that their solutions are used within the license terms. For more information, see [Licensing Framework for ISVs](/dynamicsax-2012/developer/licensing-framework-for-isvs-of-microsoft-dynamics-ax).

### License validation errors

When an ISV license becomes invalid after import, the ISV solution continues to run until the server restarts. (After the server restarts, the solution is disabled.) An error is thrown when the instance of the Application Object Server (AOS) starts. The error is written to the event log.

## Implementing ISV licensing in a solution

ISVs must have a valid Authenticode certificate (X.509) from a certificate authority (CA). Microsoft doesn't recommend any particular CA. However, many companies offer these certificates. Authenticode certificates come in various key sizes. The ISV licensing feature supports certificates of both 1024-bit and 2048-bit key sizes. 3072-bit and 4096-bit code signing certificates are supported beginning with platform updates for version 10.0.20. Use the larger bit key size because it provides stronger encryption. However, if you already have a valid 1024-bit or 2048-bit key size, that key size works with the ISV licensing feature.

For HSM-based certificates, only those with an RSA private key are supported, as the license generator exclusively works with RSA.

> [!NOTE]
> Authenticode certificates have various cryptographic service providers. The ISV licensing feature uses Enhanced cryptographic provider, which also covers Base cryptographic provider. Many independent providers offer Authenticode certificates.

## Certificate import and export

Use the certificate to sign your customer license files and validate the license files at the time of import. Authenticode certificates support four file formats. For the ISV licensing feature, you must have the certificate files in two formats:

- **Personal Information Exchange (PFX, also known as PKCS #12)** – The PKCS #12 format, which uses the .pfx file name extension, supports secure storage of certificates, private keys, and all certificates in a certification path. The PKCS #12 format is the only file format that can be used to export a certificate and its private key.
- **Base64-encoded X.509** – The Base64 format supports storage of a single certificate. This format doesn't support storage of the private key or certification path.

There's a restriction on the format. Use the PFX (PKCS #12) format only to export the certificate together with its private key for signing and generating purposes. Never share it outside the ISV organization. Use the DER-encoded binary X.509 format, which uses the .cer file name extension, to export the public key of the certificate that must be embedded in the Application Object Tree (AOT) License. Distribute this public key to customers via the model. It's used when a license is imported, to make sure that the license is signed by the ISV license that owns the private key.

> [!NOTE]
> Instead of using .pfx files, ISVs can now also opt for HSM (Hardware Security Module)–based keys for private key storage, with the tool able to load the certificate directly from the store. However, the public key is still required in the Base64-encoded X.509 format.

## Enable licensing for your ISV solution

Follow these steps to enable licensing for your solution.

1. Create an ISV solution. In Visual Studio, select **File > New project**. In the **New Project** dialog, select **Installed > Templates > Dynamics 365**. Create a **Finance Operations** project. In this example, name the project **NewISVSolution**.

    :::image type="content" source="media/isv_new_isv_project.png" alt-text="Screenshot of creating an ISV solution.":::

1. Add the certificate's public key (.cer file) to your project as a resource. To create a certificate for testing, see [Appendix: Create self-signed certificates for test purposes](#appendix-create-self-signed-certificates-for-test-purposes).

    1. Right-click the project in Solution Explorer, and then select **Add > New item**.
    1. Under **Installed > Dynamics 365 Items**, select **Labels And Resources**, and then select **Resource**. Name the resource. In this example, name the resource **ISVCert**.

        :::image type="content" source="media/isv_new_resource.png" alt-text="Screenshot of clicking Resource.":::

    1. Select **Add** and select the certificate's public key file (.cer file).

        :::image type="content" source="media/isv_select_cer.png" alt-text="Screenshot of selecting the certificate's public key as the resource.":::

    1. Select **Open** to add the certificate.

        :::image type="content" source="media/isv_resource_cer.png" alt-text="Screenshot of adding the certificate as a resource.":::

1. Create a license code. Right-click the project in Solution Explorer, and then select **Add > New item**. Under **Installed > Dynamics 365 Items**, choose **Configuration**. In the list, choose **License Code** and name the license code. In this example, name the license code **ISVLicenseCode**. Select **Add**.

    :::image type="content" source="media/isv_new_license_code.png" alt-text="Screenshot of creating a license code.":::

1. Map the certificate to the license code. In the Properties window for the license code, set the **Certificate** property to your certificate resource. In this example, set **Certificate** to **ISVCert**.

    :::image type="content" source="media/isv_map_license_cert.png" alt-text="Screenshot of mapping the certificate to the license code.":::

1. Create one or more configuration keys. Right-click the project in Solution Explorer, and then select **Add > New item**. Under **Installed > Dynamics 365 Items**, choose **Configuration**. In the list, choose **Configuration Key**. Name the key and select **Add**. In this example, name the configuration key **ISVConfigurationKey1**.

    :::image type="content" source="media/isv_new_configuration_key.png" alt-text="Screenshot of creating a configuration key.":::

1. Associate the license code with the configuration key. In Solution Explorer, double-click the configuration key to open the Properties window. In the Properties window, set the **LicenseCode** property to your license code. In this example, set the **LicenseCode** to **ISVLicenseCode**.

    :::image type="content" source="media/isv_select_license_code.png" alt-text="Screenshot of associating the license code with the configuration keys.":::

1. Associate a configuration key to an element in your solution. For example, create a new form. Right-click the project in Solution Explorer, and then select **Add > New item**. Under **Installed > Dynamics 365 Items**, choose **User Interface**. In the list, choose **Form** and give it a name. In this example, name the form **ISVForm**.

    :::image type="content" source="media/isv_new_form.png" alt-text="Screenshot of creating a new form.":::

1. Add a button to the form. Double-click the form in the Solution Explorer. In the Design window, right-click and select **New**, and then **Button**. Set the **Text** property to **ISVButton**.

    :::image type="content" source="media/isv_button_designtime.png" alt-text="Screenshot of adding a button to the new form.":::

    At runtime, the button is visible because it isn't controlled by a configuration key at first.

    :::image type="content" source="media/isv_button_visible_runtime.png" alt-text="Screenshot of new button visible when it's first added.":::

1. Associate a configuration key with the button. In the Properties window for the button, set the **Configuration Key** property to your configuration. In this example, set the **Configuration Key** to **ISVConfigurationKey1**.

    :::image type="content" source="media/isv_select_key_for_button.png" alt-text="Screenshot of associating a configuration key with the button.":::

    At runtime, the button isn't visible because the configuration key must be available and enabled.

    :::image type="content" source="media/isv_button_invisible_runtime.png" alt-text="Screenshot of button no longer visible.":::

## Create a package and generate a customer-specific license

1. Collect the tenant name and ID for the customer to issue the license to. You can find this information at **Settings \> Help \& Support \> About** on the **Licenses** tab.

    :::image type="content" source="./media/isv_tenant_id.png" alt-text="Screenshot of customer's tenant name and ID.":::

1. Generate a license for the customer (tenant ID and name), and sign the license by using the certificate's private key. Pass the following parameters to the **axutil genlicense** command to create the license file.

    **For environments on version >= 10.0.43**

    | Parameter name  | Description                                                                  |
    |-----------------|------------------------------------------------------------------------------|
    | file            | The name of your license file.                                               |
    | licensecode     | The name of your license code (from Microsoft Visual Studio).                |
    | serialnumber    | The customer's tenant ID (labeled "Serial number" in the screenshot).        |
    | subjectname| Specifies the subject name of the certificate that you install in the certificate store (Current User/My). To load the certificate, use either the subjectname or certificatepath/password, but not both. This parameter is available in Dynamics 365 Finance version 10.0.37 and higher. |
    | thumbprint| Optional: It's a unique identifier for selecting a particular certificate with the given subject name. While this parameter is optional, it can only be used along with subjectname. If thumbprint isn't specified and the store contains multiple certificates with same subject name, the tool picks up the certificate with the furthest(maximum) expiry. This parameter is available in Dynamics 365 Finance version 10.0.37 and higher. |
    | certificatepath | The path of your certificate's private key. Use this value if you don't have the HSM based certificate. |
    | password        | The password for your certificate's private key.                             |
    | expirationdate  | Optional: The expiration date for the license.                               |
    | usercount       | Optional: The number that custom validation logic can use as required. This number could be users, but isn't limited to users. |

    Example for HSM based key.
     > [!NOTE]
     > To use the subject name and thumbprint parameters, first install the certificate to the Windows certificate store. Go to **Current user** > **Personal (My)** and run the following command:

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /licensecode:ISVLicenseCode /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /subjectName:"ISVCert" /thumbprint:******** /expirationdate:11/30/2023 
     ```

    Example for file based key.

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /licensecode:ISVLicenseCode /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /certificatepath:c:\tempisvcert.pfx /password:********
    ```

    **For environments on version < 10.0.43**

    | Parameter name  | Description                                                                  |
    |-----------------|------------------------------------------------------------------------------|
    | file            | The name of your license file.                                               |
    | licensecode     | The name of your license code (from Microsoft Visual Studio).                |
    | certificatepath | The path of your certificate's private key.                                  |
    | password        | The password for your certificate's private key.                             |
    | customer        | The customer's tenant name (from the screenshot under step 1).              |
    | serialnumber    | The customer's tenant ID (labeled "Serial number" in the screenshot).       |
    | expirationdate  | Optional: The expiration date for the license.                               |
    | usercount       | Optional: The number that custom validation logic can use as required. This number could be users, but isn't limited to users. |
    | SignatureVersion| Optional: Defines the hashing algorithm to be used for license generation. Value 1 defines SHA1. Value 2 defines SHA256 and the default value is 2. IMPORTANT: SHA1 will be deprecated in a future release. It's recommended to use 2 for this parameter. After SHA1 is deprecated, ISV Licensing will work with SHA256 (value 2). |
    | UseLegacyCryptoServiceProvider| Optional: Use an older CryptoServiceProvider. If generating the license key fails, this option allows users to use on an older version of ISV License generation. The default value is 0 and should only be used to provide a fallback mechanism if there's an error with the default value. This parameter is available in Dynamics 365 Finance version 10.0.36. |
    | AllowCrossDomainInstallation| Optional: This parameter provides ISVs (Independent Software Vendors) with the ability to generate licenses that can be used across different environments for the same tenant (customer). The default value is set to **false**, which means the tenant can't use the same ISV license across different environments or reuse the same ISV license within the same environment when the admin domain name changes. When the value is set to **true**, the customer can install the same ISV license across different environments associated with the same tenant or when the customer changes the admin domain name of the environment. This parameter is available in Dynamics 365 Finance version 10.0.38 and higher. |
    | subjectname| Specifies the subject name of the certificate that is installed in the cert store (Current User/My). To load the certificate, you can use either the subjectname or certificatepath/password, but not both. This parameter is available in Dynamics 365 Finance version 10.0.37 and higher. |
    | thumbprint| Optional: It's a unique identifier for selecting a particular certificate with the given subject name. While this parameter is optional, it can only be used along with subjectname. If thumbprint isn't specified and the store contains multiple certificates with same subject name, the tool picks up the certificate with the furthest(maximum) expiry. This parameter is available in Dynamics 365 Finance version 10.0.37 and higher. |

    Example for HSM based key.
    > [!NOTE]
    > To use the subjectname and thumbprint parameter: first install the certificate to Current User | My store, and then run the following command:

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /licensecode:ISVLicenseCode  /customer:TAEOfficial.ccsctp.net /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /subjectName:"ISVCert" /thumbprint:******** /expirationdate:11/30/2023 
     ```

    Example for file based key.

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /certificatepath:c:\tempisvcert.pfx /licensecode:ISVLicenseCode /customer:TAEOfficial.ccsctp.net /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /password:********
    ```

1. Import the license into the target environment.

    > [!NOTE]
    > In production systems, complete this step from Microsoft Dynamics Lifecycle Services (LCS), by using a deployable package. For more information, see the "Production environments" section later in this article.

    | Parameter name                | Description                                                                                            |
    |-------------------------------|--------------------------------------------------------------------------------------------------------|
    | --setupmode importlicensefile | Use this parameter to inform the setup tool that a license is loaded.                             |
    | --metadatadir                 | Use this parameter to specify the metadata directory. Use the default packages directory.   |
    | --bindir                      | Use this parameter to specify the binaries directory. Use the default packages directory.   |
    | --sqlserver                   | Use this parameter to specify the Microsoft SQL Server. For one-box environment, use a period (**.**). |
    | --sqldatabase                 | Use this parameter to specify the SQL Server database. For one-box environments, use **AXDB**.     |
    | --sqluser                     | Use this parameter to specify the SQL Server user. Use **axdbadminr**.                  |
    | --sqlpwd                      | Use this parameter to specify the SQL Server password.                                                 |
    | --licensefilename             | Use this parameter to specify the license file that is loaded.                                    |

    For example.

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\Microsoft.Dynamics.AX.Deployment.Setup.exe --setupmode importlicensefile --metadatadir c:\packages --bindir c:\packages --sqlserver . --sqldatabase axdb --sqluser axdbadmin --sqlpwd ******** --licensefilename c:\templicense.txt
    ```

1. The corresponding configuration key is available and enabled on the **License configuration** page. By default, the configuration is enabled. For example, see the **ISVConfigurationKey1** configuration key in the following screenshot.

    :::image type="content" source="media/isv_license_configuration_page.png" alt-text="Screenshot of ISVConfigurationKey1 configuration key enabled on the License configuration page.":::

1. In nonproduction installations, you must start the database synchronization process from Visual Studio.

After you enable the configuration key, the button becomes visible, as shown in the following screenshot.

:::image type="content" source="media/isv_button_visible_runtime.png" alt-text="Screenshot of button visible after the configuration key is enabled.":::

## Protection best practices

You can deliver solutions in two forms:

- Model files (source code)
- Deployable packages (binary)

To protect your configuration keys and license codes, release them in binary form by using a deployable package. Customers can install and interact with those elements in Visual Studio. Although customers can refer to items in the deployable package, they can't access source code or make modifications to the items. (However, they can create extensions.) More details about the capability to release solutions in binary form are available soon. The deployable package (binary) can also include classes and other logic that your customer doesn't require access to and shouldn't be able to customize.

:::image type="content" source="./media/isv_protected_solution.png" alt-text="Screenshot of protected vs. unprotected ISV solutions.":::

## Production environments

To install ISV licenses in production systems, you must use a deployable package through LCS. You can find a template package for configuration mode at the following location in all installations: \<PackagesFolder\>\\bin\\CustomDeployablePackage\\ImportISVLicense.zip. The Packages folder is typically under j:\\AOSService\\PackagesLocalDirectory or c:\\AOSService\\PackagesLocalDirectory\\.

> [!div class="mx-imgBorder"]
> :::image type="content" source="media/isv_template_location.png" alt-text="Screenshot of location of the template package for configuration mode.":::

1. Make a copy of the package template.
1. Put the license file in the following folder within the package template: ImportISVLicense.zip\\AosService\\Scripts\\License

You can install more than one license at a time. If one of the licenses depends on another license, make sure that it's named accordingly. (Licenses are installed in alphabetical order.)

## Appendix: Create self-signed certificates for test purposes

> [!NOTE]
> Use self-signed certificates only during development. Production environments don't support self-signed certificates.

For Platform update 34 and earlier versions:
(Deprecated - uses SHA1 hash algorithm for license creation)

1. For test purposes, create a self-signed CA certificate. Use the Visual Studio tools prompt to run the following command.

    ```Console
    makecert -r -pe -n "CN=IsvCertTestAuthority O=IsvCertTestAuthority" -ss CA -sr LocalMachine -a sha256 -len 2048 -cy authority -sky signature -b 01/01/2016 -sv c:\temp\CA.pvk c:\temp\CA.cer
    ```

    For more information, see the [MakeCert](/windows/win32/seccrypto/makecert) documentation.

1. Create a certificate by using the CA.

    ```Console
    makecert -pe -n "CN=IsvCertTest O=IsvCertTest" -ss ISVStore -sr LocalMachine -a sha256 -len 2048 -cy end -sky signature -eku 1.3.6.1.5.5.7.3.3 -ic c:\temp\ca.cer -iv c:\temp\ca.pvk -b **/**/**** -sv c:\temp\isvcert.pvk c:\temp\isvcert.cer
    ```

1. Convert the ISV certificate to PFX format.

    ```Console
    pvk2pfx -pvk c:\temp\isvcert.pvk -spc c:\temp\isvcert.cer -pfx c:\temp\isvcert.pfx -po ********
    ```

1. For a test scenario, import the self-signed CA certificate manually on all the AOS instances.

    ```Console
    certutil -addstore root c:\temp\ca.cer
    ```

    However, if a self-signed ISV certificate was used, import that certificate instead of the CA certificate.

    ```Console
    certutil -addstore root c:\temp\isvcert.cer
    ```

For Platform update 35 and later versions:
(Uses SHA256 hash algorithm for license creation)

1. For test purposes, create a self-signed certificate by using the PowerShell command `New-SelfSignedCertificate`:
    1. Create the certificate. (Note: adjust start and end dates accordingly.)

        ```PowerShell
        $cert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "IsvCert" -Type CodeSigningCert -KeyExportPolicy Exportable -HashAlgorithm sha256 -KeyLength 2048 -KeySpec Signature -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" -NotBefore (Get-Date -Year 2020 -Month 1 -Day 1) -NotAfter (Get-Date -Year 2022 -Month 12 -Day 31)
        ```

    1. Get a reference to the new certificate.

        ```PowerShell
        [String]$certPath = Join-Path -Path "cert:\LocalMachine\My\" -ChildPath "$($cert.Thumbprint)"
        ```

    1. Create the secure string password that the certificate uses. (Replace "##############" with the certificate password)

        ```PowerShell
        [System.Security.SecureString]$certPassword = ConvertTo-SecureString -String "##############" -Force -AsPlainText
        ```

    1. Export the certificate private key as **.pfx** file using the password.

        ```PowerShell
        Export-PfxCertificate -Cert $certPath -FilePath "C:\Temp\IsvCert.pfx" -Password $certPassword
        ```

    1. Export the certificate public key as a **.cer** file.

        ```PowerShell
        Export-Certificate -Cert $certPath -FilePath "C:\Temp\IsvCert.cer"
        ```

1. Add the certificate to the root store.

    ```PowerShell
    certutil -addstore root C:\Temp\IsvCert.cer
    ```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
