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
| `itemnumber` | The item number | String |
| `approvedvendoraccountnumber` | The vendor account number of the approved vendor for the item | String |
| `validfrom` | The date and time from which the approval is valid | Datetime |
| `validto` | The date and time from to which the approval is valid | Datetime |

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
| `requisitionnumber` | The requisition number | String |
| `requisitionname` | The requisition name | String |
| `requisitionstatus` | The current status of the requisition | Choice, with the following value options: <ul><li>200000000: Draft <li>200000001: In review <li>200000002: Rejected <li>200000003: Approved <li>200000004: Cancelled <li>200000005: Closed <li>200000006: Budget reserved </ul> |
| `lines/requisitionlinenumber` | The requisition line number | Integer |
| `lines/itemnumber` | The item number for the line | String |
| `lines/linedescription` | The description of the line | String |
| `lines/productname` | The line product name | String |
| `lines/procurementproductcategoryname` | The procurement category for the product | String |
| `lines/requestedpurchasequantity` | The requested purchase quantity | Decimal |
| `lines/purchaseprice` | The purchase price per unit | Decimal |
| `lines/lineamount` | The total amount for the line | Decimal |
| `lines/currencycode` | The currency code for the line currency values | String |
| `lines/requesteddate` | The requested date for the line item | Datetime |

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
| `result` | The result of the operation to release the lines | String |

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
    "organization:: 'usmf',
    "itemNumber": '1000'
  }
]
```

**Outputs**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `ItemNumber` | The item number | String | 
| `SiteID` | Site ID | String | 
| `WarehouseID` | Warehouse ID | String |
| `AvailablePhysical` | The available physical inventory for the item, site, and warehouse | Decimal |

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
    "itemNumber": '1000',
    "quantity": 1,
    "fromWarehouseId": '11',
    "toWarehouseId": '12'  
  }
]
```

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `result` | A message indicating the result of the transfer operation | String | 

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
    "itemNumber": '1000',
    "expectedPurcahseQuantity": 1
  }
]
```

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `price` | The price for the trade agreement with the vendor. | Decimal | 
| `currency` | The currency code of the price. | String | 
| `siteID` | The site for the purchase agreement | String | 
| `warehouseID` | The warehouse ID for the purchase agreement | String |
| `vendoraccountnumber` | Vendor account number | String |
| `itemnumber` | Item number | String |
| `unit` | Unit of measure | String |

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
| `itemnumber` | Item number | String |
| `displayproductnumber` | Display product number | String |
| `product_name` | Array of product names for the release products | String |

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
| `VendName` | Vendor name | String |
| `EmployeeResponsible` | The responsible employee for the vendor | String |
| `PurchId` | The ID of the purchase invoice | String | 
| `ItemList/Item` | The item number of the item in the list | String |
| `ItemList/Received` | The received quantity of the item on the invoice line | Decimal |
| `ItemList/Pending` | The pending quantity of the item on the invoice line | Decimal |

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
| `vendAccount` | Vendor account number | String |
| `invoiceStatus` | Invoice status | VendInvoiceCopilotExceptionStatus enum |
| `productReceiptToMatch` | Product receipt to match

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
- **Description:** Retrieves a list of vendor invoices that have not been matched.
- **Custom API:** `msdyn_VendInvoiceGetUnmatchedInvoicesCustomAPI`

**Input**: This tool does not require input properties.

**Output**

| Output | Description | Data type |
| ------ | ----------- | --------- |
| `invoiceId` | The invoice ID of the unmatched invoice | String |
| `vendorAccount` | The vendor account number | String |

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
| `message` | Failure details in case of Failure status | String |


