---
title: "for Statement (C++)"
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
ms.topic: language-reference
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
caps.latest.revision: 15
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
# for Statement (C++)
Executes a statement repeatedly until the condition becomes false. For information on the range-based for statement, see [Range-based for Statement (C++)](../VS_visualcpp/Range-based-for-Statement--C---.md).  
  
## Syntax  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## Remarks  
 Use the `for` statement to construct loops that must execute a specified number of times.  
  
 The `for` statement consists of three optional parts, as shown in the following table.  
  
### for Loop Elements  
  
|Syntax Name|When Executed|Description|  
|-----------------|-------------------|-----------------|  
|`init-expression`|Before any other element of the **for** statement, `init-expression` is executed only once. Control then passes to `cond-expression`.|Often used to initialize loop indices. It can contain expressions or declarations.|  
|`cond-expression`|Before execution of each iteration of `statement`, including the first iteration. `statement` is executed only if `cond-expression` evaluates to true (nonzero).|An expression that evaluates to an integral type or a class type that has an unambiguous conversion to an integral type. Normally used to test for loop-termination criteria.|  
|`loop-expression`|At the end of each iteration of `statement`. After `loop-expression` is executed, `cond-expression` is evaluated.|Normally used to increment loop indices.|  
  
 The following examples show different ways to use the `for` statement.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    // The counter variable can be declared in the init-expression.  
    for (int i = 0; i < 2; i++ ){   
       cout << i;  
    }  
    // Output: 01  
    // The counter variable can be declared outside the for loop.  
    int i;  
    for (i = 0; i < 2; i++){  
        cout << i;  
    }  
    // Output: 01  
    // These for loops are the equivalent of a while loop.  
    i = 0;  
    while (i < 2){  
        cout << i++;  
    }  
}  
    // Output: 012  
```  
  
 `init-expression` and `loop-expression` can contain multiple statements separated by commas. For example:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
    int i, j;  
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {  
        cout << "i + j = " << (i + j) << '\n';  
    }  
}  
    // Output:  
    i + j = 15  
    i + j = 17  
    i + j = 19  
```  
  
 `loop-expression` can be incremented or decremented, or modified in other ways.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
for (int i = 10; i > 0; i--) {  
        cout << i << ' ';  
    }  
    // Output: 10 9 8 7 6 5 4 3 2 1  
    for (int i = 10; i < 20; i = i+2) {  
        cout << i << ' ';  
    }  
    // Output: 10 12 14 16 18  
```  
  
 A `for` loop terminates when a [break](../VS_visualcpp/break-Statement--C---.md), [return](../VS_visualcpp/return-Statement--C---.md), or [goto](../VS_visualcpp/goto-Statement--C---.md) (to a labeled statement outside the **for** loop) within `statement` is executed. A [continue](../VS_visualcpp/continue-Statement--C---.md) statement in a `for` loop terminates only the current iteration.  
  
 If `cond-expression` is omitted, it is considered true and the **for** loop will not terminate without a `break`, `return`, or `goto` within `statement`.  
  
 Although the three fields of the `for` statement are normally used for initialization, testing for termination, and incrementing, they are not restricted to these uses. For example, the following code prints the numbers 0 through 4. In this case, `statement` is the null statement:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    int i;  
    for( i = 0; i < 5; cout << i << '\n', i++){  
        ;  
    }  
}  
```  
  
## for Loops and the C++ Standard  
 The C++ standard says that a variable declared in a `for` loop shall go out of scope after the `for` loop ends. For example:  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 By default, under [/Ze](../VS_visualcpp/-Za---Ze--Disable-Language-Extensions-.md), a variable declared in a `for` loop remains in scope until the `for` loop's enclosing scope ends.  
  
 [/Zc:forScope](../VS_visualcpp/-Zc-forScope--Force-Conformance-in-for-Loop-Scope-.md) enables standard behavior of variables declared in for loops without needing to specify /Za.  
  
 It is also possible to use the scoping differences of the `for` loop to redeclare variables under /Ze as follows:  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 This more closely mimics the standard behavior of a variable declared in a `for` loop, which requires variables declared in a `for` loop to go out of scope after the loop is done. When a variable is declared in a `for` loop, the compiler internally promotes it to a local variable in the `for` loop's enclosing scope even if there is already a local variable with the same name.  
  
## See Also  
 [Iteration Statements](../VS_visualcpp/Iteration-Statements--C---.md)   
 [Keywords](../VS_visualcpp/Keywords--C---.md)   
 [while Statement (C++)](../VS_visualcpp/while-Statement--C---.md)   
 [do-while Statement (C++)](../VS_visualcpp/do-while-Statement--C---.md)   
 [Range-based for Statement (C++)](../VS_visualcpp/Range-based-for-Statement--C---.md)