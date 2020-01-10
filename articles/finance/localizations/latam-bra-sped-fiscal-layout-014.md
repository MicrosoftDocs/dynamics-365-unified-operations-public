---
# required metadata

title: SPED fiscal ICMS-IPI Layout 014
description: This topic explains how to set up and generate Sped fiscal statement layout 014 applicable.
author: sndray
manager: AnnBe
ms.date: 01/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2020-01-15
ms.dyn365.ops.version: 10.0.9

---

# SPED fiscal ICMS-IPI Layout 014 

[!include [banner](../includes/banner.md)]


This topic provides information about how to set up and generate the Sped fiscal statement layout 014 which is applicable as of January 2020 under the practical guide, **EFD-ICMS/IPI – version 3.0.3**.

To view the new layout, go to **Fiscal books** > **Setup** > **Tax statements parameters** > **Sped fiscal** > **Sped fiscal parameters** > **Layout version**.

## Record 0002: Classification of fiscal establishment

This record is generated when the field **IND_ATIV** of record 0000 is equal to "0" and the classification of the fiscal establishment is configured and assigned. This can be completed by going to **Fiscal books** > **Setup** > **Tax statements parameters** > **Sped fiscal** > **Sped fiscal parameters** > **Classification**. 

The classification is assigned to the related fiscal establishment. When more than one type of classification applies, select the classification that is most relevant in the establishment.

## Record C500: Incoming fiscal documents
This record is generated for Incoming fiscal document models, 6, 66, 29, and 28. The following new fields are included as part of new layout

| #  | Field        | Description                                                                                                                            |
|----|--------------|----------------------------------------------------------------------------------------------------------------------------------------|
| 28 | CHV_DOCe     | Access key of the fiscal document then the fiscal document is equal to 66. Otherwise, the field is blank.                              |
| 29 | FIN_DOCe     | Fixed as one (1) only when a fiscal document is equal to 66. Otherwise, the field is blank.                                            |
| 30 | CHV_DOCe_REF | The access key for the referenced fiscal document if it exists when the fiscal document is equal to 66. Otherwise, the field is blank. |
| 31 | IND_DEST     | Fixed as one (1) because the fiscal establishment in the ICMS taxpayer.                                                                |
| 32 | COD_MUN_DEST | The IBGE code of the fiscal establishment.                                                                                             |
| 33 | COD_CTA      | Expense or Asset main account. A Financial ledger dimension.                                                                           |

## Complement and compensation of ICMS-ST tax
The tax authority has introduced records C180, C185, 1010, and 1250 which detail the operations that are subject to ICMS-ST tax when the company applies the complement and compensation of ICMS-ST tax. Generating these records will be addressed by each state.


### Prerequisites

Before you enable generating these records, you must enable the presumed tax calculation. To do this, go to **Organization administration** > **Setup** > **Brazilian parameters** > **Fiscal document** and enable the following:
	
- ICMS- ST presumed tax
- ICMS-ST presumed tax in fiscal books 

To generate these records, complete the followign steps to set up the rule that will allow the records to be generated. The rule must be set up for each state.

1. Go to  **Fiscal books** > **Setup** > **Fiscal books parameters per state**.
2. Select the related state. For example, **SP**.
3. Enable record C180 and C185 as **Yes**. Records H030 with MOT_INV = 06 of record H005 and 1010, 1250, 1255 are also generated. 
4. Select the method of calculation in **SPED presumed tax calculation algorithm**. The amounts calculated in the presumed tax process will be reported in record C185.
	
![SpedFiscal Setup](media/bra-sped-Fiscal014-Setup.png)	
  
 ### Table 5.7 - Reason code table for complement and restitution

Table 5.7 represents the classification of complement and compensation of the ICMS-ST amounts. This table is implemented by each state and configured in **Fiscal books** > **Setup** > **Reason code for complement and restitution**.

![bra-sped-fiscal014-table57-setup](media/bra-sped-fiscal014-table57-setup.png)

After you complete the configuration of the reason code table, you need to set up the determination of reason code table 5.2 in **Fiscal books** > **Setup** > **Table 5.7 determination** by using the following criteria:

- Item code 
- CFOP code
- Taxation code

![bra-sped-fiscal014-table57-determination-setup](media/bra-sped-fiscal014-table57-determination-setup.png)

### Record C180
This new record introduces complementary information of incoming fiscal document models 01, 1B, 04. and 55 for transactions with the ICMS-ST tax transaction. This record is generated based on the following criteria:

- Fiscal books parameters per state, **Enable record C180 and C185** = Yes 
- Fiscal document tax transactions have taxation code = 10, 30, 60, 70

| #  | Field                   | Description                                                                                                                                                                                                                                            |
|----|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | REG                     | Fixed text containing C180.                                                                                                                                                                                                                            |
| 2  | COD_RESP_RET            | The code that indicates the person responsible for the withholding of ICMS-ST:1-Direct sender, 2-Indirect sender, and 3-Own declarant. This classification is available on the fiscal document line.                                                   |
| 3  | QUANT_CONV              | The quantity of the incoming fiscal document.                                                                                                                                                                                                          |
| 4  | UNID                    | The unit of measure of QUANT_CONV.                                                                                                                                                                                                                     |
| 5  | VL_UNIT_CONV            | Line amount per unit considering the unit of measure used to inform the field QUANT_CONV of incoming fiscal document.                                                                                                                                  |
| 6  | VL_UNIT_ICMS_OP_CONV    | ICMS amount of own operation that the informant would be entitled to recover (credit) considering the unit used to inform the QUANT_CONV field. This is the ICMS amount per unit. The ICMS tax transaction must be defined with the internal tax rate. |
| 7  | VL_UNIT_BC_ICMS_ST_CONV | Base Amount of the ICMS-ST per unit considering the unit used to inform the QUANT_CONT field.                                                                                                                                                          |
| 8  | VL_UNIT_ICMS_ST_CONV    | ICMS-ST or ICMS-ST presumed tax including FCP considering the unit used to report the QUANT_CONV.                                                                                                                                                      |
| 9  | VL_UNIT_FCP_ST_CONV     | ICMS-ST or ICMS-ST presumed FCP amount per unit.                                                                                                                                                                                                       |
| 10 | COD_DA                  | Type of collection document: 0-State document of collection or 1-GNRE. This classification is available on the fiscal document line.                                                                                                                   |
| 11 | NUM_DA                  | Number of the state collection document. This classification is available in the fiscal document line.                                                                                                                                                 |

### Record C185
This new record introduces complementary information of outgoing fiscal document models 01, 1B, 04, and 55 for transactions with the ICMS-ST tax transaction. This record is generated based on the following criteria:

- Fiscal books parameters per state, **Enable record C180 and C185** = **Yes** 
- Fiscal document tax transactions taxation code = 10, 30, 60, or 70

| #  | Field                            | Description                                                                                                                                        |
|----|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | REG                              | Fixed text containing **C185**.                                                                                                                    |
| 2  | NUM_ITEM                         | The sequence number of the fiscal document item line.                                                                                              |
| 3  | COD_ITEM                         | The item code of the fiscal document line.                                                                                                         |
| 4  | CST_ICMS                         | The ICMS taxation code.                                                                                                                            |
| 5  | CFOP                             | The CFOP.                                                                                                                                          |
| 6  | COD_MOT_REST_COMPL               | The reason code for restitution or complement per Table 5.7.                                                                                       |
| 7  | QUANT_CONV                       | The item quantity.                                                                                                                                 |
| 8  | UNID                             | The unit of measure.                                                                                                                               |
| 9  | VL_UNIT_CONV                     | The amount of goods per unit.                                                                                                                      |
| 10 | VL_UNIT_ICMS_NA_OPERACAO_CONV    | The ICMS amount per unit.                                                                                                                          |
| 11 | VL_UNIT_ICMS_OP_CONV             | The ICMS-ST presumed amount per unit from the incoming fiscal document.                                                                            |
| 12 | VL_UNIT_ICMS_OP_ESTOQUE_CONV     | The average ICMS tax amount per unit in inventory, as the unit is used to inform the field, **QUANT_CONV**.                                        |
| 13 | VL_UNIT_ICMS_ST_ESTOQUE_CONV     | The average ICMS-ST tax amount including FCP ST, of the goods in stock as the unit is used to inform the field, **QUANT_CONV**.                    |
| 14 | VL_UNIT_FCP_ICMS_ST_ESTOQUE_CONV | The average of the OCMS ST FCP per unit of the goods in stock, as the unit is used to inform the field, **QUANT_CONV**.                            |
| 15 | VL_UNIT_ICMS_ST_CONV_REST        | The ICMS-ST amount, including FCP ST, to be refunded or reimbursed.                                                                                |
| 16 | VL_UNIT_FCP_ST_CONV_REST         | The ICMS-ST FCP amount that composes the field, **VL_UNIT_ICMS_ST_CONV_REST** as the unit is used to inform the field, **QUANT_CONV**.             |
| 17 | VL_UNIT_ICMS_ST_CONV_COMPL       | The ICMS amount complement, including FCP ST, as the unit is used to inform the field, **QUANT_CONV**.                                             |
| 18 | VL_UNIT_FCP_ST_CONV_COMPL        | The ICMS-ST FCP amount that composes the field, **VL_UNIT_ICMS_ST_CONV_COMPL** as the unit is used to inform what is in the field, **QUANT_CONV**. |

> [!NOTE]
> The amounts from field 10 to field 18 are recovered from the ICMS-ST presumed tax calculation in the ICMS-ST tax assessment.

### Record 1010

| #  | Field                       | Description                                                                                                                                                                                            |
|----|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 14 | IND_REST_RESSARC_COMPL_ICMS | This field is filled with **S** when the generated records, C180 and C185 are enabled in the Fiscal books parameters per state. When you enable records C180 and C185, record 1250 is no longer empty. |

### Record 1250

Record 1250 is generated to consolidate information about the balance of complement or restitution of the ICMS and the ICMS-ST. 

<table>
  <tr>
    <th>#</th>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td>REG</td>
    <td>Fixed text that contains **1250**.</td>
  </tr>
  <tr>
    <td>2</td>
    <td>VL_CREDITO_ICMS_OP</td>
    <td>The sum of records 1255 in field, **VL_CREDITO_ICMS_OP_MOT**.</td>
  </tr>
  <tr>
    <td>3</td>
    <td>VL_ICMS_ST_REST</td>
    <td>The sum of records 1255 in field **VL_ICMS_ST_REST_MOT**.</td>
  </tr>
  <tr>
    <td>4</td>
    <td>VL_FCP_ST_REST</td>
    <td>The sum of records 1255 in the following fields:<table>
  <tr>
    <th>#</th>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td>REG</td>
    <td>Fixed text that contains **1250**.</td>
  </tr>
  <tr>
    <td>2</td>
    <td>VL_CREDITO_ICMS_OP</td>
    <td>The sum of record 1255 in the field **VL_CREDITO_ICMS_OP_MOT**.</td>
  </tr>
  <tr>
    <td>3</td>
    <td>VL_ICMS_ST_REST</td>
    <td>The sum of record 1255 in field **VL_ICMS_ST_REST_MOT**.</td>
  </tr>
  <tr>
    <td>4</td>
    <td>VL_FCP_ST_REST</td>
    <td>The sum of record 1255 in field **VL_ICMS_FCP_REST_MOT**.</td>
  </tr>
  <tr>
    <td>5</td>
    <td>VL_ICMS_ST_COMPL</td>
    <td>The sum of record 1255 in field **VL_ICMS_ST_COMPL_MOT**.</td>
  </tr>
  <tr>
    <td>6</td>
    <td>VL_FCP_ST_COMPL</td>
    <td>The sum of record 1255 in field **VL_FCP_ST_COMPL_MOT**.</td>
  </tr>
</table>L_ICMS_FCP_REST_MOT</td>
  </tr>
  <tr>
    <td>5</td>
    <td>VL_ICMS_ST_COMPL</td>
    <td>The sum of record 1255 in field **VL_ICMS_ST_COMPL_MOT**.</td>
  </tr>
  <tr>
    <td>6</td>
    <td>VL_FCP_ST_COMPL</td>
    <td>The sum of record 1255 in field **VL_FCP_ST_COMPL_MOT**.</td>
  </tr>
</table>

### Record 1255

Record 1255 is generated to consolidate information about the balance of complement or restitution of ICMS by reason code (table 5.7). 

| # | Field                  | Description                                                                                |
|---|------------------------|--------------------------------------------------------------------------------------------|
| 1 | REG                    | Fixed text of **1255**.                                                                    |
| 2 | COD_MOT_REST_COMPL     | The reason code for restitution or complement for Table 5.7.                               |
| 3 | VL_CREDITO_ICMS_OP_MOT | The sum of record C185 in field **VL_UNIT_ICMS_OP_CONV** x ** QUANT_CONV**.      |
| 4 | VL_ICMS_ST_REST_MOT    | The sum of record C185 in field **VL_UNIT_ICMS_ST_CONV_REST** x **QUANT_CONV**.  |
| 5 | VL_FCP_ST_REST_MOT     | The sum of record C185 in field **VL_UNIT_FCP_ST_CONV_REST** x **QUANT_CONV**.   |
| 6 | VL_ICMS_ST_COMPL_MOT   | The sum of record C185 in field **VL_UNIT_ICMS_ST_CONV_COMPL** x **QUANT_CONV**. |
| 7 | VL_FCP_ST_COMPL_MOT    | The sum of record C185 in field **VL_UNIT_FCP_ST_CONV_COMPL** x **QUANT_CONV**.  |

### Record H030 
Record H030 is generated together with H005 and H010 when the control of compensation or restitution of the ICMS-ST tax was enabled  by setting **Enable record C180 and C185** to **Yes** in the Fiscal books parameters per state.
The record H005 is generated with field **MOT_INV** equal to six (6). The record H010 is generated in the same way when the field **MOT_INV** is not equal to six (6). 

| # | Field         | Description                                                   |
|---|---------------|---------------------------------------------------------------|
| 1 | REG           | Fixed text, **H030**.                                       |
| 2 | VL_ICMS_OP    | The average unit amount of the ICMS operations.               |
| 3 | VL_BC_ICMS_ST | The Average unit amount of the ICMS-ST base.                  |
| 4 | VL_ICMS_ST    | The average unit amount of the ISMC-ST tax including the FCP. |
| 5 | VL_FCP        | The average unit amount of the FCP of ICMS-ST tax.            |

## Record G130
Record G130 is generated to identify the fiscal document of CIAP operations. A new field has been included as part of the new layout.

| # | Field  | Description                                                                                                |
|---|--------|------------------------------------------------------------------------------------------------------------|
| 9 | NUM_DA | The number of the state collection document. This classification is available in the fiscal document line. |

## Record G140 
Record G140 is generated to identify the fiscal document of CIAP operations. New fields have been included as part of the new layout.

| # | Field                | Description                                                                                                    |
|---|----------------------|----------------------------------------------------------------------------------------------------------------|
| 4 | QTDE                 | The quantity that was applied to the item. This is expressed in the same unit as the incoming fiscal document. |
| 5 | UNID                 | The unit of measure of the incoming fiscal document.                                                           |
| 6 | VL_ICMS_OP_APLICADO  | The ICMS amount of the incoming fiscal document. The ICMS column from the CIAP assessment.                     |
| 7 | VL_ICMS_ST_APLICADO  | The ICMS-ST amount of the incoming fiscal document. The ICMS column from the CIAP assessment.                  |
| 8 | VL_ICMS_FRT_APLICADO | The ICMS amount of the incoming fiscal document. The ICMS on the freight column from the CIAP assessment.      |
| 9 | VL_ICMS_DIF_APLICADO | The ICMS-DIF amount of the incoming fiscal document. The ICMS-DIF column from the CIAP assessment.             |

