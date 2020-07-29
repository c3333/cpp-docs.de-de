---
title: 'Vorgehensweise: Erstellen eines Dialog Felds (C++)'
ms.date: 02/15/2019
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 0d5e4836933f1ce32f28c7fd03c81be5b7d09fd9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222081"
---
# <a name="how-to-create-a-dialog-box-c"></a>Vorgehensweise: Erstellen eines Dialog Felds (C++)

Die Position und Größe eines C++-Dialog Felds sowie der Speicherort und die Größe der darin enthaltenen Steuerelemente werden in Dialogfeld Einheiten gemessen. Die Werte für einzelne Steuerelemente und das Dialogfeld werden in der Statusleiste von Visual Studio in der unteren rechten Ecke angezeigt, wenn Sie Sie auswählen.

> [!NOTE]
> Wenn das Projekt noch keine RC-Datei enthält, finden Sie weitere Informationen unter [Erstellen einer neuen Ressourcen Skriptdatei](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Vorgehensweise

Der **Dialog-Editor** ermöglicht Folgendes:

### <a name="to-create-a-new-dialog-box"></a>So erstellen Sie ein neues Dialogfeld

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie **Ressource hinzufügen**aus.

1. Wählen Sie im Dialogfeld **Ressource hinzufügen** in der Liste **Ressourcentyp** den Text **Dialog** aus, und wählen Sie dann **neu**aus.

   Wenn ein Pluszeichen ( **+** ) neben dem Ressourcentyp " **Dialog** " angezeigt wird, bedeutet dies, dass Dialog Feld Vorlagen verfügbar sind. Wählen Sie das Pluszeichen aus, um die Liste der Vorlagen zu erweitern, wählen Sie eine Vorlage aus, und wählen Sie **neu**aus.

   Das Dialogfeld Neu wird im Dialogfeld- **Editor**geöffnet.

Sie können auch vorhandene Dialogfelder im Dialogfeld-Editor zum Bearbeiten öffnen.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>So erstellen Sie ein Dialogfeld, das von Benutzern nicht beendet werden kann

Sie können ein Lauf Zeit Dialogfeld erstellen, das ein Benutzer nicht beenden kann. Diese Art Dialogfeld ist nützlich für Anmeldungen und für Sperren von Anwendungen oder Dokumenten.

1. Legen Sie im **Eigenschaften** Bereich des Dialog Felds die Eigenschaft **System Menü** auf fest **`false`** .

   Mit dieser Einstellung werden das Systemmenü des Dialog Felds und die Schaltfläche **Schließen** deaktiviert.

1. Löschen Sie auf dem Formular des Dialogfelds die Schaltflächen **Abbrechen** und **OK** .

   Zur Laufzeit kann ein Benutzer ein modales Dialogfeld, das diese Eigenschaften aufweist, nicht beenden.

Um das Testen dieser Art von Dialogfeldern zu ermöglichen, erkennt die Funktion zum Testen des Dialog Felds, wenn **ESC** gedrückt wird. **ESC** wird auch als VK_ESCAPE virtuellen Schlüssel bezeichnet. Unabhängig davon, wie das Dialogfeld zur Laufzeit Verhalten soll, können Sie den Testmodus beenden, indem Sie **ESC**drücken.

> [!NOTE]
> Um für MFC-Anwendungen ein Dialogfeld zu erstellen, das von Benutzern nicht beendet werden kann, müssen Sie das Standardverhalten von und außer Kraft setzen, `OnOK` `OnCancel` denn selbst wenn Sie die zugeordneten Schaltflächen löschen, kann das Dialogfeld weiterhin durch Drücken der **Eingabe** Taste oder **ESC**verworfen werden.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>So geben Sie den Speicherort und die Größe eines Dialog Felds an

Es gibt Eigenschaften, die Sie im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window) festlegen können, um anzugeben, wo ein Dialogfeld auf dem Bildschirm angezeigt wird.

- Die boolesche **Zentrier** -Eigenschaft.

   Wenn Sie den Wert auf **true**festlegen, wird das Dialogfeld immer in der Mitte des Bildschirms angezeigt. Wenn Sie diese Eigenschaft auf **false**festlegen, können Sie die **xPos** -und **yPos** -Eigenschaften festlegen.

- Die **xPos** -und **yPos** -Eigenschaften, die verwendet werden, um explizit zu definieren, wo das Dialogfeld auf dem Bildschirm angezeigt wird.

   Diese Positions Eigenschaften sind Offset Werte aus der linken oberen Ecke des Anzeige Bereichs, der als definiert ist `{X=0, Y=0}` .

- Die **absolute align** -Eigenschaft, die die Position beeinflusst.

   Wenn **true**, sind die Koordinaten relativ zum Bildschirm. Wenn der Wert **false**ist, sind die Koordinaten relativ zum Fenster des Dialog Besitzers.

### <a name="to-test-a-dialog-box"></a>So testen Sie ein Dialogfeld

Beim Entwerfen eines Dialogfelds können Sie dessen Laufzeitverhalten simulieren und testen, ohne das Programm zu kompilieren. In diesem Modus können Sie folgende Aufgaben ausführen:

- Texteingabe, Auswahl aus Kombinationsfeldlisten, Aktivieren oder Deaktivieren von Optionen sowie Auswahl von Befehlen.

- Testen der Aktivierreihenfolge.

- Testen der Steuerelementgruppierung (z. B. von Optionsfeldern und Kontrollkästchen).

- Testen der Tastenkombinationen für Steuerelemente im Dialogfeld.

> [!NOTE]
> Verbindungen mit Dialogfeld Code, der mithilfe von Assistenten erstellt wurde, sind nicht in der Simulation enthalten.

Während des Testverfahrens wird ein Dialogfeld normalerweise relativ zum Hauptprogrammfenster angezeigt. Wenn Sie die Eigenschaft des Dialog Felds **absolute Ausrichtung** auf **true**festgelegt haben, wird das Dialogfeld an einer Position angezeigt, die relativ zur oberen linken Ecke des Bildschirms ist.

1. Wenn der **Dialog-Editor** das aktive Fenster ist, wechseln Sie zum Menü **Format**  >  **Test Dialog**.

1. Um die Simulation zu beenden, drücken Sie **ESC** , oder wählen Sie die Schaltfläche **Schließen** im Dialogfeld aus, das Sie testen.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Dialog-Editor](../windows/dialog-editor.md)<br/>
[Gewusst wie: Verwalten von Dialog Feld-Steuerelementen](../windows/controls-in-dialog-boxes.md)<br/>
