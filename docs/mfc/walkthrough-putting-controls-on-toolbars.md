---
title: 'Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen'
ms.date: 04/25/2019
helpviewer_keywords:
- Customize dialog box, adding controls
- toolbars [MFC], adding controls
ms.assetid: 8fc94bdf-0da7-45d9-8bc4-52b7b1edf205
ms.openlocfilehash: 2a801e61c49301d9b8780bbf7eb77025990337ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360270"
---
# <a name="walkthrough-putting-controls-on-toolbars"></a>Exemplarische Vorgehensweise: Steuerelemente in eine Symbolleiste einfügen

In diesem Artikel wird beschrieben, wie Sie einer Symbolleiste eine Symbolleistenschaltfläche hinzufügen, die ein Windows-Steuerelement zu einer Symbolleiste enthält. In MFC muss eine Symbolleistenschaltfläche eine [CMFCToolBarButton-Klasse](../mfc/reference/cmfctoolbarbutton-class.md)-abgeleitete Klasse sein, z. B. [CMFCToolBarComboBoxButton-Klasse](../mfc/reference/cmfctoolbarcomboboxbutton-class.md), [CMFCToolBarEditBoxButton-Klasse](../mfc/reference/cmfctoolbareditboxbutton-class.md), [CMFCDropDownToolbarButton-Klasse](../mfc/reference/cmfcdropdowntoolbarbutton-class.md)oder [CMFCToolBarButtonButton-Klasse](../mfc/reference/cmfctoolbarmenubutton-class.md).

## <a name="adding-controls-to-toolbars"></a>Hinzufügen von Steuerelementen zu Symbolleisten

Führen Sie zum Hinzufügen eines Steuerelements zu einer Symbolleiste die folgenden Schritte aus:

1. Reservieren Sie eine Platzhalterressourcen-ID für die Schaltfläche in der übergeordneten Symbolleistenressource. Weitere Informationen zum Erstellen von Schaltflächen mithilfe des **Toolbar-Editors** in Visual Studio finden Sie im Artikel [Toolbar-Editor.](../windows/toolbar-editor.md)

1. Reservieren Sie ein Symbolleistenbild (Schaltflächensymbol) für die Schaltfläche in allen Bitmaps der übergeordneten Symbolleiste.

1. Gehen Sie im Nachrichtenhandler, der die `AFX_WM_RESETTOOLBAR` Nachricht verarbeitet, die folgenden Schritte aus:

   1. Erstellen Sie das Schaltflächensteuerelement mithilfe einer von `CMFCToolbarButton` abgeleiteten Klasse.

   1. Ersetzen Sie die Dummy-Schaltfläche durch das neue Steuerelement mithilfe von [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton). Sie können das Schaltflächenobjekt auf dem Stapel erstellen, da `ReplaceButton` das Schaltflächenobjekt kopiert und die Kopie beibehält.

> [!NOTE]
> Wenn Sie die Anpassung in Ihrer Anwendung aktiviert haben, müssen Sie die Symbolleiste möglicherweise zurücksetzen, indem Sie die Schaltfläche **Zurücksetzen** auf der Registerkarte **Symbolleisten** im Dialogfeld **Anpassen** verwenden, um das aktualisierte Steuerelement in der Anwendung nach dem erneuten Kompilieren anzuzeigen. Der Zustand der Symbolleiste wird in der Windows-Registrierung gespeichert, und die Registrierungsinformationen werden geladen und angewendet, nachdem die `ReplaceButton`-Methode während des Anwendungsstarts ausgeführt wurde.

## <a name="toolbar-controls-and-customization"></a>Symbolleisten-Steuerelemente und Anpassung

Die Registerkarte **Befehle** im Dialogfeld **Anpassen** enthält eine Liste der Befehle, die in der Anwendung verfügbar sind. Standardmäßig verarbeitet das Dialogfeld **Anpassen** die Anwendungsmenüs und erstellt eine Liste der Standardsymbolleistenschaltflächen in jeder Menükategorie. Um die erweiterte Funktionalität der Symbolleistensteuerelemente beizubehalten, müssen Sie die Standardsymbolleistenschaltfläche durch das benutzerdefinierte Steuerelement im Dialogfeld **Anpassen** ersetzen.

Wenn Sie die Anpassung **Customize** aktivieren, erstellen Sie `OnViewCustomize` das Dialogfeld Anpassen im Anpassungshandler mithilfe der [CMFCToolBarsCustomizeDialog-Klasse.](../mfc/reference/cmfctoolbarscustomizedialog-class.md) Bevor Sie das Dialogfeld **Anpassen** anzeigen, indem Sie [CMFCToolBarsCustomizeDialog::Create](../mfc/reference/cmfctoolbarscustomizedialog-class.md#create)aufrufen, rufen Sie [CMFCToolBarsCustomizeDialog::ReplaceButton auf,](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) um die Standardschaltfläche durch das neue Steuerelement zu ersetzen.

## <a name="example-creating-a-find-combo-box"></a>Beispiel: Erstellen eines Suchkombinationsfelds

In diesem Abschnitt wird beschrieben, wie Sie ein Steuerelement für das Werkzeugkombinationsfeld **Suchen** erstellen, das auf einer Symbolleiste angezeigt wird und zuletzt verwendete Suchzeichenfolgen enthält. Der Benutzer kann eine Zeichenfolge im Steuerelement eingeben und die EINGABETASTE drücken, um ein Dokument zu suchen, oder er kann die ESC-TASTE drücken, um zum Hauptframe zurückzukehren. In diesem Beispiel wird davon ausgegangen, dass das Dokument in einer von [CEditView Class abgeleiteten](../mfc/reference/ceditview-class.md)Ansicht angezeigt wird.

### <a name="creating-the-find-control"></a>Erstellen des Suchen-Steuerelements

Erstellen Sie zunächst das Steuerelement **Kombinationsfeld suchen:**

1. Fügen Sie den Anwendungsressourcen die Schaltfläche und die zugehörigen Befehle hinzu:

   1. Fügen Sie in den Anwendungsressourcen eine neue Schaltfläche mit einer `ID_EDIT_FIND`-Befehls-ID zu einer Symbolleiste in Ihrer Anwendung und zu allen der Symbolleiste zugeordneten Bitmaps hinzu.

   1. Erstellen Sie ein neues `ID_EDIT_FIND` Menüelement mit der Befehls-ID.

   1. Fügen Sie der Zeichenfolgentabelle eine neue Zeichenfolge "Text suchen\nSuchen" hinzu, und weisen Sie ihr eine `ID_EDIT_FIND_COMBO`-Befehls-ID zu. Diese ID wird als Befehls-ID der Schaltfläche Kombinationsfeld **suchen** verwendet.

        > [!NOTE]
        > Da `ID_EDIT_FIND` ein Standardbefehl ist, der von `CEditView` verarbeitet wird, ist es nicht erforderlich, einen speziellen Handler für diesen Befehl zu implementieren.  Sie müssen jedoch einen Handler für den neuen Befehl `ID_EDIT_FIND_COMBO` implementieren.

1. Erstellen Sie eine `CFindComboBox`neue Klasse , , abgeleitet von [cComboBox Class](../mfc/reference/ccombobox-class.md).

1. Überschreiben Sie in der Klasse `CFindComboBox` die virtuelle Methode `PreTranslateMessage`. Mit dieser Methode kann das Kombinationsfeld die [WM_KEYDOWN-Nachricht](/windows/win32/inputdev/wm-keydown) verarbeiten. Wenn der Benutzer die ESC-TASTE (`VK_ESCAPE`) drückt, kehren Sie zum Hauptrahmenfenster zurück. Wenn der Benutzer die EINGABETASTE (`VK_ENTER`) drückt, geben Sie im Hauptrahmenfenster eine `WM_COMMAND`-Meldung aus, die die Befehls-ID `ID_EDIT_FIND_COMBO` enthält.

1. Erstellen Sie eine Klasse für die Schaltfläche Kombinationsfeld **suchen,** die von [der CMFCToolBarComboBoxButton-Klasse](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)abgeleitet ist. In diesem Beispiel hat es den Namen `CFindComboButton`.

1. Der Konstruktor von `CMFCToolbarComboBoxButton` akzeptiert drei Parameter: die Befehls-ID der Schaltfläche, den Index des Schaltflächensymbols und das Format des Kombinationsfelds. Legen Sie diese Parameter wie folgt fest:

   1. Übergeben Sie `ID_EDIT_FIND_COMBO` als Befehls-ID.

   1. Verwenden Sie [CCommandManager::GetCmdImage](reference/internal-classes.md) mit, `ID_EDIT_FIND` um den Bildindex abzubekommen.

   1. Eine Liste der verfügbaren Kombinationsfeldstile finden Sie unter [Combo-Box Styles](../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

1. Überschreiben Sie in der `CFindComboButton`-Klasse die `CMFCToolbarComboBoxButton::CreateCombo`-Methode. Hier sollten Sie das `CFindComboButton`-Objekt erstellen und einen Zeiger darauf zurückgeben.

1. Verwenden [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) Sie das IMPLEMENT_SERIAL-Makro, um die Kombinationsschaltfläche dauerhaft zu machen. Der Arbeitsbereichs-Manager lädt und speichert den Zustand der Schaltfläche automatisch in der Windows-Registrierung.

1. Implementieren Sie den `ID_EDIT_FIND_COMBO`-Handler in der Dokumentenansicht. Verwenden Sie [CMFCToolBar::GetCommandButtons](../mfc/reference/cmfctoolbar-class.md#getcommandbuttons) mit, `ID_EDIT_FIND_COMBO` um alle Schaltflächen zum **Suchen** in Kombinationsfeldern abzurufen. Aufgrund der Anpassung können mehrere Kopien einer Schaltfläche mit derselben Befehls-ID vorhanden sein.

1. Verwenden `ID_EDIT_FIND` Sie `OnFind`im Nachrichtenhandler [CMFCToolBar::IsLastCommandFromButton,](../mfc/reference/cmfctoolbar-class.md#islastcommandfrombutton) um zu bestimmen, ob der Suchbefehl von der Schaltfläche Kombinationsfeld **suchen** gesendet wurde. Wenn dies der Fall ist, suchen Sie den Text, und fügen Sie dem Kombinationsfeld die Suchzeichenfolge hinzu.

### <a name="adding-the-find-control-to-the-main-toolbar"></a>Hinzufügen des Suchen-Steuerelements zur Hauptsymbolleiste

Führen Sie zum Hinzufügen der Kombinationsfeldschaltfläche zur Symbolleiste die folgenden Schritte aus:

1. Implementieren Sie den `AFX_WM_RESETTOOLBAR`-Meldungshandler `OnToolbarReset` im Hauptrahmenfenster.

    > [!NOTE]
    > Das Framework sendet diese Meldung an das Hauptrahmenfenster, wenn während des Anwendungsstarts eine Symbolleiste initialisiert wird oder wenn eine Symbolleiste während der Anpassung zurückgesetzt wird. In beiden Fällen müssen Sie die Standardmäßige Symbolleistenschaltfläche durch die **benutzerdefinierte** Schaltfläche Kombinationsbox suchen ersetzen.

1. Untersuchen `AFX_WM_RESETTOOLBAR` Sie im Handler die Symbolleisten-ID, d. h. den *WPARAM* der AFX_WM_RESETTOOLBAR-Nachricht. Wenn die Symbolleisten-ID der Symbolleiste entspricht, die die Schaltfläche Kombinationsfeld **suchen** enthält, rufen Sie [CMFCToolBar::ReplaceButton](../mfc/reference/cmfctoolbar-class.md#replacebutton) `ID_EDIT_FIND)` auf, `CFindComboButton` um die **Schaltfläche Suchen** (d. h. die Schaltfläche mit der Befehls-ID durch ein Objekt) zu ersetzen.

    > [!NOTE]
    > Sie können ein `CFindComboBox`-Objekt auf dem Stapel erstellen, da `ReplaceButton` das Schaltflächenobjekt kopiert und die Kopie beibehält.

### <a name="adding-the-find-control-to-the-customize-dialog-box"></a>Hinzufügen des Suchen-Steuerelements zum Dialogfeld "Anpassen"

Rufen Sie `OnViewCustomize`im Anpassungshandler [CMFCToolBarsCustomizeDialog::ReplaceButton](../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) auf, um die **Schaltfläche** Suchen `ID_EDIT_FIND`(d. h. die Schaltfläche mit der Befehls-ID ) durch ein `CFindComboButton` Objekt zu ersetzen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../mfc/hierarchy-chart.md)<br/>
[Klassen](../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar-Klasse](../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton-Klasse](../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton-Klasse](../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCToolBarsCustomizeDialog-Klasse](../mfc/reference/cmfctoolbarscustomizedialog-class.md)
