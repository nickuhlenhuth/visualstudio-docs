---
title: "Run UWP apps on the local machine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
  - "VB"
  - "FSharp"
  - "C++"
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: ghogen
ms.workload: 
  - "uwp"
---
# Run UWP apps on the local machine
![Applies to Windows only](../debugger/media/windows_only_content.png "windows_only_content")  
  
 To debug, test, or run performance analysis on a UWP app, you can run the app on the same machine that hosts Visual Studio. If the display on the device is touch-enabled, you can exercise the full functionality of the app; otherwise, you will be limited to mouse and keyboard gestures.  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> How to run on a local machine  
 To run the app on the local machine, select **Local Machine** from the drop-down list next to the Start Debugging button on the debugger **Standard** toolbar.  
  
 ![Run on Local Machine](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 If you can't see the **Standard** toolbar, click the **View** menu, point to **Toolbars**, and then click **Standard**.  
  
 The choice you make in the drop-down list is persisted in the project properties file and becomes the default run target.  
  
 You can also set the run target directly in the project properties file. Right-click the project name in **Solution Explorer** and then choose **Properties**. Then do one of the following:  
  
-   In C# and Visual Basic projects, click **Debug** and then select **Local Machine** from the **Target Device** drop-down list.  
  
     ![C&#35; and Visual Basic project property page](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   In C++ and JavaScript projects, expand the **Configuration Properties** node, click **Debugging**, and then select **Local Debugger** from the **Debugger to launch** list.  
  
     ![C&#43;&#43; and JavaScript project properties page](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  