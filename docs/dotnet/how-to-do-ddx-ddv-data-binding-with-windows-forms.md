---
title: 'Vorgehensweise: DDX-/DDV-Datenbindung mit Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: a0759eba1c55e72f2c0a99964b0b2d254df82a25
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008309"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Gewusst wie: DDX-/DDV-Datenbindung mit Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) ruft [CWinFormsControl:: foratemanagedcontrol](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) auf, um ein Steuerelement zu erstellen, das mit der Ressourcen Steuerungs-ID übereinstimmt. Wenn Sie `DDX_ManagedControl` für ein `CWinFormsControl` -Steuerelement verwenden (in vom Assistenten generierten Code), sollten Sie nicht `CreateManagedControl` explizit für dasselbe Steuerelement aufgerufen werden.

Rufen `DDX_ManagedControl` Sie in [CWnd auf::D odataexchange](../mfc/reference/cwnd-class.md#dodataexchange) , um Steuerelemente aus Ressourcen-IDs zu erstellen. Für den Datenaustausch müssen Sie die DDX/DDV-Funktionen nicht mit Windows Forms-Steuerelementen verwenden. Stattdessen können Sie Code für den Zugriff auf die Eigenschaften des verwalteten Steuer Elements in der- `DoDataExchange` Methode Ihrer Dialog-(oder Sicht-) Klasse platzieren, wie im folgenden Beispiel gezeigt.

Im folgenden Beispiel wird gezeigt, wie eine native C++-Zeichenfolge an ein .NET-Benutzer Steuerelement gebunden wird.

## <a name="example-ddxddv-data-binding"></a>Beispiel: DDX/DDV-Datenbindung

Im folgenden finden Sie ein Beispiel für die DDX/DDV-Datenbindung einer MFC-Zeichenfolge `m_str` mit der benutzerdefinierten `NameText` Eigenschaft eines .NET-Benutzer Steuer Elements.

Das-Steuerelement wird erstellt, wenn [CDialog:: OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) `CMyDlg::DoDataExchange` zum ersten Mal aufruft. Daher muss jeder Code, auf den verweist, `m_UserControl` nach dem `DDX_ManagedControl` Aufruf erfolgen.

Sie können diesen Code in der MFC01-Anwendung implementieren, die Sie in Gewusst [wie: Erstellen des Benutzer Steuer Elements und des Hosts in einem Dialog Feld](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)erstellt haben.

Fügen Sie den folgenden Code in die Deklaration von CMFC01Dlg ein:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example-implement-dodataexchange"></a>Beispiel: Implementieren von DoDataExchange ()

Fügen Sie den folgenden Code in die Implementierung von CMFC01Dlg ein:

```cpp
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

## <a name="example-add-handler-method"></a>Beispiel: Hinzufügen einer Handlermethode

Nun fügen wir die Handlermethode für einen Klick auf die Schaltfläche "OK" hinzu. Klicken Sie auf die Registerkarte **Ressourcenansicht** . Doppelklicken Sie in Ressourcenansicht auf `IDD_MFC01_DIALOG` . Die Dialogressource wird in Ressourcen-Editor angezeigt. Doppelklicken Sie dann auf die Schaltfläche OK.

Definieren Sie den Handler wie folgt.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example-set-the-textbox-text"></a>Beispiel: Festlegen des TextBox-Texts

Fügen Sie der Implementierung von BOOL CMFC01Dlg:: OnInitDialog () die folgende Zeile hinzu.

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Sie können die Anwendung jetzt erstellen und ausführen. Beachten Sie, dass jeder Text im Textfeld in einem Popup-Meldungs Feld angezeigt wird, wenn die Anwendung geschlossen wird.

## <a name="see-also"></a>Siehe auch

[CWinFormsControl-Klasse](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
