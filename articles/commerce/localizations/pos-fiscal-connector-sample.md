---
# required metadata

title: Fiscal integration sample for connector located on POS register.
description: This topic provides an overview of the fiscal integration sample for connector, located on register in Microsoft Dynamics 365 Commerce.
author: Mikhailc
ms.date: 02/14/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: mikhailc
ms.search.validFrom: 2018-11-1

---
# Fiscal integration sample for connector located on POS register. 

[!include[banner](../includes/banner.md)]

This topic provides an overview of installation for the fiscal integration sample for connector located on the POS register in Microsoft Dynamics 365 Commerce.

The Commerce functionality for connector, located on register includes the point of sale (POS) fiscal connector sample for the [fiscal integration framework](fiscal-integration-for-retail-channel.md) , which enables POS to communicate directly with a fiscal device or service without a hardware station. 

## Use the sample

You can download the sample as a zip file and open it in Microsoft Visual Studio 2017. After you open the sample, build the solution. After a successful build, output installer packages will be created.

If you want to use the sample in the legacy software development kit (SDK), see [Using the sample in legacy SDK](pos-fiscal-connector-sample.md#use-the-sample-in-the-legacy-sdk) .

## Configuration

### Configure Commerce channels

To enable POS to use the new fiscal connector, you must create a fiscal connector technical profile in Commerce headquarters and configure the following settings:

- **Connector type** = **Local**
- **Connector location** = **Register**

You can then add it  to the required POS functionality profile as a fiscal service.

For more information about how to configure fiscal integration, see [Set up the fiscal integration for Commerce channels](setting-up-fiscal-integration-for-retail-channel.md).

### Configure HTTPS and TLS

To use the POS fiscal connector, the fiscal device or service must be configured to use Hypertext Transfer Protocol Secure (HTTPS).
For information about how to set up HTTPS in EFR, see [EFR Reference](http://public.efsta.net/efr/).

Ensure that the client devices that run Cloud POS or Modern POS use Transport Layer Security (TLS) 1.2 or later. TLS 1.0 and 1.1 must be disabled.

## Use the sample in the legacy SDK
To use the point of sale (POS) fiscal connector in the legacy software development kit (SDK), follow these steps.

1. If the solution was previously built, clean it by running the following command-line command.

    ``` 
    C:\Commerce-Samples-EndToEndSolutions\src\FiscalIntegration\PosFiscalConnectorSample> msbuild /t:Clean
    ```

1. Copy the **Pos.Extension** folder to the POS **Extensions** folder of the legacy SDK (C:\RetailSDK\src\POS\Extensions).
1. Rename the copy of the **Pos.Extension** folder  to **PosFiscalConnector**.
1. Remove the following folders and files from the **PosFiscalConnector** folder:

    - bin
    - DataService
    - devDependencies
    - Libraries
    - obj
    - Contoso.PosFiscalConnectorSample.Pos.csproj
    - RetailServerEdmxModel.g.xml
    - tsconfig.json

1. Open **CloudPos.sln** or **ModernPos.sln**.
1. In the **Pos.Extensions** project, include the **PosFiscalConnector** folder.
1. Open **extensions.json**, and add the **PosFiscalConnector** extension.
1. Build the SDK.

For more information about POS samples, see [Run the POS samples](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/pos-run-samples) .
