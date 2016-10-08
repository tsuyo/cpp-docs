---
title: "lgamma Function"
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
ms.assetid: 05c2b608-77a0-4100-a977-2b5227e688b3
caps.latest.revision: 9
manager: ghogen
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
# lgamma Function
Computes the natural logarithm of the absolute value of gamma of the argument  
  
## Syntax  
  
```  
inline float lgamma(  
    float _X,  
    _Out_ int * _Sign ) restrict(amp);  
  
inline double lgamma(  
    double _X,  
    _Out_ int * _Sign ) restrict(amp);  
```  
  
#### Parameters  
 `_X`  
 Floating-point value  
  
 `_Sign`  
 Returns the sign  
  
## Return Value  
 Returns the natural logarithm of the absolute value of gamma of the argument  
  
## Requirements  
 **Header:** amp_math.h  
  
 **Namespace:** Concurrency::precise_math  
  
## See Also  
 [Concurrency::precise_math Namespace](../VS_visualcpp/Concurrency--precise_math-Namespace.md)