# **Formula Designer**

TDS is calculated based on the formula defined for each TDS tax code in the TDS group that is attached to the transaction. First, you must do the basic setup that is required for TDS. Set up TDS component groups in the **Withholding** **tax** **component** **groups** form. Set up TDS components in the **Withholding** **tax** **components** form and attach TDS component group to the TDS components. Set up TDS tax codes in the **Withholding** **tax** **codes** form and attach TDS components to the tax codes. Set up TDS tax group in the **Withholding** **tax** **groups** form, attach TDS tax codes to the tax group, and define the formula using the **Formula** **designer** form. 

**Example**:

The TDS group Rent is attached to a purchase invoice created for Vendor A. The invoice amount is 100000. Refer to the following table to view the TDS calculation for the invoice.

| TDS  Group                                                   | TDS tax codes attached to the TDS group | Value              | Taxable basis  (Formula designer) | Calculation expression  (Formula designer) | Base amount | Calculated TDS amount |
| ------------------------------------------------------------ | --------------------------------------- | ------------------ | --------------------------------- | :----------------------------------------: | ----------- | --------------------- |
| Rent                                                         | TDS  (TDS component-TDS)                | 10%                | Gross amount                      |                                            | 100000      | 10000                 |
| Surcharge  (TDS component-Surcharge)                         | 10%                                     | Excl. gross amount | +TDS                              |                   10000                    | 1000        |                       |
| PE-Cess  (TDS component- PE-Cess)                            | 2%                                      | Excl. gross amount | +TDS+Surcharge                    |                   11000                    | 220         |                       |
| SHE Cess  (TDS component- SHE Cess)                          | 1%                                      | Excl. gross amount | +TDS+Surcharge                    |                   11000                    | 110         |                       |
| **Total** **TDS**  **calculated** **for** **the** **invoice** | **11330**                               |                    |                                   |                                            |             |                       |

 

The voucher entries are created as follows:

| Account           | Debit  | Credit |
| ----------------- | ------ | ------ |
| Rent              | 100000 |        |
| Vendor A          |        | 100000 |
| Vendor A          | 11330  |        |
| TDS payable       |        | 10000  |
| Surcharge payable |        | 1000   |
| PE-Cess payable   |        | 220    |
| SHE Cess payable  |        | 110    |
