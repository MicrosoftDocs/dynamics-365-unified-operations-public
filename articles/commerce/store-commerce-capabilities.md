---
title: Store Commerce app capabilities
description: This article describes the functionality that is available in the Store Commerce app for Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 04/26/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2022-09-30

---

# Store Commerce app capabilities

[!include [banner](includes/banner.md)]

The Store Commerce app is the modern point of sale (POS) experience for Microsoft Dynamics 365 Commerce. It enables businesses to process transactions in-store and manage back-office operations such as inventory and order-proccessing. The app also enables businesses to manage customer relationships with loyalty and clienteling. 

Powered by Commerce Scale Unit (CSU), the Store Commerce app provides a complete omni-channel solution. For example, a customer can buy a product online and pick it up in a nearby store, thereby continuing their shopping journey across channels without losing any data. 

This article provides an overview of the Store Commerce app capabilities.

## Platform

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Omni-channel | Dynamics 365 Commerce delivers a comprehensive omni-channel solution that unifies back-office, in-store, call center, and digital experiences. | [Overview](index.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/dynamics-365-commerce-overview-november-2-2020) |
| Headless Commerce | The Commerce Scale Unit hosts the headless commerce engine. The headless commerce engine serves as the central point for all commerce business logic and powers a complete omni-channel solution. | <p>[Architecture overview](commerce-architecture.md)</p><p>[Headless architecture](dev-itpro/retail-server-architecture.md)</p> | [Tech talk](https://community.dynamics.com/365/b/techtalks/posts/dynamics-365-commerce-architecture-overview-december-4-2020) |
| Commerce headquarters | Commerce headquarters provides back-office capabilities that enable the configuration of products, employees, business processes, pricing, and other functionality that is required for the business. | [Architecture overview](commerce-architecture.md) | |
| Point of sale (POS) | The Store Commerce app is the POS experience for Dynamics 365 Commerce. It delivers feature-rich and comprehensive POS capabilities that help sales associates, cashiers, and managers provide superior customer service. In addition, it provides several deployment options to retailers, helps improve performance, and offers improved application lifecycle management (ALM). | [Store Commerce App](dev-itpro/store-commerce.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/modernize-the-dynamics-365-commerce-in-store-technology-using-the-new-store-commerce-app-march-30-2022)</p><p>[Video](https://youtu.be/7B332XH_zfs)</p><p>[Migration from MPOS to Store Commerce](dev-itpro/pos-extension/migrate-mpos-store-commerce.md)</p> |
| Cloud deployment | Multiple instances of Commerce Scale Units can be deployed for load distribution and geo proximity. | [Cloud deployment](../fin-ops-core/dev-itpro/deployment/cloud-deployment-overview.md) | |
| On-premises deploymen | Using a local business data deployment, Commerce customers can have greater ownership and management of a Dynamics 365 environments. | [On-premises deployment](../fin-ops-core/dev-itpro/deployment/deploy-retail-onprem.md) | |

## Device management

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Multiple form factors | The Store Commerce app is supported on multiple device form factors, such as PCs, tablets, and mobile devices. The responsive user interface (UI) enables the layout to automatically be resized and adjust to the screen size. | [Visual configurations](pos-screen-layouts.md) |  |
| Cross-platform | The Store Commerce app is supported on web, Windows, iOS, and Android platforms. | [Platforms](dev-itpro/hybridapp.md) | |
| Branding | The screen designer lets you customize screen layouts to meet your business requirements. In addition, themes, layouts, colors, and images can be created based on employee roles, and can then be shared across users for brand consistency and ease of use. | [Visual configurations](pos-screen-layouts.md) | [Video](https://www.youtube.com/watch?v=ldqCw2wf5fY) |
| Topology | Different in-store topologies are supported, based on network availability. | <p>[Topology](dev-itpro/retail-modern-pos-architecture.md)</p><p>[Infographic](dev-itpro/retail-in-store-topology.md)</p> | |
| Multi-device management | Multiple devices across stores can be easily managed from Commerce headquarters. | [Activation](set-up-activation-accounts-validate-devices-hq.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/commerce-mass-deployment-with-sccm-system-center-configuration-manager-october-6-2022) |

## Employee management

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Sign-in | Each store employee can have a dedicated sign-in. Sign-in types include user name, bar code, magnetic stripe reader (MSR), biometrics, and Azure Active Directory (Azure AD). | <p>[Azure AD](aad-pos-logon.md)</p><p>[Extended logon](extended-logon.md)</p> | |
| Permissions | Different levels of permissions are supported for employees, such as permission to create orders and permission to edit orders. | [Permissions](tasks/create-pos-permission-groups.md) | |
| Time and attendance management | Attendance can be managed by using the Time Clock function. Attendance data can be processed into payroll by using the Dynamics 365 Human Resources app. | [Time management](retail-time-attendance.md) | |
| Sales commission | Sales can be tracked by sales representative to calculate commissions or other incentives. | [Commission](pos-sales-groups-track-commissions.md) | |

## Merchandising

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Assortment management | Merchandising managers can assort products so that they are available for sale in a specific channel and during a specific period. | [Assortments](assortments.md) | |
| Catalogs | Merchandising managers can manage catalogs to identify the products that you want to offer with catalog-specific pricing. | [Catalogs](/dynamicsax-2012/appuser-itpro/about-retail-product-catalogs) | |
| Product and category management | In Commerce headquarters, merchandising managers can create products that have variants, attributes, a unit of measure, and so on. They can also define a category hierarchy to organize products. | [Product](retail-hierarchies.md) | |
| Bundles | Merchandising managers can group products so that they are sold as a bundle or kit. | [Kits](/dynamicsax-2012/appuser-itpro/about-setting-up-retail-product-kits) | |
| Info codes | Use info codes to prompt the cashier to enter information during different actions at the POS, such as item sales, item returns, or customer selection. | [Info codes](/dynamicsax-2012/appuser-itpro/about-info-codes-retail) | |
| Linked items | Use linked items to upsell products when an item is added to transaction. | [Linked items](/dynamicsax-2012/appuser-itpro/set-up-products-for-cross-selling-and-up-selling) | |
| Warranties | Extended warranties can be sold together with products. | [Warranty](extended-warranty.md) | |
| Label printing | Labels can be generated that contain product information such as the batch number, serial number, and expiration date. | [Label printing](/dynamicsax-2012/appuser-itpro/create-and-print-labels-overview) | |

## Assisted selling

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Product browsing | Browse products by category. | [Product hierarchy](retail-hierarchies.md) | |
| Product search | Search products by name, and refine searches by using product attributes such as the brand, price, and material. This capability is powered by Azure Cognitive Search. | [Cloud powered search](cloud-powered-search-overview.md) | |
| Product details page | Rich product details pages can include images, a description, product attributes, and recommended products. Recommendations are powered by the Recommendations Service. | | |
| Product compare | Compare multiple products, and help customers choose one and add it to a transaction. | | |
| Endless aisle | Easily look up inventory in other stores, and create orders. | [Inventory lookup](pos-inventory-lookup-operation.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021)</p> <p>[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSx)</p> |
| Recommendations | Upsell and cross-sell products by using the Recommendations Service. This service uses patented technology to suggest recommendations, based on purchase trends, and characteristics such as newly arrived, similar looks, and bestselling. These recommendations are available on product details pages, the **Customer details** page, and the **Transactions** page. | [Recommendations](product-recommendations.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/unlock-the-power-of-dynamics-365-commerce-recommendations-march-2-2021) |

## Customer relationship

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Customer management | Create, edit, and manage customer accounts. Customer accounts can be managed in async mode to avoid real-time processing. | [Management](customer-mgmt-stores.md) | |
| Customer attributes | The Customer attributes framework enables additional customer related data to be captured based on business requirements. | [Attributes](dev-itpro/customer-attributes.md) | |
| Customer details page | A rich customer details page provides an omni-channel view of the customer's interactions across all channels. These interactions include purchases, wish lists, and loyalty points. | | |
| Cloud-powered customer search | Search customers by name, telephone number, email address, loyalty card, address, and so on. | [Cloud powered search](pos-search-improvements.md#customer-search) | |
| Loyalty and rewards | Customers can join loyalty programs, and earn and redeem loyalty points across channels. | [Loyalty](set-up-customer-loyalty-program.md) | [Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5c2wW) |
| Clienteling | Manage key customers by using a client book, and track activities and notes on the customer profile. Dynamics 365 Customer Insights integration lets store employees get cues about the next best action for each customer. | [Clienteling](clienteling-overview.md#activities-and-notes) | [Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSP) |

## Pricing and discounts

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Trade agreements | Pricing managers can use trade agreements to define special prices, based on long-term deals for specific customers. | [Pricing](price-management.md)| [Video](https://www.youtube.com/watch?v=r2VD8IxHesM) |
| Sales agreements | Pricing managers can use sales agreements to define contract-based prices in business-to-business (B2B) commerce scenarios. | [Pricing](price-management.md) | |
| Price adjustments | Pricing managers can use the price adjustments capability to create, track, and manage price markdowns for their products over time. | [Price adjustments](price-adjustments-discounts.md) | |
| Discounts | Pricing managers can set up several types of discounts to run a variety of promotions. These discounts include simple discounts, quantity discounts, threshold discounts, mix and match discounts, tender-based discounts, and shipping discounts. | [Discounts](retail-discounts-overview.md) | |
| Coupons | Pricing managers can set up coupon codes or bar codes, link them to discounts, and distribute them to customers. Sales associates can add coupons to sales transactions or remove them. | [Coupons](coupons.md) | |
| Price groups | Pricing managers can use the price group capability to define contextual prices, based on channels, catalogs, affiliations, or loyalty programs. | [Pricing](price-management.md) | |
| Available promotions | Sales associates can easily look up available promotions for products in the store, products that have been added to a transaction, and so on. | [Pricing functions](pos-pricing-functions.md) | |
| Price checks | Sales associates can quickly check active sales prices of products in the store. | [Pricing functions](pos-pricing-functions.md) | |
| Price overrides | Sales associates who have the required permissions can override system-configured or calculated prices. | [Pricing functions](pos-pricing-functions.md) | |
| Manual discounts | Sales associates who have the required permissions can apply manual discounts to sales transaction or sales lines. | [Pricing functions](pos-pricing-functions.md) | |

## Electronic payments

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Credit and debit | The Store Commerce app supports major credit and debit card payments through Adyen Payment Gateway and order fulfillment through PayPal. The Payments SDK allows for external gateway connections that are supported by independent software vendor (ISV) integrations. | <p>[Adyen](dev-itpro/adyen-connector.md?tabs=10-0-23)</p><p>[PayPal](paypal.md)</p><p>[Payments](payment-methods.md)</p> | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/unlock-the-power-of-dynamics-365-commerce-omni-channel-payment-configuration-february-9-2021)</p><p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/unlock-the-power-of-dynamics-365-commerce-omni-channel-payment-overview-processing-february-4-2021)</p> |
| Digital wallet support | The Store Commerce app supports payments through digital wallet payment methods that don't use Bank Identification Number (BIN) ranges as traditional credit and debit cards do. Payment methods can be mapped to digital wallet payments such as Adyen. | [Wallet](wallets.md) | |
| Gift card support | Bank Identification Number Dynamics 365 gift card, Stored Value Solutions (SVS), and Givex gift cards. Gift cards can be purchased and redeemed in an order. | [Gift cards](dev-itpro/gift-card.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/d365-commerce-internal-gift-cards-november-16-2021) |
| Fraud protection | Dynamics 365 Fraud Protection help you prevent fraudulent activity and identify places where fraud might be unnoticed. | [Fraud protection](dev-itpro/dfp.md) | [Video](https://www.youtube.com/watch?v=j_1nEiq3LfM) |

## Taxes and charges

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Taxes | The Store Commerce app supports many types of indirect taxes, such as sales tax, value-added tax (VAT), goods and services tax (GST), unit-based fees, and withholding tax. | [Taxes](/dynamics365/finance/general-ledger/indirect-taxes-overview?toc=%2Fdynamics365%2Fcommerce%2Ftoc.json) | |
| Charges | Charges can be configured at the line level, at the header level, as auto-charges, by channel, and so on. | [Charges](omni-auto-charges.md) | |

## Order processing and fulfillment

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Order creation | An order can be created for shipment or for pickup at a nearby store. Time slots can be provided for pickup. | [Overview](customer-orders-overview.md) | |
| Order modification | An order can be modified, returned, canceled, and so on. | <p>[Cancel](customer-orders-overview.md#cancel-a-customer-order)</p><p>[Returns](pos-returns.md)</p> | |
| Search | Search for and filter orders by using order-specific information. | [Search](enhancedorderrecall.md) | |
| Order attributes | The Order attribute framework enables additional order-related information to be captured based on business requirements. | [Attributes](dev-itpro/order-attributes.md) | |
| Direct delivery | Items can be marked for direct delivery by a vendor to a customer address. Direct delivery is also known as drop shipping. | [Direct delivery](/dynamics365/supply-chain/sales-marketing/tasks/ship-orders-direct-deliveries) | |
| Quotation | Store employees can create quotations for customers, and can specify a special price, manual discounts, and a quotation validity date. | [Quotation](/dynamics365/supply-chain/sales-marketing/tasks/create-edit-sales-quotations) | |
| Fulfillment | Stores can pick, pack, and ship orders. A packing slip can be added to the packages that are ready for shipment. | [Fulfillment](order-fulfillment-overview.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/unlock-the-power-of-dynamics-365-commerce-supporting-buy-online-pickup-in-store-curbside-with-dynamics-365-commerce-pos-february-3-2021)</p> <p>[Video](https://www.microsoft.com/videoplayer/embed/RE5bRXE)</p>|
| Distributed order management | The Store Commerce app supports intelligent order fulfillment optimization where business strategies can be configured based on the nature of the business, the type of customer, the origin of an order, and the delivery method for an order. | [DOM](dom.md) | [Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bRYl)|

## Inventory management

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Buyer's push | Streamline the distribution of available inventory from a distribution center to multiple stores or warehouses. | [Buyer's push](tasks/set-up-rules-parameters-cross-docking-buyers-push.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Cross-docking | Streamline the distribution of inventory on incoming purchase orders to multiple stores or warehouses. | [Cross docking](tasks/set-up-rules-parameters-cross-docking-buyers-push.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021) |
| Inbound inventory | Receive inventory from a vendor via a purchase order, or from another warehouse via a transfer order. Create an inbound purchase order or transfer order request. | [Inbound](pos-inbound-inventory-operation.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021)</p>  <p>[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSx)</p>|
| Outbound inventory | Ship inventory to another warehouse via a transfer order, and create an outbound transfer order request. | [Outbound](pos-outbound-inventory-operation.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021)</p>  <p>[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSx)</p> |
| Inventory lookup | Check on-hand inventory for products across stores and warehouses, and check available-to-promise (ATP) inventory on future dates. | [Inventory lookup](pos-inventory-lookup-operation.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021)</p> <p>[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSx)</p> |
| Inventory adjustment | Adjust inventory into or out of a store warehouse to meet specific business requirements without using a sale, receipt, or recount. | [Inventory adjustment](work-with-store-inventory.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021)</p> <p>[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSx)</p>|
| Stock counts | Count physical inventory, and adjust the system bookkeeping inventory to match it. | [Counting](work-with-store-inventory.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021)</p> <p>[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSx)<p> |
| Inventory movement | Move inventory between locations in a store. | [Movement](work-with-store-inventory.md) | <p>[Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-dynamics-365-commerce---store-inventory-may-13-2021)</p> <p>[Video](https://www.microsoft.com/en-us/videoplayer/embed/RE5bMSx)</p> |

## Financials

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Cash management | The Store Commerce app supports management of cash and other specified tenders in the store. In addition, shift reconciliation in the store can be enabled for advanced cash management capabilities. | [Cash](cash-mgmt.md) | |
| Financial statements and reconciliation | Cash and transactional transactions for a store are recorded in Commerce headquarters through the statement posting processes. | [Statements](retail-statements.md) | |
| Income and expense transactions | Process petty cash transactions in the store, and record income that doesn't come in the traditional way, such as lost-and-found money, the share of revenue from a coffee shop in your lobby, and carpet cleaning services. | [Statements](retail-statements.md) | |
| Invoice payments | Capture payments against invoices. | [Invoice](payinvoice.md) | |

## Employee productivity

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Task management | Create task lists and tasks, and assign them to stores and employees. Track the status of tasks across stores. Seamless integration with Microsoft Teams is provided. | <p>[Task Management](task-mgmt-overview.md)</p><p>[Microsoft Teams](commerce-teams-integration.md)</p> | [Video](https://www.youtube.com/watch?v=ES1whB4C2lU) |

## Hardware and peripherals

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Connect peripherals | Connect peripherals such as printers, cash drawers, scanners, and payment devices to a POS terminal. | [Peripherals](retail-peripherals-overview.md)<br/><br/>[Network peripherals](dev-itpro/network-peripherals.md) ||
| Share peripherals | Receipt printers, cash drawers, and payment devices can be shared among many terminals by connecting them to a shared hardware station. | [Hardware station](retail-peripherals-overview.md) ||
| POS and peripheral simulator | The peripheral simulator supports testing of scenarios that usually require physical POS peripheral devices. It also includes a POS simulator that can be used to test the compatibility of physical peripheral devices without requiring deployment of the POS client. | [Peripheral simulator](dev-itpro/retail-peripheral-simulator.md) | |
| POS health check | Point of sale users can test the connectivity and functionality of peripherals such as printers, payment terminals, and bar code scanners. Health check also provides the ability to test the network performance for a POS terminal, as well as its connectivity to the Commerce Scale Unit and Retail Server. | [Health check](pos-healthcheck.md) | [Video: Health check for Dynamics 365 Commerce point of sale](https://www.youtube.com/watch?v=3BaU9ciY-1o&ab_channel=MicrosoftDynamics365Community) |

## Receipts

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Print receipts | Receipts of various types, such as sales receipts, credit card receipts, gift receipts, and invoices, can be printed by default or after cashier confirmation at checkout. They can also be reprinted from the journal. | [Printing](receipt-templates-printing.md) | |
| Email receipts | Receipts can be emailed from the POS after a checkout is completed. | [Email](email-receipts.md) | |
| Design receipts | Store receipts can be customized so that they show data and layouts that are appropriate to the retailer and transaction type. Receipts can also be extended so that they show custom data that is required by the retailer. | [Design](receipt-templates-printing.md) | |

## Offline support

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Seamless offline | Seamless offline lets you continue to transact even when internet connectivity is limited or unavailable. Data exclusion helps you reduce the data size of the offline databases and maximize performance. | [Offline](pos-operations.md) | |
| Performance-based switching | Switch to offline when performance degradation is detected. | [Offline](dev-itpro/implementation-considerations-offline.md) | [Video](https://youtu.be/sQU-2pgHToI) |
| Offline dashboard | The **Offline status** dashboard shows the offline status, errors, and details of the data for each device. Therefore, it's easy to manage the status of many devices. | [Offline](dev-itpro/implementation-considerations-offline.md) | [Video](https://youtu.be/sQU-2pgHToI)|

## Extensibility

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Commerce headquarters | Commerce headquarters solutions can be customized by adding or modifying business processes. Commerce headquarters supports the use of metadata and a code-driven extension model to add custom functionality. It can be easily integrated into external solutions. | [Overview](dev-itpro/extend-customer-cdx-package.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-unlock-the-power-of-dynamics-365-commerce-commerce-extensibility-overview-february-23-2021) |
| Headless commerce | The Extensible Omni-channel API framework can be used to customize and add business logic. APIs that have request handlers, and pre-trigger and post-trigger extension patterns. | [CSU](dev-itpro/retail-server-customer-consumer-api.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-series-commerce-extensions) |
| Commerce SDK | The Commerce SDK includes the code, code samples, templates, and tools that are required to extend or customize Dynamics 365 Commerce functionality. The SDK is published in different repositories (repos) in GitHub, depending on the extension components. | [SDK](dev-itpro/retail-sdk/sdk-github.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-series-commerce-extensions) |
| Point of sale | Store Commerce app can be extended independently by using the POS extension feature of the Commerce SDK. The framework supports customization of the user experience (UX), workflows, and business logic. | [POS](dev-itpro/pos-extension/pos-extension-overview.md) | [Tech talk](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-series-commerce-extensions) |

## Reporting

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Sales reports | Sales reports by staff, register, payment type, returns, product, and so on, are available to store managers. Managers can view these reports, and use them to allocate commission and identify product trends. | | |

## Diagnostics

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Operational insights | Store-curated service health reliability and performance metrics are available in the customer's Application Insights subscription. Advanced alerting and monitoring capabilities are available. | | |
| Health check | Availability of peripherals that are connected to a POS can be verified by running the health check operation. Individual peripheral issues can then be fixed and verified. | [Health check](pos-healthcheck.md) | [Video](https://www.youtube.com/watch?v=RfPDNmnqYvY) |

## Globalization

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Multi-market support | Market-specific features such as fiscal integration, GST, advanced invoicing, and prepayments are supported out of the box. This capability covers several markets in Europe, the Americas, Russia, Asia, Saudi Arabia, and so on. | [Globalization](localizations/fiscal-integration-for-retail-channel.md) | |

## Compliance

| Capability | Description | Documentation | Supplemental content |
|---|---|---|---|
| Microsoft standards | The Store Commerce app meets Microsoft standards for security, privacy, accessibility, the General Data Protection Regulation (GDPR), the European Union (EU) Data Boundary, and so on. | | |

