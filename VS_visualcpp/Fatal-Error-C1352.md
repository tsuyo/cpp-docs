---
title: "Fatal Error C1352"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-csharp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
caps.latest.revision: 7
manager: douge
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# Fatal Error C1352
Invalid or corrupt MSIL in function 'function' from module 'file'  
  
 A .netmodule was passed to the compiler, but the compiler detected corruption in the file.  Ask the person who produced the .netmodule to investigate.  
  
 The compiler does not check .netmodule files for all types of corruption.  It does, however, check that all control paths in a function contain a return statement.  
  
 For more information, see [.netmodule Files as Linker Input](../VS_visualcpp/.netmodule-Files-as-Linker-Input.md).