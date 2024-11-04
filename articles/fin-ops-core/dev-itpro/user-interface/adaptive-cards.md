---
title: Adaptive Card controls
description: Learn how to use Adaptive Cards that are embedded on pages in finance and operations apps.
author: jaredha
ms.author: jaredha
ms.topic: article
ms.date: 11/04/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2024-10-28
ms.dyn365.ops.version: PU66F
---

# Adaptive Card controls

[!include [banner](../includes/banner.md)]

[Adaptive Cards](/adaptive-cards) are a platform-agnostic way for developers to create rich, interactive, card-like interfaces that can be embedded in various applications, such as Microsoft Teams, Outlook, Copilot Studio chatbots, and other chat or web applications. The key benefit of Adaptive Cards is that developers can design a card once and then use it across multiple platforms without having to adjust the layout for each one. The open card exchange format lets developers describe content as a simple JavaScript Object Notation(JSON) object. Therefore, it's easy to structure and manipulate cards dynamically.

The Adaptive Cards control for finance and operations apps lets developers render Adaptive Cards natively on application pages. Learn more on the [Adaptive Cards](https://adaptivecards.io) site, which includes documentation, samples, and a designer that you can use to start to build your own Adaptive Cards.

:::image type="content" source="./media/AdaptiveCardControl.png" alt-text="Screenshot of an Adaptive Card that shows a customer profile and insights on the Customers page in finance and operations apps.":::

## Using Adaptive Cards

To use an Adaptive Card on a page in finance and operations apps, follow these steps.

1. Define the data contract for the data properties that populate the Adaptive Card.
1. Configure the Adaptive Card template to define the card's layout and formatting.
1. Add the Adaptive Card control to the page.
1. Define the data that populates the card.

### Define the data properties for an Adaptive Card

First define the data properties that populate the Adaptive Card. Create a new class as a data contract that extends the `AdaptiveCardData` class, and define the properties. Then add an accessor method for each property in the class.

The following example shows a class that contains properties for an Adaptive Card that displays a profile and insights about a customer record.

```X++
[DataContract]
public class AdaptiveCardCustomerData extends AdaptiveCardData
{
    private str custName = "";
    private str profileImage = "";
    private str createdUtc = "2017-02-14T06:08:39Z";
    private str custDescription = "";
    private str custInsightsTitle = "";
    private str custInsights = "";

    [DataMember("custName")]
    public str custName(str _custName = custName)
    {
        custName = _custName;
        return custName;
    }

    [DataMember("profileImage")]
    public str profileImage(str _profileImage = profileImage)
    {
        profileImage = _profileImage;
        return profileImage;
    }

    [DataMember("createdUtc")]
    public str createdUtc(str _createdUtc = createdUtc)
    {
        createdUtc = _createdUtc;
        return createdUtc;
    }

    [DataMember("custDescription")]
    public str custDescription(str _custDescription = custDescription)
    {
        custDescription = _custDescription;
        return custDescription;
    }

    [DataMember("custInsightsTitle")]
    public str custInsightsTitle(str _custInsightsTitle = custInsightsTitle)
    {
        custInsightsTitle = _custInsightsTitle;
        return custInsightsTitle;
    }

    [DataMember("custInsights")]
    public str custInsights(str _custInsights = custInsights)
    {
        custInsights = _custInsights;
        return custInsights;
    }
}
```

### Configure the Adaptive Card template

After you define the properties that populate the Adaptive Card, configure the Adaptive Card template to control how the fields are laid out on the card. The template defines the layout and formatting of the data on the Adaptive Card control. 

To define how the fields are laid out on an Adaptive Card, follow these steps.

1. Create a class that extends the `AdaptiveCardTemplate` class.
1. Define the class as a data contract that has accessor methods to return properties that are set in the class.
1. For the `type` property, provide a value that is used as an identifier for the template type.
1. For the `template` property, provide a string of the JSON object that defines the layout and format of the Adaptive Card.

    > [!TIP]
    > If you need help creating the JSON for the Adaptive Card template, you can use tools such as the [Adaptive Cards designer](https://adaptivecards.io/designer).

1. Build your project to make the template available for use on pages finance and operations apps.

The following example shows a class for an Adaptive Card template. This class includes actions to refresh the contents of the card, copy defined card elements, and provide feedback through thumbs-up and thumbs-down voting.

```X++
[DataContract]
public class AdaptiveCardCustomerTemplate extends AdaptiveCardTemplate
{
    List dataToCopy;

    public void new()
    {
        super();
        this.type("CustomerCard");
        this.template(strFmt('{"type":"AdaptiveCard","$schema":"https://adaptivecards.io/schemas/adaptive-card.json","version":"1.5","id":"CustomerCard","body":[{"type": "ColumnSet", "columns": [{"type": "Column", "items": [{"type": "Image", "style": "Person", "url": "${profileImage}", "altText": "${custName}", "size": "Small"}], "width": "auto"},{"type": "Column", "items": [{"type": "TextBlock", "size": "Medium", "weight": "Bolder", "text": "${custName}", "wrap": true}, {"type": "TextBlock", "spacing": "None", "text": "Customer since {{DATE(${createdUtc},SHORT)}}", "isSubtle": true, "wrap": true}], "width": "stretch"},{"type":"Column","width":"auto","items":[{"type":"ActionSet","id":"headingActions","actions":[{"type":"Action.Execute","id":"RefreshCard","title":"%1","mode":"secondary","iconUrl":"icon:ArrowClockwise"}]}]}]},{"type":"TextBlock","text":"${custDescription}","wrap":true,"spacing":"Medium"},{"type": "TextBlock", "size": "Medium", "weight": "Bolder", "text": "${custInsightsTitle}", "wrap":true, "Spacing": "Medium"}, {"type": "TextBlock", "text": "${custInsights}", "wrap": true}]}',
            "@AdaptiveCardControl:Refresh"));
    }
}
```

### Add the Adaptive Card control to a page

To add an Adaptive Card control in the desired place on a page in finance and operations apps, follow these steps. 

1. In Visual Studio, in the page design of the page in your development environment for finance and operations apps, select and hold (or right-click) the node where you want to put the Adaptive Card. Then select **New** \> **Adaptive card**.
1. In the properties for the control, for the **Name** property, provide a name for the new card.
1. For the **Template class** property, select the template class that you created earlier.

### Populate the data properties on the Adaptive Card

After the Adaptive Card control is added to the desired page, you can define the data that populates the properties in the template for the card.

To populate the data properties for an Adaptive Card, follow these steps.

1. View the code for the page where you added the Adaptive Card.
1. Create an instance of your data class, and populate the properties of the data contract.
1. Create a class that defines any actions that should be added to the template.

The following example shows the definition of properties and actions to populate the template that you created earlier.

```X++
[Form]
public class MyCustomerInsightsForm extends FormRun
{
    AdaptiveCardCustomerData currentData;

    public void run()
    {
        super();

        if (SysUserInfo::find().Density == SysUserInfoDensity::Density21)
        {
            CustomerProfile.widthValue(420);
            CustomerProfile.heightValue(190);
        }

        currentData = new AdaptiveCardCustomerData();
        currentData.custName('Contoso Electronics');
        currentData.profileImage('https://media.licdn.com/dms/image/C560BAQFJq1MdKASLWA/company-logo_200_200/0/1591822700485?e=2147483647&v=beta&t=BrJUkBS5fE2EO3x5XsiiakRIDzN5GXqzPV6U1oEHOc8');
        currentData.createdUtc('2017-02-14T06:08:39Z');
        currentData.custDescription('Contoso Electronics is a mid-sized IT service provider specializing in network infrastructure, cybersecurity, and cloud migration for small-to-medium businesses.');
        currentData.custInsightsTitle("Customer Insights");
        currentData.custInsights('- Needs streamlined tools for remote network monitoring and incident response.\n- Anticipating 20% growth with plans for new hires in cybersecurity and cloud engineering\n- Current outstanding balance: $35,000\n- Payment history: Generally prompt but had delayed payments twice in the past year due to cash flow adjustments during expansion phases.');

        CustomerProfile.cardData(currentData);
    }

    [Control("Custom")]
    class CustomerProfile
    {
        public void executeAction(str actionId, str actionPayload)
        {
            super(actionId, actionPayload);

            if (actionId == "RefreshCard")
            {
                currentData.custName('Contoso Electronics');
                currentData.profileImage('https://media.licdn.com/dms/image/C560BAQFJq1MdKASLWA/company-logo_200_200/0/1591822700485?e=2147483647&v=beta&t=BrJUkBS5fE2EO3x5XsiiakRIDzN5GXqzPV6U1oEHOc8');
                currentData.createdUtc('2017-02-14T06:08:39Z');
                currentData.custDescription('Contoso Electronics is a mid-sized IT service provider specializing in network infrastructure, cybersecurity, and cloud migration for small-to-medium businesses.');
                currentData.custInsightsTitle('Customer Insights');
                currentData.custInsights('- Needs streamlined tools for remote network monitoring and incident response.\n- Anticipating 20% growth with plans for new hires in cybersecurity and cloud engineering\n- Current outstanding balance: $35,000\n- Payment history: Generally prompt but had delayed payments twice in the past year due to cash flow adjustments during expansion phases.');
                CustomerProfile.cardData(currentData);
            }
        }
    }
}
```
