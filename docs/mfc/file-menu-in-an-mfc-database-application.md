---
title: Das Dateimenü in einer MFC-Datenbankanwendung
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: fbbb4382749278708e8e758f79a618d5cad0549e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615701"
---
# <a name="file-menu-in-an-mfc-database-application"></a>Das Dateimenü in einer MFC-Datenbankanwendung

Wenn Sie eine MFC-Datenbankanwendung erstellen und die Serialisierung nicht verwenden, wie sollten Sie die Befehle "Öffnen", "Schließen", "Speichern" und "Speichern unter" im Menü "Datei" interpretieren, wenn keine Stilrichtlinien für diese Frage vorliegen, finden Sie hier einige Vorschläge:

- Entfernen Sie den Befehl zum Öffnen des Menüs "Datei" vollständig.

- Interpretieren Sie den Befehl Öffnen als "Datenbank öffnen", und zeigen Sie dem Benutzer eine Liste der Datenquellen an, die Ihre Anwendung erkennt.

- Interpretieren Sie den Open-Befehl wie möglicherweise "Profil öffnen". Bleiben geöffnet, um eine serialisierte Datei zu öffnen, aber verwenden Sie die Datei, um ein serialisiertes Dokument zu speichern, das "Benutzerprofil"-Informationen enthält, z. b. die Benutzereinstellungen, einschließlich seiner Anmelde-ID (optional mit Ausnahme des Kennworts) und der Datenquelle, mit der er zuletzt gearbeitet hat.

Der MFC-Anwendungs-Assistent unterstützt das Erstellen einer Anwendung ohne Menübefehle im Zusammenhang mit Dokument Dateien. Wählen Sie auf der Seite **Datenbankunterstützung** die Option **Daten Bank Ansicht ohne Dateiunterstützung** aus.

Um einen Datei Menübefehl auf besondere Weise zu interpretieren, müssen Sie einen oder mehrere Befehls Handler überschreiben, größtenteils in der von `CWinApp` abgeleiteten Klasse. Wenn Sie z. b. vollständig `OnFileOpen` überschreiben (wodurch der Befehl implementiert wird `ID_FILE_OPEN` ), bedeutet dies, dass "Open Database:"

- Nennen Sie die Basisklassen Version von nicht `OnFileOpen` , da Sie die Standard Implementierung des-Befehls des Frameworks vollständig ersetzen.

- Verwenden Sie stattdessen den Handler, um ein Dialogfeld anzuzeigen, in dem Datenquellen aufgelistet werden. Sie können ein solches Dialogfeld anzeigen, indem Sie `CDatabase::OpenEx` oder `CDatabase::Open` mit dem Parameter **null**aufrufen. Daraufhin wird ein ODBC-Dialogfeld geöffnet, in dem alle verfügbaren Datenquellen auf dem Computer des Benutzers angezeigt werden.

- Da Datenbankanwendungen in der Regel nicht das gesamte Dokument speichern, sollten Sie die Save-und Save as-Implementierungen wahrscheinlich entfernen, es sei denn, Sie verwenden ein serialisiertes Dokument, um Profilinformationen zu speichern. Andernfalls können Sie den Befehl "Speichern" wie z. b. "COMMIT TRANSACTION" implementieren. Weitere Informationen zum Überschreiben dieser Befehle finden Sie in der [technischen Notiz 22](tn022-standard-commands-implementation.md) .

## <a name="see-also"></a>Siehe auch

[Serialisierung: Serialisierung im Vergleich zur Datenbankeingabe/-ausgabe](serialization-serialization-vs-database-input-output.md)
