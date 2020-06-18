---
# required metadata

title: Edit personal information
description: This article describes how to edit personal information in Employee and manager self service.
author: andreabichsel
manager: AnnBe
ms.date: 03/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

ms.search.form: HRMParameters, EssWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Operations, Human Resources
# ms.tgt_pltfrm: 
ms.custom: 51941
ms.assetid: 2cfb061a-a616-4bf9-9d98-9cde00039eec
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-03-19
ms.dyn365.ops.version: Human Resources

---

# Edit personal information

You can edit your personal information in Dynamics 365 Human Resources in the **Employee self service workspace**.

The personal information you can edit includes:

- Addresses
- Contact details
- Personal contacts
- Identification numbers
- Payment method
- Image used in Human Resources

Parameters set in the global address book determine the roles that can see your personal information.

1. In Human Resources, select **Employee self service**.

2. Select **Edit personal details**.

3. To change your address, select the **Addresses** tab. Changes you make appear in the **Personnel management** workspace to alert HR. 

    - To add a new address, select **Add**.
    - To edit an existing address, select the address and then select **Edit**.
    - To view a map, select **Map**.
    - To add or remove a contact, select **More options** and then select **Advanced**. Under **Contact information**, select **Add** or **Remove** and edit the fields as necessary.
    - To set your time zone and location, select **More options** and then select **Advanced**. Under **General**, edit the fields as necessary.

4. To change your contact details, select the **Contact details** tab. You can provide different types of contact information, including phone, email, and social media links. You can set a contact detail as primary, but you can only set one of each type as primary. 

    - To add new contact information, select **Add**. Edit the fields as necessary.
    - To edit existing contact information, select the item and then select **Edit**. Edit the fields as necessary.
    - To set a contact detail as private, select the item, select **Advanced**, and then set the **Private** toggle to **Yes**. Select **OK**.
  
5. To change your personal contacts, select the **Personal contacts** tab. You can designate emergency contacts, beneficiaries, and dependents. A contact can be a person or organization. The **Benefits management** feature uses personal contact information. For more information, see [Configure personal contact eligibility options](hr-benefits-setup-contact-eligibility-options.md).

6. To change your identification numbers, such as Social Security Number, select the **Identification numbers** tab. Changes might go through an approval process if your organization set up an approval workflow.

    - To add an identification number, select **New**. Complete the fields as necessary and select **Save**.
    - To edit a number, select **Edit**. Edit the fields as necessary and select **Save**.

7. To change the methods by which you're paid, select the **My payment information** tab. This tab is only available if payment methods are enabled in the **Human Resources parameters** form. HR can enable **Bank draft**, **Cash**, **Check**, **Electronic payment**, or **Other**. HR can also disable electronic payment validation (used for US Payroll), and bank account and routing number validation.

8. To change the image that displays in Human Resources for your profile, select the **Image** tab. Depending on your organization's settings, images might be routed for approval.

    - To upload an image, select **Upload new image**.
    - To remove an image, select the image and then select **Remove**.

