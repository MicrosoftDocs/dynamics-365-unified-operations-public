---
title: Store Commerce app capabilities
description: This article describes the functionality available in the Store Commerce app for Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 10/03/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2022-10-31
ms.dyn365.ops.version: 10.0.28
ms.custom: 
ms.assetid: 
ms.search.industry: Retail
---

# Store Commerce app capabilities

[!include [banner](includes/banner.md)]

The Store Commerce app is the retail point of sale (POS) experience for Microsoft Dynamics 365 Commerce. It delivers feature-rich and comprehensive POS capabilities that help sales associates, cashiers, and managers provide superior customer service. This document provides an overview of the Store Commerce app capabilities. 

## Platform

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Omni-channel | Dynamics 365 Commerce delivers a comprehensive omnichannel solution that unifies back-office, in-store, call center, and digital experiences. | [Overview]() | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/dynamics-365-commerce-overview-november-2-2020) |
| Headless commerce | Headless Commerce engine serves as the central point for all commerce business logic and powers a complete omni-channel solution. | <p>[Architecture overview]()</p><p>[Headless architecture](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/retail-server-architecture) | [Tech talk](https://community.dynamics.com/365/b/techtalks/posts/dynamics-365-commerce-architecture-overview-december-4-2020) |
| Headquarters | Commerce Headquarters provides back-office capabilities that enable the configuration of products, employees, business processes, pricing and other functionality that is required for the business. | [Architecture overview](https://docs.microsoft.com/dynamics365/commerce/commerce-architecture) | |
| Cloud Deployment | Multi-instance deployment of Commerce Scale Units for load distribution and geo proximity. | | |
| Point-of-sale | Store Commerce app is the point-of-sale experience for Microsoft Dynamics 365 Commerce. It delivers feature-rich and comprehensive point of sale capabilities that help sales associates, cashiers and managers provide superior customer service. In addition, it provides several deployment choices to retailers, helps improve performance, and offers improved application lifecycle management (ALM). | [Store Commerce App](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/store-commerce) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/modernize-the-dynamics-365-commerce-in-store-technology-using-the-new-store-commerce-app-march-30-2022)</p><p>[Release video](https://youtu.be/7B332XH_zfs)</p><p>[Migration from MPOS to Store Commerce](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/pos-extension/migrate-mpos-store-commerce) |

## Device Management

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Multi-form factor | Supported on multiple device form factors such as PC, Tablet and Mobile. Responsive UI allows the layout to automatically re-size and adjust to screen size. | [Visual configurations](https://docs.microsoft.com/dynamics365/commerce/pos-screen-layouts) | |
| Cross-platform | Supported on Web, Windows, iOS, and Android. | [Platforms](https://learn.microsoft.com/dynamics365/commerce/dev-itpro/hybridapp) | |
| Branding | Screen layouts can be customized using our Screen Designer to meet business requirements. In addition, theme, layout, color, images can be created based on employee role and shared across users for brand consistency and ease of use. | [Visual configurations](https://docs.microsoft.com/dynamics365/commerce/pos-screen-layouts) | [Video](https://www.youtube.com/watch?v=ldqCw2wf5fY) |
| Topology | Various in-store topologies are supported based on network availability. | <p>[Topology](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/retail-modern-pos-architecture)</p><p>[Infographic](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/retail-in-store-topology)</p> | |
| Multi-device management | Multiple devices across stores can be easily managed from Headquarters | [Activation](https://learn.microsoft.com/dynamics365/commerce/set-up-activation-accounts-validate-devices-hq) | |

## Employee Management

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Logon | Each store employee can have a dedicated login with login types such as username, barcode, MSR, biometrics, AAD etc. | <p>[AAD](https://docs.microsoft.com/dynamics365/commerce/aad-pos-logon)</p><p>[Extended logon](https://docs.microsoft.com/dynamics365/commerce/extended-logon)</p> | |
| Permissions | Different level of permissions is supported for employees such as create order, edit order etc. | [Permissions]() | |
| Time and attendance management | Attendance can be managed using the Time Clock function. This data can be processed into payroll using the Dynamics 365 Human Resources app. | [Time management](https://docs.microsoft.com/dynamics365/commerce/retail-time-attendance) | |
| Sales commission | Sales can be tracked by sales representative to calculate commissions or other incentives. | [Commission]() | |

## Merchandising

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Assortment management | Merchandising managers can assort products assort to be available in a specific channel for sale and during a specific period | [Assortments](https://docs.microsoft.com/dynamics365/commerce/assortments) | |
| Catalog | Merchandising managers can manage catalogs to identify the products that you want to offer with a catalog-specific pricing. | [Catalogs](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/about-retail-product-catalogs) | |
| Product & Category management | Merchandising managers can create products with variants, attributes, unit of measure etc. via Headquarters. They can define a category hierarchy to organize products | [Product](https://docs.microsoft.com/dynamics365/commerce/retail-hierarchies) | |
| Bundle | Merchandising managers can group products to be sold as a bundle/kit. | [Kit]() | |
| Info codes | Use info codes to prompt the cashier to enter information during various actions at the POS, such as item sales, item returns, or selecting customers. | | |
| Linked items | Use linked items to upsell products when an item is added to transaction. | | |
| Warranty | Extended warranties can be sold along with products. | [Warranty](https://learn.microsoft.com/dynamics365/commerce/extended-warranty) | |
| Label printing | Labels can be generated to contain product information including batch number, serial number and expiration date. | [Label printing](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/create-and-print-labels-overview) | |

## Assisted selling

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Product browsing | Browse products by category. | [Heirarchy](https://docs.microsoft.com/dynamics365/commerce/retail-hierarchies) | |
| Product search | Search products by name and refine using product attributes such as brand, price, material etc. Powered by Azure Cognitive Search. | [Cloud powered search](https://docs.microsoft.com/dynamics365/commerce/cloud-powered-search-overview) | |
| Product details page | Rich product details page with images, description, product attributes and recommended products. Recommendation powered by Recommendation service. | | |
| Product compare | Compare multiple products, help customer decide and add to transaction. | | |
| Endless aisle | With Endless aisle, easily lookup for inventory in other stores and create an order. | [Inventory lookup](https://docs.microsoft.com/dynamics365/commerce/pos-inventory-lookup-operation) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Recommendations | Upsell and cross-sell products using the Recommendations Service which uses patented technology to suggest recommendations based on purchase trends, newly arrived, similar looks, bestselling etc. These recommendations are available on the PDP, Customer details page and Transactions page. | [Recommendations]() | |

## Customer Relationship

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Customer accounts | Create, edit, and manage customer accounts. Customer accounts can be managed in async mode to avoid real time | [Accounts]() | |
| Customer attributes | Customer attributes framework allows additional customer related data to be captured as per business requirements | [Attributes](https://learn.microsoft.com/dynamics365/commerce/dev-itpro/customer-attributes) | |
| Customer details page | Rich customer details page with an omni-channel view of the customer's interactions across all channels including purchases, wish list, loyalty points etc. | | |
| Cloud powered customer search | Search customers by Name, Phone, Email, Loyalty card, Address etc. | [Cloud powered search](https://docs.microsoft.com/dynamics365/commerce/pos-search-improvements#customer-search) | |
| Loyalty & Rewards | Customers can join, earn and redeem loyalty points across channels. | [Loyalty](https://docs.microsoft.com/dynamics365/commerce/set-up-customer-loyalty-program) | |
| Clientelling | Manage key customers with a client book and track activities/notes on the customer profile. With Dynamics 365 Customer Insights integration, store employees can get cues on the next best action for each customer. | [Clientelling](https://docs.microsoft.com/dynamics365/commerce/clienteling-overview#activities-and-notes) | |

## Pricing and discounts

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Trade agreements | Pricing managers can use trade agreements to define special prices based on long-term deals for specific customers. | [Pricing]() | [Video](https://www.youtube.com/watch?v=r2VD8IxHesM) |
| Sales agreements | Pricing managers can use sales agreement to define contract-based prices in B2B commerce scenarios. | [Pricing]() | |
| Price adjustments | Pricing managers can use the price adjustments capability to create, track and manage price markdowns for their products over time. | [Pricing]() | |
| Discounts | Pricing managers can set up several types of discounts to run a variety of promotions. Those include simple discount, quantity discount, threshold discount, mix & match discount, tender-based discounts, and shipping discount. | [Discounts]() | |
| Coupons | Pricing managers can set up coupon codes or barcodes, link them to discounts, and distribute them to customers. Sales associates can add coupon(s) into or remove coupon(s) from sales transactions. | [Coupons](https://learn.microsoft.com/dynamics365/commerce/coupons) | |
| Price group | Pricing managers can use price group capability to define contextual prices based on channel, catalog, affiliation, or loyalty program. | [Pricing](https://learn.microsoft.com/dynamics365/commerce/price-management) | |
| Available promotions | Sales associates can easily lookup available promotions for products in-store, products added to the transaction etc. | [Pricing functions](https://learn.microsoft.com/dynamics365/commerce/pos-pricing-functions) | |
| Price check | Sales associates can quickly check active sales prices of products in-store. | [Pricing functions](https://learn.microsoft.com/dynamics365/commerce/pos-pricing-functions) | |
| Price override | Sales associates can override system configured or calculated prices within granted permissions. | [Pricing functions](https://learn.microsoft.com/dynamics365/commerce/pos-pricing-functions) | |
| Manual discount | Sales associates can apply manual discounts to sales transaction or sales lines within granted permissions. | [Link](https://learn.microsoft.com/dynamics365/commerce/pos-pricing-functions) | |

## Electronic Payments

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Credit and debit | Support for major credit and debit card payments through Adyen Payment Gateway and order fulfillment with PayPal. Payments SDK allows for external gateway connections supported by ISV integrations. | <p>[Adyen](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/adyen-connector?tabs=10-0-23)</p><p>[PayPal](https://learn.microsoft.com/dynamics365/commerce/paypal)</p><p>[Payments](https://docs.microsoft.com/dynamics365/commerce/payment-methods)</p> | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/unlock-the-power-of-dynamics-365-commerce-omni-channel-payment-configuration-february-9-2021)</p><p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/unlock-the-power-of-dynamics-365-commerce-omni-channel-payment-overview-processing-february-4-2021)</p> |
| Digital Wallet support | Support for payments using digital wallet payment methods that do not use BIN ranges like traditional credit and debit cards. Payment methods can be mapped to digital wallet payments such as Adyen. | [Wallet](https://docs.microsoft.com/dynamics365/commerce/wallets) | |
| Gift card support | Supports Dynamics 365 gift card, SVS and Givex gift cards. Gift cards can be purchased/redeemed in an order. | [Gift cards](https://learn.microsoft.com/dynamics365/commerce/dev-itpro/gift-card) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/d365-commerce-internal-gift-cards-november-16-2021) |
| Fraud protection | Prevent fraudulent activity and identify places where fraud might be unnoticed with Dynamics 365 Fraud Protection. | [Fraud protection](https://learn.microsoft.com/dynamics365/commerce/dev-itpro/dfp) | [Video](https://www.youtube.com/watch?v=j_1nEiq3LfM) |

## Taxes & Charges

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Taxes | Supports many types of indirect taxes, such as sales tax, value-added tax (VAT), goods and services tax (GST), unit-based fees, and withholding tax. | [Taxes](https://docs.microsoft.com/dynamics365/finance/general-ledger/indirect-taxes-overview?toc=%2Fdynamics365%2Fcommerce%2Ftoc.json) | |
| Charges | Charges can be configured at line level, header level, auto-charges, by channel etc. | [Charges](https://docs.microsoft.com/dynamics365/commerce/omni-auto-charges) | |

## Order Processing & Fulfillment

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Order creation | An order can be created for shipping or pick-up at a nearby store. Timeslots can be provided for pickup. | [Overview]() | |
| Order modification | An order can be modified, returned, cancelled etc. | <p>[Cancel](https://docs.microsoft.com/dynamics365/commerce/customer-orders-overview#cancel-a-customer-order)</p><p>[Returns](https://docs.microsoft.com/dynamics365/commerce/pos-returns)</p> | |
| Search | Search and filter orders using order-specific information | [Search](https://docs.microsoft.com/dynamics365/commerce/enhancedorderrecall) | |
| Order attributes | Order attribute framework allows additional order related information to be captured based on business needs | [Attributes](https://learn.microsoft.com/dynamics365/commerce/dev-itpro/order-attributes) | |
| Direct delivery | Items can be marked for direct delivery aka drop shipping by a vendor to a customer address | [Direct delivery](https://docs.microsoft.com/dynamics365/supply-chain/sales-marketing/tasks/ship-orders-direct-deliveries) | |
| Quotation | A store employee can create quotations for the customer along with a special price, manual discounts, and a quotation validity date. | [Quotation](https://docs.microsoft.com/dynamics365/supply-chain/sales-marketing/tasks/create-edit-sales-quotations) | |
| Fulfillment | Stores have the ability to pick, pack and ship orders. A packing slip can be added to the packages that are ready to ship | [Fulfillment](https://docs.microsoft.com/dynamics365/commerce/order-fulfillment-overview) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/unlock-the-power-of-dynamics-365-commerce-supporting-buy-online-pickup-in-store-curbside-with-dynamics-365-commerce-pos-february-3-2021) |
| Distributed Order Management | Support for intelligent order fulfillment optimization with configurable business strategies based on nature of business, type of customer, origin of order and delivery method for an order | [DOM](https://docs.microsoft.com/dynamics365/commerce/dom) | |

## Inventory Management

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Buyer's push | Streamline the distribution of available inventory from distribution center to multiple stores / warehouses. | [Buyer's push]() | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Cross docking | Streamline the distribution of inventory in incoming purchase order to multiple stores / warehouses. | [Cross docking](https://docs.microsoft.com/dynamics365/commerce/tasks/set-up-rules-parameters-cross-docking-buyers-push) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Inbound inventory | Receive inventory from vendor via purchase order or another warehouse via transfer order. Create inbound purchase order or transfer order request. | [Inbound]() | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Outbound inventory | Ship inventory to another warehouse via transfer order, create outbound transfer order request. | [Outbound](https://docs.microsoft.com/dynamics365/commerce/pos-outbound-inventory-operation) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Inventory lookup | Check products' on-hand inventory across stores / warehouses and APT (available to promise) inventory on future dates. | [Inventory lookup](https://learn.microsoft.com/dynamics365/commerce/pos-inventory-lookup-operation) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Inventory adjustment | Adjust inventory in or out of store warehouse to accommodate specific business needs without sale, receipt, or recount. | [Inventory adjustment](https://learn.microsoft.com/dynamics365/commerce/work-with-store-inventory) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Stock count | Count physical inventory and adjust system bookkeeping inventory to match | [Counting](https://learn.microsoft.com/dynamics365/commerce/work-with-store-inventory) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Inventory movement | Move inventory between locations within a store. | [Movement](https://learn.microsoft.com/dynamics365/commerce/work-with-store-inventory) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |

## Financials

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Cash management | Supports cash and other specified tender management within the store. Shift reconciliation within the store can be enabled for advanced cash management capabilities as well. | [Cash](https://docs.microsoft.com/dynamics365/commerce/cash-mgmt) | |
| Financial statement and reconciliations | Store cash and transactional transactions are recorded in Headquarters through the statement posting processes. | [Statements]() | |
| Income and expense transactions | Process petty cash transactions within the store as well as to record income that doesn't come in the traditional way such as lost and found money, revenue share from a coffee shop in your lobby, carpet cleaning services. | [Statements]() | |
| Invoice payments | Capture payments against invoices | [Invoice](https://docs.microsoft.com/dynamics365/commerce/payinvoice) | |

## Employee Productivity

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Task Management | Create task-lists and tasks, assign to stores and employees. Track the status of tasks across stores. Seamless integration provided with Microsoft Teams. | <p>[Task Management](https://docs.microsoft.com/dynamics365/commerce/task-mgmt-overview)</p><p>[Teams](https://learn.microsoft.com/dynamics365/commerce/commerce-teams-integration)</p> | [Video](https://www.youtube.com/watch?v=ES1whB4C2lU) |

## Hardware & Peripherals

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Connect peripherals | Connect peripherals such as printers, cash drawers, scanners and payment devices to a point-of-sale terminal | <p>[Peripherals](https://docs.microsoft.com/dynamics365/commerce/retail-peripherals-overview)</p><p>[Hardware station]()</p> | |
| Share peripherals | Receipt printers, cash drawers and payment devices can be shared among many terminals by connecting them to a shared hardware station. | <p>[Peripherals](https://docs.microsoft.com/dynamics365/commerce/retail-peripherals-overview)</p><p>[Hardware station]()</p> | |
| POS and peripherals simulator | Peripheral Simulator supports testing of scenarios that usually require physical POS peripheral devices. Peripheral simulator also includes a POS simulator which can be used to test the compatibility of physical peripheral devices without having to deploy the POS client. | [Simulator]() | |

## Receipts

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Print receipts | Receipts of various types such as sales receipt, credit card receipt, gift receipt, invoices etc. can be printed by default or on cashier confirmation at checkout. They can also be reprinted from the journal. | [Printing](https://docs.microsoft.com/dynamics365/commerce/receipt-templates-printing) | |
| Email receipts | Receipts can be emailed from POS after a checkout is completed. | [Email](https://docs.microsoft.com/dynamics365/commerce/email-receipts) | |
| Design receipts | Store receipts can be customized to display data and layouts that are appropriate to the retailer and transaction type. Receipts can also be extended to display custom data required by the retailer. | [Printing](https://docs.microsoft.com/dynamics365/commerce/receipt-templates-printing) | |

## Offline support

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Seamless offline | With seamless offline, continue to transact even when internet connectivity is limited or unavailable. Data exclusion allows to reduce the data size of the offline databases and maximize performance. | [Offline]() | |
| Performance based switching | Switch to offline when a performance degradation is detected | [Offline](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/implementation-considerations-offline) | [Video](https://youtu.be/sQU-2pgHToI) |
| Offline dashboard | Offline status dashboard shows the offline status, error, and details of the data for each device making it easy to manage the status of many devices | [Offline]() | |

## Extensibility

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Headquarters | Commerce headquarters solutions can be customized to add/modify business processes. It supports metadata and code driven extension model to add custom functionality. It can be easily integrated into external solutions. | [Overview]() | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-unlock-the-power-of-dynamics-365-commerce-commerce-extensibility-overview-february-23-2021) |
| Headless commerce | Extensible Omni channel API framework to customize and add business logic, and APIs with request handlers and pre/pot trigger extension patterns. | [SDK]() | |
| Point of sale | Framework supports customizing UX, workflows and business logic. Store Commerce SDK includes the code samples, templates, and tools that are required to add, extend, or customize existing functionality. The SDK supports Azure DevOps integration for source, build and package management. | [POS](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/pos-extension/pos-extension-overview) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-series-commerce-extensions) |

## Reporting

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Sales Reports | Sales reports available by staff, register, payment type, returns, product etc. for store managers to view, allocate commission and identify product trends. | | |

## Diagnostics

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Operational Insights | Store curated service health reliability and performance metrics available in the customers Application Insights subscription. Advanced alerting and monitoring capabilities | | |
| Health check | Availability of peripherals connected to a point of sale can be verified by running the health check operation. Individual peripheral issues can then be fixed and verified. | [Health check](https://docs.microsoft.com/dynamics365/commerce/pos-healthcheck) | [Release video](https://www.youtube.com/watch?v=RfPDNmnqYvY) |

## Globalization

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Multi-market support | Market specific features such as Fiscal integration, GST, Advanced invoicing, pre-payments etc. supported out-of-box. This covers several markets in Europe, Americas, Russia, Asia, Saudi Arabia etc. | [Globalization](https://docs.microsoft.com/dynamics365/commerce/localizations/fiscal-integration-for-retail-channel) | |

## Compliance

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Microsoft standards | Meets Microsoft standards for Security, Privacy, Accessibility, GDPR, EUDB etc. | | |

