---
title: "How to: Do DDX-DDV Data Binding with Windows Forms"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], hosting a Windows Forms Control"
  - "Windows Forms [C++], MFC support"
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
caps.latest.revision: 13
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
# How to: Do DDX/DDV Data Binding with Windows Forms
[DDX_ManagedControl](../Topic/DDX_ManagedControl.md) calls [CWinFormsControl::CreateManagedControl](../Topic/CWinFormsControl::CreateManagedControl.md) to create a control matching the resource control ID. If you use `DDX_ManagedControl` for a `CWinFormsControl` control (in wizard-generated code), you should not call `CreateManagedControl` explicitly for the same control.  
  
 Call `DDX_ManagedControl` in [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md) to create controls from resource IDs. For data exchange, you do not need to use the DDX/DDV functions with Windows Forms controls. Instead, you can place code to access the properties of the managed control in the `DoDataExchange` method of your dialog (or view) class, as in the following example.  
  
 The following example shows how to bind a native C++ string to a .NET user control.  
  
## Example  
 The following is an example of DDX/DDV data binding of an MFC string `m_str` with the user-defined `NameText` property of a .NET user control.  
  
 The control is created when [CDialog::OnInitDialog](../Topic/CDialog::OnInitDialog.md) calls `CMyDlg::DoDataExchange` for the first time, so any code that references `m_UserControl` must come after the `DDX_ManagedControl` call.  
  
 You can implement this code in the MFC01 application you created in [How to: Create the User Control and Host in a Dialog Box](../cli/how-to--create-the-user-control-and-host-in-a-dialog-box.md).  
  
 Put the following code in the declaration of CMFC01Dlg:  
  
```  
class CMFC01Dlg : public CDialog  
{  
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;  
   CString m_str;  
};  
```  
  
## Example  
 Put the following code in the implementation of CMFC01Dlg:  
  
```  
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)  
{  
   CDialog::DoDataExchange(pDX);  
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);  
  
   if (pDX->m_bSaveAndValidate) {  
      m_str = m_MyControl->textBox1->Text;  
   } else  
   {  
      m_MyControl->textBox1->Text = gcnew System::String(m_str);  
   }  
}  
```  
  
## Example  
 Now we will add the handler method for a click on the OK button. Click the **Resource View** tab. In Resource View, double-click on `IDD_MFC01_DIALOG`. The dialog resource appears in Resource Editor. Then double click the OK button..  
  
 Define the handler as follows.  
  
```  
void CMFC01Dlg::OnBnClickedOk()  
{  
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));  
   OnOK();  
}  
```  
  
## Example  
 And add the following line to the implementation of BOOL CMFC01Dlg::OnInitDialog().  
  
```  
m_MyControl.GetControl()->textBox1->Text = "hello";  
```  
  
 You can now build and run the application. Notice that any text in the text box will be displayed in a pop-up message box when the application closes.  
  
## See Also  
 [CWinFormsControl Class](../mfcref/cwinformscontrol-class.md)   
 [DDX_ManagedControl](../Topic/DDX_ManagedControl.md)   
 [CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)