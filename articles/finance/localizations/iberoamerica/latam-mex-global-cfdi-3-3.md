---
title: Global CFDI electronic invoices for Mexico
description: Learn about the functionality for Global CFDI electronic invoices for Mexico, including an outline on processing global CFDI documents.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: article
ms.date: 06/29/2022
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Mexico
ms.search.industry: Retail
ms.search.validFrom: 2019-06-01
ms.search.form:
ms.dyn365.ops.version: 10.0.2
---

# Global CFDI electronic invoices for Mexico 

[!include[banner](../../includes/banner.md)]

The Commerce functionality for Mexico supports the Comprobantes fiscales digitales por internet (CFDI) format for Mexican companies. For more information about CFDI electronic invoices, see [Electronic invoices (CFDI)](latam-mex-CFDI-electronic-invoices.md). When a company closes the period, it must issue a Global CFDI document to consolidate all the receipts that were issued to the final consumers. This document includes the following information for each transaction that is registered during the period:

- A receipt number
- A corresponding amount

## Processing Global CFDI documents

The Global CFDI functionality lets you perform the following tasks:

- Create an electronic invoice, in Global CFDI format, that is based on the posted commerce statement. For more information about the layout, see [CFDI layout version 4.0](latam-mex-cfdi-4-0.md).
- For each electronic invoice, generate a file in the .pdf or .xml format, and send it to the customer as an email attachment. After the Global CFDI electronic invoices are generated, they are verified and certified by a digital signature service provider (PAC) in the same way as other CFDI documents. For more information, see [Electronic invoices (CFDI)](latam-mex-CFDI-electronic-invoices.md) and [Inquire and print an electronic invoice](mx-00010-inquire-print-electronic-invoice.md).

To generate and submit a Global CFDI electronic invoice, follow these steps.

1. Go to **Accounts receivable** \> **Invoices** \> **E-Invoices** \> **Electronic invoice parameters**. 
2. On the **Retail** tab, specify the default parameters of the Global CFDI format.
3. Go to **Organization administration** \> **Number sequences** \> **Number sequences**, and create a new number sequence that has the following settings: 
	
	- Set the **Scope** field to **Operation unit**.
	- Set the **Operating unit** field to **MX store**.
	- Add **CFDI Global aggregated statement number** to the references.

4. Close the shift at the point of sale (POS).
5. Run the P-job in the distribution schedule to transfer transactions from the channel database to Headquarters.
6. Calculate and post a statement by following the steps in [Create, calculate, and post a statement for a retail store](../../../retail/tasks/create-calculate-post-statement-retail-store.md).
7. Run the **Post CFDI – Electronic invoices** periodic operation to create Global CFDI electronic invoices that are based on a posted statement. Select a statement number for this periodic operation. If you don't select a statement number, the system creates Global CFDI electronic invoices for all posted statements that haven't yet been processed. 

    > [!NOTE]
    > Mark the **Aggregation** flag, and select the period for aggregation: **Daily**, **Weekly**, **Biweekly**, **Monthly**, or **Bimonthly**. This option is mandatory for layout version 4.0.

    As a result of the **Post CFDI – Electronic invoices** periodic operation, two Global CFDI electronic invoices are created. One electronic invoice collects all the receipts that are related to sales operations, and the other collects all the receipts that are related to returns. For the electronic invoice that is related to returns, the **Return** attribute is set to **Yes**. You can view these electronic invoices on the **CFDI (electronic invoices)** pages by going to **Retail and Commerce** \> **Inquiries and reports** \> **CFDI (electronic invoices)** and **CFDI (electronic invoices) aggregated**.

    All further workflows, such as communication with a service provider, generation of the .pdf and .xml files, and manual functions, are the same as the workflows for CFDI Normal electronic invoices.

8. Run the **Export/import electronic invoice process** periodic operation to submit electronic invoices to the PAC.

## Updates for the Global CFDI functionality

In Microsoft Dynamics 365 Finance version 10.0.2 (May 2019), the Global CFDI functionality was extended to support new requirements that were introduced in the second revision of the *Global CFDI filling guide*. Starting in Microsoft Dynamics 365 Finance version 10.0.2 (May 2019), you can perform the following tasks:

- At the customer's request, generate a separate CFDI Normal electronic invoice that is based on a sale or return operation that is registered at the POS.

    In this case, the sale or return operation should be registered as a customer order. For more information about the functionality for customer orders, see [Customer orders in Modern POS (MPOS)](/dynamics365/unified-operations/retail/customer-orders-overview).

- In a CFDI electronic invoice that is generated based on returns, specify universally unique identifiers (UUIDs) for CFDI electronic invoices that are related to the original sales operations.

Starting in Dynamics 365 Finance version 10.0.2 (May 2019), the Global CFDI functionality also supports the following additional scenarios:

- [Item returns across multiple customer orders and invoices](/dynamics365/unified-operations/retail/multireturn)
- Customer order returns that involve an exchange, when a customer invoice includes both lines that have positive amounts and lines that have negative amounts

Starting in Dynamics 365 for Finance and Operations version 10.0.27 (June 2022), the Global CFDI functionality has been extended to meet the regulatory requirement for version 4.0 of the Global CFDI layout. The following main changes were made to the format:

- Aggregation of all receipts that were issued to the final consumers for the selected period
- A new retail-specific **InformacionGlobal** element that indicates the period parameters


### Showing related CFDI documents in a CFDI electronic invoice

To show the UUIDs of the original sales in CFDI electronic invoices for returns, turn on the **Specify related CFDI in returns** parameter on the **Retail** tab of the **Electronic invoice parameters** page (**Organization administration \> Setup \> EInvoice \> Electronic invoice parameters**). After you turn on this parameter, both Global CFDI and CFDI Normal documents are generated that include the following information:

- A list of related electronic invoices.
- A status of **Draft**. (This status is a new status that was introduced in version 10.0.2). An electronic invoice is automatically set to this status if a UUID isn't specified for all the related electronic invoices. The **Export/import electronic invoice process** periodic procedure skips all electronic invoices that have a status of **Draft**.
- An XML file that is generated, where the **CFDI relacionados** section contains the list of related electronic invoices. You can view the list of related electronic invoices by selecting **Inquiries \> Related e-invoices**. You can also manually add a new related electronic invoice on the same page.

The status of electronic invoices is automatically updated later, when all related electronic invoices get their UUIDs. To manually update the status of an electronic invoice, you can use the **Mark as ready** function. The status of the electronic invoice will be changed, and it will become available for export.

### Excluding customer orders from Global CFDI electronic invoices

To process customer orders as CFDI Normal electronic invoices in the same way that sales orders are processed in the **Accounts receivable** module, and to exclude those operations from the Global CFDI electronic invoices, turn on the **Exclude customer orders from CFDI Global** parameter on the **Retail** tab of the **Electronic invoice parameters** page (**Organization administration \> Setup \> EInvoice \> Electronic invoice parameters**). After you turn on this parameter, a separate electronic invoice is created based on each sale or return operation that is posted via a customer order at the POS.

The following customer order operations can cause a CFDI Normal electronic invoice to be posted:

- Customer order pickup
- Customer order return
- Hybrid customer order (For more information about this scenario, see [Hybrid customer orders](/dynamics365/unified-operations/retail/hybrid-customer-orders).)

When the **Exclude customer orders from CFDI Global** parameter is turned off, and no previous customer invoice was posted from the same customer order and processed as a separate electronic invoice (CFDI Normal), customer orders are included in Global CFDI electronic invoices. Otherwise, customer orders are processed as separate electronic invoices (CFDI Normal). Therefore, they are excluded from Global CFDI electronic invoices.

Customer order returns are processed in the same way (either CFDI Global or CFDI Normal) as the original sales operations.

### Limitations

Note the following limitations:

- All invoices from an original sales order are included in a return electronic invoice as the related CFDI documents.
- The scenario of a customer order return that involves an exchange is supported only for Global CFDI electronic invoices.
- Mixed transactions aren't supported for CFDI-global and CFDI-normal for commerce orders. Electronic invoices can't be created in the case of mixed orders (that is, orders that have positive and negative lines). We recommend that you mark the **Prohibit mixing sales and returns in one receipt** flag by going to **Retail and Commerce** \> **Channel setup** \> **POS setup** \> **POS profiles** \> **Functionality profiles**. When this restriction is enabled, the mixed lines are blocked in cash and carry sales.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
