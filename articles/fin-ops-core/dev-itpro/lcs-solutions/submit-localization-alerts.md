---
title: Submit alerts about country/region-specific regulatory features
description: This article describes how to use Microsoft Dynamics Lifecycle Services (LCS) to submit alerts through the Localization and translation service.
author: kfend
ms.date: 12/14/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: kfend
ms.search.region: global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: b37140b4-5d6f-460f-ae36-f0d7bd90c0d3
---

# Submit alerts about country/region-specific regulatory features

[!include [banner](../includes/banner.md)]

This article describes how to use Microsoft Dynamics Lifecycle Services (LCS) to submit alerts through the  Dynamics regulatory alert submission service. This article also explains how to track planned and released regulatory features through LCS Issue search. 

## Accessing the regulatory alert submission service

To access the regulatory alert submission service, in your project or a project you are invited to in Dynamics Lifecycle Services (LCS), do one of the following:
- From the menu, select **Alert service**.
- Scroll to the right side of the page, and under **More tools**, select **Alert service**. 

The **Dynamics regulatory alert submission** page appears. You can use this page to view any alerts that have previously been submitted by you or your organization.

## Submitting a regulatory alert
To enter a new regulatory alert, click the plus sign (**+**) at the top of the **Dynamics regulatory alert submission** page, above the filter. The **Alert submission** wizard starts. You can complete the following tasks in this wizard:

- Search for existing regulatory items.
- Describe an alert.
- Confirm submissions.

### Search for existing regulatory items

Use Issue search to identify whether a regulatory feature, that is related to the alert, already exists.

1.  Enter a search term, such as a keyword, country/region, Microsoft Knowledge Base (KB) number, or Application Object Tree (AOT) object. Click the search button. Any items that include the search term, in either product issues or regulatory features, appear in the search results. You can narrow the search by using the filters that are available.
2.  If you don't find the regulatory feature that you're looking for, you can submit a regulatory alert by clicking **Submit regulatory alert** at the bottom of the browser window. 

### Describe the alert

1. Enter information about the alert in the appropriate fields. Required fields are indicated by a red asterisk. The following table provides more information about the fields on the **Describe the alert** page.

    <table >
            <tr>
                <td >
                <p><strong>Field</strong></p>
                </td>
                <td >
                <p><strong>Description</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Title</p>
                </td>
                <td>
                <p>Enter a descriptive title to identify the area of impact. For example, enter <strong>Changes in invoice document as of January 1, 2018</strong>.</p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Description</p>
                </td>
                <td>
                <p>Enter a brief overview of the law. Your description should focus on issues that are relevant to enterprise resource planning (ERP), so that users can understand the requirements at a high level without having to read the legislation first. </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Country</p>
                </td>
                <td>
                <p>Select the country or region that the legislation applies to. </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Industry</p>
                </td>
                <td>
                <p>Select the industry, if the requirement applies only to specific industries. For example, select <strong>Public sector</strong>, <strong>Commerce</strong>, or <strong>Manufacturing</strong>. </p><br/>            </td>
            </tr>
            <tr>
                <td>
                <p>Feature reference</p>
                </td>
                <td>
                <p>Enter the feature reference, if you know it.</p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Law enforcement date</p>
                </td>
                <td>
                <p>Select the date when affected customers must start to comply with the law.  </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Government announcement date</p>
                </td>
                <td>
                <p>Select the date when the authority announced the change. </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Latest filing date</p>
                </td>
                <td>
                <p>Select the deadline for the first submission of the new or changed report.     </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Link to legislation </p>
                </td>
                <td>
                <p>Enter one or more links to the published law, interpretation guideline, implementation guidance, or any other useful documentation that will help users understand or implement the requirement.</p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Company name</p>
                </td>
                <td>
                <p>Enter the company name for the person who is submitting the alert.         </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Contact name</p>
                </td>
                <td>
                <p>Enter the name of the person who is submitting the alert.     </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Contact email</p>
                </td>
                <td>
                <p>The email address of the person who is submitting the alert.   </p>
                </td>
            </tr>
            <tr>
                <td>
                <p>Business process</p>
                </td>
                <td>
                <p>The business processes that you selected through the <strong>Alert submission</strong> wizard.</p>
                </td>
            </tr>
            <tr>
                <td>Comments</td>
                <td>
                <p>Enter any additional information that might be help users understand or implement the requirement. Click <strong>Submit</strong> to save your comment. Multiple comments can be added and should be submitted separately. Comments are saved in the order that they are added. </p>
                </td>
            </tr>
            <tr>
                <td> Attachments </td>
                <td> <p>Click the <strong>Upload</strong> button, and then browse to select a file to add as an attachment. After you select the file, it&#39;s uploaded and appears as a linked file. You can add up to three files that have a size of 5 MB each. To delete files that have been attached, click <strong>Remove</strong> under the title of the file. <strong>Note</strong> Attachments must be publicly available materials. They can&#39;t be propriety or customer-specific/partner-specific.</p>
                </td>
            </tr>
    </table>

2.  After you've finished entering all the information, select the consent check box (**By submitting this regulatory alert, I consent to Microsoft contacting me for additional information about this alert. Microsoft Privacy Statement.**). When you select the check box, the **Submit** button becomes available.
3.  Click **Submit** to save and submit the alert.

If you don't have all of the required information, or if you're not yet ready to submit the alert, you can save a partially completed alert.

### Confirm your submission

-   When the alert is successfully submitted, you receive a confirmation message. Click **Done** to exit the wizard.
-   If you save the alert before you submit it, an alert ID is generated, and you receive confirmation that the alert has been saved.

## Track the status of regulatory features in Issue search
You can use Issue search in LCS to find planned and released regulatory features, and any associated localization documentation, certifications, and reports. To narrow your search to regulatory features, use the following filters:

-   **Category** - Select **Regulatory feature** only.
-   **Country/region** - Click **&gt;** to select the country/region that you're interested in.

To narrow the search even more, you can apply the following additional filters

-   **Product** - Select the products and product versions that you're interested in.
-   **Status** - Select specific statuses.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
