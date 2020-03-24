---
title: Menü-EditorC++()
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: 3671dbe33b2d6e373e2df3d54267c6aac5bbf20d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214447"
---
# <a name="menu-editor-c"></a>Menü-EditorC++()

Menüs ermöglichen Ihnen das Anordnen von Befehlen in einer logischen und leicht verständlichen Weise. Mit dem **Menü-Editor**können Sie Menüs erstellen und bearbeiten, indem Sie direkt mit einer Menüleiste arbeiten, die der Anwendung in der fertigen Anwendung sehr ähnlich ist.

> [!TIP]
> Mit dem **Menü-Editor**können Sie in vielen Fällen mit der rechten Maustaste klicken, um ein Popupmenü mit häufig verwendeten Befehlen anzuzeigen. Die verfügbaren Befehle hängen davon ab, auf was der Zeiger verweist.

## <a name="how-to"></a>Vorgehensweise

Der **Menü-Editor** ermöglicht Ihnen Folgendes:

### <a name="to-create-a-standard-menu"></a>So erstellen Sie ein Standardmenü

1. Wechseln Sie zur Menü **Ansicht** > **anderen Fenster** > **Ressourcenansicht** , und klicken Sie mit der rechten Maustaste auf die **Menü** Überschrift. Wählen Sie **Ressource hinzufügen**und dann **Menü**aus.

1. Wählen Sie in der Menüleiste das Feld **Neues Element** (das Rechteck, das den *Typ hier*enthält) aus.

   ![Feld "Neues Element" im Menü-Editor](../windows/media/vcmenueditornewitembox.gif "vcmenueditor-Element")<br/>
   Feld " **Neues Element** "

1. Geben Sie einen Namen für das neue Menü ein, z. b. *File*.

   Der von Ihnen angezeigte Text wird sowohl im **Menü-Editor** als auch im Feld **Beschriftung** im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window)angezeigt. Die Eigenschaften des neuen Menüs können an einer der beiden Stellen bearbeitet werden.

   Nachdem Sie das neue Menü in der Menüleiste benannt haben, rückt das Feld für das neue Menüelement nach rechts (damit ein weiteres Menü eingefügt werden kann). Unter dem ersten Menü wird ein weiteres Feld geöffnet, dem Sie Menübefehle hinzufügen können.

   ![Erweitertes Feld "Neues Element"](../windows/media/vcmenueditornewitemboxexpanded.gif "vcmenueditor-Element")<br/>
   Feld " **Neues Element** " mit Fokus nach dem Eingeben des Menü namens

   > [!NOTE]
   > Um ein Menü mit einem einzelnen Element in der Menüleiste zu erstellen, legen Sie die Eigenschaft **Popup** auf **false**fest.

### <a name="to-create-a-submenu"></a>So erstellen Sie ein Untermenü

1. Wählen Sie den Menübefehl aus, für den Sie ein Untermenü erstellen möchten.

1. Geben Sie im Feld **Neues Element** , das rechts angezeigt wird, den Namen des neuen Menübefehls ein. Dieser neue Befehl wird im Untermenü an erster Stelle angezeigt.

1. Fügen Sie dem Untermenü weitere Menübefehle hinzu.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>So fügen Sie ein neues Menüs zwischen vorhandenen Menüs ein

Wählen Sie einen vorhandenen Menünamen aus, und drücken Sie die **Eingabe** Taste, oder klicken Sie mit der rechten Maustaste auf die Menüleiste, und wählen Sie **neue einfügen**.

   Das Feld **Neues Element** wird vor dem ausgewählten Element eingefügt.

### <a name="to-add-commands-to-a-menu"></a>So fügen Sie Befehle zu einem Menü hinzu

1. Erstellen Sie ein Menü. Wählen Sie dann einen Menünamen aus, z. b. **Datei**.

   Jedes Menü wird erweitert, und es wird ein neues Elementfeld für Befehle zur Verfügung gestellt. Beispielsweise können Sie die Befehle **New**, **Open**und **Close** zu einem Menü **Datei** hinzufügen.

1. Geben Sie im neuen Elementfeld einen Namen für den neuen Menübefehl ein.

   > [!NOTE]
   > Der von Ihnen angezeigte Text wird sowohl im **Menü-Editor** als auch im Feld **Beschriftung** im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window)angezeigt. Die Eigenschaften des neuen Menüs können an einer der beiden Stellen bearbeitet werden.

   > [!TIP]
   > Sie können eine mnemonische Taste (Zugriffstaste) definieren, die dem Benutzer ermöglicht, den Menübefehl auszuwählen. Geben Sie ein kaufmännisches und-Zeichen (`&`) vor einem Buchstaben ein, um es als mnetmonisches anzugeben. Der Benutzer kann den Menübefehl auswählen, indem er diesen Buchstaben eingibt.

1. Wählen Sie im **Eigenschaften** Fenster die Menübefehls Eigenschaften aus, die angewendet werden sollen. Weitere Informationen finden Sie unter [Menübefehls Eigenschaften](../windows/menu-command-properties.md).

1. Geben Sie im Fenster **Eigenschaften** in das Feld **Eingabe** Aufforderung die Zeichenfolge ein, die Sie in der Statusleiste Ihrer Anwendung anzeigen möchten.

   In diesem Schritt wird ein Eintrag in der Zeichen folgen Tabelle mit dem gleichen Ressourcen Bezeichner erstellt wie der von Ihnen erstellte Menübefehl.

   > [!NOTE]
   > Eingabe Aufforderungen können nur auf Menü Elemente mit der **Popup** -Eigenschaft " **true**" angewendet werden. Beispielsweise können Menüelemente auf oberster Ebene über Eingabeaufforderungen verfügen, wenn sie über Untermenüelemente verfügen. Der Zweck einer **Eingabeaufforderung** besteht darin, anzugeben, was geschieht, wenn ein Benutzer das Menü Element auswählt.

1. Drücken **Sie die Eingabe** Taste, um den Menübefehl abzuschließen.

   Das neue Elementfeld wird ausgewählt, sodass Sie zusätzliche Menübefehle erstellen können.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>So wählen Sie mehrere Menübefehle zum Ausführen von Massen Vorgängen aus, z.b. löschen oder Ändern von Eigenschaften

Wenn Sie die **STRG** -Taste gedrückt halten, wählen Sie die gewünschten Menüs oder unter Menübefehle aus.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Verschieben und Kopieren von Menüs und Menübefehlen

- Verwenden Sie die Drag & Drop-Methode:

   1. Ziehen oder kopieren Sie das zu verschiebende Elemente in:

      - Eine neue Position im aktuellen Menü.

      - Ein anderes Menü. Sie können zu anderen Menüs navigieren, indem Sie den Mauszeiger darüber ziehen.

   1. Legen Sie den Menübefehl ab, wenn die Einfügemarke die gewünschte Position anzeigt.

- Verwenden Sie Kontextmenü Befehle:

   1. Klicken Sie mit der rechten Maustaste auf ein oder mehrere Menüs oder Menübefehle, und wählen Sie dann **Ausschneiden** (zum Verschieben) oder **Kopieren**aus.

   1. Wenn Sie die Elemente zu einer anderen Menü Ressource oder Ressourcen Skriptdatei verschieben, [Öffnen Sie Sie in einem anderen Fenster](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Wählen Sie die Position des Menüs oder Menübefehls aus, zu der Sie das Verschieben oder Kopieren vornehmen möchten.

   1. Wählen Sie im Kontextmenü **Einfügen**aus. Das verschobene oder kopierte Element wird vor dem von Ihnen ausgewählten Element platziert.

> [!NOTE]
> Sie können Elemente auch ziehen und kopieren und sie in anderen Menüs in anderen Menüfenstern einfügen.

### <a name="to-delete-a-menu-or-menu-command"></a>So löschen Sie ein Menü oder einen Menübefehl

Klicken Sie mit der rechten Maustaste auf den Menü Namen oder-Befehl, und wählen Sie **Löschen**

> [!NOTE]
> Entsprechend können Sie mit dem Kontextmenü andere Aktionen ausführen, wie z. B. Kopieren, Ausschneiden, Einfügen, Neue einfügen, Trennzeichen einfügen, IDs bearbeiten, Als Popup anzeigen, Mnemonik überprüfen usw.

## <a name="pop-up-menus"></a>Popup Menüs

[Popupmenüs](../mfc/menus-mfc.md) enthalten häufig verwendete Befehle. Sie können kontextbezogen für die Position des Zeigers sein. Für das Verwenden von Popupmenüs in Ihrer Anwendung muss das Menü selbst erstellt und anschließend mit dem Anwendungscode verbunden werden.

Nachdem Sie die Menü Ressource erstellt haben, muss der Anwendungscode die Menü Ressource laden und [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) verwenden, damit das Menü angezeigt wird. Nachdem der Benutzer das Popup Menü durch Auswahl außerhalb des Popup Menüs geschlossen oder einen Befehl ausgewählt hat, gibt diese Funktion zurück. Wenn der Benutzer einen Befehl auswählt, wird dessen Befehlsmeldung an das Fenster gesendet, dessen Handle übergeben wurde.

> [!NOTE]
> Verwenden Sie für MFC-Bibliotheksprogramme (Microsoft Foundation Class) und ATL-Programme **Code-Assistenten** , um Menübefehle mit Code zu verbinden. Weitere Informationen finden Sie unter [Hinzufügen eines Ereignisses](../ide/adding-an-event-visual-cpp.md) und Zuordnen von [Nachrichten zu Funktionen](../mfc/reference/mapping-messages-to-functions.md).

- Erstellen Sie ein Menü mit einem leeren Titel, und geben Sie keine *Beschriftung*an, um ein Popupmenü zu erstellen. Fügen Sie dann dem Menü "neu" einen Menübefehl hinzu. wechseln Sie zum ersten Menübefehl unter dem leeren Menütitel *, und geben* Sie dann eine *Beschriftung* und weitere Informationen ein.

   Wiederholen Sie diesen Vorgang für alle anderen Menübefehle im Popupmenü, und speichern Sie die Menü Ressource.

- Fügen Sie zum Verbinden eines Popup Menüs mit Ihrer Anwendung z. b. einen Meldungs Handler für WM_CONTEXTMENU hinzu, und fügen Sie dann den folgenden Code zum Nachrichten Handler hinzu:

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > Der vom Meldungs Handler übergeben [CPoint](../atl-mfc-shared/reference/cpoint-class.md) befindet sich in Bildschirm Koordinaten.

Wenn Sie im **Menü-Editor**arbeiten, wird normalerweise eine Menü Ressource als Menüleiste angezeigt. Sie verfügen jedoch möglicherweise über Menüressourcen, die während der Ausführung des Programms zur Menüleiste der Anwendung hinzugefügt werden.

- Klicken Sie zum Anzeigen einer Menü Ressource als Popupmenü mit der rechten Maustaste auf das Menü, und wählen Sie **als Popup anzeigen**aus.

   Diese Option ist nur eine Anzeige Einstellung und ändert Ihr Menü nicht.

> [!TIP]
> Um zurück zur Menüleisten Ansicht zu wechseln, wählen Sie erneut **als Popup anzeigen** aus. Durch diese Aktion wird das Häkchen entfernt, und die Menüleisten Ansicht wird zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcen-Editor](../windows/resource-editors.md)<br/>
[Menübefehle](../windows/menu-command-properties.md)<br/>
[Benutzeroberflächenobjekte und Befehls-IDs](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menüs](../mfc/menus-mfc.md)<br/>
[Menüs](/windows/win32/menurc/menus)
