---
# required metadata

title: Tax calculation data model overview
description: This topic provides information about how the field values in the tax data model are determined during tax calculation transactions.
author: kailiang
ms.date: 08/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21

---
# Tax calculation data model overview

This topic provides information about how the fieldvalues in the tax data model are determined in tax calculation transactions.

The **tax data model** is made up of fields that are required for tax calculations. Microsoft provides the **Tax calculation data model** which is includes header fields and line fields of transaction documents in Dynamics 365 finance and operations apps. The fields defined in the tax calculation data model are the available columns of the applicability rules tables in the tax calculation feature configuration.

> [!NOTE] 
> Some nodes, such as **Record ID** and **Table ID** are defined in the data model are for technical purposes. They aren't available columns in the tax calculation feature configuration.

Conplete the following steps to view the Tax calculation data model.

1.  Log in to the Regulatory Configuration Service (RCS) and go to **Electronic reporting** > **Tax configurations**.
2.  Select **Tax Data Model** > **Tax Calculation Data Model**.
3.  On the **Versions** FastTab, select a version.
4.  Select **Designer**.

    [![Data model designer (button)](./media/tax-calculation-model-mapping-1.png)](./media/tax-calculation-model-mapping-1.png)

5.  Expand the **Tax service** node.
6.  Expand the **Header** node to view the header data models.
7.  Expand the **Lines** node to view the line data models.

    [![Data models](./media/tax-calculation-model-mapping-2.png)](./media/tax-calculation-model-mapping-2.png)

You can also view the Tax calculation data model and the available columns in the **Applicability rules** table.

1.  In RCS, go to **Globalization features** > **Tax calculation**.
2.  Find a tax feature with a status of **Draft** and then select **Edit**.
3.  On the **General** tab, select the configuration version based on the tax calculation data model version. For example, 40.46.212.
4.  On the **Tax group applicability** tab, select **Manage columns**.

    [![Manage columns](./media/tax-calculation-model-mapping-3.png)](./media/tax-calculation-model-mapping-3.png)

The Tax calculation data model is integrated with finance and operations apps. During each tax calculation related transaction, the values of the fields defined in the **Applicability** tables will be collected and sent to the tax calculation service for calculation. In version 40.46, there are 57 predefined data models available for the following transactions: purchase order, sales order, transfer order, purchase requisition, request for quotation and sales quotation.

There are 31 data models that can be included as fields on the header of a transaction. However, not all fields are applicable to all transaction types. The following table provides information about which header fields are available on specific transaction types. In some cases, a specific priority is defined by logic to determine the field mapping. A list and field path is provided for clarify. 

| Field                                 | Business transaction type and field mapping |
|---------------------------------------|---------------------------------------------|
| Amount include tax                    |  - **Sales order**: Prices include sales tax <br> - **Purchase order**: Prices include sales tax <br> - **Purchase requisition**: No <br> - **Request for quotation**: Prices include sales tax <br> - **Sales quotation**: Prices include sales tax                                     |
| Business process                      | - **Sales order**: Sales <br> - **Purchase order**: Purchase <br> - **Transfer order - Ship**: Inventory <br>- **Transfer order - Receive**: Inventory <br>- **Purchase requisition**: Purchase  <br>- **Request for quotation**: Purchase <br>- **Sales quotation**: Sales                  |
| Currency                              | - **Sales order**: Transaction currency<br>- **Purchse order**: Transaction currency <br>- **Transfer order - Ship**: Accounting currency <br>- **Transfer order - Receive**: Accounting currency <br>- **Purchase requisition**: Transaction currency                                      |
| Customer account                      | - **Sales order**: Customer account <br>- **Sales quotation**: Customer account                                      |
| Customer invoice account              | - **Sales order**: Invoice account <br>- **Sales quotation**: Invoice account                                    |
| Delivery term                         | - **Sales order**: Delivery terms <br>- **Purchase order**: Delivery terms <br> - **Transfer order - Ship**: Delivery terms <br>- **Transfer order - Receive**: Delivery terms <br> - **Request for quotation**: Delivery terms <br> - **Sales quotation**: Delivery terms                                    |
| Invoice from city                     | **Sales order**<br>1. Legal entity > Default invoice address > City <br>2. Legal entity > Primary address > City <br>**Purchase order**<br>1. Header > Invoice account > Default invoice address > City <br>2. Header > Invoice account > Primary address > City <br>**Sales quotation**<br>1. Legal entity > Default invoice address > City <br>2. Legal entity > Primary address > City                                    |
| Invoice from country/region           | **Sales order**<br> 1. Legal entity > Default invoice address > Country/region <br>2. Legal entity > Primary address > Country/region <br>**Purchase order**<br>1. Header > Invoice account > Default invoice address > Country/region <br>2. Header > Invoice account > Primary address > Country/region <br>**Sales quotation**<br>1. Legal entity > Default invoice address > Country/region <br>2. Legal entity > Primary address > Country/region                                     |
| Invoice from country/region type      | SO                                    |
| Invoice from province/state           | SO                                    |
| Invoice from zip code                 | SO                                    |
| Invoice to city                       | SO                                    |
| Invoice to country/region             | SO                                    |
| Invoice to country/region type        | SO                                    |
| Invoice to province/state             | SO                                    |
| Invoice to zip code                   | SO                                    |
| Ship from city                        | SO                                    |
| Ship from country/region              | SO                                    |
| Ship from country/region type         | SO                                    |
| Ship from province/state              | **Sales order**<br>1. Header > Warehouse > Primary address > State<br>2. Header > Site > Primary address > State<br>3. Legal entity > Default delivery address > State<br>4. Legal entity > Primary address > State<br>**Purchase order**<br>1. Header > Vendor account > Default delivery address > State<br>2. Header > Vendor account > Primary address > State<br>**Transfer order - Ship**<br>1. Header > From warehouse > Primary address > State<br>2. Header > From site > Primary address > state<br>**Transfer order - Receive**<br>1. Header > From warehouse > Primary address > State<br>2. Header > From site > Primary address > State<br>**Request for quotation**<br>1. Header > Vendor account > Default delivery address > State<br>2. Header > Vendor account > Primary address > State<br> **Sales quotation**<br>1. Header > Warehouse > Primary address > State<br>2. Header > Site > Primary address > State<br>3. Legal entity > Default delivery address > State<br>4. Legal entity > Primary address > State                                    |
| Ship from zip code                    | **Sales order**<br>1. Header > Warehouse > Primary address > ZIP/postal code<br>2. Header > Site > Primary address > ZIP/postal code<br>3. Legal entity > Default delivery address > ZIP/postal code <br>4. Legal entity > Primary address > ZIP/postal code<br>**Purchase order**<br>1. Header > Vendor account > Default delivery address > ZIP/postal code<br>2. Header > Vendor account > Primary address > ZIP/postal code<br>**Transfer order - Ship**<br>1. Header > From warehouse > Primary address > ZIP/postal code<br>2. Header > From site > Primary address > ZIP/postal code<br>**Transfer order - Receive**<br>1. Header > From warehouse > Primary address > ZIP/postal code<br>2. Header > From site > Primary address > ZIP/postal code <br>**Request for quotation**<br>1. Header > Vendor account > Default delivery address > ZIP/postal code<br>2. Header > Vendor account > Primary address > ZIP/postal code<br> **Sales quotation**<br>1. Header > Warehouse > Primary address > ZIP/postal code<br>2. Header > Site > Primary address > ZIP/postal code<br>3. Legal entity > Default delivery address > ZIP/postal code<br>4. Legal entity > Primary address > ZIP/postal code                                |
| Ship to city                          | **Sales order**<br>1. Header > Delivery address > City <br>2. Header > Customer account > Default delivery address > City <br>3. Header > Customer account > Primary address > City<br>**Purchase order**<br>1. Header > Delivery address > City<br>2. Header > Warehouse > Primary address > City<br>3. Header > Site > Primary address > City<br>4. Legal entity >Default delivery address > City<br>5. Legal entity > Primary address > City<br>**Transfer order - Ship**<br>1. Header > To warehouse > Primary address > City<br>2. Header > To site > Primary address > City<br>**Transfer order- Receive**<br>1. Header > To warehouse > Primary address > City<br>2. Header > To site > Primary address > City<br>**Request for quotation**<br>1. Header > Warehouse > Primary address > City<br>2. Header > Site > Primary address > City<br>3. Legal entity > Default delivery address > City<br>4. Legal entity > Primary address > City<br>**Sales quotation**<br>1. Header > Delivery address > City<br>2. Header > Customer account > Default delivery address > City<br>3. Header > Customer account > Primary address > City                                    |
| Ship to country/region                | **Sales order**<br>1. Header > Delivery address > Country/region <br>2. Header > Customer account > Default delivery address > Country/region <br>3. Header > Customer account > Primary address > Country/region<br>**Purchase order**<br>1. Header > Delivery address > Country/region<br>2. Header > Warehouse > Primary address > Country/region<br>3. Header > Site > Primary address > Country/region<br>4. Legal entity >Default delivery address > Country/region<br>5. Legal entity > Primary address > Country/region<br>**Transfer order - Ship**<br>1. Header > To warehouse > Primary address > Country/region<br>2. Header > To site > Primary address > Country/region<br>**Transfer order- Receive**<br>1. Header > To warehouse > Primary address > Country/region<br>2. Header > To site > Primary address > Country/region<br>**Request for quotation**<br>1. Header > Warehouse > Primary address > Country/region<br>2. Header > Site > Primary address > Country/region <br>3. Legal entity > Default delivery address > Country/region<br>4. Legal entity > Primary address > Country/region<br>**Sales quotation**<br>1. Header > Delivery address > Country/region<br>2. Header > Customer account > Default delivery address > Country/region<br>3. Header > Customer account > Primary address > Country/region     |
| Ship to country/region type           | **Sales order** <br>1. If the **Ship from country/region** and **Ship to country/region** fields have the same value, then the type is **Domestic**. <br>2. Determined by the configuration in **Tax** > **Foreign trade parameters** > **Country/region properties** based on the value in the **Ship to country/region** field. <br>**Purchase order**<br>1. If the **Ship from country/region** and **Ship to country/region** fields have the same value, then the type is **Domestic**.<br>2. Determined by the configuration in **Tax** > **Foreign trade parameters** > **Country/region properties** based on the value in the **Ship to country/region** field.<br>**Transfer order - Ship**<br>1. If the **Ship from country/region** and **Ship to country/region** fields have the same value, then the type is **Domestic**.<br>2. Determined by the configuration in **Tax** > **Foreign trade parameters** > **Country/region properties** based on the value in the **Ship to country/region** field.<br>**Transfer order - Receive**<br>1. If the **Ship from country/region** and **Ship to country/region** fields have the same value, then the type is **Domestic**.<br>2. Determined by the configuration in **Tax** > **Foreign trade parameters** > **Country/region properties** based on the value in the **Ship to country/region** field.<br>**Purchase requisition**: Domestic<br>**Request for quotation**<br>1. If the **Ship from country/region** and **Ship to country/region** fields have the same value, then the type is **Domestic**.<br>2. Determined by the configuration in **Tax** > **Foreign trade parameters** > **Country/region properties** based on the value in the **Ship to country/region** field.<br>**Sales quotation**<br>1. If the **Ship from country/region** and **Ship to country/region** fields have the same value, then the type is **Domestic**.<br>2. Determined by the configuration in **Tax** > **Foreign trade parameters** > **Country/region properties** based on the value in the **Ship to country/region** field.                                |
| Ship to province/state               | **Sales order** <br> 1. Header > Delivery address > State <br> 2. Header > Customer account > Default delivery address > State <br> 3. Header > Customer account > Primary address > State <br>**Purchase order** <br> 1. Header > Delivery address > State <br> 2. Header > Warehouse > Primary address > State <br> 3. Header > Site > Primary address > State <br>4. Legal entity > Default delivery address > State <br>5.  Legal entity > Primary address > State <br>**Transfer order - Ship** <br>1. Header > To warehouse > Primary address > State <br>2. Header > To site > Primary address > State <br>**Transfer order - Receive** <br>1. Header > To warehouse > Primary address > State <br>2. Header > To site > Primary address > State <br>**Request for quotation**<br>1. Header > Warehouse > Primary address > State <br>2. Header > Site > Primary address > State <br>3. Legal entity > Default delivery address > State <br>4. Legal entity > Primary address > state <br>**Sales quotation** <br>1. Header > Delivery address > state <br>2. Header > Customer account > Default delivery address > state <br>3. Header > Customer account > Primary address state                                   |
| Ship to zip code                      | **Sales order** <br> 1. Header > Delivery address > ZIP/postal code <br> 2. Header > Customer account > Default delivery address > ZIP/postal code <br> 3. Header > Customer account > Primary address > ZIP/postal code <br>**Purchase order** <br> 1. Header > Delivery address > ZIP/postal code <br> 2. Warehouse > Primary address > ZIP/postal code <br> 3. Header > Site > Primary address > ZIP/postal code <br>4. Legal entity > Default delivery address > ZIP/postal code <br>5.  Legal entity > Primary address > ZIP/postal code <br>**Transfer order - Ship** <br>1. Header > To warehouse > Primary address > ZIP/postal code <br>2. Header > To site > Primary address > ZIP/postal code <br>**Transfer order - Receive** <br>1. Header > To warehouse > Primary address > ZIP/postal code <br>2. Header > To site > Primary address > ZIP/postal code <br>**Request for quotation**<br>1. Header > Warehouse > Primary address > ZIP/postal code <br>2. Site > Primary address > ZIP/postal code <br>3. Legal entity > Default delivery address > ZIP/postal code <br>4. Legal entity > Primary address > ZIP/postal code <br>**Sales quotation** <br>1. Header > Delivery address > ZIP/postal code <br>2. Header > Customer account > Default delivery address > ZIP/postal code <br>3. Header > Customer account > Primary address ZIP/postal code                              |
| Site                                  | - **Sales order**: Site <br>- **Purchase order**: Site <br>- **Transfer order - Ship**: Site of the From warehouse <br>- **Transfer order - Receive**: Site of To warehouse <br>- **Request for quotation**: Site <br>- **Sales quotation**: Site                                   |
| Tax direction                         | - **Sales order**: Output <br>- **Purchase order**: Input <br>- **Transfer order - Ship**: Output <br>- **Transfer order - Receive**: Input <br>- **Purchase requisition**: Input <br>- **Request for quotation**: Input <br> - **Sales quotation**: Output                                    |
| Vendor account                        | - **Purchase order**: Vendor account                                    |
| Vendor invoice account                | - **Purchase order**: Invoice account                                    |
| Warehouse                             | - **Sales order**: Warehouse <br>- **Purchase order**: Warehouse <br>- **Transfer order - Ship**: From warehouse <br>- **Transfer order - Receive**: To warehouse <br>- **Request for quotation**: Warehouse <br>- **Sales quotation**: Warehouse                                   |



There are 26 data models that are included as fields in the lines of a transaction. As with the header fields, not all fields are applicable to all transaction types. The following table provides information about which line fields are available on specific transaction types. 


​                   <--table 2 line fields fetching logic-->

