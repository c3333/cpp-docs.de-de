---
title: Befehlsroutingerläuterung
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: d362cfe54a9b5a562237c7bb9632edae6e58228b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622911"
---
# <a name="command-routing-illustration"></a>Befehlsroutingerläuterung

Um dies zu veranschaulichen, sollten Sie eine Befehls Meldung aus dem Menü Element Alle löschen im Menü Bearbeiten einer MDI-Anwendung in Erwägung nehmen. Angenommen, die Handlerfunktion für diesen Befehl ist eine Member-Funktion der Dokument Klasse der Anwendung. Dieser Befehl erreicht seinen Handler, nachdem der Benutzer das Menü Element ausgewählt hat:

1. Das Hauptrahmen Fenster empfängt zuerst die Befehls Meldung.

1. Das Haupt-MDI-Rahmen Fenster gibt dem momentan aktiven untergeordneten MDI-Fenster die Möglichkeit, den Befehl zu verarbeiten.

1. Durch das Standard Routing eines untergeordneten MDI-Rahmen Fensters erhält seine Ansicht eine Chance vor der Überprüfung der eigenen Meldungs Zuordnung.

1. Die Ansicht prüft zuerst Ihre eigene Meldungs Zuordnung und, ohne Handler zu suchen, leitet den Befehl als nächstes an das zugehörige Dokument weiter.

1. Das Dokument überprüft seine Meldungs Zuordnung und findet einen Handler. Diese dokumentmember-Funktion wird aufgerufen, und das Routing wird beendet.

Wenn das Dokument keinen Handler enthielt, wird der Befehl als nächstes an seine Dokument Vorlage weitergeleitet. Anschließend würde der Befehl an die Ansicht und dann an das Rahmen Fenster zurückgegeben. Schließlich würde das Rahmen Fenster seine Meldungs Zuordnung überprüfen. Wenn diese Überprüfung ebenfalls fehlgeschlagen ist, wird der Befehl zurück an das Haupt-MDI-Rahmen Fenster und dann an das Anwendungs Objekt weitergeleitet – das endgültige Ziel nicht behandelter Befehle.

## <a name="see-also"></a>Siehe auch

[So ruft das Framework einen Handler auf](how-the-framework-calls-a-handler.md)
