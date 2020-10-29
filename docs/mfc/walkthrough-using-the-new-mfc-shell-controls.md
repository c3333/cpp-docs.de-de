---
title: 'Exemplarische Vorgehensweise: Verwenden der neuen MFC-Shell-Steuerelemente'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 0d8db9044a64305bd7bb9ef6fe10de9ecef1ce51
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924755"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Exemplarische Vorgehensweise: Verwenden der neuen MFC-Shell-Steuerelemente

In dieser exemplarischen Vorgehensweise erstellen Sie eine Anwendung, die dem Datei-Explorer ähnelt. Sie erstellen ein Fenster mit zwei Bereichen. Der linke Bereich enthält ein [cmfcshelltreectrl](../mfc/reference/cmfcshelltreectrl-class.md) -Objekt, das den Desktop in einer hierarchischen Ansicht anzeigt. Der Rechte Bereich enthält einen [cmfcshelllistctrl](../mfc/reference/cmfcshelllistctrl-class.md) , der die Dateien im Ordner anzeigt, der im linken Bereich ausgewählt ist.

## <a name="prerequisites"></a>Voraussetzungen

- In Visual Studio 2017 und höher ist die MFC-Unterstützung eine optionale Komponente. Öffnen Sie die Visual Studio-Installer über das Windows-Startmenü, um Sie zu installieren. Suchen Sie die Version von Visual Studio, die Sie verwenden, und klicken Sie auf die Schaltfläche **ändern** . Stellen Sie sicher, dass die Kachel **Desktop Entwicklung mit C++** aktiviert ist. Überprüfen Sie unter **optionale Komponenten** die Schaltfläche **MFC-Unterstützung** .

- In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie Visual Studio für die Verwendung **allgemeiner Entwicklungseinstellungen** eingerichtet haben. Wenn Sie eine andere Entwicklungs Einstellung verwenden, werden einige Visual Studio-Fenster, die in dieser exemplarischen Vorgehensweise verwendet werden, möglicherweise nicht standardmäßig angezeigt.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>So erstellen Sie eine MFC-Anwendung mit dem MFC-Anwendungs-Assistenten

Diese Schritte variieren abhängig von der verwendeten Version von Visual Studio. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version** . Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker range="msvc-160"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>So erstellen Sie ein MFC-Projekt in Visual Studio 2019

1. Wählen Sie im Hauptmenü **Datei** > **Neu** > **Projekt** aus, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Geben Sie im Suchfeld am oberen Rand **MFC** ein, und wählen Sie dann in der Ergebnisliste die Option **MFC-App** aus.

1. Klicken Sie auf **Weiter** . Geben Sie auf der nächsten Seite einen Namen für das Projekt ein, und geben Sie den Speicherort des Projekts an, wenn dies gewünscht ist.

1. Klicken Sie auf die Schaltfläche **Erstellen** , um das Projekt zu erstellen.

   Nachdem der **MFC-Anwendungs-Assistent** angezeigt wird, verwenden Sie die folgenden Optionen:

   1. Wählen Sie auf der linken Seite **Anwendungstyp** aus. Wählen Sie dann **einzelnes Dokument** aus, und wählen Sie **Unterstützung für Dokument-/sichtarchitektur** Wählen Sie unter **Projekt Stil** die Option **Visual Studio** aus, und wählen Sie in der Dropdown Liste **visueller Stil und Farben** die Option **Office 2007 (blaues Design)** aus.

   1. Wählen Sie im Bereich **Verbund Dokument Unterstützung** die Option **keine** aus.

   1. Nehmen Sie keine Änderungen am Eigenschaften Bereich für **Dokumentvorlagen** vor.

   1. Vergewissern Sie sich, dass im Bereich **Benutzeroberflächen Funktionen** die Option **Menüleiste und Symbolleiste verwenden** ausgewählt ist. Lassen Sie alle anderen Optionen unverändert.

   1. Wählen Sie im Bereich **Erweiterte Funktionen** die Option **ActiveX** -Steuerelemente, **gemeinsames Steuerelement Manifest** und **Navigations** Bereich aus. Lassen Sie alles andere unverändert. Die Option **Navigations** Bereich bewirkt, dass der Assistent den Bereich auf der linken Seite des Fensters mit einem `CMFCShellTreeCtrl` bereits eingebetteten erstellt.

   1. Wir nehmen keine Änderungen am Bereich **generierte Klassen** vor. Klicken Sie deshalb auf ' **Fertig** stellen ', um das neue MFC-Projekt zu erstellen.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>So erstellen Sie ein MFC-Projekt in Visual Studio 2017 oder früher

1. Verwenden Sie den **MFC-Anwendungs-Assistenten** , um eine neue MFC-Anwendung zu erstellen. Um den Assistenten auszuführen, wählen Sie im Menü **Datei** die Option **neu** aus, und wählen Sie dann **Projekt** aus. Das Dialogfeld **Neues Projekt** wird angezeigt.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C++** im Bereich **Projekttypen** , und wählen Sie **MFC** aus. Wählen Sie dann im Bereich **Vorlagen** die Option **MFC-Anwendung** aus. Geben Sie einen Namen für das Projekt ein, z.b., `MFCShellControls` und klicken Sie auf **OK** .

   Nachdem der **MFC-Anwendungs-Assistent** angezeigt wird, verwenden Sie die folgenden Optionen:

   1. Deaktivieren Sie im Bereich **Anwendungstyp** unter **Anwendungstyp** die Option **Dokumente im Register** Format. Wählen Sie als nächstes **einzelnes Dokument** aus, und wählen Sie **Unterstützung für Dokument-/Ansicht** Wählen Sie unter **Projekt Stil** die Option **Visual Studio** aus, und wählen Sie in der Dropdown Liste **visueller Stil und Farben** die Option **Office 2007 (blaues Design)** aus.

   1. Wählen Sie im Bereich **Verbund Dokument Unterstützung** die Option **keine** aus.

   1. Nehmen Sie keine Änderungen am Bereich Zeichen folgen für **Dokumentvorlagen** vor.

   1. Wählen Sie im Bereich **Datenbankunterstützung** (Visual Studio 2015 und älter) die Option **keine** aus, da die Anwendung keine Datenbank verwendet.

   1. Vergewissern Sie sich, dass im Bereich **Benutzeroberflächen Funktionen** die Option **Menüleiste und Symbolleiste verwenden** ausgewählt ist. Lassen Sie alle anderen Optionen unverändert.

   1. Wählen Sie im Bereich **Erweiterte Funktionen** unter **Erweiterte Funktionen** nur ActiveX-Steuer **Elemente** und **gemeinsames Steuerelement Manifest** aus. Wählen Sie unter **Erweiterte Frame** Bereiche nur die Option **Navigations** Bereich aus. Dies bewirkt, dass der Assistent den Bereich auf der linken Seite des Fensters mit einem `CMFCShellTreeCtrl` bereits eingebetteten erstellt.

   1. Wir nehmen keine Änderungen am Bereich **generierte Klassen** vor. Klicken Sie deshalb auf ' **Fertig** stellen ', um das neue MFC-Projekt zu erstellen.

::: moniker-end

Überprüfen Sie, ob die Anwendung erfolgreich erstellt wurde, indem Sie sie erstellen und ausführen. Um die Anwendung zu erstellen, wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen** aus. Wenn die Anwendung erfolgreich erstellt wird, führen Sie die Anwendung aus, indem Sie im Menü **Debuggen** die Option **Debugging starten** auswählen

Der Assistent erstellt automatisch eine Anwendung, die über eine Standardmenü Leiste, eine Standard Symbolleiste, eine Standardstatus Leiste und eine Outlook-Leiste auf der linken Seite des Fensters mit einer **Ordner** Ansicht und einer **Kalender** Ansicht verfügt.

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>So fügen Sie das Shell-Listensteuerelement der Dokumentenansicht hin

1. In diesem Abschnitt fügen Sie `CMFCShellListCtrl` der Ansicht, die vom Assistenten erstellt wurde, eine Instanz von hinzu. Öffnen Sie die Header Datei für die Ansicht, indem Sie im **Projektmappen-Explorer** auf **mfcshellcontrolsview. h** doppelklicken.

   Suchen Sie die `#pragma once`-Anweisung am oberen Rand der Headerdatei. Fügen Sie direkt darunter den folgenden Code hinzu, mit dem die Headerdatei für `CMFCShellListCtrl` eingeschlossen wird:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Fügen Sie nun eine Membervariable des Typs `CMFCShellListCtrl` hinzu. Suchen Sie zunächst den folgenden Kommentar in der Headerdatei:

   ```cpp
   // Generated message map functions
   ```

   Fügen Sie direkt über diesem Kommentar den folgenden Code hinzu:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. Der **MFC-Anwendungs-Assistent** hat bereits ein `CMFCShellTreeCtrl` -Objekt in der `CMainFrame` -Klasse erstellt, es handelt sich jedoch um einen geschützten Member. Wir greifen zu einem späteren Zeitpunkt auf das Objekt zu, erstellen also jetzt einen Accessor. Öffnen Sie die Header Datei MainFrm. h, indem Sie in der **Projektmappen-Explorer** auf die Datei doppelklicken. Suchen Sie den folgenden Kommentar:

   ```cpp
   // Attributes
   ```

   Fügen Sie direkt darunter die folgende Methodendeklaration hinzu:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Öffnen Sie als nächstes die Quelldatei "mainfrm. cpp", indem Sie in der **Projektmappen-Explorer** auf die Datei doppelklicken. Fügen Sie am unteren Rand dieser Datei die folgende Methodendefinition hinzu:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Jetzt aktualisieren wir die `CMFCShellControlsView`-Klasse, um die `WM_CREATE`-Fenstermeldung zu bearbeiten. Öffnen Sie das Fenster **Klassenansicht** , und wählen Sie die `CMFCShellControlsView` Klasse aus. Klicken Sie mit der rechten Maustaste, und wählen Sie **Eigenschaften** aus.

   Klicken Sie anschließend im [Klassen-Assistenten](reference/mfc-class-wizard.md)auf die Registerkarte **Nachrichten** . Scrollen Sie nach unten, bis Sie die `WM_CREATE` Meldung finden. Wählen Sie in der Dropdown Liste neben die Option `WM_CREATE` **\<Add> OnCreate** aus. Mit dem Befehl wird ein Meldungs Handler für uns erstellt, und die MFC-Meldungs Zuordnung wird automatisch aktualisiert.

   In der- `OnCreate` Methode erstellen wir jetzt das- `CMFCShellListCtrl` Objekt. Suchen Sie die `OnCreate`-Methodendefinition in der Quelldatei MFCShellControlsView.cpp, und ersetzen Sie die entsprechende Implementierung durch folgenden Code:

    ```cpp
    int CMFCShellControlsView::OnCreate(LPCREATESTRUCT lpCreateStruct)
    {
        if (CView::OnCreate(lpCreateStruct) == -1)
            return -1;

        CRect rectDummy (0, 0, 0, 0);

        m_wndList.Create(WS_CHILD | WS_VISIBLE | LVS_REPORT,
            rectDummy, this, 1);

        return 0;
    }
    ```

1. Wiederholen Sie den vorherigen Schritt nun für die `WM_SIZE`-Meldung. Dies bewirkt, dass die Anwendungs Ansicht neu gezeichnet wird, wenn ein Benutzer die Größe des Anwendungsfensters ändert. Ersetzen Sie die Definition für die `OnSize`-Methode durch den folgenden Code:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Der letzte Schritt besteht darin, das `CMFCShellTreeCtrl` -Objekt und das- `CMFCShellListCtrl` Objekt mithilfe der [cmfcshelltreectrl:: setrelatedlist](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) -Methode zu verbinden. Nachdem Sie aufgerufen `CMFCShellTreeCtrl::SetRelatedList` haben, `CMFCShellListCtrl` zeigt das automatisch den Inhalt des Elements an, das in der ausgewählt wurde `CMFCShellTreeCtrl` . Wir verbinden die Objekte in der- `OnActivateView` Methode, die von [CView:: OnActivateView](../mfc/reference/cview-class.md#onactivateview)überschrieben wird.

   Fügen Sie in der Headerdatei MFCShellControlsView.h innerhalb der `CMFCShellControlsView`-Klassendeklaration die folgende Methodendeklaration hinzu:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Fügen Sie als nächstes die Definition für die-Methode der Quelldatei mfcshellcontrolsview. cpp hinzu:

    ```cpp
    void CMFCShellControlsView::OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView)
    {
        if (bActivate&& AfxGetMainWnd() != NULL)
        {
            ((CMainFrame*)AfxGetMainWnd())->GetShellTreeCtrl().SetRelatedList(&m_wndList);
        }

        CView::OnActivateView(bActivate,
            pActivateView,
            pDeactiveView);
    }
    ```

   Da wir Methoden aus der- `CMainFrame` Klasse aufrufen, müssen wir `#include` am Anfang der Quelldatei mfcshellcontrolsview. cpp eine-Direktive hinzufügen:

    ```cpp
    #include "MainFrm.h"
    ```

1. Überprüfen Sie, ob die Anwendung erfolgreich erstellt wurde, indem Sie sie erstellen und ausführen. Um die Anwendung zu erstellen, wählen Sie im Menü **Erstellen** die Option Projekt Mappe **Erstellen** aus. Wenn die Anwendung erfolgreich erstellt wird, führen Sie Sie aus, indem Sie im Menü **Debuggen** die Option **Debugging starten** auswählen

   Sie sollten nun die Details zum Element sehen, die im Ansichtsbereich `CMFCShellTreeCtrl` ausgewählt sind. Wenn Sie auf einen Knoten in `CMFCShellTreeCtrl` klicken, wird `CMFCShellListCtrl` automatisch aktualisiert. Wenn Sie auf einen Ordner in `CMFCShellListCtrl` doppelklicken, sollte `CMFCShellTreeCtrl` automatisch aktualisiert werden.

   Klicken Sie mit der rechten Maustaste auf ein beliebiges Element im Struktur Steuerelement oder im Listen Steuerelement. Sie erhalten dasselbe Kontextmenü wie bei Verwendung des echten **Datei-Explorers** .

## <a name="next-steps"></a>Nächste Schritte

- Der Assistent hat eine Outlook-Leiste mit einem **Ordner** Bereich und einem **Kalender** Bereich erstellt. Es ist wahrscheinlich nicht sinnvoll, einen **Kalender** Bereich in einem **Explorer** -Fenster zu haben. entfernen Sie diesen Bereich nun.

- `CMFCShellListCtrl`Unterstützt das Anzeigen von Dateien in verschiedenen Modi, z. b. **große Symbole** , **kleine Symbole** , **Listen** und **Details** . Aktualisieren Sie die Anwendung, um diese Funktionalität zu implementieren. Hinweis: siehe [Visual C++ Beispiele](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweisen](../mfc/walkthroughs-mfc.md)
