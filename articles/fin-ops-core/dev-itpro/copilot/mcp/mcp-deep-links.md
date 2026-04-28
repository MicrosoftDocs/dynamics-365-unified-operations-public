---
title: Deep links for Dynamics 365 ERP MCP (preview)
description: Learn about generating and using deep link URLs through the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 4/28/2026

---

# Deep links for Dynamics 365 ERP MCP (preview)

The deep links capability in the Dynamics 365 ERP MCP server enables responses generated from Microsoft Copilot and agent experiences to include direct navigation links to the corresponding records in Dynamics 365 finance and operations apps. When an MCP request retrieves or modifies record data, the MCP response includes a deep link URL that opens the application context used to generate that response. This allows users to seamlessly transition from conversational or agent-driven interactions into the relevant transactional or master data forms within the Dynamics 365 ERP client.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Deep link navigation

The response to requests to the MCP server returns the deep link URL as a parameter. The agent can then format the URL to include it in the agent response to the user.

The target for the deep link navigation depends on the number of records retrieved in the response. If a single record is returned in the response, the deep link targets the details form for that single record. A prompt that returns multiple records in the response includes a single deep link to a list page in the client, filtered to the records returned in the response. Consider the following examples:

| Prompt | MCP request | Response |
| ------ | ----------- | -------- |
| In which customer group is customer account US-001? | The MCP server uses the `data_find_entities_sql` tool to query the CustomersV3 entity for the given customer. | The MCP response includes: <ul><li>The customer group for the customer.</li><li>A deep link URL to the `CustTable` details form for the customer</li></ul> |
| Show me all customers whose name begins with "Contoso". | The MCP server uses the `data_find_entities_sql` tool to query the CustomersV3 entity to find all customers where the name is like 'Contoso%'. | The MCP response includes: <ul><li>The list of all customers whose name starts with "Contoso".</li><li>A deep link URL to the `CustTable` list page, with a filter applied to the **Name** column for only values that begin with "Contoso".</li></ul> |
| Confirm sales order 000811. | The MCP server uses form tools to open select the **Confirm now** action on the `SalesTableDetails` page for order number 000811. | The MCP response includes: <ul><li>Detail about the confirmed sales order.</li><li>A deep link URL to the `SalesTable` list page, with a filter applied limiting the list to the single record for order number 000811.</li></ul>

The MCP deep link feature returns the deep link URL in the MCP response, but this feature doesn't necessarily mean that the agent orchestrator automatically formats and displays the deep link to the user in the agent response. Each agent client might have different formats and surfaces for displaying deep links and citations. You might need to add guidance in your agent instructions on how to format and display the deep link in the agent response. For example, in an agent in Copilot Studio, you can add instructions similar to the following:

```
# Citation and deep link instructions
- Tool responses may include citations in a `DeepLinks` array in the JSON body. Each deep link has a `Url` and `Label`. Always include these links in your response as clickable markdown links (e.g. `Label`) so the user can navigate directly to the referenced form or record in Dynamics 365.
- Always render DeepLinks URLs exactly as returned by tools — never reconstruct, simplify, or strip query parameters (including encoded q= parameters). Use the full URL verbatim in markdown link syntax.
```

## Deep link generation

When you invoke a deep link, the system evaluates the query filters and determines the navigation behavior based on the number of matching records and whether there's a formRef.

| Result count | Navigation behavior |
| ------------ | ------------------- |
| 0 records | Displays a modal error dialog |
| 1 result with formRef | Opens the record's detail form directly. |
| Multiple results, or no formRef | Opens the `McpDeepLinkBrowser` grid view to display the list of records. This view is dynamically generated. Data sources and columns are created at runtime, and supported columns might include joined table fields. The column order is defined as: <ol><li>Primary key fields</li><li>Company (dataAreaId) for cross-company queries</li><li>Filtered fields</li><li>Remaining available fields</li></ol> |

When the navigation results in multiple matching records, the `McpDeepLinkBrowser` provides a dynamically generated grid view.

The MCP has multiple sets of tools for completing MCP operations. Because of the differences in technologies among the tool sets, the deep link URL is generated differently depending on the MCP tool used to fulfill the request. This difference also results in slightly different behavior for the deep link navigation, as noted in the examples in the previous section.

For SQL-based MCP tools, the system extracts filters from the WHERE clause of the tool query. It then applies a three-tier link generation strategy:

1. The system derives a complete set of filtered records from the query.
1. If the system can't fully resolve the filters against the available filters on the list page, it falls back to a per-record deep link. For example, for queries that have complex joins or subqueries, the filters might not be fully resolved.
1. If record-level filtering isn't possible, the deep link URL targets the relevant list page without filters. The user can then manually filter the page to find the relevant record.

For OData-based MCP tools:

- After create or update operations, the system generates deep links by using entity key fields.
- The system supports entity-to-table field resolution, including fields from joined data sources. For example, `OrganizationName` on the entity resolves to `DirPartyTable.Name` on the data source of the related form.

For form-based MCP tools:

- The system captures the active form's primary table and tracked filter expressions.
- If the main form doesn't contain usable filters, the system attempts to use filters from subform data sources.

### Deep link URL format

MCP tools generate deep links that use the following format:

```
https://<Environment base URL>/?mi=ation:McpDeepLinkNavigator&tableName=<TableName>&filters=[{"f":"<FieldName>","op":"<Operator>","v":"<Value>"}]&cmp=<CompanyId>
```

For example, the following deep link URL navigates to a filtered list of customers in the USMF company whose names begin with "Contoso":

```
https://contoso.operations.dynamics.com/?mi=action:McpDeepLinkNavigator&tableName=CustTable&filters=[{"f":"Name","op":"BeginsWith","v":"Contoso","ds":"DirPartyTable"}]&cmp=USMF
```

The filter in the URL is an array that supports multiple filters for the given query. The deep links support the following operators:

- Is
- IsNot
- Contains
- DoesNotContain
- BeginsWith
- GreaterThanOrEqual
- LessThanOrEqual
- IsOneOf
- Matches
- IsEmpty
- IsNotEmpty

Optionally, add the `crossCompany=true` parameter to the URL to display data from across all companies.

## Known limitations

- The system doesn't generate deep links for aggregate data entities (AxAggregateDataEntity) because it can't resolve them to base tables.
- Complex SQL queries that include joins, subqueries, conditional logic, or arithmetic expressions in the WHERE clause fall back to per-record deep links.
- SQL aggregation queries, such as those that use GROUP BY, SUM, or COUNT, don't generate deep links.
- The McpDeepLinkBrowser currently provides view-only navigation and doesn't support click-through to detail forms.
- The entity resolver can't currently resolve the PurchaseRequisitionNumber field on PurchReqTable.
- Large filter sets might exceed browser URL length limits, which is approximately 2,000 characters.
- MCP requests that perform delete operations on data don't return deep links.
- By default, the MCP server doesn't return deep links for the API action tools.
