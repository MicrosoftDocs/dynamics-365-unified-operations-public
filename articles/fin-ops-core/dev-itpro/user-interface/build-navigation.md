---
title: Build navigation
description: Learn about build navigation, including key concepts and outlines on setups and overviews on various workspaces.
author: jasongre
ms.author: jasongre
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/09/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: ad8ba47b-becb-4d13-a5af-8aca46075e82
---

# Build navigation

[!include [banner](../includes/banner.md)]

In this tutorial, you add navigational elements to a workspace and the navigation pane.

## Prerequisites

For this tutorial, you need to access the environment by using Remote Desktop, and be provisioned as an administrator on the instance. For more information, see [Access Instances](../dev-tools/access-instances.md).

## Key concepts

- A *workspace* is an overview page that's specific to a particular subject area. All users share workspaces. In this tutorial, you add content into an existing workspace.
- The *dashboard* is the default home page for each user.
- *Tiles* are securable objects that you can show on a workspace or the dashboard. You can secure them by using menu items.

## Setup

If this tutorial is the first tutorial that you're working on, review [Access Instances](../dev-tools/access-instances.md) and make sure that you provision your administrator user if you're working on a local VM.

### Import the tutorial project

If you already imported the Fleet management tutorial project, go to the next section.

1. Download the Fleet Management sample from <https://github.com/Microsoft/FMLab>, save it to **C:\\**, and unzip it.
1. In Visual Studio, on the **Finance and operations** menu, select **Import Project**.
1. In **Import Project**, next to the **Filename** text box, select the ellipsis button.
1. In **Select the file to import**, browse to **C:\FMLab**, select **FMTutorialDataModel.axpp**, and then select **Open**.
1. In the **Project file location** text box, enter **C:\FMLab**.
1. Select the **Overwrite Elements** option, and then select **OK**.

### Import transactional data

1. In Visual Studio, open the **FMTutorial** project. On the **File** menu, point to **Open**, and then select **Project/Solution**.
1. In **Open Project**, browse to `C:\FMLab\FMTutorial`, and then select `FMTutorial`. Select **Open**. The **FMTutorial** project appears in **Solution Explorer**.
1. Use the `FMTDataHelper` class to load data for the Fleet Management tutorial. In **Solution Explorer**, in the **FMTutorial** project, expand **Classes**, right-click **FMTDataHelper**, and then select **Set as Startup Object**.
1. From the **BUILD** menu, select **Rebuild Solution**. You use the rebuild to update the timestamps of the imported artifacts. You can view the build progress in the **Output** window.
1. Press **Ctrl+F5** to run the project and load the data.

## Add a tile to the tutorial workspace

First, add a new tile to the form `FMTClerkWorkspace`.

1. In **Solution Explorer**, expand **Forms** and then double-click `FMTClerkWorkspace`.
1. In the designer, expand **PanoramaBody**.
1. Right-click **TileContainer**, and then select **New** > **Tile Button**.
1. Specify the following properties for the new tile button.

    | **Property** | **Value**           |
    |--------------|---------------------|
    | Text         | Test tile           |
    | Tile         | FMTAllCustomersTile |

    This tile duplicates the existing **All customers** tile.
1. In **Solution Explorer**, select **Forms** > `FMTClerkWorkspace`. Right-click the form, and then select **Set as Start-up Object**. You need to set a start-up object so Visual Studio can launch when you press **Ctrl+F5** in step 7. When you set this form as the start-up object, the work-in-progress Fleet management clerk workspace appears after you press **Ctrl+F5**. You preview this form again later in detail.
1. Right-click `FMTutorial`, and then select **Rebuild**.
1. Press **Ctrl+F5** to run the project.

After you build and run the project, the Fleet management clerk workspace launches. The new tile named **Test tile** that you created appears in the first section of the workspace, at the end of the set of tiles.

:::image type="content" source="./media/nav1.png" alt-text="Screenshot of set of tiles.":::

> [!NOTE]
> The tile doesn't navigate anywhere when clicked. To enable this behavior, define a **Menu Item Name** on `FMTAllCustomersTile` under **Tiles** in **Solution Explorer**.

## Add a new workspace to the navigation pane

Next, add the FMTClerkWorkspace form to the navigation pane. Add it in two locations:

- The **All workspaces** list.
- A new item in the area list containing a menu structure that shows the workspace.

### Create a menu item that points to the FMTClerkWorkspace workspace

1. Right-click **FMTutorial**, point to **Add**, and then click **New Item**.
1. Select **AX Artifacts** > **User Interface** > **Display Menu Item**. In the **Name** property, enter **FMTClerkWorkspace**.
1. Select **Add**.
1. Specify the following properties for the new menu item.

    | **Property** | **Value**                       |
    |--------------|---------------------------------|
    | Label        | Reservation management tutorial |
    | Object       | FMTClerkWorkspace               |

### Create a tile that points to the FMTClerkWorkspace workspace menu item

1. Right-click **FMTutorial**, point to **Add**, and then click **New Item**.
1. Select **AX Artifacts** > **User Interface** > **Tile**. In the **Name** property, enter **FMTClerkWorkspace**.
1. Select **Add**.
1. Specify the following properties for the new tile.

    | **Property** | **Value**         |
    |--------------|-------------------|
    | MenuItemName | FMTClerkWorkspace |

### Add a menu extension for the navigation pane

1. In **Application Explorer**, select **User Interface** > **Menus**. Right-click **NavPaneMenu**, and then select **Create extension**.
1. In **Solution Explorer**, double-click **NavPaneMenu.Extension**.
1. In the designer, right-click **NavPaneMenu.Extension**, point to **New**, and then select **Submenu**.
1. Select the new submenu. In the **Name** property, enter **NavPaneMenuFleetTutorial**.
1. In **Solution Explorer** or **Application Explorer**, locate the **FMTClerkWorkspace** tile, and drag it onto the newly created submenu. Select **Save**.
1. Right-click `FMTutorial`, and then select **Rebuild**.
1. Press **Ctrl+F5** to run the project. After you build and run the project, the navigation pane contains a link to the new workspace. Open the navigation pane by selecting the navigation pane button (three lines) at the top right of the application window.
1. When you open the navigation pane, select **All workspaces**, and scroll down in the list after it opens. You see the following new Reservation management tutorial workspace in the list.

### Add the form to the main menu structure

Now you add a new main menu section that contains a tile that points to the tutorial workspace. You then add a link to the same form in this section. This section demonstrates the appearance of a non-workspace form link.

1. In Visual Studio, in **Solution Explorer**, right-click **FMTutorial**, point to **Add**, and then click **New Item**.
1. Select **AX Artifacts** > **User Interface** > **Menu**. In the **Name** property, enter **FleetManagementTutorial**.
1. Click **Add**.
1. In **Solution Explorer**, double-click the new menu **FleetManagementTutorial** if it isn't already open.
1. In the properties list, set the **Label** property to **Fleet management tutorial**.
1. In the designer, right-click **FleetManagementTutorial**, and click **New** > **Submenu**.
1. Specify the following properties for the new submenu.

    | **Property** | **Value**  |
    |--------------|------------|
    | Name         | Workspaces |
    | Label        | Workspaces |

1. In **Solution Explorer** or **Application Explorer**, locate the **FMTClerkWorkspace** display menu item and drag it onto the new **Workspaces** submenu.
1. In the designer, right-click **FleetManagementTutorial**, and then click **New** > **Submenu**.
1. Specify the following properties for the new submenu.

    | **Property** | **Value** |
    |--------------|-----------|
    | Name         | Common    |
    | Label        | Common    |

1. In **Solution Explorer** or **Application Explorer**, locate the **FMTClerkWorkspace** display menu item and drag it onto the new **Common** submenu.
1. In **Application Explorer**, select **User Interface** > **Menus** > **MainMenu**. Right-click **MainMenu**, and then click **Create extension**.
1. In **Solution Explorer**, locate and open the new extension. Select and double-click **MainMenu.Extension** to open it.
1. In the designer, right click **MainMenu.Extension**, point to **New**, and then click **Menu reference**.
1. Specify the following properties for the new menu reference.

    | **Property** | **Value**               |
    |--------------|-------------------------|
    | Name         | FleetManagementTutorial |
    | Menu Name    | FleetManagementTutorial |

1. Select **Save**.
1. Right-click **FMTutorial**, and then click **Build**.
1. Press **Ctrl+F5** to run the project.
1. Go to the main menu section you just modified. Open the navigation pane and scroll down until you see the new top-level **Fleet management tutorial** menu. You might need to clear your browser cache by pressing **Ctrl+F5**.
1. Select **Fleet management tutorial** > **Workspaces** to expand that submenu. Your navigation pane should look like the following image.

    If you select the **Common** submenu, you see the menu item that you modeled there. You can select either of these links to check that you set up the references correctly. If you set up the references correctly, the tutorial workspace you’re working on opens when selected.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
