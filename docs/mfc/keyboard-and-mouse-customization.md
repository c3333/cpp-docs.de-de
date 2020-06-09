---
title: Anpassen von Tastatur und Maus
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 262555b060f226a86438a2189eda44d83c55d5a2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621501"
---
# <a name="keyboard-and-mouse-customization"></a>Anpassen von Tastatur und Maus

Mit MFC kann der Benutzer der Anwendung anpassen, wie die Tastatur-und Maus Eingaben behandelt werden. Der Benutzer kann Tastatureingaben anpassen, indem er Befehle Tastenkombinationen zuweist. Der Benutzer kann die Maus Eingaben auch anpassen, indem er den Befehl auswählt, der ausgeführt werden soll, wenn der Benutzer in bestimmte Fenster der Anwendung doppelklickt. In diesem Thema wird erläutert, wie die Eingabe für die Anwendung angepasst wird.

Im Dialogfeld **Anpassung** kann der Benutzer die benutzerdefinierten Steuerelemente für die Maus und die Tastatur ändern. Um dieses Dialogfeld anzuzeigen, zeigt der Benutzer im Menü **Ansicht** die Option **Anpassen** an und klickt dann auf **Symbolleisten und Andocken**. Im Dialogfeld klickt der Benutzer auf die Registerkarte **Tastatur** oder **Maus** .

## <a name="keyboard-customization"></a>Tastatur Anpassung

Die folgende Abbildung zeigt die Registerkarte **Tastatur** des Dialog Felds **Anpassung** .

![Registerkarte "Tastatur" im Dialogfeld "Anpassen"](../mfc/media/mfcnextkeyboardtab.png "Registerkarte "Tastatur" im Dialogfeld "Anpassen"") <br/>
Registerkarte Tastatur Anpassung

Der Benutzer interagiert mit der Registerkarte "Tastatur", um einem Befehl eine oder mehrere Tastenkombinationen zuzuweisen. Die verfügbaren Befehle sind auf der linken Seite der Registerkarte aufgeführt. Der Benutzer kann alle verfügbaren Befehle im Menü auswählen. Nur Menübefehle können einer Tastenkombination zugeordnet werden. Nachdem der Benutzer eine neue Verknüpfung eingegeben hat, wird die Schaltfläche " **zuweisen** " aktiviert. Wenn der Benutzer auf diese Schaltfläche klickt, ordnet die Anwendung den ausgewählten Befehl dieser Verknüpfung zu.

Alle momentan zugewiesenen Tastenkombinationen werden im Listenfeld in der rechten Spalte aufgelistet. Der Benutzer kann auch einzelne Verknüpfungen auswählen und entfernen oder alle Zuordnungen für die Anwendung zurücksetzen.

Wenn Sie diese Anpassung in der Anwendung unterstützen möchten, müssen Sie ein [ckeyboardmanager](reference/ckeyboardmanager-class.md) -Objekt erstellen. Um ein- `CKeyboardManager` Objekt zu erstellen, rufen Sie die [CWinAppEx:: initkeyboardmanager](reference/cwinappex-class.md#initkeyboardmanager)-Funktion auf. Mit dieser Methode wird ein Tastatur-Manager erstellt und initialisiert. Wenn Sie einen Tastatur-Manager manuell erstellen, müssen Sie dennoch aufzurufen, `CWinAppEx::InitKeyboardManager` um ihn zu initialisieren.

Wenn Sie den Assistenten zum Erstellen der Anwendung verwenden, initialisiert der Assistent den Tastatur-Manager. Nachdem die Anwendung den Tastatur-Manager initialisiert hat, fügt das Framework dem **Anpassungs** Dialogfeld eine Registerkarte **Tastatur** hinzu.

## <a name="mouse-customization"></a>Maus Anpassung

In der folgenden Abbildung wird die Registerkarte " **Maus** " des Dialog Felds " **Anpassung** " gezeigt.

![Registerkarte "Maus" im Dialogfeld "Anpassen"](../mfc/media/mfcnextmousetab.png "Registerkarte "Maus" im Dialogfeld "Anpassen"") <br/>
Registerkarte "Maus Anpassung

Der Benutzer interagiert mit dieser Registerkarte, um der Maus Doppelklick Aktion einen Menübefehl zuzuweisen. Der Benutzer wählt eine Ansicht auf der linken Seite des Fensters aus und verwendet dann die Steuerelemente auf der rechten Seite, um einen Befehl mit der Doppelklick Aktion zuzuordnen. Nachdem der Benutzer auf **Schließen**geklickt hat, führt die Anwendung den zugeordneten Befehl aus, wenn der Benutzer auf eine beliebige Stelle in der Ansicht doppelklickt.

Standardmäßig ist die Maus Anpassung nicht aktiviert, wenn Sie eine Anwendung mit dem Assistenten erstellen.

#### <a name="to-enable-mouse-customization"></a>So aktivieren Sie die Maus Anpassung

1. Initialisieren Sie ein [cmousemanager](reference/cmousemanager-class.md) -Objekt, indem Sie [CWinAppEx:: initmousemanager](reference/cwinappex-class.md#initmousemanager)aufrufen.

1. Rufen Sie mithilfe von [CWinAppEx:: getmousemanager](reference/cwinappex-class.md#getmousemanager)einen Zeiger auf den Maus-Manager ab.

1. Fügen Sie dem Maus-Manager mithilfe der [cmousemanager:: AddView](reference/cmousemanager-class.md#addview) -Methode Sichten hinzu. Führen Sie dies für jede Ansicht aus, die Sie dem Maus-Manager hinzufügen möchten.

Nachdem die Anwendung den Maus-Manager initialisiert hat, fügt das Framework die **Maus** Registerkarte zum Dialogfeld **Anpassen** hinzu. Wenn Sie keine Sichten hinzufügen, führt der Zugriff auf die Registerkarte zu einer nicht behandelten Ausnahme. Nachdem Sie eine Liste von Sichten erstellt haben, ist die **Maus** Registerkarte für den Benutzer verfügbar.

Wenn Sie dem Maus-Manager eine neue Ansicht hinzufügen, geben Sie Ihr eine eindeutige ID. Wenn Sie die Maus Anpassung für ein Fenster unterstützen möchten, müssen Sie die WM_LBUTTONDBLCLICK Nachricht verarbeiten und die [CWinAppEx:: onviewdoubleclick](reference/cwinappex-class.md#onviewdoubleclick) -Funktion aufrufen. Wenn Sie diese Funktion aufgerufen haben, ist einer der Parameter die ID für dieses Fenster. Es liegt in der Verantwortung des Programmierers, die ID-Nummern und die zugeordneten Objekte nachzuverfolgen.

## <a name="security-concerns"></a>Sicherheitsaspekte

Wie in [benutzerdefinierten Tools](user-defined-tools.md)beschrieben, kann der Benutzer dem Doppelklick-Ereignis eine benutzerdefinierte Tool-ID zuordnen. Wenn der Benutzer auf eine Ansicht doppelklickt, sucht die Anwendung nach einem Benutzer Tool, das mit der zugeordneten ID übereinstimmt. Wenn die Anwendung ein entsprechendes Tool findet, führt Sie das Tool aus. Wenn die Anwendung kein übereinstimmendes Tool finden kann, sendet Sie eine WM_COMMAND Nachricht mit der ID an die Ansicht, auf die doppelt geklickt wurde.

Die angepassten Einstellungen werden in der Registrierung gespeichert. Durch Bearbeiten der Registrierung kann ein Angreifer eine gültige Benutzer Tool-ID durch einen beliebigen Befehl ersetzen. Wenn der Benutzer auf eine Ansicht doppelklickt, verarbeitet die Ansicht den Befehl, den der Angreifer gepflanzt hat. Dies kann zu unerwartetem und potenziell gefährdem Verhalten führen.

Außerdem kann diese Art von Angriff Benutzeroberflächen-Schutzmaßnahmen umgehen. Nehmen Sie beispielsweise an, dass eine Anwendung den Druck deaktiviert hat. Das heißt, in der Benutzeroberfläche sind das Menü "Drucken" und die Schaltfläche " **Drucken** " nicht verfügbar. Normalerweise wird dadurch das Drucken der Anwendung verhindert. Wenn jedoch ein Angreifer die Registrierung bearbeitet hat, könnte ein Benutzer den Befehl Drucken direkt durch Doppelklicken auf die Ansicht senden und dabei die Elemente der Benutzeroberfläche umgehen, die nicht verfügbar sind.

Um diese Art von Angriffen zu schützen, fügen Sie Ihrem Anwendungs Befehls Handler Code hinzu, um zu überprüfen, ob ein Befehl gültig ist, bevor er ausgeführt wird. Hängen Sie nicht von der Benutzeroberfläche ab, um zu verhindern, dass ein Befehl an die Anwendung gesendet wird.

## <a name="see-also"></a>Siehe auch

[Anpassung für MFC](customization-for-mfc.md)<br/>
[Ckeyboardmanager-Klasse](reference/ckeyboardmanager-class.md)<br/>
[Cmousmanager-Klasse](reference/cmousemanager-class.md)<br/>
[Sicherheitsauswirkungen der Anpassung](security-implications-of-customization.md)
