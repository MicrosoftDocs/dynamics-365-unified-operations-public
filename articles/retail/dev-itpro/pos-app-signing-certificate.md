---
# required metadata

title: Sign MPOS with code signing certificate
description: This topic explains how to sign MPOS with code signing certificate.
author: mugunthanm
manager: AnnBe
ms.date: 09/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 28021
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mumani
ms.search.validFrom: 2019-09-2019
ms.dyn365.ops.version: AX 10.0.5

---

# Sign MPOS with code signing certificate

[!include [banner](../includes/banner.md)]

To install Modern POS (MPOS) in Windows OS its recommended to sign the MPOS app with signing certificate from trusted provider. To sign the MPOS app with certificate, Retail SDK\\Build tool\\Customization.settings file supports three options:

-   Add the Secure file task part of Azure DevOps build steps and upload the certificate to secure file task and use the secure file task output path variable as parameter in the Customization.settings file.

    -   **Note:** Secure File task, don’t support password protected certificate, remove the password before uploading to this task. Since the certificate is uploaded to the secure file system task in Azure, its fine to remove the password only for this step but before removing the password discuss with the security experts and then decide, don't decide based on this statement. The certificate uploaded to the build task can be accessed only by the build pipeline during build flow and no other process can access it. So, with secure file task the additional layer of password security is not required only during the build signing process. Don’t remove the certificate password for other scenarios.

-   **Certificate placed in the File system:** Downloaded/generated certificate is placed in the file system where the build is running and the VSO agent or build user should have access to this path and file.

-   Use thumbprint to look up in the certificate in the store and sign with that certificate.

**Using Secure File task is the recommended approach for UWP app signing.**

<https://docs.microsoft.com/en-us/windows/uwp/packaging/auto-build-package-uwp-apps#configure-package-signing>

![MPOS app signing flow](media/POSSigningFlow.png)

## Steps to configure the certificate for signing:

### Certificate in the file system/secure location:

-   Download the [Download File task](https://docs.microsoft.com/en-us/visualstudio/msbuild/downloadfile-task?view=vs-2019) and add it as first step in the build process. The advantage of using the Secure File task is the file is encrypted and placed in the disk during build and no matter whether the build pipelines succeeds, fails, or canceled, the file is deleted from its download location after the build process is completed.

    1.  Download and Add the Secure File task as first step in the Azure DevOps build pipeline. You can download the secure file task from [here](https://marketplace.visualstudio.com/items?itemName=automagically.DownloadFile).

    2.  Upload the certificate to the Secure file task and set Reference name under Output Variables. Ex: MySigningCert

        ![Secure file task](media/SecureFile.png)

    3.  Create a new variable in the Azure DevOps pipeline by clicking the New Variable button under the Variables tab.

    4.  Provide some name for the variable. Ex: CertFile. In the value field $(MySigningCert.secureFilePath).

    5.  Save the variable.

    6.  Open the Customization.settings file from the RetailSDK\\BuildTools and update the ModernPOSPackageCertificateKeyFile with variable name created in the Azure DevOps pipeline (Step 3).

        Ex: &lt;ModernPOSPackageCertificateKeyFile Condition="'$(ModernPOSPackageCertificateKeyFile)' == ''"&gt;$( CertFile)&lt;/ModernPOSPackageCertificateKeyFile&gt;

<!-- -->

### Downloaded or generated certificate:

If downloaded or generated certificate is used to sign the MPOS app then the update the "ModernPOSPackageCertificateKeyFile" node in the BuildTools\\Customization.settings file to point to the pfx file location ("$(SdkReferencesPath)\\appxsignkey.pfx").

**Ex:**

&lt;ModernPOSPackageCertificateKeyFile Condition="'$(ModernPOSPackageCertificateKeyFile)' == ''"&gt;$(SdkReferencesPath)\\appxsignkey.pfx&lt;/ModernPOSPackageCertificateKeyFile&gt;

In this case the certificate  file name is appxsignkey.pfx and its placed in Retail SDK\\Reference folder.

### Thumbprint to sign the MPOS app:

If thumbprint is used to sign the MPOS app then install the certificate locally and then update the thumbprint value in the ModernPOSPackageCertificateThumbprint node in the BuildTools\\Customization.settings file.

This option will work fine if the build user is local user but if you are using the Azure DevOps/VSO agents to generate the build then the agent may not have permission to access the cert store to use the certificate for signing or the build machine will not have the certificate installed. The workaround in this case is change the build user to local user and install the certificate in the box but this option will not work well if you don’t have admin access to the box etc.

**Note:** If pfx file or secure file task option is used to sign the app then leave the “ModernPOSPackageCertificateThumbprint” node in Customization.settings empty and if thumbprint option is used then leave the ModernPOSPackageCertificateKeyFile empty. If both the values are updated, then the build will fail.
