---
title: Deep links for Dynamics 365 ERP MCP
description: Learn about generating and using deep link URLs through the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: twheeloc
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/09/2026

---

# Deep links for Dynamics 365 ERP MCP

[!INCLUDE [banner](../../../../includes/banner.md)]

The Dynamics 365 ERP MCP server's deep links capability enables responses generated from Microsoft Copilot and agent experiences to include direct navigation links to the corresponding records in Dynamics 365 finance and operations apps. When an MCP request retrieves or modifies record data, the MCP response includes a deep link URL that opens the application context used to generate that response. This capability allows users to seamlessly transition from conversational or agent-driven interactions into the relevant transactional or master data forms within the Dynamics 365 ERP client.

A deep link doesn't grant access to anything. When a user opens a deep link, the app checks the user's own security roles before it shows any page or data.

## Prerequisites

To include deep links in your MCP responses, ensure the **Deep links for Model Context Protocol** feature in **Feature management** is enabled. It's enabled by default. When you disable the feature, the MCP server stops including deep links in tool responses. Links that were already returned still open, subject to the same security checks.

## How tools return deep links

Tools that support deep links return them in a `DeepLinks` array. Each item has a `Url` and a `Label`.

| Tool type | Location of the array in the tool result |
| --- | --- |
| Data tools | `Result.DeepLinks` |
| Form tools | `DeepLinks` (top level) |

```json
{
  "Result": {
    "Value": [ { "CustomerAccount": "US-001", "CustomerGroupId": "30" } ],
    "DeepLinks": [
      {
        "Url": "https://contoso.operations.dynamics.com/?mi=action:McpDeepLinkNavigator&nav=CustCustomerV3Entity&nt=entity&filters=[...]&cmp=USMF",
        "Label": "Open CustomersV3"
      }
    ]
  }
}
```

The label describes the target, for example `Open CustomersV3`, `Open US-001` (a link to one record), `View CustomersV3` (after a create or update), or `Open <page name>` (from form tools).

### Tools that return deep links

| Tool | Deep links returned |
| --- | --- |
| `data_find_entities_sql` | One link to the query results, one link per returned record, or no link. For details, see [SQL query tool](#sql-query-tool). |
| `data_find_entities` | One link to the matching list. |
| `data_create_entities`, `data_update_entities` | One link for each created or updated record. |
| `form_open_menu_item`, `form_click_control`, `form_filter_form`, `form_filter_grid`, `form_select_grid_row`, `form_sort_grid_column`, `form_open_or_close_tab`, `form_open_lookup`, `form_save_form`, `form_close_form` | One link to the page that's open after the action, scoped to the current filter or record when possible. |
| `data_delete_entities`, `data_get_entity_metadata`, `data_find_entity_type`, `data_list_attachments`, `form_find_controls`, `form_find_menu_item`, `form_set_control_values`, `api_find_actions`, `api_invoke_action` | None. |

### Show deep links to users

Tool definitions include response semantics metadata (`_meta["microsoft/response_semantics"]`) that points to the `DeepLinks` array. Microsoft 365 Copilot uses this metadata to show the links as clickable citations.

Other clients decide for themselves how to show links and citations. You might need to tell your agent how to format deep links. For example, in an agent in Copilot Studio, you can add instructions similar to the following:

```
# Citation and deep link instructions
- Tool responses may include citations in a `DeepLinks` array in the JSON body. Each deep link has a `Url` and `Label`. Always include these links in your response as clickable markdown links (e.g. [Label](Url)) so the user can navigate directly to the referenced form or record in Dynamics 365.
- Always render DeepLinks URLs exactly as returned by tools — never reconstruct, simplify, or strip query parameters. Use the full URL verbatim in markdown link syntax.
```

## What happens when a user opens a deep link

When a user opens a deep link, the app:

1. Checks that the user has permission to open the target. For details, see [Security](#security).
2. Opens the target page through its own menu item. The page applies its usual setup, such as its default filters.
3. Adds the filters from the link to the page.
4. Counts the matching records and decides what to show.

| Situation | What the user sees |
| --- | --- |
| No records match the filters | The message "The requested record was not found." |
| Exactly one record matches, and the table has a details page | The record's details page. |
| More than one record matches | The list page, filtered to the matching records. |
| The table has no page that the link can open | A read-only grid (the MCP deep link browser) that shows the matching records. |
| A link from a data tool contains a filter that the page can't apply | The read-only grid, which can apply the filter. |
| A link from a form tool contains a filter that the page can't apply | The page, unfiltered, with the message "One or more filters could not be applied." |
| A cross-company link matches records in one company | The page, opened in that company. |
| A cross-company link matches records in several companies | The page in cross-company mode if the page supports it. Otherwise, the read-only grid with a **Company** column. |
| The user lacks permission | The message "You do not have permission to open this form. Contact your system administrator to request access." |

The read-only grid shows up to 15 columns: the record's key fields, the company for cross-company links, the filtered fields, and then other fields. Values that refer to other records are links that open those records. The grid doesn't support editing.

### Examples

| Prompt | MCP request | Deep link in the response | What opens |
| --- | --- | --- | --- |
| In which customer group is customer account US-001? | `data_find_entities_sql` queries the `CustomersV3` entity for that customer account. | One link, filtered to customer account US-001. | The customer's details page. |
| Show me all customers whose name begins with "Contoso". | `data_find_entities_sql` queries `CustomersV3` with a `LIKE 'Contoso%'` condition on the name. | One link, filtered to names that begin with "Contoso". | The customer list, filtered to those customers. |
| Which customers in group 30 have open sales orders? | `data_find_entities_sql` joins `CustomersV3` and a sales order entity. | One link per returned customer, because the join condition can't be expressed as a filter on the customer list. | Each link opens one customer. |
| Confirm sales order 000811. | Form tools open the sales order and select **Confirm**. | One link to the sales order page, scoped to order 000811. | Sales order 000811. |

## How each tool type builds deep links

### SQL query tool

`data_find_entities_sql` turns the conditions in the query's `WHERE` clause into deep link filters:

| SQL condition | Deep link filter |
| --- | --- |
| `=`, `<>`, `>`, `>=`, `<`, `<=` | `Is`, `IsNot`, `GreaterThan`, `GreaterThanOrEqual`, `LessThan`, `LessThanOrEqual` |
| `IN (...)`, or `OR` between equality conditions on the same field | `IsOneOf` |
| `BETWEEN` | `Between` |
| `LIKE '%text%'`, `LIKE 'text%'`, `LIKE '%text'` | `Contains`, `BeginsWith`, `EndsWith` |
| `NOT LIKE '%text%'` | `DoesNotContain` |
| `LIKE` with wildcards inside the text, such as `'%Contoso%Europe%'` | `Matches`, with `%` converted to `*` and `_` converted to `?` |
| Conditions on `dataAreaId` | Not used. The company comes from the tool's `companyId` parameter. |

The tool then chooses which links to return:

- **All conditions can be expressed as filters:** one link to the list, with those filters.
- **No `WHERE` clause:** one link to the list, without filters.
- **Some conditions can't be expressed as filters:** one link per returned record. This case includes inner joins and `EXISTS` conditions on another entity, `OR` between different fields, and functions or other unsupported expressions. Per-record links need the entity's key fields in the result. If the key fields are missing, the tool returns no link and adds a note to the response that explains why. It never returns a link that would show more records than the query matched. Left (outer) joins don't prevent a single link.
- **Aggregation query** (`GROUP BY`, `SUM`, `COUNT`, and so on): no link.

> [!TIP]
> To get per-record links for queries that use joins, include the entity's key fields (for example, `CustomerAccount`) in the `SELECT` list.

### OData tools

- **`data_find_entities`:** the link uses the equality conditions (`Field eq 'value'`) in `$filter`. The company comes from a `dataAreaId eq '<company>'` condition, or else the current company.
- **`data_create_entities` and `data_update_entities`:** the link uses the key of each created or updated record, and opens that record.

Entity field names are translated to the fields of the underlying tables, including fields from joined data sources. For example, `OrganizationName` on the `CustomersV3` entity becomes the `Name` field of the related party record.

### Form tools

Form tools return a link to the page that's open after the action. The link uses, in order of preference:

1. The record that the action created or updated on the page.
2. The filters that form tools applied to the page, or the record that's selected.
3. For a page opened from another page, the parent record. When the page can only be opened from its parent record, the link includes the parent page (`parentNav`) so the app can supply that record. If there's no usable parent record, the link opens the parent page instead.

## Security

Deep links use the same security as the rest of the app:

- **Links from data tools** require read permission for the data entity, as granted to OData and other data services. If a user's roles grant access to the entity's pages but not to the entity itself, the app opens the entity's list page or details page instead, if the user can open it. When the table has a list page or details page, the user must also be allowed to open that page.
- **Links from form tools** require permission to open the page's menu item.
- **Detail pages** open only if the user is allowed to open them. Otherwise, the user stays on the filtered list.
- **Field-level security:** filters on fields that the user isn't allowed to view are ignored, and the message "One or more filters could not be applied." appears.
- **Record-level security** (extensible data security policies) and company access apply to every page and grid that a deep link opens.

The message for a missing page or entity is the same as the message for a page the user can't open, so a deep link doesn't reveal what exists in the environment.

All users can open deep links through the **System user** role, which includes the **Navigate MCP deep links** duty (`McpDeepLinkNavigatorView`). The duty only lets users start navigation. It doesn't grant access to any page or data.

## Deep link URL format

Deep link URLs use the following format. The example shows the URL decoded for readability. In tool responses, parts of the URL are percent-encoded.

```
https://<environment>/?mi=action:McpDeepLinkNavigator&nav=<target>&nt=<entity|mi>&filters=<filters>&cmp=<company>
```

| Parameter | Description |
| --- | --- |
| `nav` | The target: a data entity name (for example, `CustCustomerV3Entity`) or a display menu item name (for example, `CustTableListPage`). |
| `nt` | The target type: `entity` for data entities, or `mi` for display menu items. |
| `filters` | Optional. A JSON array of filters. See [Filters](#filters). |
| `cmp` | Optional. The company to open the link in. If the link has neither `cmp` nor `crossCompany`, it opens in the user's default company. |
| `crossCompany` | Optional. `true` to show matching records from all companies. Tools that ran in cross-company mode use this parameter instead of `cmp`. |
| `parentNav` | Optional. The display menu item of a parent page, for pages that can only be opened from a parent record. |

For example, the following URL opens customer US-001 in the USMF company:

```
https://contoso.operations.dynamics.com/?mi=action:McpDeepLinkNavigator&nav=CustCustomerV3Entity&nt=entity&filters=[{"f":"AccountNum","op":"Is","v":"US-001"}]&cmp=USMF
```

The following URL opens the list of all customers in the USMF company:

```
https://contoso.operations.dynamics.com/?mi=action:McpDeepLinkNavigator&nav=CustTableListPage&nt=mi&cmp=USMF
```

### Filters

Each filter is an object with these keys:

| Key | Description |
| --- | --- |
| `f` | The field name. |
| `op` | The operator. |
| `v` | The value. For `IsOneOf`, separate values with commas. |
| `ds` | Optional. The data source that contains the field, when the field isn't on the main table. For example, `"ds":"DirPartyTable"` for a customer's name. |

When a link has several filters on different fields, a record must match all of them.

Deep links support these operators: `Is`, `IsNot`, `Contains`, `DoesNotContain`, `BeginsWith`, `EndsWith`, `IsOneOf`, `Between`, `GreaterThan`, `GreaterThanOrEqual`, `LessThan`, `LessThanOrEqual`, and `Matches`. With `Matches`, the value uses the app's filter syntax, including the `*` and `?` wildcards.

## Known limitations

- Aggregation queries (`GROUP BY`, `SUM`, `COUNT`, and so on) don't return deep links.
- SQL queries with conditions that can't be expressed as filters return one link per record, or no link if the result doesn't include the entity's key fields. For details, see [SQL query tool](#sql-query-tool).
- For `data_find_entities`, only equality conditions (`Field eq 'value'`) in `$filter` are included in the link. If the query uses other conditions, the linked list can include more records than the response.
- Form tool links include only the first value of a filter that has several values.
- If a link's filter data is longer than 4,096 characters, the filters are ignored and the page opens without them. Very long URLs can also exceed browser or server URL length limits.
- Deep links aren't generated for aggregate data entities (`AxAggregateDataEntity`), because they can't be resolved to a table.
- Delete operations and the API action tools (`api_find_actions`, `api_invoke_action`) don't return deep links.
- The read-only grid shows up to 15 columns and doesn't support editing. A row in the grid can't be opened in a details page, but values that refer to other records open those records.
