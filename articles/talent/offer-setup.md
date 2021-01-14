---
# required metadata

title: Set up offer management in Attract
description: This topic describes how to set up offers in Microsoft Dynamics 365 Talent.
author: andreabichsel
manager: AnnBe
ms.date: 12/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2018-10-18
ms.dyn365.ops.version: AX 7.0.0

---

# Set up offer management in Attract

[!include [banner](includes/banner.md)]

When a candidate is moved to the offer stage in Dynamics 365 Talent: Attract, you need to ensure that the
offers can be quickly created for the candidate, approved as necessary, and sent
out to the candidate. Because most offers are standard, they can be created from reusable templates. In Attract, all
offers are rolled into an offer package, which is a collection of one or
more offer documents. 

This topic lists all the steps that an Attract administrator would follow to set up different offer package templates as part
of the offer management capability in Attract. Users with non-administrator roles will not have access to these capabilities.

>[!NOTE]
> Offer management capabilities are available as part of the Comprehensive Hiring Add-On.

## Offer data 

Offer data is the smallest unit inside the offer package template. A typical offer consists of standard text and a set of values. The sets of values are the only pieces that could change between offers. During the offer creation, the most important aspect that the offer creator can focus on is the list of offer data placeholders present in an offer package template. To set up offer data, do the following.

1.  Go to **Offer management**.

1.  Expand the **Library** section in the left navigation pane, then go to **Offer data**.

    >[!NOTE]
    > On the **Offer data** page are the **Candidate details** and **Job details** sections. Attract provides a few offer data placeholders out-of-the-box.
    > 
    > There are sections on the page to organize different offer data placeholders together in logical groups. These sections can help with maintenance of offer data and population of data during the offer creation process.
    > 
    > To create a list of values for a placeholder, upload an Excel spreadsheet that has one column with the placeholder as the column title and the list of choices in the rows underneath. If the same placeholder is referenced in another data rule set, ensure they have a common set of values.
    
1.  To create a new offer data section, click **Add a section** and enter a unique name for the section.

1.  To add offer data placeholders to any section, click **Add offer data** and enter a unique name for the placeholder.

1.  To edit the name of any section, hover over the section name and update the name.

1.  To edit the name of any existing offer data placeholder, first make sure that the placeholder is not already part of any template. Then, hover over the name of the offer data placeholder and update the name as needed.

1. To delete an existing offer data placeholder, first make sure that the placeholder is not part of any other template. Then, hover over the placeholder and when the trash can icon appears, click the trash can to delete the offer data placeholder.
    >[!NOTE]
    > You can see how many templates an offer data placeholder is part of by the number indicator next to each offer data. 

1. To delete any section, hover over the name. If none of the offer data placeholders inside the section appear in any template, you can click the trash can icon to delete it. 
    >[!NOTE]
    > Deleting the section will also delete all the offer data placeholders inside that section.

After the offer data placeholders have been set up, you can use them across any document template. Offer data placeholders are not restricted to a specific template -- the same set can be used across all templates.

## Offer data rules

Most organization have rules for how offers must be created. For example, an organization may want to require that the maximum annual salary offer for a specific location and seniority level combination has to be within a certain range, or that there are only a few specific values possible for the offer level for the new hire. Attract currently supports all such data rules using a CSV file.

To prepare the data rules CSV file, do the following.

1.  Determine the offer data placeholder for the rule set. For example, **Annual Salary**.

1.  Identify the dependent offer data placeholder values. For example, **Job Location** and **Level**.

1.  Specify columns 1 and 2 as **Job Location** and **Level**.

1.  To upload a range value, make columns 3 and 4 **Annual Salary**. To upload a specific value instead of a range, only make column
    3 **Annual Salary**.

1.  Populate the Microsoft Excel file based on your required roles.

1.  Ensure that each row is a unique combination of all the values put together.

1.  Save the file as a CSV format.

To upload the offer data rules file, do the following.

1.  Go to **Offer management**.

1.  Expand the **Library** section in the left navigation panel, then go to **Offer data rules**.

1.  Click **New data set** to display the **Upload** dialog box.

1.  Specify a unique name for the rule set and then upload the saved CSV file.

1.  Click **Add**.
    The rule set will be processed in the background and you will be notified in-app and via email once it completes.

    You will be notified if there are errors while processing the upload. You can then download the error log, fix the file, and upload it again.

1.  Use the ellipses button (**…**) option if you want to download the rule set and update the set of values. After updating, you can upload the file again.

1.  You can delete an existing rule set upload if the placeholder being defined is not being used in another document template.

>[!NOTE]
> - Each placeholder can only have one unique set of columns that it is dependent on. For example, if **Annual Salary** is dependent on **Job Location** and **Level**, you can't upload another rule set where **Annual Salary** is dependent on a different set of columns.

> - You can download sample offer data rule sets on the **Samples** tab on the **Offer data rules** page.

> - When an offer creator overrides the values that are recommended by the offer data rules, the offer is flagged as non-standard and offer approval workflow will be mandated.

## Document templates

An offer document template can help administrators create offer letters. The offer document template is a combination of the text that will be part of the offer as well as the defined offer data placeholders. 

To create an offer document template, do the following.

1.  Go to **Offer management**.

1.  Expand the **Library** section in the left navigation pane and go to **Templates**.

    The **Templates** page will display a list of document templates that have already been defined.

1.  To create a new document template, click **New Template**.

1.  Enter a unique name for the template and click **Create**.

1.  Use the rich text editor to insert or edit the offer document content. You can insert tables, images, and hyperlinks using the options available at the top of the text editor.

1.  You can insert offer data placeholders in the offer template document by:

    - Dragging and dropping from the right pane.

    - Hashtag the offer data placeholder directly into position. Type **\#** and then start typing the name of the offer data
        placeholder. Options will appear in the drop-down list. Click or press **Enter** to insert the offer data placeholder.

    >[!NOTE]
    > - To associate a placeholder to the offer document template without exposing its value to the candidate, hover over the offer data placeholder and click the **Pin** icon. This will push the placeholder to the **Pinned offer data** section of the offer document template. To unpin, follow the same steps but click **Unpin** in the list of offer data placeholders.

    > - To view the list of active offer data placeholders, switch to the **Active** tab in the right pane.

    > - If you insert a placeholder that is driven by an offer data rule set, you can see the dependency of that offer data placeholder on other values.

    > - Alternatively, you can **Import** the content from a .docx file on your local machine and edit as required. That way, you don’t have to type in all the content in the editor.

1. To preview the offer document, use the **Preview** option at the top of the page.

1. To control whether an offer creator can edit the offer document content, use the **Manage permission** option at the top of the page. If you want the offer creator to only insert placeholder values and not edit text, set the permission value to **No**.

1. Click **Save** to save your progress. The template will be saved in a draft state.

1. To finalize and mark the document as published, click **Finish**.

1. You can see which document templates are currently active, in draft mode, and have been archived and are no longer in use on the document templates library landing experience.

>[!NOTE]
> You can delete any offer document template that is not part of an existing offer package template.


## Offer package templates

Offer packages are the offer artifacts that are shared with the candidate and consist of a combination of one or more offer document templates. To create an offer package, do the following.

1.  Go to **Offer management**.

1.  Go to **Packages** from the left navigation pane.

    A list of active package templates that are available for offer creators to use is displayed.

1.  To create a new offer package, click **New Package**.

1.  Enter a unique name and click **Create**.

1.  Click **Add template**.

    >[!NOTE]
    > - You can choose to create a new template or choose from an existing one.

    > - If you choose to add an existing template, you need to make sure that the
    offer document template was saved, finalized, and marked as
    active.
    
    > - You can choose as many document templates as you want. 
    
1.  Click **Done** to return to **Package management**.

    You can configure the sequence of the documents and also mark whether
    the specific offer document is required during offer creation. The
    offer creator will have an option to delete the documents marked as **Not
    required**.

1. To save the offer package template so that it's usable by all offer creators, click **Save and publish**.

   To view draft offer package templates, go to the **Drafts** tab. If a change is made to the offer package template, it must be
    saved and republished.

## Configure an offer process

There are several parts of the offer creation process that can be configured by an Attract administrator.

- **Offer approvals** - Choose whether offer approvals are required before the offer can be sent to the candidate. As an administrator, you can also decide whether all offer approvals will happen in a sequential manner or parallel approval workflow. You can also mandate whether offer approvers must add a comment along with their offer approval. Offer approvals are mandatory for all non-standard
offers.

- **Candidate’s offer experience** - As administrator, you can choose to set whether all offers have an expiration date, and if so, what the default offset for the expiration date should be. You can also configure whether candidates can decline an offer.

- **e-Signatures** - As an administrator, you can also choose the method that candidates can use to sign offers.
    - Adobe Sign - All offer packages will be sent and signed via Adobe Sign. Each offer creator publishing the offer needs to have their Adobe Sign account connected to Attract. For Adobe Sign licenses and a free Trial, please visit this [link](https://acrobat.adobe.com/us/en/business/integrations/microsoft-dynamics-365-for-talent.html).

    - DocuSign - All offer packages will be sent and signed via DocuSign. Each offer creator publishing the offer needs to have their DocuSign account connected to Attract. 
    
    - ESign - This is the default option, provided out of the box, where the user can sign an offer by typing their name and initials.


To learn more about the offer creation process, see [Create, approve, and sign offers](./creating-offers.md).
