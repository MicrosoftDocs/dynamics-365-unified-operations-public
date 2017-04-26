---
# required metadata

title: Custom designs for business documents
description: This topic shows how to create a custom report design for an existing application business document by using a pure extension model. 
author: sericks007
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 2051
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 266574
ms.assetid: fba7faa3-716b-4adf-ab3e-8573f3614894
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Custom designs for business documents

[!include[banner](../includes/banner.md)]


This topic shows how to create a custom report design for an existing application business document by using a pure extension model. 

Microsoft Dynamics 365 for Operations includes an expanded set of tools to support custom solutions. This topic focuses on the steps for creating a custom report design for an existing application business document by using a pure extension model. Follow the steps later in this topic to associate a custom report design with an instance of an application document. When you've finished, users can configure Print management settings to select the custom design whenever it's appropriate, based on transaction details. The following illustration shows a typical application customization.[![extendingprintmgt](./media/extendingprintmgt1.png)](./media/extendingprintmgt1.png)  

## What's important to know?
Here are some important points that you should be aware of before you apply this solution:

-   Print management settings are scoped to the active legal entity. Custom designs can be associated with one or more Print management settings.
-   Standard report designs continue to be available alongside custom solutions. Use Print management settings to select the appropriate design, based on transaction details.
-   If you introduce a business document for a custom business process, more work is required. For more information about how to create a custom business document solution, see the [Print Management Integration Guide](https://www.microsoft.com/en-us/download/details.aspx?id=36049).

## Customize a business document
The following walkthrough shows the process of introducing a custom report design for an existing application business document and then using Print management to select the new design. The solution includes a custom design definition for the **Sales confirmation** report that is provided in the standard application as part of the Application Suite model. The application customizations will be defined in an extension model.

1.  **Create a new model for your application customizations.** For more information about extension models, see [Customization: Overlayering and extensions](..\extensibility\customization-overlayering-extensions.md). For this example, you add a model that is named **Application Suite Extensions**, and that references the Application Suite, Application Platform, and Application Foundation packages.
2.  **Create a new project in Microsoft Visual Studio.** Make sure that the project is associated with your extension model. The following illustration shows the project settings. [![Project settings in Visual Studio](./media/app-extension-vs-project-settings.png)](./media/app-extension-vs-project-settings.png)
3.  **Create a custom report design for the business document.** You must make sure that your custom solution consumes the correct report data contract. Find the existing Application Suite report in Application Explorer. This report is named **SalesConfirm**. Right-click it, and then click **Duplicate in project** to create the custom solution.
4.  **Rename the report so that it has a meaningful name.** For this example, name the custom report **SalesConfirmExt** to distinguish it from the standard solution. Compile the project, and deploy the report to verify that the changes have no errors.
5.  **Use the free-form designer to customize the report design.** Select the report design that is named **Report**, right-click it, and open the precision designer. Customize the design to satisfy the organization’s business requirements. The following illustration shows a custom design definition for the **Sales confirmation** report. [![Custom design definition for the Sales confirmation report](./media/app-extension-report-designer-1024x613.png)](./media/app-extension-report-designer.png)
6.  **Add a new X++ class that extends the standard report controller.** Give the class a name that appropriately describes that it's a handler for an existing application report. For this example, rename the class **SalesConfirmControllerExt** to distinguish it from other report controllers.
7.  **Use the extended class to load the custom design.** Add a **main** method that refers to the custom report design. (You can just copy the **main** method from the standard solution and add references to the new **Controller** class.) Here is the code that extends the standard solution.

        class SalesConfirmControllerExt extends SalesConfirmController
        {
            public static SalesConfirmControllerExt construct()
            {
                return new SalesConfirmControllerExt();
            }
            public static void main(Args _args)
            {
                SrsReportRunController formLetterController = SalesConfirmControllerExt::construct();
                SalesConfirmControllerExt controller = formLetterController;controller.initArgs(_args, ssrsReportStr(SalesConfirmExt, Report));
                if (classIdGet(_args.caller()) == classNum(SalesConfirmJournalPrint))
                {
                    formLetterController.renderingCompleted += eventhandler(SalesConfirmJournalPrint::renderingCompleted);
                }
                formLetterController.startOperation();
            }
        }

8.  **Add a new report handler (X++) class to the project.** Give the class a name that appropriately describes that it's a handler for Print management–based documents. For this example, rename the class **PrintMgtDocTypeHandlerExt** to distinguish it from other object handlers.
9.  **Add a delegate handler method to start to use your custom report.** In this example, extend the **getDefaultReportFormatDelegate** method in the **PrintMgtDocTypeHandlerExt** class by using the following code.

        class PrintMgtDocTypeHandlersExt
        {
            [SubscribesTo(classstr(PrintMgmtDocType), delegatestr(PrintMgmtDocType, getDefaultReportFormatDelegate))]
            public static void getDefaultReportFormatDelegate(PrintMgmtDocumentType _docType, EventHandlerResult _result)
            {
                switch (_docType)
                {
                    case PrintMgmtDocumentType::SalesOrderConfirmation:
                        _result.result(ssrsReportStr(SalesConfirmExt, Report));
                        break;
                }
            }
        }

10. **Extend the menu item for the application report.** Find the existing Application Suite menu item in Application Explorer. This menu item is named **SalesConfirmation**. Right-click it, and then click **Create extension**. Open the new extension object in the designer, and set the value of the **Object** property to **SalesConfirmControllerExt** to redirect user navigations to the extended solution.
11. **Update the Print management settings to use the custom business document.** For this example, go to **Accounts receivable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**. Click **Print Management**, find the document configuration settings, and then select the custom design. The following illustration shows the Print management settings after the changes have been compiled. [![Print Management settings after compilation](./media/app-extension-print-mgt-after-1024x608.png)](./media/app-extension-print-mgt-after.png)

You’ve now finished customizing the business document. Users will now be presented with the custom report design for the business document when they process transactions in the application.



