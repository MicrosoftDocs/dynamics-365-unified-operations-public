# SPED Fiscal ICMS-IPI - Layout 014

This topic explains how to set up and generate Sped fiscal statement layout 014 applicable from January 2020 under the practical guide **EFD-ICMS/IPI – version 3.0.3**

## Record 0000 - Opening record

New layout 014.(1.13) has been introduced in **Fiscal books > Setup > Tax statements parameters > Sped fiscal > Sped fiscal parameters > Layout version**

## Record 0002 - Classification of fiscal establishment

This record is generated when the field **IND_ATIV** of record 0000 is equal to "0" and the classification of fiscal establishment is configured in **Fiscal books > Setup > Tax statements parameters > Sped fiscal > Sped fiscal parameters > Classification**. 

Assign classification in the related fiscal establishment and when applies more than one type of classification, please inform the classification that is most relevant in the establishment.


## Record C500. Incoming fiscal documents
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

## Complement and compensation for ICMS-ST
The tax authority has introduced the generation of records C180, C185, 1010 and 1250 to detail the operations that that are subject to ICMS-ST tax when the company applies the complement and compensation of ICMS-ST tax. The generation of these record will be addressed by each state


### Prerequisites

Before you enable the generation of these records , enable the Presumed tax calculation in **Organization administration > Setup > Brazilian parameters > Fiscal document**
	- ICMS- ST presumed tax
	- ICMS-ST presumed tax in fiscal books 


In order to generate these records, you need to setup per state the rule that will allow the generation of these records:
	1. Go to  **Fiscal books > Setup > Fiscal books parameters per state**
	2. Select the related State, for example SP
	3. Mark as **Yes** 
	4. Select the **SPED presumed tax calculation algorithm**  since the amounts calculated will be reported in record C185
  
  
