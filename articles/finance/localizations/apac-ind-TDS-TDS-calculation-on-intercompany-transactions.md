# TDS calculation on intercompany transactions

TDS is calculated on intercompany transactions. TDS is calculated in the following phases in intercompany transactions:

When an intercompany purchase order or sales order is created, the default TDS group defined for the customer or vendor is used to calculate TDS. TDS amount is posted to the recoverable or payable accounts after the invoice is posted.

1. A sales order or purchase order is created automatically in the intercompany for the original purchase order or sales order. The default TDS group is also displayed in the automatically created order to calculate TDS and can be modified. If the net invoice amount after deducting the TDS amount of the automatically created order does not match the net invoice amount of the original order, the invoice cannot be posted.

   For example, a sales invoice is created for 50000. A TDS group-10% is attached to the invoice. The posted invoice amount is 45000 and the posted TDS amount is 5000 for the sales invoice. A purchase order is automatically created for the sales order in the intercompany with the TDS group-10%. If you change the TDS group to 15%, you cannot post the invoice because the net invoice amount of the automatically created order does not match the net invoice amount of the original order.

2. When a payment journal is created for an intercompany invoice, a payment journal is posted automatically in the intercompany. If the net payment amount of the automatically created payment journal does not match the net payment amount of the original payment journal, the automatically created payment journal cannot be posted.