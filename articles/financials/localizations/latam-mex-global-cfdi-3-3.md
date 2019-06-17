In Finance and Operations monthly update version 10.0.2, the Global CFDI functionality was extended to support new requirements introduced in the second revision of the *_Global CFDI filling guide_*. Starting in update version 10.0.2, you can do the following.

  - Generate a separate CFDI Normal electronic invoice based on sales or return operation registered on POS, when a customer demands it. 
  
  In that case a sale or return operation should be registered as a customer order. You can find more information about the functionality of customer orders in [Customer orders in Retail Modern POS (MPOS)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/customer-orders-overview). 
  
  - Specify UUID of CFDI electonic invoices, which are related to the original sales operations, in a CFDI electronic invoice generated based on the returns. 

Also starting from the 10.0.2 monthly update, the Global CFDI functionality supports the following additional scenarios.

  - [Return items across multiple customer orders and invoices](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/multireturn).
  - Customer order return with an exchange, when a customer invoice includes lines with both positive and negative amounts. 

### Displaying related CFDI documents in a CFDI electronic invoice

The **Specify related CFDI in returns** parameter was added on the **Retail** tab of the **Electronic invoices parameters** page (**Organization administration > Setup > EInvoice > Electronic invoice parameters**). Enable this option to display UUID of original sales in CFDI electronic invoices for returns.

If the **Specify related CFDI in returns parameter** is enabled, then electronic invoices for returns, both CFDI Global and CFDI Normal, are generated with the following.

  - A list of related e-invoices.
  
  - The **Draft** status (a new status introduced within this update). An electonic invoice gets this status automatically, if not all of the related electronic invoices have UUID specified. The **Export/import electronic invoice process** periodic procedure skips all electronic invoices having the  **Draft** status. 
  
  - An xml-file that is generated with the **CFDI relacionados** section that contains the list of related electronic invoices. You can view the list of related electronic invoices using the **Inquiries - Related e-invoices** menu item. It is also possible to add a new related electronic invoice manually on the same form. 

The status of electronic invoices is updated automatically later, when all related electronic invoices get their UUIDs. To update the status of an electronic invoice manually, you can use the  **Mark as ready** function. As a result, the status of an electronic invoice will be changed, and it will become available for export. 

### Excluding customer orders from Global CFDI electronic invoices

Enable the **Exclude customer orders from CFDI Global** option on the **Retail** tab of the **Electronic invoices parameters** page (**Organization administration > Setup > EInvoice > Electronic invoice parameters**) to process customer orders as CFDI Normal electonic invoices in the same way as sales orders in the Accounts Receivable module, and exclude such operations from the Global CFDI electronic invoices. 

If the **Exclude customer orders from CFDI Global** parameter is enabled, then a separate electronic invoice will be created based on each sale or return operation posted via a customer order on POS. 

The customer order operations that could lead to posting a CFDI Normal electronic invoice are as follows.

  - Customer order pick up. 
  
  - Customer order return. 
  
  - Hybrid customer order. For more details about this scenario see [Hybrid customer orders](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/hybrid-customer-orders). 

Customer orders are included in Global CFDI electronic invoices when the **Exclude customer orders from CFDI Global**  parameter is disabled and there is no any previous customer invoice that was posted from the same customer order and processed as a separate electonic invoice (CFDI Normal). Otherwise, customer orders are processed as separate electronic invoices (CFDI Normal), and are therefore excluded from Global CFDI electronic invoices.

Customer order returns are processed in the same way (either CFDI Global or CFDI Normal), as the original sales operations. 

#### Limitations of the feature 

The following limitations should be noted.

  - All invoices from an original sales order are included in a return electronic invoice as the related CFDI documents.
  
  - The scenario of a customer order return with exchange is supported for the Global CFDI electronic invoices only.
