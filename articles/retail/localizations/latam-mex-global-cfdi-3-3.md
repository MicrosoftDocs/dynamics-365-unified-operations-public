---
# required metadata

title: Global CFDI e-invoices for Mexico
description: This topic is a functionality overview for Global CFDI e-invoices for Mexico.
author: v-kikozl
manager: epopov
ms.date: 10/10/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Mexico
ms.search.industry: Retail
ms.author: v-kikozl
ms.search.scope: Retail
ms.search.validFrom: 2019-06-01
ms.dyn365.ops.version: 10.0.2

---

# Global CFDI electronic invoices for Mexico 

[!include[banner](../includes/banner.md)]

## Introduction

The Microsoft Dynamics 365 for Retail functionality for Mexico supports the Comprobantes fiscales digitales por internet (CFDI) format for the Mexican retail companies. See the [Electronic invoices (CFDI)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/latam-mex-cfdi-electronic-invoices) topic to find more general information about the CFDI electronic invoices. When a company closes the daily process, it is required to issue a Global CFDI to consolidate all receipts issued to the final consumers in a Global CFDI document, that indicates: 
  - A receipt number for each transaction registered during the period.
  - A corresponding amount for each transaction registered during the period.
    
## Processing of Global CFDI

The Global CFDI functionality allows to perform the following:
  - Create an electronic invoice based on the posted retail statement in the format of Global CFDI (layout 3.3). See the [CFDI layout version 3.3](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/latam-mex-cfdi-3-3) topic for more details about the layout.

  - Create and post electronic invoices based on posted retail statements, and send the .pdf and .xml files as an e-mail attachments to customers. The Global CFDI electronic invoices are generated, and then verified and certified by a digital signature service provider (PAC) in the same way as other CFDI documents. See the [Electronic invoices (CFDI)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/latam-mex-cfdi-electronic-invoices) and [Inquire and print an electronic invoice](https://docs.microsoft.com/en-us/dynamics365/unified-operations/financials/localizations/tasks/mx-00010-inquire-print-electronic-invoice) topics for more details.
  
User should complete the steps listed below to get a Global CFDI electronic invoice generated and submitted to PAC:

  1. As a preparation step the default values for some parameters that are used in the format of Global CFDI should be specified on the **Retail** tab of **Electronic invoice parameters** form.

  2. Close shift on POS.

  2. Run P-job in the disctribution schedule to transfer retail transactions from the channel database to the Retail Headquarters.

  3. Calculate and post a retail statement following the instructions provided in the [Create, calculate, and post a statement for a retail store](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/tasks/create-calculate-post-statement-retail-store) topic.

  4. Run the **Post CFDI – Electronic invoices** periodic operation to create Global CFDI electronic invoices based on a posted retail statement. User can select a statement number for this periodic operation. If a statement number was not selected, the system will create Global CFDI electronic invoices for all posted retail statements, that haven't been processed yet. 
  
  As a result of the **Post CFDI – Electronic invoices** periodic operation, two Global CFDI electronic invoices will be created - one of them collects all receipts related to sales operations, and the other - all receipts related to returns. An electronic invoice, which is related to returns, has the **Return** attribute marked as **Yes**. 
  
  You can view these electronic invoices on the **CFDI (electronic invoices)** form, that can be opened from the *_Retail > Inquiries and reports_* menu.

  All further workflow including communication with a service provider, printing form output and manual functions are the same as for the CFDI Normal electronic invoices.

  5. Run the **Export/import electronic invoice process** periodic operation to submit electonic invoices to PAC.

## Updates for the Global CFDI functionality

In the 10.0.2 monthly update the Global CFDI functionality was extended to support new requirements introduced in the second revision of the *_Global CFDI filling guide_*:

  - Generate a separate CFDI Normal electronic invoice based on sales or return operation registered on POS, when customer demanded it. 
  - Specify UUID of CFDI electonic invoices, which are related to the original sales operations, in a CFDI electronic invoice generated based on the returns. 

Also starting from the 10.0.2 monthly update the Global CFDI functionality supports additional scenarios:
  - [Return items across multiple customer orders and invoices](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/multireturn),
  - Customer order return with exchange, when a customer invoice includes lines with both positive and negative amounts. 

### Displaying related CFDI documents in a CFDI electronic invoice

New parameter **Specify related CFDI in returns** was added on the Retail tab of the **Electronic invoices parameters** form (*_Organization administration > Setup > EInvoice > Electronic invoice parameters_*). Enable this option to display UUID of original sales in CFDI electronic invoices for returns.

If the **Specify related CFDI in returns parameter** is enabled, then electronic invoices for returns, both CFDI Global and CFDI Normal, are generated:
  - With a list of related e-invoices, 
  - With the **Draft** status, which is a new status introduced within this update. An electonic invoice gets this status automatically, if not all related electronic invoices have UUID specified. The **Export/import electronic invoice process** periodic procedure skips all electronic invoices having the  **Draft** status. 
  - An xml-file is generated with the **CFDI relacionados** section, that contains the list of related electronic invoices. User can view the list of related electronic invoices using the **Inquiries - Related e-invoices** menu item. Also it is possible to add a new related electronic invoice manually on the same form. 

The status of electronic invoices is updated automatically later, when all related electronic invoices get their UUIDs. To update the status of an electronic invoice manually, you can use a new function **Mark as ready**. As a result, the status of an electronic invoice will be changed, and it will become available for export. 

### Excluding customer orders from Global CFDI electronic invoices

New parameter **Exclude customer orders from CFDI Global** was added on the Retail tab of the **Electronic invoices parameters** form (*_Organization administration > Setup > EInvoice > Electronic invoice parameters_*). Enable this option to process customer orders as CFDI Normal electonic invoices in the same way as sales orders in the Accounts Receivable module, and exclude such operations from the Global CFDI electronic invoices. 

If the **Exclude customer orders from CFDI Global** parameter is enabled, then a separate electronic invoice will be created based on each sale or return operation posted via customer order on POS. You can find more information about the functionality of customer orders in the [Customer orders in Retail Modern POS (MPOS)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/customer-orders-overview) topic. 

The customer order operations, that could lead to posting a CFDI Normal electronic invoice:
  - Customer order pick up, 
  - Customer order return, 
  - Hybrid customer order. For more details about this scenario see the [Hybrid customer orders](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/hybrid-customer-orders) topic. 

Customer orders are included in Global CFDI electronic invoices, when the **Exclude customer orders from CFDI Global**  parameter is disabled, and there is no any previous customer invoice, that was posted from the same customer order and processed as a separate electonic invoice (CFDI Normal). Otherwise, customer orders are processed as separate electronic invoices (CFDI Normal), and therefore, they are excluded from Global CFDI electronic invoices.

Customer order returns are processed in the same way (either CFDI Global or CFDI Normal, as the original sales operations. 

#### Limitations of the feature 

  - All invoices from an original sales order are included in a return electronic invoice as the related CFDI documents.
  - The scenario of a customer order return with exchange is supported for the Global CFDI electronic invoices only.
