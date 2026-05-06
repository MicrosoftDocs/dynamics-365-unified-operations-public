---
title: Enable contextual switching of Store Commerce from any application
description: Learn how external applications can launch Store Commerce and invoke specific business actions such as add items to cart or recall order etc. to complete a workflow or transaction
author: shajain
ms.date: 04/23/2026
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: mirao
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2026-04-23
---

# Launch Store Commerce via custom protocol URLs

[!include [banner](../includes/banner.md)]

This article explains how external applications can launch Store Commerce and invoke specific business actions such as add items to cart or recall order etc. to complete a workflow or transaction

## Scenarios

Contextual switch to Store Commmerce functionality enables store associates to move seamlessly between external applications and Store Commerce without manually navigating to the correct screen or re-entering data. This capability helps reduce checkout time and can eliminate multiple manual steps from common workflows. The following examples describe scenarios where custom protocol URLs can be helpful:

- **Look item online and add to Store Commerce** — An auto parts shop uses a proprietary system to look up parts. The customer is added to the transaction in Store Commerce, and the store associate then opens the proprietary system to select the part. With a single click, Store Commerce is launched with the selected item already added to the current transaction. This capability eliminates the need for the associate to search for the same part again using the part number from the proprietary system, saving time and reducing errors.
- **Clienteling and appointments** — When a customer arrives for a scheduled appointment, the associate's device receives a notification that opens Store Commerce with the customer's profile and pre-selected products from their wishlist or prior consultation. This process helps the associate provide a personalized experience and reduces setup time.
- **Order fulfillment handoff** — A back-office system approves a customer order and hands it off to the store. The associate receives a link that opens Store Commerce and recalls the order, so that the associate can begin processing fulfillment immediately.

In addition to these scenarios, ISVs and partners can build custom actions for industry-specific workflows and invoke them from their own applications by using the same protocol. Learn more in [Extensibility](#extensibility).

## Overview

Store Commerce supports launching the application and executing business actions through custom protocol URLs. An external application can construct a URL that opens Store Commerce and performs a specific action, such as creating a transaction or recalling an order.

The URL format is:

```
ms-d365sc://executeAction?actionName={actionName}&param={base64-encoded-json}
```

For Cloud POS (browser), append the parameters to the Cloud POS URL:

```
https://{your-cpos-url}/POS?actionName={actionName}&param={base64-encoded-json}
```

**Components**:

| Component | Description |
|-----------|-------------|
| `ms-d365sc://` | Custom protocol scheme registered by Store Commerce |
| `executeAction` | Fixed path (do not change) |
| `actionName` | The action to invoke (for example, `D365.CreateTransaction`) |
| `param` | Base64-encoded JSON containing action parameters |

> [!NOTE]
> The `actionName` is kept readable (not encoded) for logging and diagnostics. The `param` value is standard base64 encoding of a UTF-8 JSON string.

## Prerequisites

- Store Commerce version 10.0.48 or later.
- The `StoreCommerce.EnableDeepLinkFlight` feature flag must be enabled (enabled by default).
- The user must be logged in. If the user is not logged in when a URL is received, Store Commerce queues the request and processes it after login.
- Use the latest version of Commerce SDK i.e., SDK versions 9.58 or higher if you are building your Store Commerce app.

## Supported platforms

Custom protocol URLs work in both cold start (app not running) and warm start (app already running) scenarios. In a cold start, Store Commerce launches and processes the request after the user logs in. In a warm start, the running instance receives and processes the request immediately.

| Platform | Support |
|----------|---------|
| **Windows** | Supported |
| **Android** | Supported |
| **Cloud POS** | Supported |
| **iOS** | Planned |

## Built-in actions

Built-in actions use the `D365.` prefix (for example, `D365.CreateTransaction`).

To discover the available actions and their parameter contracts, reference the typed interfaces exported from the POS extensibility API:

- **Parameter interfaces**: Exported under `Commerce.Framework.DeepLink` namespace from `PosApi/Extend/DeepLink`. Each action has a corresponding parameter interface (for example, `ICreateTransactionActionParameters`, `ICreateCustomerOrderActionParameters`, `IRecallOrderActionParameters`).
- **Replacement handler classes**: Each replaceable action exports a typed handler class from `PosApi/Extend/DeepLink` (for example, `CreateTransactionReplacementDeepLinkActionHandler`). The presence of a replacement class is the definitive list of which built-in actions exist and are extensible.

These interfaces are the source of truth for required and optional parameters, enums, and data types. Refer to them directly rather than maintaining a separate parameter reference.

**Example URL**:

```
ms-d365sc://executeAction?actionName=D365.CreateTransaction&param=ewogICAgImN1c3RvbWVySWQiOiAiMDA0MDAzIiwKICAgICJpdGVtcyI6IFsKICAgICAgICB7CiAgICAgICAgICAgICJwcm9kdWN0SWQiOiAyMjU2NTQyMTk2MywKICAgICAgICAgICAgInF1YW50aXR5IjogMgogICAgICAgIH0sCiAgICAgICAgewogICAgICAgICAgICAicHJvZHVjdElkIjogMjI1NjU0MjE5NjQKICAgICAgICB9CiAgICBdLAogICAgIm1vZGUiOiAiVm9pZEFuZENyZWF0ZSIKfQ==
```

Decoded `param`:

```json
{
    "customerId": "004003",
    "items": [
        {
            "productId": 22565421963, // Product variant RecordId
            "quantity": 2
        },
        {
            "productId": 22565421964
        }
    ],
    "mode": "VoidAndCreate"
}
```
## Parameter encoding

1. Construct a JSON object with the action's parameters.
2. Serialize to a UTF-8 string.
3. Encode with standard base64 (`btoa()` in JavaScript, `Convert.ToBase64String()` in C#).
4. Set as the `param` query parameter value.

**Limits**: The overall URL should stay under 2,048 characters.

## Extensibility

The custom protocol framework supports three extension patterns:

- **Create a new action**: Register a custom action handler that responds to a new `actionName`. Extend `DeepLinkActionHandlerBase` from `PosApi/Create/DeepLink` and register in `manifest.json` under `components.create.deepLinkActions`. The framework automatically prefixes your action name with the extension package name (for example, `ContosoRetail.CheckInventory`).

- **Replace a built-in action**: Completely replace the behavior of an existing `D365.*` action. Extend the specific per-action replacement class from `PosApi/Extend/DeepLink` (for example, `CreateTransactionReplacementDeepLinkActionHandler`) and register in `manifest.json` under `components.extend.deepLinkActions`. This is a pure replacement — you do not have access to the original implementation.

- **Add triggers**: Hook into any action's execution without replacing it. Three trigger types are available: `PreDeepLinkAction` (cancelable, fires before the action), `PostDeepLinkAction` (fires after success), and `DeepLinkActionFailure` (fires on error). Triggers are global and fire for all actions — use `options.actionName` to filter. Register in `manifest.json` under `components.extend.triggers`.

For implementation details and working code, refer to the extension samples: [Store Commerce custom protocol extension sample](https://aka.ms/Contextualswitch).

## Known limitations

- iOS platform support is not yet available.
- All actions require the user to be authenticated. Unauthenticated requests are queued and processed only after login.
- Queued requests are cleared when the user logs off.
- Extension action names are auto-prefixed with the package name to prevent naming conflicts.
- Only one request can be queued at a time. If a new request arrives while one is queued, the new request replaces the queued one.
