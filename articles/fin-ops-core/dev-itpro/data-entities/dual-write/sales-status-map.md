---
title: Set up the mapping for the sales order status columns
description: Learn how to set up the sales order status columns for dual-write, including various tables that outline setup and mappings for dual-write solutions.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 10/29/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2020-06-25
ms.custom: sfi-image-nochange
---

# Set up the mapping for the sales order status columns

[!include [banner](../../includes/banner.md)]

The columns that indicate sales order status have different enumeration values in Microsoft Dynamics 365 Supply Chain Management and Dynamics 365 Sales. You need extra setup to map these columns in dual-write.

## Columns in Supply Chain Management

In Supply Chain Management, two columns reflect the status of the sales order. The columns that you must map are **Status** and **Document Status**.

The **Status** enumeration specifies the overall order status. The order header shows this status.

The **Status** enumeration has the following values:

- Open Order
- Delivered
- Invoiced
- Canceled

The **Document Status** enumeration specifies the most recent document generated for the order. For example, if you confirm the order, this document is a sales order confirmation. If you partially invoice a sales order and then confirm the remaining line, the document status remains **Invoice** because the system generates the invoice later in the process.

The **Document Status** enumeration has the following values:

- Confirmation
- Picking List
- Packing Slip
- Invoice

## Columns in Sales

In Sales, two columns indicate the order status. Map the **Status** and **Processing Status** columns.

The **Status** enumeration specifies the overall status of the order. It has the following values:

- Active
- Submitted
- Fulfilled
- Invoiced
- Canceled

The **Processing Status** enumeration lets you map status more accurately with Supply Chain Management.

The following table shows the mapping of **Processing Status** in Supply Chain Management.

| Processing Status   | Status in Supply Chain Management | Document Status in Supply Chain Management |
|---------------------|-----------------------------------|--------------------------------------------|
| Active              | Open Order                        | None                                       |
| Confirmed           | Open Order                        | Confirmation                               |
| Picked              | Open Order                        | Picking List                               |
| Partially Delivered | Open Order                        | Packing Slip                               |
| Delivered           | Delivered                         | Packing Slip                               |
| Partially Invoiced  | Delivered                         | Invoice                                    |
| Invoiced            | Invoiced                          | Invoice                                    |
| Canceled           | Canceled                         | Not applicable                             |

The following table shows the mapping of **Processing Status** between Sales and Supply Chain Management.

| Processing Status   | Status in Sales | Status in Supply Chain Management |
|---------------------|-----------------|-----------------------------------|
| Active              | Active          | Open Order                        |
| Confirmed           | Submitted       | Open Order                        |
| Picked              | Submitted       | Open Order                        |
| Partially Delivered | Active          | Open Order                        |
| Partially Invoiced  | Active          | Open Order                        |
| Partially Invoiced  | Fulfilled       | Delivered                         |
| Invoiced            | Invoiced        | Invoiced                          |
| Canceled           | Canceled       | Canceled                         |

## Mappings for the updated Dual-write Supply chain solution

If you're using the updated Dual-write Supply chain solution, then the status map is updated as described in this section. These changes depend on whether the map for the *CDS sales order headers* entity or the map for the *Dynamics 365 Sales order headers* entity is running. For details about version requirements, see [Prerequisites](../../../fin-ops/data-entities/add-efficiency-in-quote-to-cash-enable.md#prerequisites).

The following table shows the resulting status map if the map for the *CDS sales order headers* entity is running.

| Processing Status   | Status in Supply Chain Management | Document Status in Supply Chain Management | Status in Sales |
|---------------------|-----------------------------------|--------------------------------------------|-----------------|
| Active              | Open Order                        | None                                       | Active          |
| Confirmed           | Open Order                        | Confirmation                               | Active          |
| Picked              | Open Order                        | Picking List                               | Active          |
| Partially Delivered | Open Order                        | Packing Slip                               | Active          |
| Partially Invoiced  | Open Order                        | Invoice                                    | Active          |
| Delivered           | Delivered                         | Packing Slip                               | Fulfilled       |
| Invoiced            | Invoiced                          | Invoice                                    | Invoiced        |
| Canceled           | Canceled                         | Not applicable                             | Canceled        |

If the map for the *Dynamics 365 Sales order headers* entity is running, the processing status (*Delivered and Partially Invoiced*) is introduced. The following table shows the resulting status map.

| Processing Status                 | Status in Supply Chain Management | Document Status in Supply Chain Management | Status in Sales |
|-----------------------------------|-----------------------------------|--------------------------------------------|-----------------|
| Active                            | Open Order                        | None                                       | Active          |
| Confirmed                         | Open Order                        | Confirmation                               | Active          |
| Picked                            | Open Order                        | Picking List                               | Active          |
| Partially Delivered               | Open Order                        | Packing Slip                               | Active          |
| Partially Invoiced                | Open Order                        | Invoice                                    | Active          |
| Delivered                         | Delivered                         | Packing Slip                               | Fulfilled       |
| Delivered and Partially Invoiced  | Delivered                         | Invoice                                    | Fulfilled       |
| Invoiced                          | Invoiced                          | Invoice                                    | Invoiced        |
| Canceled                         | Canceled                         | Not applicable                             | Canceled        |

## Setup

To set up the mapping for the sales order status columns, enable the **IsSOPIntegrationEnabled** and **isIntegrationUser** attributes.

To enable the **IsSOPIntegrationEnabled** attribute:

1. In a browser, go to `https://<test-name>.crm.dynamics.com/api/data/v9.0/organizations`. Replace *`<test-name>`* with your company's link to Sales.
1. On the page that opens, find **organizationid**, and make a note of the value.

    :::image type="content" source="media/sales-map-orgid.png" alt-text="Screenshot of finding organizationid.":::

1. In Sales, open the browser console, and run the following script. Use the **organizationid** value from step 2.

    ```javascript
    Xrm.WebApi.updateRecord("organization",
    "d9a7c5f7-acbf-4aa9-86e8-a891c43f748c", {"issopintegrationenabled" :
    true}).then(
        function success(result) {
            console.log("Account updated");
            // perform operations on row update
        },
        function (error) {
            console.log(error.message);
            // handle error conditions
        }
    );
    ```

    :::image type="content" source="media/sales-map-script.png" alt-text="Screenshot of JavaScript code in the browser console.":::

1. Verify that **IsSOPIntegrationEnabled** is set to **true**. Use the URL from step 1 to check the value.

    :::image type="content" source="media/sales-map-integration-enabled.png" alt-text="Screenshot of IsSOPIntegrationEnabled set to true.":::

To enable the **isIntegrationUser** attribute:

1. In Sales, go to **Settings > Customization > Customize the System**, select **User table**, and then open **Form > User**.

    :::image type="content" source="media/sales-map-user.png" alt-text="Screenshot of opening the user form.":::

1. In Field Explorer, find **Integration user mode**, and double-click it to add it to the form. Save your change.

    :::image type="content" source="media/sales-map-field-explorer.png" alt-text="Screenshot of adding the Integration user mode column to the form.":::

1. In Sales, go to **Settings > Security > Users**, and change the view from **Enabled Users** to **Application Users**.

    :::image type="content" source="media/sales-map-enabled-users.png" alt-text="Screenshot of changing the view from Enabled Users to Application Users.":::

1. Select the two entries for **DualWrite IntegrationUser**.

    :::image type="content" source="media/sales-map-user-mode.png" alt-text="Screenshot of list of application users.":::

1. Change the value of the **Integration user mode** column to **Yes**.

    :::image type="content" source="media/sales-map-user-mode-yes.png" alt-text="Screenshot of changing the value of the Integration user mode column.":::

Your sales orders are now mapped.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
