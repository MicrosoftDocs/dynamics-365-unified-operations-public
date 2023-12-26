---
title: Turn off model customization and deprecate functionality
description: This article describes the process of disabling customization of a model. By following this process, you make it ineligible for over-layering.
author: pvillads
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: pvillads
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: f3df4b82-84d9-401e-8d7f-cfd42772621c
---

# Turn off model customization and deprecate functionality

[!include [banner](../includes/banner.md)]

This article describes the process of disabling customization of a model. By following this process, you make it ineligible for over-layering. Developers will still be able to extend that model. This article also describes how you can deprecate obsolete functionality.

Typically, you build an application in models that depend on other models. At the very least, your models will depend on the Application Platform model that is provided. Finance and operations applications run on the Microsoft Azure cloud platform. In other words, it runs off-premises, in data centers that are managed by Microsoft. Because we can’t support changes from a large number of vendors in the fundamental models, your applications can no longer over-layer artifacts in those models. Therefore, to build your applications, you must use extensions instead of over-layering. Even though all the artifacts in the models that you depend on are available for documentation purposes, you can’t compile someone else’s intellectual property and run it in the cloud.

## Locking customizations
Transitioning a model from over-layering to extensions involves three steps:

1.  You set a property that causes instances of over-layering to be flagged as warnings. This step is sometimes known as “soft-locking.”
2.  You have a period when you can burn down the warnings by using extensions instead of over-layering.
3.  When you have resolved all the warnings, it’s time to make over-layering a hard error that causes compilation to fail. This step is known as “hard-locking.” When a model is hard-locked, the tooling that is required for over-layering can’t be used for that model. Additionally, you can’t have more than one model in a given package.

Currently, there is no tooling that you can use to manipulate the property that disables customizations. Instead, you must add the **Customization** XML element to the model descriptor file, as shown in the following example. You can find the model descriptor file at ...\\&lt;packages&gt;\\&lt;package name&gt;\\Descriptor\\&lt;model name&gt;.xml.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AxModelInfo xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
<Customization>DoNotAllow</Customization>
<Description>My cool locked application</Description>
...
<</AxModelInfo>
```

There are three levels of customization settings:

-   **Allow customizations** – If the **Customization** element is omitted, or if it’s provided but the text **Allow** is used inside it, there are no restrictions.
-   **Soft-locking** – If you require soft-locking, use the text **AllowAndWarn** inside the **Customization** element.
-   **Hard-locking** – To disable customization of the model, use the text **DoNotAllow** inside the **Customization** element, as shown in the preceding example.

> [!NOTE]
> Elements in the descriptor file must be listed in alphabetical order.

## Backward compatibility of the platform
There is a requirement that your application must continue to run even if a newer version of a dependent platform model is installed. Therefore, we enforce strict requirements for backward compatibility on all the changes that we make in those platform models. We can clarify this point through an example. For this example, you have a base model M that has the following class.

```xpp
public void DoSomething(int arg)
{
    // Do great stuff
}
```

In your model that depends on model M, you want to take advantage of all the great functionality that the **DoSomething** class offers. Therefore, you have the following code.

```xpp
{
    var c = new SomeClass();
    c.DoSomething(42);
}
```

Later, your vendor (perhaps Microsoft) releases a new, updated version of the model that you depend on (model M). When this model is released, we must support the public interface, because things must run without recompilation. Suppose that we changed the method signature by adding another parameter, as shown here.

```xpp
public void DoSomething(int arg, str anotherArg)
{
    // Do greater stuff
}
```

In this case, we break the app. The common language runtime (CLR) can’t call the method, because the parameter profile that is assumed in the call isn’t the same as the parameter profile of the callee (the calling code provided one parameter, but two are now required). Therefore, it’s a good idea to limit what is publicly consumable. If something is private, nobody can use it from outside your model. However, another option is to make the artifact internal. If you apply the **internal** modifier to a class or method, the artifact is visible only inside your model and can’t be reached from the outside. Essentially, you must assume that anything that isn’t internal or private will be used from outside your model. Therefore, you must support it forever. Never make anything public or protected unless it absolutely must be public or protected, and use interfaces to hide implementation details that aren’t relevant outside the boundary of your model. There is no way to mark metadata (as opposed to code) with the internal visibility specifier.

## Testing internal functionality
By limiting the surface area of your model, you help guarantee that you will be able to fix issues in your models that do not allow customizations, and that the application will run smoothly. However, you might argue that, by making things internal, you limit the ability to test your code. To remedy this situation, you can inform your test packages about the packages that they should test. In other words, the test packages can access internal things. To implement this solution, you edit the descriptor file, as shown in the following example.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AxModelInfo xmlns:i=http://www.w3.org/2001/XMLSchema-instance>
<InternalsVisibleTo xmlns:d2p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
<d2p1:string>ExternalPackageName</d2p1:string>
</InternalsVisibleTo>
...
</AxModelInfo>
```

You can provide any number of external packages by including them in the **InternalsVisibleTo** element. This information is provided for the package that contains the code to test, not for the package that contains the testing code. In other words, the package determines who it shares information with. **Note:** The elements under **AxModelInfo** must be in alphabetical order.

## Deprecating functionality
### Deprecating methods

Sometimes, you no longer want to support source code that is public. As we mentioned earlier, you should not remove an artifact from the code unless that artifact is private or internal, because there might be users who rely on it. Instead, you can use the **SysObsoleteAttribute** attribute to specify that consumers should no longer use that artifact. We recommend that you mark things as obsolete in two phases:

1.  Specify that using the artifact is flagged as a warning.
2.  After one or more release cycles, make using the artifact an error.

In the following example, the **DoSomething** method is defined in the first release of a model.

```xpp
class SomeApi
{
    void DoSomething()
    {
        // Do great stuff
    }
}
```

In the second release, you’ve determined that there is a better way to accomplish something. Therefore, you add the new implementation and make the old implementation obsolete.

```xpp
class SomeApi
{
    [SysObsolete("Use DoSomethingNew instead", false)]
    void DoSomething()
    {
        // Do great stuff
    }

    void DoSomethingNew()
    {
    }
}
```

All your existing customers will continue to call the old version. This situation is fine, but the customers won’t be able to take advantage of the benefits of the new version. Anyone who codes against your class will receive a build warning together with the message that you provided in the **SysObsolete** attribute argument. Presumably, these clients will update their code so that it uses the new method. As time passes, more clients will move to the new version. Therefore, at some point, it will make sense for you to make coding against the method a hard error.

```xpp
class SomeApi
{
    [SysObsolete("Use DoSomethingNew instead", true)]
    void DoSomething()
    {
        // Do great stuff
    }

    void DoSomethingNew()
    {
    }
}
```

Again, for the reasons that we mentioned earlier, you may never be able to get rid of the old method completely, because it was not made private or internal.

### Deprecating metadata

For deprecating model elements (tables, data entities, EDTs, Enums, ...etc.), use the property **IsObsolete** that is available on all model element types. **IsObsolete** is also available on table, view, and data entity fields. When you set **IsObsolete** to Yes, references to that element or field will cause compilation warnings.





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
