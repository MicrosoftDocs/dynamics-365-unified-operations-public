---
# required metadata

title: TL;DR - Important changes to the development and ALM experiences in 10.0.10 - 10.0.13 
description: This topic highlights the major changes in the development tools, SDKs, and ALM .
author: RobBertram 
manager: AnnBe
ms.date: 07/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail 
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: mumani
ms.search.validFrom: 2020-04-10
ms.dyn365.ops.version: 10.0.10
---

# TL;DR - Important changes to the development and ALM experiences in 10.0.10 - 10.0.13 

It is common for those on Commerce to pause updates and then leapfrog to the current version.  Please read this so that you land safely.  Ther are significant changes and updates to the development and build tools.  As always, Microsoft strives to provide updates with no breaking changes.  The changes described in this article do not require you to refactor your customizations.  

Customizations following best practice patterns and developed on prior versions are deployable on the latest service update.  

## Who should read this

[!include [banner](../../includes/banner.md)]

If you have a technical role (or manage someone that does) in your organization who works with Dynamics 365 Finance, Supply Chain Management, or Commerce, then please continue reading.  There have been some substantial improvements and changes, and there is a wealth of information and documentation about what has changed and what is coming.  The goal of this tl;dr ("too long; didn't read") article is to consolidate all of that information into a single spot so that you have better clarity on specific changes that will be required in terms of updating your development environments or adjusting your ALM processes.  


## Overall improvements, changes, and notes (versionless or 10.0.10+)

The following features are available to anyone but might not have been fully documented.
- [All in one application (X++) deployable package](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/aio-deployable-packages) (for X++):  Merge all of your custom code and ISV models into a single custom package.
  - Custom payment connectors for card-not-present can be included in your [application (X++) deployable package natively starting in 10.0.10](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/aio-deployable-packages).
  - All in one package will be **mandatory** in version 10.0.13.
- The commerce deployable package (a.k.a. RetailSDK) should not be deployed to the AOS anymore.  Instead upload your self-service installers to LCS and use the [synchronize feature](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/synchronize-installers).
- Use a Microsoft-hosted build agent instead of a dedicated build machine
  - For building [application deployable packages](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/hosted-build-automation) 
  - For building [commerce deployable package](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/sdk-build-pipeline)
> [!NOTE]
> This will increase your azure consumption.  However, you should see cost savings if you can decomission your dedicated build server.

Always check to see [what is new and changed](https://docs.microsoft.com/en-us/dynamics365/finance/get-started/whats-new-home-page) for a general overview of each application release.

## What has changed in the 10.0.10 release
- Custom payment connectors for card-not-present can be included in your [application (X++) deployable package natively starting in 10.0.10](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/aio-deployable-packages).
- Upload your self-service installers to LCS and use the [synchronize feature](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/synchronize-installers).
  > [!NOTE]
  > This is a manual process for now.  We are working to incorporate the new Commerce asset types into the [DevOps pipeline tools for Dynamics 365 Finance and Operations](https://marketplace.visualstudio.com/items?itemName=Dyn365FinOps.dynamics365-finops-tools) so that you can automate the upload to LCS.
- Bugfix (ecom):  Custom retail deployable packages no longer need to include the Adyen payment DLLs.

## What has changed in the 10.0.11 release

- The [Retail SDK has been updated to Visual Studio 2017](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/migrate-sdk). 
  - VM templates for 10.0.13 are expected to have Visual Studio 2017 installed.  So you will need to [update manually](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/migrate-sdk#migrate-to-the-sdk-for-visual-studio-2017).
  - You also need to install the [D365 add-on (X++ development tools)](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/update-development-tools). 
    > [!NOTE]
    > The article above is a little out of date and might not be specific enough. 
    > 1. Download the latest D365 service update package from the shared asset library.  
    > 2. It is a .zip file.  Open it and look for the following directory: DevToolsService\Scripts
    > 3. Extract the Scripts folder to somewhere local (e.g., K:\Temp\Scripts).
    > 4. Look for the file **Microsoft.Dynamics.Framework.Tools.Installer.vsix** which should be around 150 megabytes.  Right-click and choose **Open**.
    > [![Visual Studio 2017 D365 extension](./media/vs2017-extensions.png)](./media/vs2017-extensions.png)
  - Navigate to the folder containing your unmodified 10.0.11 Retail SDK. 
    1. Create a backup copy of it for safe keeping.
    2. Open Visual Studio 2017 in Administrator mode, then open each standard solution file in the SDK folder. You will likely encounter a message like the one below.  Click Continue. 
    [![Visual Studio 2017 D365 extension](./media/vs2017-individual-workloads.png)](./media/vs2017-extensions.png)
    3. Open the VS 2017 command prompt (as **administrator**) and verify that the standard SDK compiles.  Go to the root of the RetailSDK folder and execute the following command:  (*If it fails, you skipped a step from above.*)
    ```CMD
    msbuild /t:rebuild
    ```
    > [!IMPORTANT]
    > Visual Studio 2015 uses version 14 of the developer command prompt.  Visual Sutdio 2017 uses version 15. 
    > [![Visual Studio 2017 D365 extension](./media/vs2017-command-prompt.png)](./media/vs2017-command-prompt.png)     

- References have been updated to PackageReference (NuGet package reference).  This means that project references are much easier to maintain.  It also means that you have to manually update *every* custom project in the RetailSDK.  Expect to spend about 5 minutes per project.  Look at how the standard projects were updated and emulate that.
  - Obviously, make sure that everything compiles and a package can be created from your local dev box.
  - Next, make sure that your build server is updated to VS 2017.  
  - Your build server will likely fail as the NuGet reference folders are exceptionally long and will exceed the 260 character file path limit.  
- RetailSDK bloat:  An unmodified retail deployable package is now around 340 megabytes.  With customizations, this might increase to 350.  If you try to deploy this to your Commerce Cloud Scale Unit (aka RCSU), you will get an error message informing you that [packages larger than 300 megabytes](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-packaging#deploy-the-deployable-packages) cannot be deployed.
  - Follow the instructions in the above link, and manually remove the self-service installer files.  
  - Upload the much smaller package to LCS and continue with your deployment as usual.
  > [!NOTE]
  > For now the build and deployment scripts embedded in the deployable package are hard-coded to check for the self-service installers.  Expect an update to the build process when we update the pipeline tools to support automatic uploading of Commerce self-service installers to LCS.



## What has changed in 10.0.12

- Generating the [Commerce proxy](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/typescript-proxy-retail-pos) gets easier.

## What has changed in 10.0.13

- Application development (X++) now requires Visual Studio 2017.  If you haven't updated yet, review the section above on 10.0.11.  
- We are actively working to rebuild the VHD template used to provision Dev/Test environments so that they include Visual Studio 2017 automatically.  There is no confirmed date when it will be available, but we expect it to be ready shortly after 10.0.13 is generally available in September, 2020.

## Where to go for help
1. First, double (and triple) check to ensure that you followed each step already listed in the relevant articles listed above.  
2. Check with your partner.  They know your business and setup better than anyone else.  There might be something unique (custom) with your setup that they can quickly identify and address. 
3. Check the [RetailSDK FAQ](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/sdk-faq).  It is a living document and will be updated as common issues are identified.
4. Submit a support request through LCS.  Provide as much information as you can about the problem.  Copy your FastTrack solution architect when you submit the request.
5. Expect to do a screen share with your partner, the support specailist, your solution architect, or possibly a combination of the three.  Be prepared to reproduce the error.
