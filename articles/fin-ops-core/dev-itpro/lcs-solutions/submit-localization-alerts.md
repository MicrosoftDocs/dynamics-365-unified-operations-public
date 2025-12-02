---
title: Submit alerts about country/region-specific regulatory features
description: Learn about how to use Microsoft Dynamics Lifecycle Services to submit alerts through the Regulatory alert submission service.
author: filatovm
ms.author: evgenypopov
ms.topic: how-to
ms.date: 11/10/2025
ms.reviewer: johnmichalak
ms.search.region: global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b37140b4-5d6f-460f-ae36-f0d7bd90c0d3
---

# Submit alerts about country or region-specific regulatory features

[!include [banner](../includes/banner.md)]

This article describes how to use Microsoft Dynamics 365 Lifecycle Services to submit alerts through the Dynamics 365 regulatory alert submission service. This article also explains how to track planned and released regulatory features through Lifecycle Services Issue search. 

A regulatory alert is a notification for Microsoft about an **upcoming** (that is, not yet enforced) change in country or region-specific laws or regulations that might affect business processes supported in Dynamics 365 finance and operations apps. Microsoft processes such alerts and decides whether any changes in Dynamics 365 finance and operations apps are required to support the regulatory changes. Microsoft then releases corresponding [regulatory updates](../../../finance/localizations/global/regulatory-updates.md).

> [!IMPORTANT]
> Don't use the Dynamics regulatory alert submission service to communicate information about issues in existing regulatory features, missing regulatory features, or unsupported existing regulatory requirements. In such cases, contact Microsoft support for further guidance.

## Access the regulatory alert submission service

To access the regulatory alert submission service, in your project or a project you're invited to in Dynamics Lifecycle Services, do one of the following actions:
- From the menu, select **Alert service**.
- Scroll to the right side of the page, and under **More tools**, select **Alert service**. 

The **Dynamics regulatory alert submission** page appears. You can use this page to view any alerts that you or your organization previously submitted.

## Submit a regulatory alert
To enter a new regulatory alert, select the plus sign (**+**) at the top of the **Dynamics regulatory alert submission** page, above the filter. The **Alert submission** wizard starts. You can complete the following tasks in this wizard:

- Search for existing regulatory items.
- Describe an alert.
- Confirm submissions.

### Search for existing regulatory items

Use Issue search to find out if a regulatory feature related to the alert already exists.

1.  Enter a search term, such as a keyword, country/region, Microsoft Knowledge Base (KB) number, or Application Object Tree (AOT) object. Select the search button. The search results show any items that include the search term, in either product issues or regulatory features. You can narrow the search by using the available filters.
1.  If you don't find the regulatory feature that you're looking for, you can submit a regulatory alert by selecting **Submit regulatory alert** at the bottom of the browser window. 

### Describe the alert

1. Enter information about the alert in the appropriate fields. Required fields are indicated with a red asterisk. The following table provides more information about the fields on the **Describe the alert** page.

    | Field | Description |
    |-------|-------------|
    | Title | Enter a descriptive title to identify the area of impact. For example, enter **Changes in invoice document as of January 1, 2018**. |
    | Description | Enter a brief overview of the law. Your description should focus on issues that are relevant to enterprise resource planning (ERP), so that users can understand the requirements at a high level without having to read the legislation first. |
    | Country/region | Select the country or region that the legislation applies to. |
    | Industry | Select the industry, if the requirement applies only to specific industries. For example, select **Public sector**, **Commerce**, or **Manufacturing**. |
    | Feature reference | Enter the feature reference, if available. |
    | Law enforcement date | Select the date when affected customers must start to comply with the law. |
    | Government announcement date | Select the date when the authority announced the change. |
    | Latest filing date | Select the deadline for the first submission of the new or changed report. |
    | Link to legislation | Enter one or more links to the published law, interpretation guideline, implementation guidance, or any other useful documentation that help users understand or implement the requirement. |
    | Company name | Enter the company name for the person who is submitting the alert. |
    | Contact name | Enter the name of the person who is submitting the alert. |
    | Contact email | The email address of the person who is submitting the alert. |
    | Business process | The business processes that you selected through the **Alert submission** wizard. |
    | Comments | Enter any other information that might help users understand or implement the requirement. Select **Submit** to save your comment. You can add multiple comments, and you should submit them separately. Comments are saved in the order that you add them. |
    | Attachments | Select the **Upload** button, and then browse to select a file to add as an attachment. After you select the file, it's uploaded and appears as a linked file. You can add up to three files that are 5 MB each. To delete attached files, select **Remove** under the title of the file. **Note** Attachments must be publicly available materials. They can't be proprietary or customer-specific/partner-specific. |

1.  After you finish entering all the information, select the consent check box (**By submitting this regulatory alert, I consent to Microsoft contacting me for more information about this alert. Microsoft Privacy Statement.**). When you select the check box, the **Submit** button becomes available.
1.  Select **Submit** to save and submit the alert.

If you don't have all of the required information, or if you're not yet ready to submit the alert, you can save a partially completed alert.

### Confirm your submission

-   When the alert is successfully submitted, you receive a confirmation message. Select **Done** to exit the wizard.
-   If you save the alert before you submit it, an alert ID is generated, and you receive confirmation that the alert is saved.

## Track the status of regulatory features in Issue search
You can use Issue search in Lifecycle Services to find planned and released regulatory features, and any associated localization documentation, certifications, and reports. To narrow your search to regulatory features, use the following filters:

-   **Category** - Select **Regulatory feature** only.
-   **Country/region** - Select **>** to select the country or region that you're interested in.

To narrow the search even more, you can apply the following filters:

-   **Product** - Select the products and product versions that you're interested in.
-   **Status** - Select specific statuses.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
