---
title: Extensible control programming reference
description: This article provides reference content for extensible control programming.
author: jasongre
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0a774c73-9e5d-4faa-8716-61476c1a9b6e
---

# Extensible control programming reference

[!include [banner](../includes/banner.md)]

This article provides reference content for extensible control programming.

This document describes the API, HTML, and JavaScript support for creating extensible controls.

## Examples
This document contains small code snippets that show how to use each API that is documented. More complete examples of finished controls that leverage many of these APIs can be found on Github. [Extensible Control Examples on Github](https://github.com/Microsoft/Dynamics-AX-Extensible-Control-Samples)

## Control block diagram
This high-level diagram illustrates the key components of an extensible control and how they interact with each other. Your extensible control solution will contain two X++ classes that implement your control. The runtime class implements the runtime data, presentation, and behavior of your control. The build class defines how your control is displayed in Form Designer, Property Window, and Application Explorer. [![Extensibility architecture.](./media/extensibilityarchitecture.png)](./media/extensibilityarchitecture.png)

## X++

The X++ API of your control is the Form-developer-facing API. Be sure to consider the APIs and behaviors you want to provide to the Form developer when designing the X++ APIs for your control.

## Runtime: The X++ runtime class
The runtime class defines the public, developer-facing API for your control. It also contains the runtime logic for your control. The job of the runtime class is to maintain the state of the control via the control’s properties.

## Runtime: Class declaration
Declare an X++ class that extends <strong>FormTemplateControl</strong> or a type derived from <strong>FormTemplateControl</strong><em>. ***FormTemplateControl</em>* contains basic properties that are necessary for every control, such as the Template ID and the Resource Bundle. The following example extends the base control class, <strong>FormTemplateControl</strong>.

```xpp
class MyControl extends FormTemplateControl
```

## Runtime: FormControlAttribute
You must apply the **FormControlAttribute** attribute to the X++ class declaration.

```xpp
[FormControlAttribute(<Template ID>, <Resource Bundle Path>, <Build class name>))]
```

You must supply the following arguments:

-   **Template ID**: A string that specifies the ID of the template. The Template ID is the JavaScript class name & the HTML element ID of the control. By convention, the TemplateID matches the class name of the control's runtime class.
-   **Resource Bundle Path**: A string that specifies the path to the resource bundle. The Resource Bundle Path is the web path where the main HTM files are located. At runtime, the Client framework will load the HTM file specified by the Resource Bundle Path. At runtime, the Client framework will search the Resource Bundle for the HTML element with an ID matching the specified Template ID. At runtime, the Client framework will instantiate the JavaScript class specified by the Template ID. This path is relative to the root of the web directory.
-   **Build class name**: A string that specifies the name of the build class. The build class name is the X++ class that determines the design-time behavior. At design time, the Visual Studio framework reflects over this attribute and loads the specified X++ class as the designer class. At runtime, the X++ framework will instantiate the specified X++ class as the build class in the super of applyBuild().

The following example shows a typical class and attribute declaration for a control named "MyControl".

```xpp
[FormControlAttribute('MyControl', '/resources/html/MyControl', classStr(MyControlBuild))]
class MyControl extends FormTemplateControl
```

## Runtime: FormCommandAttribute
The **FormCommandAttribute** is applied to a method in your control class, which allows the method to be called from a control’s JavaScript class. A method with this attribute applied is called a **command.** Use the **FormCommandAttribute** on only the X++ methods that need to be accessed directly from the control’s JavaScript class. An X++ method serving as a command can only accept string arguments. The method must perform the necessary operations to serialize or deserialize the string arguments into other types. The **FormCommandAttribute** has no effect on the behavior of the X++ method when the method is used from within X++. The **FormCommandAttribute** exposes the X++ method as an external endpoint that is accessible from JavaScript. As such, every command should be threat modeled and tested for exploits, and should perform validation on all of its arguments. The underlying X++ method should be declared private so that it is not accessible from X++. If X++ code needs to access this method’s behavior, then a separate X++ method should be declared as public without the **FormCommandAttribute.** This public method should contain any shared code that is needed by both X++ and JavaScript. The private X++ method with the **FormCommandAttribute** can then call this public method to access the shared code. This practice allows the command to perform logic that is specific to calls coming from JavaScript (such as argument type deserialization, argument validation, security validation, etc.) before executing the core shared X++ logic. You supply the following arguments to the **FormCommandAttribute** constructor:

-   **Name**: A required string that specifies the name of the command. A few best practices for naming Properties:
    -   Capitalize the first letter, and use PascalCase.
    -   Use a verb in the name.
    -   Include the Property name if the Command is used to read/write a FormProperty (ex: Set\_&lt;PropertyName&gt;)
    -   Do not use any of the names of inherited JavaScript properties.
-   **Execute immediate**: An optional boolean that specifies whether calls to this command are deferred or require immediate execution. By default, commands have **Execute immediate** set to **true,** so calls are not deferred. Most commands likely require immediate execution because their X++ logic must run before allowing the user to complete their next action. However, commands that have no side-effects on the user’s ability to take their next action can likely be safely deferred to gain a performance benefit. For commands that can be deferred, set Execute immediate to **false** to reduce network chattiness.

The following example declares a command with the name of "SetText".

```xpp
[FormCommandAttribute("SetText")]
private void setText(str value)
{
    // Add implementation code here.
}
```

## Runtime: FormPropertyAttribute
The **FormPropertyAttribute** is applied to a method in your control class, which allows an X++ method to be called as a **FormProperty** getter/setter from the control's JavaScript class. A method with this attribute applied is called a **property.** Only use the **FormPropertyAttribute** on those X++ methods which need to be accessed directly from the control’s JavaScript class. The **FormPropertyAttribute** has no effect on the behavior of the X++ method when the method is used from within X++. Every property exposes an endpoint to the browser. As such, every property should be threat modeled and tested for exploits. The underlying X++ method should be declared private so that it is not accessible from other X++ code. If other X++ code needs to access the property, then declare a separate public X++ method without the **FormPropertyAttibute,** and move the shared property logic to this method. Then call this method from the private X++ method with the **FormPropertyAttribute. This practice allows the property to perform logic that is specific to calls coming from JavaScript (such as argument type deserialization, argument validation, security validation, etc.) before executing the core shared X++ logic.** The underlying X++ method must accept and return the desired type of the property. If the desired type if an EDT, the property must accept and return the base type of the EDT. The supported property types are:

-   [X++ primitive types](/dynamicsax-2012/developer/primitive-data-types)
-   [X++ data contracts](/dotnet/api/system.runtime.serialization.datacontractattribute) (whose members are also supported types)
-   [X++ List](/previous-versions/dynamics/ax-2012/system-classes/gg921795(v=ax.60)) (whose items are also supported types)

You supply the following arguments to the **FormPropertyAttribute** constructor:

-   **FormPropertyKind:** A required **FormProperyKind** value that specifies the type of the property. Use **FormPropertyKind::Value** for Properties not bound to a data source field, and use **FormPropertyKind::BindableValue** for properties that may be bound to a data source field.
-   **Name:** A required string that specifies the name of the property. A few best practices for naming properties:
    -   Capitalize the first letter, and use PascalCase.
    -   Do not use any of the names of inherited JavaScript properties
-   **Read only**: An optional boolean that specifies whether this property is writable from the control’s JavaScript class. By default, properties have **Read only** set to **false,** so they are writeable. This argument does not affect the ability to write to this property from X++. To make the X++ method read only, remove all method arguments from the method declaration. A majority of properties should not be writable from the control’s JavaScript class. Because most property values require validation, a command should be used as a setter for the property so that validation logic is can be run before the backing property is set.
-   **Execute immediate**: An optional Boolean that specifies whether writes to this property are deferred or require immediate execution. By default, properties have **Execute immediate** set to **false,** so writes are deferred. Because the majority of properties should not be writeable form the control’s JavaScript class, the **Execute immediate** flag defaults to **false** and provides performance benefits. Even in the case of properties that are writable from the control’s JavaScript class, the performance side effects of immediate execution should be carefully considered before enabling the behavior.

The following example shows a typical property declaration. Most properties share the same boilerplate code for getting/setting, as shown below. The textProperty variable is the backing FormProperty field for this property.

```xpp
[FormPropertyAttribute(FormPropertyKind::Value, "Text", true)
private str parmText(str _value = textProperty.parmValue())
{
    if(!prmIsDefault(_value))
    {
        textProperty.setValueOrBinding(_value);
    }
    return textProperty.parmValue();
}
```

## Runtime: FormProperty
##### Behavior

**FormProperty** is an X++ [derived type](/previous-versions/visualstudio/visual-studio-2010/esd9wew8(v=vs.100)) used by the control framework for the synchronization of property values between X++ and JavaScript. **FormProperty** objects are considered the backing fields used internally by properties. Each **FormProperty** is typically used in 4 places throughout a control’s X++ runtime class:

1.  The **FormProperty** is declared, usually right below the class declaration
2.  The **FormProperty** is instantiated in the **new** method of the class
3.  The **FormProperty** is initialized in the **applyBuild** method of the class
4.  The **FormProperty** is read and written in the X++ method for the property

The following example shows a **FormProperty** being used in a typical controls’ X++ runtime class.

```xpp
[FormControlAttribute("MyControl", "/resources/html/MyControl", classStr(BuildMyControl))]
class MyControl extends FormTemplateControl
{             
    FormProperty textProperty;          

    public void new(FormBuildControl _build, FormRun _formRun)
    {
        super(_build, _formRun);
        
        this.setTemplateId("MyControl");
        this.setResourceBundleName("/resources/html/MyControl");
        textProperty = this.addProperty(
        methodStr(MyControl, parmText), Types::String);
    }

    public void applyBuild()
    {
        BuildMyControl build;
        
        super();

        build = this.build();
        if(build)
        {
            this.parmText(build.Text());
        }
    }

    [FormPropertyAttribute(FormPropertyKind::Value, "Text", true)
    private str parmText(str _value = textProperty.parmValue())
    {
        if(!prmIsDefault(_value))
        {
            textProperty.setValueOrBinding(_value);
        }
        return textProperty.parmValue();
    }
}
```

## Runtime: new method
The **new** method on a control’s X++ runtime class is called as a part of instantiating the control on a form. For the details on when the **new** method is called in the form lifecycle, please see the Control Lifecycle Diagrams. This method is used for instantiation of a control’s FormProperties and setting the control’s Template ID and Resource Bundle Path. See typical use of the **new** method in the example for FormProperty.

## Runtime: applyBuild method
The **applyBuild** method on a control’s X++ runtime class is called as a part of instantiating the control on a form. For the details on when the **applyBuild** method is called in the form lifecycle, please see the Control Lifecycle Diagrams. This method is used for initialization of a control’s FormProperties to their default values, or to the values specified by the form developer who placed the control on the form. See typical use of the **applyBuild **method in the example for FormProperty.

## Runtime: FormBindingUtil::initbinding method
The **FormBindingUtil** is an API provided by the control framework. It is used to bind FormProperties to data fields and data methods on a data source. The following example binds the data field with name "Value" on the data source with name "DataSource1" to the textProperty FormProperty of the runtime class.

```xpp
[FormControlAttribute("MyControl", "/resources/html/MyControl", classStr(BuildMyControl))]
class MyControl extends FormTemplateControl
{
    FormProperty textProperty;

    public void new(FormBuildControl _build, FormRun _formRun)
    {
        super(_build, _formRun);
        this.setTemplateId("MyControl");
        this.setResourceBundleName("/resources/html/MyControl");
        textProperty = this.addProperty(
        methodStr(MyControl, parmText), Types::String);
    }

    public void applyBuild()
    {
        BuildMyControl build;
            
        super();
           
        build = this.build();
        if(build)
        {
            this.parmText(FormBindingUtil::initBinding(
            "DataSource1", "Value", this.formRun()));
        }
    }

    [FormPropertyAttribute(FormPropertyKind::Value, "Text", true)
    private str parmText(str _value = textProperty.parmValue())
    {
        if(!prmIsDefault(_value))
        {
            textProperty.setValueOrBinding(_value);
        }
        return textProperty.parmValue();
    }
}
```

## Design time: The X++ build class
The build class defines the design time behavior of your control. This class determines which properties appear in the property sheet, and how the control behaves when it is modeled in the Form designer. The job of the design time class is to capture design time information for the runtime class to access later on.

## Design time: Class declaration & FormDesignControlAttribute
The FormDesignControlAttribute is necessary for the control to appear in the Visual Studio Form designer when right-clicking on the design node of the form. If the FromDesignControlAttribute is missing, then the control can only be added to a form via imperative X++ code (i.e. via the addControlEx method on the form).

```xpp
[FormDesignControlAttribute("MyControl")]
class MyControlBuild extends FormBuildControl
{

}
```

## Design time: FormDesignPropertyAttribute
Placing this attribute on a method in the design time class will result in a new property with the name specified by the first argument (and in the section specified by the second argument) appearing the property sheet for this control, with the corresponding X++ method operating as the getter/setter for the property.

```xpp
[FormDesignControlAttribute("MyControl")]
class MyControlBuild extends FormBuildControl
{
    str text; 

    [FormDesignPropertyAttribute("Text", "Data")]
    public str Text(str _value = text)
    {
        if(!prmIsDefault(_value))
        {
            text = _value;
        }
        return text;
    }
}
```

## Design time: FormDesignProperty** **Attribute
There are a number of FormDesignProperty attributes which may be applied alongside the standard FormDesignPropertyAttribute for specialized behavior in the property sheet. The specialized behavior includes enabling the property as a combobox which allows selecting from a list of a values. The different types of lists that used are enumerated below. Whenever the user selects an item from the combobox, the string name of that item is passed into the X++ method getter/setter with the attribute.

-   \[FormDesignPropertyDataSourceAttribute\] - Shows a list of the data sources on the form.
-   \[FormDesignPropertyDataFieldAttribute(&lt;data source name&gt;)\] - Shows a list of the data fields on the specified data source.
-   \[FormDesignPropertyDataMethodAttribute(&lt;data source name&gt;)\] - Shows a list of the data methods on the specified data source.
-   \[FormDesignPropertyFieldGroupAttribute(&lt;data source name&gt;)\] - Shows a list of the field groups on the specified data source.
-   \[FormDesignPropertyExtendsClassAttribute(&lt;class name&gt;)\] - Shows a list of the classes which extend the specified class.
-   \[FormDesignPropertyImplementsAttribute(&lt;interface name&gt;)\] - Shows a list of the classes which implement the specified interface.
-   \[FormDesignPropertyReferenceAttribute(&lt;FormDesignPropertyReferenceType::&lt;type&gt;)\] - Shows a list of the specified AOT artifacts with the given type. The supported types are:
    -   Table
    -   View
    -   Map
    -   EDT
    -   BaseEnum
    -   Query
    -   Class
    -   Form
    -   MenuItemDisplay
    -   MenuItemOuput
    -   MenuItemAction
    -   Tile
    -   KPI

The following example shows standard properties used to allow a Form developer to specify the Data Source and Data Field for the design time class.

```xpp
[FormDesignControlAttribute("MyControl")]
class MyControlBuild extends FormBuildControl
{
    str dataSource; 
    str dataField;
    str dataMethod;

    [FormDesignPropertyAttribute("Data source", "Data"),
     FormDesignPropertyDataSourceAttribute]
    public str DataSource(str _value = dataSource)
    {
        if(!prmIsDefault(_value))
        {
            dataSource = _value;
        }
        return dataSource;
    }

    [FormDesignPropertyAttribute("Data Field", "Data"),
     FormDesignPropertyDataFieldAttribute(methodStr(MyControlBuild, DataSource))]
    public str DataField(str _value = dataField)
    {
        if(!prmIsDefault(dataField))
        {
            dataField = _value;
        }
        return dataField;
    }

    [FormDesignPropertyAttribute("Data Method", "Data"),
     FormDesignPropertyDataMethodAttribute(methodStr(MyControlBuild, DataSource))]
    public str DataMethod(str _value = dataMethod)
    {
        if(!prmIsDefault(dataMethod))
        {
            dataMethod = _value;
        }
        return dataMethod;
    }
}
```

A control with a design time class like the one above can then bind to the specified data source and data field inside of the applyBuild method, as show below.

```xpp
public void applyBuild()
{
    BuildMyControl build;

    super();

    build = this.build();
    if(build)
    {
        this.parmText(FormBindingUtil::initBinding(
        build.DataSource(), build.DataField(), this.formRun(), build.DataMethod()));
    }
}
```

If you supply both a data field and data method to FormBindingUtil::initBinding, the data field binding will override the data method binding.

## HTML
## HTML: Framework attributes

The following section documents the HTML attributes that are used in the control framework for control development.

### data-dyn-bind

**data-dyn-bind**, the data binding attribute, standardizes many common DOM manipulations - such as modifying an element’s attributes, properties and CSS, or handling DOM events - through a declarative HTML-based API. The data binding attribute allows for these behaviors without requiring complex JavaScript. Using the data binding attribute rather than writing complex JavaScript can save the control developer valuable time by making things such as designing, debugging and maintaining the control much easier. However, complex JavaScript is still available when scenarios require its use. The data binding attribute binds HTML element behaviors to values supplied by the control developer. The values supplied can be simple JavaScript [variables](https://www.w3schools.com/js/js_variables.asp), JavaScript [comparison](https://www.w3schools.com/js/js_comparisons.asp) or [arithmetic](https://www.w3schools.com/js/js_arithmetic.asp) expressions, JavaScript [functions](https://www.w3schools.com/js/js_functions.asp) and JSON [objects](https://www.w3schools.com/js/js_json_objects.asp). The values supplied can also be observable variables, created using the APIs described in this document. The way in which the supplied value is bound to the HTML element is determined by the binding handler that is used with the data binding attribute. A list of all supported binding handlers is provided in this document. The data binding attribute requires the following syntax when used with any binding handler. The syntax for **data-dyn-bind** is:

```xpp
data-dyn-bind="[first binding handler]: [value to bind to]"
```

The data binding attribute accepts a comma-separated list of binding handler-value pairs, so you can supply more than one binding handler to the binding attribute at a time. The following example binds the **visible** property of the div element to true, and binds the **textContent** property of the div element to "Hi".

```xpp
data-dyn-bind="text: 'Hi', visible: true"
```

The data binding attribute is a custom HTML attribute understood by the control framework. The data binding attribute can be applied to any HTML element. Some HTML elements may not have the behavior which the binding handler modifies. For example, using the text binding handler on an **&lt;svg&gt;** element will not show the text since the **&lt;svg&gt;** element does not have a textContent property. The control framework reads and executes the data bindings specified in the control’s template at runtime. The lifecycle for the control in the browser can be summarized as follows:

1.  The control’s HTM file is loaded by the browser.
2.  Any script or resource files referenced in the HTM file are also loaded by the browser. Steps 1 and 2 are executed only once during a user’s session, even if there are multiple instances of the control.
3.  The JavaScript class's constructor for the control is call and passed with the X++ properties for the control instance.
4.  The control’s template is copied from the HTM file and into the browser’s memory.
5.  HTML elements in the control’s template are processed for data binding in hierarchical order (depth first), and data bindings on each element are executed in order from left-to-right
6.  The final HTML, including the original data binding attributes as well as any other markup added by the binding handlers or by the framework, is added to the browser’s DOM and rendered for the user to see.
7.  Later, when the value of an observable changes, any binding handlers subscribed to the observable are re-executed and the live DOM is updated in real-time.

## HTML: Binding handlers
### attr

The **attr** binding handler applies the supplied HTML attribute and value to the element. For a list of HTML attributes see [W3 Schools – HTML Attributes](https://www.w3schools.com/html/html_attributes.asp). The arguments are passed in as an object array. Each argument is dual-valued. The first value is the name of the attribute, and the second value is the value of the attribute.

-   **Name**: a string that specifies the desired name of the attribute to create.
-   **Value or Expression:** a string that specifies the value to set on the attribute. If an expression is supplied, the value returned by evaluating the expression will be used.

The following example creates the title and name attributes and sets their value.

```xpp
<!-- the markup in the HTML template -->
<div data-dyn-bind="attr: {title: 'Hello', name: 'Greeting'}"></div>

<!-- the markup in the browser after the binding handler is applied -->
<div title="Hello" data-dyn-bind="attr: {title: 'Hello', name: 'Greeting'}" name="Greeting"></div>
```

The following example uses expressions and functions. However, using JavaScript functions as in-line HTML like the example below is not recommended.

```xpp
<!-- the markup in the HTML template -->
<div data-dyn-bind="attr: {title: false? 'Hello':'World', name: function(){return 'Greetings';}()}"></div>

<!-- the markup in the browser after the binding handler is applied -->
<div title="World" data-dyn-bind="attr: {title: false? 'Hello':'World', name: function(){return 'Greetings';}()}" name="Greetings"></div>
```

#### click

##### Behavior

Subscribes the supplied function to the click event on the element. For more information on subscribing to the click event see [jQuery – click()](https://api.jquery.com/click/).

##### Arguments

###### EventHandler (function)

The function to call when the event is raised.

##### Example 1

The following example shows an alert message “Hello” when the element is clicked.

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.ElementClicked = function (event) {
    /* handle the click event */
    alert('Hello');
};
...
</script>

<!-- In your control’s template HTM file -->
<div data-dyn-bind="click: $control.ElementClicked"></div>
```

The following example prevents the click event on child elements from bubbling up to parent elements. The example below will show only one alert with message “Hello” when the child element is clicked.

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.ParentElementClicked = function (event) {
    /* handle the click event */
    alert('Hi');
};

self.ElementClicked = function (event) {
    /* prevents the event form bubbling up to parent elements*/
    event.stopPropagation();

    /* handle the click event */
    alert('Hello');
};

...
</script>

<!-- In your control’s template HTM file -->
<div data-dyn-bind="click: $control.ParentElementClicked">
<div data-dyn-bind="click: $control.ElementClicked"></div>
</div>
```

The following example prevents the browser default behavior from executing. For anchor tags, the default hyperlink behavior is prevented, so the browser will not navigate to the link when the element is clicked.

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.LinkClicked = function (event) {
        /* handle the click event */
        alert($dyn.format('Navigation to ' + {0} + ' was prevented', $(event.target).attr("href")));

        /* prevents the default event behavior */
        event.preventDefault();
};
</script>

<!-- In your control’s template HTM file -->
<a href="https://www.microsoft.com" data-dyn-bind="click: $control.LinkClicked">Click here</a>
```

#### css

##### Behavior

Adds or removes the specified CSS class name(s) to the element, based on the specified condition(s). Note that expressions supplied to the binding handler are only executed once.

##### Arguments

The arguments are passed in as an object array. Each argument is dual-valued. The first value is the Class name, and the second value is the Condition.

###### Class name (string)

The CSS class name to add to the element.

###### Condition (expression)

The condition on which to add the CSS class name. If the condition evaluates to true, the CSS class name is added. If the condition evaluates to false, the CSS class name is removed. If a supplied condition takes a dependency on an observable (via $dyn.value), then the condition will be re-evaluated whenever the observable value changes, and the associated CSS class name will be added/removed based on the new condition. The following example adds the CSS class names "red", "green", and "yellow".

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.red = function () { return true; };
self.yellow = $dyn.observable(true);
...
</script>

<!-- the markup in the HTML template -->
<div data-dyn-bind="css: {green: true, red: $control.red, yellow: $dyn.value($control.yellow)}"></div>

<!-- the markup in the browser after the binding handler is applied -->
<div class="green red yellow" data-dyn-bind="css: {green: true, red: $data.red, yellow: $dyn.value($control.yellow) }"></div>
```

#### event

##### Behavior

Subscribes the supplied event handler to the specified DOM event. For a list of supported DOM events, see [jQuery - Event](https://api.jquery.com/Types/#Event).

##### Arguments

For details on the arguments to the event binding handler, see [jQuery - .bind()](https://api.jquery.com/bind/). The following example subscribes to the mouseover event and shows an alert when the element is hovered.

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.elementHovered = function (event) { alert($dyn.format('{0}',$(event.target).text()))};
...
</script>

<!-- the markup in the HTML template -->
<div data-dyn-bind="event: {mouseover: $data.elementHovered}">Greetings!</div>
```

#### foreach

##### Behavior

Repeats the content of the child element, updating the binding context of each child based on the supplied data. Supply ***only one*** child element inside of the element with the **foreach** binding. This one element is the element that will be cloned and repeated. Any other additional elements or content will be removed when the binding is applied. Binding handlers are executed in the order in which they appear on the element. Since the **foreach** binding changes the binding context, it is a best practice to always place the **foreach** binding after all other bindings on the element. This will ensure that preceding bindings are not affected by the binding context created by the **foreach** binding. To avoid performance issues, be careful to not create unintentional dependencies on observables inside of your **foreach.** Do not access an observable in the array using **$dyn.value** from within the child elements of the **foreach,** as the **foreach** binding has already subscribed to the observables in the array. Instead, use **$dyn.peek** to access an observable’s value once without creating a subscription.

##### Arguments

###### Data (array list or JSON object)

The list of items to bind the child element to. If an array list is supplied, the binding context is an item in the array. If a JSON object array is supplied, the binding context is one of the object’s properties.

##### Scope variables

When inside the scope of the **foreach,** the following scope variables are useful and can be used on the repeatable child element: $data, index, control, your own scope variables. The following example uses **foreach** to render a span element for each color in the array.

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.colors = ['Red','Blue','Green'];
...
</script>

<!-- the markup in the HTML template -->
<div data-dyn-bind="foreach: $control.Colors">
<span data-dyn-bind="text: $data"></span>
</div>

<!-- the markup in the browser after the binding handler is applied -->
<div data-dyn-bind="foreach: $control.colors">
<span data-dyn-bind="text: $data">Red</span>
<span data-dyn-bind="text: $data">Blue</span>
<span data-dyn-bind="text: $data">Green</span>
</div>
```

The following examples shows a nested **foreach** binding. This example showcases how to use the index framework scope variable and custom scope variables to access the binding context from the parent element.

```xpp
    // In your control’s code-behind JS file
<script>
... // boilerplate code
self.colors = [
    {
        Name: 'Red',
        Variants: ['Maroon','Burgundy','Sunrise']
    },
    {
        Name: 'Green',
        Variants: ['Sage','Forest','Lime']
    },
    {
        Name: 'Blue',
        Variants: ['Navy','Sky','Ice']
    }
];
...
</script>
<!-- the markup in the HTML template -->
<div data-dyn-bind="foreach: $control.colors">
<div data-dyn-bind="vars: {$BaseIndex: $index, $BaseColor: $data.Name}">
<div data-dyn-bind="foreach: $data.Variants">
<div data-dyn-bind="text: $BaseIndex+'.'+$index+' '+$data+' '+$BaseColor"></div>
</div>
</div>
</div>
<!-- the markup in the browser after the binding handler is applied -->
<div data-dyn-bind="foreach...">
<div data-dyn-bind="vars...">
<div data-dyn-bind="foreach...">
<div data-dyn-bind="vars...foreach...">
<div data-dyn-bind="text...">1.1 (0.2552) X++ Language</div>
<div data-dyn-bind="text...">1.2 (0.7) Applications</div>
</div>
</div>
<div data-dyn-bind="vars...">
<div data-dyn-bind="text...">2. (600) Technology</div>
<div data-dyn-bind="vars... foreach...">
<div data-dyn-bind="text...">2.1 (600.343) Microsoft Corporation</div>
<div data-dyn-bind="text...">2.2 (600.117) Enterprise Resource Planning</div>
</div>
</div>
</div>
```

#### if

##### Behavior

Conditionally renders and binds the child elements of the element with this binding. This binding handler only operates on the child elements. It will not show/hide the element with the binding, nor will this binding show/hide the text content of the element with the binding. Bindings on the child elements will only be executed if the condition evaluates to true. Once the bindings on child elements have been evaluated once they will remain data bound even if the condition changes to false. This means that any calculations caused by bindings on child elements will continue to operate even after the child elements are hidden. Consider this when evaluating the performance of your control.

##### Arguments

###### Condition (expression)

Determines whether to render the children elements. The following example conditionally binds the **show** and **text** elements.

```xpp
    // In your control’s code-behind JS file
<script>
... // boilerplate code
self.show = $dyn.observable(false);
self.text = "Hello";
...
</script>
<!-- the markup in the HTML template -->
<div data-dyn-bind="if: $control.show">
<div data-dyn-bind="text: $control.text"></div>
</div>
<!-- the markup in the browser after the binding handler is applied -->
<div data-dyn-bind="if: $control.show">
</div>
// Later on, the value of the “show” observable changes to true
<script>
...
self.show(true);
...
</script>
<!-- the markup in the browser after the binding handler is re-applied due to the observable value changing -->
<div data-dyn-bind="if: $control.show">
<div data-dyn-bind="text: $control.text">Hello</div>
</div>
```

#### sizing

##### Behavior

Specifies the height and width of the control. The sizing binding handler should always be applied to the root element of the template (the element that has the id attribute), and supplied the height and width values from the X++ instance of the control by using the $dyn.layout.sizing helper function. See Example 1.

##### Arguments

The arguments are passed an object containing height and width properties.

###### Height (int)

Determines the height in pixels of the element on which the binding handler is applied.

###### Width (int)

Determines the width in pixels of the element on which the binding handler is applied. The following example specifies the size of **MyControl.**

```xpp
<!-- the markup in the HTML template -->
<!-- this boilerplate binding ensures that the control’s container is sized based on the height and width properties -->
<div id="MyControl" data-dyn-bind="sizing: $dyn.layout.sizing($control)"></div>
<!-- the markup in browser after the binding handler is applied will vary based on the height and width properties defined in $control -->
```

The following example makes the control large or small depending on the value of the **bigbox** variable.

```xpp
// Later on, the value of the “show” observable changes to true
<script>
...
self.bigBox = true;
...
</script>
<!-- the markup in the HTML template -->
<div data-dyn-bind="sizing: {height: $control.bigBox?50:10, width: $control.bigBox?50:10}"></div>
<!-- the markup in the browser after the binding handler is applied -->
<div style="width: 50px; height: 50px;" data-dyn-bind="sizing: {height: $control.bigBox?50:10, width: $control.bigBox?50:10}"></div>
```

#### text

##### Behavior

Binds to the textContent property of the element. The text binding handler is meant to be used with UI text. It is not meant to bind non-string values (such as numbers, dates or Booleans) to the element. Convert all values into strings before supplying them to the binding handler, by using the dyn.format function. The text binding handler will replace all of the content inside of the element with the binding, whether or not the existing content is HTML or simple text.

##### Arguments

###### Text (string)

The text to bind to. The following example binds the textContext property of the div element to the text property on the control.

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.text = "Hello";
...
</script>
<!-- the markup in the HTML template -->
<div data-dyn-bind="text: $dyn.format('{0}',$control.text)"></div>
<!-- the markup in browser after the binding handler is applied -->
<div data-dyn-bind="text: $dyn.format('{0}',$control.text)">Hello</div>
```

#### vars

##### Behavior

Creates an HTML scope variable with the supplied name and value. The created scope variable is accessible only from bindings in the template. In addition, the scope variable is inherited by child elements. Binding handlers are executed in the order in which they appear on the element. Since the vars binding adds variables to the binding context, it is a best practice to always place the vars binding before all other bindings on the element. This will ensure that the subsequent bindings can access scope variables added by the vars binding. Do not create scope variables with any of the following names, as these names are reserved for framework scope variables: $control, $data, $index, and $value.

##### Arguments

###### Scope variables (object array)

The object array whose keys are the scope variable names and whose values are the initial values for the scope variables. The following example creates scope variables named "Hello" and "World" and displays their values.

```xpp
<!-- the markup in the HTML template -->
<div data-dyn-bind="vars: {$myVar: 'Hello', $myObs: $dyn.observable('World')}">
<span data-dyn-bind="text: $dyn.format('{0} {1}!', $myVar, $myObs)">
</span>
</div>
<!-- the markup in browser after the binding handler is applied -->
<div data-dyn-bind="vars: {$myVar: 'Hello', $myObs: $dyn.observable('World')}">
<span data-dyn-bind="text: $dyn.format('{0} {1}!', $myVar, $myObs)">
Hello World!
</span>
</div>
```

##### Example 2

For an example, see the foreach binding handler examples.

#### visible

##### Behavior

Sets the visibility of the element. Always supply the visible binding handler on the root element of the template, and bind to the *Visible* property from the X++ control. This will ensure that the control respects the *Visible* property when it is set by a form developer or when it is set by the framework. If a control is initialized with its *Visible* X++ property set to false, then the control will not appear on the form, and it the control’s template will not be loaded in the browser. If the control’s *Visible* X++ property is set to true at a later time, then the control’s template will be loaded and instantiated in the browser at that time. A control’s *Visible* X++ property can be inherited from its parent controls on the form. An element’s visibility may be controlled by its parent elements, controls and containers, regardless of whether the visible binding handler is applied. The cascading nature of visibility is a standard HTML behavior and is not specific to the control framework.

##### Arguments

###### Visible (boolean)

Determines whether the element is visible or not. The following example sets the visibility of the control's outermost div element.

```xpp
// In your control’s code-behind JS file
<script>
... // boilerplate code
self.Visible(false); // set the X++ observable property to false
...
</script>
<!-- the markup on the root element of the HTML template -->
<div id="MyControl" data-dyn-bind="visible: $control.Visible">Hello World!</div>
<!-- the markup in browser after the binding handler is applied -->
<div id="MyControl" style="display: none;" data-dyn-bind="visible: $control.Visible">Hello World!</div>
```

## HTML: Scope variables
Scope variables can be used when binding values to binding handlers. Scope variables are only accessible from within the control’s HTML template, and can only be used with the data binding attribute. Scope variables are neither accessible from other HTML attributes nor from the control’s JavaScript class, but scope variables can be used in inline JavaScript expressions, functions and JSON objects that are passed to binding handlers.

#### $control

The *$control* scope variable provides the bindings in the HTML template with access to the properties and functions on the control’s JavaScript instance. The following example binds visibility of the div element to the of Visible property of the control.

```xpp
<div id="MyControl" data-dyn-bind="visible: $control.Visible"></div>
```

#### $data

The *$data* scope variable provides elements with access to their current binding context. Only variables defined in $data (the binding context) or scope variables, can be used inside of HTML bindings. Variables that do not exist in the current binding context and do not exist as current scope variable cannot be accessed from an HTML binding. In most cases the binding context will be the control’s JavaScript instance, so *$data* and *$control* will be equivalent. However, in some cases the binding context can change. For example, for elements inside of a **foreach** binding, *$data* provides the elements with access to the current array item. In cases involving multiple nested **foreach** bindings, elements in a nested binding may need access to the array item in a parent **foreach** binding. To access items in the parent **foreach** binding, you may create a scope variable which will be accessible to elements in the nested **foreach** biding. For an example, see the foreach binding handler examples.

#### $index

The $index scope variable provides a 0-based index of the array item when in a **foreach** binding. For an example, see the foreach binding handler examples.

## JavaScript: Inherited properties
#### Visible

The **Visible** property is inherited from the base JavaScript class (via **$dyn.ui.Controls.apply**). There is also a **Visible** property in X++ that the runtime class in inherits from the base **FormControl** X++ class. Simply bind this property to the visible binding handler and place it on the root element of the HTML template for your control. The framework takes care of the rest. The following example shows how to use the Visible property.

```xpp
<!-- the markup in the HTML template -->
<div id="MyControl" data-dyn-bind="visible: $control.Visible"></div>
```

## Observable framework
#### $dyn.observe

##### Usage

Subscribes a function to changes of an observable. We recommend that you use dispose.

```xpp
$dyn.observe(observable, observer, [context], [disposableObserver])
```

##### Arguments

###### Observable (observable)

Instance of an observable. Or a function, which will become a $dyn.computed.

###### Observer (function)

Function is invoked upon registration and also later when the observable is updated. Function is invoked with one argument, the value of the observable. If Observer returns false, then we un-subscribed automatically.

###### Context (options, optional)

Context to pass to the Observer. The Context becomes the ***this*** variable inside of the observer.

###### DisposableObserver (options, optional)

Unsubscribes the supplied DisposableObserver

##### Returns

###### Subscription (object)

Observable, ID, Dispose function (public) used to unsubscribe The following example subscribes to the myObs observable, and executes the supplied function whenever the myObs observable value changes.

```xpp
$dyn.observe(myObs, function (value) { console.log(value);});
```

The following example shows how a function can automatically subscribe to observables simply by accessing the observable using $dyn.value. The first function is treated like an observable whose value is dependent upon the value of two other observables (FirstName and LastName). Every time one of the observables  (FirstName or LastName) changes its value, then the first function has also changed its value. When this happens, the second function (the callback function) will log the concatenation of the observable values to the console.

```xpp
self.FirstName = $dyn.observable("Joanne");
self.LastName = $dyn.observable("Gordon");
$dyn.observe(
    function () {
        // Joann + " " + Gordon
        return $dyn.value(self.FirstName) + " " + $dyn.value(self.LastName);
    },
    function (value) {
        // "Joanne Gordon"
        console.log(value);
    }
);
```

The following example performs similarly to the previous example. However, this example uses a computed observable, named myComp, to handle the concatenation.

```xpp
self.FirstName = $dyn.observable("Joanne");
self.LastName = $dyn.observable("Gordon");
self.myComp = $dyn.computed(function () {
    // Joanne + " " + Gordon
    return $dyn.value(self.FirstName) + " " + $dyn.value(self.LastName);
});
$dyn.observe(
    self.myComp,
    function (value) {
        // "Joanne Gordon"
        console.log(value)
    );
},
{FirstNameLabel: label1, LastNameLabel: label2}
);
```

#### $dyn.observable

##### Usage

Creates an observable variable.

```xpp
$dyn.observable([initial value])
```

##### Arguments

###### Initial value (optional)

The value to initialize the observable to.

##### Returns

###### Observable (function)

The newly created observable The following example creates and observable variable named "Hello".

```xpp
var greeting = $dyn.observable("Hello");
```

#### $dyn.value

##### Usage

Accesses the value of an observable variable. When **$dyn.value** is called from inside of an observer function (such as an observer passed to **$dyn.observe** or **$dyn.computed**, as well as the binding expression passed to a binding handler) a dependency on the observable is created. This will cause the binding handler or callback to re-execute whenever the value of the observable changes. Because this dependency is created automatically when using **$dyn.value**, it is important to only use **$dyn.value** when you intentionally wish to create such a dependency. If you wish to access the value of an observable without creating a dependency, you should use $dyn.peek.

```xpp
$dyn.value(observable)
```

##### Arguments

###### Observable

The observable property whose value to access.

##### Returns

###### Value

The current value in the observable property The following example returns the value of variable named observable and prints it to the console.

```xpp
console.log($dyn.value(observable));
```

#### $dyn.peek

##### Usage

Accesses the value of an observable variable, without creating a dependency. For more information about dependency, see the $dyn.value function.

```xpp
$dyn.peek(observable)
```

##### Arguments

###### Observable

The observable whose value to access.

##### Returns

###### Value

The current value in the observable The following example returns the value of variable named observable and prints it to the console.

```xpp
console.log($dyn.peek(observable));
```

#### $dyn.computed

##### Usage

Wraps a function with an observability scope. If observables are accessed from inside of the function by using the **$dyn.value** function, then the function will re-execute whenever the values of those observables change. Observables that are accessed by using **$dyn.peek** will not cause the function to re-execute when their values change.

```xpp
$dyn.computed(observer, [context], [disposableObserver])
```

##### Arguments

###### Observer (function)

Function is invoked upon registration and can also be invoked later due to an observable value change. The Observer automatically observes any observables that are accessed using $dyn.value from within the scope of the function.

###### Context (options, optional)

Context to pass to the Observer. The Context becomes the *this* variable inside of the observer.

###### DisposableObserver (options, optional)

Unsubscribes the supplied DisposableObserver

##### Returns

###### Anything (optional)

If the Observer returns a value, then that value will also be returned by the call to **$dyn.computed** on the first time **$dyn.computed** is called (upon registration) as well every time the observer is invoked.

## Framework functions
#### $dyn.callFunction

##### Usage

Calls the apply method on specified function. It cannot be used during an interaction.

##### Arguments

###### Function (function or observable)

The function to call. If an observable is supplied, the current value of the observable will be retrieved and used as the function.

###### This (object, optional)

The object to assign to *this* within the scope of the function.

###### Arguments (array, optional)

The arguments to pass to the supplied function.

###### Callback (function, optional)

The callback function to call when the supplied function has returned. The callback will be passed any values that are returned by the function that is called. The following example calls the **apply** function on the **printName** function.

```xpp
self.Name = "Joanne M Gordon";
var printName = function () {
    console.log(this.Name);
};
$dyn.callFunction(printName, self);
```

The following example calls the **getWholeName** function.

```xpp
var getWholeName = function (first, middle, last) {
    var wholeName = first + " " + middle + " " + last;
    return wholeName;
};
var printName = function (wholeName) {
    console.log("Your name is: " + wholeName);
};
var firstName = "Joanne";
var middleName = "M";
var lastName = "Gordon";
$dyn.callFunction(getWholeName, null, [firstName , middleName, lastName], printName);
```

#### $dyn.format

##### Usage

Builds a string using the supplied values according to the supplied format.

##### Arguments

###### Format (string)

The format in which to build the string. Use bracket notation for placeholders.

###### Values (optional)

The comma separated values to use in the format

##### Returns

###### FormattedString (string)

The string after formatting has been applied The following example builds a string with the first, middle initial, and the last name.

##### Example 1

```xpp
var first = "Joanne";
var middle = "M";
var last = "Gordon";
var $dyn.format("Your name is : {0} {1} {2}", first, middle, last);
```

#### $dyn.label

##### Usage

Provides access to any labels stored via the Globalization API.

##### Arguments

###### Identifier (string)

The label ID, as specified to the Globalization API.

##### Returns

###### Value (string)

The label string in the current culture, if the Identifier is found. Otherwise, returns the supplied Identifier as a string. The following example returns and prints the label named "greeting".

```xpp
Globalize.addCultureInfo("en", {
    messages: {
        "greeting": "Hello!"
    },
});
console.log($dyn.label("greeting"));
```

## CSS

Add namespaces to all CSS class names by prepending the class name with the control’s template ID. This will prevent your control and its styles from conflicting with other controls in the client.

## Flexbox
For advanced layout scenarios we encourage using Flexbox. Flexbox is compatible with the Extensible Control framework. [Using CSS flexible boxes (Mozilla Developer Network)](https://developer.mozilla.org/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes) Please see the [public Flexbox documentation](https://developer.mozilla.org/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes) for explanations and examples of the following topics:

-   Responsive layouts
-   Building columns and rows
-   Arranging elements horizontally or vertically
-   Arranging nesting elements
-   Auto-sizing elements to stretch and shrink
-   Locking/Freezing elements
-   Building scrollable elements

## Control Lifecycle Diagrams

### Control Instantiation
[![Extensibility process.](./media/extensibilityprocess-951x1024.png)](./media/extensibilityprocess.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
