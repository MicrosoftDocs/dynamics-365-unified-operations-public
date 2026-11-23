---
title: Configure Offer management in Recruiting Add-on
description: Offer management for the Recruiting Add-on lets you configure offer creation, approval workflows, and eSignature integrations. 
ms.author: twheeloc
ms.reviewer: twheeloc
author: twheeloc
ms.date: 11/12/2026
ms.topic: article
---

# Offer management for the Recruiting Add-on

Offer management is a Recruiting Add-on capability that organizations use to configure offer creation, approval workflows, and electronic signature integrations within the application. It supports multiple signing providers and delivery methods, so organizations can align offer package delivery with their licensing and business requirements.

This article explains the concepts and components involved in enabling Offer management, Approval management, and electronic signature integrations. It covers connection references, provider-specific flows, manual email delivery flows, and parent Offer management flows required to configure the application.

## Prerequisites

- Recruiting Add-on solution deployed in the target environment.
- Valid eSign provider license required when eSigning is enabled. Microsoft supports BOYL (Bring Your Own License) model.
- Credentials for Admin user configured on eSign provider tenants.

### Connections

Create connections in the Power Apps Maker Portal before you configure connection references. They authenticate the environment to the connectors used by Offer management flows.

To create the required connections, follow these steps:

1. Open the Power Apps [Maker Portal](https://make.preview.powerapps.com/) and sign in with a user that has the system administrator role.
1. Select the target environment where you want to enable the Offer management feature.

   :::image type="content" source="media/hr-offer-management-setup/image1.png" alt-text="Screenshot of the environment selection in the Power Apps Maker Portal.":::

1. After the environment's home page loads, search for **Connections** in the left-side menu and select it to open the connections page. This page shows all connections created in the environment.

   :::image type="content" source="media/hr-offer-management-setup/image2.png" alt-text="Screenshot of the Connections page listing existing connections in the environment.":::

1. Select **New connection** at the top left of the page to list all supported connectors from Microsoft Power Automate.
1. Search for the connector by using the search lookup at the top right.
1. Select **+** next to the selected connector to create the connection. An authentication window opens for the connector.
1. Sign in with credentials that have a license enabled for the connector. A successful sign-in automatically creates the connection and displays a status of **Connected**.

If the Recruiting Add-on is already set up in the environment, some connections already exist. If a connection for the connector already exists and you need a new connection with different credentials, create a new connection by using the same steps. When cached credentials are used, select the ellipsis on the newly created connection and choose **Switch account** to relaunch the authentication window and update the connection with different credentials.

#### Microsoft managed connection references

| Connection reference | Connector |
| :--: | :--: |
| Recruiting Approvals connection | Standard approval |
| Recruiting Content Conversion connection | Content conversion |
| Recruiting Dataverse connection | Microsoft Dataverse |
| Recruiting Office 365 Outlook connection | Microsoft 365 Outlook |
| Recruiting Teams connection | Microsoft Teams |

### Connection references

Connection references link created connections to Offer management. After you create connections, the system administrator attaches them to the connection references.

To configure connection references, follow these steps:

1. Select **Solutions** in the left menu to open the solutions page in the Maker Portal.
1. Open the **Default Solution** from the **Unmanaged solutions** list.
1. Select **Connection references** from the objects list on the **Default solution** to list all connection references in the environment.
1. Search for the **Recruiting** keyword by using the search lookup at the top right to list all Microsoft Managed Connection References.

   :::image type="content" source="media/hr-offer-management-setup/image4.png" alt-text="Screenshot of the filtered list of Recruiting connection references in the Default Solution.":::

1. Select a connection reference from the filtered list to open its metadata in the right-side panel.
1. Select the **Connection** for the connection reference. Refresh the connection before selecting it to show all available connections.
1. Choose the connection from the list.
1. Select **Save** to complete the connection reference configuration.

### Offer management settings

Offer management settings determine if the feature is enabled, how offer packages are delivered, and which eSign provider is used. A system administrator or recruiting administrator configures these settings from the Recruiting Add-on application.

> [!NOTE]
> To use a different eSign provider than the one Microsoft ships, use the feature extension guide before enabling these settings.

To configure Offer management settings, follow these steps:

1. Open the organization URL in a browser and sign in with a user that has the system administrator or recruiting administrator role.
1. If a list of apps appears, select the Recruiting Add-on app to launch the application. If the Recruiting Add-on is already selected, the application launches directly.
1. In the **Setup** group, select **Offer management** to open the **Offer management settings** page.
1. Select **Edit** to open settings in edit mode.
1. Set the **Enable Offer management** toggle to **Yes** to enable the Offer management feature.
1. After you enable the feature, the **Enable eSigning** setting becomes visible and determines how offer packages are delivered. When set to **Yes**, recruiters can send offer packages for electronic signature by using a supported eSign provider. When set to **No**, offer packages are delivered by using the standard, non-eSignature (manual) process.
1. If you turn **Enable eSigning** on, you must select an **eSign Provider**. This setting determines which licensed eSign provider is used to send offer packages. When you save the settings, the selected provider is activated for all subsequent eSigning operations.
1. Select **Save** or **Save & Close**. A **Settings saved successfully** notification confirms the settings are enabled for the environment.

#### Offer management settings

| Setting | Description |
| :--: | :--: |
| Enable Offer management | Enables Offer management in the application. |
| Enable eSigning | Controls whether offers are sent by using an eSignature provider or manual email delivery. |
| Select eSign Provider | Used when eSigning is enabled. |
| Account for eSign Provider | Required only if there's additional information required to store related to the selected eSign provider. |

## Offer management flows

After you configure the offer management settings, turn on the related flows to enable services such as approval and offer package delivery. These flows reside in the **Microsoft D365 Recruiting Flows** managed solution.

To enable flows, follow these steps:

1. Go to the **Solutions** page in the Maker Portal.
1. Open the **Microsoft D365 Recruiting Flows** solution under the managed solutions list, which contains all Microsoft-managed Power Automate flows.
1. Search for the **Offer** keyword in the top-right search lookup to list all Offer management flows.
1. To enable a flow, select it and choose **Turn On** from the ellipsis.

### Approval process flows

The approval process relies on the following flows.

#### Approval related flows

| Flow name | Type |
| ------------------------------------ | ------------------ |
| Send offer approval motification | Child flow |
| Candidate offer approval | Parent flow |
| Cancel offer approval notification | Independent flow |

Enable the flows in the following sequence:

1. Send offer approval notification.
1. Candidate offer approval.
1. Cancel offer approval notification.

### Offer package delivery flows

The system administrator enables only one delivery method based on business requirements and licensed procurement.

#### Manual sign related flows

Enable the following flows to enable the manual signing flow.

| Flow name |
| ----------------------------------------------------------- |
| Offer management - Send offer to applicant without e-sign |
| Offer management - Receive signed offer without e-sign |
| Offer management - Void offer without e-sign |

#### Parent offer processing flows

Enable parent offer management flows after you enable the selected delivery method flows.

| Flow name |
| -------------------------------------------- |
| Offer management - Send offer to applicant |
| Offer management - Void sent offer |

1. Enable **Offer management - Send offer to applicant**.
1. Enable **Offer management - Void sent offer**.

#### eSign provider flow customization and support

The eSign provider flows that come with **Offer management** are reference implementations to help customers establish integration between the Recruiting Add-on application and the selected eSign provider.

Customers can use the provided flows as delivered, modify them to meet organization-specific requirements, or create their own implementation in place of the reference flows.

Microsoft provides support for the parent **Offer management** flows because they create, update, and manage data within the Recruiting Add-on application as part of the core application integration. Provider-specific eSign reference flows are sample integration assets. Customers can raise support requests for issues encountered with reference flows. However, customer-specific customizations and customer-developed implementations are owned by the customer.

#### Publishing customizations

When you finish all setup steps, publish all customizations so that the configured setup can sync with internal components.

#### Update Offer management settings

When you update **Offer management** settings, such as enabling or disabling eSigning, changing the eSign provider, or updating the eSign provider account ID, follow these steps to ensure the changes are fully reflected:

1. Turn off all parent Power Automate flows.
1. Turn off all child Power Automate flows.
1. Perform **Publish All Customizations** in the environment.
1. Turn on all child Power Automate flows.
1. Turn on all parent Power Automate flows.

These steps are required because Power Automate caches dynamic content when a flow is turned on. Turning the flows off clears the cached metadata, and turning them back on refreshes the cache so that the updated **Offer management** settings are picked up correctly.

#### Audit enablement

The **Offer management** feature relies on the platform-provided Dataverse auditing capability. Auditing in Power Platform is optional for this feature and can be enabled or disabled based on an organization's compliance and business requirements.

If your organization chooses to enable auditing, see [Manage Dataverse auditing - Power Platform](/power-platform/admin/manage-dataverse-auditing) to configure auditing for your Dataverse environment.
