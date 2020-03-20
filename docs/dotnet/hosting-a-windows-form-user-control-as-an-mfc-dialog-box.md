---
title: Hosten eines Windows Form-Benutzersteuerelements als MFC-Dialogfeld
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 7fc2aad1e0a550fb8f22b311518ae9fb16c076a5
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "79544796"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hosten eines Windows Form-Benutzersteuerelements als MFC-Dialogfeld

MFC stellt die Vorlagen Klasse [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) bereit, sodass Sie in einem modalen oder nicht modalen MFC-Dialogfeld ein Windows Forms Benutzer Steuerelement (<xref:System.Windows.Forms.UserControl>) hosten können. `CWinFormsDialog` wird von der MFC-Klasse [CDialog](../mfc/reference/cdialog-class.md)abgeleitet, sodass das Dialogfeld als modales oder nicht modales Dialogfeld gestartet werden kann.

Der Prozess, der von `CWinFormsDialog` zum Hosten des Benutzer Steuer Elements verwendet wird, ähnelt dem unter [Hosten eines Windows Form-Benutzer Steuer Elements in einem MFC-Dialog Feld](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). `CWinFormsDialog` verwaltet jedoch die Initialisierung und das Hosten des Benutzersteuerelements, sodass es nicht manuell programmiert werden muss.

Eine Beispielanwendung, die Windows Forms anzeigt, die mit MFC verwendet werden, finden Sie unter [MFC-und Windows Forms-Integration](https://www.microsoft.com/download/details.aspx?id=2113).

### <a name="to-create-the-mfc-host-application"></a>So erstellen Sie die MFC-Hostanwendung

1. Erstellen Sie ein MFC-Anwendungsprojekt.

   Wählen Sie im Menü **Datei** die Option **neu**aus, und klicken Sie dann auf **Projekt**. Wählen Sie im Ordner " **Visual C++**  " die Option **MFC-Anwendung**aus.

   Geben Sie im Feld **Name** `MFC03` ein, und ändern Sie die Projektmappeneinstellung zu Projekt Mappe **Hinzufügen**. Klicken Sie auf **OK**.

   Akzeptieren Sie im **MFC-Anwendungs-Assistenten**alle Standardwerte, und klicken Sie dann auf **Fertig**stellen. Dies erstellt eine MFC-Anwendung mit einem MDI (Multiple Document Interface).

1. Konfigurieren des Projekts.

   Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten **den MFC03** , und wählen Sie **Eigenschaften**aus. Das Dialogfeld **Eigenschaften Seiten** wird angezeigt.

   Wählen Sie im Dialogfeld Eigenschaften **Seiten** in der **Strukturansicht Konfigurations Eigenschaften** die Option **Allgemein**aus, und legen Sie dann im Abschnitt **Projekt** Standards die **Common Language Runtime-unter** Stützung auf **Common Language Runtime-Unterstützung (/CLR)** fest. Klicken Sie auf **OK**.

1. Fügen Sie dem .NET-Steuerelement einen Verweis hinzu.

   Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten **den MFC03** , und wählen Sie **Hinzufügen**, **Verweise**aus. Klicken Sie auf der **Eigenschaften Seite**auf **neuen Verweis hinzufügen**, wählen Sie WindowsControlLibrary1 (unter der Registerkarte **Projekte** ) aus, und klicken Sie auf **OK**. Dadurch wird ein Verweis in Form einer [/Fu](../build/reference/fu-name-forced-hash-using-file.md) -Compileroption hinzugefügt, damit das Programm kompiliert wird. Außerdem wird WindowsControlLibrary1. dll in das `MFC03`-Projektverzeichnis kopiert, damit das Programm ausgeführt wird.

1. Fügen Sie `#include <afxwinforms.h>` zu " *PCH. h* " (*stdafx. h* in Visual Studio 2017 und früher) am Ende der vorhandenen `#include` Anweisungen hinzu.

1. Fügen Sie eine neue Klasse hinzu, die `CDialog` als Unterklasse verwendet.

   Klicken Sie mit der rechten Maustaste auf den Projektnamen, und fügen Sie eine MFC-Klasse mit dem Namen CHostForWinForm hinzu, die `CDialog` als Unterklasse verwendet. Da Sie die Dialogfeld Ressource nicht benötigen, können Sie die Ressourcen-ID löschen (Wählen Sie **Ressourcenansicht**aus, erweitern Sie den **Dialog** Ordner, und löschen Sie `IDD_HOSTFORWINFORM` Ressource.  Entfernen Sie dann alle Verweise auf die ID aus dem Code.)

1. Ersetzen Sie in den Dateien CHostForWinForm.h und CHostForWinForm.cpp `CDialog` durch `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Rufen Sie in der CHostForWinForm-Klasse DoModal auf.

   Fügen Sie in der Datei MFC03.cpp die Zeichenfolge `#include "HostForWinForm.h"` hinzu.

   Fügen Sie in der Definition von CMFC03App::InitInstance vor der return-Anweisung Folgendes hinzu:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Erstellen Sie das Projekt, und führen Sie es aus.

   Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.

   Als Nächstes fügen Sie Code zum Überwachen des Zustands eines Steuerelements in den Windows Forms aus der MFC-Anwendung hinzu.

1. Fügen Sie einen Handler für OnInitDialog hinzu.

   Zeigen Sie das **Eigenschaften** Fenster (F4) an. Wählen Sie in **Klassenansicht**CHostForWinForm aus. Wählen Sie im Fenster **Eigenschaften** die Option außer Kraft setzungen aus, und klicken Sie in der Zeile für OnInitDialog in der linken Spalte auf \< > hinzufügen. Dadurch wird in CHostForWinForm.h die folgende Zeile hinzugefügt:

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. Definieren Sie OnInitDialog (in CHostForWinForm.cpp) wie folgt:

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. Fügen Sie anschließend den OnButton1-Handler hinzu. Fügen Sie dem öffentlichen Abschnitt der CHostForWinForm-Klasse in CHostForWinForm.h die folgenden Zeilen hinzu:

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   Fügen Sie in CHostForWinForm.cpp die folgende Definition hinzu:

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. Erstellen Sie das Projekt, und führen Sie es aus. Wenn Sie auf die Schaltfläche klicken, die sich im Windows Form befindet, wird der Code in der MFC-Anwendung ausgeführt.

    Als Nächstes fügen Sie Code hinzu, mit dem der Wert aus dem MFC-Code im Textfeld des Windows Forms angezeigt wird.

1. Fügen Sie in CHostForWinForm.h im öffentlichen Abschnitt der CHostForWinForm-Klasse die folgende Deklaration hinzu:

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. Fügen Sie in der Definition von DoDataExchange in CHostForWinForm.cpp am Ende der Funktion die folgenden drei Zeilen hinzu:

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. Fügen Sie in der Definition von OnButton1 in CHostForWinForm.cpp am Ende der Funktion die folgenden drei Zeilen hinzu:

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. Erstellen Sie das Projekt, und führen Sie es aus.

## <a name="see-also"></a>Siehe auch

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[mithilfe eines Windows Form-Benutzer Steuer Elements in MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
