#SPED Fiscal ICMS-IPI - Layout 014

This topic explains how to set up and generate Sped fiscal statement layout 014 applicable from January 2020 under the practical guide **EFD-ICMS/IPI – version 3.0.3**

##Record 0000 - Opening record

New layout 014.(1.13) has been introduced in **Fiscal books > Setup > Tax statements parameters > Sped fiscal > Sped fiscal parameters > Layout version**

##Record 0002 - Classification of fiscal establishment

This record is generated when the field **IND_ATIV** of record 0000 is equal to "0" and the classification of fiscal establishment is configured in **Fiscal books > Setup > Tax statements parameters > Sped fiscal > Sped fiscal parameters > Classification**. 

Assign classification in the related fiscal establishment and when applies more than one type of classification, please inform the classification that is most relevant in the establishment.


##Record C500. Incoming fiscal documents
This record is generated for Incoming fiscal documents model **6, 66, 29, 28**. The following new fields are included as part of new layout

<table>
  <tr>
    <th>#</th>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>28</td>
    <td>CHV_DOCe</td>
    <td>Access key of fiscal document when fiscal document = 66, otherwise the field is presented in blank</td>
  </tr>
  <tr>
    <td>29</td>
    <td>FIN_DOCe</td>
    <td>Fixed as 1 only for fiscal document = 66 otherwise the field is presented in blank</td>
  </tr>
  <tr>
    <td>30</td>
    <td>CHV_DOCe_REF</td>
    <td>Access key of referenced fiscal document if exist. When fiscal document = 66, otherwise the field is presented in blank</td>
  </tr>
  <tr>
    <td>31</td>
    <td>IND_DEST</td>
    <td>Fixed as 1 since the fiscal establishment is ICMS taxpayer.</td>
  </tr>
  <tr>
    <td>32</td>
    <td>COD_MUN_DEST</td>
    <td>IBGE code of fiscal establishment.</td>
  </tr>
  <tr>
    <td>33</td>
    <td>COD_CTA</td>
    <td>Expense or Asset main account. (Financial ledger dimension)</td>
  </tr>
</table>

##Complement and compensation for ICMS-ST
The tax authority has introduced the generation of records C180, C185, 1010 and 1250 to detail the operations that that are subject to ICMS-ST tax when the company applies the complement and compensation of ICMS-ST tax. The generation of these record will be addressed by each state


###Prerequisites

Before you enable the generation of these records , enable the Presumed tax calculation in **Organization administration > Setup > Brazilian parameters > Fiscal document**
	- ICMS- ST presumed tax
	- ICMS-ST presumed tax in fiscal books 


In order to generate these records, you need to setup per state the rule that will allow the generation of these records:
	1. Go to  **Fiscal books > Setup > Fiscal books parameters per state**
	2. Select the related State, for example SP
	3. Mark as **Yes** 
	4. Select the **SPED presumed tax calculation algorithm**  since the amounts calculated will be reported in record C185.
	
![SpedFiscal Setup](media/bra-sped-Fiscal014-Setup.png)	
  
 ###Table 5.7 . Reason code table for complement and restitution

The table 5.7 represents the classification of complement and compensation of ICMS-ST amounts. This table is implemented by each state and configured in **Fiscal books > Setup > Reason code for complement and restitution**

![bra-sped-fiscal014-table57-setup](media/bra-sped-fiscal014-table57-setup.png)

After to complete the configuration of reason code table you need to setup the determination of reason code table 5.2 in **Fiscal books > Setup > Table 5.7 determination** by using the following criteria's
	- Item code 
	- CFOP code
	- Taxation code

![bra-sped-fiscal014-table57-determination-setup](media/bra-sped-fiscal014-table57-determination-setup.png)

###Record C180
This new record introduces complementary information of incoming fiscal document model 01, 1B, 04 and 55 for transactions with ICMS-ST tax transaction. This record is generated under the following criteria:
	- Fiscal books parameters per state, **Enable record C180 and C185** = Yes, 
	- Fiscal document tax transactions have taxation code = 10, 30, 60, 70


<table>
  <tr>
    <th>#</th>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td>REG</td>
    <td>Fixed text containing C180</td>
  </tr>
  <tr>
    <td>2</td>
    <td>COD_RESP_RET</td>
    <td>Code that indicates the person responsible for the withholding of ICMS-ST: 1-Direct Sender, 2-Indirect Sender and 3-Own declarant.This classification is available in the fiscal document line. 
  </tr>
  <tr>
    <td>3</td>
    <td>QUANT_CONV</td>
    <td>The quantity of incoming fiscal document</td>
  </tr>
  <tr>
    <td>4</td>
    <td>UNID</td>
    <td>Unit of measure of QUANT_CONV</td>
  </tr>
  <tr>
    <td>5</td>
    <td>VL_UNIT_CONV</td>
    <td>Line amount per unit considering the unit of measure  used to inform the field QUANT_CONV of incoming fiscal document</td>
  </tr>
  <tr>
    <td>6</td>
    <td>VL_UNIT_ICMS_OP_CONV</td>
    <td>ICMS amount of own operation that the informant would be entitled to recover (credit) considering unit used to inform the QUANT_CONV field. This is the ICMS amount per unit. The ICMS tax transaction must be defined with the internal tax rate.</td>
  </tr>
  <tr>
    <td>7</td>
    <td>VL_UNIT_BC_ICMS_ST_CONV</td>
    <td>Base Amount of ICMS-ST per unitconsidering the unit used to inform the QUANT_CONV field.</td>
  </tr>
  <tr>
    <td>8</td>
    <td>VL_UNIT_ICMS_ST_CONV</td>
    <td>ICMS-ST or ICMS-ST presumed tax including FCP considering the unit used to report the QUANT_CONV.</td>
  </tr>
  <tr>
    <td>9</td>
    <td>VL_UNIT_FCP_ST_CONV</td>
    <td>ICMS-ST or ICMS-ST presumed FCP amount per unit</td>
  </tr>
  <tr>
    <td>10</td>
    <td>COD-DA</td>
    <td>Type of collection document: 0-State document of collection or 1-GNRE. This classification is available in the fiscal document line.</td>
  </tr>
  <tr>
    <td>11</td>
    <td>NUM_DA</td>
    <td>Number of the state collection document. This classification is available in the fiscal document line.</td>
  </tr>
</table>

###Record C185
This new record introduces complementary information of outgoing fiscal document model 01, 1B, 04 and 55 for transactions with ICMS-ST tax transaction. This record is generated under the following criteria:
	- Fiscal books parameters per state, **Enable record C180 and C185** = Yes, 
	- Fiscal document tax transactions have taxation code = 10, 30, 60, 70

<table>
  <tr>
    <th>#</th>
    <th>Field</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td>REG</td>
    <td>Fixed text containing "C185"</td>
  </tr>
  <tr>
    <td>2</td>
    <td>NUM_ITEM</td>
    <td>Sequence number of fiscal document item line</td>
  </tr>
  <tr>
    <td>3</td>
    <td>COD_ITEM</td>
    <td>Item code of fiscal document line</td>
  </tr>
  <tr>
    <td>4</td>
    <td>CST_ICMS</td>
    <td>ICMS Taxation code</td>
  </tr>
  <tr>
    <td>5</td>
    <td>CFOP</td>
    <td>CFOP</td>
  </tr>
  <tr>
    <td>6</td>
    <td>COD_MOT_REST_COMPL</td>
    <td>Reason code for restitution or complement as per Table 5.7. For more information<br>&nbsp;&nbsp;about how is determined this classification see….</td>
  </tr>
  <tr>
    <td>7</td>
    <td>QUANT_CONV</td>
    <td>Item quantity</td>
  </tr>
  <tr>
    <td>8</td>
    <td>UNID</td>
    <td>Unit of measure</td>
  </tr>
  <tr>
    <td>9</td>
    <td>VL_UNIT_CONV</td>
    <td>Amountof goods per unit</td>
  </tr>
  <tr>
    <td>10</td>
    <td>VL_UNIT_ICMS_NA_OPERACAO_CONV</td>
    <td>ICMS amount per unit</td>
  </tr>
  <tr>
    <td>11</td>
    <td>VL_UNIT_ICMS_OP_CONV</td>
    <td>ICMS-ST presumed amount (from incoming fiscal document) per unit</td>
  </tr>
  <tr>
    <td>12</td>
    <td>VL_UNIT_ICMS_OP_ESTOQUE_CONV</td>
    <td>Average ICMS tax amount in inventory per unit, considering unit used to inform the QUANT_CONV field.</td>
  </tr>
  <tr>
    <td>13</td>
    <td>VL_UNIT_ICMS_ST_ESTOQUE_CONV</td>
    <td>Average ICMS-ST tax amount including FCP ST, of the goods in stock, considering the unit used to inform the QUANT_CONV</td>
  </tr>
  <tr>
    <td>14</td>
    <td>VL_UNIT_FCP_ICMS_ST_ESTOQUE_CONV</td>
    <td>Average of the ICMS ST FCP per unit of the goods in stock, considering the unit used to inform the field QUANT_CONV</td>
  </tr>
  <tr>
    <td>15</td>
    <td>VL_UNIT_ICMS_ST_CONV_REST</td>
    <td>ICMS-ST amount, including FCP ST, to be refunded / reimbursed</td>
  </tr>
  <tr>
    <td>16</td>
    <td>VL_UNIT_FCP_ST_CONV_REST</td>
    <td>ICMS-ST FCP amount that composes the field "VL_UNIT_ICMS_ST_CONV_REST", considering the unit used to inform the QUANT_CONV field.</td>
  </tr>
  <tr>
    <td>17</td>
    <td>VL_UNIT_ICMS_ST_CONV_COMPL</td>
    <td>ICMS amount complement, including FCP ST, considering the unit used to inform the QUANT_CONV field.</td>
  </tr>
  <tr>
    <td>18</td>
    <td>VL_UNIT_FCP_ST_CONV_COMPL</td>
    <td>ICMS-ST FCP amount that composes the field "VL_UNIT_ICMS_ST_CONV_COMPL", considering unit used to inform the QUANT_CONV field.</td>
  </tr>
</table>



