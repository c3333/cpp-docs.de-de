---
title: 'Gewusst wie: Definieren von Steuerelement Zugriff und-Werten (C++)'
ms.date: 02/15/2019
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls [C++], mnemonics
- access keys [C++], checking
- mnemonics [C++], checking for duplicate
- mnemonics
- mnemonics [C++], dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
- combo boxes [C++], Data property
- controls [C++], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- Data property
- combo boxes [C++], testing values
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
ms.openlocfilehash: 91b6365334b977957ff6bd6c25278d4088961a2c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222068"
---
# <a name="how-to-define-control-access-and-values-c"></a>Gewusst wie: Definieren von Steuerelement Zugriff und-Werten (C++)

## <a name="tab-order"></a>Aktivierreihenfolge

Die Aktivier Reihenfolge ist die Reihenfolge, in der die **Tab** -Taste den Eingabefokus von einem Steuerelement auf das nächste Element in einem Dialogfeld verschiebt. Normalerweise wird die Aktivier Reihenfolge von links nach rechts und von oben nach unten in einem Dialogfeld fortgesetzt. Jedes Steuerelement verfügt über eine **Tabstopps** -Eigenschaft, die bestimmt, ob ein Steuerelement den Eingabefokus erhält.

- Um den Eingabefokus für ein Steuerelement festzulegen, wählen Sie im [Fenster Eigenschaften](/visualstudio/ide/reference/properties-window)in der **Tabstopps** -Eigenschaft die Option **true** oder **false** aus.

Sogar Steuerelemente, für die die **Tabstopp** -Eigenschaft nicht auf **true** festgelegt ist, müssen Teil der Aktivier Reihenfolge sein, insbesondere für Steuerelemente, die keine Beschriftungen aufweisen. Statischer Text, der eine Zugriffstaste für ein verknüpftes Steuerelement enthält, muss unmittelbar vor dem zugehörigen Steuerelement in der Aktivier Reihenfolge stehen.

> [!NOTE]
> Wenn das Dialogfeld überlappende Steuerelemente enthält, kann das Ändern der Aktivier Reihenfolge die Anzeige der Steuerelemente ändern. Steuerelemente, die später in der Aktivier Reihenfolge angezeigt werden, werden immer über überlappende Steuerelemente angezeigt, die sich in der Aktivier Reihenfolge befinden

- Um die aktuelle Aktivier Reihenfolge für alle Steuerelemente anzuzeigen, wechseln Sie zur Menü **Format**-  >  **Reihenfolge**, oder drücken Sie **STRG**  +  **D**.

   Eine Zahl in der oberen linken Ecke jedes Steuer Elements zeigt den Platz in der aktuellen Aktivier Reihenfolge an.

- Um die Aktivier Reihenfolge für alle Steuerelemente zu ändern, wechseln Sie zur Menü **Format**-Reihenfolge,  >  **Tab Order** und legen Sie die Aktivier Reihenfolge fest, indem Sie die einzelnen Steuerelemente in der Reihenfolge auswählen **Tab** ,

- Um die Aktivier Reihenfolge für zwei oder mehr Steuerelemente zu ändern, wechseln Sie zur Menü **Format**-  >  **Reihenfolge**. Halten Sie die **STRG** -Taste gedrückt, und wählen Sie das Steuerelement aus, in dem die Änderung in der Reihenfolge beginnt, und geben Sie dann die **STRG** -Taste ein, und wählen Sie die Steuerelemente in der Reihenfolge aus, in der die **Tab**

   Wenn Sie z. b. die Reihenfolge der Steuerelemente durch ändern möchten, halten Sie die STRG-Taste `7` `9` gedrückt, und wählen Sie dann zuerst Steuerung **Ctrl** `6` .

- Doppelklicken Sie auf das-Steuerelement, um ein bestimmtes Steuerelement auf Number `1` oder First in der Aktivier Reihenfolge festzulegen.

> [!TIP]
> Nachdem Sie den **Tab-Reihenfolge** Modus eingegeben haben, drücken Sie die **ESC** -Taste oder die **Eingabe** Taste, um den **Tab-Reihen** Folge Modus zu beenden

## <a name="mnemonics-access-keys"></a>Mnetmonics (Zugriffsschlüssel)

Normalerweise verschieben Tastatur Benutzer den Eingabefokus in einem Dialogfeld mit der **Registerkarte** und den **Pfeil** Tasten von einem Steuerelement zu einem anderen. Sie können jedoch eine Zugriffstaste (ein mnetmonisches oder leicht zu merkende Name) definieren, die es Benutzern ermöglicht, ein Steuerelement durch Drücken einer einzelnen Taste auszuwählen.

### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>So definieren Sie eine Zugriffstaste für ein Steuerelement mit einer sichtbaren Beschriftung (Schaltflächen, Kontrollkästchen und Options Felder)

1. Wählen Sie das Steuerelement im Dialogfeld aus.

1. Geben Sie im [Fenster Eigenschaften](/visualstudio/ide/reference/properties-window)in der **Beschriftung** -Eigenschaft einen neuen Namen für das-Steuerelement ein, und geben `&` Sie vor dem Buchstaben, den Sie als Zugriffstaste für dieses Steuerelement festlegen möchten, ein kaufmännisches und-Element () ein. Beispiel: `&Radio1`.

1. Drücken Sie die **EINGABETASTE**.

   In der angezeigten Beschriftung wird ein Unterstrich angezeigt, um die Zugriffstaste anzugeben, z. b. **R**adio1.

### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>So definieren Sie eine Zugriffstaste für ein Steuerelement ohne sichtbare Beschriftung

1. Erstellen Sie eine Beschriftung für das Steuerelement, indem Sie ein **statisches Text** Steuerelement in der [Toolbox](/visualstudio/ide/reference/toolbox)verwenden.

1. Geben Sie in der Beschriftung statischer Text `&` vor dem Buchstaben, den Sie als Zugriffsschlüssel haben möchten, ein kaufmännisches und-Zeichen () ein.

1. Stellen Sie sicher, dass das statische Text Steuerelement unmittelbar vor dem Steuerelement in der Aktivier Reihenfolge steht.

> [!NOTE]
> Alle Zugriffsschlüssel in einem Dialogfeld sollten eindeutig sein. Um nach doppelten Zugriffs Schlüsseln zu suchen, wechseln Sie zu Menü **Format**  >  **überprüfen mnetmonics**.

## <a name="combo-box-values"></a>Kombinations Feld Werte

Sie können einem Kombinations Feld-Steuerelement Werte hinzufügen, solange der **Dialog-Editor** geöffnet ist.

> [!TIP]
> Es empfiehlt sich, alle Werte dem Kombinations Feld hinzuzufügen, *bevor* Sie das Feld im **Dialog-Editor**anpassen, oder Sie können Text abschneiden, der im Kombinations Feld angezeigt werden soll.

### <a name="to-enter-values-into-a-combo-box-control"></a>So geben Sie Werte in ein Kombinations Feld-Steuerelement ein

1. Wählen Sie das Kombinations Feld-Steuerelement, indem Sie es auswählen.

1. Scrollen Sie im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window)nach unten zur Eigenschaft **Daten** .

   > [!NOTE]
   > Wenn Sie Eigenschaften anzeigen, die nach Typ gruppiert sind, werden die **Daten** in den **misc** -Eigenschaften angezeigt.

1. Wählen Sie den Wertebereich für die **Daten** Eigenschaft aus, und geben Sie Ihre Datenwerte durch Semikolons getrennt ein.

   > [!NOTE]
   > Fügen Sie keine Leerzeichen zwischen den Werten ein, da Leerzeichen in der Dropdown Liste die alphabetische Sortierung beeinträchtigen.

1. Drücken Sie die **Eingabe** Taste, wenn Sie die Werte hinzugefügt haben.

Informationen zum Vergrößern des Dropdown Bereichs eines Kombinations Felds finden Sie unter [Festlegen der Größe des Kombinations Felds und der Dropdown Liste](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).

> [!NOTE]
> Sie können Win32-Projekten keine Werte hinzufügen, indem Sie dieses Verfahren verwenden (die **Data** -Eigenschaft ist für Win32-Projekte ausgegraut). Da Win32-Projekte keine Bibliotheken aufweisen, die diese Funktion hinzufügen, müssen Sie einem Kombinations Feld mit einem Win32-Projekt Programm gesteuert Werte hinzufügen.

### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>So testen Sie die Darstellung von Werten in einem Kombinations Feld

1. Nachdem Sie die Werte in die **Daten** Eigenschaft eingegeben haben, wählen Sie die Schaltfläche **Testen** auf der [Symbolleiste des Dialog-Editors](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)

1. Versuchen Sie, einen Bildlauf nach unten durchführen. Werte werden genau so angezeigt, wie Sie im **Eigenschaften** Fenster in der Eigenschaft **Daten** eingegeben werden. Es gibt keine Rechtschreibprüfung oder Groß-/Kleinschreibung.

1. Drücken Sie **ESC** , um zum **Dialog Feld** -Editor zurückzukehren.

## <a name="radio-button-values"></a>Optionsfeld Werte

Wenn Sie einem Dialogfeld Options Felder hinzufügen, behandeln Sie Sie als Gruppe, indem Sie im **Eigenschaften** Fenster für die erste Schaltfläche in der Gruppe eine **Gruppen** Eigenschaft festlegen. Eine Steuerelement-ID für das betreffende Optionsfeld wird dann im [Assistent zum Hinzufügen von Membervariablen](../ide/add-member-variable-wizard.md)angezeigt und ermöglicht das Hinzufügen einer Membervariablen zur Gruppe der Optionsfelder.

Sie können mehr als eine Gruppe von Options Feldern in einem Dialogfeld auswählen. Fügen Sie jede Gruppe mithilfe des folgenden Verfahrens hinzu.

### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>So fügen Sie einem Dialogfeld eine Gruppe von Optionsfeldern hinzu

1. Wählen Sie das Optionsfeld-Steuerelement im [Fenster Toolbox](/visualstudio/ide/reference/toolbox) aus, und wählen Sie im Dialogfeld die Position aus, an der das Steuerelement platziert werden soll.

1. Wiederholen Sie den obigen Schritt, um so viele Options Felder hinzuzufügen, wie Sie benötigen. Stellen Sie sicher, dass die Options Felder in der Gruppe in der Aktivier Reihenfolge aufeinander folgen.

1. Legen Sie im Fenster [Eigenschaften](/visualstudio/ide/reference/properties-window)die Eigenschaft **Gruppe** des *ersten* Optionsfelds in der Aktivierreihenfolge auf **Wahr**fest.

   Wenn Sie die Eigenschaft " **Group** " in " **true** " ändern, wird dem Eintrag der Schaltfläche im Dialogfeld Objekt des Ressourcen Skripts das WS_GROUP Format hinzugefügt, und es wird verhindert, dass der Benutzer mehrere Options Felder gleichzeitig in der Schaltflächen Gruppe auswählen kann (wenn der Benutzer eine Options Schaltfläche auswählt, werden die anderen in der Gruppe gelöscht).

   > [!NOTE]
   > Die Eigenschaft **Gruppe** sollte nur für das erste Optionsfeld einer Gruppe auf **Wahr**festgelegt werden. Wenn Sie über weitere Steuerelemente verfügen, die nicht Teil der Schaltflächen Gruppe sind, legen Sie die Eigenschaft **Gruppe** des ersten Steuer Elements *, das sich außerhalb der Gruppe befindet* , ebenfalls auf **true** fest. Sie können das erste Steuerelement außerhalb der Gruppe schnell ermitteln, indem Sie **STRG** + **D** verwenden, um die Aktivier Reihenfolge anzuzeigen.

### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>So fügen Sie eine Membervariable für die Optionsfeldgruppe hinzu

1. Klicken **Sie mit**der rechten Maustaste auf das erste Optionsfeld-Steuerelement in der Aktivier Reihenfolge (das bestimmende Steuerelement und das Element, bei dem die **Group** -Eigenschaft auf **true**festgelegt ist)

1. Aktivieren Sie im [Assistent zum Hinzufügen von Membervariablen](../ide/add-member-variable-wizard.md)das Kontrollkästchen **Steuerungsvariable** , und aktivieren Sie dann das Optionsfeld **Wert** .

   - Geben Sie im Feld **Variablenname** einen Namen für die neue Membervariable ein.

   - Wählen Sie im Listenfeld **Variablentyp** die Option **`int`** *int*aus.

   Jetzt können Sie Ihren Code ändern, um festzulegen, welches Optionsfeld aus aktiviert angezeigt werden soll. Beispielsweise `m_radioBox1 = 0;` wählt das erste Optionsfeld in der Gruppe aus.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Dialog Feld-Steuerelemente verwalten](controls-in-dialog-boxes.md)<br/>
[Gewusst wie: Hinzufügen, bearbeiten oder Löschen von Steuerelementen](adding-editing-or-deleting-controls.md)<br/>
[Gewusst wie: Layout von Steuerelementen](arrangement-of-controls-on-dialog-boxes.md)<br/>
