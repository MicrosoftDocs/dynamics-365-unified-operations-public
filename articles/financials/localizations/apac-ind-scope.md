---
# required metadata

title: Scope of India localization
description: This topic provides information about the strategy and scope of the tax, finance, and accounting laws regulations in India that were implemented as part of Microsoft Dynamics 365 for Finance and Operations. 
author: kfend
manager: AnnBe
ms.date: 08/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form:
audience: IT Pro, Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.suite: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.scope: Core, Operations
# ms.search.industry: 
ms.author: ralin
ms.dyn365.ops.version: 7.3.1
ms.search.validFrom: 2019-6-21
---


# Scope of India localization

[!include [banner](../includes/banner.md)]

Generally, Microsoft deploys significant resources to generate the business process functionality of Microsoft Dynamics applications by developing the features and functionality to address certain tax accounting or financial regulatory requirements in countries where Microsoft Dynamics is generally available. 
Microsoft Dynamics 365 for Finance and Operations helps business operations to comply with country-specific laws, regulations, and common business practices for handling routine activities. The software is designed with features and functionality that address specific central and state government taxes, accounting, and financial or statutory reporting laws or regulations that usually govern business in India. However, because laws and regulations are diverse and numerous, Microsoft Dynamics 365 for Finance and Operations does not cover all laws, regulations, or commercial requirements in India. For example, regulatory features that Microsoft develops and makes generally available for Microsoft Dynamics 365 for Finance and Operations in India do not usually support industry-specific laws or national standards, particular state-specific laws, or city or municipal law requirements except as is specifically noted in this topic. 
Following the global strategy to deliver Finance and Operations, channel partners are a very important part of the process and their deliberation crystallizes the thought process and helps Microsoft to design a roadmap to achieve excellence in localization requirements. The flexible, need-based architecture of Finance and Operations is useful for channel partners in addressing a customer’s specific business needs during development, configuration, and implementation. Although channel partners may provide solutions that meet specific regulatory requirements that are unique to cities, states, or other regions in India, Microsoft does not provide any guarantees or warranties (expressed, implied, statutory, or otherwise) that partner-created solutions comply with local business, tax, and regulatory, legal, or other applicable requirements. Channel partners or customers are solely responsible for any configurations, customizations, localizations, or translations (including any update for each of the same) that they create or implement on behalf of customers. This includes any support or other service that is provided to customers for such solutions. User must contact their channel partner for information about the solutions that they create for licensed versions of Finance and Operations. 
This topic outlines the strategy and scope of localization that Microsoft has implemented as part of the version of Finance and Operations that is commercially available in India. 

## Definitions

**Customization**: 

- Any configuration, modifications, or changes that are made by partners or customers to Microsoft Dynamics software or, when applicable, software documentation to fit a customer’s specific business needs, such as adding or renaming fields or tables, creating custom reports, or integrating with third-party solutions.
- Any software developed by or for partners or customers for the Microsoft Dynamics software.

**Localization**: Any modification to, addition to, or adaptation of Microsoft Dynamics software to enable or include certain features or functionality in the software to comply with applicable regulatory requirements. This includes but is not limited to, versions and updates of the Microsoft Dynamics software, user assistance tools, or end-user documentation. Examples of laws or regulatory requirements that may require localization of software include local tax reporting (GST, Customs and Tax Deduction at Source (TDS)/Tax collection at source (TCS)), specific law driven- tax calculations (reverse charge, price exclusive, and price inclusive tax), local accounting rules, and local regulatory and statutory reporting.

**National Standards**: Local requirements that are not required by law or regulation but are widely adopted inside a geographic region and are critical to the sale of licenses for business management software in that geographic region.

## India localization strategy
To address the tax (direct and indirect), financial accounting, and statutory reporting requirements for India, the strategy that was adopted by Microsoft is to provide localizations for Finance and Operations. This strategy consists of:   

- Meet the Central-level tax requirements that are described in the India localization scope section.
- Meet state- and region-specific tax requirements if they are generic across all states in India. 
- Meet tax requirements on export and import transactions.
- Deliver new regulatory feature requirements through configurations or new development according to the localization scope and rules that are specified in this topic and implementation opportunities that are driven by the Finance and Operations roadmap.
- Deliver new regulatory features for all supported versions of Finance and Operations.

> [!NOTE]
> There is no focus on requirements of specific businesses, segments, verticals, regions, even when this is required by laws, statutes, or regulations at the federal, state, or city levels. City-specific tax requirements, except for those that are described in the India localization scope section, are not included.

There are specific laws and requirements that are out of scope for Finance and Operations. Localization that is developed by Microsoft for Finance and Operations is limited to the features and functionality that are described in this document. Therefore, the localization  must be analyzed by prospective customers or a tax professional, such as an accounting and tax auditor, a tax law firm, or a tributary consulting firm who can perform an assessment to determine whether the functionality will meet the customer’s business needs, or whether custom solutions are required. 

## India localization scope
Finance and Operations localization provides a configuration for language user interface and Help settings. India localization is available in English-IN. Additional documentation such as white papers and comprehensive training materials are also available in English. 
The localization scope for Finance and Operations in India is limited to fiscal and financial accounting transactions in the following areas: 

- Tax 
- General ledger
- Accounts payable
- Accounts receivable
- Inventory management
- Product information and Management 
- Organization and management 
- Project and service anagement  
- Fixed assets
- Retail 

The features that Microsoft delivers and supports as part of the India localization for Finance and Operations are listed later in this topic. 

## Market availability 
Microsoft tries to deliver regulatory updates and changes with enough time for installation and implementation. Our goal is to release tax and regulatory updates to be incorporated into Microsoft Dynamics 365 for Finance and Operations in advance of the effective date or other date that is mandated by the tax authorities, regardless of whether it is central or state government tax, so that our channel partners can acquaint themselves with features and have enough time to update their customer solutions. Internally, we call this delivery date the “market required date” (MRD). 
We try to meet our established MRDs and dates that are mandated by the various government authorities. However, various factors can adversely affect the timely delivery of tax and regulatory updates. These include the following: 
•	Legislative or regulatory changes that are made by the government with short notice before the date of law enforcement
•	Feature, functionality, infrastructure, or architectural limitations of the affected software versions that are generally available in the marketplace 
•	Complexity and coverage of the coding, redesign, or improvement of the software that is required to implement the legislation or regulatory requirements 
•	Schedule conflicts
In any situation in which Microsoft finds it difficult to meet these dates, we use reasonable efforts to develop and release tax and regulatory updates as soon as possible.
Disclaimer: 
Any dates that Microsoft publishes are for planning only and are subject to change at any time without notice.
Microsoft makes no representations, warranties, or guarantees about the timeliness or completeness of any tax or regulatory updates it provides and, to the maximum extent permitted under applicable law, disclaims all implied warranties and conditions, such as implied warranties or conditions of merchantability and fitness for a particular purpose. 

## Localization India: Key benefits 
- Configurable localization of [GTE](../general-ledger/tax-engine) and [GER](../../dev-itpro/analytics/general-electronic-reporting) offers key major benefits:

  - Extensibility in transaction type: A unified model is used in the tax calculation. Adding additional transaction types will require additions only to the model mapping.
  - Extensibility in tax calculation: Formula-based calculation can be completed by a power user.
  - Extensibility in tax behavior: Configurable tax posting and accounting and configurable settlement rule
  - Extensibility in tax return 
  - Database independent
  - Easy to upgrade
  - Lean 
  
- Generated as configuration in XML format 
- Base configurations, India GST and GSTR are provided by Microsoft 
- ISV can create their own configurations on top of Microsoft software
- Delta customization is supported for configuration
- India localization is enabled to work in parallel with the standard Dynamics 365 features in a global environment
- The registration-number details of the company, vendors, and customers regarding GST and direct taxes can be stored at a centralized location
- Flexible tax settlement process where tax settlement hierarchy can be defined based on the users needs
- User-definable inquiry forms provide the relevant information that is used for statutory reporting
- Users can make manual adjustments of taxes before they run the periodic tax settlement process
- Component depreciation is calculated according to the Companies Act and Income tax Act of India, as required by the user

## Localization India: Key tax areas that are covered 
The key features that are covered in this localization are as follows. 
•	Direct taxes 
o	Tax deduction at source (TDS) 
o	Tax collection at source (TCS)
•	GTE (Generic Tax engine) and GER (Generic Electronic Reporting)
o	Configurable tax engine 
o	Tax calculation, accounting logic and report are now configuration instead of code Selection of multiple tax bases 
o	Allow the functional consultants to make the configuration alongside with a power user and confirm the outcome instantly
o	The lead time can be counted in days or even hours before a user can try out how the system is likely to work. Faster interaction with the user would lead to higher satisfaction and less project risk
•	GST 
o	Outward supplies: 
	B2B sales
	B2C sales
	Export sales
•	Goods
•	Services 
	Deemed export 
	Sales
•	Non-GST items 
•	Zero rated goods/services
•	Exempted goods/services 
	Reverse charge sales
	E-commerce sales 
o	Inward supplies: 
	Supply from registered vendor 
	Supply from composite vendor
	Supply from unregistered vendor 
	Supply from reverse charge vendor 
	Supply from foreign vendor 
•	General import 
•	Import from Associate enterprise 
	Supply of exempted goods/Services
	Supply of Non-GST items
•	Depreciation on fixed assets 
o	Depreciation as per Companies Act,2013
	Component depreciation accounting 
	Depreciation as per reducing balance with residual value 
o	Depreciation as per Income Tax Act,1961
	Depreciation as per block of assets
	Depreciation as per >180 or <180 days 
•	GST Report 
o	GSTR -1 Govt. offline tool
o	GSTR -1 
o	GSTR -2 

•	Retail 
	Intrastate and interstate transactions 
	Normal sales
	Customer order
	Return order
	GST price inclusive
	GST price exclusive
	Discounts and offers
	Exempted sales
	Replenishment
	Uniform invoice number and POS receipt number 

## India localization features
Finance and Operations India localization provides a configurable tax engine that enables users to comply with the complex Indian statutory requirements by doing extension in configuration. 
![Tax document page](media/india-scope-01.png)

The following table lists the localization features that are supported in Finance and Operations. Any specific feature that is not listed in this table is not supported in the current localization version.


