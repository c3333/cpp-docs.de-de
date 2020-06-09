---
title: Vereinfachtes Erstellen von Internetclientanwendungen mit WinInet
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 54f63da7451dfef39a33e6b437be938cb1652326
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624571"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Vereinfachtes Erstellen von Internetclientanwendungen mit WinInet

Die Win32-Internet Erweiterungen (WinInet) ermöglichen den Zugriff auf gängige Internetprotokolle, einschließlich Gopher, FTP und http. Mithilfe von WinInet können Sie Internet Client Anwendungen auf einer höheren Programmier Ebene schreiben, ohne sich mit Winsock, TCP/IP oder den Details bestimmter Internet Protokolle befassen zu müssen. WinInet bietet eine konsistente Reihe von Funktionen für alle drei Protokolle mit einer vertrauten Win32-API-Schnittstelle. Diese Konsistenz minimiert Codeänderungen, die Sie vornehmen müssen, wenn sich das zugrunde liegende Protokoll ändert (z. b. von FTP zu http).

Visual C++ bietet zwei Möglichkeiten für die Verwendung von Wininet. Sie können die Win32-Internet Funktionen direkt abrufen (Weitere Informationen finden Sie in der OLE-Dokumentation im Windows SDK), oder Sie können WinInet über die [MFC-WinInet-Klassen](mfc-classes-for-creating-internet-client-applications.md)verwenden.

**Sie können WinInet für Folgendes verwenden:**

- HTML-Seiten herunterladen.

   HTTP ist ein Protokoll, das zum Übertragen von HTML-Seiten von einem Server auf einen Client Browser verwendet wird.

- Senden von FTP-Anforderungen zum Hochladen oder Herunterladen von Dateien oder zum erhalten von Verzeichnislisten.

   Eine typische Anforderung ist eine anonyme Anmeldung zum Herunterladen einer Datei.

- Verwenden Sie das Menüsystem von Gopher, um auf Ressourcen im Internet zuzugreifen.

   Menü Elemente können mehrere Typen sein, z. u. andere Menüs, eine indizierte Datenbank, die Sie durchsuchen können, eine Newsgroup oder eine Datei.

Für alle drei Protokolle stellen Sie eine Verbindung her, stellen Anforderungen an den Server und schließen die Verbindung.

**Die MFC-WinInet-Klassen erleichtern Folgendes:**

- Lesen Sie die Informationen von http-, FTP-und Gopher-Servern so einfach wie das Lesen von Dateien von einer Festplatte.

- Verwenden Sie http-, FTP-und Gopher-Protokolle, ohne direkt in Winsock oder TCP/IP programmieren zu müssen.

   Entwickler, die die Win32-Internet Funktionen verwenden, müssen nicht mit TCP/IP oder Windows Sockets vertraut sein. Sie können weiterhin auf Socketebene programmieren, indem Sie Winsock-und TCP/IP-Protokolle direkt verwenden, aber es ist noch einfacher, die MFC-WinInet-Klassen für den Zugriff auf http-, FTP-und Gopher-Protokolle über das Internet zu verwenden. Für viele gängige Vorgänge müssen Entwickler die Details des jeweiligen Protokolls nicht kennen, das Sie verwenden.

Viele Vorgänge, die von Ihrem Computer als Client für andere Computer im Internet ausgeführt werden können, können sehr lange dauern. Die Geschwindigkeit dieser Vorgänge wird normalerweise durch die Geschwindigkeit der Netzwerkverbindung eingeschränkt, aber Sie können auch von anderem Netzwerk Datenverkehr und der Komplexität des Vorgangs beeinflusst werden. Wenn Sie z. b. eine Verbindung mit einem Remote-FTP-Server herstellen, müssen Sie zunächst den Namen des Servers nachschlagen, um die Adresse zu ermitteln. Die Anwendung versucht dann, eine Verbindung mit dem Server an dieser Adresse herzustellen. Nachdem die Verbindung geöffnet wurde, Initiieren der Computer und der Remote Server eine Konversation mit dem File Transfer-Protokoll, bevor Sie die Verbindung tatsächlich zum Abrufen von Dateien verwenden können.

## <a name="see-also"></a>Siehe auch

[Win32-Interneterweiterungen (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Vereinfachtes Erstellen von Internetclientanwendungen mit MFC](how-mfc-makes-it-easier-to-create-internet-client-applications.md)
