---
# required metadata

title: Get started with the Electronic invoicing add-on
description: This topic provides information that will help you get started with the Electronic invoicing add-on in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: gionoder
manager: AnnBe
ms.date: 10/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with the Electronic invoicing add-on

[!include [banner](../includes/banner.md)]

# Get started with the Electronic invoicing add-on

This topic provides information that help you get started with
Electronic invoicing add-on.

The table below shows the name of electronic invoicing features and over
which business documents they are applicable.

| **Feature name**                      | **Business document**   |
|---------------------------------------|-------------------------|
| Austrian electronic invoices (AT)     | Sales invoice</br>Project invoice |
| Belgian electronic invoice (BE)       | Sales invoice</br>Project invoice |
| Brazilian NF-e (BR)                   | Fiscal document model 55</br>Correction letter |
| Brazilian NFS-e ABRASF Curitiba (BR)  | Service Fiscal document |
| Brazilian NFS-e São Paulo (BR)        | Service Fiscal document |
| Danish electronic invoice (DK)        | Sales invoice</br>Project invoice |
| Egyptian electronic invoice (EG)      | Sales invoice</br>Project invoice |
| Estonian electronic invoice (EE)      | Sales invoice</br>Project invoice |
| Finish electronic invoice (FI)        | Sales invoice</br>Project invoice |
| French electronic invoice (FR)        | Sales invoice</br>Project invoice |
| German electronic invoice (DE)        | Sales invoice</br>Project invoice |
| FatturaPA (IT)                        | Sales invoice</br>Project invoice |
| Mexican CFDI Interfactura (MX)        | Sales invoice</br>Packing slip</br>Inventory transfer</br>Payment complement |
| Dutch electronic invoice (NL)         | Sales invoice</br>Project invoice |
| Norwegian electronic invoice (NO)     | Sales invoice</br>Project invoice |
| Spanish electronic invoice (ES)       | Sales invoice</br>Project invoice |
| PEPPOL electronic invoice             | Sales invoice</br>Project invoice |


# Prerequisites

Before you complete the steps in this topic, you must have the following
prerequisites in place:

-   Configured your RCS and your Dynamics 365 Finance or Dynamics 365
    Supply Chain Management for submitting to Electronic invoicing
    add-on.

-   Created and published a service environment into Electronic
    invoicing add-on.

-   Created a connected application.

-   For more information, see [Get started with the Electronic invoicing
    add-on service
    administration](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/e-invoicing-GA-docs/articles/finance/localizations/e-invoicing-get-started-service-administration.md).

-   Created a configuration provider for your organization. For more
    information, see [Create configuration provider and mark them as
    active.](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11)

# Import the Electronic invoicing feature from Microsoft Configuration provider 

1.  Sign in to your LCS account.

2.  In the **Globalization feature** workspace, in the **Features**
    section, select the **e-Invoicing** tile.

3.  Click **Import.**

4.  Click **Synchronize.**

5.  Filter the column **Configuration provider** by Microsoft.

6.  Select a feature the name of the feature (from one of country/region
    listed above).

7.  Click **Import.**

# Configure Electronic invoicing feature

1.  Depending on the Country/region, the Electronic invoicing feature
    can require additional configurations. See the Get started
    documentation available for your country/region for specific steps.

# Configure the Application setup

1.  Select the Electronic invoicing feature you imported.

2.  Click on **Version** tab.

3.  Make sure the **Draft** version is selected.

4.  Click on **Setups** tab, then click on **Application setup.**

Note: make sure your organization is set as Active as configuration
provider. For more information, see [Create configuration provider and
mark them as
active.](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11)

1.  Select a **Feature setup**.

2.  Select a **Connected application.**

3.  In **Electronic document types** field group, click **Add**.

4.  Repeat for each business document the Feature name supports, select and enter the **Table name** according to the 
    the table below:

| **Feature name**                      | **Business document** | **Table name** |
|---------------------------------------|-------------------------|-------------------------|
| Austrian electronic invoices (AT)     | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Belgian electronic invoice (BE)       | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Brazilian NF-e (BR)                   | Fiscal document</br>Correction letter | Fiscal document |
| Brazilian NFS-e ABRASF Curitiba (BR)  | Service Fiscal document | Fiscal document |
| Brazilian NFS-e São Paulo (BR)        | Service Fiscal document | Fiscal document |
| Danish electronic invoice (DK)        | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Egyptian electronic invoice (EG)      | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Estonian electronic invoice (EE)      | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Finish electronic invoice (FI)        | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| French electronic invoice (FR)        | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| German electronic invoice (DE)        | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| FatturaPA (IT)                        | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Mexican CFDI Interfactura (MX)        | Sales invoice</br>Packing slip</br>Inventory transfer</br>Payment complement | Customer invoice journal |
| Dutch electronic invoice (NL)         | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Norwegian electronic invoice (NO)     | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| Spanish electronic invoice (ES)       | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |
| PEPPOL electronic invoice             | Sales invoice</br>Project invoice | Customer invoice journal</br>Project invoice |


1.  In **Context**, repeat for each business document the Feature name supports, select and enter the **Context** according to the 
    the table below:

| **Feature name**                      | **Business document** | **Context** |
|---------------------------------------|-----------------------|-------------------------|
| Austrian electronic invoices (AT)     | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Belgian electronic invoice (BE)       | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Brazilian NF-e (BR)                   | Fiscal document</br>Correction letter | Customer invoice context model – Fiscal document context</br>Customer invoice context model – FD correction letter context |
| Brazilian NFS-e ABRASF Curitiba (BR)  | Service Fiscal document| Customer invoice context model – Fiscal document context |
| Brazilian NFS-e São Paulo (BR)        | Service Fiscal document| Customer invoice context model – Fiscal document context |
| Danish electronic invoice (DK)        | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Egyptian electronic invoice (EG)      | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Estonian electronic invoice (EE)      | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Finish electronic invoice (FI)        | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| French electronic invoice (FR)        | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| German electronic invoice (DE)        | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| FatturaPA (IT)                        | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Mexican CFDI Interfactura (MX)        | Sales invoice</br>Packing slip</br>Inventory transfer</br>Payment complement | Customer invoice context model – Customer invoice context |
| Dutch electronic invoice (NL)         | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Norwegian electronic invoice (NO)     | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| Spanish electronic invoice (ES)       | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |
| PEPPOL electronic invoice             | Sales invoice</br>Project invoice | Customer invoice context model – Customer invoice context</br>Customer invoice context model – Project invoice context |


1.  In **Business document mapping**, repeat for each business document the Feature name supports, select and enter the **Business document mapping** according to the 
    the table below:

| **Feature name**                      | **Business document** | **Business document mapping** |
|---------------------------------------|-------------------------|-----------------------------|
| Austrian electronic invoices (AT)     | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Belgian electronic invoice (BE)       | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Brazilian NF-e (BR)                   | Fiscal document</br>Correction letter | Fiscal document mapping – Fiscal document mapping</br>Fiscal document mapping – correction letter mapping |
| Brazilian NFS-e ABRASF Curitiba (BR)  | Service Fiscal document | Fiscal document mapping – Fiscal document mapping |
| Brazilian NFS-e São Paulo (BR)        | Service Fiscal document | Fiscal document mapping – Fiscal document mapping |
| Danish electronic invoice (DK)        | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Egyptian electronic invoice (EG)      | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Estonian electronic invoice (EE)      | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Finish electronic invoice (FI)        | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| French electronic invoice (FR)        | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| German electronic invoice (DE)        | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| FatturaPA (IT)                        | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Mexican CFDI Interfactura (MX)        | Sales invoice</br>Packing slip</br>Inventory transfer</br>Payment complement | Invoice model mapping – Customer invoice |
| Dutch electronic invoice (NL)         | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Norwegian electronic invoice (NO)     | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| Spanish electronic invoice (ES)       | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |
| PEPPOL electronic invoice             | Sales invoice</br>Project invoice | Invoice model mapping – Customer invoice</br>Invoice model mapping – Project invoice |


1.  Depending on the Country/region, the Electronic invoicing feature
    can require additional configurations. See the Get started
    documentation available for your country/region for specific steps.

# Deploy the Electronic invoicing feature

1.  On tab **Versions,** select the Version of the Electronic invoicing
    feature you want to deploy.

2.  Click on **Change status**, and select **Complete.**

3.  Click on **Change status** and select **Publish**.

4.  Click on **Deploy.**

5.  Set the toggle **Deploy to connected application** to Yes.

6.  On **Connect application**, select the connection associated to your
    instance of Dynamics 365 Finance or Dynamics 365 Supply Chain
    Management.

7.  Set the toggle **Deploy to service environment** to Yes.

8.  On **Service environment**, select the Electronic invoicing add-on
    service environment you want to deploy the electronic invoicing
    feature.

9.  On **From date**, select the date the Electronic invoicing feature
    must become effective in Electronic invoicing add-on.

10. Click **OK**.

# Turn on the Electronic invoicing feature in Dynamics 365 Finance or Dynamics 365 Supply Chain Management

1.  Sign in to Dynamics 365 Finance or Dynamics 365 Supply Chain
    Management

2.  Make sure you are in the proper **Legal entity**.

3.  Go to **Organization administration &gt; Setup &gt; Electronic
    document parameters**.

4.  On **Features** tab, select the **Feature reference** given by the
    table below to turn on the Electronic invoicing feature on the in
    Dynamics 365 Finance or Dynamics 365 Supply Chain Management side

| **Feature name**                      | **Country/Region** | **Feature reference** |
|---------------------------------------|-------------------------|-------------------------|
| Austrian electronic invoices (AT)     | Austria | EUR-00023 |
| Belgian electronic invoice (BE)       | Belgium | EUR-00023 |
| Brazilian NF-e (BR)                   | Brazil | BR-00053 |
| Brazilian NFS-e ABRASF Curitiba (BR)  | Brazil | BR-00095 |
| Brazilian NFS-e São Paulo (BR)        | Brazil | BR-00095 |
| Danish electronic invoice (DK)        | Denmark | EUR-00023<br /></br>DK-00001 |
| Dutch electronic invoice (NL)         | The Netherlands | EUR-00023 |
| Egyptian electronic invoice (EG)      | Egypt | EG-00008 |
| Estonian electronic invoice (EE)      | Estonia | EUR-00023 |
| Finnish electronic invoice (FI)       | Finland | EUR-00023 |
| French electronic invoice (FR)        | France | EUR-00023 |
| German electronic invoice (DE)        | Germany | EUR-00023 |
| Mexican CFDI Interfactura (MX)        | Mexico | MX-00010</br>MX-00016 |
| Norwegian electronic invoice (NO)     | Norway | EUR-00023<br /></br>NO-00010 |
| Spanish electronic invoice (ES)       | Spain | EUR-00023<br /></br>ES-00025 |
| Italian electronic invoice (IT)       | Italy | EUR-00023<br /></br>IT-00036 |
| PEPPOL electronic invoice             | Europe | EUR-00023 |


1.  Click **Save.**

# Issue electronic invoices

1.  Go to **Organization administration &gt; Periodic &gt; Electronic
    documents &gt; Submit electronic documents.**

2.  Expand **Record to include** fast tab.

3.  Click on **Filter**.

4.  If you want to add a table name to the query filter, click **Add.**

5.  Select the **Table** that contains the invoices.

Note: It must be one the table names entered in section **Configure the
Application setup.**

1.  Select the **Field** name from the table you want to query.

2.  Type the **Criteria** to query the table name and field name.

3.  Repeat to add more **Field and Criteria** to the query.

4.  When done, click **OK.**

5.  Click **OK.**

# View submission logs

1.  Go to **Organization administration &gt; Periodic &gt; Electronic
    documents &gt; Electronic document submission log.**

2.  In **Document type**, select the **Table** that contains the
    invoices.

Note: It must be one the table names entered in section **Configure the
Application setup.**

1.  Select an invoice listed in the grid.

2.  Click **Inquire &gt; Submission details.**

3.  Depending on the Country/region, the Electronic invoicing feature
    can require additional configurations. See the Get started
    documentation available for your country/region for specific steps.

## Related topics

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with the Electronic invoicing add-on for Brazil](e-invoicing-bra-get-started.md)
- [Get started with the Electronic invoicing add-on for Mexico](e-invoicing-mex-get-started.md)
- [Get started with the Electronic invoicing add-on for Italy](e-invoicing-ita-get-started.md)
- [Set up the Electronic invoicing add-on](e-invoicing-setup.md)
