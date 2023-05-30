---
title: Write best practice rules
description: This article describes how you can author best practice rules in C#, for both metadata and X++ code.
author: pvillads
ms.date: 11/03/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: pvillads
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 4fe671c4-c556-4942-8570-307cf68ae0a7
---

# Write best practice rules

[!include [banner](../includes/banner.md)]

This article describes how you can author best practice rules in C#, for both metadata and X++ code. Best practice checks are run by the compiler. You can run them in daily builds to catch objectionable practices that are unacceptable in shipping code. The features can also be used to author simple one-of tools to gather information about the application.

You can also use best practice rules to author simple tools that gather information about your application. The framework is built on top of a managed framework called XLNT (shorthand for X++ LaNguage Toolkit). You can use the framework to build custom tools that extract information from, and modify, X++ code. There are two types of best practice rules: rules that deal with metadata and rules that deal with source code.

## Code Best Practice framework

The Code Best Practice Framework (CBPF) enables you to write your own tools for analyzing X++ source code. These rules diagnose things that you consider to be problems with X++ source code. This section describes the foundation of the Best Practice functionality. This information is helpful for understanding the later sections that describe creating your own rules in greater detail. It is also helpful to developers who want to code rules that are more complex than those demonstrated in this document. The CBPF API lets you focus on the rule you are expressing, without having to deal with infrastructure issues. You don't need to read tokens and piece them together to create something intelligible from them. Instead, the CBPF provides the following parts:

- A parser that builds an Abstract Syntax Tree (AST) from X++ source code.
- A pipeline that runs a sequence of passes over the X++ code.
- A number of prebuilt passes. The first pass is the parsing of the source code.
- Infrastructure to read metadata.

Because rules are based on ASTs, it is important to understand that concept before starting to write rules.

### The parser and ASTs

The parser reads  X++ code and produces an AST from it if it does not contain egregious syntax errors. The parser has a built-in error recovery scheme, so it can recover from most syntax errors reasonably well. When a syntax error happens, the parser will read symbols until it encounters a semicolon, and then try to building the AST by unstacking its state until it reaches a state where a semicolon is a correct symbol. In addition, the parser is able to suggest the correct set of symbols when a syntax error occurs. The parser is not intended to be directly interacted with by consumers of the API, but should be considered a black box that works without user intervention. As the parser recognizes the language constructs in the source code, it builds an AST. The AST consists of nodes that are abstractions of the X++ artifact they represent. We will illustrate the concept by showing a few AST nodes below:

```xpp
public abstract class Statement : Ast
{
    /// <summary>
    /// Gets or sets the comments in the statement
    /// </summary>
    public string Comments { get; set; }

    public abstract string ToString(int indent);
}
```

The **Statement** class is abstract, because it doesn't make sense to instantiate a ”statement”. Only concrete derived classes, like **if** and **while** statements, can be instantiated. Since the Comments property is placed on this base class, it applies to all derived classes. In other words, all statements can have comments preceding the statement. The comments are accessible through the given property. There are many different kinds of statement in X++ and each one is described by a class derived in one or more steps from the abstract **Statement** class shown above. The following example shows the definition of a **while** statement.

```xpp
public class WhileStatement : Statement
{
    /// <summary>
    /// Gets or sets the while condition.
    /// </summary>
    public Expression Condition { get; set; }

    /// <summary>
    /// Gets or sets the constituent while statement.
    /// </summary>
    public Statement Statement { get; set; }
}
```

The **while** statement consists of the condition (an expression) and the constituent statement, that is executed as long as the condition evaluates to true. The parser will maintain the source code positions where the represented artifact starts and ends (that is, its extent). As the ASTs are traversed, it may be useful to add information to the individual nodes. For example, every expression has a type. As the tree is traversed to diagnose type compatibility problems it becomes useful to be able to place that information on the individual node. Rather than having to modify the AST nodes for each requirement, there is a property collection that can be used to provide name/value pairs to each node. Each AST node has a **ToString** method that will return a high fidelity string representation of the node, which is useful in debugging scenarios.

### The AstSweeper class

The AstSweeper applies a visitor pattern to the AST instance that it is given. The visitor pattern allows the programmer to separate the underlying data structure (that is, the AST) from the operations that the user wants to perform on the nodes (that is, the logic reasoning about the code). The **AstSweeper** class has a virtual method for each of the AST node types, and it will call them as directed by the structure of the AST. The following examples show how the sweeper works. Some details have been omitted for clarity.

```xpp
/// <summary>The AST sweeper visits each node in the AST</summary>
/// <typeparm name="TReturn">The type returned by each of the sweeper methods</typeparm>
/// <typeparm name="TPayload">
/// The type of the payload passed to each of the sweeper methods
/// </typeparm>
public class AstSweeper<TReturn, TPayload> where TReturn : class
{
    protected virtual TReturn VisitStatement(TPayload o, Statement statement)
    {
        var compoundStatement = statement as CompoundStatement;
        if (compoundStatement != null)
        {
            return this.VisitCompoundStatement(o, compoundStatement);
        }

        var whileStatement = statement as WhileStatement;
        if (whileStatement != null)
        {
            return this.VisitWhileStatement(o, whileStatement);
        }
    }

    protected virtual TReturn VisitWhileStatement(TPayload o, WhileStatement statement)
    {
        this.VisitExpression(statement.Condition);
        this.VisitStatement(statement.Statement);

        return null;
    }
}
```

The name of the virtual method handling a particular AST node is the name of the AST class prepended with Visit. The parameters are the node to visit and a payload that may be passed to all the visitors as they are called. In this way, the sweeper will call the virtual method once for each and every one of the nodes in the AST that is passed to it in a depth-first traversal. The payload parameter can be used to pass information (for example, a symbol table) to each node as required. Developers will build classes derived from the AstSweeper class, overriding the methods of particular interest to them.

#### Example

Suppose you need to determine the percentage of parameter names starting with an underscore character, thus conforming to the X++ coding guidelines. You would then write a class deriving from the **AstSweeper** class with logic that calculated the number of parameters and the number of parameters starting with underscore. The following example shows this code.

```xpp
public class ParameterCounter : AstSweeper<object, object>
{
    /// <summary>
    /// The parameter count maintained as the methods are encountered.
    /// </summary>
    public int ParameterCount { get; set; }

    /// <summary>
    /// The number of parameters that start with an underscore character.
    /// </summary>
    public int UnderscoredParameters { get; set; }

    /// <summary>
    /// Visits the method parameters.
    /// </summary>
    /// <param name="o">The payload. Not used in this scenario.</param>
    /// <param name="parameters">The list of parameters to visit.</param>
    /// <returns>The method parameters.</returns>
    protected override object VisitMethodParameters(object o,
        IEnumerable<ParameterDeclaration> parameters)
    {
        this.ParameterCount += parameters.Count();
        this.UnderscoredParameters += parameters
            .Where(p => p.Name.StartsWith("_")).Count();

        return null;
    }
}
```

In this case, the tally is maintained in the **ParametersCount** and **UnderscoredParameters** properties that are defined in the class scope. Another equally valid approach would be to pass this information into the payload that is passed to all the **Visit** methods. In most cases, the user should unconditionally call **super()** from the overridden method to make sure that the **Visit** methods are called for all nodes below the one being visited. In the case above, it does not make a difference so we opt to improve performance by pruning the AST tree traversal.

### Writing code for Best Practice rules

To author a business rule:

1. Define the situation you want to diagnose in terms of properties of the AST. You will write **Visit\*** methods that can do the analysis.
2. When the error condition has been found, a diagnostic message must be generated. There is an API that is used for this purpose; basically you need to write some boilerplate code for each diagnostic message.
3. You need to hook your new best practice rule into the rest of the framework, so the user can decide whether or not to include your rule and to run it if so directed.

### Create a best practice rules project in Visual Studio

In this walkthrough, we imagine the following scenario:

- Some methods are adorned with an Author attribute that provides the name of the individual who wrote the code. The attribute is useful when finding who to point the finger at when stack traces containing that method appear.
- Since we have a significant turnaround of developers, the names of the developers listed cannot be static. We want to find the names that are used in the Author attributes, and match them against a list of names of current developers.

The author attribute class is defined as:

```xpp
class AuthorAttribute extends SysAttribute
{
    private str theAuthor;

    public void new(str _author) 
    {
        this.theAuthor = _author;
    }
}
```

In production code, we would put in documentation comments and assertions to validate key assumptions about parameter values etc. For the sake of clarity, we omit these steps in this walkthrough, where the code is written for clarity. Now that we have set the stage for what we want to achieve, we can start up Visual Studio and create a best practice rules project. Provide a meaningful name that properly conveys what the rules are intended to do: Visual Studio creates a project with some source code snippets and project references set up. You can save considerable time by using this source code as a starting point for your own code. The pre-canned example contains rules that prohibit the word “Microsoft” in any method names (presumably for copyright reasons) and a metadata-based rule prohibiting certain characters in names. Since we are not concerned with the metadata checks for now, you can delete the InvalidCharactersDiagnosticItem.cs and DemoMetadataCheck.cs files from the project. Also, since we are not interested in the Microsoft name check, go ahead and delete the content of the VisitMethod method in the DemoAST class. The first thing we need to do is to find out if there are one or more Author attributes for a particular method. You will notice that the Method type (that is passed as a parameter to the VisitMethod method) has an Attributes property of type AttributeList. Let's use it to see if any Author attributes are defined on this method:

```xpp
protected override object VisitMethod(BestPracticeCheckerPayload payload, Method method)
{
    var names = new List<string>();
    foreach (var attribute in method.Attributes.Attributes)
    {
        if (string.Compare(attribute.Name, "Author",
            ignoreCase: true, culture: CultureInfo.InvariantCulture) == 0)
        {
            var authorNameLiteral = attribute.Parameters.First().Literal as StringAttributeLiteral;
            // The name contains quotes (either single or double). Get rid of those
            var authorName = authorNameLiteral.Value.Trim('\'', '"');
            names.Add(authorName);
        }
    }

    // More to come...
    return null;
}
```

At this point we have looped through any attributes, and collected a list of author names, that is names that are provided as the first parameters to the Author attributes. Now we need to compare the list against a list of acceptable authors, that we maintain in a static list. Whenever an author is provided that is not mentioned in the list we need to issue an appropriate diagnostic message. At this time, we have something like:

```xpp
public class AuthorListRule : BestPracticeAstChecker<BestPracticeCheckerPayload>
{
    private static HashSet<string> authorlist = new HashSet<string>()
    {
        "Alan Kay", "John von Neuman", "C.A.R. Hoare"
    };

    public AuthorListRule() : base()
    {
    }

    protected override object VisitMethod(BestPracticeCheckerPayload payload, Method method)
    {
        var names = new List<string>();
        foreach (var attribute in method.Attributes.Attributes)
        {
            if (string.Compare(attribute.Name, "Author",
                ignoreCase: true, culture: CultureInfo.InvariantCulture) == 0)
            {
                var authorNameLiteral = attribute.Parameters.First().Literal as StringAttributeLiteral;
                // The name contains quotes (either single or double). Get rid of those
                var authorName = authorNameLiteral.Value.Trim('\'', '"');
                names.Add(authorName);
            }
        }

        foreach (var name in names)
        {
            if (!authorlist.Contains(name))
            {
                // TODO: Add a diagnostic message
            }
        }
        return null;
    }
}
```

In other words, we need to create a diagnostic message to let the user know about the transgression of the rule. As noted before, it is important to call the base implementation of your visitor, which will then call visitor methods for all the nodes that are contained in the method. However, in this case, we do not want to do any further processing once we have determined if the author attribute is on the list.

### Add a class for the diagnostic message

The project already includes boilerplate code for an error message, so we will use that as our starting point to create the diagnostic message that will be returned if the rule is violated. Each message is implemented as a class of its own. Each error message may have any amount of contextual information encoded into it. In this case, the contextual information is the name of the author that is not found in the list. We will start by adding the message to the messages resource file: Open that file in the project and add a string to it. We will use the name (also known as the error moniker) AuthorNotCurrent. The ‘{0}’ string is a placeholder for the contextual information, in this case the name of the author who is not in the list. In addition to the actual text that will appear in the error message, there is also a string containing a description of the rule. This information is shown in the best practice dialog within Visual Studio and is designed to help the user decide which rules to enable on the system. Create a class for the diagnostic message, and call it **AuthorNotCurrentDiagnosticItem.cs**. Add the following code inspired from the **NotAllowedWordDiagnosticItem** class.

```xpp
namespace CompareAuthorsToList
{
    using System;
    using System.Collections.Generic;
    using System.Runtime.Serialization;
    using System.Xml.Linq;
    using Microsoft.Dynamics.AX.Metadata.XppCompiler;

    [DataContract]
    public class AuthorNotCurrentDiagnosticItem : CustomDiagnosticItem
    {
        private const string AuthorNotCurrentKey = "Author";
        public const string DiagnosticMoniker = "AuthorNotCurrent";

        public AuthorNotCurrentDiagnosticItem(string path, string elementType, TextPosition textPosition, string author)
            : base(path, elementType, textPosition, DiagnosticType.BestPractices, Severity.Warning, DiagnosticMoniker, Messages.AuthorNotCurrent, author)
        {
            this.AuthorNotCurrent = author;
        }

        public AuthorNotCurrentDiagnosticItem(Stack<Ast> context, TextPosition textPosition, string author)
            : base(context, textPosition, DiagnosticType.BestPractices, Severity.Warning, DiagnosticMoniker, Messages.AuthorNotCurrent, author)
        {
            this.AuthorNotCurrent = author;
        }

        // Serialization support
        public AuthorNotCurrentDiagnosticItem(XElement element)
            : base(element)
        {
        }

        [DataMember]
        public string AuthorNotCurrent { get; private set; }

        /// <summary>
        /// Hydrate the diagnostic item from the given XML element.
        /// </summary>
        /// <param name="itemSpecificNode">The XML element containing the diagnostic.</param>
        protected override void ReadItemSpecificFields(System.Xml.Linq.XElement itemSpecificNode)
        {
            this.AuthorNotCurrent = base.ReadCustomField(itemSpecificNode, AuthorNotCurrentKey);
        }

        /// <summary>
        /// Write the state into the given XML element.
        /// </summary>
        /// <param name="itemSpecificNode">The element into which the state is persisted.</param>
        protected override void WriteItemSpecificFields(System.Xml.Linq.XElement itemSpecificNode)
        {
            this.WriteCustomField(itemSpecificNode, AuthorNotCurrentKey, this.AuthorNotCurrent);
        }
    }
}
```

The diagnostic message is ready for consumption. There is just one piece of bookkeeping that needs to be done; the rule needs to publish declaratively which diagnostics it potentially issues. Go back to your rule and modify the BestPracticeRule attribute to reflect the new diagnostic message:

```xpp
[BestPracticeRule(
    AuthorNotCurrentDiagnosticItem.DiagnosticMoniker,
    typeof(Messages),
    AuthorNotCurrentDiagnosticItem.DiagnosticMoniker + "Description",
    BestPracticeCheckerTargets.Class)]
public class AuthorListRule : BestPracticeAstChecker<BestPracticeCheckerPayload>
{ // ... }
```

As you can see, there are four parameters specified for the **BestPracticeRule** attribute:

1. The rule moniker.
2. The type of the resource file holding the rule description. In this example, we are using the default resource file named. Messages, which created a class called Messages. We want the type of this class as the second argument.
3. The name of the string resource that contains the description of the rule. This name is the string called **AuthorNotCurrentDescription** that we added to the resource file above; it contains a human legible string to describe the rule. This string is used to describe the rule to the user in a best practice dialog within Visual Studio. In Visual Studio, select **Dynamics 365 &gt; Best Practices Configuration** to view the dialog.
4. A description of the artifacts to check. In this case, the value specifies that the rule should only be applied to classes. Modify the description as needed by using one of the other literals in the **BestPracticeCheckerTargets** enumeration.

Instantiate the class that describes the diagnostic message and add it to the set of diagnostics:

```xpp
foreach (var name in names)
{
    if (!authorlist.Contains(name))
    {
        // Create the custom error message, including
        // the contextual name information...
        var warning = new AuthorNotCurrentDiagnosticItem(
            this.Context, method.Position, name);

        // and add it to the set of reported messages.
        this.ExtensionContext.AddErrorMessage(warning);
    }
}
```

At this point, you have a complete best practice rule, ready to provide value in your organization. Build it and fix any errors.

## Metadata based Best Practice rules

Until now we have been describing how to write rules that deal with code. In this section we show how to author rules that apply to metadata, not code. Classes that deal with metadata rules are derived from **BestPracticeMetadataChecker**. The derived instance receives an instance of the metadata describing the artifact that must be checked. You then use the APIs in the **Microsoft.Dynamics.AX.Metadata.Metamodel** to fetch further metadata as needed, and use LINQ queries over the metadata graphs. The template for best practice checks contains a class performing metadata checks as well as a code based one we discussed in the previous section. The mechanics involved in issuing diagnostic messages is the same as we covered above.

## Install, run, and test your rule

When your code compiles cleanly, a DLL will be created. In order for the tooling to be able to pick up the new rule, this DLL must be installed before running it. Installing the DLL can be done in two ways:

- By using the button on the Best Practice configuration dialog. Click the **Install extension** button. You will be asked to point to the assembly file that contains your rule (that is, the DLL generated when you build the rule). Press OK, and the system will copy the DLL where it needs to be (see below).
- By manually installing the DLL into the C:\\Packages\\bin\\BPExtensions folder.

If you want to debug your rule, you will find it useful to copy the .pdb file to the same directory as the assembly. After the DLL has been deployed to the target directory, Visual Studio needs to be restarted. After that, the rule is available for use. You may have to debug your rule to iron out any remaining kinks. In fact, stepping through your rule and inspecting the ASTs is valuable when you are getting started. To debug a rule, you need to know that the best practice rule is run by the **xppAgent** process; it is therefore not run within the context of VS itself. Make sure you have selected **Run best practice checks** in the Visual Studio Options dialog, in the **finance and operations** page. Otherwise, your check will not run.   Set a breakpoint in the **VisitMethod** method, and then do a build of a model that has the new rule switched on as shown above for the Fleet management model. Attach your VS instance to the **xppcAgent** process. When you do a build your breakpoint will be hit, and you can start drilling into your code. You can see all the properties, the list of declarations and statements, and find out all the details about them.

### Running rules in XppBp.exe

As described above the best practice rules are often run as part of the build of a project from Visual Studio, but there is also a dedicated command-line tool to run them. This tools is the **xppbp.exe** tool, and it is intended mainly for nightly build scenarios. Invoking it from the command line yields a useful overview of the command-line switches and arguments. Here are some useful examples:

- Run BP on all forms in a module: `xppbp -module:FleetManagement form:*`
- Run BP on specific elements: `xppbp -module:FleetManagement class:MyClass form:MyForm`
- Run BP on all items in the model (and only for this one model in the module): `xppbp -module:FleetManagement -model:FleetManagement –all`
- Run BP on all items in all models in the module: `xppbp -module:FleetManagement –all`
- Write the output to log files: `xppbp -module:FleetManagement -all -xmllog=Log.xml -log=Log.txt`


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
