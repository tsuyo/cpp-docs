---
title: "How to: Debug a Release Build"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d333e4d1-4e6c-4384-84a9-cb549702da25
caps.latest.revision: 7
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# How to: Debug a Release Build
You can debug a release build of an application.  
  
### To debug a release build  
  
1.  Open the **Property Pages** dialog box for the project. For details, see [Working with Project Properties](../VS_visualcpp/Working-with-Project-Properties.md).  
  
2.  Click the **C/C++** node. Set **Debug Information Format** to [C7 compatible (/Z7)](../VS_visualcpp/-Z7---Zi---ZI--Debug-Information-Format-.md) or **Program Database (/Zi)**.  
  
3.  Expand **Linker** and click the **General** node. Set **Enable Incremental Linking** to [No (/INCREMENTAL:NO)](../VS_visualcpp/-INCREMENTAL--Link-Incrementally-.md).  
  
4.  Select the **Debugging** node. Set **Generate Debug Info** to [Yes (/DEBUG)](../VS_visualcpp/-DEBUG--Generate-Debug-Info-.md).  
  
5.  Select the **Optimization** node. Set **References** to [/OPT:REF](../VS_visualcpp/-OPT--Optimizations-.md) and **Enable COMDAT Folding** to [/OPT:ICF](../VS_visualcpp/-OPT--Optimizations-.md).  
  
6.  You can now debug your release build application. To find a problem, step through the code (or use Just-In-Time debugging) until you find where the failure occurs, and then determine the incorrect parameters or code.  
  
     If an application works in a debug build, but fails in a release build, one of the compiler optimizations may be exposing a defect in the source code. To isolate the problem, disable selected optimizations for each source code file until you locate the file and the optimization that is causing the problem. (To expedite the process, you can divide the files into two groups, disable optimization on one group, and when you find a problem in a group, continue dividing until you isolate the problem file.)  
  
     You can use [/RTC](../VS_visualcpp/-RTC--Run-Time-Error-Checks-.md) to try to expose such bugs in your debug builds.  
  
     For more information, see [Optimizing Your Code](../VS_visualcpp/Optimizing-Your-Code.md).  
  
## See Also  
 [Fixing Release Build Problems](../VS_visualcpp/Fixing-Release-Build-Problems.md)