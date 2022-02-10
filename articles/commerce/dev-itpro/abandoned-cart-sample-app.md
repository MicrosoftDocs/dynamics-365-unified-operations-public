---
# required metadata

title: 
description: This topic explains how to configure Azure Active Directory as the authentication method in Microsoft Dynamics 365 Commerce point of sale.
author: stuharg
ms.date: 02/08/2022
ms.topic: article
ms.prod:
ms.technology: 
# optional metadata
# ms.search.form:
audience: Developer
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: global
# ms.search.industry:
ms.author: stuharg
ms.search.validFrom:
ms.dyn365.ops.version: 10.0.18
---

# Detect abandoned carts and send notifications to customers

[!include [banner](includes/banner.md)]

## Overview

The ability to recover revenue and retain customers through abandoned cart notifications is an important capability that Dynamics 365 for Commerce now supports. By customizing a connector sample provided by Microsoft, retailers can now access shopping carts on Retail Server that have not been modified within a time window defined by the retailer. Those carts can then be retrieved and augmented with product and customer data, and passed on to a 3rd party email marketing provider where an email can be generated and sent to the customer. 

The email that customers receive can contain the following information:

- Customer first name

- Customer last name

- Customer email

- URL that that returns the customer to their cart

- Transaction currency

- List of products in their cart. Each product has:

- - Product display name
  - Product ID (used for assembling a URL to the product description page)
  - Product image that can be automatically resized to accommodate various viewport sizes
  - Product image alt text
  - Product unit price

 

## Overview of the abandoned cart connector sample

Abandoned cart retrieval and sending to a 3rd party email marketing provider is enabled through a connector model that Microsoft provides through the Dynamics 365 Commerce SSK. The connector handles communication with Retail Server, leverages Azure KeyVault for security, handles scheduling of cart retrieval for a specified time window, and retrieves order and product data. The connector also provides a sample implementation for an integration with a 3rd party email marketing provider. Out of the box, the connector is built to communicate with [Emarsys](https://emarsys.com), and it can be easily customized to integrate with other solutions such as ConstantContact, MailChimp, SendGrid or others. 

 

![Component diagram of abandoned cart connector sample app](C:\Users\stuharg\OneDrive - Microsoft\Documents\GitHub\Dynamics-365-Operations\articles\commerce\dev-itpro\media\AbandonedCartConnector.png)

>  [!NOTE]
>
> Microsoft does not provide an affordance for customers who wish to opt out of having their cart data passed to an email marketing provider, or who wish to have their data removed. If you plan to do business in regions that mandate these options for customers, you will need to provide the necessary infrastructure and customizations to collect and track the customer preference, and suppress the passing of their data to your email platform based on that preference. Additionally, you will need to define a process for purging customer data from your email marketing provider if requested by a customer. 

 

## Obtaining the code sample

The Abandoned Cart sample app is included in the Retail software development kit (SDK), starting with version 10.0.16. The code can be found under …\RetailSDK\Code\SampleExtensions\RetailServer\Extensions.AbandonedCartSample. To learn more about the Retail SDK and where to obtain it, see the [Retail software development kit (SDK)](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fdynamics365%2Fcommerce%2Fdev-itpro%2Fretail-sdk%2Fretail-sdk-overview&data=04|01|stuharg%40microsoft.com|4ecdbff39ad948e2937b08d8956eb0e8|72f988bf86f141af91ab2d7cd011db47|1|1|637423649928432139|Unknown|TWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D|1000&sdata=XcUtwz7EfRpiSooEidtOCkA0JH909Io2KqMC9TO8hVI%3D&reserved=0) help topic.  

> [!NOTE] Although the sample code was first made available in 10.0.16 builds, it is compatible with Retail Server builds starting with 10.0.13. 

 

## Prerequisites and dependencies

Before you can deploy and configure the Abandoned cart connector sample code, the following prerequisites must be in place:

### Dynamics 365 Commerce access

In order to configure and deploy the abandoned cart connector app, you will need access to the following Dynamics 365 Commerce resources

1. Admin access to Dynamics 365 Commerce Headquarters for your environment
2. Access to the LCS project for your environment

### Set up Azure Cosmos

The abandoned cart connector app uses Azure Cosmos DB to track the IDs and timestamps of carts that have previously been retrieved. You may choose to use Azure Cosmos DB to persist these data, or you can customize the code sample to integrate with another data storage option. 

If you use Azure Cosmos DB, the following prerequisites must be in place before you can run this sample. 

1. An active Azure Cosmos DB account - If you don't have an account, refer to the [Create a database account](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet#create-a-database-account) article
2. Retrieve the URI and PRIMARY KEY (or SECONDARY KEY) values from the Keys blade of your Azure Cosmos DB account in the Azure portal. For more information on obtaining endpoint & keys for your Azure Cosmos DB account refer to [View, copy, and regenerate access keys and passwords](https://docs.microsoft.com/en-us/azure/cosmos-db/manage-account#keys)

[Learn more about Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction#:~:text= Key Benefits  1 Turnkey global distribution.,Designed with transparent horizontal partitioning and... More )

### Set up an Azure Key Vault

The abandoned cart connector app uses Azure Key vault to store the names and secrets of various components that require secure access.

1. Follow the instructions in the [Manage Key Vault in Azure Stack Hub using the portal](https://docs.microsoft.com/en-us/azure-stack/user/azure-stack-key-vault-manage-portal?view=azs-2002) help topic to set up Azure Key Vault
2. Create secrets for 
   1. Emarsys API user name and API secret
   2. Abandoned cart application ID and secret 


The abandoned cart connector sample code makes use of Azure Default Credentials to access Azure Key Vault. Please provide **List** and **Read** permissions to the identity you plan to use for accessing Key Vault. 

[Read more about Azure default credentials]([https://docs.microsoft.com/en-us/dotnet/api/azure.identity.defaultazurecredential?view=azure-dotnet ](https://docs.microsoft.com/en-us/dotnet/api/azure.identity.defaultazurecredential?view=azure-dotnet)) 



## Set up Connector App ID in AAD Tenant

Follow instructions here to create application id for abandoned cart sample code. [Use the portal to create an Azure AD application and service principal that can access resources](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal)

  

## Whitelist the Abandoned cart connector app ID against the Retail Server API

Instructions for whitelisting an application ID in Azure can be found at https://community.dynamics.com/ax/b/axforretail/posts/support-for-service-to-service-authentication-in-retail-server. 

 

## Configure the abandoned cart connector

The configuration file for the Abandoned Cart connector sample app is at the root of the AbandonedCartDetectionSample directory and is called appSettings.json. Below are the individual settings and their purpose:

 

**KeyVaultOptions**

| **Property** | **Purpose**                                                  |
| ------------ | ------------------------------------------------------------ |
| KeyVaultURI  | The DNS Name of  the key vault you're using on https://portal.azure.com |

 

**RetailServerClientOption**s

| **Property**                                  | **Purpose**                                                  |
| --------------------------------------------- | ------------------------------------------------------------ |
| TenantId                                      | The AAD Tenant ID  for the Azure Tenant ID you're using      |
| RetailServerAudienceId                        | Can be left as is                                            |
| AppIdKeyVaultSecretName                       | Name of the secret  you created for the Abandoned Cart Connector App ID. |
| AppSecretKeyVaultSecretName                   | Name of the secret  that stores app secret for abandoned cart app id |
| RetailServerUrl                               | URL of your Retail  Server instance, which is found in LCS   |
| OperatingUnitNumber                           | Operating Unit  Number (OUN), which is found in Headquarters |
| IncludeAbandonedCartsModifiedSinceLastMinutes | Defines the **beginning of the time window** for the  abandoned carts you want to retrieve. For example, setting the value to 120  will retrieve all carts that were last modified within 120 minutes of now,  but not after the end of the time window defined in  ExcludeAbandonedCartsModifiedSinceLastMinutes |
| ExcludeAbandonedCartsModifiedSinceLastMinutes | Defines the **end of the time window** for the abandoned  carts you want to retrieve. As an example, setting this value to 30 will  retrieve all carts that were modified between two hours ago and 30 minutes  ago (when 120 is used as the value for  IncludeAbandonedCartsModifiedSinceLastMinutes.) In practice,   ExcludeAbandonedCartsModifiedSinceLastMinutes defines the length of  time you wish to wait before declaring a cart to be abandoned. |
| ReturnToCartUrl                               | The URL of the  cart on your e-commerce site (refer format in app.config.) |

 

 

**AzureCosmosOptions**

The abandoned cart retrieval job status, cart IDs and modified timestamps are stored in Azure Cosmos. By default, this config file is configured to point to the local emulator instance of Azure Cosmos. You will need to configure these settings to interact with the Cosmos instance in your Azure subscription when deploying the connector to production. For local or sandbox testing, you can use the [Azure Cosmos Emulator](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)

 

| **Property** | **Purpose**                              |
| ------------ | ---------------------------------------- |
| EndPointUri  | provided by Azure  or emulator           |
| PrimaryKey   | provided by Azure  or emulator           |
| DatabaseId   | Leave default  value or provide your own |
| ContainerId  | Leave default  value or provide your own |

 

 

**EmarsysClientOptions**

NOTE: If you are integrating with a different email marketing provider, you will extend the IEmailProvider interface as appropriate to talk to that provider

 

| **Property**                  | **Purpose**                                                  |
| ----------------------------- | ------------------------------------------------------------ |
| ApiUrl                        | https://api.emarsys.net/api/v2/event/{0}/trigger             |
| ExternalEventId               | The id of the  external event record that is created in Emarsys. Found under Trigger  settings in the campaign you created for sending abandoned cart mails |
| ApiUserNameKeyVaultSecretName | Name of the key  where the Emarsys API user name is stored.  |
| ApiSecretKeyVaultSecretName   | Name of the key  for the Emarsys API secret is stored.       |
| EmarsysContactKeyId           | 3 // ID of the  email column in the Emarsys contact DB (should not need to be changed. ) |

 

**MediaOptions**

If you are using the e-commerce capabilities in Dynamics 365 Commerce, you have the option to leverage the Digital Asset Manager to retrieve product images. 

 

| **Property**                        | **Purpose**                                                  |
| ----------------------------------- | ------------------------------------------------------------ |
| ImageServerUrl                      | The root URL of  your site's digital asset manager. This value can be found in the Media  Server Base URL Property Key under **Modules  > Retail and commerce >**       **setup >  Channel profiles.** |
| ImageViewPorts                      |                                                              |
| ImageViewPorts/Viewport             |                                                              |
| ImageViewPorts/imageWidth           |                                                              |
| imageViewPort/imageHeight           |                                                              |
| imageViewPort/useForDefaultImageTag | Image to use when  the <picture /> HTML tag isn't supported for a web browser or email  client |

## Additional resources





[!INCLUDE[footer-include](../includes/footer-banner.md)]