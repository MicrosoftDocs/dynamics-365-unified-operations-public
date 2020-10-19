---
# required metadata

title: Integrate with LinkedIn Talent Hub
description: Set up integration between Dynamics 365 Human Resources and LinkedIn Talent Hub.
author: jaredha
manager: tfehr
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-10-20
ms.dyn365.ops.version: Human Resources

---

# Integrate with LinkedIn Talent Hub

[LinkedIn Talent Hub](https://business.linkedin.com/talent-solutions/talent-hub) is an Applicant Tracking System (ATS) platform that lets you source, manage, and hire employees all in one place. You can integrate Dynamics 365 Human Resources with LinkedIn Talent Hub, so you can easily create employee records in Human Resources for applicants who have been hired for a position.

## Setup

A system administrator must perform setup tasks to enable the integration, including setting up a user and security role in the Power Apps environment to grant LinkedIn Talent Hub the appropriate permissions to write data into Human Resources.

### Link your environment to LinkedIn Talent Hub

1. Open [LinkedIn Talent Hub](https://business.linkedin.com/talent-solutions/talent-hub).

2. On the user drop-down menu, select **Product Settings**.

3. In the **Advanced** section of the left navigation pane, select **Integrations**.

4. Select **Authorize** for the Microsoft Dynamics 365 Human Resources integration.

5. On the **Dynamics 365 Human Resources** page, select the environment to which you want to link Talent Hub, and select the **Link** action.

    ![LinkedIn Talent Hub onboarding](./media/hr-admin-integration-talent-hub-onboarding.jpg)

    > [!NOTE]
    > You can only link to environments for which your user account has administrator access to both the Human Resources environment and the associated Power Apps environment. If no environments are listed on the Human Resources link page, ensure that you have licensed Human Resources environments on the tenant and that the user with which you are signed into the link page has administrator permissions to both the Human Resources environment and the Power Apps environment.

### Create a Power Apps security role

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com).

2. In the Environments list, select the environment associated with the Human Resources environment with which you want to link your instance of LinkedIn Talent Hub.

3. Select **Settings**.

4. Expand the **Users + Permissions** node and select **Security Roles**.

5. On the Security Roles page, select **New role** on the action ribbon.

6. On the **Details** tab, enter a role name, for example **LinkedIn Talent Hub HRIS Integration**.

7. On the **Customization** tab, select organization-level **Read** permission on the following entities:

    - Entity
    - Field
    - Relationship

8. Save and close the security role.  

### Create a Power Apps application user

An application user must be created for the LinkedIn Talent Hub adapter to grant permissions to the adapter to write candidate records into the Power Apps environment.

1. Open the [Power Platform admin center](https://admin.powerplatform.microsoft.com).

2. In the Environments list, select the environment associated with the Human Resources environment with which you want to link your instance of LinkedIn Talent Hub.

3. Select **Settings**.

4. Expand the **Users + Permissions** node and select **Users**.

5. Select **Manage users in Dynamics 365**.

6. Change the view from the default Enabled Users to **Application Users** on the System Views list in the list header.

    ![Application Users](./media/hr-admin-integration-power-apps-application-users.jpg)

7. Select **New** on the action ribbon.

8. On the **New user** page:

    - Change the **User type** to **Application User**.
    - Set **User Name** to "Dynamics365 HR LinkedIn HRIS Integration".
    - Set **Application ID** to "3a225c96-d62a-44ce-b3ec-bd4e8e9befef".
    - Enter any values in the **First Name**, **Last Name**, and **Primary Email** fields.
    - Select **Save & Close** on the action ribbon.

### Assign security role to the new user

After saving and closing the new application user in the previous section, you are returned to the **Users list** page.

1. On the **Users list** page, change the view to **Application Users**.

3. Select the new application user created in the previous section.

4. Select **Manage Roles** on the action ribbon.

5. Select the new security role you created for the integration.

6. Click **OK**.
    
### Add Azure Active Directory App in Human Resources

1. In Dynamics 365 Human Resources, open the **Azure Active Directory applications** page.

2. Add a new record to the list:

    - **Client Id**: 3a225c96-d62a-44ce-b3ec-bd4e8e9befef
    - **Name**: The name of the Power Apps security role created earlier, for example **LinkedIn Talent Hub HRIS Integration**.
    - **User ID**: Select a user that has permissions to write data in Personnel Management.

### Create the entity in Common Data Service

> [!IMPORTANT]
> The integration with LinkedIn Talent Hub is dependent on virtual entities in Common Data Service for Human Resources. Configuring virtual entities is a prerequisite for this step in the setup. For information on configuring virtual entities, see [Configure Common Data Service virtual entities](https://docs.microsoft.com/en-us/dynamics365/human-resources/hr-admin-integration-common-data-service-virtual-entities).

1. In Human Resources, open the **Common Data Service (CDS) integration** page.

2. Select the **Virtual entities** tab.

3. Filter the entity list by entity label to **LinkedIn exported candidate**.

4. Select the entity, and select the **Generate/refresh** action.

## Exporting candidate records

Once setup completes, recruiters and HR professionals can use the **Export to HRIS** function in LinkedIn Talent Hub to export hired candidate records from LinkedIn Talent Hub to Human Resources.

### Export records from LinkedIn Talent Hub

Once a candidate has moved through the recruiting process and has been hired, you can export the candidate record from LinkedIn Talent Hub to Human Resources.

1. In LinkedIn Talent Hub, open the project for which you have hired the new employee.

2. Select a candidate record.

3. Select **Change stage**, and select **Hired**.

4. On the ellipses menu for the candidate, select **Export to HRIS**.

5. In the **Export to HRIS** pane, enter the information to be exported:

    - On the **HRIS provider** drop-down list, select **Microsoft Dynamics 365 Human Resources**.
    - Select a **Start date** value for the new employee.
    - Enter the **Job title** for the new employee's job.
    - Enter the **Location** where the employee will be based.
    - Enter or verify the **Email** address of the employee.

![Export to HRIS from LinkedIn Talent Hub](./media/hr-admin-integration-linkedin-talent-hub-export.jpg)

## Complete onboarding in Human Resources

Candidate records exported from LinkedIn Talent Hub to Human Resources display in the **Candidates to hire** section of the **Personnel management** page.

1. In Human Resources, open the **Personnel management** page.

2. In the **Candidates to hire** section, select the **Hire** action for the selected candidate.

3. In the **Hire new worker** pane, review the record and add any required information. You may also select the position number for which the candidate has been hired.

Once the required information has been entered, you can continue with your standard processes of creating employee records and employee onboarding.

The following details are imported and included on the new employee record:

- First name
- Last name
- Employment start date
- Email address
- Phone number

## See also

[Configure Common Data Service virtual entities](./hr-admin-integration-common-data-service-virtual-entities.md)<br>
[What is Common Data Service?](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)