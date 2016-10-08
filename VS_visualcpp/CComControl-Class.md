---
title: "CComControl Class"
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
ms.topic: reference
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: 16
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
# CComControl Class
This class provides methods for creating and managing ATL controls.  
  
> [!IMPORTANT]
>  This class and its members cannot be used in applications that execute in the Windows Runtime.  
  
## Syntax  
  
```  
template <  
    class T,  
    class WinBase = CWindowImpl< T  
   > >  
    class ATL_NO_VTABLE CComControl :  
    public CComControlBase, public WinBase;  
```  
  
#### Parameters  
 `T`  
 The class implementing the control.  
  
 *WinBase*  
 The base class that implements windowing functions. Defaults to [CWindowImpl](../VS_visualcpp/CWindowImpl-Class.md).  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CComControl::CComControl](../Topic/CComControl::CComControl.md)|Constructor.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](../Topic/CComControl::ControlQueryInterface.md)|Retrieves a pointer to the requested interface.|  
|[CComControl::CreateControlWindow](../Topic/CComControl::CreateControlWindow.md)|Creates a window for the control.|  
|[CComControl::FireOnChanged](../Topic/CComControl::FireOnChanged.md)|Notifies the container's sink that a control property has changed.|  
|[CComControl::FireOnRequestEdit](../Topic/CComControl::FireOnRequestEdit.md)|Notifies the container's sink that a control property is about to change and that the object is asking the sink how to proceed.|  
|[CComControl::MessageBox](../Topic/CComControl::MessageBox.md)|Call this method to create, display, and operate a message box.|  
  
## Remarks  
 `CComControl` is a set of useful control helper functions and essential data members for ATL controls. When you create a standard control or a DHTML control using the ATL Control Wizard, the wizard will automatically derive your class from `CComControl`. `CComControl` derives most of its methods from [CComControlBase](../VS_visualcpp/CComControlBase-Class.md).  
  
 For more information about creating a control, see the [ATL Tutorial](../VS_visualcpp/Active-Template-Library--ATL--Tutorial.md). For more information about the ATL Project Wizard, see the article [Creating an ATL Project](../VS_visualcpp/Creating-an-ATL-Project.md).  
  
 For a demonstration of `CComControl` methods and data members, see the [CIRC](../VS_visualcpp/Visual-C---Samples.md) sample.  
  
## Inheritance Hierarchy  
 `WinBase`  
  
 [CComControlBase](../VS_visualcpp/CComControlBase-Class.md)  
  
 `CComControl`  
  
## Requirements  
 **Header:** atlctl.h  
  
##  <a name="ccomcontrol__ccomcontrol"></a>  CComControl::CComControl  
 The constructor.  
  
```  
CComControl();  
```  
  
### Remarks  
 Calls the [CComControlBase](../Topic/CComControlBase::CComControlBase.md) constructor, passing the `m_hWnd` data member inherited through [CWindowImpl](../VS_visualcpp/CWindowImpl-Class.md).  
  
##  <a name="ccomcontrol__controlqueryinterface"></a>  CComControl::ControlQueryInterface  
 Retrieves a pointer to the requested interface.  
  
```  
virtual HRESULT ControlQueryInterface(  
    const IID& iid,  
    void** ppv );  
```  
  
### Parameters  
 `iid`  
 [in] The GUID of the interface being requested.  
  
 `ppv`  
 [out] A pointer to the interface pointer identified by `iid`, or **NULL** if the interface is not found.  
  
### Remarks  
 Only handles interfaces in the COM map table.  
  
### Example  
 [!CODE [NVC_ATL_COM#15](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_COM#15)]  
  
##  <a name="ccomcontrol__createcontrolwindow"></a>  CComControl::CreateControlWindow  
 By default, creates a window for the control by calling `CWindowImpl::Create`.  
  
```  
virtual HWND CreateControlWindow(  
    HWND hWndParent,  
    RECT& rcPos );  
```  
  
### Parameters  
 `hWndParent`  
 [in] Handle to the parent or owner window. A valid window handle must be supplied. The control window is confined to the area of its parent window.  
  
 `rcPos`  
 [in] The initial size and position of the window to be created.  
  
### Remarks  
 Override this method if you want to do something other than create a single window, for example, to create two windows, one of which becomes a toolbar for your control.  
  
### Example  
 [!CODE [NVC_ATL_COM#16](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_COM#16)]  
  
##  <a name="ccomcontrol__fireonchanged"></a>  CComControl::FireOnChanged  
 Notifies the container's sink that a control property has changed.  
  
```  
HRESULT FireOnChanged(    DISPID dispID );  
```  
  
### Parameters  
 *dispID*  
 [in] Identifier of the property that has changed.  
  
### Return Value  
 One of the standard HRESULT values.  
  
### Remarks  
 If your control class derives from [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), this method calls [CFirePropNotifyEvent::FireOnChanged](../Topic/CFirePropNotifyEvent::FireOnChanged.md) to notify all connected `IPropertyNotifySink` interfaces that the specified control property has changed. If your control class does not derive from `IPropertyNotifySink`, this method returns `S_OK`.  
  
 This method is safe to call even if your control doesn't support connection points.  
  
### Example  
 [!CODE [NVC_ATL_COM#17](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_COM#17)]  
  
##  <a name="ccomcontrol__fireonrequestedit"></a>  CComControl::FireOnRequestEdit  
 Notifies the container's sink that a control property is about to change and that the object is asking the sink how to proceed.  
  
```  
HRESULT FireOnRequestEdit(    DISPID dispID );  
```  
  
### Parameters  
 *dispID*  
 [in] Identifier of the property about to change.  
  
### Return Value  
 One of the standard HRESULT values.  
  
### Remarks  
 If your control class derives from [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), this method calls [CFirePropNotifyEvent::FireOnRequestEdit](../Topic/CFirePropNotifyEvent::FireOnRequestEdit.md) to notify all connected `IPropertyNotifySink` interfaces that the specified control property is about to change. If your control class does not derive from `IPropertyNotifySink`, this method returns `S_OK`.  
  
 This method is safe to call even if your control doesn't support connection points.  
  
### Example  
 [!CODE [NVC_ATL_COM#18](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_COM#18)]  
  
##  <a name="ccomcontrol__messagebox"></a>  CComControl::MessageBox  
 Call this method to create, display, and operate a message box.  
  
```  
int MessageBox(  
    LPCTSTR lpszText,  
    LPCTSTR lpszCaption = _T(""),  
    UINT nType = MB_OK  
   );  
```  
  
### Parameters  
 `lpszText`  
 The text to be displayed in the message box.  
  
 `lpszCaption`  
 The dialog box title. If NULL (the default), the title "Error" is used.  
  
 `nType`  
 Specifies the contents and behavior of the dialog box. See the [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) entry in the Windows SDK documentation for a list of the different message boxes available. The default provides a simple **OK** button.  
  
### Return Value  
 Returns an integer value specifying one of the menu-item values listed under [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) in the Windows SDK documentation.  
  
### Remarks  
 `MessageBox` is useful both during development and as an easy way to display an error or warning message to the user.  
  
## See Also  
 [CWindowImpl Class](../VS_visualcpp/CWindowImpl-Class.md)   
 [Class Overview](../VS_visualcpp/ATL-Class-Overview.md)   
 [CComControlBase Class](../VS_visualcpp/CComControlBase-Class.md)   
 [CComCompositeControl Class](../VS_visualcpp/CComCompositeControl-Class.md)