---
title: Independent software vendor (ISV) licensing
description: This article describes the independent software vendor (ISV) licensing feature.
author: peakerbl
ms.date: 05/08/2020
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: peakerbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 90ae4ae6-f19a-4ea5-8bd9-1d45729b0636
---

# Independent software vendor (ISV) licensing

[!include [banner](../includes/banner.md)]

This article describes the independent software vendor (ISV) licensing feature. It includes information about benefits and capabilities of the ISV licensing feature, and explains how to enable licensing for an ISV solution, create a package and generate a customer-specific license, and create self-signed certificates for test purposes.

The Microsoft Dynamics ecosystem provides tools and frameworks that let independent software vendors (ISVs) build, deploy, sell, and therefore monetize vertical industry solutions that can be repackaged. The ISV licensing feature provides the following benefits:

-   It provides a safer licensing mechanism for ISV solutions for customers and partners. ISV solutions are enabled only if the customer has purchased a valid license key from the ISV.
-   It aligns how customers handle licenses for ISV solutions from different ISVs, and therefore lowers the total cost of ownership (TCO).
-   ISVs can independently generate, manage, and distribute ISV licenses by using industry standard frameworks.

This feature doesn't enable ISV competitor copycat protection (that is, source-based protection).

## Capabilities
This section describes various capabilities of the ISV licensing feature.

### ISVs can generate their own licenses

ISVs can independently generate their own licenses, apply them to solutions, and deliver those solutions to partners and customers. Each ISV license enables run-time features that help protect the ISV solution. Additionally, each ISV license is tied to an ISV Authenticode certificate, which ensures that the software was distributed by the ISV.

### A run-time check makes sure that an ISV-generated license key exists in the customer's environment

Each ISV solution that is tied to a license runs only when a valid license key exists in the customer's environment. Therefore, if an ISV ties its solution to a license, but the customer doesn't have a valid license key, the solution doesn't run.

### There are two types of license: Boolean and Number

ISVs can create two types of license: **Boolean** and **Number**. ISVs can associate an expiration date with either type of license. This expiration date is applied only to the ISV licenses and is independent of the system expiration date. A Boolean license is a simple activation license. The type of license (**Boolean** or **Number**) is set through a property in the license code node. ISVs can write their own custom logic to check the count that is provided in the ISV license, to make sure that their solutions are being used within the license terms. For more information, see [Licensing Framework for ISVs](/dynamicsax-2012/developer/licensing-framework-for-isvs-of-microsoft-dynamics-ax).

### License validation errors

When an ISV license becomes invalid after import, the ISV solution continues to run until the server is restarted. (After the server is restarted, the solution is disabled.) An error is thrown when the instance of the Application Object Server (AOS) starts. The error is written to the event log.

## Implementing ISV licensing in a solution
ISVs must have a valid Authenticode certificate (X.509) from a certificate authority (CA). Microsoft doesn't recommend any particular CA. However, many companies offer these certificates. Authenticode certificates come in various key sizes. The ISV licensing feature supports certificates of both 1024-bit and 2048-bit key sizes. 3072-bit and 4096-bit code signing certificates are supported beginning with platform updates for version 10.0.20. We recommend that ISVs use the larger bit key size because it provides stronger encryption. However, if an ISV already has a valid 1024-bit or 2048-bit key size, that key size works with the ISV licensing feature. 

> [!NOTE]
> Authenticode certificates can have various cryptographic service providers. The ISV licensing feature uses Enhanced Cryptographic Provider (which also covers Base Cryptographic Provider). There are many independent providers that you can purchase an Authenticode certificate from. Microsoft doesn't recommend any particular provider. Some providers that are often used are Symantec VeriSign, and Thawte.

## Certificate import and export
The certificate is used to sign your customer license files and validate the license files at the time of import. Authenticode certificates support four file formats. For the ISV licensing feature, you must have the certificate files in two formats:

-   **Personal Information Exchange (PFX, also known as PKCS \#12)** – The PKCS \#12 format, which uses the .pfx file name extension, supports secure storage of certificates, private keys, and all certificates in a certification path. The PKCS \#12 format is the only file format that can be used to export a certificate and its private key.
-   **Base64-encoded X.509** – The Base64 format supports storage of a single certificate. This format doesn't support storage of the private key or certification path.

There is a restriction on the format. The PFX (PKCS \#12) format should be used only to export the certificate together with its private key for signing/generating purposes. It should never be shared outside the ISV organization. The DER-encoded binary X.509 format, which uses the .cer file name extension, should be used to export the public key of the certificate that must be embedded in the Application Object Tree (AOT) License. This public key is distributed to customers via the model. It's used when a license is imported, to make sure that the license is signed by the ISV license that owns the private key.

## Enable licensing for your ISV solution
Follow these steps to enable licensing for your solution.

1. Create an ISV solution. In Visual Studio, click **File \> New project**. In the **New Project** dialog, click **Installed > Templates > Dynamics 365**.  Create a **Finance Operations** project. In this example, we named the project **NewISVSolution**.

    ![Creating an ISV solution.](media/isv_new_isv_project.png)

2. Add the certificate's public key (.cer file) to your project as a resource. To create a certificate for testing, see [Appendix: Create self-signed certificates for test purposes](#appendix-create-self-signed-certificates-for-test-purposes).

    1. Right-click the project in Solution Explorer, then click **Add \> New item**. 
    2. Under **Installed \> Dynamics 365 Items**, click **Labels And Resources**, and then select **Resource**. Name the resource. In this example, we named the resource **ISVCert**.

        ![Clicking Resource.](media/isv_new_resource.png)

    3. Click **Add** and select the certificate's public key file (.cer file).

        ![Selecting the certificate's public key as the resource.](media/isv_select_cer.png)

    4. Click **Open** to add the certificate.

        ![Adding the certificate as a resource.](media/isv_resource_cer.png)

3. Create a license code. Right-click the project in Solution Explorer, then click **Add \> New item**. Under **Installed \> Dynamics 365 Items**, choose **Configuration**. In the list, choose **License Code** and name the license code. In this example, we named the license code **ISVLicenseCode**. Click **Add**.

    ![Creating a license code.](media/isv_new_license_code.png)

4. Map the certificate to the license code. In the Properties window for the license code, set the **Certificate** property to your certificate resource. In this example, we set **Certificate** to **ISVCert**.

    ![Mapping the certificate to the license code.](media/isv_map_license_cert.png)

5. Create one or more configuration keys. Right-click the project in Solution Explorer, then click **Add \> New item**. Under **Installed \> Dynamics 365 Items**, choose **Configuration**. In the list, choose **Configuration Key**. Name the key and click **Add**. In this example, we named the configuration key **ISVConfigurationKey1**.

    ![Creating a configuration key.](media/isv_new_configuration_key.png)

6. Associate the license code with the configuration key. In Solution Explorer, double-click the configuration key to open the Properties window. In the Properties window, set the **LicenseCode** property to your license code. In this example, we set the **LicenseCode** to **ISVLicenseCode**.

    [![Associating the license code with the configuration keys.](media/isv_select_license_code.png)

7. Associate a configuration key to an element in your solution. For example, create a new form. Right-click the project in Solution Explorer, then click **Add \> New item**. Under **Installed \> Dynamics 365 Items**, choose **User Interface**. In the list, choose **Form** and give it a name. In this example, we named the form **ISVForm**.

    ![Creating a new form.](media/isv_new_form.png)

8. Add a button to the form. Double-click the form in the Solution Explorer. In the Design window, right-click and select **New**, and then **Button**. Set the **Text** property to **ISVButton**.

    ![Adding a button to the new form.](media/isv_button_designtime.png)

    At runtime, the button is visible because it isn't controlled by a configuration key at first. 

    ![New button is visible when it's first added.](media/isv_button_visible_runtime.png)

9.  Associate a configuration key with the button. In the Properties window for the button, set the **Configuration Key** property to your configuration. In this example, we set the **Configuration Key** to **ISVConfigurationKey1**.

    ![Associating a configuration key with the button.](media/isv_select_key_for_button.png) 

    At runtime, the button is not visible because the configuration key must be available and enabled. 

    ![Button is no longer visible.](media/isv_button_invisible_runtime.png)


## Create a package and generate a customer-specific license
1.  Collect the tenant name and ID for the customer to issue the license to. You can find this information at **Settings \> Help \& Support \> About** on the **Licenses** tab. 

    ![Customer's tenant name and ID.](./media/isv_tenant_id.png)

2.  Generate a license for the customer (tenant ID and name), and sign the license by using the certificate's private key. You must pass the following parameters to the **axutil genlicense** command to create the license file.

    | Parameter name  | Description                                                                  |
    |-----------------|------------------------------------------------------------------------------|
    | file            | The name of your license file.                                               |
    | licensecode     | The name of your license code (from Microsoft Visual Studio).                |
    | certificatepath | The path of your certificate's private key.                                  |
    | password        | The password for your certificate's private key.                             |
    | customer        | The customer's tenant name (from the screenshot under step 1).              |
    | serialnumber    | The customer's tenant ID (labeled "Serial number" in the screenshot).       |
    | expirationdate  | Optional: The expiration date for the license.                               |
    | usercount       | Optional: The number that custom validation logic can use as required. This could be users, but is not limited to users. |

    Here is an example.
 
    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\axutil genlicense /file:c:\templicense.txt /certificatepath:c:\tempisvcert.pfx /licensecode:ISVLicenseCode /customer:TAEOfficial.ccsctp.net /serialnumber:4dbfcf74-c5a6-4727-b638-d56e51d1f381 /password:********
    ``` 


3.  Import the license into the target environment.

    > [!NOTE]
    > In production systems, you complete this step from Microsoft Dynamics Lifecycle Services (LCS), by using a deployable package. For more information, see the "Production environments" section later in this article.

    | Parameter name                | Description                                                                                            |
    |-------------------------------|--------------------------------------------------------------------------------------------------------|
    | --setupmode importlicensefile | Use this parameter to inform the setup tool that a license will be loaded.                             |
    | --metadatadir                 | Use this parameter to specify the metadata directory. You should use the default packages directory.   |
    | --bindir                      | Use this parameter to specify the binaries directory. You should use the default packages directory.   |
    | --sqlserver                   | Use this parameter to specify the Microsoft SQL Server. For one-box environment, use a period (**.**). |
    | --sqldatabase                 | Use this parameter to specify the SQL Server database. For one-box environments, use **AXDB**.     |
    | --sqluser                     | Use this parameter to specify the SQL Server user. You should use **axdbadminr**.                  |
    | --sqlpwd                      | Use this parameter to specify the SQL Server password.                                                 |
    | --licensefilename             | Use this parameter to specify the license file that will be loaded.                                    |

    Here is an example.

    ```Console
    C:\AOSService\PackagesLocalDirectory\Bin\Microsoft.Dynamics.AX.Deployment.Setup.exe --setupmode importlicensefile --metadatadir c:\packages --bindir c:\packages --sqlserver . --sqldatabase axdb --sqluser axdbadmin --sqlpwd ******** --licensefilename c:\templicense.txt
    ```

4.  The corresponding configuration key will be available and enabled on the **License configuration** page. By default, the configuration is enabled. For example, see the **ISVConfigurationKey1** configuration key in the following screenshot. 

    ![ISVConfigurationKey1 configuration key enabled on the License configuration page.](media/isv_license_configuration_page.png)

5.  In non-production installations, you must start the database synchronization process from Visual Studio.

After the configuration key is enabled, the button becomes visible, as shown in the following screenshot. 

![Button is visible after the configuration key is enabled.](media/isv_button_visible_runtime.png)

## Protection best practices
Solutions can be delivered in two forms:

-   Model files (source code)
-   Deployable packages (binary)

To protect your configuration keys and license codes, we recommend that you release them in binary form, by using a deployable package. Customers will then be able to install and interact with those elements in Visual Studio. Although customers will be able to refer to items in the deployable package, they won't be able to access source code or make modifications to the items. (However, they can create extensions.) More details about the capability to release solutions in binary form will be available soon. The deployable package (binary) can also include classes and other logic that your customer doesn't require access to and should not be able to customize. 

![Protected vs. unprotected ISV solutions.](./media/isv_protected_solution.png)

## Production environments
To install ISV licenses in production systems, you must use a deployable package through LCS. You can find a template package for configuration mode at the following location in all installations: \<PackagesFolder\>\\bin\\CustomDeployablePackage\\ImportISVLicense.zip (Packages folder is typically under j:\\AOSService\\PackagesLocalDirectory or c:\\AOSService\\PackagesLocalDirectory\\) 

> [!div class="mx-imgBorder"]
> ![Location of the template package for configuration mode.](media/isv_template_location.png)

1.  Make a copy of the package template.
2.  Put the license file in the following folder within the package template: ImportISVLicense.zip\\AosService\\Scripts\\License

More than one license can be installed at a time. If one of the licenses depends on another, make sure that it's named accordingly. (Licenses are installed in alphabetical order.)

## Appendix: Create self-signed certificates for test purposes

> [!NOTE]
> Self-signed certificates can be used only during development. They aren't supported in production environments.

For Platform update 34 and earlier:
(Deprecated - uses SHA1 hash algorithm for license creation)

1. For test purposes, create a self-signed CA certificate. Use the Visual Studio tools prompt to run the following command.

    ```Console
    makecert -r -pe -n "CN=IsvCertTestAuthority O=IsvCertTestAuthority" -ss CA -sr LocalMachine -a sha256 -len 2048 -cy authority -sky signature -b 01/01/2016 -sv c:\temp\CA.pvk c:\temp\CA.cer
    ```

    For more information, see the [MakeCert](/windows/win32/seccrypto/makecert) documentation.

2. Create a certificate by using the CA.

    ```Console
    makecert -pe -n "CN=IsvCertTest O=IsvCertTest" -ss ISVStore -sr LocalMachine -a sha256 -len 2048 -cy end -sky signature -eku 1.3.6.1.5.5.7.3.3 -ic c:\temp\ca.cer -iv c:\temp\ca.pvk -b **/**/**** -sv c:\temp\isvcert.pvk c:\temp\isvcert.cer
    ```

3. Convert the ISV certificate to PFX format.

    ```Console
    pvk2pfx -pvk c:\temp\isvcert.pvk -spc c:\temp\isvcert.cer -pfx c:\temp\isvcert.pfx -po ********
    ```

4. For a test scenario, import the self-signed CA certificate manually on all the AOS instances.

    ```Console
    certutil -addstore root c:\temp\ca.cer
    ```

    However, if a self-signed ISV certificate was used, that certificate must be imported instead of the CA certificate.

    ```Console
    certutil -addstore root c:\temp\isvcert.cer
    ```

For Platform update 35 and later:
(Uses SHA256 hash algorithm for license creation)

1. For test purposes, create a self-signed certificate using the PowerShell command `New-SelfSignedCertificate`:
    1. Create the certificate. (Note: adjust start and end dates accordingly.)

        ```PowerShell
        $cert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "IsvCert" -Type CodeSigningCert -KeyExportPolicy Exportable -HashAlgorithm sha256 -KeyLength 2048 -KeySpec Signature -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" -NotBefore (Get-Date -Year 2020 -Month 1 -Day 1) -NotAfter (Get-Date -Year 2022 -Month 12 -Day 31)
        ```

    2. Get a reference to the new certificate.

        ```PowerShell
        [String]$certPath = Join-Path -Path "cert:\LocalMachine\My\" -ChildPath "$($cert.Thumbprint)"
        ```

    3. Create the secure string password that the certificate uses. (Replace "##############" with the certificate password)

        ```PowerShell
        [System.Security.SecureString]$certPassword = ConvertTo-SecureString -String "##############" -Force -AsPlainText
        ```

    4. Export the certificate private key as **.pfx** file using the password.

        ```PowerShell
        Export-PfxCertificate -Cert $certPath -FilePath "C:\Temp\IsvCert.pfx" -Password $certPassword
        ```

    5. Export the certificate public key as a **.cer** file.

        ```PowerShell
        Export-Certificate -Cert $certPath -FilePath "C:\Temp\IsvCert.cer"
        ```

2. Add the certificate to the root store.

    ```PowerShell
    certutil -addstore root C:\Temp\IsvCert.cer
    ```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
