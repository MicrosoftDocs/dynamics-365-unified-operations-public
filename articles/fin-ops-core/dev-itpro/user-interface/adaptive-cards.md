---
title: Adaptive Card controls
description: Use Adaptive Cards embedded in forms in finance and operations apps
author: jaredha
ms.author: jaredha
ms.topic: article
ms.date: 02/08/2023
ms.reviewer: 
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2024-10-28
ms.dyn365.ops.version: PU66
ms.assetid: 
---

# Adaptive Card controls

[!include [banner](../includes/banner.md)]

[Adaptive Cards](https://learn.microsoft.com/adaptive-cards) are a platform-agnostic way for developers to create rich, interactive card-like interfaces that can be embedded in various applications like Microsoft Teams, Outlook, Copilot Studio chatbots, and other chat or web applications. The key benefit of Adaptive Cards is that they allow developers to design a card once and use it across multiple platforms without needing to adjust the layout for each one. The open card exchange format enables developers to describe content as a simple JSON object, making it easy to structure and manipulate cards dynamically.

The Adaptive Cards control for finance and operations apps enables developers to render Adaptive Cards natively in application forms. See [https://adaptivecards.io](https://adaptivecards.io) for more information on Adaptive Cards, including documentation, samples, and a designer to get started in building your Adaptive Cards.

## Using Adaptive Cards
The following steps are needed to use Adaptive Cards on forms in finance and operations apps:
1. Define the data contract for the data properties that will populate the adaptive card.
2. Configure the Adaptive Card template to define the card layout and formatting.
3. Add the Adaptive Card control to the form.
4. Define the data that will populate the card.

### Define the data properties for your Adaptive Card
First define the data properties that populate your Adaptive Card. This is done by creating a new class as a data contract that extends the `AdaptiveCardData` class. Define the properties and add an accessor method for each property in the class.

The following provides an example class for properties that may be used for an Adaptive Card displaying a profile and insights about a customer record.

```X++
[DataContract]
public class AdaptiveCardCustomerData extends AdaptiveCardData
{
    private str cardTitle = "";
    private str custName = "";
    private str profileImage = "";
    private str createdUtc = "2017-02-14T06:08:39Z";
    private str custDescription = "";
    private str custInsightsTitle = "";
    private str custInsights = "";
    private int feedback = 0;

    [DataMember("cardTitle")]
    public str cardTitle(str _cardTitle = cardTitle)
    {
        cardTitle = _cardTitle;
        return cardTitle;
    }

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

    [DataMember("feedback")]
    public int Feedback(int _feedback = feedback)
    {
        feedback = _feedback;
        return feedback;
    }
}
```

### Configure the Adaptive Card template
After defining the properties that will display on the Adaptive Card, you define how the fields will be laid out on the card. The Adaptive Card template defines the layout and formatting of the data on the Adaptive Card control. 
1. Create a class that extends the `AdaptiveCardTemplate` class.
2. Define the class as a data contract with accessor methods to return properties set in the class.
3. Provide a value for the `type` property that will be used as an identifier for the template type.
4. The `template` property is set to a string of the JSON object that defines the layout and format of the Adaptive Card.

> [!TIP]
> You can use tools like the [Adaptive Cards designer](https://adaptivecards.io/designer) for assistance in creating the JSON for the Adaptive Card template.

The following is an example class for an Adaptive Card template. This example includes actions to refresh the contents of the card, copy defined card elements, and provide feedback with thumbs up and down voting.

```X++
[DataContract]
public class AdaptiveCardCustomerTemplate extends AdaptiveCardTemplate
{
    List dataToCopy;

    public void new()
    {
        super();
        this.type("CustomerCard");
        this.template(strFmt('{"type":"AdaptiveCard","$schema":"https://adaptivecards.io/schemas/adaptive-card.json","version":"1.5","id":"CustomerCard","body":[{"type":"ColumnSet","columns":[{"type":"Column","width":"auto","items":[{"type":"Icon","name":"TextBulletListSquareSparkle","color":"Accent","size":"Small"}]},{"type":"Column","width":"stretch","items":[{"type":"TextBlock","text":"${cardTitle}","wrap":true,"style":"heading","horizontalAlignment":"Left"}],"verticalContentAlignment":"Center"},{"type":"Column","width":"auto","items":[{"type":"ActionSet","id":"headingActions","actions":[{"type":"Action.Execute","id":"RefreshCard","title":"%1","mode":"secondary","iconUrl":"icon:ArrowClockwise"}]}]}]},{"type": "ColumnSet", "columns": [{"type": "Column", "items": [{"type": "Image", "style": "Person", "url": "${profileImage}", "altText": "${custName}", "size": "Small"}], "width": "auto"}, {"type": "Column", "items": [{"type": "TextBlock", "weight": "Bolder", "text": "${custName}", "wrap": true}, {"type": "TextBlock", "spacing": "None", "text": "Customer since {{DATE(${createdUtc},SHORT)}}", "isSubtle": true, "wrap": true}], "width": "stretch"}]},{"type":"TextBlock","text":"${custDescription}","wrap":true,"spacing":"Medium"},{"type": "TextBlock", "size": "Medium", "weight": "Bolder", "text": "${custInsightsTitle}", "wrap":true, "Spacing": "Medium"}, {"type": "TextBlock", "text": "${custInsights}", "wrap": true},{"type":"ColumnSet","spacing":"Medium","columns":[{"type":"Column","width":"stretch","items":[{"type":"ActionSet","actions":[{"type":"Action.Execute","title":"%2","id":"CopyToClipboard","iconUrl":"icon:Copy"}]}]},{"type":"Column","width":"auto","items":[{"type":"ColumnSet","columns":[{"type":"Column","width":"auto","items":[{"type":"Icon","name":"ThumbLike","size":"xSmall","color":"Accent","style":"${if(feedback > 0, \'Filled\', \'Regular\')}","selectAction":{"type":"Action.Execute","id":"FeedbackLike","tooltip":"%3"}}]},{"type":"Column","width":"auto","items":[{"type":"Icon","name":"ThumbDislike","size":"xSmall","color":"Accent","style":"${if(feedback < 0, \'Filled\', \'Regular\')}","selectAction":{"type":"Action.Execute","id":"FeedbackDislike","tooltip":"%4"}}]}]}],"verticalContentAlignment":"Center"}]}]}',
            "@AdaptiveCardControl:Refresh",
            "@AdaptiveCardControl:Copy",
            "@AdaptiveCardControl:Useful",
            "@AdaptiveCardControl:NotUseful"));

        List il = new List(Types::String);
        il.addEnd("custName");
        il.addEnd("custDescription");
        il.addEnd("custInsights");

        this.dataToCopy(il);
    }

    [DataMember("dataToCopy")]
    public List dataToCopy(List _dataToCopy = dataToCopy)
    {
        dataToCopy = _dataToCopy;
        return dataToCopy;
    }
}
```

### Add the Adaptive Card control
Add the Adaptive Card control in the desired placement on your form. 
1. On the form in your development environment for finance and operations apps in Visual Studio, right-click the node in your form design where you want to place the Adaptive Card.
2. On the context menu, select **New > Adaptive card**.
3. On the **Properties** for the control, provide a **Name**, and select the template class created earlier in the **Template class** property.

### Populate the data properties on the Adaptive Card
When the Adaptive Card control is added to your form, you can now define the data that will populate the properties in your template for the card.
1. View the code for the form where you added the Adaptive Card.
2. Create an instance of your data class, and populate the properties of the data contract.
3. Create a class that defines any actions added to the template.

The following example shows the defining properties and actions to populate the template created in previous steps:

```X++
[Form]
public class MyCustomerInsightsForm extends FormRun
{
    AdaptiveCardCustomerData currentData2;

    public void run()
    {
        super();

        if (SysUserInfo::find().Density == SysUserInfoDensity::Density21)
        {
            SummaryCard2.widthValue(420);
            SummaryCard2.heightValue(190);
        }

        currentData2 = new AdaptiveCardCustomerData();
        currentData2.cardTitle('Customer Profile');
        currentData2.custName('Contoso Electronics');
        currentData2.profileImage('https://media.licdn.com/dms/image/C560BAQFJq1MdKASLWA/company-logo_200_200/0/1591822700485?e=2147483647&v=beta&t=BrJUkBS5fE2EO3x5XsiiakRIDzN5GXqzPV6U1oEHOc8');
        currentData2.createdUtc('2017-02-14T06:08:39Z');
        currentData2.custDescription('Contoso Electronics is a mid-sized IT service provider specializing in network infrastructure, cybersecurity, and cloud migration for small-to-medium businesses.');
        currentData2.custInsightsTitle("Customer Insights");
        currentData2.custInsights('- Needs streamlined tools for remote network monitoring and incident response.\n- Anticipating 20% growth with plans for new hires in cybersecurity and cloud engineering\n- Current outstanding balance: $35,000\n- Payment history: Generally prompt but had delayed payments twice in the past year due to cash flow adjustments during expansion phases.');

        SummaryCard2.cardData(currentData2);
    }

    [Control("Custom")]
    class SummaryCard2
    {
        public void executeAction(str actionId, str actionPayload)
        {
            super(actionId, actionPayload);

            if (actionId == "FeedbackLike")
            {
                if (currentData2.Feedback() != 1)
                {
                    currentData2.Feedback(1);
                }
                else
                {
                    currentData2.Feedback(0);
                }
                SummaryCard2.cardData(currentData2);
            }
            else if (actionId == "FeedbackDislike")
            {
                if (currentData2.Feedback() != -1)
                {
                    currentData2.Feedback(-1);
                }
                else
                {
                    currentData2.Feedback(0);
                }
                SummaryCard2.cardData(currentData2);
            }
            else if (actionId == "RefreshCard")
            {
                currentData2.cardTitle('Customer Profile');
                currentData2.custName('Contoso Electronics');
                currentData2.profileImage('https://media.licdn.com/dms/image/C560BAQFJq1MdKASLWA/company-logo_200_200/0/1591822700485?e=2147483647&v=beta&t=BrJUkBS5fE2EO3x5XsiiakRIDzN5GXqzPV6U1oEHOc8');
                currentData2.createdUtc('2017-02-14T06:08:39Z');
                currentData2.custDescription('Contoso Electronics is a mid-sized IT service provider specializing in network infrastructure, cybersecurity, and cloud migration for small-to-medium businesses.');
                currentData2.custInsightsTitle('Customer Insights');
                currentData2.custInsights('- Needs streamlined tools for remote network monitoring and incident response.\n- Anticipating 20% growth with plans for new hires in cybersecurity and cloud engineering\n- Current outstanding balance: $35,000\n- Payment history: Generally prompt but had delayed payments twice in the past year due to cash flow adjustments during expansion phases.');
                SummaryCard2.cardData(currentData2);
            }
        }
    }
}

```
