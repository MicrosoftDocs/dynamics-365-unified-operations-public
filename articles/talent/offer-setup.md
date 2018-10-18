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
    > On the **Offer data** page, there are a couple of offer data sections, specifically **Candidate details** and **Job details**. Attract provides a few offer data placeholders out-of-the-box.

>[!NOTE]
> There are sections on the page to organize different offer data placeholders together in logical groups. These sections can help with maintenance of offer data and population of data during the offer creation process.

6.  To create new offer data section, click **Add a section** and enter the
    unique section name

7.  To add offer data placeholders to any section, click **Add offer data** and
    enter a unique name for the placeholder.

8.  To edit the name of any section, hover over the section name and update the
    name

9.  To edit the name of any existing offer data placeholder, we need to make
    sure that they are not already part of any template. You can hover over the
    name of the offer data placeholder and update the name as desired

10. To delete any existing offer data placeholder, we need to make sure that
    they are not already part of any template. You can hover over the
    placeholder and the trash-can icon will appear, click that to delete the
    offer data placeholder.

11. To delete any section, hover over the name. If none of the offer data
    placeholders inside the section appear in any template, you can click the
    trash-can icon. This will also delete all the offer data placeholders inside
    that section.

12. You can also see how many templates any offer data placeholder is part of by
    the number indicator next to each offer data.

13. Alternatively, you can also view and edit the offer data in a similar way
    from within each document template creation.

Once the offer data placeholders have been set up, you can use these across any
document templates. Contrary to our earlier public preview release, offer data
placeholders are not restricted to a specific template but the same set can be
used across all templates.

Offer data rules
----------------

Every organization has a few rules for how offers cannot be created, for example
you want to indicate that the max annual salary offer for a specific location,
seniority level combination has to be within a certain range or how there are
only a few certain values possible for offer level for the new hire. We
currently support all such data rule uploads via CSV files.

Preparing the data rules CSV file:

1.  Determine the offer data placeholder for which the rule set is. Example,
    Annual Salary

2.  Identify the dependent offer data placeholder values, let’s say Job Location
    and Level

3.  Put columns 1 and 2 as Job Location and Level

4.  Since we are uploading a range value, put Columns 3 and 4 as Annual Salary.
    If we are uploading a specific value instead of a range, only create Column
    3 as Annual Salary

5.  Populate the excel file per your required roles.

6.  Ensure each row is a unique combination of all the value put together.

7.  Save the excel in a CSV format.

Uploading the offer data rule:

1.  Navigate to offer management

2.  Expand the Library section in the left navigation panel, go to **Offer data
    rules**

3.  Click **+ New data set** to bring up the upload dialog box

4.  Give a unique name for the rule set name and upload the saved csv file

5.  Click **Add**

6.  The rule set is processed in background and you will be notified in-app and
    via email once it completes

7.  If there were errors processing the upload, you will be notified, and you
    can then download the error log to fix the sheet and re-upload.

8.  To edit/download the rule set, use the **…** option to download the rule set
    and update the set of values and re-upload.

9.  You can delete an existing rule set upload if the placeholder being defined
    is not being used in any document template already.

Please note a few important pieces:

1.  Each placeholder can only have one unique set of columns its dependent on.
    For example, Annual Salary is dependent on Job Location and Level. We cannot
    upload another rule set where Annual Salary is dependent on another
    different set of columns.

2.  You can download some sample offer data rule sets under the **Samples** tab
    of the Offer data rules screen.

3.  When an offer creator overrides the values that are recommended by the offer
    data rules, it flags the offer as non-standard and offer approval workflow
    is mandated.

Document templates
------------------

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
