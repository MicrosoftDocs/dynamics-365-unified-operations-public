# NT2021.004 – Layout and validation updates in the electronic fiscal document (NF-e)

This article describes the updates to the XML layout and validation rules that were introduced by technical note NT2021.004 for the generation of electronic fiscal document model 55 (NF-e).

## Enable the technical note in Dynamics 365 Finance and Dynamics 365 Supply Chain Management

1.  Sign in to your instance of Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management.

2.  Go to **Organization administration &gt; Organizations &gt; Fiscal establishments &gt; Fiscal establishments.**

3.  Select the Fiscal establishment, Select **Edit**.

4.  On fast tab **NF-e and NFC-e federal**, on field group **NF-e technical notes**, select **Enable NF-e technical note**.

5.  On field **NF-e technical notes**, select **2021.004 v1.00 technical note**.

6.  Select **Save.**

## Scope for version 1.00 of the technical note

This technical note introduced a new tag to send the information about the Concessionary act applicable only when the Agency from the referenced process is SEFAZ (Brazilian tax authority), and new validations rules to enforce the correct usage of the Freight information in the XML.

### Updates in the XML

New tag &lt;tpAto&gt;:

New options added to the Fiscal document source texts to enable the setup of the Type of concessionary act to populate the new tag &lt;tpAto&gt;, in scenarios where **Agency** is **SEFAZ.**

1.  Go to **Organization administration &gt; Organizations &gt; Setup &gt; Fiscal document source texts.**

2.  Select a Fiscal document source text.

3.  On the **Referenced process** tab, select **New.**

4.  Select SEFAZ in the **Agency** column.

5.  Type the number of referenced process.

6.  Select the **Type of Concessionary act**, as defined in the Technical Note.

7.  Select **Save.**

## Scope for version 1.31 of the technical note

### Updates on validation rules:

New validation rules were updated during posting of fiscal documents to prevent the following NF-e rejection error codes:

-   847

-   849

During posting of outbound electronic fiscal documents, when tag tpNF = 1 (outgoing):

-   When the Tax registration ID (base CNPJ) of the Transporter is equal to the Tax registration ID (base CNPJ) of the Issuer, the Freight charges terms must be different from Prepaid (modFrete = 0), otherwise it violates validation rule X04-50.

-   When the Tax registration ID (base CNPJ) of the Transporter is equal to the Tax registration ID (base CNPJ) of the Receiver, the Freight charges terms must be different from Collect (modFrete = 1), otherwise it violates validation rule X04-90.

During posting of inbound electronic fiscal documents, when tag tpNF = 0 (inbound):

-   When the Tax registration ID (base CNPJ) of the Transporter is equal to the Tax registration ID (base CNPJ) of the Issuer, the Freight charges terms must be different from Collect (modFrete = 1), otherwise it violates validation rule X04-100.

-   When the Tax registration ID (base CNPJ) of the Transporter is equal to the Tax registration ID (base CNPJ) of the Receiver, the Freight charges terms must be different from Prepaid (modFrete = 0), otherwise it violates validation rule X04-60.
