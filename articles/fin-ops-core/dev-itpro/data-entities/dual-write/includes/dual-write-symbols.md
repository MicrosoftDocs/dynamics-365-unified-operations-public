## Mapping tables

### Mapping types

There are several different mapping types. The following table explains the symbols used in the template tables.

| Symbol | Description |
|--------|-------------|
| >  | One-way |
| >> | One-way, and data is transformed in the process. |
| =  | Bidirectional |
| >< | Bidirectional, and data is transformed in the process. |
| << | One-way, and data is transformed in the process. |

### Filters

The source filter and reverse source filter determine which rows are synchronized.

### Default values

If a synchronized field does not exist in either the finance and operations table or the customer engagement table, then a default value is assigned in the synchronized table. In some cases, the default value is an integer that is a lookup to an attribute value in Dataverse. For example, in the **Contact** table, the default value for [address1AddressTypeCode](/common-data-model/schema/core/applicationcommon/foundationcommon/contact#address1AddressTypeCode) is **3** (**Primary address**).
