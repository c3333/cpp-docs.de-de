---
title: 'Exemplarische Vorgehensweise: Verwenden der neuen MFC-Shell-Steuerelemente'
ms.date: 04/25/2019
helpviewer_keywords:
- shell controls (MFC)
ms.assetid: f0015caa-199d-4aaf-9501-5a239fce9095
ms.openlocfilehash: 5786fbbf7ec9f31e7d895a96dae27b8fc95abda1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360215"
---
# <a name="walkthrough-using-the-new-mfc-shell-controls"></a>Exemplarische Vorgehensweise: Verwenden der neuen MFC-Shell-Steuerelemente

In dieser exemplarischen Vorgehensweise erstellen Sie eine Anwendung, die dem Datei-Explorer ähnelt. Sie erstellen ein Fenster mit zwei Bereichen. Im linken Bereich befindet sich ein [CMFCShellTreeCtrl-Objekt,](../mfc/reference/cmfcshelltreectrl-class.md) das Ihren Desktop in einer hierarchischen Ansicht anzeigt. Im rechten Bereich befindet sich eine [CMFCShellListCtrl,](../mfc/reference/cmfcshelllistctrl-class.md) in der die Dateien in dem Ordner angezeigt werden, der im linken Bereich ausgewählt ist.

## <a name="prerequisites"></a>Voraussetzungen

- In Visual Studio 2017 und höher ist die MFC-Unterstützung eine optionale Komponente. Um es zu installieren, öffnen Sie Visual Studio Installer im Windows-Startmenü. Suchen Sie die Version von Visual Studio, die Sie verwenden, und wählen Sie die Schaltfläche **Ändern** aus. Stellen Sie sicher, dass die **Kachel Desktopentwicklung mit C++aktiviert** ist. Überprüfen Sie unter **Optionale Komponenten**die **MFC-Support-Schaltfläche.**

- In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie Visual Studio für die Verwendung **der allgemeinen Entwicklungseinstellungen**eingerichtet haben. Wenn Sie eine andere Entwicklungseinstellung verwenden, werden einige Visual Studio-Fenster, die wir in dieser exemplarischen Vorgehensweise verwenden, möglicherweise nicht standardmäßig angezeigt.

## <a name="to-create-a-new-mfc-application-by-using-the-mfc-application-wizard"></a>So erstellen Sie eine MFC-Anwendung mit dem MFC-Anwendungs-Assistenten

Diese Schritte hängen davon ab, welche Version von Visual Studio Sie verwenden. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-an-mfc-project-in-visual-studio-2019"></a>So erstellen Sie ein MFC-Projekt in Visual Studio 2019

1. Klicken Sie im Hauptmenü auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Geben Sie im Suchfeld oben **MFC** ein, und wählen Sie dann **MFC App** aus der Ergebnisliste aus.

1. Klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite einen Namen für das Projekt ein, und geben Sie ggf. den Projektspeicherort an.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

   Verwenden Sie nach der Anzeige des **MFC-Anwendungs-Assistenten** die folgenden Optionen:

   1. Wählen Sie **Anwendungstyp** auf der linken Seite. Wählen Sie dann **Einzeldokument** aus, und wählen Sie **Dokument-/Ansichtsarchitekturunterstützung**aus. Wählen Sie unter **Projektstil** **Visual Studio**aus, und wählen Sie aus der Dropdown-Liste **Visual-Stil und -Farben** **Office 2007 (Blaues Design)** aus.

   1. Wählen Sie im Bereich **"Unterstützung für zusammengesetzte Dokumente"** die Option **Keine**aus.

   1. Nehmen Sie keine Änderungen am Bereich **Dokumentvorlageneigenschaften** vor.

   1. Stellen Sie im Bereich **Benutzeroberflächen-Features** sicher, dass die Option **Menüleiste und Symbolleiste** verwenden ausgewählt ist. Lassen Sie alle anderen Optionen unverändert.

   1. Wählen Sie im Bereich **Erweiterte Features** die Option **ActiveX-Steuerelemente**, **Allgemeines Steuerelementmanifest**und **Navigationsbereich** aus. Lassen Sie alles andere so, wie es ist. Die Option **Navigationsbereich** bewirkt, dass der Assistent den Bereich `CMFCShellTreeCtrl` links neben dem Fenster mit einem bereits eingebetteten Fenster erstellt.

   1. Wir werden keine Änderungen am Bereich **Generierte Klassen** vornehmen, daher klicken Sie auf **Fertig stellen,** um Ihr neues MFC-Projekt zu erstellen.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-an-mfc-project-in-visual-studio-2017-or-earlier"></a>So erstellen Sie ein MFC-Projekt in Visual Studio 2017 oder früher

1. Verwenden Sie den **MFC-Anwendungs-Assistenten,** um eine neue MFC-Anwendung zu erstellen. Um den Assistenten auszuführen, wählen Sie im **Menü Datei** **Neu**aus, und wählen Sie dann **Projekt**aus. Das Dialogfeld **Neues Projekt** wird angezeigt.

1. Erweitern Sie im Dialogfeld **Neues Projekt** den **Visual C++-Knoten** im Bereich **Projekttypen,** und wählen Sie **MFC**aus. Wählen Sie dann im Bereich **Vorlagen** **MFC-Anwendung**aus. Geben Sie einen Namen für `MFCShellControls` das Projekt ein, z. B. und klicken Sie auf **OK**.

   Verwenden Sie nach der Anzeige des **MFC-Anwendungs-Assistenten** die folgenden Optionen:

   1. Deaktivieren Sie im Bereich **Anwendungstyp** unter **Anwendungstyp**die Option **Tabbed-Dokumente.** Wählen Sie als Nächstes **Einzeldokument** aus, und wählen Sie **Dokument-/Ansichtsarchitekturunterstützung**aus. Wählen Sie unter **Projektstil** **Visual Studio**aus, und wählen Sie aus der Dropdown-Liste **Visual-Stil und -Farben** **Office 2007 (Blaues Design)** aus.

   1. Wählen Sie im Bereich **"Unterstützung für zusammengesetzte Dokumente"** die Option **Keine**aus.

   1. Nehmen Sie keine Änderungen am Bereich **Dokumentvorlagenzeichenfolgen** vor.

   1. Wählen Sie im Bereich **Datenbankunterstützung** (Visual Studio 2015 und älter) **Keine** aus, da die Anwendung keine Datenbank verwendet.

   1. Stellen Sie im Bereich **Benutzeroberflächen-Features** sicher, dass die Option **Menüleiste und Symbolleiste** verwenden ausgewählt ist. Lassen Sie alle anderen Optionen unverändert.

   1. Wählen Sie im Bereich **Erweiterte Funktionen** unter **Erweiterte Funktionen**nur **ActiveX-Steuerelemente** und **Common Control Manifest**aus. Wählen Sie unter **Erweiterte Rahmenbereiche**nur die Option **Navigationsbereich** aus. Dadurch erstellt der Assistent den Bereich links neben dem `CMFCShellTreeCtrl` Fenster mit einem bereits eingebetteten Fenster.

   1. Wir werden keine Änderungen am Bereich **Generierte Klassen** vornehmen, daher klicken Sie auf **Fertig stellen,** um Ihr neues MFC-Projekt zu erstellen.

::: moniker-end

Überprüfen Sie, ob die Anwendung erfolgreich erstellt wurde, indem Sie sie erstellen und ausführen. Um die Anwendung zu erstellen, wählen Sie im Menü **Erstellen** die Option **Lösung erstellen**aus. Wenn die Anwendung erfolgreich erstellt wird, führen Sie die Anwendung aus, indem Sie im **Debugmenü** **Debuggen starten** auswählen.

Der Assistent erstellt automatisch eine Anwendung mit einer Standardmenüleiste, einer Standardsymbolleiste, einer Standardstatusleiste und einer Outlookleiste links neben dem Fenster mit einer **Ordneransicht** und einer **Kalenderansicht.**

### <a name="to-add-the-shell-list-control-to-the-document-view"></a>So fügen Sie das Shell-Listensteuerelement der Dokumentenansicht hin

1. In diesem Abschnitt fügen Sie der `CMFCShellListCtrl` Ansicht, die der Assistent erstellt hat, eine Instanz von hinzu. Öffnen Sie die Ansichtsheaderdatei, indem Sie im **Projektmappen-Explorer**auf **MFCShellControlsView.h** doppelklicken.

   Suchen Sie die `#pragma once`-Anweisung am oberen Rand der Headerdatei. Fügen Sie direkt darunter den folgenden Code hinzu, mit dem die Headerdatei für `CMFCShellListCtrl` eingeschlossen wird:

   ```cpp
   #include <afxShellListCtrl.h>
   ```

   Fügen Sie nun eine Membervariable des Typs `CMFCShellListCtrl` hinzu. Suchen Sie zunächst den folgenden Kommentar in der Headerdatei:

   ```cpp
   // Generated message map functions
   ```

   Fügen Sie direkt über diesem Kommentar diesen Code hinzu:

   ```cpp
   private:
   CMFCShellListCtrl m_wndList;
   ```

1. Der **MFC-Anwendungs-Assistent** hat bereits ein `CMFCShellTreeCtrl` Objekt in der `CMainFrame` Klasse erstellt, ist jedoch ein geschützter Member. Wir greifen später auf das Objekt zu, also erstellen Sie jetzt einen Accessor dafür. Öffnen Sie die MainFrm.h-Headerdatei, indem Sie im **Projektmappen-Explorer**darauf doppelklicken. Suchen Sie den folgenden Kommentar:

   ```cpp
   // Attributes
   ```

   Fügen Sie direkt darunter die folgende Methodendeklaration hinzu:

   ```cpp
   public:
       CMFCShellTreeCtrl& GetShellTreeCtrl();
   ```

   Öffnen Sie als Nächstes die MainFrm.cpp-Quelldatei, indem Sie im **Projektmappen-Explorer**darauf doppelklicken. Fügen Sie am unteren Rand dieser Datei die folgende Methodendefinition hinzu:

   ```cpp
   CMFCShellTreeCtrl& CMainFrame::GetShellTreeCtrl()
   {
        return m_wndTree;
   }
   ```

1. Jetzt aktualisieren wir die `CMFCShellControlsView`-Klasse, um die `WM_CREATE`-Fenstermeldung zu bearbeiten. Öffnen Sie das Fenster `CMFCShellControlsView` **Klassenansicht,** und wählen Sie die Klasse aus. Klicken Sie mit der rechten Maustaste, und wählen Sie **Eigenschaften** aus.

   Als Nächstes klicken Sie im [Klassen-Assistenten](reference/mfc-class-wizard.md)auf die `WM_CREATE` Registerkarte **Nachrichten.** Scrollen Sie nach unten, bis Sie die Nachricht gefunden haben. Wählen Sie `WM_CREATE` ** \<** in der Dropdown-Liste neben> OnCreate hinzufügen aus. Der Befehl erstellt einen Nachrichtenhandler für uns und aktualisiert automatisch die MFC-Nachrichtenzuordnung.

   In `OnCreate` der Methode erstellen wir `CMFCShellListCtrl` nun unser Objekt. Suchen Sie die `OnCreate`-Methodendefinition in der Quelldatei MFCShellControlsView.cpp, und ersetzen Sie die entsprechende Implementierung durch folgenden Code:

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

1. Wiederholen Sie den vorherigen Schritt nun für die `WM_SIZE`-Meldung. Dies führt dazu, dass die Anwendungsansicht neu gezeichnet wird, wenn ein Benutzer die Größe des Anwendungsfensters ändert. Ersetzen Sie die Definition für die `OnSize`-Methode durch den folgenden Code:

    ```cpp
    void CMFCShellControlsView::OnSize(UINT nType, int cx, int cy)
    {
        CView::OnSize(nType, cx, cy);

        m_wndList.SetWindowPos(NULL, -1, -1, cx, cy,
            SWP_NOMOVE | SWP_NOZORDER | SWP_NOACTIVATE);
    }
    ```

1. Der letzte Schritt besteht `CMFCShellTreeCtrl` `CMFCShellListCtrl` darin, die und-Objekte mithilfe der [CMFCShellTreeCtrl::SetRelatedList-Methode](../mfc/reference/cmfcshelltreectrl-class.md#setrelatedlist) zu verbinden. Nach dem `CMFCShellTreeCtrl::SetRelatedList`Aufruf `CMFCShellListCtrl` zeigt der automatisch den Inhalt `CMFCShellTreeCtrl`des im ausgewählten Elements an. Wir verbinden die `OnActivateView` Objekte in der Methode, die aus [CView::OnActivateView](../mfc/reference/cview-class.md#onactivateview)überschrieben wird.

   Fügen Sie in der Headerdatei MFCShellControlsView.h innerhalb der `CMFCShellControlsView`-Klassendeklaration die folgende Methodendeklaration hinzu:

    ```cpp
    protected:
    virtual void OnActivateView(BOOL bActivate,
        CView* pActivateView,
        CView* pDeactiveView);
    ```

   Fügen Sie als Nächstes die Definition für die Methode der MFCShellControlsView.cpp-Quelldatei hinzu:

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

   Da wir Methoden aus `CMainFrame` der Klasse aufrufen, `#include` müssen wir oben in der MFCShellControlsView.cpp-Quelldatei eine Direktive hinzufügen:

    ```cpp
    #include "MainFrm.h"
    ```

1. Überprüfen Sie, ob die Anwendung erfolgreich erstellt wurde, indem Sie sie erstellen und ausführen. Um die Anwendung zu erstellen, wählen Sie im Menü **Erstellen** die Option **Lösung erstellen**aus. Wenn die Anwendung erfolgreich erstellt wird, führen Sie sie aus, indem Sie im **Debugmenü** **Debuggen** starten auswählen.

   Sie sollten nun die Details zum Element sehen, die im Ansichtsbereich `CMFCShellTreeCtrl` ausgewählt sind. Wenn Sie auf einen Knoten in `CMFCShellTreeCtrl` klicken, wird `CMFCShellListCtrl` automatisch aktualisiert. Wenn Sie auf einen Ordner in `CMFCShellListCtrl` doppelklicken, sollte `CMFCShellTreeCtrl` automatisch aktualisiert werden.

   Klicken Sie mit der rechten Maustaste auf ein beliebiges Element im Struktursteuerelement oder im Listensteuerelement. Sie erhalten das gleiche Kontextmenü, als ob Sie den echten **Datei-Explorer**verwenden würden.

## <a name="next-steps"></a>Nächste Schritte

- Der Assistent hat eine Outlook-Leiste mit einem **Ordnerbereich** und einem **Kalenderbereich** erstellt. Es macht wahrscheinlich keinen Sinn, einen **Kalenderbereich** in einem **Explorer-Fenster** zu haben, also entfernen Sie diesen Bereich jetzt.

- Der `CMFCShellListCtrl` unterstützt das Anzeigen von Dateien in verschiedenen Modi, z. B. **Große Symbole**, **Kleine Symbole**, **Liste**und **Details**. Aktualisieren Sie die Anwendung, um diese Funktionalität zu implementieren. Hinweis: siehe [Visual C++-Beispiele](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweisen](../mfc/walkthroughs-mfc.md)
