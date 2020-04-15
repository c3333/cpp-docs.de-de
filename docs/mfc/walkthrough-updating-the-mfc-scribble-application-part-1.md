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
ms.openlocfilehash: 18803d2222c80b80ac2b1fde75b442ea1e9a89bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360259"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 1)

In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie eine vorhandene MFC-Anwendung so ändern, dass die Menüband-Benutzeroberfläche verwendet wird. Visual Studio unterstützt sowohl das Menüband von Office 2007 als auch das "Scenic Ribbon" von Windows 7. Weitere Informationen zur Multifunktionsleisten-Benutzeroberfläche finden Sie unter [Multifunktionsleisten](/windows/win32/uxguide/cmd-ribbons).

In dieser exemplarischen Vorgehensweise wird das klassische MFC-Beispiel Scribble 1.0 geändert, das Ihnen ermöglicht, mit der Maus Strichzeichnungen zu erstellen. In diesem Teil der exemplarischen Vorgehensweise wird gezeigt, wie das Scribble-Beispiel so geändert wird, dass es eine Menübandleiste anzeigt. [Teil 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) fügt der Multifunktionsleisten weitere Schaltflächen hinzu.

## <a name="prerequisites"></a>Voraussetzungen

Das [Scribble 1.0 MFC-Beispiel](https://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Hilfe zum Konvertieren in Visual Studio 2017 oder höher finden Sie unter [Portierungshandbuch: MFC Scribble](../porting/porting-guide-mfc-scribble.md).

## <a name="sections"></a><a name="top"></a>Bereichen

Dieser Teil der exemplarischen Vorgehensweise enthält die folgenden Abschnitte:

- [Ersetzen der Basisklassen](#replaceclass)

- [Hinzufügen von Bitmaps zum Projekt](#addbitmap)

- [Hinzufügen einer Menübandressource zum Projekt](#addribbon)

- [Erstellen einer Instanz der Menübandleiste](#createinstance)

- [Hinzufügen einer Menübandkategorie](#addcategory)

- [Festlegen der Darstellung der Anwendung](#setlook)

## <a name="replacing-the-base-classes"></a><a name="replaceclass"></a>Ersetzen der Basisklassen

Zum Konvertieren einer Anwendung, die ein Menü unterstützt, in eine Anwendung, die ein Menüband unterstützt, müssen Sie die Anwendung, das Rahmenfenster und die Symbolleistenklassen von den aktualisierten Basisklassen ableiten. (Wir empfehlen, dass Sie das ursprüngliche Scribble-Beispiel nicht ändern. Reinigen Sie stattdessen das Scribble-Projekt, kopieren Sie es in ein anderes Verzeichnis, und ändern Sie dann die Kopie.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>So ersetzen Sie die Basisklassen in der Scribble-Anwendung

1. Überprüfen Sie in scribble.cpp, dass `CScribbleApp::InitInstance` ein Aufruf von [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit)enthalten ist.

1. Fügen Sie der *Datei pch.h* (*stdafx.h* in Visual Studio 2017 und früher) den folgenden Code hinzu:

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. Ändern Sie in scribble.h `CScribbleApp` die Definition für die Klasse so, dass sie von [der CWinAppEx-Klasse](../mfc/reference/cwinappex-class.md)abgeleitet ist.

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 wurde geschrieben, als Windows-Anwendungen eine Initialisierungsdatei (.ini) verwendeten, um die Benutzereinstellungen zu speichern. Ändern Sie Scribble so, dass die Benutzereinstellungen statt in einer Initialisierungsdatei in der Registrierung gespeichert werden. Um den Registrierungsschlüssel und die Basis festzulegen, geben Sie den folgenden Code in `CScribbleApp::InitInstance` nach der `LoadStdProfileSettings()`-Anweisung ein.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. Der Hauptframe für eine MDI-Anwendung (Multiple Document Interface) wird nicht mehr von der `CMDIFrameWnd`-Klasse abgeleitet. Stattdessen wird es von der [CMDIFrameWndEx-Klasse](../mfc/reference/cmdiframewndex-class.md) abgeleitet.

    Ersetzen Sie in den Dateien "mainfrm.h" und "mainfrm.cpp" alle Verweise auf `CMDIFrameWnd` durch `CMDIFrameWndEx`.

1. Ersetzen Sie in den Dateien "childfrm.h" und "childfrm.cpp" `CMDIChildWnd` durch `CMDIChildWndEx`.

    Im Kinderfrm. h-Datei, `CSplitterWnd` `CSplitterWndEx`ersetzen durch .

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

Für die nächsten vier Schritte dieser exemplarischen Vorgehensweise sind Bitmapressourcen erforderlich. Sie können die entsprechenden Bitmaps auf verschiedene Arten abrufen:

- Verwenden Sie die [Ressourcen-Editoren,](../windows/resource-editors.md) um Ihre eigenen Bitmaps zu erfinden. Oder verwenden Sie die Ressourcen-Editoren, um Bitmaps aus den Bildern des portablen Netzwerks (.png) zusammenzustellen, die in Visual Studio enthalten sind und aus der [Visual Studio-Bildbibliothek](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library)heruntergeladen werden können.

    Die **Multifunktionsleisten-Benutzeroberfläche** erfordert jedoch, dass bestimmte Bitmaps transparente Bilder unterstützen. Transparente Bitmaps verwenden 32-Bit-Pixel, wobei 24 Bit die roten, grünen und blauen Komponenten der Farbe angeben und 8 Bits einen *Alphakanal* definieren, der die Transparenz der Farbe angibt. Die aktuellen Ressourcen-Editoren können Bitmaps mit 32 Bits/Pixel anzeigen, aber nicht ändern. Verwenden Sie daher einen externen Bild-Editor anstelle der Ressourcen-Editoren, um transparente Bitmaps zu bearbeiten.

- Kopieren Sie eine entsprechende Ressourcendatei aus einer anderen Anwendung in Ihr Projekt, und importieren Sie dann Bitmaps von dieser Datei.

In dieser exemplarischen Vorgehensweise werden Ressourcendateien aus dem Beispiel kopiert, das in [Walkthrough: Erstellen einer Multifunktionsleistenanwendung mithilfe von MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md)erstellt wurde.

### <a name="to-add-bitmaps-to-the-project"></a>So fügen Sie dem Projekt Bitmaps hinzu

1. Verwenden Sie den Datei-Explorer, um die folgenden`res`BMP-Dateien aus dem`res`Ressourcenverzeichnis ( ) des Multifunktionsleistenbeispiels in das Ressourcenverzeichnis ( ) des Scribble-Projekts zu kopieren:

   1. Kopieren Sie "main.bmp" in Ihr Scribble-Projekt.

   1. Kopieren Sie "filesmall.bmp" und "filelarge.bmp" in Ihr Scribble-Projekt.

   1. Erstellen Sie neue Kopien der Dateien filelarge.bmp und filesmall.bmp, speichern Sie die Kopien jedoch im Multifunktionsleistenbeispiel. Benennen Sie die Kopien in "homesmall.bmp" und "homelarge.bmp" um, und verschieben Sie sie dann in das Scribble-Projekt.

   1. Erstellen Sie eine Kopie der Datei toolbar.bmp, aber speichern Sie die Kopie im Multifunktionsleistenbeispiel. Benennen Sie die Kopie in "panelicons.bmp" um, und verschieben Sie sie dann in das Scribble-Projekt.

1. Importieren Sie die Bitmap für eine MFC-Anwendung. Doppelklicken Sie in **der Ressourcenansicht**auf den Knoten **scribble.rc,** doppelklicken Sie auf den **Bitmap-Knoten,** und klicken Sie dann auf **Ressource hinzufügen**. Klicken Sie im angezeigten Dialogfeld auf **Importieren**. Navigieren Sie `res` zum Verzeichnis, wählen Sie die Datei main.bmp aus, und klicken Sie dann auf **Öffnen**.

   Die Bitmap "main.bmp" enthält ein 26x26-Bild. Ändern Sie die ID `IDB_RIBBON_MAIN`der Bitmap in .

1. Importieren Sie die Bitmaps für das Dateimenü, das an die Schaltfläche **Anwendung** angefügt ist.

   1. Importieren Sie die Datei filesmall.bmp, die elf 16x16 (16x176) Bilder enthält. Ändern Sie die ID `IDB_RIBBON_FILESMALL`der Bitmap in .

   > [!NOTE]
   > Da wir nur die ersten acht 16x16-Bilder (16x128) benötigen, können Sie optional die rechte Breite dieser Bitmap von 176 bis 128 zuschneiden.

   1. Importieren Sie die Dateilarge.bmp, die neun 32x32 (32x288) Bilder enthält. Ändern Sie die ID `IDB_RIBBON_FILELARGE`der Bitmap in .

1. Importieren Sie die Bitmaps für die Menübandkategorien und -bereiche. Jede Registerkarte in der Menübandleiste ist eine Kategorie und besteht aus einer Textbezeichnung und einem optionalen Bild.

   1. Importieren Sie die bitmap homesmall.bmp, die elf 16x16-Bilder für kleine Schaltflächenbitmaps enthält. Ändern Sie die ID `IDB_RIBBON_HOMESMALL`der Bitmap in .

   1. Importieren Sie die bitmap homelarge.bmp, die neun 32x32-Bilder für große Schaltflächenbitmaps enthält. Ändern Sie die ID `IDB_RIBBON_HOMELARGE`der Bitmap in .

1. Importieren Sie Bitmaps für die Menübandbereiche, deren Größe geändert wurde. Diese Bitmaps oder Bereichssymbole werden nach einer Größenänderung verwendet, wenn das Menüband zu klein ist, um den gesamten Bereich anzuzeigen.

   1. Importieren Sie die Bitmap "panelicons.bmp", die acht 16x16-Bilder enthält. Passen Sie im **Eigenschaftenfenster** des **Bitmap-Editors**die Breite der Bitmap auf 64 (16x64) an. Ändern Sie die ID `IDB_PANEL_ICONS`der Bitmap in .

   > [!NOTE]
   > Da wir nur die ersten vier 16x16-Bilder (16x64) benötigen, können Sie optional die rechte Breite dieser Bitmap von 128 bis 64 zuschneiden.

## <a name="adding-a-ribbon-resource-to-the-project"></a><a name="addribbon"></a>Hinzufügen einer Multifunktionsleistenressource zum Projekt

Wenn Sie eine Anwendung, die Menüs verwendet, in eine Anwendung konvertieren, die ein Menüband verwendet, müssen Sie die vorhandenen Menüs nicht entfernen oder deaktivieren. Erstellen Sie einfach eine Multifunktionsleistenressource, fügen Sie Multifunktionsleistenschaltflächen hinzu, und ordnen Sie die neuen Schaltflächen dann den vorhandenen Menüelementen zu. Obwohl die Menüs nicht mehr sichtbar sind, werden Nachrichten aus der Menüleistenleiste durch die Menüs weitergeleitet, und menüverknüpfungen funktionieren weiterhin.

Ein Menüband besteht aus der **Schaltfläche Anwendung,** d. h. der großen Schaltfläche auf der oberen linken Seite des Menübands, und einer oder mehreren Kategorieregisterkarten. Jede Kategorienregisterkarte enthält einen oder mehrere Bereiche, die als Container für Menübandschaltflächen und Steuerelemente dienen. Das folgende Verfahren zeigt, wie Sie eine Multifunktionsleistenressource erstellen und dann die **Schaltfläche Anwendung** anpassen.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>So fügen Sie dem Projekt eine Menübandressource hinzu

1. Wenn das Im **Projektmappen-Explorer**ausgewählte Scribble-Projekt im **Menü Projekt** auf **Ressource hinzufügen**klicken.

1. Wählen Sie im Dialogfeld **Ressource hinzufügen** **die Menübandauswahl** aus, und klicken Sie dann auf **Neu**.

   Visual Studio erstellt eine Menübandressource und öffnet sie in der Designansicht. Die Multifunktionsleistenressourcen-ID ist `IDR_RIBBON1`, die in der **Ressourcenansicht**angezeigt wird. Das Menüband enthält eine Kategorie und einen Bereich.

1. Sie können die **Schaltfläche Anwendung** anpassen, indem Sie deren Eigenschaften ändern. Die Meldungs-IDs, die in diesem Code verwendet werden, sind bereits im Menü für Scribble 1.0 definiert.

1. Klicken Sie in der Entwurfsansicht auf die Schaltfläche **Anwendung,** um deren Eigenschaften anzuzeigen. Ändern Sie Eigenschaftswerte `IDB_RIBBON_MAIN`wie folgt: **Image** to , `IDB_RIBBON_FILELARGE` **Aufforderung** an `File`, **Tasten** für `f`, Große **Bilder** in und **Kleine Bilder** in `IDB_RIBBON_FILESMALL`.

1. Mit den folgenden Änderungen wird das Menü erstellt, das angezeigt wird, wenn der Benutzer auf die Schaltfläche **Anwendung** klickt. Klicken Sie auf die Auslassungspunkte (**...**) neben **Hauptelemente,** um den **Items Editor**zu öffnen.

   1. Wenn Sie die **Schaltfläche** **Elementtyp** ausgewählt haben, klicken Sie auf **Hinzufügen,** um eine Schaltfläche hinzuzufügen. Ändern **Caption** Sie `&New`Beschriftung `ID_FILE_NEW`in , **ID** in `0`, **Bild** in `0`, Bild **groß** in .

   1. Klicken Sie auf **Hinzufügen,** um eine Schaltfläche hinzuzufügen. Ändern **Caption** Sie `&Save`Beschriftung `ID_FILE_SAVE`in , **ID** in `2`, **Bild** in `2`und Bild **Groß** in .

   1. Klicken Sie auf **Hinzufügen,** um eine Schaltfläche hinzuzufügen. Ändern **Caption** Sie `Save &As`Beschriftung `ID_FILE_SAVE_AS`in , **ID** in `3`, **Bild** in `3`und Bild **Groß** in .

   1. Klicken Sie auf **Hinzufügen,** um eine Schaltfläche hinzuzufügen. Ändern **Caption** Sie `&Print`Beschriftung `ID_FILE_PRINT`in , **ID** in `4`, **Bild** in `4`und Bild **Groß** in .

   1. Ändern Sie den **Elementtyp** in **Separator,** und klicken Sie dann auf **Hinzufügen**.

   1. Ändern Sie den **Artikeltyp** in **Schaltfläche**. Klicken Sie auf **Hinzufügen,** um eine fünfte Schaltfläche hinzuzufügen. Ändern **Caption** Sie `&Close`Beschriftung `ID_FILE_CLOSE`in , **ID** in `5`, **Bild** in `5`und Bild **Groß** in .

1. Mit den folgenden Änderungen wird ein Untermenü unter der Schaltfläche **Drucken** erstellt, die Sie im vorherigen Schritt erstellt haben.

   1. Klicken Sie auf die Schaltfläche **Drucken,** ändern Sie den **Artikeltyp** in **Beschriftung,** und klicken Sie dann auf **Einfügen**. Ändern Sie `Preview and print the document`die **Beschriftung** in .

   1. Klicken Sie auf die Schaltfläche **Drucken,** ändern Sie den **Artikeltyp** in **Schaltfläche**, und klicken Sie auf **Einfügen**. Ändern **Caption** Sie `&Print`Beschriftung `ID_FILE_PRINT`in , **ID** in `4`, **Bild** in `4`und Bild **Groß** in .

   1. Klicken Sie auf die Schaltfläche **Drucken,** und klicken Sie dann auf **Einfügen,** um eine Schaltfläche hinzuzufügen. Ändern **Caption** Sie `&Quick Print`Beschriftung `ID_FILE_PRINT_DIRECT`in , **ID** in `7`, **Bild** in `7`und Bild **Groß** in .

   1. Klicken Sie auf die Schaltfläche **Drucken,** und klicken Sie dann auf **Einfügen,** um eine weitere Schaltfläche hinzuzufügen. Ändern **Caption** Sie `Print Pre&view`Beschriftung `ID_FILE_PRINT_PREVIEW`in , **ID** in `6`, **Bild** in `6`und Bild **Groß** in .

   1. Sie haben jetzt die **Hauptelemente**geändert. Klicken Sie auf **Schließen,** um den **Element-Editor**zu beenden.

1. Mit der folgenden Änderung wird eine Exit-Schaltfläche erstellt, die unten im Menü **anwendungsschaltfläche** angezeigt wird.

   1. Wählen Sie die Registerkarte **Ressourcenansicht** im **Projektmappen-Explorer**aus.
   1. Klicken Sie im **Eigenschaftenfenster** auf die Auslassungspunkte (**...**) neben **Button,** um den **Element-Editor**zu öffnen.

   1. Wenn Sie die **Schaltfläche** **Elementtyp** ausgewählt haben, klicken Sie auf **Hinzufügen,** um eine Schaltfläche hinzuzufügen. Ändern **Caption** Sie `E&xit`Beschriftung `ID_APP_EXIT`in , `8` **ID** in , **Bild** in .

   1. Sie haben die **Schaltflächen**geändert. Klicken Sie auf **Schließen,** um den **Element-Editor**zu beenden.

## <a name="creating-an-instance-of-the-ribbon-bar"></a><a name="createinstance"></a>Erstellen einer Instanz der Multifunktionsleisten

Die folgenden Schritte zeigen, wie beim Starten Ihrer Anwendung eine Instanz der Menübandleiste erstellt wird. Um eine Menübandleiste zu einer Anwendung hinzuzufügen, deklarieren Sie die Menübandleiste in der Datei "mainfrm.h". Schreiben Sie dann in der Datei "mainfrm.cpp" Code zum Laden der Menübandressource.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>So erstellen Sie eine Instanz der Menübandleiste

1. Fügen Sie in der Datei "mainfrm.h" einen Datenmember zum geschützten Abschnitt von `CMainFrame`, der Klassendefinition für den Hauptframe, hinzu. Dieses Element ist für die Multifunktionsleistenleiste.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. Fügen Sie in der Datei "mainfrm.cpp" den folgenden Code vor der letzten `return`-Anweisung am Ende der `CMainFrame::OnCreate`-Funktion hinzu. Es wird eine Instanz der Multifunktionsleistenerstellt erstellt.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

## <a name="customizing-the-ribbon-resource"></a><a name="addcategory"></a>Anpassen der Multifunktionsleistenressource

Nachdem Sie die **Schaltfläche Anwendung** erstellt haben, können Sie dem Menüband Elemente hinzufügen.

> [!NOTE]
> In dieser exemplarischen Vorgehensweise wird das gleiche Bereichssymbol für alle Bereiche verwendet. Sie können jedoch auch andere Bildlistenindizes verwenden, um andere Symbole anzuzeigen.

### <a name="to-add-a-home-category-and-edit-panel"></a>So fügen Sie eine Kategorie "Startseite" und einen Bereich "Bearbeiten" hinzu

1. Das Scribble-Programm erfordert nur eine Kategorie. Doppelklicken Sie in der Entwurfsansicht in der **Toolbox**auf **Kategorie,** um eine hinzuzufügen und ihre Eigenschaften anzuzeigen. Ändern Sie Eigenschaftswerte `&Home`wie folgt: `IDB_RIBBON_HOMELARGE` **Beschriftung** in `IDB_RIBBON_HOMESMALL`, Große **Bilder** in , Kleine **Bilder** in .

1. Jede Menübandkategorie ist in benannte Bereiche unterteilt. Jedes Bedienfeld enthält eine Reihe von Steuerelementen, die verwandte Vorgänge abschließen. Diese Kategorie verfügt über einen Bereich. Klicken Sie auf **Panel** `Edit`, und ändern Sie dann **Beschriftung** in .

1. Fügen Sie dem **Bearbeitungsbereich** eine Schaltfläche hinzu, die für das Löschen des Dokumentinhalts zuständig ist. Die Nachrichten-ID für diese Schaltfläche `IDR_SCRIBBTYPE` wurde bereits in der Menüressource definiert. Geben `Clear All` Sie als Schaltflächentext und als Index der Bitmap an, die die Schaltfläche schmückt. Öffnen Sie die **Toolbox**, und ziehen Sie dann eine **Schaltfläche** in das **Bearbeitungsfenster.** Klicken Sie auf die `Clear All`Schaltfläche, und ändern Sie dann **Beschriftung** in , **ID** `ID_EDIT_CLEAR_ALL`zu , **Bildindex** in `0`, Großer **Bildindex** in `0`.

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Die Scribble-Anwendung sollte angezeigt werden, und sie sollte am oberen Rand des Fensters über eine Menübandleiste anstelle einer Menüleiste verfügen. Die Menübandleiste sollte eine Kategorie haben, **Home**und **Home** sollte ein Bedienfeld haben, **Bearbeiten**. Die menüband-Schaltflächen, die Sie hinzugefügt haben, sollten den vorhandenen Ereignishandlern zugeordnet werden, und die Schaltflächen **Öffnen**, **Schließen**, **Speichern**, **Drucken**und **Alle löschen** sollten wie erwartet funktionieren.

## <a name="setting-the-look-of-the-application"></a><a name="setlook"></a>Festlegen des Aussehens der Anwendung

Ein *visueller Manager* ist ein globales Objekt, das alle Zeichnungen für eine Anwendung steuert. Da die ursprüngliche Scribble-Anwendung die Benutzeroberfläche im Office 2000-Stil nutzt, sieht die Anwendung möglicherweise altmodisch aus. Sie können die Anwendung zurücksetzen, um den visuellen Manager "Office 2007" zu verwenden, sodass sie einer Office 2007-Anwendung ähnelt.

### <a name="to-set-the-look-of-the-application"></a>So legen Sie die Darstellung der Anwendung fest

1. Geben `CMainFrame::OnCreate` Sie in der Funktion `return 0;` den folgenden Code vor der Anweisung ein, um den visuellen Standard-Manager und -Stil zu ändern.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Speichern Sie die Änderungen, erstellen Sie anschließend die Anwendung, und führen Sie sie aus. Die Anwendungsbenutzeroberfläche sollte der Office 2007-Benutzeroberfläche ähneln.

## <a name="next-steps"></a>Nächste Schritte

Sie haben das klassische Scribble 1.0 MFC-Beispiel geändert, um den **Ribbon Designer**zu verwenden. Gehen Sie nun zu [Teil 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweisen](../mfc/walkthroughs-mfc.md)<br/>
[Exemplarische Vorgehensweise: Aktualisieren der MFC Scribble-Anwendung (Teil 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
