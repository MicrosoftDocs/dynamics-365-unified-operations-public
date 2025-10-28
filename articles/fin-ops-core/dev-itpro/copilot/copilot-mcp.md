---
title: Use Model Context Protocol for finance and operations apps
description: Learn how to use a Model Context Protocol (MCP) server to create and extend agents for Microsoft Dynamics 365 finance and operations apps.
author: jaredha
ms.author: jaredha
ms.topic: how-to
ms.date: 06/03/2025
ms.update-cycle: 180-days
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.collection:
  - bap-ai-copilot
ms.search.region: Global
---

# Use Model Context Protocol for finance and operations apps (preview)

[!include [banner](../includes/banner.md)]

The [Model Context Protocol (MCP)](https://www.anthropic.com/news/model-context-protocol) is an open standard that facilitates the connection of AI agents to various data systems to enhance the relevance of agent responses. MCP standardizes how applications provide context to large language models (LLMs). Because it enables seamless integration between LLM applications and external data sources, the protocol is useful for building AI-powered tools and workflows. MCP defines a common language for how agents and applications interact with enterprise data and business logic. Instead of relying on custom APIs or pont-to-point integrations, MCP provides a unified framework that standardizes access to ERP operations, ensuring consistency, context, and control. Standardization on the common protocol enables:

- Agent access to data and business logic in multiple apps
- Reuse of agents across enterprise resource planning (ERP) systems
- Access to tools in finance and operations apps from any compatible agent platform
- A simplified agent development experience
- Consistent data access, permissions, and auditability across all agent integrations

## Prerequisites

Before you can use the Dynamics 365 ERP MCP (Preview) server, the following prerequisites must be met:

- The product version of finance and operations apps must be at least **10.0.2428.15**.
- The **(Preview) Dynamics 365 ERP Model Context Protocol server** feature must be enabled in [Feature Management](../../fin-ops/get-started/feature-management/feature-management-overview.md)

> [!NOTE] An earlier version of the MCP server, known as the "static Dynamics 365 ERP MCP" server, is also available in public preview. This server, built on the Dataverse connector framework, has 13 tools enabling specific business functions for Dynamics 365 Finance and Supply Chain Management. This static server will be **retired in the 2026 calendar year**. The server is still available in finance and operations apps environments with version 10.0.2263.17 and greater. However, it is recommended that you use the new dynamic Dynamics 365 ERP MCP server that is the subject of this documentation to avoid disruption when the static server is retired.

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
The following list of MCP tools currently available in the **Microsoft Dynamics 365 ERP MCP** server. This is a static list of tools that isn't currently extensible. For each tool, the details include the following information:
- The **description** of the tool.
- The **Dataverse custom API** that shows the tool schema and makes the call to perform the operation. The custom API can be found in the related Dataverse solution, either **Copilot in Microsoft Dynamics 365 Finance** or **Copilot in Microsoft Dynamics 365 Supply Chain Management**.
- A table outlining the **inputs** for the tool.
- A table defining the **outputs** of the tool.

### **Find Approved Vendors**
- **Name:** `findapprovedvendors`
- **Description:** Finds vendors that are approved to supply specific items. The request can include item number and vendor account number as filters.
- **Custom API:** `msdyn_FindApprovedVendors`

**Inputs**

| Property Name       | Description                                      | Data Type | Required |
|---------------------|--------------------------------------------------|----------|----------|
| `itemNumber`       | Item number. Can be blank if no filter required. | `string` | No       |
| `vendorAccountNumber` | Vendor account number. Can be blank if no filter needed. | `string` | No |

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `itemnumber` | The item number | `string` |
| `approvedvendoraccountnumber` | The vendor account number of the approved vendor for the item | `string` |
| `validfrom` | The date and time from which the approval is valid | `datetime` |
| `validto` | The date and time from to which the approval is valid | `datetime` |

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

### **Find Requisitions**
- **Name:** `findrequisitions`
- **Description:** Finds open purchase requisitions, with an option to filter by approval status.
- **Custom API:** `msdyn_FindRequisitions`

**Inputs**

| Property Name   | Description                                              | Data Type | Required |
|----------------|----------------------------------------------------------|----------|----------|
| `approvedOnly` | Controls whether the list is filtered to approved requisitions. | `boolean` | Yes |

**Example input**
```json
[
  {
    "approvedOnly": false
  }
]
```

**Outputs**
For each purchase requisition there may be zero to many requisition lines returned in the output.

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `requisitionnumber` | The requisition number | `string` |
| `requisitionname` | The requisition name | `string` |
| `requisitionstatus` | The current status of the requisition | Enum, with the following value options: <ul><li>`200000000`: Draft <li>`200000001`: In review <li>`200000002`: Rejected <li>`200000003`: Approved <li>`200000004`: Canceled <li>`200000005`: Closed <li>`200000006`: Budget reserved </ul> |
| `lines/requisitionlinenumber` | The requisition line number | `integer` |
| `lines/itemnumber` | The item number for the line | `string` |
| `lines/linedescription` | The description of the line | `string` |
| `lines/productname` | The line product name | `string` |
| `lines/procurementproductcategoryname` | The procurement category for the product | `string` |
| `lines/requestedpurchasequantity` | The requested purchase quantity | `decimal` |
| `lines/purchaseprice` | The purchase price per unit | `decimal` |
| `lines/lineamount` | The total amount for the line | `decimal` |
| `lines/currencycode` | The currency code for the line currency values | `string` |
| `lines/requesteddate` | The requested date for the line item | `datetime` |

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

### **Release Purchase Requisition Lines**
- **Name:** `releasepurchaserequisitionlines`
- **Description:** Releases purchase requisition lines and creates purchase orders for them.
- **Custom API:** `msdyn_ReleasePurchaseRequisitionLines`

**Inputs**

| Property Name               | Description                                                      | Data Type | Required |
|-----------------------------|------------------------------------------------------------------|----------|----------|
| `defaultVendorAccountNumber` | The vendor account number to use for lines without assigned vendors. | `string` | No |
| `linesToRelease`            | JSON array of lines to release: `[{ "requisitionnumber": "REQ0001", "requisitionlinenumber": 1 }]`. | `string` | Yes |

**Example input**
```json
[
  {
    "defaultVendorAccountNumber": "US-001",
    "linesToRelease": [
      {
        "requisitionnumber":"REQ1001", 
        "requisitionlinenumber": 1
      }
    ]
  }
] 
```

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `result` | The result of the operation to release the lines | `string` |

**Example output**
```json
[
  {
    "result": "OK"
  }
]
```

### **Find Inventory**
- **Name:** `findinventory`
- **Description:** Finds available inventory for a given item number.
- **Custom API:** `msdyn_FindInventory`

**Inputs**

| Property Name  | Description                                                   | Data Type | Required |
|---------------|---------------------------------------------------------------|----------|----------|
| `itemNumber`  | Item number.                                                   | `string` | Yes |
| `siteId`      | Site ID. Can be blank to include all locations.                | `string` | No |
| `warehouseId` | Warehouse ID. Can be blank to include all locations.           | `string` | No |

**Example input**
```json
[
  {
    "itemNumber": "1000",
    "siteId": "1",
    "warehouseId": "11"
  }
]
```

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `ItemNumber` | The item number | `string` | 
| `SiteID` | Site ID | `string` | 
| `WarehouseID` | Warehouse ID | `string` |
| `AvailablePhysical` | The available physical inventory for the item, site, and warehouse | `decimal` |

**Example output**
```json
[ 
  { 
    "ItemNumber": "1000", 
    "SiteID": "1", 
    "WarehouseID": "11", 
    "AvailablePhysical": 500.0 
  }, 
  { 
    "ItemNumber": "1000", 
    "SiteID": "1", 
    "WarehouseID": "13", 
    "AvailablePhysical": 410.0 
  } 
]
```

### **Create Transfer Order for Single Item**
- **Name:** `createtransferorderforsingleitem`
- **Description:** Creates a transfer order for the specified item.
- **Custom API:** `msdyn_CreateTransferOrderForSingleItem`

**Inputs**

| Property Name   | Description                                           | Data Type | Required |
|----------------|-------------------------------------------------------|----------|----------|
| `itemNumber`   | The item number of the product being transferred.     | `string` | Yes |
| `quantity`     | Quantity of the specified item to be transferred.     | `int`    | Yes |
| `fromWarehouseId` | Warehouse from which the item is being transferred. | `string` | Yes |
| `toWarehouseId`   | Warehouse to which the item is being transferred.   | `string` | Yes |

**Example input**
```json
[
  {
    "itemNumber": "1000",
    "quantity": 1,
    "fromWarehouseId": "11",
    "toWarehouseId": "12"  
  }
]
```

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `result` | A message indicating the result of the transfer operation | `string` | 

**Example output**
```json
[
  {
    "result": "Transfer order is created."
  }
]
```

### **Find Purchase Trade Agreements**
- **Name:** `findpurchasetradeagreements`
- **Description:** Finds the most favorable purchase trade agreements based on item number, quantity, vendor, and expected purchase date.
- **Custom API:** `msdyn_FindPurchaseTradeAgreements`

**Inputs**

| Property Name            | Description                                           | Data Type | Required |
|--------------------------|-------------------------------------------------------|----------|----------|
| `itemNumber`            | Item number required to find agreements.              | `string` | Yes |
| `vendorAccountNumber`   | Vendor account number for filtering.                   | `string` | No |
| `expectedPurchaseDate`  | Expected purchase date. Leave blank if not applicable. | `string` | No |
| `expectedPurchaseQuantity` | Expected purchase quantity required for agreements. | `string` | Yes |

**Example input**
```json
[
  {
    "itemNumber": "1000",
    "expectedPurcahseQuantity": 1
  }
]
```

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `price` | The price for the trade agreement with the vendor. | `decimal` | 
| `currency` | The currency code of the price. | `string` | 
| `siteID` | The site for the purchase agreement | `string` | 
| `warehouseID` | The warehouse ID for the purchase agreement | `string` |
| `vendoraccountnumber` | Vendor account number | `string` |
| `itemnumber` | Item number | `string` |
| `unit` | Unit of measure | `string` |

**Example output**
```json
[ 
  { 
    "price": 330.0, 
    "currency": "USD", 
    "siteID": "", 
    "warehouseID": "", 
    "vendoraccountnumber": "", 
    "itemnumber": "1000", 
    "unit": "ea" 
  }, 
  { 
    "price": 200.0, 
    "currency": "USD", 
    "siteID": "", 
    "warehouseID": "", 
    "vendoraccountnumber": "1001", 
    "itemnumber": "1000", 
    "unit": "ea" 
  } 
] 
```

### **Find Released Products**
- **Name:** `findreleasedproducts`
- **Description:** Finds released products using a keyword that matches either the product name or product number.
- **Custom API:** `msdyn_FindReleasedProducts`

**Inputs**

| Property Name               | Description                         | Data Type | Required |
|-----------------------------|-------------------------------------|----------|----------|
| `productNameOrProductNumber` | Product name or product number to search. | `string` | Yes |

**Example input**
```json
[
  {
    "productNameOrProductNumber": "1000"
  }
]
```

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `itemnumber` | Item number | `string` |
| `displayproductnumber` | Display product number | `string` |
| `product_name` | Array of product names for the release products | `string` |

**Example output**
```json
[ 
  { 
    "itemnumber": "1000", 
    "displayproductnumber": "1000", 
    "product_name": [ 
      { 
        "productname": "Surface Pro 128 GB" 
      } 
    ] 
  }, 
  { 
    "itemnumber": "1405", 
    "displayproductnumber": "1405", 
    "product_name": [ 
      { 
        "productname": "Proseware LCD19 E1000" 
      } 
    ] 
  }, 
  { 
    "itemnumber": "1613", 
    "displayproductnumber": "1613", 
    "product_name": [ 
      { 
        "productname": "SV 64GB USB Flash Memory E1000" 
      } 
    ] 
  } 
] 
```

### **Find Invoice Overview**
- **Name:** `findinvoiceoverview`
- **Description:** Get vendor invoice context.
- **Custom API:** `msdyn_VendInvoiceGetInvoiceContextCustomAPI`

**Inputs**

| Property Name                                      | Description             | Data Type | Required |
|----------------------------------------------------|-------------------------|----------|----------|
| `invoiceId`                                       | Vendor invoice number.  | `string` | Yes |
| `vendAccount`                                     | Vendor account number.  | `string` | Yes |

**Outputs**<br>
The purchase invoice can include zero to many invoice lines in the output response.

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `VendName` | Vendor name | `string` |
| `EmployeeResponsible` | The responsible employee for the vendor | `string` |
| `PurchId` | The ID of the purchase invoice | `string` | 
| `ItemList/Item` | The item number of the item in the list | `string` |
| `ItemList/Received` | The received quantity of the item on the invoice line | `decimal` |
| `ItemList/Pending` | The pending quantity of the item on the invoice line | `decimal` |

### **Find Invoice Match Status**
- **Name:** `findinvoicematchstatus`
- **Description:** Check vendor invoice match status.
- **Custom API:** `msdyn_VendInvoiceGetInvoiceMatchStatusCustomAPI`

**Inputs**

| Property Name | Description                        | Data Type | Required |
|--------------|------------------------------------|----------|----------|
| `invoiceId` | Vendor invoice number of the invoice. | `string` | Yes |

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `vendAccount` | Vendor account number | `string` |
| `invoiceStatus` | Invoice status | `VendInvoiceCopilotExceptionStatus` enum |
| `productReceiptToMatch` | Product receipt to match | `integer` |

**Example output**

```json
[
  { 
    "vendAccount": "1001", 
    "invoiceStatus": "2", 
    "productReceiptToMatch": "5", 
  }
]
```

### **Match Invoice**
- **Name:** `matchinvoice`
- **Description:** Match vendor invoice with product receipt.
- **Custom API:** `msdyn_VendInvoiceMatchProductReceiptCustomAPI`

**Inputs**

| Property Name | Description                            | Data Type | Required |
|--------------|----------------------------------------|----------|----------|
| `invoiceId` | Vendor invoice number to be matched.  | `string` | Yes |

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `fullyMatched` | Whether the invoice has been fully matched | Boolean<br><ul><li>1 = matched <li>0 = not matched </ul> |


### **Notify Responsible Employee**
- **Name:** `notifyresponsibleemployee`
- **Description:** Sends a notification to the vendor's responsible employee.
- **Custom API:** `msdyn_VendInvoiceNotifyVendorResponsibleEmployeeCustomAPI`

| Property Name | Description | Data Type | Required |
|--------------|-------------|----------|----------|
| `notificationMessage` | Notification message to be sent to the vendor's responsible employee. | `string` | Yes |
| `vendAccount` | Vendor account of the vendor invoice. | `string` | Yes |

**Output**: There are no outputs for this tool.

### **Find Unmatched Invoices**
- **Name:** `findunmatchedinvoices`
- **Description:** Retrieves a list of vendor invoices that haven't been matched.
- **Custom API:** `msdyn_VendInvoiceGetUnmatchedInvoicesCustomAPI`

**Input**: This tool doesn't require input properties.

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `invoiceId` | The invoice ID of the unmatched invoice | `string` |
| `vendorAccount` | The vendor account number | `string` |

**Output example**

```json
{ 
  "invoices": [ 
    {"invoiceId": "INV001", "vendorAccount": "ACC001"}, 
    {"invoiceId": "INV002", "vendorAccount": "ACC002"}, 
    {"invoiceId": "INV003", "vendorAccount": "ACC003"} 
  ] 
} 
```

### **Submit Invoice to Workflow**
- **Name:** `submittoworkflow`
- **Description:** Submits an invoice to the workflow for processing.
- **Custom API:** `msdyn_VendInvoiceSubmitToWorkflowCustomAPI`

| Property Name | Description | Data Type | Required |
|--------------|-------------|----------|----------|
| `invoiceId` | Vendor invoice number of the given invoice. | `string` | Yes |
| `comment` | Workflow submission comment. | `string` | Yes |

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `status` | Status of the workflow submission | Enum <br><ul><li>Success <li>Failure </ul> |
| `message` | Failure details when there's a Failure status | `string` |


