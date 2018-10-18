---
# required metadata

title: Set up offer management
description: This topic describes how to set up offers in Talent.
author: josaw
manager: AnnBe
ms.date: 10/18/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2018-10-18
ms.dyn365.ops.version: AX 7.0.0

---
# Set up offer management 

[!include [banner](includes/banner.md)]

Once a candidate is moved to the offer stage in Dynamics 365 for Talent: Attract, you need to ensure that the
offers can be quickly created for the candidate, approved as necessary, and sent
out to the candidate. Most of the offers are standard in that they can be created
from reusable templates to reduce the time to offer. In Attract, all
offers are rolled into an offer package, which is a collection of one or
more offer documents. 

This topic lists all the steps that an Attract administrator would follow to set up different offer package templates as part
of the offer management capability in Attract. Users with non-administrator roles will not have access to these capabilities.

>[!NOTE]
> Offer management capabilities are available as part of the Comprehensive Hiring Add-On.

## Offer data 

Offer data is the smallest unit inside the offer package template. Any typical offer consists of standard text and a set of values. The sets of values are the only pieces that could change between offer to offer. During the offer creation, the number one thing the offer creator can focus on is the list of offer data placeholders present in any offer package template. To set up offer
data, do the following.

1.  Navigate to **Offer management**.

1.  Expand the **Library** section in the left navigation pane, then go to **Offer data**.

    >[!NOTE]
    > On the **Offer data** page are the **Candidate details** and **Job details** sections. Attract provides a few offer data placeholders out-of-the-box.
    
    > There are sections on the page to organize different offer data placeholders together in logical groups. These sections can help with maintenance of offer data and population of data during the offer creation process.

1.  To create new offer data section, click **Add a section** and enter a unique name for the section.

1.  To add offer data placeholders to any section, click **Add offer data** and enter a unique name for the placeholder.

1.  To edit the name of any section, hover over the section name and update the name.

1.  To edit the name of any existing offer data placeholder, first make sure that the placeholder is not already part of any template. Then, hover over the name of the offer data placeholder and update the name as desired.

1. To delete an existing offer data placeholder, first make sure that the placeholder is not part of any other template. Then, hover over the placeholder and when the trash-can icon appears, click the trash can to delete the offer data placeholder.
    >[!NOTE]
    > You can see how many templates an offer data placeholder is part of by the number indicator next to each offer data. 

1. To delete any section, hover over the name. If none of the offer data placeholders inside the section appear in any template, you can click the trash-can icon to delete it. 
    >[!NOTE]
    > Deleting the section will also delete all the offer data placeholders inside that section.

Once the offer data placeholders have been set up, you can use them across any document template. Offer data placeholders are no longer restricted to a specific template -- the same set can be used across all templates.

## Offer data rules

Most organization have rules for how offers must be created. For example, an organization may want to require that the max annual salary offer for a specific location and seniority level combination has to be within a certain range, or that there are only a few specific values possible for the offer level for the new hire. Attract currently supports all such data rules via CSV file that are uploaded.

To prepare the data rules CSV file, do the following.

1.  Determine the offer data placeholder for which the rule set is. For example, **Annual Salary**.

1.  Identify the dependent offer data placeholder values. For example, **Job Location** and **Level**.

1.  Specify columns 1 and 2 as **Job Location** and **Level**.

1.  To upload a range value, make columns 3 and 4 **Annual Salary**. To upload a specific value instead of a range, only make column
    3 **Annual Salary**.

1.  Populate the Excel file per your required roles.

1.  Ensure each row is a unique combination of all the values put together.

1.  Save the file as a CSV format.

To upload the offer data rules file, do the following.

1.  Navigate to **Offer management**.

1.  Expand the **Library** section in the left navigation panel, then go to **Offer data rules**.

1.  Click **+ New data set** to bring up the **Upload** dialog box.

1.  Specify a unique name for the rule set and then upload the saved csv file.

1.  Click **Add**.
    The rule set will be processed in the background and you will be notified in-app and via email once it completes.

    You will be notified if there are errors while processing the upload. You can then download the error log, fix the file, and re-upload.

1.  Use the **…** option if you want to download the rule set and update the set of values. After updating, you can upload the file again.

1.  You can delete an existing rule set upload if the placeholder being defined is not being used in any document template.

>[!Important]
> - Each placeholder can only have one unique set of columns that it is dependent on. For example, if **Annual Salary** is dependent on **Job Location** and **Level**, you can't upload another rule set where **Annual Salary** is dependent on a different set of columns.

> - You can download sample offer data rule sets on the **Samples** tab of the **Offer data rules** page.

> - When an offer creator overrides the values that are recommended by the offer data rules, the offer is flagged as non-standard and offer approval workflow will be mandated.

## Document templates

Offer document templates help administrators create the offer letters, these are
combination of the text that maybe part of the offer as well as the offer data
placeholders defined. To create offer document templates:

1.  Navigate to offer management.

2.  Expand the library section in the left navigation panel and go to
    **Templates**.

3.  You will see the document templates defined already.

4.  To create a new one, click **+ New Template** button

5.  Enter a unique name for the template and click **Create**

6.  Use the rich text editor capability to insert/edit the offer document
    content.

7.  You can insert offer data placeholders in to the offer template document by:

    1.  **Drag and drop the placeholder** from the right panel on to the
        document to the right place

    2.  **Hashtag** the offer data placeholder directly to the position
        required. **Type \#** and start typing the name of the offer data
        placeholder and the drop-down list will search across the list and show
        you the correct one. Click in and or press Enter to insert the offer
        data placeholder

8.  You can insert tables, images and hyperlinks using the options available at
    the top of the text editor.

9.  If you want to associate a placeholder to the offer document template but
    not expose its value to the candidate, hover over the offer data placeholder
    and click the **Pin** icon. This will push the placeholder to the **Pinned
    offer data** section of the offer document template. To unpin, follow the
    same method and click **unpin** icon amongst the list of offer data
    placeholders

10. To view the list of active offer data placeholders, switch to the **Active**
    tab in the right panel.

11. If you insert a placeholder which was driven by an offer data rule set, you
    can see the dependency of that offer data placeholder on other values.

12. Alternatively, you can **Import** the content from any docx file on your
    local machine, edit as required so that you don’t have type in all the
    content in this editor.

13. To view how the offer document will show up, use the **Preview** option at
    the top.

14. If you want to control whether an offer creator can edit the offer document
    content, use the **Manage Permission** option at top. If you want the offer
    creators to only insert placeholder values and not edit text, set the
    permission value to No

15. Click **Save** to save your progress. The template is now saved in a draft
    state.

16. To finalize and mark the document as published, click **Finish**.

17. On the Document templates library landing experience, you can see which
    document templates are currently active, in draft mode and have been
    archived and no longer in use.

18. You can delete any offer document template if they are not part of an offer
    package template already.

Offer Package templates
-----------------------

Offer packages are ultimately the offer artifacts that are shared with the
candidate. These are combinations of one or more offer document templates. To
create an offer package:

1.  Go to offer management.

2.  Navigate to **Packages** from the left navigation panel.

3.  You will see a list of **Active** package templates that are available for
    offer creators to use.

4.  To create a new offer package, click **+ New Package**.

5.  Enter a unique name and click **Create**.

6.  Click **Add template**

7.  You can choose to create a new template or choose from one of the existing
    ones

8.  If you choose to **add an existing template**, please ensure that those
    offer document templates were saved and finalized as well and marked as
    active. You can choose as many document templates as you want. Click
    **Done** to return to package management.

9.  You can configure the **sequence of the documents** and also mark whether or
    not the specific offer document is required during offer creation or not,
    the offer creator will have an option to delete the documents marked as Not
    required.

10. **Save and publish** the offer package template for it to be usable by all
    offer creators.

11. You can view draft offer package templates by navigating to the drafts tab.
    Whenever any changes are made to the offer package template, it must be
    saved and published again for this latest version to be used by offer
    creators.

Configure your offer process
----------------------------

There are several parts of the offer creation process that an Attract
Administrator can configure as well from the Admin Center present in Attract.

**Offer approvals**: You choose whether offer approvals are mandatory before it
can be sent to the candidate. As an admin, you can also decide whether all offer
approvals will happen in a sequential manner or parallel approval workflow.
Admins can also mandate whether offer approvers have to comment along with their
offer approval action. Offer approvals are mandatory for all non-standard
offers.

**Candidate’s offer experience**: Admins can choose to set whether all offers
will have an expiration date or not, and if yes, what the default offset for the
expiry date should be. They can also configure whether candidates can decline
the offers or not.

**E-Signatures**: Currently, the only option available is for candidates to type
their name in the offer package while accepting the offer. We will be
introducing partner integrations with other electronic signature providers
shortly.


To know more about the offer creation process, please read [Offer creation, approvals and signing](./creating-offers.md)
