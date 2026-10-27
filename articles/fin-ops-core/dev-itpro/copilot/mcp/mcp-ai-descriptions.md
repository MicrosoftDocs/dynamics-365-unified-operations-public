---
title: Add AI descriptions for the Dynamics 365 ERP MCP server
description: Learn how to add AI descriptions in X++ to data entities, entity fields, and forms so that agents that use the Dynamics 365 ERP MCP server get the business context they need.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 10/26/2026
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Add AI descriptions for the Dynamics 365 ERP MCP server

[!INCLUDE [banner](../../includes/banner.md)]

AI descriptions are short, plain-language text that tell AI agents what a data entity, its fields, or a form is used for. The Dynamics 365 ERP MCP server adds this text to its tool responses, so agents get business context alongside the structural metadata that the server already returns.

When an agent works with finance and operations apps through the [Dynamics 365 ERP MCP server](../copilot-mcp.md), the tools return metadata about data entities and forms, such as field names, field types, and labels. This metadata tells the agent what an object is, but it doesn't always tell the agent how to use it for a task. For example, an agent that's asked to retrieve all journals for a production order might find one journal entity and stop, without knowing that the journals are split across several entities by journal type. An AI description on those entities can tell the agent how they relate, so the agent finds all the records it needs.

Use AI descriptions to:

- Explain what a data entity or form is used for and when an agent should use it.
- Describe how a data entity relates to other data entities.
- Explain what field values mean.
- Identify fields that an agent shouldn't set, such as values that the system assigns or calculates.

AI descriptions add context only. They don't change which tools, data entities, forms, or fields are available to an agent, and they don't change the agent's security permissions.

## How AI descriptions work

You add an AI description by writing a provider method in X++. A provider method is a static method that has the `McpAiDescriptionProviderAttribute` attribute. Add it to the data entity itself, or to a class extension of the data entity or form that you want to describe.

At runtime, the MCP server finds the provider methods on the target data entity or form and on its class extensions. It runs the providers and adds the combined text to the tool response. You don't need to register providers or maintain a separate list of descriptions. The description is stored with the element that it describes.

An AI description has two parts, and both are optional:

- A **top-level description** of the data entity or form as a whole.
- **Field descriptions** for individual data entity fields.

The following table shows where agents see each type of description.

| What you describe | MCP tool | Where the description appears in the response |
|---|---|---|
| Data entity | `data_get_entity_metadata` | Top-level `AiDescription` property |
| Data entity field | `data_get_entity_metadata` | `Fields.<FieldName>.AiDescription` |
| Form | `form_open_menu_item` | `Context.FormAiDescription` |

### AI descriptions compared with agent instructions

AI descriptions and agent instructions both give an agent more context, but they serve different purposes.

| | AI descriptions | Agent instructions |
|---|---|---|
| **What they describe** | Facts about data entities, fields, and forms, and how they relate to each other. | Business processes, policies, and the steps that an agent follows for a scenario. |
| **Where they apply** | Every agent that uses the Dynamics 365 ERP MCP server in your environment and has access to the data entity or form. | Only the agent that you configure them for. |
| **Who typically writes them** | A developer who understands the data entity structure and relationships. | An agent maker or business user who defines the scenario. |

## Prerequisites

Before you add AI descriptions, ensure that you meet the following prerequisites:

- Your environment meets the [prerequisites for the Dynamics 365 ERP MCP server](../copilot-mcp.md#prerequisites).
- You have a development environment where you can build and deploy X++ code, such as a unified developer environment.

### Step 1: Write a provider method

A provider method must meet all of the following requirements:

- It's declared as `public static void`.
- It takes exactly one parameter of type `McpIAiDescriptionBuilder`. Use this interface, not the `McpAiDescriptionBuilder` class.
- It has the `[McpAiDescriptionProviderAttribute]` attribute.
- It's defined on the data entity itself, or in a class extension (`[ExtensionOf(...)]`) of the data entity or form that you're describing.

> [!IMPORTANT]
> If a method doesn't meet all of these requirements, the MCP server skips it without an error. If a description doesn't appear in the tool response, check the method signature and the attribute first.

The method name doesn't matter. The MCP server finds providers by their attribute and signature, so choose a name that describes what the provider adds.

In the provider method, call the following methods on the builder to add text.

| Method | Description |
|---|---|
| `appendDescription(str)` | Adds text to the top-level description of the data entity or form. |
| `appendFieldDescription(str fieldName, str)` | Adds text to the description of one data entity field. Use this method only for data entities. |

Both methods add text. If a description already has text, the new text is added on a new line. The builder doesn't provide a way to replace or remove text that another provider adds.

Choose the option that matches what you're describing:

- [Option A: Describe a data entity that you own](#option-a-describe-a-data-entity-that-you-own)
- [Option B: Describe a data entity that you don't own](#option-b-describe-a-data-entity-that-you-dont-own)
- [Option C: Describe a form](#option-c-describe-a-form)

### Option A: Describe a data entity that you own

Add the provider method to the **Methods** node of the data entity.

The following example describes a custom data entity, `ContosoRentalAgreementEntity`, that stores equipment rental agreements. The top-level description tells the agent where to find the related lines. The field descriptions explain what the values mean and which fields the agent shouldn't set.

```xpp
[McpAiDescriptionProviderAttribute]
public static void describe(McpIAiDescriptionBuilder _builder)
{
    _builder.appendDescription(
        'Equipment rental agreements with customers. One record per agreement. ' +
        'The rented items are in the ContosoRentalAgreementLines entity. ' +
        'To find the items on an agreement, filter that entity by AgreementId.');

    _builder.appendFieldDescription(fieldStr(ContosoRentalAgreementEntity, AgreementId),
        'Unique agreement number. Assigned from a number sequence when the agreement is created. ' +
        'Leave this field empty when you create a record.');

    _builder.appendFieldDescription(fieldStr(ContosoRentalAgreementEntity, Status),
        'Lifecycle stage of the agreement. Draft agreements can be edited. ' +
        'Active means that the equipment is with the customer. Returned and Closed agreements are read-only. ' +
        'The system sets this value. Do not update it directly.');

    _builder.appendFieldDescription(fieldStr(ContosoRentalAgreementEntity, PlannedReturnDate),
        'Date that the customer is expected to return the equipment. ' +
        'An Active agreement with a PlannedReturnDate in the past is overdue.');
}
```

> [!TIP]
> Use `fieldStr()` to specify field names so that the compiler checks that each field exists on the data entity. Field name matching isn't case-sensitive, but the name must match a field on the data entity.

### Option B: Describe a data entity that you don't own

To add context to a data entity in another model, such as a data entity that Microsoft provides, create a class extension of the data entity and add the provider method to the extension class. Use `dataEntityViewStr()` in the `ExtensionOf` attribute. For more information about class extensions, see [Class extension model in X++](../../extensibility/class-extensions.md).

Your provider doesn't replace the text from the data entity's own provider or from other extensions. The MCP server combines the text from all providers.

The following example extends the `CustCustomerV3Entity` data entity (**Customers V3**) to tell agents where to find a customer's equipment rental agreements.

```xpp
[ExtensionOf(dataEntityViewStr(CustCustomerV3Entity))]
public final class CustCustomerV3Entity_ContosoRental_Extension
{
    [McpAiDescriptionProviderAttribute]
    public static void describeContosoRental(McpIAiDescriptionBuilder _builder)
    {
        _builder.appendDescription(
            'Customers who rent equipment have rental agreements in the ContosoRentalAgreements entity.');

        _builder.appendFieldDescription(fieldStr(CustCustomerV3Entity, CustomerAccount),
            'To find the rental agreements for a customer, filter the ContosoRentalAgreements entity by this value.');
    }
}
```

### Option C: Describe a form

For a form, add the provider method to a class extension of the form. Use `formStr()` in the `ExtensionOf` attribute. Forms support only a top-level description, so use `appendDescription()`.

The following example describes a custom form, `ContosoRentalAgreement`, that users open to review rental agreements and record equipment returns.

```xpp
[ExtensionOf(formStr(ContosoRentalAgreement))]
public final class ContosoRentalAgreementForm_Extension
{
    [McpAiDescriptionProviderAttribute]
    public static void describeForm(McpIAiDescriptionBuilder _builder)
    {
        _builder.appendDescription(
            'Use this form to review rental agreements and record equipment returns. ' +
            'To record a return, select the agreement in the grid, and then select Return equipment on the Action Pane.');
    }
}
```

The MCP server looks up the description by form name, not by menu item name. Any menu item that opens the `ContosoRentalAgreement` form returns this description.

## Step 2: Verify the AI descriptions

1. Ensure that AI descriptions are enabled in your environment, as described in [Prerequisites](#prerequisites).
1. Build your model and deploy it to your environment.
1. From an MCP client that's connected to your environment, call the tool that returns the description:

    - **Data entity:** Call `data_get_entity_metadata` with the entity set name, which is the data entity's public collection name. Check the top-level `AiDescription` property and the `AiDescription` property of each field that you described.
    - **Form:** Call `form_open_menu_item` with a menu item that opens the form. Check the `Context.FormAiDescription` property.

The following abbreviated example shows the AI descriptions from [Option A](#option-a-describe-a-data-entity-that-you-own) in the `data_get_entity_metadata` response for the `ContosoRentalAgreements` entity set. Other properties in the response are omitted.

```json
{
  "AiDescription": "Equipment rental agreements with customers. One record per agreement. The rented items are in the ContosoRentalAgreementLines entity. To find the items on an agreement, filter that entity by AgreementId.",
  "Fields": {
    "Status": {
      "AiDescription": "Lifecycle stage of the agreement. Draft agreements can be edited. Active means that the equipment is with the customer. Returned and Closed agreements are read-only. The system sets this value. Do not update it directly."
    },
    "PlannedReturnDate": {
      "AiDescription": "Date that the customer is expected to return the equipment. An Active agreement with a PlannedReturnDate in the past is overdue."
    }
  }
}
```

The following abbreviated example shows the AI description from [Option C](#option-c-describe-a-form) in the `form_open_menu_item` response for a menu item that opens the `ContosoRentalAgreement` form.

```json
{
  "Context": {
    "FormAiDescription": "Use this form to review rental agreements and record equipment returns. To record a return, select the agreement in the grid, and then select Return equipment on the Action Pane."
  }
}
```

If a description doesn't appear, see [Troubleshoot AI descriptions](#troubleshoot-ai-descriptions).

## How the MCP server combines and limits descriptions

### Multiple providers

A data entity or form, and each of its class extensions, can have one or more provider methods. The MCP server runs all of them and joins their text with new lines. For example, if the data entity's own provider and providers in two extension models each add a top-level description, the agent receives the text from all three providers, each on its own line.

The order in which providers run isn't guaranteed. Write each description so that it makes sense on its own, regardless of the text that other providers add before or after it.

### Inheritance

The MCP server uses only the providers on the target data entity or form and on its own class extensions. It doesn't use providers on a parent class or on extensions of a parent class.

### Error handling

Failures are isolated. If a provider throws an exception, the MCP server logs the error and still returns the text from the other providers. The tool call doesn't fail.

### Length limits

After the MCP server combines the text from all providers, it truncates any text beyond the following default lengths. The text is truncated without a warning and without an ellipsis (...) at the end.

| Description | Maximum length |
|---|---|
| Top-level description | 1,500 characters |
| Each field description | 500 characters |

Because the limits apply to the combined text, text from one provider can be cut off if other providers already use most of the available length. Keep descriptions short, and put the most important information first.

### Security

A field description appears only for fields that the calling user has permission to read. As with all responses from the Dynamics 365 ERP MCP server, the security roles of the agent's authenticated user determine what the agent can access. For more information, see [Dynamic context](../copilot-mcp.md#dynamic-context).

AI descriptions are returned to any agent that has access to the data entity or form. Don't include confidential, personal, or customer-specific data in AI descriptions.

## Best practices for writing AI descriptions

Write AI descriptions for an AI reader. The metadata response always includes each field's type, and it includes the field's label whenever one is available, so don't repeat that information. Instead, explain what the record is used for, when to use it, and what the values mean.

- **Describe relationships.** Tell the agent which other data entities hold related records, and which field to use to find them.
- **Explain values.** Describe what each value of a status or type field means for the record.
- **Call out fields that agents shouldn't set.** Identify values that the system assigns or calculates.
- **Be concise.** Stay well within the length limits, and lead with the most important information.
- **Make each description stand alone.** Don't assume that text from another provider appears before or after yours.
- **Describe the data, not the process.** Use AI descriptions for facts about a data entity, its fields, or a form. Use agent instructions for business processes, policies, and approvals.

The following table shows examples of how to make a description more useful to an agent.

| Instead of | Write |
|---|---|
| `'Rental agreements.'` | `'Equipment rental agreements with customers. One record per agreement. The rented items are in the ContosoRentalAgreementLines entity.'` |
| `'Status of the agreement.'` | `'Lifecycle stage of the agreement. Draft agreements can be edited. Returned and Closed agreements are read-only. The system sets this value.'` |
| `'Planned return date.'` | `'Date that the customer is expected to return the equipment. An Active agreement with a PlannedReturnDate in the past is overdue.'` |

## Troubleshoot AI descriptions

| Issue | What to check |
|---|---|
| No AI description appears in the tool response. | Make sure that AI descriptions are enabled and that you built and deployed your model. Check that the provider method is `public static void`, takes exactly one `McpIAiDescriptionBuilder` parameter, and has the `[McpAiDescriptionProviderAttribute]` attribute. The MCP server skips methods that don't meet these requirements without an error. |
| A provider on a parent class isn't used. | Move the provider to the data entity or form itself, or to a class extension of that data entity or form. The MCP server doesn't use providers on parent classes or their extensions. |
| A field description is missing. | Check that the field name matches a field on the data entity, and use `fieldStr()` so that the compiler checks the name. Also check that the agent's authenticated user has permission to read the field. |
| A form description doesn't appear. | Make sure that the provider is in a class extension of the form that uses `formStr()`. Then call `form_open_menu_item` with a menu item that opens that form. |
| Text from one provider is missing. | The provider might have thrown an exception, or the combined text might exceed the length limit. The MCP server skips a provider that fails and returns the text from the other providers. |
| A description is cut off. | The combined text from all providers is longer than the length limit. Shorten the descriptions. |
