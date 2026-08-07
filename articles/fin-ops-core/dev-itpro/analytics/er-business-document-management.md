---
title: Business document management overview
description: Learn about how to use the Business document management feature of the ER framework, including learning about online editing in Microsoft 365 (Word/Excel for the web) and supported Microsoft Office applications.
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 08/06/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.search.form: ERBDWorkspace, ERBDParameters, ERSecurityAccessEditor
ms.dyn365.ops.version: 10.0.5
ms.assetid: 
ms.custom: sfi-image-nochange
---

# Business document management overview

[!include [banner](../includes/banner.md)]

Business users use the **Business document management** (BDM) workspace to configure formats for outbound documents in accordance with the legal requirements of various countries or regions or company-specific needs. **Business document management** is built on top of the [Electronic reporting (ER)](general-electronic-reporting.md) framework and enables business users to edit business document templates by using Microsoft 365 Apps for business or an appropriate Microsoft 365 desktop applications. Edits to the documents might include changing business document designs and adding placeholders for extra data without source code changes and new deployments. Updating business document templates doesn't require any prior knowledge of the ER framework.

The ER framework generates outbound documents in Excel and Word formats by using predefined templates. The templates are populated with required data according to the configured dataflow while required documents are generated. Each configured format can be published as part of an ER solution to generate specific outbound documents. This process is represented by an ER format configuration that can contain templates you can use to generate different outbound documents.

> [!NOTE]
> **Business document management** enables you to modify templates that are used to produce business documents such as orders, invoices, and more. When you modify a template and publish a new version, the system uses this version to generate required business documents. You can't use Business document management to modify already generated business documents.

## Supported deployments

Currently, the **Business document management** workspace is implemented only for cloud deployments. If this feature is critical to your on-premises deployment, provide feedback on the [Ideas](https://experience.dynamics.com/ideas/) site.

## Supported Microsoft 365 and Office applications

To use **Business document management** for editing templates in Excel or Word formats by using Microsoft Office desktop applications, you must have Microsoft Office 2010 or later installed and a configured **SharePoint** integration to host the files during editing. This support is available in cloud and on-premises deployments.

To use **Business document management** for editing templates in Excel or Word formats to edit templates online in Microsoft 365 (Word or Excel for the web), you must have a Microsoft 365 Office for the web subscription and a configured **SharePoint** integration to host the files during editing.

## Additional resources

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[ER Design a configuration for generating reports in OPENXML format (November 2016)](tasks/er-design-reports-openxml-2016-11.md)

[Design ER configurations to generate reports in Word format](tasks/er-design-configuration-word-2016-11.md)

[Embed images and shapes in documents that you generate by using ER](electronic-reporting-embed-images-shapes.md)

[Configure Electronic reporting (ER) to pull data into Power BI](general-electronic-reporting-report-configuration-get-data-powerbi.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
