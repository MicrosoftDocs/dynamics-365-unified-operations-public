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

If a synchronized field does not exist in either the Finance and Operations table or the other Dynamics 365 table, then a default value is assigned in the synchronized table. In some cases, the default value is an integer that is a lookup to an attribute value in the Common Data Model. For example, in the Contacts table of the Common Data Model, the default value of [**address1_addresstypecode**](../data-entities/dual-write/customer-mapping.md#customers-v3-to-contacts) is **3**. In the Common Data Model, for [address1AddressTypeCode](https://docs.microsoft.com/common-data-model/schema/core/applicationcommon/foundationcommon/contact#address1AddressTypeCode) the value of **3** is **Primary address**. 
