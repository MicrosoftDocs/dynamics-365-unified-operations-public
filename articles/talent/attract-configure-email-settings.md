---
# required metadata

title: Configure email settings in Microsoft Dynamics 365 for Talent - Attract
description: Configure settings for emails sent by Microsoft Dynamcis 365 for Talent - Attract.
author: andreabichsel
manager: AnnBe
ms.date: 06/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-06-04
ms.dyn365.ops.version: Talent October 2018 update

---

# Configure email settings
[!include[banner](../includes/banner.md)]

Your brand establishes trust and helps you to build a relationship with candidates before they even apply for your positions. Positive brand perception attracts top talent and increases loyalty with existing employees. With Microsoft Dynamics 365 for Talent: Attract, you can configure emails to reflect your company's brand to provide a consistent experience for job candidates as they progress through the application process. Attract lets you:

- Configure email settings to use your company's Exchange email service account. That way, candidates know your emails are coming from your company. For example, instead of candidates receiving emails from contoso@microsoft.com, you can configure your emails to be from recruiting@contoso.com.

- Create consistent branding for all your email communications by setting the global header and footer for email templates. 

> [!NOTE]
> You need the Comprehensive hiring add-on to configure Attract to use your company's email service account for sending emails.

## Connect an email service account

You can connect your company account to create a branded email experience for your job candidates. If you don't connect your company account, Attract will use the default Microsoft-branded email service account.

1. Select **Settings** (the gear symbol in the upper-right corner) and then select **Admin center**.

2. On the **Email settings** tab, under **Email service accounts**, select **Connect a company account**.

   ![Connect a company email service account in Attract](./media/attract-admin-email-service-accounts.png)

3. In the Microsoft sign-in window, sign in with your corporate credentials.

4. If you haven't yet set up an email service account, or if you want to add a new one, select **Add new service account** and enter your email information. If you already have an email service account set up, select the email service account you want to use.

When your email service account is successfully configured, you'll see it listed under **Email service accounts**.

## Disconnect an email service account

If you want to stop using your company's domain in email communications through Attract, you can disconnect an email account.

1. Select **Settings** (the gear symbol in the upper-right corner) and then select **Admin center**.

2. On the **Email settings** tab, under **Email service accounts**, select **More** (three dots) next to the email service account you want to disconnect.

3. Select **Disconnect email account**.

   ![Disconnect your company's email service account](./media/attract-admin-disconnect-email-account.png)

4. When prompted, select **Disconnect**.

   ![Confirm disconnecting your company's email service account](./media/attract-admin-email-confirm-disconnect.png)

If you don't connect a different email service account, emails sent from Attract will use the default Microsoft-branded email service.

## Configure email template settings

You can upload an image with your company's logo and other information as a branded header for your emails, and provide links to your privacy policy and terms of use for your email footers.

> [!NOTE]
> You must comply with all applicable laws, including anti-spam regulations, of your country and of the country that governs the email recipient.

1. Select **Settings** (the gear symbol in the upper-right corner) and then select **Admin center**.

2. On the **Email settings** tab, under **Email template settings**, drag and drop an image to use as your email header, or click the image box to browse for the file. If you want to change an existing image, select **Remove** next to the image first. The image must be a JPEG, JPG, PNG, or SVG file. The recommended size for your image is between 25 and 800 pixels wide and between 25 and 150 pixels high. The maximum file size for the header is 1 MB.

   ![Add an image for your company's email header](./media/attract-admin-email-header.png)

3. Under **Your Privacy policy for communications**, provide a link to your company's privacy policy, and under **Your Terms and conditions for communication**, provide a link to your company's terms of use.

   ![Add links to your company's privacy policy and terms of use for the email footer](./media/attract-admin-email-footer.png)

4. Select **Save** to save your email template settings.