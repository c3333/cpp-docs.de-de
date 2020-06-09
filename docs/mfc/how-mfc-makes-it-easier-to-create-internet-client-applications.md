---
title: Vereinfachtes Erstellen von Internetclientanwendungen mit MFC
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: 71b72a3079cd0d0c87289c1813c09a24d9f75c89
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618555"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Vereinfachtes Erstellen von Internetclientanwendungen mit MFC

Der Microsoft Foundation Classes die Funktionen der Win32-Internet Erweiterung (WinInet) in eine Weise Kapseln, die einen vertrauten Kontext für MFC-Programmierer bereitstellt. MFC stellt drei Internet Datei Klassen ([CInternetFile](reference/cinternetfile-class.md), [CHttpFile](reference/chttpfile-class.md)und [CGopherFile](reference/cgopherfile-class.md)) bereit, die von der [CStdioFile](reference/cstdiofile-class.md) -Klasse abgeleitet sind. Diese Klassen ermöglichen nicht nur das Abrufen und manipulieren von Internet Daten, die Programmierern vertraut sind `CStdioFile` , die für lokale Dateien verwendet wurden. mit diesen Klassen können Sie jedoch lokale Dateien und Internet Dateien auf konsistente, transparente Weise verarbeiten.

Die MFC-WinInet-Klassen bieten die gleiche Funktionalität wie `CStdioFile` für Daten, die über das Internet übertragen werden. Diese Klassen abstrahieren die Internetprotokolle für http, FTP und Gopher in eine Anwendungsprogrammierschnittstelle auf hoher Ebene und bieten einen schnellen und einfachen Weg, um Anwendungen Internet fähig zu gestalten. Beispielsweise sind für das Herstellen einer Verbindung mit einem FTP-Server nach wie vor mehrere Schritte auf niedriger Ebene erforderlich, aber als MFC-Entwickler müssen Sie nur einen-Rückruf zum `CInternetSession::GetFTPConnection` Erstellen dieser Verbindung erstellen.

Außerdem bieten die MFC-WinInet-Klassen die folgenden Vorteile:

- Gepufferte e/a

- Typsichere Handles für Ihre Daten

- Standardparameter für viele Funktionen

- Ausnahmebehandlung bei häufigen Internet Fehlern

- Automatisches Bereinigen von geöffneten Handles und Verbindungen

## <a name="see-also"></a>Siehe auch

[Win32-Interneterweiterungen (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Vereinfachtes Erstellen von Internetclientanwendungen mit WinInet](how-wininet-makes-it-easier-to-create-internet-client-applications.md)
