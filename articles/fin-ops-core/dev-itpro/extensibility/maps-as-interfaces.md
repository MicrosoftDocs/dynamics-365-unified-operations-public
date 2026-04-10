---
title: Extend table maps that are used as interfaces
description: Learn about how to extend table maps that are used as interfaces, including overviews of hierarchies and extension scenarios.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: how-to
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 11
---

# Extend table maps that you use as interfaces

[!include [banner](../includes/banner.md)]

The **SalesPurchLine** and **SalesPurchTable** table maps expose a set of common fields and methods that a variety of product features use. Refactor the mapping of fields and the implementation of methods into a class hierarchy. Some of these changes include:

- Move methods on the table maps to the class hierarchy.
- Expose fields through parm-methods on the class hierarchy.
- Keep the table map, and keep tables implementing the mapping to the table map, but make the fields on the table map obsolete, and remove field mapping.
- Make the methods on the table map obsolete.

## SalesPurchTableInterface hierarchy

The new **SalesPurchTableInterface** class is the abstract base class for the ApplicationSuite functionality that the refactoring of the **SalesPurchTable** table map introduces. The class contains abstract methods for fields and methods, which must exist for each table implementing the interface. It also contains the default logic in methods, which is common across all implementations. Each table that implements the **SalesPurchTable** table map must be represented as a derived class in the **SalesPurchTableInterface** class hierarchy. Decorate each derived class with a **SalesPurchTableInterfaceFactory** attribute class. Use the attribute to associate the derived class with the table, so that you can instantiate a class of the correct type depending on a **SalesPurchTable** record.

:::image type="content" source="media/MapsAsInterfaces1.png" alt-text="Screenshot of the MapsAsInterfaces diagram.":::

Even though the table map methods are obsolete, the corresponding methods still exist on the implementing tables. Refactor the logic in these methods from delegating calls to the method on the table map, to the corresponding method on the base class of the hierarchy.

## Extension scenario

In this example, if you want your ISVModule2 model to extend the interface class hierarchy and the tables that implement the **SalesPurchTable** table map, complete the following steps:

1. Add fields and methods through table extension to the necessary tables that implement the **SalesPurchTable** table map.
1. Create a new interface class hierarchy that exposes the new fields as parm-methods and other additional methods. The base class of the class hierarchy must be concrete and not abstract.
1. Create derived classes for each table that you extended.
    1. Decorate each derived class with the **SalesPurchTableInterfaceFactory** attribute class to associate the class with the correct table.
    1. Create a static factory method on the base class of the new class hierarchy. The factory method should instantiate the proper derived class that leverages the **SalesPurchTableInterfaceFactory** attribute. If no derived class is found, the factory method returns an instance of the base class.
1. Create an extension class of the **SalesPurchTableInterface** class. The class augments the **SalesPurchTableInterface** class with a method that creates an instance from the new class hierarchy by calling the factory method on the new class hierarchy.
 
The following diagram shows the preceding classes and extensions.

:::image type="content" source="media/MapsAsInterfaces2.png" alt-text="Screenshot of the MapsAsInterfacesWalkThrough diagram.":::

The diagram contains an ISVModule1 model, which includes the **ISV1Header** table that implements the **SalesPurchTable** table map and contains its own **SalesPurchTableInterface** derived class. The model is independent of the ISVModule2, so when logic in the ISVModule2 creates an instance from the **ISV2SalesPurchTableInterface** class hierarchy, the instance of the base class is returned when the **SalesPurchTable** record is of type **ISV1Header**. If the methods on the base class return a reasonable result for unknown tables, the two ISV models co-exist within the same installation.

## Code example

The following code example demonstrates a way to extend table maps.

```xpp
[ExtensionOf(classStr(SalesPurchTableInterface))]
final public class ISV2SalesPurchTableInterface_Extension
{
    private ISV2SalesPurchTableInterface ISV2SalesPurchTableInterface;

    public ISV2SalesPurchTableInterface ISV2SalesPurchTableInterface()
    {
        if (!ISV2SalesPurchTableInterface)
        {
            ISV2SalesPurchTableInterface = ISV2SalesPurchTableInterface::createInstance(this);
        }

        return ISV2SalesPurchTableInterface;
    }

}

public class ISV2SalesPurchTableInterface
{

    SalesPurchTableInterface salesPurchTableInterface;

    private void initializeSalesPurchTableInterface(SalesPurchTableInterface _salesPurchTableInterface)
    {
        salesPurchTableInterface = _salesPurchTableInterface;
    }

    public SalesPurchTable parmSalesPurchTable()
    {
        return salesPurchTableInterface.parmSalesPurchTable();
    }

    protected void new()
    {
    }

    public static ISV2SalesPurchTableInterface createInstance(SalesPurchTableInterface _salesPurchTableInterface)
    {
        SalesPurchTableInterfaceFactoryAttribute attr = 
  new SalesPurchTableInterfaceFactoryAttribute(
   tableId2Name(_salesPurchTableInterface.parmSalesPurchTable().tableId));
        
        ISV2SalesPurchTableInterface instance = 
  SysExtensionAppClassFactory::getClassFromSysAttribute(classStr(ISV2SalesPurchTableInterface), attr) 
  as ISV2SalesPurchTableInterface;

        instance.initializeSalesPurchTableInterface(_salesPurchTableInterface);

        return instance;
    }

    public AccountingGroupId parmAccountingGroupId()
    {
        return '';
    }

}
[SalesPurchTableInterfaceFactoryAttribute(tableStr(SalesTable))]
public class ISV2SalesTableSalesPurchTable extends ISV2SalesPurchTableInterface
{
    private SalesTable parmSalesTable()
    {
        return this.parmSalesPurchTable();
    }

    public AccountingGroupId parmAccountingGroupId()
    {
        return this.parmSalesTable().AccountingGroupId;
    }

}

[SalesPurchTableInterfaceFactoryAttribute(tableStr(PurchTable))]
public class ISV2PurchTableSalesPurchTable extends ISV2SalesPurchTableInterface
{

    private PurchTable parmPurchTable()
    {
        return this.parmSalesPurchTable();
    }

    public AccountingGroupId parmAccountingGroupId()
    {
        return this.parmPurchTable().AccountingGroupId;
    }

}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
