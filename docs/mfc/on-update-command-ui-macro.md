---
title: ON_UPDATE_COMMAND_UI Macro
ms.date: 09/06/2019
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: ba5a48fabb9142c080e688e189e0983ad5ba2eda
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624047"
---
# <a name="on_update_command_ui-macro"></a>ON_UPDATE_COMMAND_UI Macro

Öffnen Sie **Klassenansicht**, und klicken Sie dann mit der rechten Maustaste auf die Klasse, der der Handler hinzugefügt wird, und wählen Sie den **Klassen-Assistenten**aus, um ein Benutzeroberflächen Objekt mit einem Befehls Aktualisierungs Handler in einem Befehls Zielobjekt zu verbinden. Suchen Sie die ID des Benutzeroberflächen Objekts in der Liste auf der linken Seite, und wählen Sie dann im rechten Bereich **UPDATE_COMMAND_UI** aus, und klicken Sie auf **Handler hinzufügen**. Dadurch wird eine Handlerfunktion in der-Klasse erstellt und der entsprechende Eintrag in der Meldungs Zuordnung hinzugefügt. Weitere Informationen finden [Sie unter Mapping messages to Functions](reference/mapping-messages-to-functions.md) . Sie können zusätzliche Nachrichten angeben, die im Bereich **Meldungen** verarbeitet werden sollen.

Um z. b. den Befehl Clear All im Menü Bearbeiten des Programms zu aktualisieren, verwenden Sie den **Klassen-Assistenten** , um einen Meldungs Zuordnungs Eintrag in der ausgewählten Klasse hinzuzufügen, eine Funktionsdeklaration für einen Befehls Aktualisierungs Handler `OnUpdateEditClearAll` , der in der Klassen Deklaration aufgerufen wird, und eine leere Funktions Vorlage in der Implementierungs Datei der Klasse. Der Funktionsprototyp sieht wie folgt aus:

[!code-cpp[NVC_MFCDocView#2](codesnippet/cpp/on-update-command-ui-macro_1.h)]

Wie bei allen Handlern zeigt die Funktionsdeklaration das **afx_msg** -Schlüsselwort an. Wie bei allen Update Handlern benötigt es ein Argument, einen Zeiger auf ein- `CCmdUI` Objekt.

## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Aktualisieren von Benutzeroberflächenobjekten](how-to-update-user-interface-objects.md)
