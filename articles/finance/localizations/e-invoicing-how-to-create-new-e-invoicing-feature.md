# How to create a new Electronic invoicing feature

The objective of this article is to guide you through the creation of a new Electronic invoicing feature, when the country's configurable Electronic invoicing feature is not provided out-of-box for importation.

In this creation use case, you will:

- Create a new Electronic invoicing feature instead of importing from the Global repository.
- Create a new file format configurations, using the Invoice model configuration provided out-of-box as is, leveraging the existing invoice mapping for the feature you want to create.
- Add the file format configurations to the Electronic invoicing feature Configurations.
- Create the Electronic invoicing feature Setup.
- Complete and Publish the new Electronic invoicing feature into the Global repository for your organization.
- Deploy the new Electronic invoicing feature to the Service environment.

## Creating new file format configurations derived from existing Invoice model

The process begins at the **Electronic reporting** module, creating the file format configurations required for the new Electronic invoicing feature you want to create. Notice that through these steps you can either create the electronic invoice file format configuration, as well any other file format configurations your new Electronic invoicing feature may require to communicate with a web services, for example.

1.  Sign in to your Regulatory Configuration Service (RCS) account.

2.  In the **Electronic reporting** workspace, select **Repositories** from **Microsoft** Configuration provider.

3.  Select **Global**, then select **Open**.

4.  On the left panel, select **Invoice model** configuration for Electronic invoices. For Brazil you must select the **Fiscal documents** model configuration instead.

5.  On **Configurations** tab, select **Import**.

6.  Close the page.

7.  Close the page.

8.  Select **Reporting configurations** tile.

9.  Select the invoice model you imported (either **Invoice model** or **Fiscal documents** model).

10.  Select **Create configuration**, and then select **Format based on invoice context model**.

11. In the **Name** field, enter the name of the format configuration.

12. In the **Description** field, enter the description of the format configuration.

13. In the **Format type**, select the file extension type.

14. Select **Create configuration**.

15. Select the format configuration you created.

16. Select **Designer** and using the Format designer tool, configure the file layout to meet the file format specifications.

17. Close the page.

18. On **Versions** tab, select **Change status** to **Complete**.

19. On **Versions** tab, select **Change status** to **Share** for publishing in the Global repository.

To allow the Electronic invoicing service consuming the new file format configuration, it needs to be shared with the Microsoft domain.

20.  Select the format configuration you are working on.

21.  With the format configuration with status **Shared,** on **Versions** tab, select **Advanced sharing**, and then select **Global repository.**

22.  In the **Shared with** tab, select **+Organization**.

23.  In the **Parameters** field, enter **Microsoft.com** to share with the Microsoft domain.

24.  Select **OK.**

## Creating the new Electronic invoicing feature

Continue the process at the **Electronic invoicing features** page, with creation of a new e-invoicing feature.

1.  In RCS, in the **Globalization features** workspace, in the **Features** section, select the **Electronic invoicing** tile.

2.  Select **Add**, and then select **New feature**.

3.  In the **Name** field, enter the name of the e-invoicing feature.

4.  In the **Description** field, enter the description of the e-invoicing feature.

5.  Select **Create feature**.

## Adding Electronic invoicing feature Configurations

1.  Select the Electronic invoicing feature you are working on.

2.  On the **Configurations** tab, select **Add**.

3.  On the **Configurations** grid, browse and select the file format configurations you created and select **OK**.

## Adding Electronic invoicing feature Setups

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

11. To deploy your new Electronic invoicing feature to the service environment, see [Deploy the Electronic invoicing feature to Service environment](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started?toc=/dynamics365/finance/toc.json#deploy-the-electronic-invoicing-feature-to-service-environment).
