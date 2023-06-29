---
# required metadata

title: Troubleshoot business events
description: This article provides information about troubleshooting business events.
author: Sunil-Garg
ms.date: 10/31/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Troubleshoot business events

[!include[banner](../includes/banner.md)]

This article provides tips for troubleshooting issues that involve business events.

| Issue | Possible resolution | 
|---------------|---------------------|
| Unable to find navigation to business events in the **System parameters** form | You can access business events by going to **System administration > Set up > Business events**. This change was made when the business events feature was made generally available in Platform update 26.|
| **Error:** Unable to construct endpoint. Exception message: Error retrieving secret '[KeyValueSecretName]' from key vault 'https://[KeyVaultName].vault.azure.net/': AADSTS700016: Application with identifier '7e28cb03-dc28-43b5-b129-e13dcfb4b1fb' wasn't found in the directory 'ee3fe5c6-26af-42b1-9acf-5ee38e6ead6e'. | This can happen if the application hasn't been installed by the administrator of the tenant or consented to by any user in the tenant. It's likely that you may have sent your authentication request to the wrong tenant.|
|**Error:** Trace ID: 19dc9946-45b6-4335-9676-6a133dbf4000 Correlation ID: ecbc8a80-f9d0-41ec-9c8f-d334d050bd64 Timestamp: 2019-02-06 23:27:06Z| This error typically means that the value in the **Azure Active Directory Application ID** field is incorrect. Check the **Azure Active Directory Application ID** value in the customers Azure portal in **Azure Active Directory > App Registration**.|
|**Error:** Unable to construct endpoint. Exception message: Error retrieving secret '[KeyValueSecretName]' from key vault 'https://[KeyVaultName].vault.azure.net/': An error occurred while sending the request.|This error is likely due to an incorrect value in the **Key Vault DNS Name** field. To resolve this, go to the customer's Azure portal and open the key vault object. In the **Overview** section, check the **Key Vault DNS Name** value.|
|**Error:** Unable to send test event to endpoint. Exception message: 40103: Invalid authorization token signature, Resource:sb://[ServiceBusName].servicebus.windows.net/[QueueName]. TrackingId:cd0eccaa-1717-4f97-b837-4cd7eda99af4_G13, SystemTracker:[ServiceBusName].servicebus.windows.net:[QueueName], Timestamp:2019-02-06T23:36:54|The value in the customer’s Key Vault Secret is likely incorrect. Check the **Key Vault Secret** value and make sure that it's correct for the endpoint type.|
|**Error:** Unable to construct endpoint. Exception message: Error retrieving secret '[KeyValueSecretName]' from key vault 'https://[KeyVaultName].vault.azure.net/': Access denied|This is likely due to the **Azure Active Directory Application ID** not having the appropriate permissions in the Key Vault. To resolve this, go to the Azure portal and open the **Key Vault** object. Go to **Access Policies** and add the Azure Active Directory application with Key, Secret, and Certificate Management template.|
|**Error:** Unable to send test event to endpoint. Exception message: 40400: Endpoint not found., Resource:sb://[ServiceBusName].servicebus.windows.net/[QueueName]. |This issue is likely a result of the queue/topic/hub name being incorrect. Check the **Name** field by going to service bus in the Azure portal and reviewing the **Topic** or **Queue** name. If it's an Event Hub, go to the **Event Hub** object in Azure and validate the **Hub** name.|
|**Error:** Unable to send test event to endpoint. Exception message: An error occurred while sending the request.|This is likely due to an incorrect endpoint value specified in the **Endpoint URL** field. Go to the **Event Grid** object in the Azure portal and open the **Event Grid**. In the **Overview** section, this value will be the **Topic Endpoint**.|
|Business events don't show up in the **Business event catalog** in finance and operations apps. | The **Business event catalog** is built during the full database sync. As a result, there are some use cases, as noted below, where a manual refresh of the catalog is needed in order to see the new business events. A manual refresh can be invoked from the catalog by going to **Manage > Rebuild business events catalog**.<br><br>When you're implementing business events in Visual Studio you may not see the newly coded business event in the catalog.<br><br>When new workflows are configured, such as the workflow elements or steps, events might not show up in the business events catalog.<br><br>In other situations, when you don’t see certain business events, doing a manual refresh should resolve the issue.|
|Finance and operations business events aren't available in the **Catalog Assignment** tab of the virtual entity solution in the Power Platform maker portal. | Business events that are available in the **Business event catalog** in finance and operations apps should sync automatically to the virtual entity solution in the Power Platform portal. If the business events aren't available in the Power Platform portal automatically, a sync can be triggered manually by using the **Rebuild business event catalog** action on the **Manage** menu of the **Business event catalog** page. |
|- 0 is an invalid bundle size<br>- Business events aren't getting triggered<br>- Microsoft Flow isn't getting triggered by business events<br>- Unable to configure the business event because it has reached the limit of zero configured endpoints |One of the reasons why this issue can occur is if certain parameters aren't set as expected in the **BusinessEventsParameters** table. This is due to an update in which some of the business events parameters not being set correctly.<br><br>In a nonproduction environment, you must update the parameters in **System administration > Setup** to set retry count = 3; End points allowed per event = 10 and wait time = 1000. After this update, restart the batch service and run IISReset to pick up the latest values.
|Platform update 30 compiler warning when creating custom payload context fields by augmenting via Chain of Command (CoC) the addProperties method in the adapter class. **Class 'BusinessEventsServiceBusAdapter' is internal in model 'ApplicationFoundation' and cannot be extended**.  |This is a change in the compiler that prevents an internal API from being extended. This is being tracked as a bug to provide alternate ways to add custom properties. For more information, see this [Yammer discussion](https://www.yammer.com/dynamicsaxfeedbackprograms/threads/376155850727424).
|**Error:** Unable to load one or more of the requested types. Retrieve the LoaderExceptions property for more information|This error message on the error tab of active business events can typically be resolved by rebuilding the catalog.
|Alert business events don't trigger|One of the reasons why an event isn't triggering could be a potential issue with alerts email functionality. Try turning off the send email option in the alert to see if that resolves the issue.
|Unable to send test event to endpoint. Exception message: The underlying connection was closed: Could not establish trust relationship for the SSL/TLS secure channel.|Make sure the middleware is using TLS 1.2
| After configuring data events for EcoResProductV2Entity, you receive an error when creating a new released product: "Cannot execute a data definition language command on Products V2 (EcoResProductV2Entity)." | This issue occurs when the Engineering Change Management configuration key is disabled on the environment. Virtual tables, and the associated data events, don't support entities that have temporary tables as backing tables for the entity. When a configuration key is disabled, all physical tables for that configuration key are replaced with temporary tables so the system doesn't need to be recompiled for schema changes. This results in a temporary table being included in the virtual table query, which causes the error message. <br><br>To work around this in your environment, you can enable the Engineering Change Management configuration key or use another entity, such as RetailEcoResProductEntity, which doesn't include backing tables linked to disabled configuration keys. |
|**Error**: Response Status code does not indicate success: 400 error: ”invalid_client”,”error_description”;”Expected aud https://<i></i>securityservice.operations365.dynamics.com  but found.”. | For more information, see [Cloud Hosted Environments are unable to use Business Events or Virtual Entities and Receive a 400 error](che-be-ve-error.md). |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

