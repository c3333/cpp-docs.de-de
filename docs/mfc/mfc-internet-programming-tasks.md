---
title: MFC-Internetprogrammierungsaufgaben
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
ms.openlocfilehash: 6d8a542ada94bc52ee2000bc92ae0457ec87609c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617962"
---
# <a name="mfc-internet-programming-tasks"></a>MFC-Internetprogrammierungsaufgaben

Dieser Abschnitt enthält ausführliche Schritte zum Hinzufügen von Internet Unterstützung zu Ihren Anwendungen. In den Themen wird erläutert, wie Sie die MFC-Klassen verwenden, um Ihre vorhandenen Anwendungen per Internet zu aktivieren, und wie Sie der vorhandenen COM-Komponente eine aktive Dokument Unterstützung hinzufügen. Möchten Sie ein Dokument mit den neuesten Kurs Notierungen, den Fußball Ergebnissen von Pittsburgh und der aktuellen Temperatur in der Antarktis erstellen, bietet Microsoft eine Reihe von Technologien, die Sie über das Internet unterstützen.

Zu den aktiven Technologien zählen ActiveX-Steuerelemente (früher OLE-Steuerelemente) und aktive Dokumente. WinInet für das einfache Abrufen und Speichern von Dateien über das Internet. und asynchrone Moniker für das effiziente herunterladen von Daten. Visual C++ stellt Assistenten bereit, mit denen Sie schnell mit einer Starter Anwendung loslegen können. Eine Einführung in diese Technologien finden Sie unter [Grundlagen der MFC-Internet Programmierung](mfc-internet-programming-basics.md) und [MFC-com](mfc-com.md).

Wenn Sie immer eine Datei FTP haben möchten, aber keine Winsock-und Netzwerk Programmierungs Protokolle gelernt haben, werden diese Protokolle von WinInet-Klassen gekapt, sodass Sie eine einfache Reihe von Funktionen bereitstellen können, mit denen Sie eine Client Anwendung im Internet schreiben können, um Dateien mithilfe von http, FTP und Gopher herunterzuladen. Sie können WinInet verwenden, um Verzeichnisse auf Ihrer Festplatte oder auf der ganzen Welt zu durchsuchen. Sie können Daten verschiedener Typen transparent erfassen und dem Benutzer in einer integrierten Oberfläche präsentieren.

Verfügen Sie über große Datenmengen, um asynchrone Moniker herunterzuladen, stellen Sie eine com-Lösung (Component Object Model) für das Progressive Rendering von großen Objekten bereit. WinInet kann auch asynchron verwendet werden.

In der folgenden Tabelle werden einige der Aufgaben beschrieben, die Sie mit diesen Technologien erledigen können.

|Sie haben|Zweck|Sie sollten|
|--------------|-----------------|----------------|
|Ein Webserver.|Nachverfolgen von Anmeldungen und detaillierten Informationen zu URL-Anforderungen.|Schreiben Sie einen Filter, fordern Sie Benachrichtigungen für Anmelde Ereignisse und URL-Zuordnung an.|
|Ein Webbrowser.|Dynamische Inhalte bereitstellen.|Erstellen von ActiveX-Steuerelementen und aktiven Dokumenten.|
|Eine Dokument basierte Anwendung.|Unterstützung für FTP-Datei hinzufügen.|Verwenden Sie WinInet-oder asynchrone Moniker.|

Weitere Informationen zu den ersten Schritten finden Sie in den folgenden Themen:

- [Überlegungen zum Anwendungsentwurf](application-design-choices.md)

- [Schreiben von MFC-Anwendungen](writing-mfc-applications.md)

- [ActiveX-Steuerelemente für das Internet](activex-controls-on-the-internet.md)

- [Upgrading eines vorhandenen ActiveX-Steuerelements](upgrading-an-existing-activex-control.md)

- [Asynchrone Moniker im Internet](asynchronous-monikers-on-the-internet.md)

- [Testen von Internetanwendungen](testing-internet-applications.md)

- [Internetsicherheit](internet-security-cpp.md)

## <a name="see-also"></a>Siehe auch

[Grundlagen der MFC-Internetprogrammierung](mfc-internet-programming-basics.md)<br/>
[Internetinformation – nach Aufgaben geordnet](internet-information-by-task.md)
