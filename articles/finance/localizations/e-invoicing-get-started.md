---
# required metadata

title: Get started with Electronic invoicing
description: This topic provides information that will help you get started with Electronic invoicing in Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: gionoder
ms.date: 11/08/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: ["97423", "intro-internal"]
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Get started with Electronic invoicing

[!include [banner](../includes/banner.md)]

This topic provides information that will help you get started with Electronic invoicing. This topic guides you through the common configuration steps in Regulatory Configuration Services (RCS) and Dynamics 365 Finance, and provides the steps you must follow to submit business documents and review the processing results.

## Prerequisites

Before you complete the procedures in this topic, the following prerequisites must be in place:

- Configure your Microsoft Dynamics Lifecycle Services (LCS), Regulatory Configuration Service (RCS), and your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment. For more information, see [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md).
- Create a configuration provider for your organization. For more information, see [Create a configuration provider and mark them as active](../../fin-ops-core/dev-itpro/analytics/tasks/er-configuration-provider-mark-it-active-2016-11.md).

## Import an Electronic invoicing feature from the Microsoft configuration provider 

1. Sign in to your Regulatory Configuration Service (RCS) account.
2. In the **Globalization features** workspace, in the **Features** section, select the **Electronic invoicing** tile.
3. Select **Import**, and then select **Synchronize**.
4. Filter the **Configuration provider** column by the term **Microsoft**.
5. Select the name of an Electronic invoicing feature from the table, and then select **Import**.

## Create an Electronic invoicing feature under your organization provider

1. In RCS, in the **Features** section of the **Globalization features** workspace, select the **Electronic invoicing** tile.
2. Select **Add** > **Based on existing feature**, and in the **Name** field, enter the name of the Electronic invoicing feature.
3. In the **Description** field, enter a description of the feature.
4. In the **Base feature field**, select the imported Electronic invoicing feature from the Microsoft configuration provider.
5. Select **Create feature**.

## Country-specific configuration for Electronic invoicing feature

Depending on the country or region, the Electronic invoicing feature might require specific configuration. 

> [!NOTE]
> When you enable the Electronic invoicing feature for Finland, application-specific parameters in lookups aren't supported. To work around this issue, in the **Electronic reporting** module, review the configurations for the sales invoice and project invoice formats. Manually set up the calculated field for **$PaymentMethodSubstitution** mapping, and then bind that field to the **EpiPaymentMeansCode** field from the sales invoice and project invoice formats.
>
> When you enable the Electronic invoicing feature for Italy, application-specific parameters in lookups aren't supported. To work around this issue, in the **Electronic reporting** module, manually set up the calculated field for **$NaturaReverseCharge** mapping.
>
> For specific steps that are related to other locations, see the "Get started" documentation that is available for your country or region.

## Import the model mapping configurations from Electronic reporting

1. In RCS, select the **Electronic reporting** workspace.
2. From the list of **Microsoft** Configuration providers, select **Repositories**.
3. Select **Global** and on Action Pane, select **Open**.
4. Import the model mapping configurations according to the following table by feature name.

| Feature name                         | Model mapping configuration |
|--------------------------------------|-----------------------------|
| Austrian electronic invoices (AT)    | <p>Customer invoice context model</p><p>Invoice model</p> |
| Belgian electronic invoice (BE)      | <p>Customer invoice context model</p><p>Invoice model</p> |
| Brazilian NF-e (BR)                  | <p>Customer invoice context model</p><p>Fiscal documents</p><p>Response message model</p> |
| Brazilian NFS-e ABRASF Curitiba (BR) | <p>Customer invoice context model</p><p>Fiscal documents</p><p>Response message model</p> |
| Danish electronic invoice (DK)       | <p>Customer invoice context model</p><p>Invoice model</p> |
| Egyptian electronic invoice (EG)     | <p>Customer invoice context model</p><p>Invoice model</p><p>Response message model</p> |
| Estonian electronic invoice (EE)     | <p>Customer invoice context model</p><p>Invoice model</p> |
| Finish electronic invoice (FI)       | <p>Customer invoice context model</p><p>Invoice model</p> |
| French electronic invoice (FR)       | <p>Customer invoice context model</p><p>Invoice model</p> |
| German electronic invoice (DE)       | <p>Customer invoice context model</p><p>Invoice model</p> |
| FatturaPA (IT)                       | <p>Customer invoice context model</p><p>Invoice model</p> |
| Mexican CFDI Interfactura (MX)       | <p>Customer invoice context model</p><p>Invoice model</p><p>Response message model</p> |
| Dutch electronic invoice (NL)        | <p>Customer invoice context model</p><p>Invoice model</p> |
| Norwegian electronic invoice (NO)    | <p>Customer invoice context model</p><p>Invoice model</p> |
| Spanish electronic invoice (ES)      | <p>Customer invoice context model</p><p>Invoice model</p> |
| PEPPOL electronic invoice            | <p>Customer invoice context model</p><p>Invoice model</p> |
| Saudi Arabian electronic invoice (SA)| <p>Customer invoice context model</p><p>Invoice model</p> |


## Configure the application setup

1. Select the Electronic invoicing feature that you created.
2. On the **Setups** tab, select **Application setup**.
3. In the **Connect application** field, select the connection that is associated with your instance of Finance or Supply Chain Management.
4. In the **Electronic document types** section, select **Add**.
5. Select and enter a **Table name** value according to the following table.

    | Feature name                         | Business document | Table name |
    |--------------------------------------|-------------------|------------|
    | Austrian electronic invoices (AT)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Belgian electronic invoice (BE)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Brazilian NF-e (BR)                  | <p>Fiscal document</p><p>Correction letter</p> | Fiscal document |
    | Brazilian NFS-e ABRASF Curitiba (BR) | Service Fiscal document | Fiscal document |
    | Danish electronic invoice (DK)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Egyptian electronic invoice (EG)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Estonian electronic invoice (EE)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Finish electronic invoice (FI)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | French electronic invoice (FR)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | German electronic invoice (DE)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | FatturaPA (IT)                       | <p>Sales invoice</p><p>Project invoice | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Mexican CFDI Interfactura (MX)       | <p>Sales invoice</p><p>Packing slip</p><p>Inventory transfer</p><p>Payment complement</p> | Customer invoice journal |
    | Dutch electronic invoice (NL)        | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Norwegian electronic invoice (NO)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Spanish electronic invoice (ES)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | PEPPOL electronic invoice            | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |
    | Saudi Arabian electronic invoice (SA)| <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice journal</p><p>Project invoice</p> |

6. For each table name you create, select and enter a context value according to the following table.

    | Feature name                         | Business document | Context |
    |--------------------------------------|-------------------|---------|
    | Austrian electronic invoices (AT)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Belgian electronic invoice (BE)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Brazilian NF-e (BR)                  | <p>Fiscal document</p><p>Correction letter</p> | <p>Customer invoice context model – Fiscal document context</p><p>Customer invoice context model – FD correction letter context</p> |
    | Brazilian NFS-e ABRASF Curitiba (BR) | Service Fiscal document| Customer invoice context model – Fiscal document context |
    | Danish electronic invoice (DK)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Egyptian electronic invoice (EG)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Estonian electronic invoice (EE)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Finish electronic invoice (FI)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | French electronic invoice (FR)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | German electronic invoice (DE)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | FatturaPA (IT)                       | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Mexican CFDI Interfactura (MX)       | <p>Sales invoice</p><p>Packing slip</p><p>Inventory transfer</p><p>Payment complement</p> | Customer invoice context model – Customer invoice context |
    | Dutch electronic invoice (NL)        | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Norwegian electronic invoice (NO)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Spanish electronic invoice (ES)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | PEPPOL electronic invoice            | <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |
    | Saudi Arabian electronic invoice (SA)| <p>Sales invoice</p><p>Project invoice</p> | <p>Customer invoice context model – Customer invoice context</p><p>Customer invoice context model – Project invoice context</p> |

7. For each table name and context, select and enter a business document mapping value according to the following table.

    | Feature name                         | Business document | Business document mapping |
    |--------------------------------------|-------------------|---------------------------|
    | Austrian electronic invoices (AT)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Belgian electronic invoice (BE)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Brazilian NF-e (BR)                  | <p>Fiscal document</p><p>Correction letter</p> | <p>Fiscal document mapping – Fiscal document mapping</p><p>Fiscal document mapping – correction letter mapping</p> |
    | Brazilian NFS-e ABRASF Curitiba (BR) | Service Fiscal document | Fiscal document mapping – Fiscal document mapping |
    | Danish electronic invoice (DK)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Egyptian electronic invoice (EG)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Estonian electronic invoice (EE)     | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Finish electronic invoice (FI)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | French electronic invoice (FR)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | German electronic invoice (DE)       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | FatturaPA (IT)                       | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Mexican CFDI Interfactura (MX)       | <p>Sales invoice</p><p>Packing slip</p><p>Inventory transfer</p><p>Payment complement</p> | Invoice model mapping – Customer invoice |
    | Dutch electronic invoice (NL)        | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Norwegian electronic invoice (NO)    | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Spanish electronic invoice (ES)      | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | PEPPOL electronic invoice            | <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |
    | Saudi Arabian electronic invoice (SA)| <p>Sales invoice</p><p>Project invoice</p> | <p>Invoice model mapping – Customer invoice</p><p>Invoice model mapping – Project invoice</p> |


## Country-specific configuration of application setup

Depending on the country or region, the Application setup might require specific configuration. 

For the specific steps, see the "Get started" documentation that is available for your country or region.

## Deploy the Electronic invoicing feature to Service environment

1. On the **Versions** tab, select the version of the Electronic invoicing feature that you want to deploy.
2. Select **Change status** \> **Complete**.
3. Select **Change status** \> **Publish**.
4. Select **Deploy**.
5. Set the **Deploy to connected application** option to **No**.
6. Set the **Deploy to service environment** option to **Yes**.
7. In the **Service environment** field, select the Electronic invoicing service environment where you want to deploy the Electronic invoicing feature.
8. In the **From date** field, select the date when the Electronic invoicing feature must become effective in Electronic invoicing.
9. Select **OK**.

## Deploy the Electronic invoicing feature to Connected application

1. On the **Versions** tab, select a version of the Electronic invoicing feature that you want to deploy.
2. Select **Deploy**.
3. Set the **Deploy to connected application** option to **Yes**.
4. On the **Connect application** field, select the connection that is associated with your instance of Finance or Supply Chain Management.
5. Set the **Deploy to service environment** option to **No**.
6. Select **OK**.

## Turn on the Electronic invoicing feature in Finance or Supply Chain Management

1. Sign in to Finance or Supply Chain Management, and verify that you're in the correct legal entity.
2. Go to **Organization administration** \> **Setup** \> **Electronic document parameters**.
3. On the **Features** tab, select the country/region-specific feature to turn on the Electronic invoicing feature for Finance or Supply Chain Management. The following table provides a list of the electronic invoicing features available for specific country/regions. 

    | Feature name                                          | Country/region  |
    |-------------------------------------------------------|-----------------|
    | Austrian electronic invoices (AT)                     | Austria         |
    | Belgian electronic invoice (BE)                       | Belgium         |
    | CFDI Mexican electronic invoice (MX)                  | Mexico          |
    | Danish electronic invoice (DK)                        | Denmark         |
    | Dutch electronic invoice (NL)                         | The Netherlands |
    | Egyptian electronic invoice (EG)                      | Egypt           |
    | Estonian electronic invoice (EE)                      | Estonia         |
    | Finnish electronic invoice (FI)                       | Finland         |
    | French electronic invoice (FR)                        | France          |
    | German electronic invoice (DE)                        | Germany         |
    | Italian electronic invoice (IT)                       | Italy           |
    | NF-e Federal - Brazilian electronic invoice (BR)      | Brazil          |
    | NFS-e - Brazilian service (city) electronic invoice   | Brazil          |
    | Norwegian electronic invoice (NO)                     | Norway          |
    | PEPPOL electronic invoice                             | Global          |
    | Spanish electronic invoice (ES)                       | Spain           |
    | Saudi Arabian electronic invoice (SA)                 | Saudi Arabia    |
    

4. Select **Save**.

## Issue electronic invoices

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Submit electronic documents**.
2. On the **Records to include** FastTab, select **Filter**.
3. Select **Add** to add a table name to the query filter.
4. Select the table that contains the invoices.

    > [!NOTE]
    > The table name must be listed in the table in the [Configure the application setup](#configure-the-application-setup) section earlier in this topic.

5. Select the field name from the table that you want to query.
6. Enter the table name and field name for the criteria to query on.
7. Repeat steps 5 and 6 to add more fields and criteria to the query, and then select **OK**.
8. Select **OK**.

## View submission logs

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**.
2. In the **Document type** field, select the table that contains the invoices.

    > [!NOTE]
    > The table name must be listed in the table in the [Configure the application setup](#configure-the-application-setup) section earlier in this topic.

3. Select an invoice in the grid, and then select **Inquire** \> **Submission details**.

## Download an electronic document file

1. Go to **Organization administration** \> **Periodic** \> **Electronic documents** \> **Electronic document submission log**.
2. In the **Document type** field, select the table that contains the invoices.
3. Select a document in the grid, and then select **Electronic document** \> **Download file**. An archive that contains the electronic document file will be suggested for downloading.

> [!NOTE]
> Before you can download files, the **Export result** option must be turned on for the related action in the Electronic invoicing feature setup in RCS.

## Related topics

- [Electronic invoicing overview](e-invoicing-service-overview.md)
- [Get started with Electronic invoicing service administration](e-invoicing-get-started-service-administration.md)
- [Get started with Electronic invoicing for Brazil](e-invoicing-bra-get-started.md)
- [Get started with Electronic invoicing for Mexico](e-invoicing-mex-get-started.md)
- [Get started with Electronic invoicing for Italy](e-invoicing-ita-get-started.md)
- [Customer electronic invoices in Egypt](emea-egy-e-invoices.md)
- [Customer electronic invoices in Saudi Arabia](emea-sau-e-invoices.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
