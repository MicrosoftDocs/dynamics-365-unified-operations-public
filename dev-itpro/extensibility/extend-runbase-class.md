
# Extend the RunBase class

When you extend functionality of the application suite, you will encounter classes that extend the **RunBase** class. This topic shows how a **RunBase** class can be augmented end to end.

For example, you want to extend the SysUserLogCleanup class. Out of the box, this class can delete records from the SysUserLog table. However, you want to archive these records to a different table before they are deleted.

The SysUserLogCleanup class is a **RunBase** class. The **RunBase** class has a dialog box, where the user is prompted for parameters before the class is run. For this example, we will add a toggle button control to the dialog box, get the value of the control, act on the value in the run method, and make sure that the value is serialized via the pack and unpack methods. Serialization helps guarantee that the user’s last selection is presented again if the dialog box is reopened. It also helps guarantee that the settings are applied if the class is run in the background.

To avoid collisions with other eventual extensions, we followed these best practices:

- **Prefix members and methods. In the example, the prefix “my” is used. This practice is important, because it helps prevent name clashes with other extensions and future versions of the augmented class.**

- **Use RunBase.packExtension() and RunBase.unpackExtension()**. These methods provide serialization in a nonintrusive manner. They enable serialization of multiple extensions of the same class. The methods are available starting in Platform Update 5.

The following example shows how to implement this scenario.
