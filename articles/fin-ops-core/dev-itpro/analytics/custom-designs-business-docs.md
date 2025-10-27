---
title: Create custom designs for business documents
description: Learn about how to create a custom report design for an existing application business document by using a pure extension model.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 10/22/2025
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3
ms.assetid: fba7faa3-716b-4adf-ab3e-8573f3614894
---

# Create custom designs for business documents

[!include [banner](../includes/banner.md)]

This article shows how to create a custom report design for an existing application business document by using a pure extension model.

Microsoft Dynamics 365 Finance includes an expanded set of tools to support custom solutions. This article focuses on the steps for creating a custom report design for an existing application business document by using a pure extension model. Follow the steps later in this article to associate a custom report design with an instance of an application document. When you finish, users can configure Print management settings to select the custom design whenever it's appropriate, based on transaction details. The following illustration shows a typical application customization.

:::image type="content" source="./media/extendingprintmgt1.png" alt-text="Screenshot of typical application customization workflow diagram." lightbox="./media/extendingprintmgt1.png":::

## What's important to know?

Before you apply this solution, be aware of the following points:

- Print management settings are scoped to the active legal entity. You can associate custom designs with one or more Print management settings.
- Standard report designs continue to be available alongside custom solutions. Use Print management settings to select the appropriate design, based on transaction details.
- If you introduce a business document for a custom business process, you need to do more work. For more information about how to create a custom business document solution, see the [Print Management Integration Guide](https://www.microsoft.com/download/details.aspx?id=36049).

## Customize a business document

The following walkthrough shows the process of introducing a custom report design for an existing application business document and then using Print management to select the new design. The solution includes a custom design definition for the **Sales confirmation** report that is provided in the standard application as part of the Application Suite model. You define the application customizations in an extension model.

1. **Create a new model for your application customizations.** For more information about extension models, see [Customize through extension and overlayering](../extensibility/customization-overlayering-extensions.md). For this example, add a model named **Application Suite Extensions** that references the Application Suite, Application Platform, and Application Foundation packages.
1. **Create a new project in Microsoft Visual Studio.** Make sure that the project is associated with your extension model. The following illustration shows the project settings.

    :::image type="content" source="./media/app-extension-vs-project-settings.png" alt-text="Screenshot of Project settings dialog in Visual Studio.":::

1. **Create a custom report design for the business document.** Make sure that your custom solution consumes the correct report data contract. Find the existing Application Suite report in Application Explorer. This report is named **SalesConfirm**. Right-click it, then select **Duplicate in project** to create the custom solution.
1. **Rename the report so that it has a meaningful name.** For this example, name the custom report **SalesConfirmExt** to distinguish it from the standard solution. Compile the project, and deploy the report to verify that the changes have no errors.
1. **Use the free-form designer to customize the report design.** Select the report design named **Report**, right-click it, and open the precision designer. Customize the design to satisfy the organization's business requirements. The following illustration shows a custom design definition for the **Sales confirmation** report.

    :::image type="content" source="./media/app-extension-report-designer.png" alt-text="Screenshot of custom design definition for the Sales confirmation report in the report designer." lightbox="./media/app-extension-report-designer.png":::

1. **Add a new X++ class that extends the standard report controller.** Give the class a name that appropriately describes that it's a handler for an existing application report. For this example, rename the class **SalesConfirmControllerExt** to distinguish it from other report controllers.
1. **Use the extended class to load the custom design.** Add a **main** method that refers to the custom report design. (You can just copy the **main** method from the standard solution and add references to the new **Controller** class.) Here's the code that extends the standard solution.

    ```xpp
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
    ```

1. **Add a new report handler (X++) class to the project.** Give the class a name that appropriately describes that it's a handler for Print management–based documents. For this example, rename the class **PrintMgtDocTypeHandlerExt** to distinguish it from other object handlers.
1. **Add a delegate handler method to start to use your custom report.** In this example, extend the **getDefaultReportFormatDelegate** method in the **PrintMgtDocTypeHandlerExt** class by using the following code.

    ```xpp
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
    ```

1. **Extend the menu item for the application report.** Find the existing Application Suite menu item in Application Explorer. This menu item is named **SalesConfirmation**. Right-click it, then select **Create extension**. Open the new extension object in the designer, and set the value of the **Object** property to **SalesConfirmControllerExt** to redirect user navigation to the extended solution.
1. **Update the Print management settings to use the custom business document.** For this example, go to **Accounts receivable** &gt; **Setup** &gt; **Forms** &gt; **Form setup**. Select **Print Management**, find the document configuration settings, then select the custom design. The following illustration shows the Print management settings after the changes have been compiled.

    :::image type="content" source="./media/app-extension-print-mgt-after.png" alt-text="Screenshot of Print Management settings after compilation showing custom design selection." lightbox="./media/app-extension-print-mgt-after.png":::

You've now finished customizing the business document. Users will now be presented with the custom report design for the business document when they process transactions in the application.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
