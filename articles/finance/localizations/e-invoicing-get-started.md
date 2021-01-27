---
# required metadata

title: Get started with the Electronic invoicing add-on
description: This topic provides information that will help you get started with the Electronic invoicing add-on in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: gionoder
manager: AnnBe
ms.date: 01/27/2021
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

This topic provides information that help you get started with Electronic invoicing add-on.

The following table lists the electronic invoicing features and the business documents to which they can be applied.

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

Before you complete the steps in this topic, you must have the following prerequisites in place:

- Configure your Regulatory Configuration Service (RCS) and your Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment so that you can submit to the Electronic invoicing add-on.
- Create and publish a service environment into the Electronic invoicing add-on.
- Create a connected application. For more information, see [Get started with the Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md).
- Create a configuration provider for your organization. For more information, see [Create configuration provider and mark them as active.](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

# Import the Electronic invoicing feature from Microsoft Configuration provider 

1. Sign in to your LCS account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **e-Invoicing** tile.
3. Select **Import** and then select **Synchronize**.
4. Filter the column **Configuration provider** by **Microsoft**.
5. Select a feature name from one of countries/regions listed above, and then select **Import**.

# Configure the Electronic invoicing feature

- Depending on the country/region, the Electronic invoicing feature may require additional configurations. See the Get started documentation available for your country/region for specific steps.

# Configure the Application setup

1. Select the Electronic invoicing feature you imported.
2. Select the **Version** tab and verify that the **Draft** version is selected.
3. On the **Setups** tab, select **Application setup**.

    > [!NOTE]
    > Verify that your organization is set as the **Active** configuration provider. For more information, see [Create configuration provider and mark them as active.](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

4. Select **Feature setup** and then select **Connected application**.
5. In **Electronic document types** field group, select **Add**.
6. For each business document the feature name supports, select and enter the **Table name** according to the following table.

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


7.  In the **Context** field, select and enter the **Context** according to the following table. Repeat for each business document the feature name supports.

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


8. In the **Business document mapping** field,  select and enter the **Business document mapping** according to the following table. Repeat for each business document the feature name supports.

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


Depending on the Country/region, the Electronic invoicing feature can require additional configurations. See the Get started documentation available for your country/region for specific steps.

# Deploy the Electronic invoicing feature

1. On tab **Versions,** select the version of the Electronic invoicing feature you want to deploy.
2. Select **Change status** > **Complete**.
3. Select **Change status** > **Publish**.
4. Select **Deploy**.
5. Set the toggle **Deploy to connected application** to **Yes**.
6. On **Connect application**, select the connection associated to your instance of Finance or Supply Chain Management.
7. Set the toggle **Deploy to service environment** to **Yes**.
8. In the **Service environment** field, select the Electronic invoicing add-on service environment where you want to deploy the electronic invoicing feature.
9. In the **From date** field, select the date that the Electronic invoicing feature must become effective in the Electronic invoicing add-on.
10. Select **OK**.

# Turn on the Electronic invoicing feature in Finance or Supply Chain Management

1. Sign in to Finance or Supply Chain Management and verify that you are in the correct legal entity.
2. Go to **Organization administration** > **Setup** > **Electronic document parameters**.
3. On the **Features** tab, select a feature reference listed in the following to turn on the Electronic invoicing feature on for Finance or Supply Chain Management.

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


4. Select **Save.**

# Issue electronic invoices

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Submit electronic documents**.
2. Expand the **Record to include** FastTab and select **Filter**.
3. Select **Add** to add a table name to the query filter.
4. Select the table that contains the invoices.

    > [!NOTE]
    > The table name must be listed in the table provided in the **Configure the Application setup** section in this topic.

5. Select the **Field** name from the table you want to query.
6. Enter the table name and field name for the criteria to query on.
7. Repeat steps 5 and 6 to add more fields and criteria to the query and then select **OK**.
8. Select **OK**.

# View submission logs

1. Go to **Organization administration** > **Periodic** > **Electronic documents** > **Electronic document submission log**.
2. In the **Document type** field, select the table that contains the invoices.

   > [!NOTE]
   > The table name must be listed in the table provided in the **Configure the Application setup** section in this topic.

3. Select an invoice listed in the grid and then select **Inquire** > **Submission details**.

Depending on the country/region, the Electronic invoicing feature can require additional configurations. See the Get started documentation available for your country/region for specific steps.

## Related topics

- [Electronic invoicing add-on overview](e-invoicing-service-overview.md)
- [Get started with the Electronic invoicing add-on for Brazil](e-invoicing-bra-get-started.md)
- [Get started with the Electronic invoicing add-on for Mexico](e-invoicing-mex-get-started.md)
- [Get started with the Electronic invoicing add-on for Italy](e-invoicing-ita-get-started.md)
- [Get started with the Electronic invoicing add-on for Egypt](e-invoicing-ita-get-started.md)
