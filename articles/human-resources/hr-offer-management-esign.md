---
title: Set up eSign providers for Offer management
description: Extend Offer management to support new eSign providers using Power Automate. Learn about connections, child flows, event handling, and parent flow integration.
author: twheeloc
ms.author: twheeloc
ms.reviewer: twheeloc
ms.date: 11/14/2026
ms.topic: article
---


# Offer management eSign provider extensibility concepts

Offer management eSign provider extensibility is a Microsoft Power Platform capability that organizations can use to extend Offer management to support more eSign providers through **Power Automate**. By using this approach, you can integrate provider-specific functionality while continuing to use the standard Offer management experience.

This article describes the components, flows, and configuration involved in extending Offer management for a new eSign provider. It also describes the responsibilities associated with building and maintaining these custom integrations.

## Prerequisites

- System administrator access.
- Access to Power Apps Maker Portal and Power Automate.
- Access to the target eSign provider environment and credentials.

## Provider registration in Offer management

Provider registration makes a new eSign provider available within Offer management settings. Register a provider in the **Power Apps Maker Portal** by using an unmanaged solution. Although you can use the default solution, use a dedicated solution because you add extra components, such as connection references and flows, over time.

The environment variable **Offer management eSign Providers** stores the list of supported providers. Each provider entry contains:

- Display name - Recruiting administrators see this name in Offer management settings.
- Logical name - Power Automate flows and switch statements use this name.

Format the environment variable value as follows:

- Separate multiple providers with a comma (,).
- Separate the **Display name** and **Logical name** with a colon (:).
- Place the **Display name** before the **Logical name**.
- Use only lowercase letters in logical names, with no numbers or special characters.

To register a provider, add the **Offer management eSign Providers** environment variable to the solution, append the new provider information to the existing value (for example, **Test Sign:testsign**), save the environment variable, and publish all customizations. The new provider is available in Offer management settings. If you don't see the updates, perform a hard refresh.

Use the **Logical name** configured here when you extend parent flows.

### Provider connections

A connection establishes an authenticated link between Power Platform and the eSign provider.

To create a connection, follow these steps:

1. In **Power Apps Maker Portal**, select **New connection**.
1. Select the connector associated with the eSign provider, complete authentication by using the provider credentials, and save.

Connector capabilities vary by provider. Before starting implementation, review Microsoft connector documentation to understand supported triggers, actions, authentication requirements, and connector limitations.

### Connection references

A connection reference decouples flows from specific connections. Use connection references for all eSign provider–specific actions. Create a connection reference in the integration solution by providing a **Display name** and **Name**, selecting the provider connector, associating a previously created connection, saving, and publishing all customizations.

### Send offer communication child flow

The Send offer communication child flow creates and sends offer packages. Configure it with the following inputs:

- Offer ID
- Email subject
- Email body

Use the Offer ID to get extra information needed to create the package, such as offer details, signer information, and offer documents.

Providers support one of two package creation approaches:

- Single-step - One provider action creates the package, attaches documents, adds signers, and sends the package.
- Multistep - Multiple actions handle different parts of package creation, like package creation, document attachment, signer assignment, and package delivery.

The flow returns **EnvelopeId**, **EnvelopeStatus**, and **ServerError** outputs. Ensure the returned status values match the values that the parent flow expects.

#### Void offer communication child flow

The Void offer communication child flow withdraws a previously sent package. Configure it with the following inputs:

- EnvelopeId
- VoidReason

Use provider-specific actions to void, cancel, or withdraw the package. The flow returns **Status** and **ServerError** outputs. Ensure the returned status values match the values that the parent flow expects.

#### Event processing flows

Event processing flows respond to provider events during the signing lifecycle. They identify the related offer package, update communication records, and synchronize status back to Offer Management.

### Signed or Completed event

Configure this event for completed signing events. The flow identifies the related offer package, downloads the signed document package, attaches signed documents to the candidate offer record, completes the active communication record, and updates Offer management with the final signed status.

### Declined event

Configure this event for declined packages. The flow identifies the related offer package, locates the active communication record, updates it with a **Declined** status, completes the communication lifecycle, and updates Offer management to reflect the declined state.

### Delivered event

Configure this event for delivered packages when supported by the provider. The flow identifies the related offer package, locates the active communication record, updates the communication status to **Delivered**, and saves the communication updates.

Not all eSign providers support Delivered events.

#### Parent flow integration

Connect child flows to parent flows through switch cases that use the provider **Logical name**. Child flows must use the same trigger and exit used in the reference child flows. Enable child flows before enabling parent flows.

### Send offer communication parent flow

The **Offer management - Send offer to applicant** parent flow contains the action **Process offer to selected eSign provider**, where you add a new switch case by using the provider **Logical name** as the switch case value.

Within the switch case, add **Run a Child Flow** and select the **Send offer communication** child flow. Use the following input mappings:

- Map **OfferId** from the **Offer Id** input parameter that you pass to the parent flow.
- Map **EmailSubject** from the output of Compose **Email subject**.
- Map **EmailBody** from the output of Compose **Email body**.

Capture the **EnvelopeId**, **EnvelopeStatus**, and **ServerError** outputs that the child flow returns and store them in parent flow variables.

Remove unused provider-specific logic if required, such as Manual sign related child flows that aren't turned on for package delivery. Otherwise, the parent flow isn't owned. To remove these flows, delete the **Run child flow** and **set variable** actions from the case. To delete manual sign, follow the **Check if eSigning is enabled** action. After configuration, save the flow, turn on the **Send offer communication** child flow, and turn on the parent flow.

### Void offer communication parent flow

The **Offer management - Void sent offer parent flow** contains the **Process void offer to eSign provider** action, where you add a new switch case that uses the provider **Logical name** as the switch case value.

Within the switch case, add **Run a child flow** and select the **Void offer communication** child flow.

Input mappings:

- Map **EnvelopeId** from the **Envelope ID** field of the **Get offer communication record** action.
- Map **VoidReason** from the parent flow input parameter.

Capture the **Status** and **ServerError** outputs that the child flow returns and store them in parent flow variables.

Remove unused provider-specific logic if required, such as Manual sign related child flows that aren't turned on for package withdrawal. Otherwise, the parent flow isn't owned. To remove these flows, delete the **Run child flow** and **Set variable** actions from the particular case. To delete **Manual sign**, follow the **Check if e-Signing is enabled** action. After configuration, save the flow, turn on the **Void offer communication** child flow, and turn on the parent flow.

#### Additional configuration

Use **Offer management eSign provider account** to store provider-specific account information required by provider-specific **Power Automate** flows.

### Extending eSign Provider via plugin solution or web resource

In addition to Power Automate child flows, Offer management can be extended with a custom eSign provider integration built as a plugin solution or a web resource.

Whichever option is used, the custom implementation must follow the same communication flow as the default implementation and produce the same Offer Communication records and statuses, so that recruiters see the correct offer state in Offer management. 

The Send offer and Void (withdraw) offer flows in the following sections describe the expected behavior and list the status values to set for each outcome.

### Send offer flow

When the offer reaches the **Ready for communication** stage, the **Send offer** button is enabled on the **Communication** grid.

When the recruiter selects **Send offer**, a custom page (msdyn_sendoffercommunication_c8655) opens where the recruiter selects the email template and the documents to include.

When the recruiter fills in all the details, they select the **Send offer** button on that page. This action starts creating the offer package and sending it to the candidate. Keep any customized logic behind the same button if customers choose to continue with the same custom page.

When the process finishes, the system creates an Offer communication record. The system creates the record whether the offer dispatch succeeds or fails.

On success, the system updates the **Candidate offer** status to **Offer sent** and sets the Offer communication record to **Active**.

Only one Active offer communication can exist for an offer at a time. You can send a new offer package only after the active communication concludes.

Store any identifier that the eSign provider returns for package identification in the Offer communication for future reference and usage.

The Offer file and Offer communication entities have a many-to-many relationship, and they're related. Customers can implement this relationship as needed.

Send offer flow diagram with Recruiter, System, and Dataverse records swimlanes. The recruiter selects **Send offer**, selects the email template and documents, and sends them. The system creates and sends the offer package, and then creates an Offer communication record.

On success, the **Offer status** becomes **Offer sent** and the communication is **Active**. If there's a failure, the system sets the communication to **Communication error** with a **Send offer failed** reason, and the recruiter can retry.

#### Void (Withdraw) offer flow

To void an offer, follow these steps:

1. Select the Communication record where **Send offer** succeeded. The **Void offer** button then becomes visible.
1. Select **Void offer**. A pop-up window opens where the recruiter must specify the reason for voiding the offer.
1. Confirm **Void offer** in the pop-up. The system starts voiding the offer. The system uses the Envelope ID stored on the Offer communication record to identify the offer package.
1. When the void process succeeds, the system updates the **Candidate offer** status and the existing Offer communication record. If the void process fails, the system doesn't change the **Candidate offer** status, and creates a new Offer communication record for tracking purposes.

### Status tracking

Set the following values on the Candidate offer (msdyn_candidateoffer) and Offer communication (msdyn_offercommunication) records for each outcome.
The field logical names are msdyn_offerstatus on Candidate offer, and msdyn_status and msdyn_communicationstatusreason on Offer communication.

|Communication outcome |    Candidate offer status  |    Offer communication status     |   Communication status reason |
|----------------------|----------------------|-----------------------|-----------------------|
|Send succeeds | Offer sent |Active |Offer sent |
|Send fails| Unchanged Communication error |Send offer failed|
|Void succeeds| Offer withdrawn completed |Offer withdrawn |
|Void fails| Unchanged communication error |Withdraw offer failed|
|Candidate sign offer| Signed completed |Offer signed |
|Candidate decline offer| Offer declined completed |Offer declined |

### Webhook development  

In addition to sending offer and void offer communications, you need to handle the webhook APIs. These APIs help you track the decisions candidates make on offer packages. Candidates can sign or decline the offer. Most eSign providers broadcast these events through webhooks. You can listen to these webhooks and update the status for the candidate offer and offer communication. In both cases, whether the candidate signs or declines the offer, mark the offer communication completed. Most eSign providers give an identifier for the package sent to the candidate, so you can use it to search for the offer via communication.

##### Entities involved in offer management

The following entities are used in the offer management feature.

 |Entity | Name Usage  |
  |--------- |----------- |
 |Candidate offer |  Stores all metadata about the offer, such as candidate, job details, status, and more.  |
 |Offer file | Stores the offer file attached to the offer.  |
 |Offer approval  |Tracks the offer approval process.  |
 |Offer communication  |Tracks offer communication details between the recruiter and candidate.  |

#### Recommendations

- Create and validate integrations in a sandbox or demo environment first.
- Validate package creation and package delivery.
- Validate package withdrawal scenarios.
- Validate **Signed**, **Declined**, and **Delivered** events where supported.
- Validate document download and attachment processing.
- Validate communication status updates.
- After successful validation, implement and test production connector-based flows.

## Microsoft supportability disclaimer

- Microsoft provides the Offer management extensibility framework through Microsoft Power Platform and **Power Automate**.
- You're responsible for designing, developing, testing, deploying, and maintaining custom integrations for additional eSign providers.
- Microsoft doesn't provide implementation support for provider-specific business logic, custom **Power Automate** flows, webhook implementations, or custom connector configurations.
- If a Microsoft-supported connector isn't available for the selected eSign provider, you're responsible for developing and maintaining the required integration components.
- Validate all custom integrations in a sandbox or nonproduction environment before production deployment.
