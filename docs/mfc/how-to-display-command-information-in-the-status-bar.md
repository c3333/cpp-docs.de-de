---
title: 'Gewusst wie: Anzeigen von Befehlsinformationen in der Statusleiste'
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: bff5d5b20ecc9b20b7b1e8335cda34d582441425
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622535"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Gewusst wie: Anzeigen von Befehlsinformationen in der Statusleiste

Wenn Sie den Anwendungs-Assistenten ausführen, um das Gerüst der Anwendung zu erstellen, können Sie eine Symbolleiste und eine Statusleiste unterstützen. Eine Option im Anwendungs-Assistenten unterstützt beides. Wenn eine Statusleiste vorhanden ist, stellt die Anwendung automatisch nützliches Feedback bereit, da der Benutzer den Mauszeiger über Elemente in den Menüs verschiebt. Die Anwendung zeigt automatisch eine Eingabe Aufforderungs Zeichenfolge in der Statusleiste an, wenn das Menü Element hervorgehoben ist. Wenn der Benutzer beispielsweise den Mauszeiger über den Befehl " **Ausschneiden** " im Menü " **Bearbeiten** " bewegt, wird in der Statusleiste möglicherweise "die Auswahl wird gekürzt und in der Zwischenablage abgelegt" im Nachrichtenbereich der Statusleiste angezeigt. Die Eingabeaufforderung hilft dem Benutzer, den Zweck des Menü Elements zu verstehen. Dies funktioniert auch, wenn der Benutzer auf eine Symbolleisten Schaltfläche klickt.

Sie können dieser Status leisten Hilfe hinzufügen, indem Sie Eingabe Aufforderungs Zeichenfolgen für Menü Elemente definieren, die Sie dem Programm hinzufügen. Geben Sie hierzu die Eingabe Aufforderungs Zeichenfolgen an, wenn Sie die Eigenschaften des Menü Elements im Menü-Editor bearbeiten. Die von Ihnen definierten Zeichen folgen werden in der Anwendungs Ressourcen Datei gespeichert. Sie verfügen über dieselben IDs wie die von Ihnen erläuternden Befehle.

Standardmäßig fügt der Anwendungs-Assistent **AFX_IDS_IDLEMESSAGE**hinzu, die ID für eine Standardmeldung, die angezeigt wird, wenn das Programm auf neue Nachrichten wartet. Wenn Sie im Anwendungs-Assistenten die kontextabhängige Hilfe Option angeben, wird die Meldung in "für Hilfe, drücken Sie F1" geändert.

## <a name="see-also"></a>Siehe auch

[Meldungsbehandlung und Zuordnung](message-handling-and-mapping.md)
