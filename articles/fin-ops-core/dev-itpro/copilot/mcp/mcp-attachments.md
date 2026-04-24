---
title: File with Dynamics 365 ERP MCP
description: Guidance for working with files and attachments to Dynamics 365 ERP records with the Dynamics 365 ERP MCP server
author: jaredha
ms.author: jaredha
ms.reviewer: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 4/28/2026

---

# Files with Dynamics 365 ERP MCP
File support in the Dynamics 365 ERP MCP server enables powerful process automation and agentic experiences for document-centric business processes in Dynamics 365 finance and operations apps. The MCP server lets an AI agent exchange files with application in two directions: it can return large query results, exported reports, and existing attachments as embedded resources to the language model client, and it can accept file content from the client and attach it to a record in the application.

The MCP server supports two categories of file and attachment operations:

- **Output scenarios** — the server returns file content or large result sets to the LLM client as an MCP embedded resource.
- **Input scenarios** — the server accepts file content from the client and attaches it to an F&O business record through Dataverse custom APIs.

Together, these operations let an agent read reports, download exported files, and programmatically attach documents to F&O records without manual user interaction.

This article describes the supported scenarios, the tools and APIs that back them, the size and timeout limits that apply, and the validation performed on each request.

## Output scenarios
Output scenarios occur when the MCP server sends binary or large-text content back to the LLM as an MCP embedded resource. There are three triggers: data query tools, the action execution tool, and form interaction tools.

### SQL and OData data query tools
Both `data_find_entities_sql` and `data_find_entities` accept an optional Boolean parameter, `returnAsResource`. When set to `true`, the query result JSON is returned as an MCP embedded resource instead of inline text, which raises the allowed response size from roughly 160 KB to 5 MB, enabling agents to work with greater response sizes.

The MCP response with the file resource comes in the following shape:

| Content block |	Type	| Description |
| ------------- | ----- | ----------- |
| `Content[0]` |	 `text` |	Summary text — record count and any warnings. |
| `Content[1]` |	`resource`	| EmbeddedResource { Uri, MimeType, Text } containing the result JSON.

#### Constraints

- Inline responses are capped at 160,000 characters (~160 KB). Exceeding this returns a ResponseTooLarge error.
- Resource responses are limited to 5 MB.
- When a query errors, the response is always returned inline regardless of returnAsResource.

#### Typical flow

1. The agent calls data_find_entities_sql with a SELECT statement and returnAsResource=true.
2. The MCP server executes a query and serializes rows to JSON, formatting it to be readable to the agent.
3. The agent receives a summary text block followed by a resource block containing the full JSON.
4. The agent reads the resource to extract individual records.

For example

### API action tool
The `api_invoke_action` tool also accepts `returnAsResource`. When set to `true`, the action response is returned as an embedded resource, mirroring the query-tool pattern and raising the allowed response size to 5 MB.

The same size limits, flight gate, and error-handling rules apply as for the query tools. If the inline limit is exceeded, the error's fix field suggests setting returnAsResource=true.

### Form tools with output menu items
When using form tools in the MCP server, the agent has the ability to click a button that prints a report as an output menu item. The MCP server can run these actions, receiving the output file, appending it to the tool response as an embedded resource alongside the updated form state.

The MCP response is in the following shape:

| Content block |	Type | Description |
| ------------- | ----- | ----------- |
| `Content[0]` |	`text`	| Summary, for example "Button ExportToExcel was clicked. File 'report.xlsx' was downloaded." |
| `Content[1]` |	`text` |	Full form state JSON (McpToolInvocationResponseBody). |
| `Content[2..N]` |	`resource` |	One EmbeddedResource per downloaded file, with URI `file://{fileName}`. Binary files are returned as base64 `Blob`; text files are returned as UTF-8 `Text`. |

For example, an agent can run the Vendor Aging Report with a prompt like "Run the Vendor Aging Report, aging as of today's date." The agent then uses form tools to find the form and run the report, creating a PDF file. The MCP tool response then includes a file reference for the document, similar to the below response. The agent then summarizes the results of the file, and includes a link to download the PDF file.

```json
[
  {
    "text": "Button __TimerForAsyncTaskPolling was clicked. File 'VendorAgingReport_04242026.pdf' was downloaded.",
    "type": "text"
  },
  {
    "text": "{\"SessionId\":\"6493e93a-a079-41eb-b53f-986fef39286e\",\"Result\":\"Button __TimerForAsyncTaskPolling was clicked.\",\"Messages\":[],\"FormState\":{\"Name\":\"No form is open\",\"Summary\":\"No form is open\",\"Form\":{},\"Buttons\":[],\"Links\":[],\"Guidance\":[\"No form is currently open. To open a new form, use the $form_open_menu_item tool.\"]},\"MCPActivityId\":\"f5de2c35-d182-0004-0051-acf682d1dc01\",\"DeepLinks\":[]}",
    "type": "text"
  },
  {
    "file": {
      "$kind": "FileDataValue",
      "value": {
        "$kind": "ConversationFileReference",
        "value": "5a0c74a9-c4aa-4189-a6e7-8cfa08293ec4"
      }
    }
  }
]
```



## Configure attachments

1. On the **Tools** tab of the agent, select **Add a tool**.
2. In the **Add tool** dialog, select the **Flow** filter, then search for and add the **Add an attachment to a record in ERP** flow.
3. In the **Inputs** section, add the `contentBytes` input:
   - Select the **Add input** action.
   - Select the `contentBytes` input.
   - In the **Fill using** field, select **Custom value**.
   - Click the ellipses button on the **Value** field.
   - In the **Choose a variable** dialog, select the **Formula** tab, and enter the following formula: `First(System.Activity.Attachments).Content`.
   - Select **Insert**.
4. Add the `name` input:
   - Select the **Add input** action.
   - Select the `name` input.
   - In the **Fill using** field, select **Custom value**.
   - Click the ellipses button on the **Value** field.
   - In the **Choose a variable** dialog, select the **Formula** tab, and enter the following formula: `First(System.Activity.Attachments).Name`.
   - Select **Insert**.
5. **Save** the tool.
