# How to create a new Electronic invoicing feature

The objective of this article is to guide you through the creation of a new Electronic invoicing feature, applicable in the scenario where the country's configurable Electronic invoicing feature is not provided out-of-box, and it is possible to use the Invoice model configuration provided out-of-box as is, leveraging the existing invoice mapping for the feature you want to create.

## Creating new file format configurations derived from existing Invoice model

The process begins at the **Electronic reporting** module, creating a new file format configuration for the new Electronic invoicing feature you want to create.

1.  Sign in to your Regulatory Configuration Service (RCS) account.

2.  In the **Electronic reporting** workspace, select **Repositories** from **Microsoft** Configuration provider.

3.  Select **Global**, then select **Open**.

4.  On the left panel, select and import **Invoice model** configuration for Electronic invoices. For Brazil you must import the **Fiscal documents** model configuration instead.

5.  Close the page.

6.  Close the page.

7.  Select **Reporting configurations** tile.

8.  Select the invoice model you imported (either **Invoice model** or **Fiscal documents** model).

9.  Select **Create configuration**, and then select **Format based on invoice context model**.

10. In the **Name** field, enter the name of the format configuration.

11. In the **Description** field, enter the description of the format configuration.

12. In the **Format type**, select the file extension type.

13. Select **Create configuration**.

14. Select the format configuration you are working on.

15. Select **Designer** and using the Format designer tool, configure the file layout and meet the specification requirements.

17. On **Versions** tab, select **Change status** to **Complete**.

18. On **Versions** tab, select **Change status** to **Share** for publishing in the Global repository.

To allow the service consuming the format configuration, it needs to be shared with the Microsoft domain.

1.  In RCS, select the format configuration you are working on.

2.  With the format configuration with status **Shared,** on **Versions** tab, select **Advanced sharing**, and then select **Global repository.**

3.  In the **Shared with** tab, select **+Organization**.

4.  In the **Parameters** field, enter **Microsoft.com** to share with the Microsoft domain.

5.  Select **OK.**

## Creating a new e-invoicing feature

Continue the process at the **Electronic invoicing features** page, with creation of a new e-invoicing feature.

1.  In RCS, in the **Globalization features** workspace, in the **Features** section, select the **Electronic invoicing** tile.

2.  Select **Add**, and then select **New feature**.

3.  In the **Name** field, enter the name of the e-invoicing feature.

4.  In the **Description** field, enter the description of the e-invoicing feature.

## Adding the new file format configuration

1.  Select the e-invoicing feature you are working on.

2.  On the **Configurations** tab, select **Add**, select the format configuration you just created and select **OK.**

## Creating a new feature Setup

1.  On the **Setups** tab, select **Add** and then select **Custom setup.**

2.  In the **Name** field, enter the name of the feature setup.

3.  In the **Description** field, enter the description of the feature setup.

4.  In the **Setup type**, select **Processing pipeline**.

5.  Select **Create**.

6.  On the **Processing pipeline** tab, select **New** to add new pipeline action.

7.  On the **Applicability rules** tab, select **New** to add new applicability rules clauses.

8.  On the **Variables** tab, select **New** to add new variables.

9.  When finished, select **Validate** to check the consistency of the configuration.

10. Close the page.

## Publishing the new e-invoicing feature in the Global repository

1.  On the **Versions** tab, select the Feature version in **Draft.**

2.  Select **Change status** and select **Complete**.

3.  Select **Change status** again and select **Share**.

## Deploying the new e-invoicing feature

1.  On the **Versions** tab, select **Deploy**.

2.  On **Parameters**, set the **Deploy to connection application** toggle to No.

3.  Set the **Deploy to service environment** toggle to Yes.

4.  In the **Service environment** field, select the e-invoicing environment to deploy.

5.  In the **From date** field, select the effective date.

6.  Select **OK.**
