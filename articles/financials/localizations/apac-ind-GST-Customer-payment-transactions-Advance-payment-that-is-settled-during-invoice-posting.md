

# Advance payment that is settled during invoice posting

This section provides information about tax posted on the customer advance payment and selected for the settlement, while posting the customer invoice.
The following tables shows the tax entries that are generated for the invoice when an advance payment is settled in various scenarios.

| Transaction details | Example                                                 | Tax entries that are generated during settlement             |
| ------------------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| Invoice = Payment   | Invoice amount: 12,000.00<br/>Payment amount: 12,000.00 | Tax on the invoice is posted.<br/>Tax on the payment is reversed to prevent a double entry in the related voucher.<br/>IGST payable account Cr. 2,000.00<br/>**Related voucher**<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00 |
| Invoice < Payment   | Invoice amount: 6,000.00<br/>Payment amount: 12,000.00  | Tax on the invoice is posted.<br/>Tax on the payment is reversed to the extent of the invoice<br/>amount in the related voucher.<br/>IGST payable account Cr. 1,000.00<br/>**Related voucher**<br/>IGST interim payable account Cr. 1,000.00<br/>IGST payable account Dr. 1,000.00 |
| Invoice > Payment   | Invoice amount: 24,000.00<br/>Payment amount: 12,000.00 | Tax on the invoice is posted.<br/>Tax on the payment is reversed to the extent of the payment<br/>amount in the related voucher<br/>IGST payable account Cr. 4,000.00<br/>**Related voucher**<br/>IGST interim payable account Cr. 2,000.00<br/>IGST payable account Dr. 2,000.00 |





