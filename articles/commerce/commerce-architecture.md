---
# required metadata

title: Commerce architecture overview
description: This topic provides an overview of all components in the Dynamics 365 Commerce ecosystem, including integration points to the suite of Dynamics 365 products.
author: samjarawan
manager: AnnBe
ms.date: 03/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: RetailITWorkspace
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 221954
ms.assetid: 8fe1b080-00d4-41ae-b047-10da160877ab
ms.search.region: Global
ms.search.industry: Retail
ms.author: samjar
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Commerce architecture overview

[!include [banner](includes/banner.md)]

This topic provides an overview of all components in the Dynamics 365 Commerce ecosystem, including integration points to the suite of Dynamics 365 products. The following diagram shows an overview of Dynamics 365 Commerce components.

![Commerce Architecture](./media/commerce-architecture-overview.jpg)

## Architecture Benefits
### Omni-Enabled Headless Commerce Engine
The commerce scale unit, which hosts the headless commerce engine, serves as the central integration point for all commerce business logic and powers a complete omni-channel solution across physical and digital stores. Built using a portable architecture it enables flexible hosting options across the cloud, edge, and hybrid topologies. The headless commerce engine powers all native Dynamics 365 Commerce channels, including in-store and e-Commerce channels. The headless commerce engine also serves as the single integration point for third party channel solutions to leverage the power of the Dynamics 365 Commerce business logic and integration with other commerce related services provided by Microsoft and ISVs.

### Inter-Connected Business Processes
The common platform between the various Dynamics 365 business applications, such as Dynamics 365 Commerce, Dynamics 365 Supply Chain Management, or Dynamics 365 Finance provide a set of inter-connected business processes that users can immediately leverage. All back-office capabilities across these applications are built on the same web experience and data stores, which enables seamless flow of business processes across various functions in the organization without the need for custom integrations across applications and services. The out-of-box integration between the headless commerce engine and the back-office further expands the coverage of these inter-connected business processes across the back-office and commerce channels. 

### Unified Data
The Dynamics 365 Commerce stack provides unified data solution through out-of-box integrations with [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) and the [Common Data Service](https://powerapps.microsoft.com/en-us/common-data-service/). Integrations and data sharing across Dynamics 365 business applications, such as Dynamics 365 Sales or Dynamics 365 Marketing, are seamlessly supported through the shared Common Data Service. Transactional data in the Azure Data Lake Storage is leveraged to power various analytics and insights scenarios that light up in the Dynamics 365 Commerce solution but can also be leveraged by any third-party integration.

### Powered by AI and analytics 
With accessible, persistent, up-to-date and unified organizational data available in Azure Data Lake, the entire organization has a single source of truth on top of which analytics, AI, and ML can be applied to derive insights and KPIs to optimize and automate business processes across all channels.

## Component overview
### End user experiences
#### Dynamics 365
Dynamics 365 is a collection of applications which together provide comprehensive and flexible ERP solution for medium to large businesses.   It provides an extensible framework and ecosystem which can be tailored to customer-specific requirements via our extensive set of partners.  Dynamics 365 provide capabilities for their target business segments, while leveraging each other as well other Microsoft services and offerings to provide a solution to help run our customer’s complex businesses.

#### POS
Retail Modern POS is a cross-flatform (Windows, iOS, Android), multi-formfactor (desktop, tablet, phone) solution for all in-store first line workers (cashiers, sales associates, stock clerks, and store managers).  It can be deployed as an as app with offline capabilities or in the cloud accessed through a web browser.  The application is role based and fully configurable from headquarters.  It is also highly customizable and can be extended or integrated into 3rd party services using the Retail SDK.
In addition to standard “cash and carry” transaction processing, the POS includes enables assisted selling, clienteling, endless aisle, order processing/fulfillment, inventory management, cash/shift management, and reporting. To learn more, review the [Modern POS (MPOS) architecture](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-modern-pos-architecture) or [Choose between Modern POS (MPOS) and Cloud POS](https://docs.microsoft.com/en-us/dynamics365/commerce/mpos-or-cpos).

#### E-Commerce Storefront
The e-commerce storefront is the end customer facing web site rendering system. Built on the React.js framework, it uses a combination server-side and client-side rendering to deliver responsive web experiences for one or more online channels. Highly customizable but with a rich set of out-of-box capabilities, the storefront delivers a performant and scalable solution for online business. To learn more, review [Online store overview](https://docs.microsoft.com/en-us/dynamics365/commerce/online-store-overview).

#### Site Builder
Site builder is the web-based authoring interface for the content management system and storefront web site rendering system. It provides a WYSIWYG editor for site managers and content authors who will perform the day-to-day workflow tasks of managing and producing the marketing content for the e-Commerce experience. Within site builder, a marketer can provide richer marketing detail for specific products enhancing the shopping experience for consumers.  In addition, site builder includes integrated accessibility reporting, URL management, site map generation, and image focal point management, among other features. To learn more, review [Online store overview](https://docs.microsoft.com/en-us/dynamics365/commerce/online-store-overview).

#### External Services and Apps
The Headless Commerce Engine exposed via the Commerce Scale Unit allows partners and customers to leverage all the same channel side capabilities and business logic that is used by the out-of-box e-Commerce and POS components. This allows seamless omni-channel capabilities across out-of-box channel components and partner/customer developed services and applications by tapping into the same data and business process capabilities. This also provides access to all out-of-box and ISV developed surround services that are available through the Commerce Scale Unit. 

### Back Office
#### Dynamics 365 Commerce HQ
The Dynamics 365 Commerce application, commonly referred to as the Commerce HQ component, provides back-office capabilities which enable the configuration of products, employees, business processes among other functionality necessary for the business.  Is it also the application used by call-center workers to provide assisted commerce related workflows. 

#### Dynamics 365 Supply Chain Management
[Dynamics 365 Supply Chain Management](https://dynamics.microsoft.com/en-us/supply-chain-management/overview/) provides functionality to manage your product throughout the supply chain life cycle from production through inventory and warehouse to transportation and distribution. To learn more, review the [Dynamics 365 Supply Chain Management help resources](https://docs.microsoft.com/en-us/dynamics365/supply-chain/index).

#### Dynamics 365 Finance
[Dynamics 365 Finance](https://dynamics.microsoft.com/en-us/finance/overview/) provides functionality manage your global finances in a modern and automated way.  For customers of the Dynamics 365 Commerce application, Dynamics 365 Finance offers an integrated experience for managing their stores and e-commerce financial statements alongside the rest of their operations. To learn more, review the [Dynamics 365 Finance help resources](https://docs.microsoft.com/en-us/dynamics365/finance/index).

#### Dynamics 365 Human Resources
[Dynamics 365 Human Resources](https://dynamics.microsoft.com/en-us/human-resources/overview/) allows businesses to have a complete view of their employee resources and manage them in a unified way.  It provides integrated experiences going from the hiring process, through workforce planning and employee time management. To learn more, review the [Dynamics 365 Human Resources help resources](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-welcome).

### Commerce Scale Unit
Retailers are distributed organizations where their business topography can be represented as a hub (HQ) and spokes (channel) model. Dynamics 365 Commerce supports this model by having head office capabilities (hub) as well as many distributed channel components (spokes) that can be deployed in-store (self-managed) or within nearby Azure datacenters (Microsoft managed). These spokes are called scale units as they represent physical isolation (a function of scale) and an atomic unit of update. 
To facilitate cloud and edge scenarios, a commerce scale unit comes as both a SaaS component managed by Microsoft (cloud scale unit) but is also available as a self-managed component that can be deployed locally (store scale unit). A single environment can have a mix and match of cloud and store scale units allowing organizations to tune their investments of operational overhead with network redundancy for poor connectivity on a per store basis. To learn more, review [selecting the right in-store topology with Dynamics 365 Commerce](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/retail-in-store-topology).

#### Cloud Scale Units (Microsoft-managed)
Each environment can have multiple scale units associated with it. Each scale unit can be independently serviced (updated) and can serve one or more channels across one or more legal entities. Each scale unit can be deployed to any of the supported Azure regions and multiple scale units can be deployed to the same region. The independent nature of each scale unit allows for phased roll-out of updates across a collection of channels.

#### Store Scale Units (Self-managed)
To accommodate scenarios where internet connectivity is poor or unreliable, being able to bring the cloud scale unit to the edge is highly desirable. For retailers, this typically means having a physical footprint within their store. A store scale unit provides the ability for retailers to bring the same business logic and capabilities running in the Azure cloud into their stores. In these cases, although in-store connectivity will presumably be more reliable, there will be additional overhead of self-managing these components in terms of monitoring and updates. To learn more, review [selecting the right in-store topology with Dynamics 365 Commerce](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/retail-in-store-topology).

### E-Commerce Platform
#### Content Management System 
A fully featured content management system is integrated directly into the e-commerce platform.  Along with rich indexing features, it provides life cycle management for marketing materials that supplement the product information managed by the headless commerce engine. including features for localization and multi-item publishing through releases. The system is built on top of scalable, resilient Azure infrastructure including Azure Active Directory and Azure Cosmos DB. 

#### Digital Asset Management 
Extending the content management store, the digital asset manager keeps track of images, videos, and file downloads served by the web storefront site. Its image resizer service optimizes downloaded images for different devices and contexts, enhancing performance while managing image quality. It integrates with Azure Media Services for efficient playback of video streams. 

#### Web Storefront
The content management system listed previously stores its pages as a series of modules. The storefront web server assembles those modules into the rendered HTML page. The web storefront is comprised of the rendering platform, the commerce data proxy and the extensibility layer. That base is supplemented by a set of modules that power a web-based commerce experience, the Store Starter Kit. Knowing that every business has unique requirements, the initial starter kit can be modified to meet the business’s needs or supplemented with extensions and modules developed by a partner.

### Commerce Surround Services
#### Dynamics 365 Fraud Protection
[Dynamics 365 Fraud Protection](https://docs.microsoft.com/en-us/dynamics365/fraud-protection/overview) is seamlessly integrated into the eCommerce checkout flows managed processed through the commerce scale unit. The connection to the service is auto provisioned with the commerce scale unit and customers who sign up for Dynamics 365 Fraud Protection can enable and configure the integration through the Dynamics 365 HQ experience. Once enabled, the service can operate either in “evaluate” mode to assess the effectiveness of the service or in “protect” mode to catch fraudulent transactions configured via business rules.
To learn more review the [Dynamics 365 Fraud Protection integration with Dynamics 365 Commerce](https://docs.microsoft.com/en-us/dynamics365/retail/dev-itpro/dfp) article.

#### Dynamics 365 Customer Insights
[Dynamics 365 Customer Insights](https://docs.microsoft.com/en-us/dynamics365/ai/customer-insights/overview) helps you build a deeper understanding of your customers by connecting data from various transactional, behavioral, and observational sources to create a 360-degree customer view and generate insights. Dynamics 365 Commerce allows the retailers to easily turn on the integration with the Dynamics 365 Customer Insights and display the generated insights on the Point of Sale. These insights e.g. Churn probability, Next best action, etc. are extremely valuable for the sales associate to have effective conversations with the customers and deliver a personalized shopping experience to the customers. To learn more, review the [Dynamics 365 Customer Insights integration with Dynamics 365 Commerce](https://docs.microsoft.com/en-us/dynamics365/commerce/clienteling-overview#integration-with-dynamics-365-customer-insights) article.

#### Bing for Commerce
[Microsoft Bing for Commerce](https://www.microsoft.com/en-us/bing/commerce) is seamlessly integrated into the Dynamics 365 Commerce to provide consistent product discovery & search experiences via commerce scale unit across all commerce channels. In Dynamics 365 HQ - retailers have an ability to configure boosting and sinking business rules for product discovery & search experiences (e.g. boost product discovery for products on discounts or remove the out-of-stock items). Enabling retailers to turn shopper frustration & site abandonment into active carts and converted sales.  This integration also provides an out-of-box ability for Retailer’s to allow their customers’ to use images to search and discover similar products from the catalog without describing it.

#### Product Recommendations
Microsoft Dynamics 365 Commerce can be used to show product recommendations on the e-Commerce website and point of sale (POS) device. Product recommendations are items that a customer might be interested in. The recommendations are based on the purchase trends of other customers in online and brick-and-mortar stores.

Product recommendations let customers easily and quickly find products that they want while they have an experience that serves them well. Cross-selling and upselling can even be used to help customers find additional products than they didn't originally intend to buy. When recommendations are used to help with product discovery, they can create more conversion opportunities, help increase sales revenue, and even help enhance customer satisfaction and retention.
To learn more, review the [Product recommendations overview](https://docs.microsoft.com/en-us/dynamics365/commerce/product-recommendations) article.

#### Commerce Analytics
Dynamics 365 Commerce’s prepackaged, business-managed Commerce Analytics solution provides retailers with intelligent insights across all touch points in the Commerce ecosystem by embedding Power BI reports in Dynamics 365 HQ as well as Point-of-sale systems. Commerce Analytics solution provides rich comprehensive set of out-of-box business & transactional reports, dashboards, and KPIs leveraging insights across all channels. The solution standardizes data from various sources, whether the data resides in transactional or behavioral or observational or external data sources into a unified data model hosted in Azure data lake. Allowing organizations to obtain a truly complete view for their business performance across channels – from discount promotions performance, monitoring web visits and activity, comparing in-store visits and purchases, online purchases, loyalty redemptions, or perform customer RFM analysis, etc. 

#### Ratings and Reviews
The ratings and reviews solution allows end-user customers to enter product reviews and ratings through the e-commerce storefront. Retailers can then show average ratings and review information across their e-commerce website. Azure Cognitive Services to offer automatic moderation of profane words in 40 languages. Because human approval isn't required, moderation costs are reduced. The system also offers moderator tools that can be used to respond to customer concerns, feedback, and take-down requests, and to address data requests from users. To learn more, review the [Rating and reviews overview](https://docs.microsoft.com/en-us/dynamics365/commerce/ratings-reviews-overview) article.
      
### Unified Data Components
#### Azure Data Lake
Customers who bring their own [Azure Data Lake Storage](https://docs.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) can take advantage of structured business data from back office operations and clickstream data from the eCommerce storefront. This data flows back into intelligence surround services like Product Recommendations, Customer Insights, or Commerce Analytics to power customer-centric business processes and end-user experiences which can be embedded back into the Dynamics 365 Commerce HQ, POS, and eCommerce storefront.
To learn more review the article to [Make Entity store available as Data Lake](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/data-entities/entity-store-data-lake).

#### Common Data Service
[Common Data Service](https://powerapps.microsoft.com/en-us/common-data-service/) is the unified data store that integrated the data from all your business applications. Dynamics 365 applications, such as Dynamics 365 Sales, Dynamics 365 Customer Service, or Dynamics 365 Commerce use the Common Data Service to store business data, which enables seamless cross business application scenarios and can power new scenarios through Power Apps or Power Automate. To learn more, review the article on [What is Common Data Service](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro).

