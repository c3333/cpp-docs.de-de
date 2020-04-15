---
title: Handler für Meldungszuordnungsbereiche
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
ms.openlocfilehash: fc33df6957beab6e4e8de3093dfc00cf2651780e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370507"
---
# <a name="handlers-for-message-map-ranges"></a>Handler für Meldungszuordnungsbereiche

In diesem Artikel wird erläutert, wie Sie einen Bereich von Nachrichten einer einzelnen Nachrichtenhandlerfunktion zuordnen (anstatt eine Nachricht nur einer Funktion zuzuordnen).

Es gibt Zeiten, in denen Sie mehr als eine Nachricht oder Steuerbenachrichtigung auf genau die gleiche Weise verarbeiten müssen. In solchen Zeiten können Sie alle Nachrichten einer einzelnen Handlerfunktion zuordnen. Mit Message-Map-Bereichen können Sie dies für einen zusammenhängenden Bereich von Nachrichten tun:

- Sie können Bereiche von Befehls-IDs zuordnen, um:

  - Eine Befehlshandlerfunktion.

  - Eine Befehlsaktualisierungshandlerfunktion.

- Sie können Steuerbenachrichtigungen für einen Bereich von Steuer-IDs einer Nachrichtenhandlerfunktion zuordnen.

Zu den in diesem Artikel behandelten Themen gehören:

- [Schreiben des Nachrichtenkarteneintrags](#_core_writing_the_message.2d.map_entry)

- [Deklarieren der Handlerfunktion](#_core_declaring_the_handler_function)

- [Beispiel für einen Befehls-ID-Bereich](#_core_example_for_a_range_of_command_ids)

- [Beispiel für einen Bereich von Steuer-IDs](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Schreiben des Message-Map-Eintrags

In der . CPP-Datei, fügen Sie Ihren Message-Map-Eintrag hinzu, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

Der Meldungszuordnungseintrag besteht aus den folgenden Elementen:

- Das Message-Map-Bereichsmakro:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parameter für das Makro:

  Die ersten beiden Makros nehmen drei Parameter an:

  - Die Befehls-ID, die den Bereich startet

  - Die Befehls-ID, die den Bereich beendet

  - Der Name der Nachrichtenhandlerfunktion

  Der Bereich der Befehls-IDs muss zusammenhängend sein.

  Das dritte `ON_CONTROL_RANGE`Makro , , nimmt einen zusätzlichen ersten Parameter: eine Steuerbenachrichtigungsmeldung, z. **B. EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Deklarieren der Handlerfunktion

Fügen Sie Ihre Handlerfunktionsdeklaration in die hinzu. H-Datei. Der folgende Code zeigt, wie dies aussehen könnte, wie unten gezeigt:

[!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Handlerfunktionen für einzelne Befehle nehmen normalerweise keine Parameter an. Mit Ausnahme von Updatehandlerfunktionen erfordern Handlerfunktionen für Message-Map-Bereiche einen zusätzlichen Parameter, *nID*, vom Typ **UINT**. Dieser Parameter ist der erste Parameter. Der zusätzliche Parameter enthält die zusätzliche Befehls-ID, die erforderlich ist, um anzugeben, welchen Befehl der Benutzer tatsächlich gewählt hat.

Weitere Informationen zu Parameteranforderungen für das Aktualisieren von Handlerfunktionen finden Sie unter [Beispiel für einen Befehlsbereich iDs](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Beispiel für einen Befehlsbereich

Wann können Sie Bereiche verwenden Ein Beispiel ist die Handhabung von Befehlen wie dem Befehl Zoom im MFC-Beispiel [HIERSVR](../overview/visual-cpp-samples.md). Mit diesem Befehl wird die Ansicht vergrößert und zwischen 25 % und 300 % der normalen Größe skaliert. Die Ansichtsklasse von HIERSVR verwendet einen Bereich, um die Zoom-Befehle mit einem Meldungszuordnungseintrag zu verarbeiten, der wie folgender Weise ähnelt:

[!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Wenn Sie den Nachrichtenzuordnungseintrag schreiben, geben Sie Folgendes an:

- Zwei Befehls-IDs, die einen zusammenhängenden Bereich beginnen und beenden.

   Hier sind sie **ID_VIEW_ZOOM25** und **ID_VIEW_ZOOM300**.

- Der Name der Handlerfunktion für die Befehle.

   Hier ist `OnZoom`es .

Die Funktionsdeklaration würde wie folgt aussehen:

[!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

Der Fall von Updatehandlerfunktionen ist ähnlich und wahrscheinlich weiter nützlich. Es ist durchaus üblich, Handler für eine Reihe von Befehlen zu schreiben `ON_UPDATE_COMMAND_UI` und immer wieder denselben Code zu schreiben oder zu kopieren. Die Lösung besteht darin, einen Bereich von Befehls-IDs einer Aktualisierungshandlerfunktion mithilfe des `ON_UPDATE_COMMAND_UI_RANGE` Makros zuzuordnen. Die Befehls-IDs müssen einen zusammenhängenden Bereich bilden. Ein Beispiel finden `OnUpdateZoom` Sie unter `ON_UPDATE_COMMAND_UI_RANGE` dem Handler und seinem Message-Map-Eintrag in der Ansichtsklasse des HIERSVR-Beispiels.

Update-Handlerfunktionen für einzelne Befehle verwenden normalerweise einen einzelnen `CCmdUI*`Parameter, *pCmdUI*, vom Typ . Im Gegensatz zu Handlerfunktionen benötigen Updatehandlerfunktionen für Nachrichtenzuordnungsbereiche keinen zusätzlichen Parameter, *nID*, vom Typ **UINT**. Die Befehls-ID, die benötigt wird, um anzugeben, `CCmdUI` welchen Befehl der Benutzer tatsächlich gewählt hat, wird im Objekt gefunden.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Beispiel für einen Bereich von Steuer-IDs

Ein weiterer interessanter Fall ist das Zuordnen von Steuerbenachrichtigungsmeldungen für einen Bereich von Steuer-IDs zu einem einzelnen Handler. Angenommen, der Benutzer kann auf eine der 10 Schaltflächen klicken. Um alle 10 Schaltflächen einem Handler zuzuordnen, würde ihr Nachrichtenzuordnungseintrag wie folgt aussehen:

[!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Wenn Sie `ON_CONTROL_RANGE` das Makro in die Nachrichtenzuordnung schreiben, geben Sie Folgendes an:

- Eine bestimmte Steuerbenachrichtigungsmeldung.

   Hier ist es **BN_CLICKED**.

- Die Steuerelement-ID-Werte, die dem zusammenhängenden Steuerelementbereich zugeordnet sind.

   Hier sind **dies IDC_BUTTON1** und **IDC_BUTTON10**.

- Der Name der Nachrichtenhandlerfunktion.

   Hier ist `OnButtonClicked`es .

Wenn Sie die Handlerfunktion schreiben, geben Sie den zusätzlichen **UINT-Parameter** an, wie im Folgenden dargestellt:

[!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

Der `OnButtonClicked` Handler für eine einzelne **BN_CLICKED** Nachricht keine Parameter an. Derselbe Handler für einen Bereich von Schaltflächen benötigt eine **UINT**. Der zusätzliche Parameter ermöglicht die Identifizierung des bestimmten Steuerelements, das für die Generierung der **BN_CLICKED** Nachricht verantwortlich ist.

Der im Beispiel gezeigte Code ist typisch: `int` Konvertieren des Wertes, der innerhalb des Nachrichtenbereichs an einen übergeben wird, und bestätigen, dass dies der Fall ist. Dann können Sie je nachdem, auf welche Schaltfläche geklickt wurde, eine andere Aktion ausführen.

## <a name="see-also"></a>Siehe auch

[Deklarieren von Meldungshandlerfunktionen](../mfc/declaring-message-handler-functions.md)
