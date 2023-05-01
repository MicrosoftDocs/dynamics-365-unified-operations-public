---
title: Print labels using the Loftware NiceLabel label service solution
description: This article describes how to set up and print labels by using Loftware NiceLabel label service solution.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 04/04/2023
ms.custom: bap-template
---

# Print labels using the Loftware NiceLabel label service solution

[!include [banner](../includes/banner.md)]

This article describes how to set up and print labels in Microsoft Dynamics 365 Supply Chain Management by using the Loftware NiceLabel solution. It's one example that shows how to use the Supply Chain Management external service label printing feature. For general information about how this feature works, see [Print labels using an external service](label-printing-using-external-label-service.md).

Loftware NiceLabel lets you create, manage, and print standardized, compliant bar code labels. It also lets you print labels to supported cloud-connected printers or a wide variety of classic on-premises printers. NiceLabel has several products that can be used together with the external label printing service, including a cloud solution (NiceLabel Cloud) and several versions of their on-premises products. This article focuses on how to integrate Supply Chain Management with the NiceLabel Cloud solution.

For more information about Loftware NiceLabel Cloud, see [Loftware NiceLabel Cloud & Label Management System](https://www.loftware.com/products/labeling/nicelabel-cloud).

> [!IMPORTANT]
> By enabling the external service integration, you affirm that you understand that the data handling, privacy, and compliance standards of the external service might not be the same as the standards that are provided by Dynamics 365 Supply Chain Management. To learn whether the external service meets your organization's security and privacy requirements, including requirements for the handling of personal data and geo-residency, consult the external service's documentation and terms. Your privacy is important to us. To learn more, read the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

NiceLabel Cloud supports two integration approaches for other cloud applications:

- **Cloud Print API** – NiceLabel Cloud generates the labels and sends print jobs to the printer. This printer can be either a so-called *cloud printer* (a printer that's connected directly to the NiceLabel Cloud instance, without using any locally installed software or printer driver) or any printer that's connected to a workstation where a print gateway component is installed. For the current list of supported cloud printers, see the [Loftware website](https://www.loftware.com/).
- **Cloud Trigger API** – NiceLabel Cloud sends messages to an on-premises NiceLabel Automation Service instance, which generates the labels and sends them to the printer. You must install a Windows printer driver for each of your printers.

If you don't want any local software footprint, the preferred option is to use the Cloud Print API together with supported printers. Otherwise, we recommend that you use the Cloud Trigger API. Nevertheless, both options are available.

Here are some of the pros and cons of each integration option:

- The Cloud Trigger API lets you use an out-of-box cloud integration pack or completely customize the processing of print requests.
- The Cloud Print API is synchronous. In other words, the server waits for the print engine to print the label. Although the Cloud Print API reports the outcome of the print job, Supply Chain Management doesn't use that result. Therefore, you must wait a little longer when you print labels, or you must set a time-out on the external service operation. If a time-out occurs, the Cloud Print API will continue to print, but the request will be logged as a time-out.
- On-premises printer naming is simpler in the Cloud Trigger API, because you can use the names of the printers as they're configured on the servers that run the NiceLabel Automation Service. To use the Cloud Print API, you must specify a workstation ID to indicate which workstation you want to print to.
- For the Cloud Trigger API, you can install multiple instances of the NiceLabel Automation Service on the local network to achieve load balancing and high availability. As was noted in the previous point, you must specify which workstation the printing request should be routed to. If that workstation isn't available, the label won't be printed. Conversely, multiple NiceLabel Automation Service instances can handle requests to the same cloud trigger.
- The Cloud Print API has a smaller installation footprint.

> [!IMPORTANT]
> The information in this article is for general information purposes only. Although we try to keep the information up to date and correct, Microsoft makes no representation or warranties of any kind, express or implied, about accuracy, reliability, or completeness with the respect to the NiceLabel product. Loftware might change the functionality of the NiceLabel product at any time without notice. If you experience any issues or have any additional questions about the NiceLabel product, contact Loftware directly.

## <a name="prepare-integration"></a>Prepare for NiceLabel Cloud integration

Before you can access NiceLabel Cloud by using either the Cloud Print API or the Cloud Trigger API, you must register in the NiceLabel Developer Portal and then link your Developer Portal subscription with your NiceLabel Cloud instance. For instructions, see [Cloud Integrations](https://help.nicelabel.com/hc/en-001/articles/4402966072209-Cloud-Integrations#cloud-integrations-1-0) in the NiceLabel Help Center.

> [!IMPORTANT]
> When you register in the NiceLabel Developer Portal, be sure to make a copy of your primary or secondary subscription key. (Use the primary key by default.) You'll need this key to configure the external service definition later.

If you want to use printers that are enabled for the Internet of Things (IoT), you must connect them to your NiceLabel Cloud instance. For instructions, see [Cloud Printers](https://help.nicelabel.com/hc/en-001/articles/4407466158737-Cloud-Printers) in the NiceLabel Help Center.

## Configure Supply Chain Management to print to cloud printers by using the Cloud Print API

By using the Cloud Print API, you can print labels that NiceLabel Cloud generates based on variables that are sent from Supply Chain Management. You can also send a Zebra Programming Language (ZPL) label, such as an existing label layout or a shipping label that's provided by a shipping carrier for small parcel shipping (SPS) integration.

This section describes how to set up an external service definition that has two operations: one for printing variable-based layouts and one for printing ZPL-based label layouts. If you don't have to use both types of layout, you can set up just one of the two operations that are described here.

### Set up an external service definition for printing through the Cloud Print API

Follow these steps to set up an external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following fields for the new service definition:

    - **External service definition** – Enter a name for the service definition (for example, *NLPrint*).
    - **Description** – Enter a short description of the service definition (for example, *NiceLabel Cloud Print API*).

1. On the Action Pane, select **Save**.
1. On the **External service operations** FastTab, select **Edit operations** on the toolbar.
1. On the **External service operations** page, on the Action Pane, select **New** to add an operation for printing variable-based layouts. Then follow these steps for the new record. If you don't use variable-based layouts, you can skip ahead to step 8.

    - On the header, set the following fields:

        - **External service operation** – Enter a name for the operation (for example, *Print*).
        - **Description** – Enter a short description of the operation (for example, *Print to cloud printer*).

    - On the **General** FastTab, set the following fields:

        - **HTTP method** – Select *POST*.
        - **Operation timeout** – Enter a time-out period for the operation, in milliseconds (for example, *500*).
        - **Request body type** – Select *Raw*.
        - **Relative URL** – Enter */Print/v2/Print*.

        > [!NOTE]
        > Cloud Print is a synchronous API. Therefore, it will wait until the label has been printed and will then provide immediate feedback about whether printing was successful. However, because this process can take several seconds, the system might provide a bad user experience for mobile device users. Additionally, the result isn't currently used. Therefore, we recommend that you set a time-out period of 500 milliseconds. Even though Supply Chain Management stops waiting after this time-out expires, printing will continue in the background.

    - On the **Request HTTP headers** FastTab, add a row, and set the following fields for it:

        - **Key** – Enter *Ocp-Apim-Subscription-Key*.
        - **Value** – Enter *\$auth.secret\$*. Be sure to enter the value exactly as it appears here.

    - On the **Request body** FastTab, set the following fields:

        - **Content type** – Enter *application/json*.
        - **Body** – Enter the content of the request body. Here's an example.

            ```JSON
            {
                "deviceType": "CloudPrinter",
                "deviceId": {
                    "printerName": "$label.printer$",
                    "workstation": null
                },
                $label.body$
            }
            ```

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **New** to add an operation for printing ZPL-based layouts. Then follow these steps for the new record. If you don't use ZPL-based layouts, you can skip ahead to step 10.

    - On the header, set the following fields:

        - **External service operation** – Enter a name for the operation (for example, *SendData*).
        - **Description** – Enter a short description of the operation (for example, *Send ZPL to cloud printer*).

    - On the **General** FastTab, set the following fields:

        - **HTTP method** – Select *POST*.
        - **Operation timeout** – Enter a time-out period for the operation, in milliseconds (for example, *500*).
        - **Request body type** – Select *Raw*.
        - **Relative URL** – Enter */Print/v2/SendData*.

    - On the **HTTP request headers** FastTab, add a row, and set the following fields for it:

        - **Key** – Enter *Ocp-Apim-Subscription-Key*.
        - **Value** – Enter *\$auth.secret\$*. Be sure to enter the value exactly as it appears here.

    - On the **Request body** FastTab, set the following fields:

        - **Content type** – Enter *application/json*.
        - **Body** – Enter the content of the request body. Here's an example.

            ```JSON
            {
                "deviceType": "CloudPrinter",
                "deviceId": {
                    "printerName": "$label.printer$",
                    "workstation": null
                },
                "data": "$label.body:base64$"
            }
            ```

1. On the Action Pane, select **Save**.
1. Select the **Close** button to return to the **External service definition** page.
1. In the list pane, select the record that you were working on at the beginning of this procedure.
1. On the **Label print service** FastTab, set the following fields:

    - **Print operation** – If you created an operation for printing ZPL-based layouts, select the name of that operation (for example, *SendData*).
    - **Variables print operation** – If you created an operation for printing variable-based layouts, select the name of that operation (for example, *Print*).
    - **Variable label layout template** – If you're using a variable-based layout, enter the content for your variable-based layout template. Here's an example.

        ```JSON
        "filePath": "$SystemVariables.LabelFile$",
        "quantity": "$SystemVariables.Quantity$",
        "dataSources": [
            {
                {{Row Table=LabelLayoutVariable
                    "$LabelLayoutVariable.Variable$": "$LabelLayoutVariable.Value$",
                }}
            }
        ]
        ```

### Set up an external service instance for printing through the Cloud Print API

Follow these steps to set up an external service instance for printing through the Cloud Print API.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following fields for the new service instance:

    - **External service instance** – Enter a name for the instance (for example, *NLPrintProd*).
    - **Description** – Enter a short description of the instance (for example, *NiceLabel Cloud Print API Production*).
    - **External service definition** – Select the service definition to use with the instance. The example service definition value that was suggested earlier in this article was *NLPrint*.

1. On the **General** tab, set the following fields:

    - **Base URL** – Enter `https://labelcloudapi.onnicelabel.com`.
    - **Authentication secret** – Enter your primary or secondary subscription key from the NiceLabel Developer Portal. You should have made a note of this key earlier, when you were [preparing for NiceLabel integration](#prepare-integration).
    - **Logging level** – Select *Successes and errors*.
    - **Log request bodies** – Select *Successes and errors*.

You can now create label printers and label layouts by using either variables or ZPL.

> [!NOTE]
> - When you create label printers on the **Label printers** page in Supply Chain Management, in the **Label print service printer name** field, enter the name of the printer from the **Cloud printers** tab in NiceLabel Cloud Control Center.
> - When you create a variable-based label layout on the **Label layout** page of Supply Chain Management, in the **System Variables** grid, include a row where the **Variable name** field is set to *LabelFile* and the **Value** field is set to the full path and file name of the label. To find the full path and file name, sign in to NiceLabel Control Center, and then, on the **Documents** tab, select the label file, and copy the full value of the **Path** field (under **File properties**).

## Configure Supply Chain Management to print to local network printers by using the Cloud Trigger API

By using the Cloud Trigger API, you can call an on-premises installation of the NiceLabel Automation Service, which then processes the request and performs preprogrammed actions. Before you move on to the next steps, install NiceLabel on the computers that will run the NiceLabel Automation Service, and set up the required printers for those computers. For guidance that will help you install and set up printers, see the NiceLabel documentation.

To simplify the configuration of the NiceLabel Automation Service, use the NiceLabel Cloud Data Integration pack, and follow the instructions in [Appendix A: Integration bundle](https://help.nicelabel.com/hc/en-001/articles/7361192275217-Appendix-A-Integration-bundle) in the NiceLabel Help Center. The following procedure summarizes the required steps. More details are provided in the NiceLabel Help Center.

1. Download the integration pack by using the link that's provided.
1. Sign in to NiceLabel Control Center.
1. On the **Documents** tab, create the following folder: `/Demo/LabelCloudDataIntegration`.
1. Open the zip file that you downloaded, and extract the files.
1. Upload the contents of your document storage folder into the `LabelCloudDataIntegration` folder in NiceLabel Control Center.
1. On the computer where the NiceLabel Automation Service is installed, open NiceLabel Automation Manager.
1. If you haven't already done so, connect the NiceLabel Automation Service to your NiceLabel Cloud instance.
1. In NiceLabel Automation Manager, select **Add**, and browse to the `LabelCloudDataIntegration` folder in NiceLabel Cloud.
1. Open the `CloudIntegration-CloudTrigger.misx` file.
1. Verify that the print trigger is using the unique identifier *Api-CloudIntegrationDemo-Print*. Then start only this trigger. Supply Chain Management doesn't currently support other triggers.

After you've installed and started the print trigger, you're ready to configure the external service definition and external service instance that are required to access the NiceLabel Automation Service by using the Cloud Trigger API. Unless you customize the demo automation configuration, you can print only variable-based layouts, not ZPL-based layouts. In this case, you'll have to configure only one operation on the external service definition.

### Set up an external service definition for printing through the Cloud Trigger API

Follow these steps to set up an external service definition for printing through the Cloud Trigger API.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following fields for the new service definition:

    - **External service definition** – Enter *NLTrigger*.
    - **Description** – Enter *NiceLabel Label Cloud Trigger API*.

1. On the Action Pane, select **Save**.
1. On the **External service operations** FastTab, select **Edit operations** on the toolbar.
1. On the **External service operations** page, on the Action Pane, select **New** to add an operation for the *Print* service operation. Then follow these steps for the new record:

    - On the header, set the following fields:

        - **External service operation** – Enter a name for the operation (for example, *Print*).
        - **Description** – Enter a short description of the operation (for example, *Print to local printer*).

    - On the **General** FastTab, set the following fields:

        - **HTTP method** – Select *POST*.
        - **Operation timeout** – Enter a time-out period for the operation, in milliseconds (for example, *500*).
        - **Request body type** – Select *Raw*.
        - **Relative URL** – Enter */Trigger/v1/CloudTrigger/Api-CloudIntegrationDemo-Print*.

    - On the **HTTP request headers** FastTab, add a row, and set the following fields for it:

        - **Key** – Enter *Ocp-Apim-Subscription-Key*.
        - **Value** – Enter *\$auth.secret\$*. Be sure to enter the value exactly as it appears here.

    - On the **Request body** FastTab, set the following fields:

        - **Content type** – Enter *application/json*.
        - **Body** – Enter the content of the request body. Here's an example.

            ```JSON
            {
                "Printer": "$label.printer$",
                $label.body$
            }
            ```

1. On the Action Pane, select **Save**.
1. Select the **Close** button to return to the **External service definition** page.
1. On the **Label print service** FastTab, set the following fields:

    - **Print operation** – Leave this field blank.
    - **Variables print operation** – Select the print operation that you created earlier in this procedure (for example, *Print*).
    - **Variable label layout template** – Enter the content for your variable-based layout template. Here's an example.

        ```JSON
        "FilePath": "$SystemVariables.LabelFile$",
        "Quantity": "$SystemVariables.Quantity$",
        "Variables": [
            {{Row Table=LabelLayoutVariable
                { 
                    "Name": "$LabelLayoutVariable.Variable$",
                    "Value": "$LabelLayoutVariable.Value$"
                },
            }}
        ]
        ```

### Set up an external service instance for printing through the Cloud Trigger API

Follow these steps to set up an external service instance for printing through the Cloud Trigger API.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following fields for the new service instance:

    - **External service instance** – Enter a name for the instance (for example, *NLTriggerProd*).
    - **Description** – Enter a short description of the instance (for example, *NiceLabel Cloud Trigger API Production*).
    - **External service definition** – Select the service definition to use. The example service definition value that was suggested earlier in this article was *NLTrigger*.

1. On the **General** tab, set the following fields:

    - **Base URL** – Enter `https://labelcloudapi.onnicelabel.com`.
    - **Authentication secret** – Enter your primary or secondary subscription key from the NiceLabel Developer Portal. You should have made a note of this key earlier, when you were [preparing for NiceLabel integration](#prepare-integration).
    - **Logging level** – Select *Successes and errors*.
    - **Log request bodies** – Select *Successes and errors*.

You can now create label printers and label layouts by using variables.

> [!NOTE]
> - When you create label printers on the **Label printers** page in Supply Chain Management, in the **Label print service printer name** field, enter the name of the printer from the **Cloud printers** tab in NiceLabel Cloud Control Center.
> - When you create a variable-based label layout on the **Label layout** page of Supply Chain Management, in the **System Variables** grid, include a row where the **Variable name** field is set to *LabelFile* and the **Value** field is set to the full path and file name of the label. To find the full path and file name, sign in to NiceLabel Control Center, and then, on the **Documents** tab, select the label file, and copy the full value of the **Path** field (under **File properties**).

## Additional resources

- [Print labels using an external service](label-printing-using-external-label-service.md)
- [Label Layouts](print-license-plate-labels-using-label-layouts.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)
