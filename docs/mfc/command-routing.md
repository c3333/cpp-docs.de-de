---
title: Befehlsrouting
ms.date: 09/06/2019
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: e47ffd38b342301da32abae9690738ef83c0426b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620690"
---
# <a name="command-routing"></a>Befehlsrouting

Ihre Verantwortung bei der Arbeit mit Befehlen beschränkt sich auf das Erstellen von Meldungs Zuordnungs Verbindungen zwischen Befehlen und ihren Handlerfunktionen, eine Aufgabe, für die Sie den [MFC-Klassen-Assistenten](reference/mfc-class-wizard.md)verwenden. Außerdem müssen Sie den Code für die Befehls Handler schreiben.

Windows-Meldungen werden in der Regel an das Hauptrahmenfenster gesendet, aber Befehlsmeldungen werden dann an andere Objekte weitergeleitet. Das Framework leitet Befehle durch eine Standardsequenz von Befehlszielobjekten, wobei vorausgesetzt wird, dass eines von ihnen einen Handler für den Befehl besitzt. Jedes Befehlszielobjekt überprüft seine Meldungszuordnung, um festzustellen, ob es die eingehende Meldung verarbeiten kann.

Verschiedene Befehlszielklassen überprüfen ihre eigenen Meldungszuordnungen zu unterschiedlichen Zeitpunkten. In der Regel leitet eine Klasse den Befehl an bestimmte andere Objekte weiter, um ihnen die erste Chance mit dem Befehl zu geben. Wenn keines dieser Objekte den Befehl verarbeitet, überprüft die ursprüngliche Klasse ihre eigene Meldungszuordnung. Wenn sie dann keinen Handler bereitstellen kann, kann sie den Befehl noch an weitere Befehlsziele leiten. Die Tabelle [Standardmäßige Befehlsweiterleitung](#_core_standard_command_route) unten zeigt, wie die einzelnen Klassen diese Sequenz strukturieren. Die allgemeine Reihenfolge, in der ein Befehlsziel einen Befehl weiterleitet, ist:

1. An sein derzeit aktives untergeordnetes Befehlszielobjekt.

1. An sich selbst.

1. An andere Befehlsziele.

Wie teuer ist dieser Routing Mechanismus im Vergleich zu den Aktionen, die Ihr Handler als Reaktion auf einen Befehl durchführt, ist der Aufwand für das Routing gering. Beachten Sie, dass das Framework nur dann Befehle generiert, wenn der Benutzer mit einem Benutzeroberflächenobjekt interagiert.

### <a name="standard-command-route"></a><a name="_core_standard_command_route"></a> Standardmäßige Befehlsweiterleitung

|Wenn ein Objekt dieses Typs einen Befehl empfängt. . .|Es gibt sich selbst und anderen Befehlszielobjekten in der folgenden Reihenfolge eine Chance, den Befehl zu verarbeiten:|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|MDI-Rahmenfenster (`CMDIFrameWnd`)|1. aktiv`CMDIChildWnd`<br />2. dieses Rahmen Fenster<br />3. Anwendung ( `CWinApp` Objekt)|
|Dokumentrahmenfenster (`CFrameWnd`, `CMDIChildWnd`)|1. aktive Ansicht<br />2. dieses Rahmen Fenster<br />3. Anwendung ( `CWinApp` Objekt)|
|Sicht|1. diese Ansicht<br />2. an die Ansicht angefügtes Dokument|
|Dokument|1. dieses Dokument<br />2. Dokument Vorlage, die an das Dokument angefügt ist|
|Dialogfeld|1. dieses Dialogfeld<br />2. Fenster, das das Dialogfeld besitzt<br />3. Anwendung ( `CWinApp` Objekt)|

Wo nummerierte Einträge in der zweiten Spalte der vorstehenden Tabelle andere Objekte erwähnen, z. B. ein Dokument, finden Sie das entsprechende Element in der ersten Spalte. Wenn Sie z. B. in der zweiten Spalte lesen, dass die Sicht einen Befehl an sein Dokument weiterleitet, können Sie in der ersten Spalte im Eintrag „Dokument“ dem Routing weiter folgen.

## <a name="see-also"></a>Siehe auch

[So ruft das Framework einen Handler auf](how-the-framework-calls-a-handler.md)
