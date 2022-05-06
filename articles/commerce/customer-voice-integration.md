---
# required metadata

title: Integrate Customer Voice into e-commerce site pages
description: This topic describes how to integrate Microsoft Dynamics 365 Customer Voice into Microsoft Dynamics 365 Commerce e-commerce site pages.
author: samjarawan
ms.date: 05/06/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2019-10-31

---
# Integrate Customer Voice into e-commerce site pages

[!include [banner](../includes/banner.md)]

This topic describes how to integrate Microsoft Dynamics 365 Customer Voice into Microsoft Dynamics 365 Commerce e-commerce site pages.

You can integrate [Customer Voice](https://dynamics.microsoft.com/customer-voice/overview/) into your e-commerce site to collect, analyze, and track real-time customer feedback. To get started integrating Customer Voice, you must first create an account and select a Customer Voice project template for the type of feedback you want to collect. 

## Integrate the Customer Voice service

To create a Customer Voice account, go the [Customer Voice](https://dynamics.microsoft.com/customer-voice/overview/) and follow the prompts.

After creating a Customer Voice account and signing in, the next step is to select a project template for the type of feedback you want to collect.

To select a Customer Voice project template, follow these steps. 

1. Go to the [Customer Voice project template page](https://customervoice.microsoft.com/Pages/ProjectPage.aspx).
1. Select **Get started**.
1. Select the project template for the type of feedback you want to collect, and then select **Next**.
1. Select the **Send** tab, and then under **Choose an embed format**, select the embed format. The necessary code to embed within site builder appears below **Embedded code**. 

For our examples, we will use the **Periodic customer survey** project template with the **Button** embed code option selected.

The following example illustration shows the **Periodic customer survey** project template page with the **Button** embed code option selected and the associated embed code for that option provided under **Embedded code**. Embedding the provided code in your site pages will require three separate actions, as described in the sections below.

![Customer Voice Periodic customer survey page with the button option selected](media/customer-voice-integration-1.png)

### Embed the external script URL

You must embed the external script URL provided by Customer Voice on all site pages that will have a Customer Voice survey. The best way to embed the script on multiple site pages is to create a fragment in Commerce site builder that contains the external script UR and then add the fragment to the appropriate page template(s). After you publish an updated template, on affected site pages the embedded external script code will look like the following example code:

```html
<script src=https://mfpembedcdnmsit.azureedge.net/mfpembedcontmsit/Embed.js type="text/javascript"></script>
```

For information on fragments, see [Work with fragments](work-with-fragments.md).

> [!NOTE]
> You only need to add the URL to the fragment. The external script module will add the additional script code.

To embed the external script URL into a fragment, follow these steps.

1. Create a fragment in site builder based off the [External script module](script-module.md).
1. In the new fragment, select the **Default external script** slot. 
1. In the **Default external script** properties pane, under **Script source**, add the external script URL as shown in the following example illustration.

    ![External script fragment 2](media/customer-voice-integration-2.png)

1. Select **Save**, and then select **Finish editing**.
1. Select **Publish** to publish the fragment.

The new fragment with the embedded external script block is now ready to be added to the appropriate page template.

### Embed the external style sheet code

You must embed the external stylesheet code provided by Customer Voice on all site pages that will have a Customer Voice survey. Similar to the other embedded code, the best way to embed the external style sheet code on multiple site pages is to create a fragment in Commerce site builder that contains the style sheet code and then add the fragment to the appropriate page template(s). The embedded external style sheet code will look like the following example code:

```html
<link rel="stylesheet" type="text/css" href=https://mfpembedcdnmsit.azureedge.net/mfpembedcontmsit/Embed.css />
```

To embed the external style sheet code into a fragment, follow these steps.

1. Create a fragment in site builder based off the [Metatags](metatags-module.md).
1. In the fragment, select the **Default metatags** slot. 
1. In the **Default metatags** properties pane, under **Meta tags**, add the style sheet URL as shown in the following example illustration.

    ![External script fragment 3](media/customer-voice-integration-3.png)

1. Select **Save**, and then select **Finish editing**.
1. Select **Publish** to publish the fragment.

The new fragment with the embedded external style sheet code is now ready to be added to the appropriate page template.

### Embed the inline script code 

Next, you must embed the inline script code provided by Customer Voice on all site pages that will have a Customer Voice survey. Similar to the other embedded code, the best way to embed the inline script code on multiple site pages is to create a fragment in Commerce site builder that contains the inline script code and then add the fragment to the appropriate page template(s).

In the following example of inline script code, **SURVEY_KEY** is a placeholder. The value for **SURVEY_KEY** should match the actual survey key provided by Customer Voice. The last line calls the code to render the survey button after one second to ensure that enough time is given for the scripts to load. Depending on the survey you selected, you may also need to add or update other metadata such as company name.  

```html
function renderSurveyButton() {
  var se = new SurveyEmbed("SURVEY_KEY","https://customervoice.microsoft.com/","https://mfpembedcdnmsit.azureedge.net/mfpembedcontmsit/","true");

  var context = {
    "First Name":"",
    "Last Name": "",
    "locale": "en-us",
    "companyname": "Adventure Works"
  };
  se.renderButton(context);
}

setTimeout(renderSurveyButton, 4000);
```

To embed the inline script into a fragment, follow these steps.

1. Create a fragment in site builder based off the [inline script](script-module.md).
1. In the fragment, select the **Default inline script** slot. 
1. In the **Default inline script** properties pane, under **Inline script**, add the inline script code as shown in the following example illustration.

    ![Inline script fragment 4](media/customer-voice-integration-4.png)

1. Select **Save**, and then select **Finish editing**.
1. Select **Publish** to publish the fragment.

The new fragment with the embedded inline script code is now ready to be added to the appropriate page template.

## Add fragments to a template

Once the fragments containing the Customer Voice embedded code have been created, you must add the fragments to the page templates associated with the sites you want to use them on. The following example illustration shows our three example fragments added to a product details page (PDP) template. 

![Inline script fragment 5](media/customer-voice-integration-5.png)

Once the updated template is published, the Customer Voice survey will appear on the pages controlled by the template.

For information on templates, see [Work with templates](work-with-templates.md).

## Configure content security policy

After publishing the updated template(s), the survey should fail to load on the relevant site pages since by default content security policy (CSP) won't allow calls to other services without additional configuration. To see the errors, open developer tools within a browser (F12), navigate to a page that has the survey to see the CSP errors in the console output. For more information, see [Content security policy](manage-csp.md).

To configure content security policy in site builder to fix the errors, follow these steps. 

1. Go to **Site settings \> Extensions**.
1. Select the **Content security policy** tab.
1. Add `https://customervoice.microsoft.com/` to the **child-src** directive.
1. Add `https://customervoice.microsoft.com/` to the **frame-src** directive.
1. Add `https://mfpembedcdnmsit.azureedge.net` and ".azureedge.net" to the **img-src**  directive.
