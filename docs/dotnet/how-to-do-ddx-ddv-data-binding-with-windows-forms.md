---
title: 'Gewusst wie: Do DDX-DDV Datenbindung mit Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 31629a4db2559112ba49f5c069b08de7abdfc2db
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754348"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>Gewusst wie: DDX-/DDV-Datenbindung mit Windows Forms

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol) ruft [CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol) auf, um ein Steuerelement zu erstellen, das der Ressourcensteuerungs-ID entspricht. Wenn Sie `DDX_ManagedControl` für `CWinFormsControl` ein Steuerelement (in vom Assistenten `CreateManagedControl` generiertem Code) verwenden, sollten Sie nicht explizit für dasselbe Steuerelement aufrufen.

Rufen `DDX_ManagedControl` Sie [CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) auf, um Steuerelemente aus Ressourcen-IDs zu erstellen. Für den Datenaustausch müssen Sie die DDX/DDV-Funktionen nicht mit Windows Forms-Steuerelementen verwenden. Stattdessen können Sie Code platzieren, um auf die `DoDataExchange` Eigenschaften des verwalteten Steuerelements in der Methode der Dialog- (oder Ansichts-)Klasse zuzugreifen, wie im folgenden Beispiel.

Das folgende Beispiel zeigt, wie eine systemeigene C++-Zeichenfolge an ein .NET-Benutzersteuerelement gebunden wird.

## <a name="example"></a>Beispiel

Im Folgenden finden Sie ein Beispiel für die DDX/DDV-Datenbindung einer MFC-Zeichenfolge `m_str` mit der benutzerdefinierten `NameText` Eigenschaft eines .NET-Benutzersteuerelements.

Das Steuerelement wird erstellt, wenn [CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) zum ersten Mal aufruft, `CMyDlg::DoDataExchange` sodass jeder Code, der `m_UserControl` nach dem `DDX_ManagedControl` Aufruf stammen muss.

Sie können diesen Code in der MFC01-Anwendung implementieren, die Sie unter [Gewusst wie: Erstellen der Benutzersteuerung und](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)des Hosts in einem Dialogfeld erstellt haben.

Setzen Sie den folgenden Code in die Deklaration von CMFC01Dlg:

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>Beispiel

Setzen Sie den folgenden Code in die Implementierung von CMFC01Dlg:

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

## <a name="example"></a>Beispiel

Nun fügen wir die Handlermethode für einen Klick auf die Schaltfläche OK hinzu. Klicken Sie auf die Registerkarte **Ressourcenansicht.** Doppelklicken Sie in der `IDD_MFC01_DIALOG`Ressourcenansicht auf . Die Dialogressource wird in Ressourcen-Editor angezeigt. Dann doppelklicken Sie auf die Schaltfläche OK..

Definieren Sie den Handler wie folgt.

```cpp
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>Beispiel

Und fügen Sie der Implementierung von BOOL CMFC01Dlg::OnInitDialog() die folgende Zeile hinzu.

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

Sie können die Anwendung jetzt erstellen und ausführen. Beachten Sie, dass Text im Textfeld beim Schließen der Anwendung in einem Popup-Meldungsfeld angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

[CWinFormsControl-Klasse](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
