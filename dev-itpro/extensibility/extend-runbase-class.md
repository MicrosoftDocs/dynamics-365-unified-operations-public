---
# required metadata

title: Extend the RunBase class
description: This topic contains an example that shows how a RunBase class can be augmented end to end.
author: robinarh
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinarh
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 8DA4DA85-0C2D-4CAF-B350-DAC9C1BE4DF9
ms.search.region: Global
# ms.search.industry: 
ms.author: pvillads
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Extend the RunBase class

[!include[banner](../includes/banner.md)]


When you extend functionality of the application suite, you will encounter classes that extend the **RunBase** class. This topic shows how a **RunBase** class can be augmented end to end.

For example, you want to extend the SysUserLogCleanup class. Out of the box, this class can delete records from the SysUserLog table. However, you want to archive these records to a different table before they are deleted.

The SysUserLogCleanup class is a **RunBase** class. The **RunBase** class has a dialog box, where the user is prompted for parameters before the class is run. For this example, we will add a toggle button control to the dialog box, get the value of the control, act on the value in the run method, and make sure that the value is serialized via the pack and unpack methods. Serialization helps guarantee that the user’s last selection is presented again if the dialog box is reopened. It also helps guarantee that the settings are applied if the class is run in the background.

To avoid collisions with other eventual extensions, we followed these best practices:

- **Prefix members and methods**. In the example, the prefix “my” is used. This practice is important, because it helps prevent name clashes with other extensions and future versions of the augmented class.

- **Use RunBase.packExtension() and RunBase.unpackExtension()**. These methods provide serialization in a nonintrusive manner. They enable serialization of multiple extensions of the same class. The methods are available starting in Platform Update 5.

The following example shows how to implement this scenario.

<pre>
[ExtensionOf(classStr(SysUserLogCleanup))]
final class MySysUserLogCleanup_Extension
{
    // static members
    static private SysUserLogCleanup myRunningInstance;

    // Extending class state...
    private boolean myArchive;
    private DialogField myDialogArchive;
    #define.CurrentVersion(1)
    #localmacro.CurrentList
        myArchive
    #endmacro

    // Adding new instance methods
    private void myDialog(Dialog _dialog)
    {
        myDialogArchive = _dialog.addField(extendedtypestr(NoYesId), "Archive");
        myDialogArchive.value(myArchive);
    }
    private void myGetFromDialog()
    {
        myArchive = myDialogArchive.value();
    }
    private boolean myUnpack(container packedClass)
    {
        Integer version = RunBase::getVersion(packedClass);
        switch (version)
        {
            case #CurrentVersion:
                [version, #currentList] = packedClass;
                break;
            default:
                return false;
        }
        return true;
    }
    private container myPack()
    {
        return [#CurrentVersion, #CurrentList];
    }
    private void myInitParmDefault()
    {
        myArchive = true;
    }
    private void myArchiveUserLog(SysUserLog _userLog)
    {
        if (myArchive)
        {
            //...
        }
    }

    // Wiring up event handlers...
    [PostHandlerFor(classStr(SysUserLogCleanup), methodStr(SysUserLogCleanup, dialog))]
    public static void SysUserLogCleanup_Post_Dialog(XppPrePostArgs _args)
    {
        Dialog dialog = _args.getReturnValue();
        SysUserLogCleanup instance = _args.getThis() as SysUserLogCleanup;
        instance.myDialog(dialog);
    }
    [PostHandlerFor(classStr(SysUserLogCleanup), methodStr(SysUserLogCleanup, getFromDialog))]
    public static void SysUserLogCleanup_Post_GetFromDialog(XppPrePostArgs _args)
    {
        SysUserLogCleanup instance = _args.getThis() as SysUserLogCleanup;
        instance.myGetFromDialog();
    }
    [PostHandlerFor(classStr(SysUserLogCleanup), methodStr(SysUserLogCleanup, pack))]
    public static void SysUserLogCleanup_Post_pack(XppPrePostArgs _args)
    {
        SysUserLogCleanup instance = _args.getThis() as SysUserLogCleanup;
        //Also pack the extension
        instance.packExtension(_args, classStr(MySysUserLogCleanup_Extension), instance.myPack());
    }
    [PostHandlerFor(classStr(SysUserLogCleanup), methodStr(SysUserLogCleanup, unpack))]
    public static void SysUserLogCleanup_Post_unpack(XppPrePostArgs _args)
    {
        SysUserLogCleanup instance = _args.getThis() as SysUserLogCleanup;
        container myState = instance.unpackExtension(_args, classStr(MySysUserLogCleanup_Extension));
        //Also unpack the extension
        if (!instance.myUnpack(myState))
        {
            //Extension couldn't be unpacked - return false to trigger initParmDefault() gets called
            _args.setReturnValue(false);
        }
    }
    [PostHandlerFor(classStr(SysUserLogCleanup), methodStr(SysUserLogCleanup, initParmDefault))]
    public static void SysUserLogCleanup_Post_initParmDefault(XppPrePostArgs _args)
    {
        SysUserLogCleanup instance = _args.getThis() as SysUserLogCleanup;
        instance.myInitParmDefault();
    }
    [PreHandlerFor(classStr(SysUserLogCleanup), methodStr(SysUserLogCleanup, run))]
    public static void SysUserLogCleanup_Pre_run(XppPrePostArgs _args)
    {
        //Store a static reference, so we can call it from SysUserLog_onDeleting.
        myRunningInstance = _args.getThis() as SysUserLogCleanup;
    }
    [PostHandlerFor(classStr(SysUserLogCleanup), methodStr(SysUserLogCleanup, run))]
    public static void SysUserLogCleanup_Post_run(XppPrePostArgs _args)
    {
        //Running complete 
        myRunningInstance = null;
    }

    // Wiring up event handler for deletion of the record
    [DataEventHandler(tableStr(SysUserLog), DataEventType::Deleting)]
    static public void SysUserLog_onDeleting(Common _sender, DataEventArgs _e)
    {
        if (runningInstance)
        {
            myRunningInstance.myArchiveUserLog(_sender as SysUserLog);
        }
    }
}
</pre>


