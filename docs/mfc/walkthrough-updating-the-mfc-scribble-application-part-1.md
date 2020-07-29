---
title: 'Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 1)'
ms.date: 09/09/2019
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 9fc2903180a055c18c6f3779b1da55ee347d2535
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230427"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 1)

In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie eine vorhandene MFC-Anwendung so ändern, dass die Menüband-Benutzeroberfläche verwendet wird. Visual Studio unterstützt sowohl das Menüband von Office 2007 als auch das "Scenic Ribbon" von Windows 7. Weitere Informationen zur Menüband-Benutzeroberfläche finden Sie [Ribbons](/windows/win32/uxguide/cmd-ribbons)unter Multifunktionsleisten.

In dieser exemplarischen Vorgehensweise wird das klassische MFC-Beispiel Scribble 1.0 geändert, das Ihnen ermöglicht, mit der Maus Strichzeichnungen zu erstellen. In diesem Teil der exemplarischen Vorgehensweise wird gezeigt, wie das Scribble-Beispiel so geändert wird, dass es eine Menübandleiste anzeigt. [Teil 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) fügt der Menü Band Leiste weitere Schaltflächen hinzu.

## <a name="prerequisites"></a>Voraussetzungen

Das [Scribble 1,0 MFC-Beispiel](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Hilfe bei der Umstellung auf Visual Studio 2017 oder höher finden Sie unter [Leitfaden zum Portieren: MFC Scribble](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a>Strecken

Dieser Teil der exemplarischen Vorgehensweise enthält die folgenden Abschnitte:

- [Ersetzen der Basisklassen](#replaceclass)

- [Hinzufügen von Bitmaps zum Projekt](#addbitmap)

- [Hinzufügen einer Menübandressource zum Projekt](#addribbon)

- [Erstellen einer Instanz der Menübandleiste](#createinstance)

- [Hinzufügen einer Menübandkategorie](#addcategory)

- [Festlegen der Darstellung der Anwendung](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>Ersetzen der Basisklassen

Zum Konvertieren einer Anwendung, die ein Menü unterstützt, in eine Anwendung, die ein Menüband unterstützt, müssen Sie die Anwendung, das Rahmenfenster und die Symbolleistenklassen von den aktualisierten Basisklassen ableiten. (Wir empfehlen, dass Sie das ursprüngliche Scribble-Beispiel nicht ändern. Bereinigen Sie stattdessen das Scribble-Projekt, kopieren Sie es in ein anderes Verzeichnis, und ändern Sie dann die Kopie.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>So ersetzen Sie die Basisklassen in der Scribble-Anwendung

1. Vergewissern Sie sich in Scribble. cpp, dass `CScribbleApp::InitInstance` einen [AfxOLEInit](../mfc/reference/ole-initialization.md#afxoleinit)-aufzurufenden enthält.

1. Fügen Sie den folgenden Code in die Datei " *PCH. h* " ein (*stdafx. h* in Visual Studio 2017 und früher):

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. Ändern Sie in Scribble. h die Definition für die `CScribbleApp` -Klasse so, dass Sie von der [CWinAppEx-Klasse](../mfc/reference/cwinappex-class.md)abgeleitet wird.

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 wurde geschrieben, als Windows-Anwendungen eine Initialisierungsdatei (.ini) verwendeten, um die Benutzereinstellungen zu speichern. Ändern Sie Scribble so, dass die Benutzereinstellungen statt in einer Initialisierungsdatei in der Registrierung gespeichert werden. Um den Registrierungsschlüssel und die Basis festzulegen, geben Sie den folgenden Code in `CScribbleApp::InitInstance` nach der `LoadStdProfileSettings()`-Anweisung ein.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Der Hauptframe für eine MDI-Anwendung (Multiple Document Interface) wird nicht mehr von der `CMDIFrameWnd`-Klasse abgeleitet. Stattdessen wird Sie von der [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) -Klasse abgeleitet.

    Ersetzen Sie in den Dateien "mainfrm.h" und "mainfrm.cpp" alle Verweise auf `CMDIFrameWnd` durch `CMDIFrameWndEx`.

1. Ersetzen Sie in den Dateien "childfrm.h" und "childfrm.cpp" `CMDIChildWnd` durch `CMDIChildWndEx`.

    In der CHILDFRM. h-Datei, `CSplitterWnd` durch ersetzen `CSplitterWndEx` .

1. Ändern Sie die Symbolleisten und die Statusleisten so, dass die neuen MFC-Klassen verwendet werden.

    Führen Sie in der Datei "mainfrm.h" folgende Schritte aus:

    1. Ersetzen Sie `CToolBar` durch `CMFCToolBar`.

    1. Ersetzen Sie `CStatusBar` durch `CMFCStatusBar`.

1. Führen Sie in der Datei "mainfrm.cpp" folgende Schritte aus:

    1. Ersetzen Sie `m_wndToolBar.SetBarStyle` durch `m_wndToolBar.SetPaneStyle`.

    1. Ersetzen Sie `m_wndToolBar.GetBarStyle` durch `m_wndToolBar.GetPaneStyle`.

    1. Ersetzen Sie `DockControlBar(&m_wndToolBar)` durch `DockPane(&m_wndToolBar)`.

1. Kommentieren Sie in der Datei "ipframe.cpp" die folgenden drei Codezeilen aus.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus.

## <a name="adding-bitmaps-to-the-project"></a><a name="addbitmap"></a>Hinzufügen von Bitmaps zum Projekt

Für die nächsten vier Schritte dieser exemplarischen Vorgehensweise sind Bitmapressourcen erforderlich. Die entsprechenden Bitmaps können auf verschiedene Arten angezeigt werden:

- Verwenden Sie die [Ressourcen-Editoren](../windows/resource-editors.md) , um eigene Bitmaps zu erfinden. Oder verwenden Sie die Ressourcen-Editoren, um Bitmaps aus den Images der portablen Netzwerk Grafiken (PNG) zusammenzustellen, die in Visual Studio enthalten sind und aus der [Visual Studio-Bildbibliothek](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)heruntergeladen werden können.

    Die **Menüband** -Benutzeroberfläche erfordert jedoch, dass bestimmte Bitmaps transparente Bilder unterstützen. Transparente Bitmaps verwenden 32-Bit-Pixel, wobei 24 Bits die roten, grünen und blauen Komponenten der Farbe angeben und 8 Bits einen *Alphakanal* definieren, der die Transparenz der Farbe angibt. Die aktuellen Ressourcen-Editoren können Bitmaps mit 32 Bits/Pixel anzeigen, aber nicht ändern. Verwenden Sie daher einen externen Bild-Editor anstelle der Ressourcen-Editoren, um transparente Bitmaps zu bearbeiten.

- Kopieren Sie eine entsprechende Ressourcendatei aus einer anderen Anwendung in Ihr Projekt, und importieren Sie dann Bitmaps von dieser Datei.

Diese exemplarische Vorgehensweise kopiert Ressourcen Dateien aus dem Beispiel, das in Exemplarische Vorgehensweise [: Erstellen einer Multifunktionsleistenanwendung mit MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)erstellt wurde.

### <a name="to-add-bitmaps-to-the-project"></a>So fügen Sie dem Projekt Bitmaps hinzu

1. Verwenden Sie den Datei-Explorer, um die folgenden BMP-Dateien aus dem Ressourcenverzeichnis ( `res` ) des Menüband-Beispiels in das Ressourcenverzeichnis ( `res` ) des Scribble-Projekts zu kopieren:

   1. Kopieren Sie "main.bmp" in Ihr Scribble-Projekt.

   1. Kopieren Sie "filesmall.bmp" und "filelarge.bmp" in Ihr Scribble-Projekt.

   1. Erstellen Sie neue Kopien der filelarge.bmp und filesmall.bmp Dateien, speichern Sie die Kopien jedoch im Menüband-Beispiel. Benennen Sie die Kopien in "homesmall.bmp" und "homelarge.bmp" um, und verschieben Sie sie dann in das Scribble-Projekt.

   1. Erstellen Sie eine Kopie der toolbar.bmp Datei, speichern Sie die Kopie jedoch im Menüband-Beispiel. Benennen Sie die Kopie in "panelicons.bmp" um, und verschieben Sie sie dann in das Scribble-Projekt.

1. Importieren Sie die Bitmap für eine MFC-Anwendung. Doppelklicken Sie in **Ressourcenansicht**auf den Knoten **Scribble. RC** , doppelklicken Sie auf den Knoten **Bitmap** , und klicken Sie dann auf **Ressource hinzufügen**. Klicken Sie im angezeigten Dialogfeld auf **importieren**. Navigieren Sie zum `res` Verzeichnis, wählen Sie die Datei main.bmp aus, und klicken Sie dann auf **Öffnen**.

   Die Bitmap "main.bmp" enthält ein 26x26-Bild. Ändern Sie die ID der Bitmap in `IDB_RIBBON_MAIN` .

1. Importieren Sie die Bitmaps für das Menü Datei, das an die **Anwendungs** Schaltfläche angefügt ist.

   1. Importieren Sie die Datei filesmall.bmp, die elf 16x16-Bilder (16x176) enthält. Ändern Sie die ID der Bitmap in `IDB_RIBBON_FILESMALL` .

   > [!NOTE]
   > Da wir nur die ersten acht 16x16-Bilder (16x128) benötigen, können Sie optional die Rechte Breite dieser Bitmap von 176 auf 128 zuschneiden.

   1. Importieren Sie das filelarge.bmp, das neun 32 x 32-Bilder (32x288) enthält. Ändern Sie die ID der Bitmap in `IDB_RIBBON_FILELARGE` .

1. Importieren Sie die Bitmaps für die Menübandkategorien und -bereiche. Jede Registerkarte in der Menübandleiste ist eine Kategorie und besteht aus einer Textbezeichnung und einem optionalen Bild.

   1. Importieren Sie das homesmall.bmp Bitmap, das elf 16x16-Bilder für Bitmaps mit kleinen Schaltflächen enthält. Ändern Sie die ID der Bitmap in `IDB_RIBBON_HOMESMALL` .

   1. Importieren Sie das homelarge.bmp Bitmap, das neun 32 x 32-Bilder für Bitmaps mit großen Schaltflächen enthält. Ändern Sie die ID der Bitmap in `IDB_RIBBON_HOMELARGE` .

1. Importieren Sie Bitmaps für die Menübandbereiche, deren Größe geändert wurde. Diese Bitmaps oder Bereichssymbole werden nach einer Größenänderung verwendet, wenn das Menüband zu klein ist, um den gesamten Bereich anzuzeigen.

   1. Importieren Sie die Bitmap "panelicons.bmp", die acht 16x16-Bilder enthält. Passen Sie im Fenster **Eigenschaften** des **Bitmap-Editors**die Breite der Bitmap auf 64 (16X64) an. Ändern Sie die ID der Bitmap in `IDB_PANEL_ICONS` .

   > [!NOTE]
   > Da wir nur die ersten vier 16x16-Bilder (16X64) benötigen, können Sie optional die Rechte Breite dieser Bitmap von 128 auf 64 zuschneiden.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>Hinzufügen einer Menü Band Ressource zum Projekt

Wenn Sie eine Anwendung, die Menüs verwendet, in eine Anwendung konvertieren, die ein Menüband verwendet, müssen Sie die vorhandenen Menüs nicht entfernen oder deaktivieren. Erstellen Sie einfach eine Menü Band Ressource, fügen Sie Menüband-Schaltflächen hinzu, und ordnen Sie dann die neuen Schaltflächen den vorhandenen Menü Elementen zu Obwohl die Menüs nicht mehr sichtbar sind, werden die Nachrichten von der Menü Band Leiste über die Menüs weitergeleitet, und Menü Verknüpfungen funktionieren weiterhin.

Ein Menüband besteht aus der **Anwendungs** Schaltfläche, bei der es sich um die große Schaltfläche auf der oberen linken Seite des Menübands handelt, und mindestens einer kategorieregister Karte. Jede Kategorienregisterkarte enthält einen oder mehrere Bereiche, die als Container für Menübandschaltflächen und Steuerelemente dienen. Im folgenden Verfahren wird gezeigt, wie Sie eine Menü Band Ressource erstellen und dann die **Anwendungs** Schaltfläche anpassen.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>So fügen Sie dem Projekt eine Menübandressource hinzu

1. Wenn das Scribble-Projekt in **Projektmappen-Explorer**ausgewählt ist, klicken Sie im Menü **Projekt** auf **Ressource hinzufügen**.

1. Wählen Sie im Dialogfeld **Ressource hinzufügen** die Option **Menüband** aus, und klicken Sie auf **neu**.

   Visual Studio erstellt eine Menübandressource und öffnet sie in der Designansicht. Die Menüband-Ressourcen-ID ist `IDR_RIBBON1` , die in **Ressourcenansicht**angezeigt wird. Das Menüband enthält eine Kategorie und einen Bereich.

1. Sie können die **Anwendungs** Schaltfläche anpassen, indem Sie Ihre Eigenschaften ändern. Die Meldungs-IDs, die in diesem Code verwendet werden, sind bereits im Menü für Scribble 1.0 definiert.

1. Klicken Sie in der Entwurfs Ansicht auf die **Anwendungs** Schaltfläche, um die zugehörigen Eigenschaften anzuzeigen. Ändern Sie die Eigenschaftswerte wie folgt: **Bild** in `IDB_RIBBON_MAIN` , **Eingabeaufforderung** , `File` **Schlüssel** zu `f` , **große Bilder** bis `IDB_RIBBON_FILELARGE` und **kleine Bilder** zu `IDB_RIBBON_FILESMALL` .

1. Die folgenden Änderungen erstellen das Menü, das angezeigt wird, wenn der Benutzer auf die **Anwendungs** Schaltfläche klickt. Klicken Sie auf das Auslassungs Zeichen (**...**) neben **Hauptelemente** , um den **Editor für Elemente**zu öffnen.

   1. Klicken Sie bei ausgewähltem **Elementtyp auf** **Hinzufügen** , um eine **Schaltfläche hinzu** zufügen. Ändern Sie **Beschriftung** in `&New` , **ID** in `ID_FILE_NEW` , **Bild** in, `0` **Bild groß** in `0` .

   1. Klicken Sie zum Hinzufügen einer Schaltfläche auf **Hinzufügen** . Ändern Sie **Beschriftung** in `&Save` , **ID** in `ID_FILE_SAVE` , **Bild** in `2` und **Bild groß** in `2` .

   1. Klicken Sie zum Hinzufügen einer Schaltfläche auf **Hinzufügen** . Ändern Sie **Beschriftung** in `Save &As` , **ID** in `ID_FILE_SAVE_AS` , **Bild** in `3` und **Bild groß** in `3` .

   1. Klicken Sie zum Hinzufügen einer Schaltfläche auf **Hinzufügen** . Ändern Sie **Beschriftung** in `&Print` , **ID** in `ID_FILE_PRINT` , **Bild** in `4` und **Bild groß** in `4` .

   1. Ändern Sie den **Elementtyp in** **Separator** , und klicken Sie dann auf **Hinzufügen**.

   1. Ändern Sie den **Elementtyp in** " **Schaltfläche**". Klicken Sie zum Hinzufügen einer fünften Schaltfläche **Hinzufügen** . Ändern Sie **Beschriftung** in `&Close` , **ID** in `ID_FILE_CLOSE` , **Bild** in `5` und **Bild groß** in `5` .

1. Mit den folgenden Änderungen wird ein Untermenü unter der Schaltfläche **Drucken** erstellt, das Sie im vorherigen Schritt erstellt haben.

   1. Klicken Sie **auf die Schalt** Fläche **Drucken** , ändern Sie den Elementtyp in **Bezeichnung**, und klicken Sie dann auf **Einfügen**. Ändern Sie die **Beschriftung** in `Preview and print the document` .

   1. Klicken Sie **auf die Schalt** Fläche **Drucken** , ändern Sie den Elementtyp in **Schaltfläche**, und klicken Sie auf **Einfügen**. Ändern Sie **Beschriftung** in `&Print` , **ID** in `ID_FILE_PRINT` , **Bild** in `4` und **Bild groß** in `4` .

   1. Klicken Sie auf die Schaltfläche **Drucken** und dann auf **Einfügen** , um eine Schaltfläche hinzuzufügen. Ändern Sie **Beschriftung** in `&Quick Print` , **ID** in `ID_FILE_PRINT_DIRECT` , **Bild** in `7` und **Bild groß** in `7` .

   1. Klicken Sie auf die Schaltfläche **Drucken** und dann auf **Einfügen** , um eine weitere Schaltfläche hinzuzufügen Ändern Sie **Beschriftung** in `Print Pre&view` , **ID** in `ID_FILE_PRINT_PREVIEW` , **Bild** in `6` und **Bild groß** in `6` .

   1. Sie haben nun die **Hauptelemente**geändert. Klicken Sie auf **Schließen** , um den **Elemente-Editor**zu beenden

1. Mit der folgenden Änderung wird eine Schaltfläche Beenden erstellt, die am unteren Rand des **Anwendungs** Schaltflächen Menüs angezeigt wird.

   1. Wählen Sie in **Projektmappen-Explorer**die Registerkarte **Ressourcenansicht** .
   1. Klicken Sie im Fenster **Eigenschaften** auf die Schaltfläche mit den Auslassungs Punkten (**...**) neben **Schaltfläche** , um den **Elemente-Editor**zu öffnen.

   1. Klicken Sie bei ausgewähltem **Elementtyp auf** **Hinzufügen** , um eine **Schaltfläche hinzu** zufügen. Ändern Sie **Beschriftung** in `E&xit` , **ID** in `ID_APP_EXIT` , **Image** in `8` .

   1. Sie haben die **Schalt**Flächen geändert. Klicken Sie auf **Schließen** , um den **Elemente-Editor**zu beenden

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>Erstellen einer Instanz der Menü Band Leiste

Die folgenden Schritte zeigen, wie beim Starten Ihrer Anwendung eine Instanz der Menübandleiste erstellt wird. Um eine Menübandleiste zu einer Anwendung hinzuzufügen, deklarieren Sie die Menübandleiste in der Datei "mainfrm.h". Schreiben Sie dann in der Datei "mainfrm.cpp" Code zum Laden der Menübandressource.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>So erstellen Sie eine Instanz der Menübandleiste

1. Fügen Sie in der Datei "mainfrm.h" einen Datenmember zum geschützten Abschnitt von `CMainFrame`, der Klassendefinition für den Hauptframe, hinzu. Dieser Member ist für die Menü Band Leiste.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Fügen Sie in der Datei "mainfrm. cpp" den folgenden Code vor der letzten- **`return`** Anweisung am Ende der- `CMainFrame::OnCreate` Funktion hinzu. Es wird eine Instanz der Menü Band Leiste erstellt.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>Anpassen der Menüband-Ressource

Nachdem Sie die **Anwendungs** Schaltfläche erstellt haben, können Sie dem Menüband Elemente hinzufügen.

> [!NOTE]
> In dieser exemplarischen Vorgehensweise wird das gleiche Bereichssymbol für alle Bereiche verwendet. Sie können jedoch auch andere Bildlistenindizes verwenden, um andere Symbole anzuzeigen.

### <a name="to-add-a-home-category-and-edit-panel"></a>So fügen Sie eine Kategorie "Startseite" und einen Bereich "Bearbeiten" hinzu

1. Das Scribble-Programm erfordert nur eine Kategorie. Doppelklicken Sie in der Entwurfs Ansicht in der **Toolbox**auf **Category** , um eine hinzuzufügen und die zugehörigen Eigenschaften anzuzeigen. Ändern Sie die Eigenschaftswerte wie folgt: **Beschriftung** in `&Home` , **große Bilder** in `IDB_RIBBON_HOMELARGE` , **kleine Bilder** in `IDB_RIBBON_HOMESMALL` .

1. Jede Menübandkategorie ist in benannte Bereiche unterteilt. Jeder Bereich enthält eine Reihe von Steuerelementen, die Verwandte Vorgänge vervollständigen. Diese Kategorie verfügt über einen Bereich. Klicken Sie auf **Panel**, und ändern Sie dann die **Beschriftung** in `Edit` .

1. Fügen Sie dem **Bearbeitungs** Bereich eine Schaltfläche hinzu, die für das Löschen des Inhalts des Dokuments zuständig ist. Die Nachrichten-ID für diese Schaltfläche wurde bereits in der `IDR_SCRIBBTYPE` Menü Ressource definiert. Geben Sie `Clear All` als Schaltflächen Text und den Index der Bitmap an, der die Schaltfläche schmückt. Öffnen Sie die **Toolbox**, und ziehen Sie dann eine **Schaltfläche** in den **Bearbeitungs** Bereich. Klicken Sie auf die Schaltfläche, und ändern Sie dann **Beschriftung** in `Clear All` , **ID** in `ID_EDIT_CLEAR_ALL` , **Image Index** in `0` , **Large Image Index** in `0` .

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Die Scribble-Anwendung sollte angezeigt werden, und sie sollte am oberen Rand des Fensters über eine Menübandleiste anstelle einer Menüleiste verfügen. Die Menü Band Leiste sollte eine Kategorie, eine " **Home**" und " **Home** " einen Bereich haben, " **Bearbeiten**". Die Menü Band Schaltflächen, die Sie hinzugefügt haben, sollten den vorhandenen Ereignis Handlern zugeordnet sein, und die Schaltflächen **Öffnen**, **Schließen**, **Speichern**, **Drucken**und **Alle löschen** sollten erwartungsgemäß funktionieren.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>Das Aussehen der Anwendung wird festgelegt.

Bei einem *visuellen Manager* handelt es sich um ein globales Objekt, das alle Zeichnungen für eine Anwendung steuert. Da die ursprüngliche Scribble-Anwendung die Benutzeroberfläche im Office 2000-Stil nutzt, sieht die Anwendung möglicherweise altmodisch aus. Sie können die Anwendung zurücksetzen, um den visuellen Manager "Office 2007" zu verwenden, sodass sie einer Office 2007-Anwendung ähnelt.

### <a name="to-set-the-look-of-the-application"></a>So legen Sie die Darstellung der Anwendung fest

1. `CMainFrame::OnCreate`Geben Sie in der-Funktion den folgenden Code vor der `return 0;` -Anweisung ein, um den standardmäßigen visuellen Manager und Stil zu ändern.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Die Anwendungsbenutzeroberfläche sollte der Office 2007-Benutzeroberfläche ähneln.

## <a name="next-steps"></a>Nächste Schritte

Sie haben das klassische Scribble 1,0 MFC-Beispiel geändert, um den **Menüband-Designer**zu verwenden. Wechseln Sie jetzt zu [Teil 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweisen](../mfc/walkthroughs-mfc.md)<br/>
[Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
