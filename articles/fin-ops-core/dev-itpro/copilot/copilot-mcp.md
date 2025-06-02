---
title: Use Model Context Protocol for finance and operations apps
description: Learn how to use a Model Context Protocol (MCP) server to create and extend agents for Microsoft Dynamics 365 finance and operations apps.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 05/18/2024
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
audience: Application User
ms.search.region: Global
ms.search.form:
---

# Use Model Context Protocol for finance and operations apps

[!include [banner](../includes/banner.md)]

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that facilitates the connection of AI agents to various data systems to enhance the relevance of agent responses. MCP standardizes how applications provide context to large language models (LLMs). Because it enables seamless integration between LLM applications and external data sources, the protocol is useful for building AI-powered tools and workflows.

The **Microsoft Dynamics 365 ERP MCP** server is now available. This server exposes tools for Dynamics 365 finance and operations apps to agent platforms that support MCP. Standardization on the common protocol enables the following capabilities:

- Agent access to data and business logic in multiple apps
- Reuse of agents across enterprise resource planning (ERP) systems
- Access to tools in finance and operations apps from any compatible agent platform
- A simplified agent development experience

## Prerequisites

Before you can use the Dynamics 365 ERP MCP server, the following prerequisites must be met:

- The product version of finance and operations apps must be at least **10.0.2263.17**.
- The version of the **Copilot in Microsoft Dynamics 365 Finance** solution must be at least **1.0.3049.1**.
- The version of the **Copilot in Microsoft Dynamics 365 Supply Chain Management** solution must be at least **1.1.03046.2**.

## Use the Dynamics 365 ERP MCP server in Copilot Studio

You can use the Dynamics 365 ERP MCP server to create agents in Microsoft Copilot Studio. The server provides tools for actions in Dynamics 365 Finance and Dynamics 365 Supply Chain Management.

To add the tools to your agent, follow these steps.

1. In [Copilot Studio](https://copilotstudio.microsoft.com), open an existing agent, or create a new one.
1. In the agent, on the **Tools** tab, select **Add a tool**.
1. In the **Add tool** dialog, select the **Model Context Protocol** filter, and search for **Dynamics 365 ERP MCP**.
1. Create a connection to the server.
1. Select **Add to agent**.

After the Dynamics 365 ERP MCP server is added, the agent has access to the tools on it and can use them to perform actions for the related finance and operations apps. To view the list of available tools on the server, open the Dynamics 365 ERP MCP server in the agent.

## MCP tools
Below is the list of MCP tools currently available in the **Microsoft Dynamics 365 ERP MCP** server. This is a static list of tools that isn't currently extensible. A broader list of tools and options for extending the list of tools will be available in coming releases. For each tool, the below details include the following information:
- The **description** of the tool.
- The **Dataverse custom API** that shows the tool schema and makes the call to perform the operation. The custom API can be found in the related Dataverse solution, either **Copilot in Microsoft Dynamics 365 Finance** or **Copilot in Microsoft Dynamics 365 Supply Chain Management**.
- A table outlining the **inputs** for the tool.
- A table defining the **outputs** of the tool.

### FindApprovedVendors
**Description:** Finds vendors that are approved to supply specific items. The request can include item number and vendor account number as filters.
**Custom API:** msdyn_FindApprovedVendors

**Inputs**

| Input | Description | Data type | Required |
| ----- | ----------- | --------- | -------- |
| itemNumber | The item number for which the tool will be identifying approved vendors. Can be blank if the results should not be filtered by item number. | String | No |
| VendorAccountNumber | The vendor account number to identify the items for which the vendor is an approved vendor. Can be blank if the results should not be filtered by vendor account number. | String | No |

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| itemnumber | The item number | String |
| approvedvendoraccountnumber | The vendor account number of the approved vendor for the item | String |
| validfrom | The date and time from which the approval is valid | Datetime |
| validto | The date and time from to which the approval is valid | Datetime |

**Example output**

```json
[ 
  { 
    "itemnumber": "1000", 
    "approvedvendoraccountnumber": "1001", 
    "validfrom": "2012-01-15T00:00:00", 
    "validto": "2154-12-31T00:00:00" 
  }, 
  { 
    "itemnumber": "1000", 
    "approvedvendoraccountnumber": "US-104", 
    "validfrom": "2012-01-15T00:00:00", 
    "validto": "2154-12-31T00:00:00" 
  }, 
  { 
    "itemnumber": "1000", 
    "approvedvendoraccountnumber": "US-101", 
    "validfrom": "2012-01-01T00:00:00", 
    "validto": "2154-12-31T00:00:00" 
  } 
]
```

### FindRequisitions
**Description:** Finds open purchase requisitions, with an option to filter by approval status. Set 'approvedOnly' to true to return only approved requisitions, or false to include all open requisitions regardless of approval.
**Custom API:** msdyn_FindRequisitions

**Inputs**

| Input | Description | Data type | Required |
| ----- | ----------- | --------- | -------- |
| approvedOnly | Controls whether the list should be filtered to approved requisitions | Boolean | No |

**Outputs**
For each purchase requisition there may be zero to many requisition lines returned in the output.

| Output | Description | Data type |
| ------ | ----------- | --------- |
| requisitionnumber | The requisition number | String |
| requisitionname | The requisition name | String |
| requisitionstatus | The current status of the requisition | Choice, with the following value options: <ul><li>200000000: Draft <li>200000001: In review <li>200000002: Rejected <li>200000003: Approved <li>200000004: Cancelled <li>200000005: Closed <li>200000006: Budget reserved </ul> |
| lines/requisitionlinenumber | The requisition line number | Integer |
| lines/itemnumber | The item number for the line | String |
| lines/linedescription | The description of the line | String |
| lines/productname | The line product name | String |
| lines/procurementproductcategoryname | The procurement category for the product | String |
| lines/requestedpurchasequantity | The requested purchase quantity | Decimal |
| lines/purchaseprice | The purchase price per unit | Decimal |
| lines/lineamount | The total amount for the line | Decimal |
| lines/currencycode | The currency code for the line currency values | String |
| lines/requesteddate | The requested date for the line item | Datetime |

**Example output**
```json
[ 
  { 
    "requisitionnumber": "000031", 
    "requisitionname": "test", 
    "requisitionstatus": { 
      "Value": 200000000 
    }, 
    "lines": [ 
      { 
        "requisitionlinenumber": 1, 
        "itemnumber": "", 
        "linedescription": "OFFICE EQUIPMENT AND ACCESSORIES AND SUPPLIES\nOFFICE EQUIPMENT AND ACCESSORIES AND SUPPLIES", 
        "productname": "1000", 
        "procurementproductcategoryname": "CORP PROCUREMENT CATEGORIES", 
        "requestedpurchasequantity": 0.0, 
        "purchaseprice": 100.0, 
        "lineamount": 0.0, 
        "currencycode": "USD", 
        "requesteddate": "2025-04-23T00:00:00" 
      } 
    ] 
  } 
] 
```

### ReleasePurchaseRequisitionLines  
**Description:** Releases the specified purchase requisition lines and creates purchase orders for them. A default vendor account number can be provided for lines that do not have a vendor assigned. 
**Custom API:** msdyn_ReleasePurchaseRequisitionLines

**Inputs**

| Input | Description | Data type | Required |
| ----- | ----------- | --------- | -------- |
| defaultVendorAccountNumber | The account number for the vendor to use. Leave blank if only the vendor specified in the requisition must be used. | String | No | 
| linesToRelease | Lines to release. Must be a JSON array in the format the following format: <br>`[{"requisitionnumber":"number", <br>"requisitionlinenumber":linenumber}]` | Yes |

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| result | The result of the operation to release the lines | String |

**Example output**
```json
[
  {
    "result":"OK"
  }
] 
```

