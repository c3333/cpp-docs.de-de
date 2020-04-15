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
ms.openlocfilehash: 994f81524001a80d1cf0dd3783b9de742d61e84d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365842"
---
# <a name="declaring-a-variable-based-on-your-new-control-class"></a>Deklarieren einer auf der neuen Steuerelementklasse basierenden Variablen

Nachdem Sie eine MFC-Steuerelementklasse erstellt haben, können Sie eine darauf basierende Variable deklarieren. Um einen Kontext für die neue Variable bereitzustellen, müssen Sie den Dialog-Editor öffnen und das Dialogfeld bearbeiten, in dem Sie das wiederverwendbare Steuerelement verwenden möchten. Außerdem muss dem Dialogfeld bereits eine Klasse zugeordnet sein. Informationen zur Verwendung des Dialogeditors finden Sie unter [Dialogeditor](../../windows/dialog-editor.md).

### <a name="to-declare-a-variable-based-on-your-reusable-class"></a>So deklarieren Sie eine Variable basierend auf Ihrer wiederverwendbaren Klasse

1. Ziehen Sie beim Bearbeiten des Dialogfelds ein Steuerelement desselben Typs wie die Basisklasse des neuen Steuerelements aus der Symbolleiste Steuerelemente in das Dialogfeld.

1. Platzieren Sie den Mauszeiger über dem gelöschten Steuerelement.

1. Doppelklicken Sie beim Drücken der STRG-Taste auf das Steuerelement.

   Das Dialogfeld [Elementvariable hinzufügen](../../ide/add-member-variable-wizard.md) wird angezeigt.

1. Wählen Sie im Feld **Zugriff** den richtigen Zugriff für Ihr Steuerelement aus.

1. Klicken Sie auf das Kontrollkästchen **Steuerelementvariable.**

1. Geben Sie im Feld **Variablenname** einen Namen ein.

1. Klicken Sie unter **Kategorie**auf **Steuerung**.

1. Wählen Sie in der Liste **Steuerungs-ID** das Steuerelement aus, das Sie hinzugefügt haben. In der Liste **Variablentyp** sollte der richtige Variablentyp angezeigt werden, und im Feld **Steuerelementtyp** sollte der richtige Steuertyp angezeigt werden.

1. Fügen Sie im Feld **Kommentar** einen beliebigen Kommentar hinzu, der in Ihrem Code angezeigt werden soll.

1. Klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

[Zuordnen von Meldungen zu Funktionen](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class (Hinzufügen einer Klasse)](../../ide/adding-a-class-visual-cpp.md)<br/>
[Hinzufügen einer Memberfunktion](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable (Hinzufügen einer Membervariablen)](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function (Überschreiben einer virtuellen Funktion)](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler (MFC-Meldungshandler)](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigating the Class Structure (Navigieren in der Klassenstruktur)](../../ide/navigate-code-cpp.md)
