---
title: 'Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 2)'
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: bc204a152168accf3731eede8ca9ef960ab121d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360230"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 2)

[In Teil 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md) dieser exemplarischen Vorgehensweise wurde gezeigt, wie Sie der klassischen Scribble-Anwendung ein Office Fluent Ribbon hinzufügen. In diesem Teil wird gezeigt, wie Menübänder und Steuerelemente hinzugefügt werden, die Benutzer anstelle von Menüs und Befehlen verwenden können.

## <a name="prerequisites"></a>Voraussetzungen

[Visuelle C++-Beispiele](../overview/visual-cpp-samples.md)

## <a name="sections"></a><a name="top"></a>Bereichen

Dieser Teil der exemplarischen Vorgehensweise enthält die folgenden Abschnitte:

- [Hinzufügen neuer Panels zum Menüband](#addnewpanel)

- [Hinzufügen eines Hilfebereichs zur Multifunktionsleiste](#addhelppanel)

- [Hinzufügen eines Stiftbereichs zum Menüband](#addpenpanel)

- [Hinzufügen einer Farbschaltfläche zur Multifunktionsleiste](#addcolorbutton)

- [Hinzufügen eines Farbmitglieds zur Dokumentklasse](#addcolormember)

- [Initialisieren von Stiften und Spareinstellungen](#initpensave)

## <a name="adding-new-panels-to-the-ribbon"></a><a name="addnewpanel"></a>Hinzufügen neuer Panels zum Menüband

In diesen Schritten wird gezeigt, wie Sie ein **Ansichtsfenster** hinzufügen, das zwei Kontrollkästchen enthält, die die Sichtbarkeit der Symbolleiste und der Statusleiste steuern, sowie ein **Fensterfenster,** das eine vertikal ausgerichtete Split-Schaltfläche enthält, die die Erstellung und Anordnung von MDI-Fenstern (Multiple Document Interface) steuert.

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>So fügen Sie der Multifunktionsleistenleiste ein Ansichtsfenster und ein Fensterfenster hinzu

1. Erstellen Sie `View`ein Bedienfeld mit dem Namen , das über zwei Kontrollkästchen verfügt, die die Statusleiste und Symbolleiste umschalten.

   1. Ziehen Sie aus der **Toolbox**ein **Panel** in die **Kategorie Startseite.** Ziehen Sie dann zwei **Kontrollkästchen** in das Bedienfeld.

   1. Klicken Sie auf das Bedienfeld, um seine Eigenschaften zu ändern. Ändern Sie `View`die **Beschriftung** in .

   1. Klicken Sie auf das erste Kontrollkästchen, um dessen Eigenschaften zu ändern. Ändern Sie die `Toolbar` **ID** in `ID_VIEW_TOOLBAR` und die **Beschriftung** in .

   1. Klicken Sie auf das zweite Kontrollkästchen, um dessen Eigenschaften zu ändern. Ändern Sie die `Status Bar` **ID** in `ID_VIEW_STATUS_BAR` und die **Beschriftung** in .

1. Erstellen Sie `Window` ein Panel mit dem Namen mit einer geteilten Schaltfläche. Wenn ein Benutzer auf die Schaltfläche "Split" klickt, werden in einem Kontextmenü drei Befehle angezeigt, die bereits in der Scribble-Anwendung definiert sind.

   1. Ziehen Sie aus der **Toolbox**ein **Panel** in die **Kategorie Startseite.** Ziehen Sie dann eine **Schaltfläche** in das Bedienfeld.

   1. Klicken Sie auf das Bedienfeld, um seine Eigenschaften zu ändern. Ändern Sie `Window`die **Beschriftung** in .

   1. Klicken Sie auf die Schaltfläche. Ändern **Caption** Sie `Windows`Beschriftung `w`in , **Tasten** in , `False` **Großer Bildindex** in `1`, und **Split-Modus** in . Klicken Sie dann auf die Auslassungspunkte (**...**) neben **Menüelementen,** um das Dialogfeld **Element-Editor** zu öffnen.

   1. Klicken Sie dreimal auf **Hinzufügen,** um drei Schaltflächen hinzuzufügen.

   1. Klicken Sie auf die erste `New Window`Schaltfläche, `ID_WINDOW_NEW`und ändern Sie dann **Beschriftung** in , und **ID** in .

   1. Klicken Sie auf die zweite `Cascade`Schaltfläche, `ID_WINDOW_CASCADE`und ändern Sie dann **Beschriftung** in , und **ID** in .

   1. Klicken Sie auf die dritte `Tile`Schaltfläche, `ID_WINDOW_TILE_HORZ`und ändern Sie dann **Beschriftung** in , und **ID** in .

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Die Bedienfelder **Ansicht** und **Fenster** sollten angezeigt werden. Klicken Sie auf die Schaltflächen, um zu bestätigen, dass sie ordnungsgemäß funktionieren.

## <a name="adding-a-help-panel-to-the-ribbon"></a><a name="addhelppanel"></a>Hinzufügen eines Hilfebereichs zur Multifunktionsleiste

Jetzt können Sie zwei Menüelemente, die in der Scribble-Anwendung definiert sind, Multifunktionsleistenschaltflächen zuweisen, die den Namen **Hilfethemen** und **Über Scribble**tragen. Die Schaltflächen werden einem neuen Bedienfeld mit dem Namen **Hilfe**hinzugefügt.

### <a name="to-add-a-help-panel"></a>So fügen Sie ein Hilfefenster hinzu

1. Ziehen Sie aus der **Toolbox**ein **Panel** in die **Kategorie Startseite.** Ziehen Sie dann zwei **Schaltflächen** in das Bedienfeld.

1. Klicken Sie auf das Bedienfeld, um seine Eigenschaften zu ändern. Ändern Sie `Help`die **Beschriftung** in .

1. Klicken Sie auf die erste Schaltfläche. Ändern **Caption** Sie `Help Topics`Beschriftung in `ID_HELP_FINDER`, und **ID** in .

1. Klicken Sie auf die zweite Schaltfläche. Ändern **Caption** Sie `About Scribble...`Beschriftung in `ID_APP_ABOUT`, und **ID** in .

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Ein **Hilfefenster** mit zwei Menübandschaltflächen sollte angezeigt werden.

   > [!IMPORTANT]
   > Wenn Sie auf die Schaltfläche **Hilfethemen** klicken, öffnet die Scribble-Anwendung eine komprimierte HTML-Hilfedatei (.chm) mit dem Namen *your_project_name*.chm. Wenn Ihr Projekt daher nicht den Namen Scribble trägt, müssen Sie die Hilfedatei in Ihren Projektnamen umbenennen.

## <a name="adding-a-pen-panel-to-the-ribbon"></a><a name="addpenpanel"></a>Hinzufügen eines Stiftbereichs zum Menüband

Fügen Sie nun ein Bedienfeld hinzu, um Schaltflächen anzuzeigen, die die Dicke und die Farbe des Stifts steuern. Dieses Bedienfeld enthält ein Kontrollkästchen, das zwischen dicken und dünnen Stiften umschaltet. Seine Funktionalität ähnelt der des **Menüelements Thick Line** in der Scribble-Anwendung.

Mit der ursprünglichen Scribble-Anwendung kann der Benutzer Stiftbreiten aus einem Dialogfeld auswählen, das angezeigt wird, wenn der Benutzer im Menü auf **Stiftbreiten** klickt. Da die Multifunktionsleistenleiste ausreichend Platz für neue Steuerelemente bietet, können Sie das Dialogfeld durch zwei Kombinationsfelder auf dem Menüband ersetzen. Ein Kombinationsfeld passt die Breite des dünnen Stifts an, das andere Kombinationsfeld die Breite des dicken Stifts.

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>So fügen Sie dem Menüband ein Stiftbedienfeld und Kombinationsfelder hinzu

1. Ziehen Sie aus der **Toolbox**ein **Panel** in die **Kategorie Startseite.** Ziehen Sie dann ein **Kontrollkästchen** und zwei **Kombinationsfelder** in das Bedienfeld.

1. Klicken Sie auf das Bedienfeld, um seine Eigenschaften zu ändern. Ändern Sie `Pen`die **Beschriftung** in .

1. Aktivieren Sie das Kontrollkästchen. Ändern **Caption** Sie `Use Thick`Beschriftung in `ID_PEN_THICK_OR_THIN`, und **ID** in .

1. Klicken Sie auf das erste Kombinationsfeld. Ändern Sie `Thin Pen` **Beschriftung** `ID_PEN_THIN_WIDTH`in , **ID** `1;2;3;4;5;6;7;8;9;`in , `2` **Typ** in `Drop List`, **Daten** in und **Text** in .

1. Klicken Sie auf das zweite Kombinationsfeld. Ändern Sie `Thick Pen` **Beschriftung** `ID_PEN_THICK_WIDTH`in , **ID** `5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`in , `5` **Typ** in `Drop List`, **Daten** in und **Text** in .

1. Die neuen Kombinationsfelder entsprechen keinem vorhandenen Menüelement, daher müssen Sie für jede Stiftoption ein Menüelement erstellen.

   1. Öffnen Sie im Fenster **Ressourcenansicht** die **IDR_SCRIBBTYPE** Menüressource.

   1. Klicken Sie auf **Stift,** um das Stiftmenü zu öffnen. Klicken Sie dann `Thi&n Pen`auf Hier **eingeben** und geben Sie ein.

   1. Klicken Sie mit der rechten Maustaste auf den Text, den `ID_PEN_THIN_WIDTH`Sie zum Öffnen des **Eigenschaftenfensters** eingegeben haben, und ändern Sie dann die ID-Eigenschaft in .

   1. Erstellen Sie einen Ereignishandler für jedes Stiftmenüelement. Klicken Sie mit der rechten Maustaste auf das Menüelement **Thi&n Pen,** das Sie erstellt haben, und klicken Sie dann auf **Ereignishandler hinzufügen**. Der **Ereignishandler-Assistent** wird angezeigt.

   1. Wählen Sie im **Listenfeld Klasse** im Assistenten **CScribbleDoc** aus, und klicken Sie dann auf **Hinzufügen und Bearbeiten**. Der Befehl erstellt einen `CScribbleDoc::OnPenThinWidth`Ereignishandler mit dem Namen .

   1. Fügen Sie `CScribbleDoc::OnPenThinWidth` den folgenden Code hinzu.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Erstellen Sie als Nächstes ein Menüelement und Ereignishandler für den dicken Stift.

   1. Öffnen Sie im Fenster **Ressourcenansicht** die **IDR_SCRIBBTYPE** Menüressource.

   1. Klicken Sie auf **Stift,** um das Stiftmenü zu öffnen. Klicken Sie dann `Thic&k Pen`auf Hier **eingeben** und geben Sie ein.

   1. Klicken Sie mit der rechten Maustaste auf den Text, den Sie eingegeben haben, um das **Eigenschaftenfenster** anzuzeigen. Ändern Sie die `ID_PEN_THICK_WIDTH`ID-Eigenschaft in .

   1. Klicken Sie mit der rechten Maustaste auf das Menüelement **"Dickstift",** das Sie erstellt haben, und klicken Sie dann auf **Ereignishandler hinzufügen**. Der **Ereignishandler-Assistent** wird angezeigt.

   1. Wählen Sie im **Listenfeld Klasse** des Assistenten **CScribbleDoc** aus, und klicken Sie dann auf **Hinzufügen und Bearbeiten**. Der Befehl erstellt einen `CScribbleDoc::OnPenThickWidth`Ereignishandler mit dem Namen .

   1. Fügen Sie `CScribbleDoc::OnPenThickWidth` den folgenden Code hinzu.

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Neue Schaltflächen und Kombinationsfelder sollten angezeigt werden. Versuchen Sie, verschiedene Stiftbreiten zu verwenden, um zu kritzeln.

## <a name="adding-a-color-button-to-the-pen-panel"></a><a name="addcolorbutton"></a>Hinzufügen einer Farbschaltfläche zum Stiftbedienfeld

Fügen Sie als Nächstes ein [CMFCRibbonColorButton-Objekt](../mfc/reference/cmfcribboncolorbutton-class.md) hinzu, mit dem der Benutzer in Farbe kritzeln kann.

### <a name="to-add-a-color-button-to-the-pen-panel"></a>So fügen Sie dem Stiftbedienfeld eine Farbschaltfläche hinzu

1. Bevor Sie die Farbschaltfläche hinzufügen, erstellen Sie ein Menüelement dafür. Öffnen Sie im Fenster **Ressourcenansicht** die **IDR_SCRIBBTYPE** Menüressource. Klicken Sie auf das Menüelement **Stift,** um das Stiftmenü zu öffnen. Klicken Sie dann `&Color`auf Hier **eingeben** und geben Sie ein. Klicken Sie mit der rechten Maustaste auf den Text, den Sie eingegeben haben, um das **Eigenschaftenfenster** anzuzeigen. Ändern Sie die ID in `ID_PEN_COLOR`.

1. Fügen Sie nun die Farbschaltfläche hinzu. Ziehen Sie aus der **Toolbox**eine **Farbschaltfläche** in das **Stiftbedienfeld.**

1. Klicken Sie auf die Farbschaltfläche. Ändern Sie `Color` **Beschriftung** `ID_PEN_COLOR`in , **ID** in , `1` **Einfaches Suchen** nach `True`, **Großer Bildindex** in und **Split Mode** in `False`.

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Die neue Farbschaltfläche sollte auf dem **Stiftbedienfeld** angezeigt werden. Es kann jedoch nicht verwendet werden, da es noch keinen Ereignishandler hat. In den nächsten Schritten wird gezeigt, wie Sie einen Ereignishandler für die Farbschaltfläche hinzufügen.

## <a name="adding-a-color-member-to-the-document-class"></a><a name="addcolormember"></a>Hinzufügen eines Farbmitglieds zur Dokumentklasse

Da die ursprüngliche Scribble-Anwendung nicht über Farbstifte enthält, müssen Sie eine Implementierung für sie schreiben. Um die Stiftfarbe des Dokuments zu speichern, fügen `CscribbleDoc`Sie der Dokumentklasse einen neuen Member hinzu.

### <a name="to-add-a-color-member-to-the-document-class"></a>So fügen Sie der Dokumentklasse einen Farbmember hinzu

1. In scribdoc.h, `CScribbleDoc` in der `// Attributes` Klasse, finden Sie den Abschnitt. Fügen Sie die folgenden Codezeilen `m_nThickWidth` nach der Definition des Datenelements hinzu.

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. Jedes Dokument enthält eine Liste von Stokes, die der Benutzer bereits gezeichnet hat. Jeder Strich wird `CStroke` durch ein Objekt definiert. Die `CStroke` Klasse enthält keine Informationen zur Stiftfarbe, daher müssen Sie die Klasse ändern. Fügen Sie in scribdoc.h in der `CStroke` Klasse die folgenden `m_nPenWidth` Codezeilen nach der Definition des Datenmembers hinzu.

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. Fügen Sie in scribdoc.h einen neuen `CStroke` Konstruktor hinzu, dessen Parameter eine Breite und Farbe angeben. Fügen Sie die folgende `CStroke(UINT nPenWidth);` Codezeile nach der Anweisung hinzu.

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. Fügen Sie in scribdoc.cpp die `CStroke` Implementierung des neuen Konstruktors hinzu. Fügen Sie den folgenden Code `CStroke::CStroke(UINT nPenWidth)` nach der Implementierung des Konstruktors hinzu.

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. Ändern Sie die `CStroke::DrawStroke` zweite Zeile der Methode wie folgt.

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. Legen Sie die Standardstiftfarbe für die Dokumentklasse fest. Fügen Sie in scribdoc.cpp `CScribbleDoc::InitDocument`die folgenden `m_nThickWidth = 5;` Zeilen nach der Anweisung hinzu.

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. Ändern Sie in scribdoc.cpp die `CScribbleDoc::NewStroke` erste Zeile der Methode in die folgende Zeile.

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. Ändern Sie die `CScribbleDoc::ReplacePen` letzte Zeile der Methode in die folgende Zeile.

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. Sie haben `m_penColor` das Mitglied in einem vorherigen Schritt hinzugefügt. Erstellen Sie nun einen Ereignishandler für die Farbschaltfläche, die das Element festlegt.

   1. Öffnen Sie im Fenster **Ressourcenansicht** die IDR_SCRIBBTYPE Menüressource.

   1. Klicken Sie mit der rechten Maustaste auf das Menüelement **Farbe,** und klicken Sie auf **Ereignishandler hinzufügen**. Der **Ereignishandler-Assistent** wird angezeigt.

   1. Wählen Sie im **Listenfeld Klasse** im Assistenten **CScribbleDoc** aus, und klicken Sie dann auf die Schaltfläche **Hinzufügen und Bearbeiten.** Der Befehl `CScribbleDoc::OnPenColor` erstellt den Ereignishandler-Stub.

1. Ersetzen Sie den `CScribbleDoc::OnPenColor` Stub für den Ereignishandler durch den folgenden Code.

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Sie können nun die Farbtaste drücken und die Farbe des Stifts ändern.

## <a name="initializing-pens-and-saving-preferences"></a><a name="initpensave"></a>Initialisieren von Stiften und Spareinstellungen

Als Nächstes initialisieren Sie die Farbe und Breite der Stifte. Speichern und laden Sie schließlich eine Farbzeichnung aus einer Datei.

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>So initialisieren Sie Steuerelemente auf der Multifunktionsleistenleiste

1. Initialisieren Sie die Stifte auf der Multifunktionsleiste.

   Fügen Sie den folgenden Code zu scribdoc.cpp in der `CScribbleDoc::InitDocument` Methode nach der `m_sizeDoc = CSize(200,200)` Anweisung hinzu.

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. Speichern Sie eine Farbzeichnung in einer Datei. Fügen Sie die folgende Anweisung zu scribdoc.cpp in der `CStroke::Serialize` Methode nach der `ar << (WORD)m_nPenWidth;` Anweisung hinzu.

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. Laden Sie schließlich eine Farbzeichnung aus einer Datei. Fügen Sie die folgende Codezeile in `CStroke::Serialize` `m_nPenWidth = w;` der Methode nach der Anweisung hinzu.

   ```cpp
   ar >> m_penColor;
   ```

1. Jetzt kritzeln Sie in Farbe und speichern Sie Ihre Zeichnung in einer Datei.

## <a name="conclusion"></a>Zusammenfassung

Sie haben die MFC Scribble-Anwendung aktualisiert. Verwenden Sie diese exemplarische Vorgehensweise als Leitfaden, wenn Sie Ihre vorhandenen Anwendungen ändern.

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweisen](../mfc/walkthroughs-mfc.md)<br/>
[Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
