# NT2020.005 – Layout and validation updates in the Electronic fiscal document (NF-e) 

This article describes the updates in the XML layout and in the validation rules introduced by the technical note NT2020.005 in the generation of electronic fiscal document model 55 (NF-e).

## Enable the technical note in Dynamics 365 Finance and Supply Chain Management

1.  Sign in to your instance of Microsoft Dynamics 365 Finance or Supply Chain Management.

2.  Go to **Organization administration** &gt; **Organizations** &gt; **Fiscal establishments** &gt; **Fiscal establishments**.

3.  Select the fiscal establishment, and then select **Edit**.

4.  On the **NF-e and NFC-e federal** FastTab, in the **NF-e technical notes** field group, select **Enable NF-e technical note**.

5.  In the **NF-e technical notes** field, select **2020.005 v1.10 technical note** for version 1.10 of the technical note.

## Scope from version 1.00/1.10 of the Technical Note

-   Added new options to **&lt;tpViaTransp&gt;** tag

-   Updated the structure of the node &lt;adi&gt;

-   Added new tags to the nodes &lt;ICMS10&gt;, &lt;ICMS70&gt; and &lt;ICMS90&gt;:

    -   &lt;vICMSSTDeson&gt;

    -   &lt;motDesICMSST&gt;

-   Added new tags to the node &lt;ICMS51&gt;:

    -   &lt;pFCPDif&gt;

    -   &lt;vFCPDif&gt;

    -   &lt;vFCPEfet&gt;

-   Updated the validation rules NA15-20 and NA17-10 during posting of fiscal documents.
