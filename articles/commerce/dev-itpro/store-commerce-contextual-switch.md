---
title: Enable contextual switching of the Store Commerce app
description: Learn how external applications can launch the Dynamics 365 Commerce Store Commerce app and invoke specific business actions to complete a workflow or transaction.
author: shajain
ms.date: 05/07/2026
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: mirao
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2026-05-07
---

# Launch Store Commerce app by using custom protocol URLs

[!include [banner](../includes/banner.md)]

This article explains how external applications can launch the Dynamics 365 Commerce Store Commerce app and invoke specific business actions, such as adding items to cart or recalling orders, to complete a workflow or transaction.

## Scenarios

The contextual switching functionality in Store Commerce helps store associates move seamlessly between external applications and Store Commerce without manually navigating to the correct screen or reentering data. It helps reduce checkout time and eliminate multiple manual steps from common workflows. Here are a few example scenarios where you can use this capability:

- **Look up items online and add to Store Commerce**: An auto parts shop uses a proprietary system to look up parts. The customer is added to the transaction in Store Commerce, and the store associate then opens the proprietary system to select the part. With a single click, Store Commerce launches with the selected item already added to the current transaction. This capability eliminates the need for the associate to search for the same part again by using the part number from the proprietary system, helping save time and reduce errors.

- **Clienteling and appointments**: When a customer arrives for a scheduled appointment, the associate's device receives a notification that opens Store Commerce with the customer's profile and preselected products from their wishlist or prior consultations. This process helps the associate provide a personalized experience and reduces setup time.

- **Order fulfillment handoff**: A back-office system approves a customer order and hands it off to the store. The associate receives a link that opens Store Commerce and recalls the order, so that the associate can begin processing the fulfillment immediately.

Independent software vendors (ISVs) and partners can also build custom actions for industry-specific workflows and invoke them from their own applications by using the same protocol. For more information, see [Extensibility](#extensibility).

## Overview

Store Commerce supports launching applications and executing business actions through custom protocol URLs. An external application can construct a URL that opens Store Commerce and performs a specific action, such as creating a transaction or recalling an order.

Use the following URL format:

`ms-d365sc://executeAction?actionName={actionName}&param={base64-encoded-json}`

For Cloud point of sale (CPOS) (browser), append the parameters to the Cloud POS URL:

`https://{your-cpos-url}/POS?actionName={actionName}&param={base64-encoded-json}`

### Components

| Component | Description |
| --------- | ----------- |
| `ms-d365sc://` | Custom protocol scheme registered by Store Commerce |
| `executeAction` | Fixed path (don't change this value) |
| `actionName` | The action to invoke (for example, `D365.CreateTransaction`) |
| `param` | Base64-encoded JSON containing action parameters |

> [!NOTE]
> The `actionName` value is readable (and not encoded) for logging and diagnostics purposes. The `param` value is a standard Base64 encoding of a UTF-8 JSON string.

## Prerequisites

- Use Store Commerce version 10.0.48 or later.
- Enable the `StoreCommerce.EnableDeepLinkFlight` feature flag (enabled by default).
- The user must be signed in. If the user isn't signed in when a URL is received, Store Commerce queues the request and processes it after sign-in.
- Use the latest version of Commerce SDK, such as SDK versions 9.58 or higher, if you're building your Store Commerce app.

## Supported platforms

Custom protocol URLs work in both cold start (app not running) and warm start (app already running) scenarios. In a cold start, Store Commerce launches and processes the request after the user signs in. In a warm start, the running instance receives and processes the request immediately.

| Platform | Support |
| -------- | ------- |
| Windows | Supported |
| Android | Supported |
| Cloud POS | Supported |
| iOS | Planned |

## Built-in actions

Built-in actions use the `D365.` prefix (for example, `D365.CreateTransaction`).

To discover the available actions and their parameter contracts, reference the typed interfaces exported from the POS extensibility API:

- **Parameter interfaces**: Exported under the `Commerce.Framework.DeepLink` namespace from `PosApi/Extend/DeepLink`. Each action has a corresponding parameter interface (for example, `ICreateTransactionActionParameters`, `ICreateCustomerOrderActionParameters`, `IRecallOrderActionParameters`).
- **Replacement handler classes**: Each replaceable action exports a typed handler class from `PosApi/Extend/DeepLink` (for example, `CreateTransactionReplacementDeepLinkActionHandler`). The presence of a replacement class is the definitive list of which built-in actions exist and are extensible.

These interfaces are the source of truth for the required and optional parameters, enums, and data types. Refer to them directly rather than maintaining a separate parameter reference.

Here's an example URL:

`ms-d365sc://executeAction?actionName=D365.CreateTransaction&param=ewogICAgImN1c3RvbWVySWQiOiAiMDA0MDAzIiwKICAgICJpdGVtcyI6IFsKICAgICAgICB7CiAgICAgICAgICAgICJwcm9kdWN0SWQiOiAyMjU2NTQyMTk2MywKICAgICAgICAgICAgInF1YW50aXR5IjogMgogICAgICAgIH0sCiAgICAgICAgewogICAgICAgICAgICAicHJvZHVjdElkIjogMjI1NjU0MjE5NjQKICAgICAgICB9CiAgICBdLAogICAgIm1vZGUiOiAiVm9pZEFuZENyZWF0ZSIKfQ==`

Decoded `param`:

```json
{
  "customerId": "004003",
  "items": [
    {
      "productId": 22565421963,
      "quantity": 2
    },
    {
      "productId": 22565421964
    }
  ],
  "mode": "VoidAndCreate"
}
```

where `productId` is the product variant `RecordId`.

## Parameter encoding

1. Construct a JSON object with the action's parameters.
1. Serialize the JSON object to a UTF-8 string.
1. Encode the string with standard Base64 (`btoa()` in JavaScript, `Convert.ToBase64String()` in C#).
1. Set the encoded string as the `param` query parameter value.

> [!NOTE]
> Make sure you limit the overall URL length to under 2,048 characters.

## Extensibility

The custom protocol framework supports three extension patterns:

- **Create a new action**: Register a custom action handler that responds to a new `actionName`. Extend `DeepLinkActionHandlerBase` from `PosApi/Create/DeepLink` and register in `manifest.json` under `components.create.deepLinkActions`. The framework automatically prefixes your action name with the extension package name (for example, `ContosoRetail.CheckInventory`).

- **Replace a built-in action**: Completely replace the behavior of an existing `D365.*` action. Extend the specific per-action replacement class from `PosApi/Extend/DeepLink` (for example, `CreateTransactionReplacementDeepLinkActionHandler`) and register in `manifest.json` under `components.extend.deepLinkActions`. This action is a pure replacement - you don't have access to the original implementation.

- **Add triggers**: Hook into any action's execution without replacing it. The following three trigger types are available:

  - `PreDeepLinkAction` (cancelable, fires before the action)
  - `PostDeepLinkAction` (fires after success)
  - `DeepLinkActionFailure` (fires on error)

  Triggers are global and fire for all actions. Use `options.actionName` for filtering and register in `manifest.json` under `components.extend.triggers`.

For the implementation details and working code, refer to the extension samples in [Store Commerce custom protocol extension sample](https://aka.ms/Contextualswitch).

## Known limitations

- iOS platform isn't supported yet.
- All actions require the user to be authenticated. Unauthenticated requests are queued and processed only after sign-in.
- Queued requests are cleared when the user signs out.
- Extension action names are autoprefixed with the package name to prevent naming conflicts.
- Only one request can be queued at a time. If a new request arrives while one is queued, the new request replaces the queued request.
