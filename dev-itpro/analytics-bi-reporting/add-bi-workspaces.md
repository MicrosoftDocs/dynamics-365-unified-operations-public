---
# required metadata

title: Add BI to workspaces | Microsoft Docs
description: In this tutorial, you’ll add BI controls such as KPI tiles to an existing workspace. 
author: sericks007
manager: AnnBe
ms.date: 2015-12-12 19:09:49
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 24551
ms.assetid: 670475a2-aac8-4f71-8cb0-0e3dd6310436
ms.region: Global
# ms.industry: 
ms.author: milindav

---

# Add BI to workspaces

In this tutorial, you’ll add BI controls such as KPI tiles to an existing workspace. 

Key concepts
------------

-   *Aggregate measurements*, similar to *perspectives and cubes* from earlier versions, enable you to model and consume aggregate data.
-   *Key Performance Indicators* (KPIs) are a form of analytic controls that track organizational performance against the current status. KPIs are represented as tiles in a *workspace* or the *dashboard*. In this tutorial, you’ll model a KPI in Visual Studio.
-   KPIs that are modeled in Visual Studio can be modified in the client. A user also has the ability to model new KPIs using the client.
-   A *workspace* is an overview page that is specific to a particular subject area. Workspaces are common to all users. In this tutorial, you’ll add content into an existing workspace.
-   The *dashboard* is the default home page for each user.
-   *Tiles* are securable objects that can be pinned to a workspace or the dashboard. KPIs and aggregate data that are shown on the dashboard or a workspace can be secured by using menu items.
-   Aggregate data can be consumed in building charts and other controls. Using the model driven approach, you have the ability to create data entities by directly referencing aggregate measurements and aggregate dimensions. These entities are referred to as *aggregate data entities*. Aggregate data entities are read-only data entities used for reporting purposes.
-   *Aggregate programming model* enables a developer to consume aggregate data programmatically using either X++ or C\# code. Data retrieved using the aggregate programming model can be used as a data source in forms.
-   *Method expressions* enable a developer to build rich expressions using aggregate data. Method expressions are written in X++. KPIs can be modeled using method expressions thereby eliminating the need to build MDX expressions.
-   *Contextual BI* refers to providing required insights as part of the user experience such that the user has relevant insights to not only achieve the task at hand but be highly productive during the course of the day.
-   *Embedded BI* refers to analytic content being embedded in the user experience. Contextual BI and embedded BI teams are closely related – contextual BI implies the added notion that the context of analytic context revolves around the data or the task at hand.
-   *Self service BI* refers to enabling to user to tweak existing and/or create new analytic content such as reports, KPIs, and dashboards.

## Setup
1.  If this is the first tutorial you’re working on, you must complete the steps in "Installing demo data" in the [Appendix](#appendix).
2.  Import the project **Adding BI to workspaces.axpp** in the **C:FMLabLab 10-1** folder.
    -   Download the Fleet Management sample from <https://github.com/Microsoft/FMLab>, save it to **C:**, and unzip it.
    -   In Visual Studio, from the **Dynamics 365** menu, select **Import project**.
    -   Go to the **C:\\FMLab\\Lab 10-1** folder and select the **Adding BI to workspaces.axpp** project.
    -   Select the overwrite option.
    -   Select new solution.
    -   Click **OK**.

3.  You should see the project in the solution explorer in Visual Studio, and the FMRentalCalculations class is shown.

## Model a KPI definition with a range
### Model a KPI using Aggregate measures

Let’s assume that we want to monitor **Revenue per rental for Vehicles with Automatic transmission**. As you may recall, we have a measure that calculates revenue per rental. However, we want revenue per rental only from vehicles with automatic transmission. In order to achieve this scenario, we’ll define a range expression to filter the value expression.

1.  Select the project node. Right-click and select **Add**.
2.  Select **Analytics &gt; Key performance indicator** from the list of items. Enter **FMRevenuePerRentalAutoTransmission** as the name of the KPI.
3.  KPI designer will be displayed with the KPI **RevenuePerRentalAutoTransmission**.
4.  Right-click the **RevenuePerRentalAutoTransmission** node and select **Properties**. Enter the following properties.

|                       |                        |
|-----------------------|------------------------|
| **Property**          | **Value**              |
| Measurement           | FMAggregateMeasurement |
| Threshold Short Label | Auto Transmissions     |
|                       |                        |

### Define Ranges to filter value and goal

1.  Define the expression for the KPI value. Under **FMRevenuePerRentalAutoTransmission**, select the **Value** node and specify the following properties (the values must be entered in the order they appear in the table below).
    |               |                  |
    |---------------|------------------|
    | **Property**  | **Value**        |
    | Measure Group | FMRentalCharges  |
    | Measure       | RevenuePerRental |

2.  Because we want to filter vehicles with auto transmission, let’s define a range expression. Expand **Value &gt; Ranges**  and then select the **Ranges** node. Right-click and select **New Range**.
3.  Select the newly created range. Right-click and select **properties**. Enter following property values (the values must be entered in the order they appear in the table below).
    |               |                     |
    |---------------|---------------------|
    | **Property**  | **Value**           |
    | Name          | AutoTransmission    |
    | Filter Type   | Value               |
    | Dimension     | FMVehicle           |
    | Attribute     | VehicleTransmission |
    | Default value | 1 (designates Auto) |
    | Hidden        | No                  |

    **Note:** When defining value based filters, the system does not validate the string of numeric value entered for the default value property. You’re expected to enter the data value as it would appear in data. This is similar to specifying a range expression in general. If the range expression isn’t hidden, the user can change this filter value or the filter definition in the client.
4.  Define the expression for the KPI Goal. Select the **Goal** node and specify the following properties.

|              |              |
|--------------|--------------|
| **Property** | **Value**    |
| Goal Type    | BasedOnValue |
| Value        | 250          |

### 

## Create a wide KPI tile using the KPI definition
Tiles are user interface elements that can be defined as buttons to take the user to a different location in the product. In that regard, they are similar to menu item buttons. However, tiles can also display business data like counts and KPIs. Next you’ll create a KPI tile by creating a new tile element and associating it with the KPI that we defined previously.

1.  Create a new tile. In Solution Explorer, right-click the project node, point to **Add**, and then click **New Item**.
2.  Select **Operations Artifacts** &gt; **User Interface** &gt; **Tile**.
3.  In name, enter **FMRevenuePerRentalAutoTransmissionTile**. This is the name of the tile that will be created. The name must be unique across tiles.
4.  Click **Add**. The new tile will appear in Visual Studio.
5.  Drag and drop the **FMRevenuePerRentalAutoTransmission** KPI definition from Solution Explorer onto the tile in the designer. This will automatically specify a few properties. Enter following properties.
    |              |                           |
    |--------------|---------------------------|
    | **Property** | **Value**                 |
    | Label        | Revenue per Rental - Auto |
    | Size         | Wide                      |

6.  Save the tile

### Modify the workspace by adding the newly created KPI tile to it

Now that you defined a KPI tile, you can put it in the interface so the user can take advantage of it. First, add it to a workspace that you want to extend.

1.  In the Application Explorer, locate **Fleet Management &gt; User Interface &gt; Forms &gt; FMClerkWorkspace**. Right-click and select **Add to project**.
2.  In Solution Explorer, double-click **FMClerkWorkspace**. Form Designer will be launched for the selected form.
3.  You’ll place the tile at the end of the first section (TabPage) of the panorama (Tab) on the form. This section is named TileContainer. In the design window, expand **FMClerkWorkspace** &gt; **Design** &gt;**PanoramaBody (Tab)** &gt; **SummaryTileSection (TabPage)**.
4.  Right-click **SummaryTileSection**, point to **New**, and then click **Tile Button**.
5.  Specify the following values for the new tile button.
    |              |                                        |
    |--------------|----------------------------------------|
    | **Property** | **Value**                              |
    | Name         | FMRevenuePerRentalAutoTransmission     |
    | Tile         | FMRevenuePerRentalAutoTransmissionTile |

6.  Save and rebuild the project:
    -   Ensure that you have enabled DBSync on build.
    -   To enable, select the project node, right-click&gt;choose properties, and select the **Set Synchronize Database on build** property to **True**.

7.  Let’s run the form to see the tile that we created. Select the **FMClerkWorkspace** form in Solution Explorer. Right-click and select **Set as startup project**.
8.  Click **Ctrl+F5** to run the form.
9.  You’ll see the modified workspace with the tile definition.
10. Select the **RevenuePerRentalAutoTransmission** KPI tile to go to the KPI details page. Scroll and see the trends created by default.

[![BI8](./media/bi8.png)](./media/bi8.png)

## Modify default trend charts shown in the client
Trend analysis is vital to the KPI experience and the KPI details page provides the user with 3 pre-build trend charts. These charts can be used to answer the following business questions.

-   **Time trend:** When did the change occur? Has it always been this way?
-   **Top contributors:** Who or what are biggest contributors?
-   **Bottom contributors:** Who or what are contributing least?

When you define a new KPI, you get the these trends by default – the system tries to guess which trends may be relevant. This happens, even if the developer does not specify these trends when defining the KPI. As a developer who is aware of the business context, you may wish to identify specific trends that need to be shown to the user – not the default trends shown. In the following example, let’s build specific trend charts to the KPI so that users can quickly diagnose the problem.

### Modify the default time trend chart

You’ll modify the default time trend chart so that it only shows the trend for the last 6 months.

1.  Select the KPI **RevenuePerRentalAutoTransmission** in Solution Explorer and double-click. KPI designer will be displayed.
2.  Select **RevenuePerRentalAutoTransmission &gt; Trends** node. Right-click and select **New Trend**.
3.  Right-click the newly created node and select **Properties**. Modify following property values.
    |              |                 |
    |--------------|-----------------|
    | **Property** | **Value**       |
    | Name         | MyTimeTrend     |
    | Trend Type   | Time trend      |
    | Item Count   | 6               |
    | Dimension    | RentalStartDate |
    | Attribute    | Month           |
    | Label        | Past 6 months   |

4.  Save the KPI.

### Modify the default top contributors trend chart

You’ll modify the default top contributors chart to reflect the top auto transmission rentals by vehicle model.

1.  Select **RevenuePerRentalAutoTransmission &gt;** **Trends**. Right-click and select **New Trend**.
2.  Select the newly created bode. Right-click and select properties. Modify following property value.
    |              |                       |
    |--------------|-----------------------|
    | **Property** | **Value**             |
    | Name         | TopModels             |
    | Dimension    | FMVehicle             |
    | Attribute    | VehicleModel          |
    | Item Count   | 5                     |
    | Trend Type   | Top trend             |
    | Label        | Top performing models |

3.  Next, you’ll define another top contributor chart in addition to the default one. Select the **RevenuePerRentalAutoTransmission &gt; Trends** node. Right-click and select **New Trend**.
4.  Select the newly created trend node. Right-click and select **Properties**. Enter the following property values (you must enter property values in the following order).
    |              |                    |
    |--------------|--------------------|
    | **Property** | **Value**          |
    | Name         | TopCustomers       |
    | Trend Type   | Top trend          |
    | Dimension    | FMCustomerProfile  |
    | Attribute    | Customer Last Name |
    | Item Count   | 5                  |
    | Label        | Top Customers      |

5.  Save the KPI. Rebuild the project.

### Preview the trending experience in client

Preview the KPI definition in the client.

1.  Click **Ctrl+F5** to run the form in Visual Studio. You’ll see the modified workspace with the tile definition
2.  Select the **RevenuePerRentalAutoTransmission** KPI tile to go to the KPI details page. Notice that the trend definitions are shown in the KPI details UI.

[![BI9](./media/bi9.png)](./media/bi9.png) Scroll to the right and select the top contributors trend. In the drop-down select the **Top Customers** trend chart. Notice that the chart changes to reflect the trend chart selected by the user.

## Model a KPI using a method expression
Defining a KPI expression using pre-defined measures is the easiest approach toward building KPIs. However, it requires that the developer models all the required measures into the aggregate measurement. It’s a good practice to ship frequently used calculations within the aggregate measurement. This way, users can define new KPIs within the client. However, there is another way to ship calculations without crowding the aggregate measurement with many calculated measures. Developer has the ability to build a calculated expression by referencing existing measures and dimension attributes and to reuse that expression in a KPI definition. These expressions are called Method expressions. Method expressions can be thought of as the equivalent of MDX expressions in Dynamics AX 2012. But as you’ll discover in following sections, writing method expressions is both easy and quick.

### Review the first method expression

Let’s write a simple method expression that multiplies a measure by a constant. Let’s use that method expression and define a KPI. First, let’s examine the code you’re going to write.

    using  Microsoft.Dynamics.AX.Framework.Analytics.AggregateQuery.QueryModel.Core;

    [BIAggregateQueryExpressionAttribute("FMAggregateMeasurements")]
    class FMRentalCalculations
    {

        // Provide the EDT of the value returned
        [BIAggregateQueryMethodExpression(extendedtypestr(AmountMST))]
        public static NumericExpression FMRevenuePerRentalMargin()
        {
            // Margin ratio is a value derived using a function
            NumericExpression marginRatio = FMFleetMetodExpressions::RentalMarginRatio();
           
            NumericExpression calculation = new MeasureExpression("FMAggregateMeasurements/RevenuePerRental").Multiply( marginRatio);

            return calculation;
        }

        // Provides a constant that gets the margin ratio
        private static NumericConstantExpression RentalMarginRatio()
        {
            return new NumericConstantExpression("0.30");
        }
    }

Let’s examine the method in detail. This is the first attribute.

    [BIAggregateQueryExpressionAttribute("FMAggregateMeasurements")]

This specifies that the calculations in the class refer to the aggregate measurement **FMAggregateMeasurement**. Notice that you can write a method expression class scoped to a specific aggregate measurement so that the expressions can be shared across KPIs, calculations, and other classes. Each method becomes an expression that can be referenced by value or the goal property of a KPI definition. Consider the following method.

    [BIAggregateQueryMethodExpression(extendedtypestr(AmountMST))]
    public static NumericExpression FMRevenuePerRentalMargin()
        {
            
            NumericExpression marginRatio = FMFleetMetodExpressions::RentalMarginRatio();
            NumericExpression calculation = new MeasureExpression("FMAggregateMeasurementpreview
    s/RevenuePerRental").Multiply( marginRatio);

            return calculation;
        }

The first line designates the EDT of the value returned by the method.

       [BIAggregateQueryMethodExpression(extendedtypestr(AmountMST))]

Notice that a method expression must always return a NumericExpression type. A NumericExpression is a super type that refers to a number that can be bound to a value or a goal expression in a KPI. The following line is the core of the calculation.

    MeasureExpression("FMAggregateMeasurements/RevenuePerRental").Multiply( marginRatio);

A MeasureExpression is an object that evaluates measures from an aggregate measurement defined in the AOT. A measure expression can be manipulated using common operators as well as using aggregate expressions.

### Define a new KPI using a pre-defined method expression

1.  You’ll define a KPI with a pre-defined method expression present in the class **FMRentalCalculations**. Select the project node. Right-click and select **Add**.
2.  Select **Analytics &gt; Key performance indicator** from the list of items. Provide **FMRevenuePerRentalMargin** as the name of the KPI.
3.  KPI designer will be displayed with the KPI **FMRevenuePerRentalMargin**.
4.  Select **FMRevenuePerRentalMargin**. Right-click and select properties. Specify following property values.
    |              |                        |
    |--------------|------------------------|
    | **Property** | **Value**              |
    | Measurement  | FMAggregateMeasurement |

5.  Select the **Value** node. Right-click and select properties. Enter following property values (you must enter them in the order shown below).
    |                        |                          |
    |------------------------|--------------------------|
    | **Property**           | **Value**                |
    | Value Type             | Based on Expression      |
    | Expression Class name  | FMRentalCalculations     |
    | Expression method name | FMRevenuePerRentalMargin |

6.  Define the expression for the KPI goal. Select the **Goal** node and specify the following properties.
    |              |              |
    |--------------|--------------|
    | **Property** | **Value**    |
    | Goal Type    | BasedOnValue |
    | Value        | 250          |

7.  Save the KPI definition. Build the project.
8.  You can preview the KPI definition.

## Create a count tile using a KPI definition
*Tiles* are user interface elements that can be defined as buttons to take the user to a different location in the product. In that regard, they are similar to menu item buttons. However, tiles can also display business data like counts and KPIs. You have the ability to draw KPI tile into different styles using properties defined within the KPI. Next, you’ll modify KPI properties so that it renders as a count tile.

### Modify KPI properties

1.  Select the KPI **FMRevenuePerRentalMargin** in Solution Explorer and double-click. KPI designer will be displayed with the KPI **FMRevenuePerRentalMargin**.
2.  Select **FMRevenuePerRentalMargin**. Right-click and select properties. Modify the following property values.
    |                       |           |
    |-----------------------|-----------|
    | **Property**          | **Value** |
    | Show Goal             | No        |
    | Show Status and Trend | No        |

3.  Save the KPI definition.

### Create a tile using the KPI definition

Next, you’ll create a tile using the KPI definition.

1.  Create a new tile. In Solution Explorer, right-click the project node, point to **Add**, and then click **New Item**.
2.  Select **Operations** **Artifacts** &gt; **User Interface** &gt; **Tile**.
3.  For the name, enter **FMRevenuePerRentalMarginTile**. This is the name of the tile that will be created. The name must be unique across tiles.
4.  Click **Add**. The new tile will appear in Visual Studio.
5.  Drag and drop the **FMRevenuePerRentalMargin** KPI definition from Solution Explorer onto the **FMRevenuePerRentalMarginTile** tile definition in the designer. This will automatically specify following properties:
    |              |                              |
    |--------------|------------------------------|
    | **Property** | **Value**                    |
    | Size         | Wide                         |
    | Label        | Margin on Revenue per Rental |
    | Type         | KPI                          |
    | KPI          | FMRevenuePerRentalMargin     |

6.  Save the tile definition.

### Modify the workspace by adding the newly created KPI tile to it

Now that you defined a KPI tile, you can put it in the interface so the user can take advantage of it. First, add it to a workspace that you want to extend.

1.  If you haven’t done so already, launch Application Explorer and locate **Fleet Management &gt; User Interface &gt; Forms &gt; FMClerkWorkspace**. Right-click and select **Add to current project**.
2.  In Solution Explorer, expand the Forms folder and then double-click **FMClerkWorkspace**.
3.  Decide where the KPI should appear in the workspace. For this tutorial, you’ll place it at the end of the first section (TabPage) of the panorama (Tab) on the form. This section is named TileContainer. Expand **FMClerkWorkspace &gt; **Design** &gt;**PanoramaBody (Tab)** &gt; **SummaryTileSection (TabPage)****.
4.  Right-click **SummaryTileSection**, point to **New**, and then click **Tile Button**.
5.  Specify the following values for the new tile button.
    |              |                              |
    |--------------|------------------------------|
    | **Property** | **Value**                    |
    | Name         | RevenuePerRentalKPITile      |
    | Tile         | FMRevenuePerRentalMarginTile |

6.  Save and rebuild the project
7.  Let’s run the form to see the tile we created above. Select the **FMClerkWorkspace** form in the Solution Explorer. Right-click and select **Set as startup project**.
8.  Click **Ctrl+F5** to run the form.
9.  You’ll see the modified workspace with the tile definition.

## Add a drillthru link from a KPI tile to a different form
KPI tiles drill-down to the **KPIDetails** form by default. So, unless you change the drill-thru destination within the KPI definition, KPI tiles will always take the user to the details page for that KPI. In this exercise, you’ll modify the default drill-thru destination.

1.  Select the KPI **FMRevenuePerRentalMargin** in Solution Explorer and double-click. KPI designer will be displayed with the KPI **FMRevenuePerRentalMargin.**
2.  Select **FMRevenuePerRentalMargin**. Right-click and select properties. Modify following property values.
    |                      |                      |
    |----------------------|----------------------|
    | **Property**         | **Value**            |
    | Drill thru Link type | Menu item            |
    | Menu item name       | FMReservationsReport |
    | Menu item type       | Display              |

3.  Save the KPI definition.
4.  Click **Ctrl+F5** to run the form.
5.  You’ll see the modified workspace with the tile definition. Click the tile.

## Preview the enriched workspace
After making the above modifications to the clerk workspace, you can reload the workspace to view the updated content. You can access the workspace from the newly created link in the navigation pane. Your updated workspace will show the added charts and KPI tile.

## Appendix
[]()

### Installing the demo data

To work with the sample, you must install the provided demo data.

1.  Open Internet Explorer, and go to your instance base URL.
    -   In the cloud environment, the base URL is obtained from LCS
    -   On a local VM, the base URL is [https://usnconeboxax1aos.cloud.onebox.dynamics.com](https://usnconeboxax1aos.cloud.onebox.dynamics.com/en/).

2.  Sign in.
3.  On the dashboard, scroll to the right, and in the **Fleet Management** section, click the **Fleet setup** tile.
4.  On the **Setup** form, click **Load demo data**.
5.  If you’re asked to reload the base data, click **Yes**.
6.  When the data is finished loading, click **Close**.
7.  Click **Show navigation pane** in the application bar. [![BI10](./media/bi10.png)](./media/bi10.png)
8.  Click on **App links**. [![BI11](./media/bi11.png)](./media/bi11.png)
9.  Click **System Administration** &gt; **Maintain aggregate measurements**. Select **FMAggregateMeasurements**.
10. On the application bar, click **Refresh now**. Wait until the processing completes. Processing is indicated at top of the page by a series of moving dots. The processing is completed when the indicator disappears.

 

