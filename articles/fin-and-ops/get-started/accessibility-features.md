---
# required metadata

title: Accessibility features
description: This topic describes a significant set of functionality specifically designed to assist users with various disabilities, including those who utilize sight assist technologies such as Windows Narrator.
author: TLeforMicrosoft
manager: AnnBe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tlefor
ms.search.validFrom: 2017-12-31 
ms.dyn365.ops.version: 7.3
---

# Accessibility features

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition has a significant set of functionality specifically designed to assist users with various disabilities, including those who utilize sight assist technologies such as Windows Narrator.

## Windows Narrator and keyboard-only access

Each field and control has a label and description of applicable shortcuts, read by a screen reader.

## Shortcuts provided for the most common actions

Data entry and keyboard interaction is at the heart of most users' daily interactions. To enhance your user experience, we’ve authored shortcuts to help you “jump” around the screen and shortcuts for specialized actions. For more inforamtion, see [Keyboard shortcuts](shortcut-keys.md).

## Navigation search

Any page that is available in the Navigation Pane menu, is also available by typing the page name or description in the **Search** box. Go to the **Search** box by pressing Alt+G, and type the name of the page.

![cid:image001.png\@01D35891.76984830](media/6d08b0be32808221023e2aa92d69fd70.png)

For more information, see [Navigation search](navigation-search.md).

> [!Note]
> Only top-level pages can be directly navigated to. Secondary pages rely on information or context from their parent page.

## Action search for keyboard-only users or for heads-down data entry

Each action offered on a page is keyboard accessible, via the tab sequence. We also offer the ability to execute actions more directly using the action search functionality.

### Example:

Assume that the **Email notification log** option in the **Email Notification** section is the action you'd like to execute. (As shown in the right-most section.)

A user can execute that action by gaining focus into the Action Pane via the shortcut Ctrl+F6, and then tabbing through all of the tabs/actions until the **Email notification log** action has focus.

![cid:image002.jpg\@01D35891.76984830](media/f0d78399e7fafcd85ded1cd1e3d34f3c.jpg)

The user can also execute the action more directly. From anywhere on the page, the user can use a shortcut to expose the search box for actions. The shortcut is: Ctrl + ‘

![cid:image003.jpg\@01D35891.76984830](media/80f7e8c5ac412fdf2c8a12f7728f135a.jpg)

The user then types words that describe the action, and the action is made available, and can be directly executed. For example, typing *email*, *notific* (a partial word) and *log* all allow the user to “jump” to the **Email notification log** functionality.

| [./media/image4.jpeg](./media/image4.jpeg) | [./media/image5.jpeg](./media/image5.jpeg) | [./media/image6.jpeg](./media/image6.jpeg) |
|--------------------------------------------|--------------------------------------------|--------------------------------------------|

When complete, the user can once again use the shortcut Ctrl+’ and is returned to the field they were positioned when they executed the action search.

For more information, see [Action search](action-search.md).

## Tab sequence

In daily use, it is understood that not *every* field is used to perform common tasks. Therefore, by default, we offer an “optimized” tab sequence with tab stops on only those fields that are key to common scenarios.  

If the user finds that some key fields should be included in their use of the product, the user who is utilizing Windows Narrator may use Narrator’s keyboard actions to gain access to those fields to inspect their content, or the user may enable the **Enhanced tab sequence** option on the **Options** page which makes all editable and read-only fields part of the tab sequence. The user can then choose to use form personalization to create a custom tab sequence, choosing which fields they don’t need to be part of the tab sequence.

![cid:image005.png\@01D357AF.09B33870](media/8c0f12bbb3f26032997ef0ba95d89b6a.png)

## Form patterns

Nearly 90% of our pages are based on a small set of patterns. Developers refer to these as *form patterns*. Each form pattern is used to convey the most common actions taken on that form. A form pattern ensures familiarity and ease of understanding when common actions, and common data are always presented in the same location on different forms. With a small number of form patterns, regardless of the number of forms in the system, the user can easily learn and use the system with confidence once the form pattern is recognized.

To learn more about form patterns, see [Form styles and patterns](../dev-itpro/user-interface/form-styles-patterns.md).

## Responsive layout

Our product is designed to work on different devices and form factors from the smallest screens to large screens with the highest resolutions. Our responsive layout engine allows the user to zoom in to magnification levels of 200% (in some scenarios, greater than 200%)

## Guidance to our developers and customers on how to incorporate accessible thinking in their customizations

To learn more about our best practices for enabling accessibility, see [Accessibility in forms, products, and controls](./dev-itpro/user-interface/enable-accessibility).
