Use the **Formula designer** form to design and work with formula tree
structures. The designer graphically displays the formula structure. You can
select different configurations and decide what information to display on the
nodes of the tree.

| **Important**                                                                                                                                           |
|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| If you access the designer from the formula, it does not display route information, because the formula is not yet linked to a specific, finished item. |

  
Use the Designer tab

The **Designer** tab contains the following functionality:

-   A functions pane on the left part of the form that enables you to perform
    tasks such as to modify a formula version and to add formula items

-   A designer window that displays the tree structure of the formula

-   Current route information for the formula

-   A list of items

| **Note**                                                                                                                                                                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A site must be specified on the **Setup** tab. It must use either the default setting or one that you select. If the **Site** field is cleared, the tree does not display. If there are sub-formulas that use other sites, these do not display inside the tree. The tree displays only the information for one site at a time. |

The following table shows the actions that you can perform for each function in
the icon pane.

| **Function**                      | **Drag-and-drop**                               | **Click icon**   | **Right-click**      | **Double-click**               |
|-----------------------------------|-------------------------------------------------|------------------|----------------------|--------------------------------|
| Access information for the lines  | —-                                              | —-               | Line or formula      | —-                             |
| Add item                          | Formula                                         | Calculation      | —-                   | Item                           |
| Formula calculation               | —-                                              | Calculation      | Formula              | —-                             |
| Check Formula                     | —-                                              | —-               | Formula              | —-                             |
| Configuration (create/select)     | —-                                              | —-               | Configurable formula | —-                             |
| Configurations included in (view) | —-                                              | —-               | Configurable formula | —-                             |
| Configure                         | —-                                              | —-               | Configurable formula | —-                             |
| Copy lines within tree            | Copy to location. Press CTRL, and drag-and-drop | —-               | —-                   | —-                             |
| Create/Edit Formula versions      | —-                                              | Formula versions | Formula              | —-                             |
| Create/Edit route versions        | —-                                              | Route versions   | Formula              | —-                             |
| Delete                            | —-                                              | Delete record    | Line or formula      | —-                             |
| Edit line                         | —-                                              | Edit             | Line or formula      | Line                           |
| Link to operation                 | Operation number                                | —-               | —-                   | Line – insert operation number |
| Lock/Unlock route                 | —-                                              | —-               | Line or formula      | —-                             |
| Move lines within tree            | New locations                                   | —-               | —-                   | —-                             |
| Print Formula                     | —-                                              | Print            | Formula              | —-                             |
| Reload Formula                    | —-                                              | —-               | Formula              | —-                             |
| Reload route                      | —-                                              | —-               | Formula              | —-                             |
| Remove link to operation          | —-                                              | —-               | Line or formula      | Line – Delete operation number |

  
Use the Setup tab

Use the **Setup** tab to customize the information that is shown on
the **Designer** form.

| **Field group**     | **Field**             | **Description**                                                                                                                                                                                                                              |
|---------------------|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Search criteria** | **Display principle** | Select the version-display principle that applies to the current formula structure and the current route.                                                                                                                                    |
| —-                  | **Version date**      | Enter the version date for the formula and route. The version is used to identify which formula version to use on a specific date, as determined by the version dates in the formula-version setup.                                          |
| **Lines**           | **Show valid only**   | When the check box is selected, only formula lines that have valid dates are displayed in the tree structure. To open the **Edit formula line** form and view the validity dates for the formula line, right-click or double-click the line. |
| **Formula**         | All check-box fields  | Select the criteria to display in the tree structure. The designer displays the selected criteria at the bottom of both tabs.                                                                                                                |
| **Route**           | All check-box fields  | Select the criteria to display for the routes.                                                                                                                                                                                               |

-   When the principle is set to **Active** or **Selected/Active**, the valid
    formula or route version for this date is found.

-   The date is also used to find valid formula lines if **Show valid only** is
    selected.

  
See also

Formula designer (form)
