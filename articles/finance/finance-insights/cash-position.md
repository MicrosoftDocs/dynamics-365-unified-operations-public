---
# required metadata

title: Cash position
description: This article describes how the Cash flow forecasting feature predicts an organization's cash position for specific times. It also describes the options that are available for showing forecasts for different periods. 
author: ShivamPandey-msft
ms.date: 12/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.assetid: 3d43ba40-780c-459a-a66f-9a01d556e674
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2019-11-06
ms.dyn365.ops.version: AX 10.0.8

---

# Cash position

[!include [banner](../includes/banner.md)]

Cash position is the projection of cash flow that is forecast for the near term. It's based on the projection of cash receipts from customers that pay outstanding invoices and orders, and also on the projection cash disbursements that are paid to vendors for purchase invoices and orders.

When the system predicts customer payments, it uses the payment predictions from the customer payment prediction feature. Without payment predictions, the average time that is required to convert a customer invoice to a payment for each customer is used to calculate a payment date. For open customer orders, the system calculates the invoice date by using the average number of days for order lines per customer to be invoiced. It then uses the invoice date as an input for the payment prediction functionality. The customer payment prediction functionality calculates a payment date for each order line. 

The payment date for outstanding invoices is estimated from the payment predictions by picking a date that corresponds to fiftieth percentile of the cumulative distribution function that's obtained from the predicted bucket's probabilities.

A similar approach is used to predict payments to vendors. For each vendor, the system calculates the average time that is required to convert a vendor invoice to a payment. That number of days is then used to calculate the payment date. For open vendor orders, the system calculates the invoice date by considering the average number of days that is required to convert order lines to an invoice for each vendor. The system then calculates the payment date by using the average time to convert a vendor invoice to a payment for each vendor.

The upper section of the **Cash position** tab includes a cash position chart. This chart shows cash inflows and outflows, and their impact on the total liquidity balance. The details in the cash position chart can be viewed in daily, weekly, monthly, or quarterly periods. When you select **Daily**, you can view forecasts for the next 21 days. When you select **Weekly**, you can view forecasts for the next 20 weeks. When you select **Monthly**, you can view forecasts for the next 12 months. When you select **Quarterly**, you can view forecasts for the next 12 quarters. You can hide the chart if you require additional space on your screen to view content on the **Cash position** tab.

The lower section of the **Cash position** tab shows details for the position, cash flow, projected payments, and bank account.

- Information in the **Position details** grid is presented in three sections: a list of liquidity accounts, a list of documents that make up cash inflows, and a list of documents that make up cash outflows. The grid also shows cash position balances. For the first period that you're viewing, the balance for the liquidity accounts is the opening balance. For subsequent periods, the balances for the liquidity accounts are calculated based on the addition of cash inflows and the subtraction of cash outflows from previous periods. To view details of the transactions that make up the balance, select the **Balance** link.
- The **Cash flow** grid shows cash inflows, cash outflows aggregated per period, and their impact on liquidity account balances. For the first period, the balance for the liquidity accounts is the opening balance. For subsequent periods, the balances for the liquidity accounts are calculated based on the addition of cash inflows and the subtraction of cash outflows from previous periods.
- The **Projected bank balance** grid show expected cash outflows and their impact on liquidity accounts.
- The **Bank account** grid shows the impact of expected cash inflows and outflows on the bank balance.

To save and edit the cash position, create a snapshot. For more information about how to work with snapshots, see [Snapshots overview](payment-snapshots.md).

## Details of the Cash position capability 

The Cash position feature includes the following functionality. 

- Cash position feature shows the cashflow based on existing documents in the system and cash inflow and outflow lines imported from external systems.
- Makes it easy to integrate cash flow data from external systems to Dynamics 365 Finance. Cash position can also use the data import-export framework. This framework makes it easy to integrate with Excel OData. You can also combine data from multiple sources to create a comprehensive cash position solution.
- Introduces intelligent cash position. Cash position is created based on customer’s payment behavior to predict when a company can expect cash to arrive in their accounts.
- For Customer orders and invoices, customer payment prediction AI functionality is used to determine the historical customer payment behavior when an order or invoice will be paid.
- For vendor orders and invoices, we use average time between shipping and invoice and paying an invoice per vendor to determine when a vendor order or invoice will be paid making cash outflows more accurate.

This creates a more accurate view of cash flow based on historical payment behavior for the treasurer. 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
