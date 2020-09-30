---
title: Deklarieren einer auf der neuen Steuerelementklasse basierenden Variablen
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.classes.control.variable
helpviewer_keywords:
- variables [MFC], control classes
- control classes [MFC], variables
- classes [MFC], declaring variables based on
ms.assetid: 5722dc38-c0eb-40bd-93da-67a808140d03
ms.openlocfilehash: a828351a9e789228143d43d4c0a756abda879989
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506686"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarieren einer auf der neuen Steuerelementklasse basierenden Variablen

Nachdem Sie eine MFC-Steuerelement Klasse erstellt haben, können Sie eine auf Ihr basierende Variable deklarieren. Um einen Kontext für die neue Variable bereitzustellen, müssen Sie den Dialogfeld-Editor öffnen und das Dialogfeld bearbeiten, in dem Sie das wiederverwendbare Steuerelement verwenden möchten. Außerdem muss dem Dialogfeld bereits eine Klasse zugeordnet sein. Weitere Informationen zum Verwenden des Dialog-Editors finden Sie unter [Dialog-Editor](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>So deklarieren Sie eine Variable auf der Grundlage der wiederverwendbaren Klasse

1. Ziehen Sie beim Bearbeiten des Dialog Felds ein Steuerelement desselben Typs wie die Basisklasse des neuen Steuer Elements von der Symbolleiste Steuerelemente auf das Dialogfeld.

1. Platzieren Sie den Mauszeiger über dem gelöschten-Steuerelement.

1. Beim Drücken der STRG-Taste Doppelklicken Sie auf das-Steuerelement.

   Das Dialogfeld Element [Variable hinzufügen](../../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) wird angezeigt.

1. Wählen Sie im Feld **Zugriff** den richtigen Zugriff für das Steuerelement aus.

1. Aktivieren Sie das Kontrollkästchen **Steuerungs Variable** .

1. Geben Sie im Feld **Variablenname** einen Namen ein.

1. Klicken Sie unter **Kategorie**auf **Steuer**Element.

1. Wählen Sie in der Liste **Control ID** das Steuerelement aus, das Sie hinzugefügt haben. In der Liste **Variablentyp** sollte der richtige Variablentyp angezeigt werden, und im Feld **Steuerungstyp** sollte der richtige Steuer ungstyp angezeigt werden.

1. Fügen Sie im Feld **Kommentar** einen beliebigen Kommentar hinzu, der im Code angezeigt werden soll.

1. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

[Zuordnung von Nachrichten zu Funktionen](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Hinzufügen einer Memberfunktion](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable (Hinzufügen einer Membervariablen)](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function (Überschreiben einer virtuellen Funktion)](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler (MFC-Meldungshandler)](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigating the Class Structure (Navigieren in der Klassenstruktur)](../../ide/navigate-code-cpp.md)
