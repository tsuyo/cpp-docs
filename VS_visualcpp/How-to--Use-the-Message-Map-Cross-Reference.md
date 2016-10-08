---
title: "How to: Use the Message-Map Cross-Reference"
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
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: 9
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
# How to: Use the Message-Map Cross-Reference
In entries labeled <memberFxn\>, write your own member function for a derived [CWnd](../VS_visualcpp/CWnd-Class.md) class. Give your function any name you like. Other functions, such as `OnActivate`, are member functions of class `CWnd`. If called, they pass the message to the `DefWindowProc` Windows function. To process Windows notification messages, override the corresponding `CWnd` function in your derived class. Your function should call the overridden function in your base class to let the base class and Windows respond to the message.  
  
 In all cases, put the function prototype in the `CWnd`-derived class header, and code the message map entry as shown.  
  
 The following terms are used:  
  
|Term|Definition|  
|----------|----------------|  
|id|Any user-defined menu item ID (**WM_COMMAND** messages) or control ID (child window notification messages).|  
|"message" and "wNotifyCode"|Windows message IDs as defined in WINDOWS.H.|  
|nMessageVariable|Name of a variable that contains the return value from the **RegisterWindowMessage** Windows function.|  
  
## See Also  
 [Message Maps](../VS_visualcpp/Message-Maps--MFC-.md)