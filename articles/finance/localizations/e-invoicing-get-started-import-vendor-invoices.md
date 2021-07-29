# Get started import vendor invoices

This topic provides you information that will help you get started with the importation of vendor invoices using the Electronic Invoicing service. It guides you through the configuration steps in Regulatory Configuration Services (RCS) and Dynamics 365 Finance and Supply Chain Management that you must follow to receive electronic vendor invoices from the vendors.

## Set up import vendor invoices in RCS

1.  Consult the list of Electronic invoicing features in [Generally available features](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-configuration-rcs?toc=/dynamics365/finance/toc.json#generally-available-features)

2.  Select and import the Electronic invoicing feature, see [Import an Electronic invoicing feature from Microsoft configuration provider](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started?toc=/dynamics365/finance/toc.json#import-an-electronic-invoicing-feature-from-the-microsoft-configuration-provider)

3.  Create an Electronic invoicing feature under your organization, see [Create an Electronic invoicing feature under your organization provider](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started?toc=/dynamics365/finance/toc.json#create-an-electronic-invoicing-feature-under-your-organization-provider)

### Configuring an e-mail account channel

Configure an e-mail account channel if the Electronic invoicing feature imports electronic vendor invoices from attached files received by e-mails.

1.  In RCS, select the Electronic invoicing feature that you created.

2.  Make sure you selected the **Version** with status **Draft**.

3.  On **Setups** tab, in the grid select a Feature setup, and then select **Edit**.

4.  Select **Data channel** tab.

5.  In the **Parameters** field group, select **Server address** and enter the e-mail account provider.

6.  Select **Server port** and enter the port used by the e-mail account provider.

7.  Select **User name secret** and enter the name of the Key vault secret that contains the ID of the e-mail user account.

8.  Select **User password secret** and enter the name of the Key vault secret that contains the password of the e-mail user account.

9.  Select **Subject filter** and review and update the string that contains the default e-mail subject to identify the e-mail that contains the electronic vendor invoice to import.

10. Select **Applicability rules** tab, review and update the criteria if necessary. For more information, see [Applicability rules](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-configuration-rcs?toc=/dynamics365/finance/toc.json#applicability-rules).

11. Select **Save.**

12. Close the page.

### Configuring a Sharepoint channel

Configure a Sharepoint channel if the Electronic invoicing feature imports electronic vendor invoices from files placed in Sharepoint folders:

1.  In RCS, select the Electronic invoicing feature that you created.

2.  Make sure you selected the **Version** with status **Draft**.

3.  On **Setups** tab, in the grid select a Feature setup, and then select **Edit**.

4.  Select **Data channel** tab.

5.  In the **Parameters** field group, select **Sharepoint address** and enter the URL of the sharepoint.

6.  Select **Server port** and enter the port used by the e-mail account provider.

7.  Select **Application Id** and enter the name of the Key vault secret that contains the ID of the sharepoint client.

8.  Select **Application secret** and enter the name of the Key vault secret that contains the password of the sharepoint client.

9.  Select **File filter** and review and update the mask to filter the files that contain the electronic vendor invoice to import.

10. Select **Applicability rules** tab, review and update the criteria if necessary. For more information, see [Applicability rules](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-configuration-rcs?toc=/dynamics365/finance/toc.json#applicability-rules).

11. Select **Save.**

12. Close the page.

### Deploy to Electronic invoicing feature

To deploy the Electronic invoicing feature, see [Deploy the Electronic invoicing feature to Service environment](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/e-invoicing-get-started?toc=/dynamics365/finance/toc.json#deploy-the-electronic-invoicing-feature-to-service-environment).

## Set up import vendor invoices in Finance and Supply Chain Management

1.  Sign in to Finance and Supply Chain Management and verify you are in the correct legal entity.

2.  Go to **Organization administration &gt; Setup &gt; Electronic document parameters.**

### For Importation of vendor invoices from e-mail:

1.  On **Features** tab, make sure the **NF-e Federal - Brazilian electronic invoice** is selected.

2.  On **External channels** tab, on **Channels** field group, select **Add.**

3.  In the **Channel** field, enter **NFe** (the name of the channel given in the configuration of the data channel for the Electronic invoicing feature in RCS).

4.  In the **Description** field, enter a description.

5.  In the **Company** field, select the Legal entity.

6.  In the **Document context** field, select **Fiscal document context – Customer invoice context model**

7.  In the **Import sources** field group, select **Add.**

8.  In the **Name** field, enter **XmlFile** (the name of the **Attachment filter** given in the configuration of the data channel for the Electronic invoicing feature in RCS)

9.  In the **Description** field, enter a description.

10. In the **Data entity name** field, select **Received NF-e XML documents**.

11. In the **Model mapping** field, select **NF-e mail import – NF-e email import (BR)**

12. Select **Save**.

13. In the **Electronic document** tab, in the **Electronic reporting** field group select **Add.**

14. In the **Table name** field, select **Received NF-e XML document**

15. In the **Document context** field, select **Inquire fiscal document context – Customer invoice context**

16. In the **Electronic document model mapping** field, select **Inquire mapping – Fiscal document mapping**.

17. Select **Response types**, then select **New.**

18. In the **Response type** field, enter **Response**.

19. In the **Submission status** field, enter **Scheduled.**

20. In the **Model mapping** field, select **Model mapping from response message – Response message import format**.

21. Select **Save.**

22. Close the page.

23. Close the page

### For Importation of PEPPOL Electronic vendor invoices:

1.  Go to **Electronic reporting** workspace and select **Reporting configurations.**

2.  Select **Customer invoice context model** and create a derived configuration.

3.  On the **Draft** version, select **Designer.**

4.  On **Data model,** select **Customer invoice** and then select **Map model to datasource.**

5.  On **Definitions,** select **CustomerInvoice** and then select **Designer.**

6.  On **Data sources**, select **Context\_Channel**, and update **Value to "PEPPOL"** (the name of the channel given in the configuration of the data channel for the Electronic invoicing feature in RCS).

7.  Select **Save.**

8.  Close the page.

9.  Close the page.

10. Change **Status** to Completed.

11. Go to **Organization administration &gt; Setup &gt; Electronic document parameters**

12. On **Features** tab, make sure the **PEPPOL Global electronic invoices** is selected.

13. On **External channels** tab, on **Channels** field group, select **Add.**

14. In the **Channel** field, enter **PEPPOL** (the name of the channel given in the configuration of the data channel for the Electronic invoicing feature in RCS).

15. In the **Description** field, enter a description.

16. In the **Company** field, select the Legal entity.

17. In the **Document context** field, select **Customer invoice context – Customer invoice context model**

18. Select **Save.**

19. Close the page.

## Receive electronic invoices

1.  Go to **Organization administration &gt; Periodic &gt; Electronic documents &gt; Receive electronic documents.**

2.  Select **OK.**

3.  Close the page.

## View receive logs for electronic invoices

1.  Go to **Organization administration &gt; Periodic &gt; Electronic documents &gt; Electronic document receipt log.**
