## Sales invoice headers V2 to invoices

This template synchronizes data between Finance and Operations apps and Common Data Service.

Source filter: (SalesOrderNumber != "")

Finance and Operations apps | Map type | model-driven apps in Dynamics 365 | Default value
---|---|---|---
none | >> | ispricelocked | False
none | >> | statuscode | 4
CONTACTPERSONID | >> | msdyn_contactperson.msdyn_contactpersonid | 
CURRENCYCODE | >> | transactioncurrencyid.isocurrencycode | 
CUSTOMERSORDERREFERENCE | >> | description | 
INVOICEADDRESSCITY | >> | billto_city | 
INVOICEADDRESSCOUNTRYREGIONISOCODE | >> | billto_country | 
INVOICEADDRESSSTATE | >> | billto_stateorprovince | 
INVOICEADDRESSSTREET | >> | billto_line1 | 
INVOICEADDRESSSTREETNUMBER | >> | billto_line2 | 
INVOICEADDRESSZIPCODE | >> | billto_postalcode | 
INVOICECUSTOMERACCOUNTNUMBER | >> | customerid.Account(accountnumber).Contact(msdyn_contactpersonid) | 
INVOICEDATE | >> | msdyn_invoicedate | 
INVOICENUMBER | >> | msdyn_invoicenumber | 
LEDGERVOUCHER | >> | msdyn_ledgervoucher | 
PAYMENTTERMSNAME | >> | msdyn_paymentterms.msdyn_name | 
SALESORDERNUMBER | >> | salesorderid.msdyn_salesordernumber | 
TOTALCHARGEAMOUNT | >> | freightamount | 
TOTALDISCOUNTAMOUNT | >> | totaldiscountamount | 
TOTALDISCOUNTCUSTOMERGROUPCODE | >> | discountamount | 
TOTALINVOICEAMOUNT | >> | totalamount | 
TOTALTAXAMOUNT | >> | totaltax | 
