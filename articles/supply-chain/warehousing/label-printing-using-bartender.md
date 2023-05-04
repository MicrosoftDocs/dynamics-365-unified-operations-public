---
title: Print labels using the BarTender® labeling solution
description: This article describes how to set up and print labels by using the BarTender® label service solution.
author: GalynaFedorova
ms.author: gfedorova
ms.reviewer: kamaybac
ms.search.form: WHSLabelLayout, WHSLabelLayoutDataSource
ms.topic: how-to
ms.date: 01/05/2023
ms.custom: bap-template
---

# Print labels using the BarTender label service solution

[!include [banner](../includes/banner.md)]

<!-- KFM: Find out when and how to use ® and ™ -->

This article describes how to set up and print labels in Microsoft Dynamics 365 Supply Chain Management by using the BarTender® by Seagull Scientific. It's one example that shows how to use the Supply Chain Management external service label printing feature. For general information about how this feature works, see [Print labels using an external service](label-printing-using-external-label-service.md).

The BarTender labeling solution is available both as on-premies software and as a cloud-based software-as-a-service (SaaS) offering. At this time, only BarTender Cloud can be used together with the external label printing service for Supply Chain Management. This topic describes how to integrate Supply Chain Management with the BarTender Cloud™ solution.

This article describes how to communicate with BarTender Cloud by exchanging YAML format documents though the BarTender Cloud REST API. For more information about BarTender Cloud, see [BarTender Cloud](https://www.seagullscientific.com/software/cloud/).

> [!IMPORTANT]
> By enabling the external service integration, you affirm that you understand that the data handling, privacy, and compliance standards of the external service might not be the same as the standards that are provided by Dynamics 365 Supply Chain Management. To learn whether the external service meets your organization's security and privacy requirements, including requirements for the handling of personal data and geo-residency, consult the external service's documentation and terms. Your privacy is important to us. To learn more, read the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

> [!IMPORTANT]
> The information in this article is for general information purposes only. Although we try to keep the information up to date and correct, Microsoft makes no representation or warranties of any kind, express or implied, about accuracy, reliability, or completeness with the respect to the BarTender product. Seagull Scientific might change the functionality of the BarTender product at any time without notice. If you experience any issues or have any additional questions about the BarTender product, contact the [Seagull Scientific Customer Success Team](PSCustomerSuccessTeam@SeagullScientific.com), and they will route you to the appropriate internal resource.

## Prerequisites

To use the features described in this article, you must be running Supply Chain Management version 10.0.34 or later.

## <a name="prepare-integration"></a>Get a copy of your personal access token from BarTender Cloud

Before you can access BarTender Cloud through its REST API, you must get a copy of your personal access token from BarTender Cloud. Supply Chain Management will use this token to authenticate with BarTender Cloud. For more information about how to get this token, see [BarTender Cloud REST API](https://support.seagullscientific.com/hc/en-us/articles/9756611024535) in the BarTender help center.

> [!NOTE]
> Personal access tokens expire after 30 days. You'll have to enter a new token before the old one expires. You can manually refresh the token to obtain a new one.

## Configure Supply Chain Management to print to printers managed by BarTender Cloud

The BarTender Cloud Actions REST API accepts scripts to be run by the BarTender Cloud service in several formats, including YAML-based and JSON-based action scripts and scripts that use the older BarTender XML (BTXML) format. This article describes how to use the `PrintBTWAction` action to print a label based on a design saved in your BarTender Cloud account to a printer accessed through a BarTender Cloud Print Gateway installed on your local network.

### Set up an external service definition for printing through the Actions API

Follow these steps to set up an external service definition.

1. Go to **Warehouse management \> Setup \> External services \> External service definitions**.
1. On the Action Pane, select **New** to create an external service definition.
1. Set the following fields for the new service definition:

    - **External service definition** – Enter a name for the service definition (for example, *BTCloud*).
    - **Description** – Enter a short description of the service definition (for example, *BarTender Cloud*).

1. On the Action Pane, select **Save**.
1. On the **External service operations** FastTab, select **Edit operations** on the toolbar.
1. On the **External service operations** page, on the Action Pane, select **New** to add an operation for printing variable-based layouts. Then follow these steps for the new record.

    - On the header, set the following fields:

        - **External service operation** – Enter a name for the operation (for example, *Actions*).
        - **Description** – Enter a short description of the operation (for example, *Actions API*).

    - On the **General** FastTab, set the following fields:

        - **HTTP method** – Select *POST*.
        - **Operation timeout** – Enter a time-out period for the operation, in milliseconds (for example, *500*).
        - **Request body type** – Select *Raw*.
        - **Relative URL** – Enter */api/actions*.

        > [!NOTE]
        > Cloud Print is a synchronous API. Therefore, it will wait until the label has been printed and will then provide immediate feedback about whether printing was successful. However, because this process can take several seconds, the system might provide a bad user experience for mobile device users. Additionally, the result isn't currently used. Therefore, we recommend that you set a time-out period of 500 milliseconds. Even though Supply Chain Management stops waiting after this time-out expires, printing will continue in the background.

    - On the **Request HTTP headers** FastTab, add a row, and set the following fields for it:

        - **Key** – Enter *Authorization*.
        - **Value** – Enter *Bearer $auth.secret$*. Be sure to enter the value exactly as it appears here.

    - On the **Request body** FastTab, set the following fields:

        - **Content type** – Enter *text/yaml*.
        - **Body** – Enter the content of the request body. Here's an example.

            ```YAML
            - SetVariableAction:
                VariableName: D365PrinterName
                VariableValue: $label.printer$
            $label.body$
            ```

        > [!IMPORTANT]
        > Paste the body text exactly as written. Indentation is important. Be sure to use four spaces to indent, and do not use tabs.

1. On the Action Pane, select **Save**.
1. Select the **Close** button to return to the **External service definition** page.
1. In the list pane, select the record that you were working on at the beginning of this procedure.
1. On the **Label print service** FastTab, set the following fields:

    - **Print operation** – Leave blank.
    - **Variables print operation** – If you created an operation for printing variable-based layouts, select the name of that operation (for example, *Actions*).
    - **Variable label layout template** – If you're using a variable-based layout, enter the content for your variable-based layout template. Here's an example.

        ```YAML
        - PrintBTWAction:
            DocumentFile: librarian://Main/$SystemVariables.LabelFile$
            Printer: "%D365PrinterName%"
            Copies: $SystemVariables.Quantity$
            NamedDataSources:
        {{Row Table=LabelLayoutVariable
              $LabelLayoutVariable.Variable$: $LabelLayoutVariable.Value$
        }}
        ```

### Set up an external service instance for printing through the Actions API

For the this step, you will need the personal access token that you [copied earlier from BarTender Cloud](#prepare-integration).

Follow these steps to set up an external service instance for printing through the Actions API.

1. Go to **Warehouse Management \> Setup \> External services \> External service instances**.
1. On the Action Pane, select **New** to create an external service instance.
1. Set the following fields for the new service instance:
    - **External service instance** – Enter a name for the instance (for example, *BTCloud*).
    - **Description** – Enter a short description of the instance (for example, *BTCloud*).
    - **External service definition** – Select the service definition to use with the instance. The example service definition value that was suggested earlier in this article was *BTCloud*.
1. On the **General** tab, set the following fields:
    - **Base URL** – Enter one of the following instance URLs:
        - `https://am1.bartendercloud.com` for the AMER region
        - `https://eu1.bartendercloud.com` for the EMEA region
        - `https://ap1.bartendercloud.com` for the APAC region
    - **Authentication secret** – Enter the personal access token that you obtained from the BarTender Cloud API page. You should have made a note of this key earlier, when you were [preparing for BarTender integration](#prepare-integration).
    - **Logging level** – Select *Successes and errors*.
    - **Log request bodies** – Select *Successes and errors*.

You can now create label printers and label layouts by using either variables or ZPL.

> [!NOTE]
>
> - When you create label printers on the **Label printers** page in Supply Chain Management, in the **Label print service printer name** field, enter the name of the printer from the **Print dialog** in BarTender Cloud or as retrieved from the Printer API. Use the following format: *printer:workstation/printer*.
> - When you create a variable-based label layout on the **Label layout** page of Supply Chain Management, in the **System Variables** grid, include a row where the **Variable name** field is set to *LabelFile* and the **Value** field is set to the full path and file name of the label (including any folders, if the label file is stored in a folder). The BarTender Cloud REST API uses a Librarian path, but the start of the full Librarian name has already been coded in the variables label template.

## Additional resources

- [Print labels using an external service](label-printing-using-external-label-service.md)
- [Label Layouts](print-license-plate-labels-using-label-layouts.md)
- [Document routing label layouts](document-routing-layout-for-license-plates.md)