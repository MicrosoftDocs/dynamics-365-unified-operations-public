---
title: Intercompany planning groups for demand forecasting
description: Learn about intercompany planning groups and how they contribute to demand forecasting, which optimizes logistics operations across multiple companies.
author: t-benebo
ms.author: benebotg
ms.topic: overview
ms.date: 04/15/2024
ms.custom: 
  - bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Intercompany planning groups for demand forecasting

[!include [banner](../includes/banner.md)]
[!INCLUDE [demand-planning-banner](../includes/demand-planning-banner.md)]

This article describes how you can use intercompany planning groups during the demand forecasting process.

Collaboration is a vital aspect for many large-scale projects. When working with other legal entities (companies) during the development of a product or service, you can create intercompany planning groups to assist you during the demand forecasting process.

This gives all companies involved a greater understanding of the anticipated revenue that the product or service will generate. It also gives them the information necessary to devise and conduct business plans accordingly.

Many organizations utilize other companies within their organization to oversee various facets within collaborations and projects. Logistics operations that depend on other companies are handled by using intercompany sales and purchases since each legal entity has a separate chart of accounts.

Intercompany planning groups are created during the demand forecasting process after creating forecast models and removing outliers. For demand forecasts, set up downstream companies first, then set up upstream companies afterwards.

To further understand intercompany planning groups for demand forecasting, understand the following terms:

- **Demand forecast** – Allows your company to create "what if" scenarios and efficiently and cost-effectively plan for and meet demand. Accurate forecasts can make a critical difference in customer satisfaction levels about order promising dates and on-time delivery. Allows businesses to predict future sales demand and use that data to drive certain business decisions.
- **Upstream** – A relative reference in a firm or supply chain. It indicates movement in the direction of the raw material supplier.
- **Downstream** – A relative reference in a firm or supply chain. It indicates movement in the direction of the customer.
- **Planned intercompany demand** – Planned demand for a product in a company, based on planned demand for the product from a downstream company.

A plan in one company can include planned intercompany demand that is related to orders from another company's plan. This capability is useful, because it provides full visibility into planned orders across companies. It also ensures that all required planned supply orders are created, but without requiring that planned orders be firmed for the intercompany demand.

To propagate the demand throughout the intercompany chain, you must set parameters to ensure that planned purchase orders are automatically firmed; that is, orders can't be changed in terms of time or quantity. Set up the **Firming time fence** on the coverage group, or the **Firming time fence** in the master plan.

If no **Firming time fence** is set up, no intercompany purchase orders are created automatically. Only the first execution of the master scheduling results in planned orders; however, because the intercompany purchase order is not actually created, no intercompany sales order is created, and, therefore, no additional intercompany purchase orders are created, and so on.

Learn more in [Intercompany planning groups](../master-planning/demand-forecasting-setup.md#intercompany-planning-groups).

<!-- KFM: The following text needs to be verified against SCM pages and settings. I think this text is describing Business Central, not SCM. 

## Overview of the steps to get started

Use the **Intercompany Setup** page to set up the following components of intercompany transactions:

- Your company's intercompany settings.
- The company that will be the synchronization partner.
- The intercompany chart of accounts that all the partners use to exchange transactions.
- The mappings between accounts in the chart of accounts and intercompany chart of accounts for inbound and outbound transactions for each partner.
- The intercompany dimensions and dimension values to use, and how they're mapped to dimensions for each partner.
- The companies that are the intercompany partners.
- The companies that are vendors or customers, or both.

Learn more in [Demand forecasting setup](../master-planning/demand-forecasting-setup.md#intercompany-planning-groups).

## Synchronization partners

All partners must use the same intercompany chart of accounts and, if needed, the same intercompany dimensions. You can save time when you set up the partnership by using the chart of accounts and dimensions for one of the partners as a baseline for the intercompany chart of accounts and dimensions. The company that you use as the baseline is called the *synchronization partner*. Typically, the synchronization partner is the headquarter company, but it doesn't have to be.

On the **Intercompany Setup** page, each partner specifies the synchronization partner in the **Synchronization Partner** field. Afterward, the intercompany chart of accounts and intercompany dimensions are automatically specified for them, based on the setup for the synchronization partner. The partners then use the **Intercompany Chart of Accounts Mapping** and **Intercompany Dimension Mapping** pages to map their chart of accounts and dimensions to the intercompany chart of accounts and dimensions, and vice versa.

> [!NOTE]
> It's important to map accounts and dimensions in both directions. That is, both to the intercompany chart of accounts and dimensions, and from them to your own accounts and dimensions.

Exchange the following authentication settings. Each partner can get this information from their registered app.

- Client ID
- Client secret
- Token endpoint
- Redirect URL

Run the **IC Partner Cross-Environment Setup** assisted setup guide in all companies to specify the information. To start the guide, on the **Intercompany Partner** page, use the **Connect Externally Setup** action.  

-->

## Related resources

- [Demand forecasting overview](../master-planning/introduction-demand-forecasting.md)  
- [Master planning with demand forecasts](../master-planning/planning-optimization/demand-forecast.md)  
