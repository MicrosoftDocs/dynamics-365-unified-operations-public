---
# required metadata

title: Manage secrets for Retail channels
description: This topic explains how to extend the channel database.
author: AamirAllaq
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
ms.custom: 83892
ms.search.region: Global
# ms.search.industry:
ms.author: aamiral
ms.search.validFrom: 2019-09-17
ms.dyn365.ops.version: AX 7.0.0, Retail September 2017 update

---

# Manage secrets for Retail Channels

This article explains how to manage secrets when you are using an extension with Retail channels that require access to secrets. 

## Sequence

1. Development steps for extension developer.
    1. Create a test secret in Azure Key Vault
    2. Configure head office client to connect to the Azure Key Vault
    3. Specify an extension key name for a Key Vault secret in Head Office>Key Vault Parameters form. The same name must be used in the next step.
    4. Use a CommerceRuntime API (GetUserDefinedSecretStringValueServiceRequest) to get secrets. Pass a unique secret name to identify the secret.  
    5.  As part of extension setup documentation, state the secret name referenced within the extension. A recommended pattern for the extension developer is to use a namespace for the secret name to avoid conflicts with other extensions.
2.	Deployment & configuration steps for IT Pro or implementation partner
    1. Apply the extension to customer environment (https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/apply-deployable-package-system?toc=/retail/toc.json).
    2. Upload (or type in) desired secrets to Azure Key Vault (https://docs.microsoft.com/en-us/azure/key-vault/key-vault-overview)
    3. Configure head office client to connect to Azure Key Vault in Head Office>Key Vault Parameters form.
    4. Specify extension secret name for a Key Vault secret in the head-office client in Head Office>Key Vault Parameters form.

## Consume the secret in the CRT extension

To consume the secret in the extension we added the below request and response:

| Request/Response                               | Parameters               | Description                                                                                                                                    |
|------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| GetUserDefinedSecretStringValueServiceRequest  | string secretName        | Request class for getting user defined secrets from headquarters.                                                                              |
| GetUserDefinedSecretStringValueServiceResponse | string SecretStringValue | Response class for getting user defined secrets from headquarters.                                                                             
                                                                                                                                                   
   The response will SecretStringValue and extensons can type cast it to X509Certificate2 type or use it as string value depends on the scenario.  |

Steps to read the secret in CRT extension:

1.  Create a new CRT extension project (C# class library project type). Use the sample templates from the Retail SDK RetailSDK\\SampleExtensions\\CommerceRuntime)
2.  In the CRT extension you can create new request/response or add pre/post trigger for the existing CRT request and call this.
3.  For example, in the below sample we will add trigger for the SaveCartRequest and call the GetUserDefinedSecretStringValueServiceRequest to read the secret by passing the secret key configured in the HQ. You no need to write custom code to read the secret from HQ, use our request and response to read the value.

```csharp
 public class CustomSaveCartTrigger : IRequestTrigger
 {
 /// <summary>
 /// Gets the list of supported request types.
 /// </summary>
 public IEnumerable<Type> SupportedRequestTypes
 {
 get
 {
 return new[]
 {
 typeof(SaveCartRequest)
 };
 }
 }

 /// <summary>
 /// Pre trigger code.
 /// </summary>
 /// <param name="request">The request.</param>
 public void OnExecuting(Request request)
 {
 ThrowIf.Null(request, "request");
 Type requestedType = request.GetType();
 if (requestedType == typeof(SaveCartRequest))
 {
 // Sample code to get the secret in string format.
 var request = new GetUserDefinedSecretStringValueServiceRequest("SecretName");
 string response = request.RequestContext.Execute< GetUserDefinedSecretStringValueServiceResponse>(request).SecretStringValue;
 // Sample code to get the secret in X509Certificate2 format.
 var request = new GetUserDefinedSecretStringValueServiceRequest ();
 X509Certificate2 response = request.RequestContext.Execute< GetUserDefinedSecretStringValueServiceRequest >(request).Certificate;
 // custom code to additional processing with secrets.
 }
 }

 /// <summary>
 /// Post trigger code.
 /// </summary>

 /// <param name="request">The request.</param>
 /// <param name="response">The response.</param>

 public void OnExecuted(Request request, Response response)
 {
 }
 }
}

 }
 ```
4. Build the CRT extension project.
5. Copy the output class library and paste it in the …\\RetailServer\\webroot\\bin\\Ext for manual testing.
6. Update the extension composition section in the CommerceRuntime.Ext.config file with the custom library information, like below:
    ```Xml
    <add source="assembly" value="your custom library name" />
    ```

## Credential rotation
Credential management with this approach allows for more streamlined credential rotation. To update a secret, an IT admin only needs to update the secret in Key Vault, with no need to change the extension. Once a secret is updated, the new value gets used once the cache expires.

## Offline support
Currently, offline support for credentials requires the extension code to handle failover to offline when Key Vault credential is not available/accessible.
