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
ms.openlocfilehash: 44194a6e5bafea2b17c9a1d58c41bf9dc541729d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231909"
---
# <a name="handlers-for-message-map-ranges"></a>Handler für Meldungszuordnungsbereiche

In diesem Artikel wird erläutert, wie Sie eine Reihe von Nachrichten einer einzelnen nachrichtenhandlerfunktion zuordnen (anstatt eine Nachricht nur einer Funktion zuzuordnen).

Es gibt Zeiten, in denen Sie mehr als eine Nachricht oder eine Steuerungs Benachrichtigung auf genau die gleiche Weise verarbeiten müssen. Zu diesem Zeitpunkt können Sie alle Nachrichten einer einzelnen Handlerfunktion zuordnen. Nachrichten Zuordnungs Bereiche ermöglichen es Ihnen, dies für einen zusammenhängenden Bereich von Nachrichten zu erreichen:

- Sie können Bereiche von Befehls-IDs zuordnen:

  - Eine Befehls Handler-Funktion.

  - Eine befehlsaktualisierungs-Handlerfunktion.

- Sie können Steuerelement Benachrichtigungs Meldungen für einen Bereich von Steuerelement-IDs an eine nachrichtenhandlerfunktion zuordnen.

Zu den in diesem Artikel behandelten Themen gehören:

- [Der Nachrichten Zuordnungs Eintrag wird geschrieben.](#_core_writing_the_message.2d.map_entry)

- [Deklarieren der Handlerfunktion](#_core_declaring_the_handler_function)

- [Beispiel für einen Bereich von Befehls-IDs](#_core_example_for_a_range_of_command_ids)

- [Beispiel für einen Bereich von Steuerelement-IDs](#_core_example_for_a_range_of_control_ids)

## <a name="writing-the-message-map-entry"></a><a name="_core_writing_the_message.2d.map_entry"></a>Der Nachrichten Zuordnungs Eintrag wird geschrieben.

In der. Cpp-Datei, fügen Sie Ihren Meldungs Zuordnungs Eintrag hinzu, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCMessageHandling#6](codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]

Der Nachrichten Zuordnungs Eintrag besteht aus den folgenden Elementen:

- Das Nachrichten Zuordnungs Bereichs-Makro:

  - [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)

  - [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)

  - [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)

- Parameter für das Makro:

  Die ersten beiden Makros nehmen drei Parameter an:

  - Die Befehls-ID, mit der der Bereich gestartet wird.

  - Die Befehls-ID, die den Bereich endet.

  - Der Name der nachrichtenhandlerfunktion.

  Der Bereich der Befehls-IDs muss zusammenhängend sein.

  Das dritte Makro, `ON_CONTROL_RANGE` , übernimmt einen zusätzlichen ersten Parameter: eine Steuerelement Benachrichtigungs Meldung, wie z. b. **EN_CHANGE**.

## <a name="declaring-the-handler-function"></a><a name="_core_declaring_the_handler_function"></a>Deklarieren der Handlerfunktion

Fügen Sie die Deklaration der Handlerfunktion in hinzu. H-Datei. Der folgende Code zeigt, wie dies aussehen könnte, wie unten dargestellt:

[!code-cpp[NVC_MFCMessageHandling#7](codesnippet/cpp/handlers-for-message-map-ranges_2.h)]

Handlerfunktionen für einzelne Befehle nehmen normalerweise keine Parameter an. Mit Ausnahme von Update Handlerfunktionen erfordern Handlerfunktionen für Meldungs Zuordnungs Bereiche den zusätzlichen Parameter *NID*vom Typ **uint**. Dieser Parameter ist der erste Parameter. Der zusätzliche Parameter gibt die zusätzliche Befehls-ID an, die erforderlich ist, um anzugeben, welcher Befehl der Benutzer tatsächlich ausgewählt hat

Weitere Informationen zu den Parameter Anforderungen für das Aktualisieren von Handlerfunktionen finden Sie unter [Beispiel für einen Bereich von Befehls-IDs](#_core_example_for_a_range_of_command_ids).

## <a name="example-for-a-range-of-command-ids"></a><a name="_core_example_for_a_range_of_command_ids"></a>Beispiel für einen Bereich von Befehls-IDs

Wenn Sie ggf. Bereiche verwenden, können Sie beispielsweise Befehle wie den Zoom-Befehl in der MFC-Beispiel- [Hierarchie](../overview/visual-cpp-samples.md)verarbeiten. Mit diesem Befehl wird die Ansicht vergrößert und zwischen 25% und 300% ihrer normalen Größe skaliert. Die Ansichts Klasse von Hierarchien verwendet einen Bereich, um die Zoom Befehle mit einem Meldungs Zuordnungs Eintrag zu verarbeiten, der dem folgenden ähnelt:

[!code-cpp[NVC_MFCMessageHandling#8](codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]

Wenn Sie den Meldungs Zuordnungs Eintrag schreiben, geben Sie Folgendes an:

- Zwei Befehls-IDs, beginnend und Ende eines zusammenhängenden Bereichs.

   Hier sind Sie **ID_VIEW_ZOOM25** und **ID_VIEW_ZOOM300**.

- Der Name der Handlerfunktion für die Befehle.

   Hier ist es `OnZoom` .

Die Funktionsdeklaration ähnelt der folgenden:

[!code-cpp[NVC_MFCMessageHandling#9](codesnippet/cpp/handlers-for-message-map-ranges_4.h)]

Der Fall von Update Handler-Funktionen ist ähnlich und wahrscheinlich eher sehr nützlich. Es ist sehr üblich, `ON_UPDATE_COMMAND_UI` Handler für eine Reihe von Befehlen zu schreiben und zu erfahren, wie Sie denselben Code immer wieder schreiben oder kopieren. Die Lösung besteht darin, mithilfe des-Makros einen Bereich von Befehls-IDs einer Update Handler-Funktion zuzuordnen `ON_UPDATE_COMMAND_UI_RANGE` . Die Befehls-IDs müssen einen zusammenhängenden Bereich bilden. Ein Beispiel finden Sie unter dem Handler und dem zugehörigen Meldungs Zuordnungs `OnUpdateZoom` `ON_UPDATE_COMMAND_UI_RANGE` Eintrag in der Ansichts Klasse des Hierarchie Beispiels.

Aktualisierungshandlerfunktionen für einzelne Befehle nehmen normalerweise einen einzelnen Parameter, *pCmdUI*, vom Typ `CCmdUI*` . Im Unterschied zu Handlerfunktionen benötigen die Update Handler-Funktionen für Meldungs Zuordnungs Bereiche keinen zusätzlichen Parameter *NID*vom Typ **uint**. Die Befehls-ID, die benötigt wird, um anzugeben, welcher Befehl der Benutzer tatsächlich ausgewählt hat, wird im- `CCmdUI` Objekt gefunden.

## <a name="example-for-a-range-of-control-ids"></a><a name="_core_example_for_a_range_of_control_ids"></a>Beispiel für einen Bereich von Steuerelement-IDs

Ein weiterer interessanter Fall ist die Zuordnung von Steuerelement Benachrichtigungs Meldungen für einen Bereich von Steuerelement-IDs zu einem einzelnen Handler. Angenommen, der Benutzer kann auf eine von 10 Schaltflächen klicken. Um alle 10 Schaltflächen einem Handler zuzuordnen, sieht Ihr Nachrichten Zuordnungs Eintrag wie folgt aus:

[!code-cpp[NVC_MFCMessageHandling#10](codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]

Wenn Sie das Makro in der Meldungs Zuordnung schreiben `ON_CONTROL_RANGE` , geben Sie Folgendes an:

- Eine bestimmte Steuerelement Benachrichtigungs Meldung.

   Hier ist es **BN_CLICKED**.

- Die Steuerelement-ID-Werte, die dem zusammenhängenden Bereich von Steuerelementen zugeordnet sind.

   Hier sind **IDC_BUTTON1** und **IDC_BUTTON10**.

- Der Name der nachrichtenhandlerfunktion.

   Hier ist es `OnButtonClicked` .

Wenn Sie die Handlerfunktion schreiben, geben Sie den zusätzlichen **uint** -Parameter an, wie im folgenden dargestellt:

[!code-cpp[NVC_MFCMessageHandling#11](codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]

Der `OnButtonClicked` Handler für eine einzelne **BN_CLICKED** Nachricht nimmt keine Parameter an. Der gleiche Handler für einen Bereich von Schaltflächen erfordert eine **uint**. Der zusätzliche Parameter ermöglicht das Identifizieren eines bestimmten Steuer Elements, das für das Erstellen der **BN_CLICKED** Nachricht verantwortlich ist.

Der im Beispiel gezeigte Code ist typisch: der Wert, der an einen **`int`** innerhalb des Nachrichten Bereichs übergeben wird, und die Behauptung, dass dies der Fall ist. Dann können Sie abhängig von der Schaltfläche, auf die geklickt wurde, verschiedene Aktionen durchführen.

## <a name="see-also"></a>Weitere Informationen

[Deklarieren von nachrichtenhandlerfunktionen](declaring-message-handler-functions.md)
