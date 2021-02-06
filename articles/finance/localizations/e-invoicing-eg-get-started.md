# Get started with the Electronic invoicing add-on for Egypt

This topic provides information that will help you get started with the
Electronic invoicing add-on for Egypt. It guides you through the
configuration steps that are country-dependent in Regulatory
Configuration Services (RCS), complementing the steps described in [Get
started with the Electronic invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

## Country specific configuration for Egyptian electronic invoice (EG) Electronic invoicing feature

The configuration of Egyptian electronic invoice (EG) Electronic
invoicing feature requires specific steps to be accomplished. Some of
parameters from the configurations are published with default values, so
they need to be reviewed and updated to better fit to your business
operation.

### Prerequisite

Before you complete the procedures in this topic, you must have created
a Egyptian electronic invoice (EG) Electronic invoicing feature under
your organization, as described in the section **Create an Electronic
invoicing feature under your organization provider** from [Get started
with the Electronic invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

1.  In RCS, in the **Features** section of the **Globalization feature**
    workspace, select the **Electronic invoicing add-on** tile.

2.  In the **Electronic invoicing add-on Features** page, verify if the
 **Egyptian electronic invoice (EG)** Electronic invoicing feature
    you have created is selected.

3.  On the **Versions** tab, verify the **Draft** version is selected.

4.  On the **Setups** tab, in the grid, select **Sales invoice** Feature
    setup.

5.  Select **Edit.**

6.  Select **Actions** tab, in the **Actions** field group, select
 **Sign json document for Egyptian Tax Authority** action.

7.  In the **Parameters** field group, select **Certificate name**
    parameter.

8.  Select **Save.**

9.  Close the page.

10. Return to [Get started with the Electronic invoicing
    add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md)
    for configuration of the application setup.

## Country specific configuration of Application setup for Egyptian electronic invoice (EG) Electronic invoicing feature

The configuration of the Application setup for **Egyptian electronic
invoice (EG)** Electronic invoicing feature requires specific steps to
be accomplished. You must accomplish those steps before you deploy your
Electronic invoicing feature to your Electronic invoicing add-on service
environment.

### Prerequisite

Before you complete the procedures in this topic, you must have created
a **Egyptian electronic invoice (EG)** Electronic invoicing feature and
you must have initiated the configuration of application setup for
**Egyptian electronic invoice (EG)** Electronic invoicing feature, as
described in the section **Configure the application setup** from [Get
started with the Electronic invoicing
add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md).

1.  In RCS, in the **Features** section of the **Globalization feature**
    workspace, select the **Electronic invoicing add-on** tile.

2.  In the **Electronic invoicing add-on Features** page, verify if the
 **Egyptian electronic invoice (EG)** Electronic invoicing feature is
    selected.

3.  On the **Versions** tab, verify that the **Draft** version is
    selected.

4.  On the **Setups** tab, select **Application setup**.

5.  In the **Connected application** field, select the application to
    where you want to deploy.

6.  On **Table name** field, verify if Customer invoice journal is
    selected.

7.  Select **Response types** and select **New**.

8.  In the **Response type** field, enter "Response" as fixed value. In
    the **Description** field, enter Description.

9.  In the **Submission status** field, select Pending.

10. In the **Model mapping** field, select **Model mapping from response
    message**, with **(Preview) Response message import format.**

11. Select **Save**.

12. Select **New**.

13. In the **Response type** field, enter "ResponseData" as fixed value.
    In the **Description** field, enter Description.

14. In the **Submission status** field, select Pending.

15. In the **Data entity name** field, select **Sales invoice headers
    V2**.

16. In the **Model mapping** field, select **Egypt response data
    import**, with **(Preview) Egypt response data import.**

17. Select **Save**.

18. Return to in [Get started with the Electronic invoicing
    add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/e-invoicing-get-started.md)
    for deployment of the Electronic invoicing feature.

## Privacy notice

Enabling the EG-00008 (E-invoicing for Egypt) feature may require
sending limited data, which includes the organization tax registration
ID. This will be transmitted to third-party agencies authorized by the
tax authority for purposes of sending electronic invoices to this tax
authority in the predefined format required for integration with the
government's web service. An administrator can enable and disable the
EG-00008 (E-invoicing for Egypt) feature by navigating to **Organization
administration &gt; Setup &gt; Electronic document parameters**. Select
the **Features** tab, select the row containing the EG-00008 feature,
and then make the appropriate selection. Data imported from these
external systems into this Dynamics 365 online service are subject to
our [privacy statement](https://go.microsoft.com/fwlink/?LinkId=512132).
Please consult the Privacy notice sections in country-specific feature
documentation for more information.

## Additional resources

-   [Electronic invoicing add-on
    overview](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/gionoder2021-03/articles/finance/localizations/e-invoicing-service-overview.md)

-   [Get started with Electronic invoicing add-on service
    administration](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/gionoder2021-03/articles/finance/localizations/e-invoicing-get-started-service-administration.md)

-   [Get started with the Electronic invoicing
    add-on](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/gionoder2021-03/articles/finance/localizations/e-invoicing-get-started.md)

-   [Customer electronic invoices in
    Egypt](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-egy-e-invoices)


