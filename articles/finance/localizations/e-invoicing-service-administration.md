---
# required metadata

title: Electronic invoicing administration components
description: This topic provides information about the components that are related to administration of Electronic invoicing.
author: gionoder
ms.date: 08/31/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Electronic invoicing administration components

[!include [banner](../includes/banner.md)]


This topic provides information about the components that are related to administration of Electronic invoicing. It also provides information about how to configure the Electronic invoicing service.

## Azure

Use Microsoft Azure to create the secrets for the key vault and set up a storage account. Then use the key vault secrets and the storage account SAS token in the configuration of Electronic invoicing.

## Lifecycle Services

Use Microsoft Dynamics Lifecycle Services (LCS) to enable the Electronic invoicing Add-in for your LCS deployment project.

> [!NOTE]
> The installation of the add-ins in LCS requires at least a **Tier 2 environment**. For more information about environment planning, see [Environment planning](../../fin-ops-core/fin-ops/imp-lifecycle/environment-planning.md).
 

## Regulatory Configuration Services

Dynamics 365 Regulatory Configuration Services (RCS) is the interface that is used to configure Electronic invoicing. Resources such as environments and electronic invoicing features are created, maintained, and hosted in RCS. When the resources are ready, they are published to Electronic invoicing service.

For RCS sign-up, see [Regulatory services](https://marketing.configure.global.dynamics.com/).

For more information about RCS, see [Regulatory Configuration Services (RCS) - Globalization features](rcs-globalization-feature.md)

### Integration with Electronic invoicing 

Before you can use RCS to configure electronic invoices, you must configure RCS to allow for communication with Electronic invoicing. You complete this configuration on the **Electronic invoicing** tab of the **Electronic reporting parameters** page.

#### <a id='svc-endpoint-uris'></a>Service endpoint

Electronic invoicing is available in several Azure datacenter geographies. The following table lists the availability per region.


| Datacenter Azure geography | Service endpoint URI                                                       |
|----------------------------|----------------------------------------------------------------------------|
| United States              | <p>https://gw.us-il101.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il102.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il103.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il104.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il105.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il106.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il107.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il108.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.us-il109.gateway.prod.island.powerapps.com/electronicinvoicing</p> |
| Europe                     | <p>https://gw.eu-il101.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il102.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il103.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il104.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il105.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il106.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il107.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il108.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il109.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.eu-il110.gateway.prod.island.powerapps.com/electronicinvoicing/</p> |
| United Kingdom             | <p>https://gw.uk-il101.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.uk-il102.gateway.prod.island.powerapps.com/electronicinvoicing/</p> |
| Asia                       | <p>https://gw.as-il101.gateway.prod.island.powerapps.com/electronicinvoicing/</p><p>https://gw.as-il102.gateway.prod.island.powerapps.com/electronicinvoicing/</p> |

### Service environments

Service environments are logical partitions that are created to support execution of the globalization features in Electronic invoicing. The security secrets and digital certificates, and the governance (that is, access permissions), must be configured at the service environment level.

Customers can create as many service environments as they want. All the service environments that a customer creates are independent of each other.

Service environments must be created and maintained in RCS. When the service environments are ready, they must be published to Electronic invoicing.

#### Service environment status

Service environments can be managed through status. The possible options are:

- **Not published** – The environment has been created, but it hasn't yet been published.
- **Published** – The environment has been published to Electronic invoicing.
- **Changed** – The attributes of a published environment have been changed, but the changes haven't yet been published.

#### Customer secrets

The Electronic invoicing service is responsible for storing all your business data in the Azure resources that your company owns. To ensure that the service works correctly, and that all the business data that is required for and generated by Electronic invoicing is accessed appropriately, you must create two main Azure resources:

- An Azure storage account (Blob storage) that will store electronic documents, including electronic invoices, results of document transformations, and responses from external web services.
- An Azure key vault that will store certificates and the uniform resource identifier (URI) of the storage account (SAS token).


A dedicated Key Vault and customer storage account must be allocated specifically for use with Electronic Invoicing. For more information, see [Create an Azure storage account and a Key Vault](e-invoicing-create-azure-storage-account-key-vault.md).

To monitor the health of your Key Vault and receive alerts, configure the Azure Monitor for key Vault. By enabling Key Vault logging, you can monitor how, when, and by whom your Key Vaults are accessed. For more information, see [Monitoring and alerting for Azure Key Vault](/azure/key-vault/general/alert) and [How to enable Key Vault logging](/azure/key-vault/general/howto-logging?tabs=azure-cli).

As a best practice, periodically rotate the secrets. For more information, see [Secrets documentation](/azure/key-vault/secrets/).

#### Users

Each service environment must list the users who can connect from Dynamics 365 Finance and Dynamics 365 Supply Chain Management in Electronic invoicing.

#### Publication

Service environments must be published to Electronic invoicing before they can be used. Only published environments can be accessed by Finance and Supply Chain Management. Additionally, a service environment must be published before any updates to its attributes will take effect on the electronic invoicing service.

### Connected applications

Connected applications are the instances of Finance and Supply Chain Management that you might want to reach through RCS. Besides the application URL and its tenant, a connected application contains the credentials that enable RCS to connect to the environment.

Through the connected applications, you can configure part of the electronic invoicing feature in Finance and Supply Chain Management to make the whole electronic invoicing feature work.

## Finance and Supply Chain Management

### Integration with Electronic invoicing

Before you can use Finance and Supply Chain Management to issue electronic invoices through Electronic invoicing, it must be configured to allow for communication with the service.

#### Electronic invoicing integration feature

To enable communication between Finance and Supply Chain Management and Electronic invoicing, you must turn on the **Electronic Invoicing integration** feature in the **Feature management** workspace.

#### Service endpoint

The service endpoint is the URL where Electronic invoicing is located. Before electronic invoices can be issued, the service endpoint must be configured in Finance and Supply Chain Management to allow for communication with the service.

To configure the service endpoint, go to **Organization administration \> Setup \> Electronic document parameters**, and then, on the **Electronic invoicing** tab, in the **Endpoint URL** field, enter the appropriate URL from the table in the [Service endpoint](#svc-endpoint-uris) section earlier in this topic.

#### Environments

The environment name that is entered in Finance and Supply Chain Management refers to the name of the environment that is created in RCS and published to Electronic invoicing.

The environment must be configured on the **Electronic invoicing** tab of the **Electronic document parameters** page. In that way, every request to issue electronic invoices contains the environment where Electronic invoicing can determine which electronic invoicing feature must process the request.

## Additional resources

- [Configure electronic invoices in RCS](e-invoicing-configuration-rcs.md)
- [Issue electronic invoices in Finance and Supply Chain Management](e-invoicing-issuing-electronic-invoices-finance-supply-chain-management.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
