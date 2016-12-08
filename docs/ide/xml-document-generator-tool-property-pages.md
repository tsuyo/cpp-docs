---
title: "XML Document Generator Tool Property Pages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCXDCMakeTool.ValidateIntelliSense"
  - "VC.Project.VCXDCMakeTool.SuppressStartupBanner"
  - "VC.Project.VCXDCMakeTool.DocumentLibraryDependencies"
  - "VC.Project.VCXDCMakeTool.OutputDocumentFile"
  - "VC.Project.VCXDCMakeTool.AdditionalDocumentFiles"
dev_langs: 
  - "C++"
ms.assetid: 645912b5-197a-4c36-ba58-64df09444ca0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# XML Document Generator Tool Property Pages
The XML Document Generator Tool property page exposes the functionality of xdcmake.exe. xdcmake.exe merges .xdc files into an .xml file when your source code contains documentation comments and [/doc (Process Documentation Comments) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md) is specified,. See [Recommended Tags for Documentation Comments](../ide/recommended-tags-for-documentation-comments-visual-cpp.md) for information on adding documentation comments to source code.  
  
> [!NOTE]
>  xdcmake.exe options in the development environment (property pages) differ from the options when xdcmake.exe is used at the command line. For information on using xdcmake.exe at the command line, see [XDCMake Reference](../ide/xdcmake-reference.md).  
  
## UIElement List  
 **Suppress Startup Banner**  
 Suppress copyright message.  
  
 **Additional Document Files**  
 Additional directories in which you want the project system to look for .xdc files. xdcmake will always look for .xdc files generated by the project. Multiple directories can be specified.  
  
 **Output Document File**  
 The name and directory location of the .xml output file. See [Common Macros for Build Commands and Properties](../ide/common-macros-for-build-commands-and-properties.md) for information on using macros to specify directory locations.  
  
 **Document Library Dependencies**  
 If your project has a dependency on a .lib project in the solution, you can process .xdc files from the .lib project into the .xml files for the current project.  
  
## See Also  
 [Property Pages](../ide/property-pages-visual-cpp.md)   
 [Property Pages](../ide/property-pages-visual-cpp.md)