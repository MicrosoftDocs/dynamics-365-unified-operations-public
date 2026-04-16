---
title: Deep links for Dynamics 365 ERP MCP
description: A desciption for genaration and use of deep link URLs through the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 4/28/2026

---

# Deep links for Dynamics 365 ERP MCP (Preview)
The deep links capability in the Dynamics 365 ERP MCP server enables responses generated from Microsoft Copilot and agent experiences to include direct navigation links to the corresponding records in Dynamics 365 finance and operations apps. When an MCP request retrieves or modifies record data, the MCP response includes a deep link URL that opens the application context used to generate that response. This allows users to seamlessly transition from conversational or agent-driven interactions into the relevant transactional or master data forms within the Dynamics 365 ERP client.

## Deep link navigation
The deep link URL is returned as a parameter in the response to requests to the MCP server. The agent can then format the URL to include it in the agent response to the user.

The target for the deep link navigation is dependent on the number of records retrieved in the response. If a single record is returned in the response, then the deep link will target the details form for that single record. A prompt that returns multiple records in the response will include a single deep link to a list page in the client, filtered to the records returned in the response. Consider the following examples:

| Prompt | MCP request | Response | 
| ------ | ----------- | -------- |
| In which customer group is customer account US-001? | The MCP server uses the `data_find_entities_sql` tool to query the CustomersV3 entity for the given customer. | The MCP response includes: <ul><li>The customer group for the customer.</li><li>A deep link URL to the `CustTable` details form for the customer</li></ul> |
| Show me all customers whose name begins with "Contoso". | The MCP server uses the `data_find_entities_sql` tool to query the CustomersV3 entity to find all customers where the name is like 'Contoso%'. | The MCP response includes: <ul><li>The list of all customers whose name starts with "Contoso".</li><li>A deep link URL to the `CustTable` list page, with a filter applied to the Name column for only values that begin with "Contoso".</li></ul> |
| Confirm sales order 000811. | The MCP server uses form tools to open select the "Confirm now" action on the `SalesTableDetails` form for order number 000811. | The MCP response includes: <ul><li>Detail about the confirmed sales order.</li><li>A deep link URL to the `SalesTable` list page, with a filter applied limiting the list to the single record for order number 000811.</li></ul>

The MCP deep link feature returns the deep link URL in the MCP response, but this doesn't necessarily mean that the agent orchestrator will automatically format and display the deep link to the user in the agent response. Each agent client may have different formats and surfaces for displaying deep links and citations. You may need to add guidance in your agent instructions on how to format and display the deep link in the agent response. For example, in an agent in Copilot Studio, you an add instructions similar to the following:

```
# Citation And Deep Links Instructions
- Tool responses may include citations in a `DeepLinks` array in the JSON body. Each deep link has a `Url` and `Label`. Always include these links in your response as clickable markdown links (e.g. `🔗 Label`) so the user can navigate directly to the referenced form or record in D365.
- Always render DeepLinks URLs exactly as returned by tools — never reconstruct, simplify, or strip query parameters (including encoded q= parameters). Use the full URL verbatim in markdown link syntax.
```

## Deep link generation
When a deep link is invoked, the system evaluates the query filters and determines the navigation behavior based on the number of matching records, and whether there is a formRef.

| Result count | Navigation behavior |
| ------------ | ------------------- |
| 0 records | Displays a modal error dialog |
| 1 result with formRef | Opens the record's detail form directly. |
| Multiple results, or no formRef | Opens the `McpDeepLinkBrowser` grid view to display the list of records. This is a dynamically-generated grid view. Data sources and columns are created at runtime and supported columns may include joined table fields. Column order is defined as: <ol><li>Primary key fields</li><li>Company (dataAreaId) for cross-company queries</li><li>Filtered fields</li><li>Remaining available fields</li></ol> |

When the navigation results in multiple matching records, the `McpDeepLinkBrowser` provides a dynamically generated grid view. 

The MCP has multiple sets of tools for completing MCP operations. Because of the differences in technologies among the tool sets, the deep link URL is generated differently depending on the MCP tool used to fulfill the request. This also results in slightly different behavior for the deep link navigation, noted in the examples in the previous section.

**For SQL-based MCP tools**, filters are extracted from the WHERE clause of the tool query. A three-tier link generation strategy is then applied:
1. A complete set of filtered records is derived from the query.
2. If the filters cannot be fully resolved against the available filters on the list page, the response falls back to a per-record deep link. For example, for queries tat have complex joins or subqueries, the filters may not fully resolve.
3. If record-level filtering is not possible, the deep link URL targets the relevant list page without filters. The user can then manually filter the form to find the relevant record.

**For OData-based MCP tools:**
- After create or update operations, deep links are generated using entity key fields.
- Entity-to-table field resolution is supported, including fields from joined data sources. For example `OrganizationName` on the entity resolves to `DirPartyTable.Name` on the data source of the related form.

**For form-based MCP tools:**
- The active form's primary table and tracked filter expressions are captured.
- If the main form does not contain usable filters, the system attempt to use filters from subform data sources.

### Deep link URL format
Deep links generated by MCP tools use the following format:

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

Optionally, the `crossCompany=true` parameter may be added to the URL to display data from across all companies.

## Known limitations
- Deep links are not generated for aggregate data entities (AxAggregateDataEntity) because they cannot be resolved to base tables.
- Complex SQL queries that include joins, subqueries, conditional logic, or arithmetic expressions in the WHERE clause mail fall back to per-record deep links.
- SQL aggregation queries (for example, GROUP BY, SUM, or COUNT) do not generate deep links.
- The McpDeepLinkBrowser currently provides view-only navigation and does not support click-through to detail forms.
- The PurchaseRequisitionNumber field on PurchReqTable cannot currently be resolved through the entity resolver.
- Large filter sets may exceed browser URL length limits (approximlately 2000 characters).
- No deep links are returned for MCP requests that perform delete operations on data.
- Deep links are not returned by default for the API action tools in the MCP server.
