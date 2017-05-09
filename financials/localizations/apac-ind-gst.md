---
# required metadata

title: Overview to India GST | Microsoft Docs
description: This article describes the solution architecture and overview to India GST. Microsoft will release a default configuration that enables the capabilities needed by the India GST regulation update. The partners and customers can choose to either use the default configuration or extend it for specific requirements. The reporting is taken care by leveraging Generic Electronic Reporting solution for the GSTR reports.
author: ShylaThompson
manager: AnnBe
ms.date: 0000-00-00 00:00:00
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
# audience: 
# ms.devlang: 
ms.reviewer: ShylaThompson
# ms.suite: 
# ms.tgt_pltfrm: 
ms.custom: 1587884
ms.assetid: d3ccc142-0027-4675-9a7c-84dab4f2e6f7
ms.region: Global
# ms.industry: 
ms.author: leguo

---

# Overview to India GST

This article describes the solution architecture and overview to India GST. Microsoft will release a default configuration that enables the capabilities needed by the India GST regulation update. The partners and customers can choose to either use the default configuration or extend it for specific requirements. The reporting is taken care by leveraging Generic Electronic Reporting solution for the GSTR reports.

Overview
========

India government is about to introduce Goods and Services Tax (GST). Microsoft Dynamics AX in-market versions are planned to provide compliance capability to the regulatory update. This article lays out the overall approach of leveraging the Generic Tax Engine (GTE) to meet the compliant with India GST. Below chart displays the overall flow to GST solution. This article will discuss overview on the approach. Please find more detailed documentations for each of the steps. [![India GST Overview](./media/india-gst-overview-1024x368.png)](./media/india-gst-overview.png)

Configurations on cloud
=======================

Step 1 is to have the configurations ready. **Configuration** refers to the set of data defining tax rules such as when a particular tax should be applied (Tax applicability), how it should be calculated (Tax calculation), how to account it for (Posting and Accounting), and how to accumulate the input tax credit and tax liabilities (Credit pool); or the activities of defining it. The configuration is done using Generic Tax Engine that is available on Dynamics 365 for Operations. We are leveraging the trial experience of the Dynamics 365 for Operations to provide the configuration box. Microsoft will release a configuration. The customers and partners can choose to use it out of the box, or extend it for their own requirements. The configuration is viewable also on the Dynamics 365 for Operations.

Download and load
=================

Step 2 is to download and load. The configuration can be downloaded as xml file. The configuration that Microsoft releases will contain 3 files. If partner has extension, it can be more files. Then the users needs to load the configuration files in their local box of Dynamics AX 2012 or Dynamics AX 2009.

Tax setup
=========

Step 3 is to setup the tax contents, such as tax rates, main accounts etc. The main difference between configuration and setup is the access to customer specific master data. When it requires the access to customer specific master data, the user needs to provide the setup in the tax setup. For example, the exact value of tax rate, the exact account number of tax recoverable posting etc. These data are required to run the GTE runtime to apply, calculate, post and account for taxes. Set off rules are to be determined here also, for rule-based tax settlement.

Transactions and tax
====================

Step 4 is to enter transactions and GTE will process taxes according to configuration and setup. It is important to notice that GTE does not use the traditional mechanism to determine tax, which is the combination of sales tax group and item sales tax group. GTE implements a rule based configurable engine for the tax applicability. Refer to the configuration part for more details on what is tax applicability and how to configure it.

Settle and reports
==================

Step 5 is to settle the tax recoverable and tax payable to calculate the final tax payment amount. The settlement engine support rule based settlement, which can set off the recoverable and payable across different tax types and tax components. With the settlement results, it is possible to generate required reports. In India GST context, the return reports are called GSTRs (GST-R1, GST-R2 etc). We are leveraging Generic Electronic Reporting (GER) for the reporting strategy. The GER contents are available at: [Electronic reporting overview](https://authoring.help.dynamics.com/en/?post_type=incsub_wiki&p=285041)

