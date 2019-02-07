---
# required metadata

title: Troubleshooting business events
description: This topic provides information about troubleshooting business events.
author: Sunil-Garg
manager: AnnBe
ms.date: 02/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Business event errors
## Unable to construct endpoint. Exception message: Error retrieving secret '[KeyValueSecretName]' from key vault 'https://[KeyVaultName].vault.azure.net/': AADSTS700016: Application with identifier '7e28cb03-dc28-43b5-b129-e13dcfb4b1fb' was not found in the directory 'ee3fe5c6-26af-42b1-9acf-5ee38e6ead6e'. This can happen if the application has not been installed by the administrator of the tenant or consented to by any user in the tenant. You may have sent your authentication request to the wrong tenant Trace ID: 19dc9946-45b6-4335-9676-6a133dbf4000 Correlation ID: ecbc8a80-f9d0-41ec-9c8f-d334d050bd64 Timestamp: 2019-02-06 23:27:06Z
When this error happens, it usually means that the Azure Active Directory Application ID field value is likely incorrect. Check the AAD Application ID value in the customers azure portal in Azure Active Directory > App Registration.

## Unable to construct endpoint. Exception message: Error retrieving secret '[KeyValueSecretName]' from key vault 'https://[KeyVaultName].vault.azure.net/': An error occurred while sending the request
This is likely do to an incorrect value in the Key Vault DNS Name field. To resolve go to open the customers azure portal and open the customers key vault object, on the Overview section check the DNS Name value.

## Unable to send test event to endpoint. Exception message: 40103: Invalid authorization token signature, Resource:sb://[ServiceBusName].servicebus.windows.net/[QueueName]. TrackingId:cd0eccaa-1717-4f97-b837-4cd7eda99af4_G13, SystemTracker:[ServiceBusName].servicebus.windows.net:[QueueName], Timestamp:2019-02-06T23:36:54
The value in the customers Key Vault Secret is likely incorrect. Check the Key Vault Secret value and make sure it is correct for the endpoint type.

## Unable to construct endpoint. Exception message: Error retrieving secret '[KeyValueSecretName]' from key vault 'https://[KeyVaultName].vault.azure.net/': Access denied
This is likely do to the Azure Active Directory Application ID does not have the appropriate permissions in the Key Vault. To resolve this go to the customers Azure portal and open the Key Vault object, go to Access Policies and add the AAD application with Key, Secret & Certificate Management template.

## Unable to send test event to endpoint. Exception message: 40400: Endpoint not found., Resource:sb://[ServiceBusName].servicebus.windows.net/[QueueName].
This issue is likely do to the queue/topic/hub name being incorrect. Check the *Name field, you can validate this by going to service bus in the customer azure portal and reviewing the Topic or Queue name. If it is an Event Hub go to the Event Hub object in azure and validate the hub name.

## Unable to send test event to endpoint. Exception message: An error occurred while sending the request.
This is likely do to an incorrect endpoint value specified in the Endpoint URL field. Go to the Event Grid object in the customers Azure portal open the Event Grid, from the Overview section this value will be the Topic Endpoint value.

