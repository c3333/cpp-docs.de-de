---
title: Aktualisieren des Textes in der Statusleiste
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: 723046fc1721cc46608e00f19a4431ef081be13d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366692"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>Aktualisieren des Textes in der Statusleiste

In diesem Artikel wird erläutert, wie Sie den Text ändern, der in einem MFC-Statusleistenbereich angezeigt wird. Eine Statusleiste – ein Fensterobjekt der Klasse [CStatusBar](../mfc/reference/cstatusbar-class.md) – enthält mehrere "Panes". Jeder Bereich ist ein rechteckiger Bereich der Statusleiste, den Sie zum Anzeigen von Informationen verwenden können. Beispielsweise zeigen viele Anwendungen den Status der CAPS LOCK, NUM LOCK und anderer Tasten in den rechten Bereichen an. Anwendungen zeigen häufig auch informativen Text im linken Bereich (Bereich 0) an, der manchmal als "Nachrichtenbereich" bezeichnet wird. Die Standard-MFC-Statusleiste verwendet beispielsweise den Meldungsbereich, um eine Zeichenfolge anzuzeigen, die das aktuell ausgewählte Menüelement oder die Symbolleistenschaltfläche erläutert. Die Abbildung in [Statusleisten](../mfc/status-bar-implementation-in-mfc.md) zeigt eine Statusleiste aus einer vom Anwendungs-Assistenten erstellten MFC-Anwendung.

Standardmäßig aktiviert MFC beim `CStatusBar` Erstellen des Bereichs keinen Bereich. Um einen Bereich zu aktivieren, müssen Sie das ON_UPDATE_COMMAND_UI-Makro für jeden Bereich in der Statusleiste verwenden und die Bereiche aktualisieren. Da Bereiche keine WM_COMMAND Nachrichten senden (sie sind nicht wie Symbolleistenschaltflächen), müssen Sie den Code manuell eingeben.

Angenommen, ein Bereich `ID_INDICATOR_PAGE` hat den Befehlsbezeichner und enthält die aktuelle Seitenzahl in einem Dokument. Im folgenden Verfahren wird beschrieben, wie Sie einen neuen Bereich in der Statusleiste erstellen.

### <a name="to-make-a-new-pane"></a>So erstellen Sie einen neuen Bereich

1. Definieren Sie die Befehls-ID des Bereichs.

   Klicken Sie im Menü **Ansicht** auf **Ressourcenansicht**. Klicken Sie mit der rechten Maustaste auf die Projektressource, und klicken Sie auf **Ressourcensymbole**. Klicken Sie im Dialogfeld `New`Ressourcensymbole auf . Geben Sie einen Befehls-ID-Namen ein: z. `ID_INDICATOR_PAGE`B. . Geben Sie einen Wert für die ID an, oder akzeptieren Sie den im Dialogfeld Ressourcensymbole vorgeschlagenen Wert. Akzeptieren Sie `ID_INDICATOR_PAGE`z. B. für den Standardwert. Schließen Sie das Dialogfeld Ressourcensymbole.

1. Definieren Sie eine Standardzeichenfolge, die im Bereich angezeigt werden soll.

   Wenn die Ressourcenansicht geöffnet ist, doppelklicken Sie im Fenster, in dem Ressourcentypen für Ihre Anwendung aufgeführt sind, auf **Stringtabelle** doppelklicken. Wenn der **String Table-Editor** geöffnet ist, wählen Sie neue **Zeichenfolge** aus dem Menü **Einfügen** aus. Wählen Sie die Befehls-ID `ID_INDICATOR_PAGE`Ihres Bereichs aus (z. B. ) und geben Sie einen Standardzeichenfolgenwert ein, z. B. "Seite ". Schließen Sie den Zeichenfolgeneditor. (Sie benötigen eine Standardzeichenfolge, um einen Compilerfehler zu vermeiden.)

1. Fügen Sie den Bereich dem *Indikatoren-Array* hinzu.

   In der Datei MAINFRM. CPP, suchen *indicators* Sie das Indikatoren-Array. Dieses Array listet Befehls-IDs für alle Indikatoren der Statusleiste auf, in der Reihenfolge von links nach rechts. Geben Sie an der entsprechenden Stelle im Array die Befehls-ID Ihres Bereichs ein, wie hier für `ID_INDICATOR_PAGE`folgende Informationen gezeigt:

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

Es wird empfohlen, Text in einem `SetText` Bereich anzuzeigen, `CCmdUI` indem die Memberfunktion der Klasse in einer Aktualisierungshandlerfunktion für den Bereich aufruft. Sie können z. B. eine Ganzzahlvariable *einrichten, m_nPage* die `SetText` die aktuelle Seitenzahl enthält, und den Text des Bereichs auf eine Zeichenfolgenversion dieser Zahl festlegen.

> [!NOTE]
> Der `SetText` Ansatz wird empfohlen. Es ist möglich, diese Aufgabe auf einer `CStatusBar` etwas `SetPaneText`niedrigeren Ebene auszuführen, indem Sie die Memberfunktion aufrufen. Trotzdem benötigen Sie weiterhin einen Updatehandler. Ohne einen solchen Handler für den Bereich deaktiviert MFC den Bereich automatisch und löscht dessen Inhalt.

Das folgende Verfahren zeigt, wie Sie eine Aktualisierungshandlerfunktion verwenden, um Text in einem Bereich anzuzeigen.

#### <a name="to-make-a-pane-display-text"></a>So erstellen Sie einen Bereich zum Anzeigen von Text

1. Fügen Sie einen Befehlsaktualisierungshandler für den Befehl hinzu.

   Fügen Sie manuell einen Prototyp für den `ID_INDICATOR_PAGE` Handler hinzu, wie hier gezeigt (in MAINFRM. H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. In der entsprechenden . CPP-Datei, fügen Sie die Definition des `ID_INDICATOR_PAGE` Handlers hinzu, wie hier gezeigt (in MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   Die letzten drei Zeilen dieses Handlers sind der Code, der Ihren Text anzeigt.

1. Fügen Sie in der entsprechenden Meldungszuordnung das `ID_INDICATOR_PAGE` ON_UPDATE_COMMAND_UI-Makro hinzu, wie hier gezeigt (in MAINFRM. CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

Nachdem Sie den Wert der *m_nPage* Membervariablen (der Klasse `CMainFrame`) definiert haben, bewirkt diese Technik, dass die Seitenzahl während der Verarbeitung im Leerlauf auf die gleiche Weise angezeigt wird, wie die Anwendung andere Indikatoren aktualisiert. Wenn *sich m_nPage* ändert, ändert sich die Anzeige während der nächsten Leerlaufschleife.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Aktualisieren von Benutzeroberflächenobjekten (wie Toolbar-Schaltflächen und Menüelemente aktualisiert werden, wenn sich die Programmbedingungen ändern)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>Siehe auch

[Implementieren der Statusleiste mit MFC](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar-Klasse](../mfc/reference/cstatusbar-class.md)
