---
title: Überlegungen zum Anwendungsentwurf
ms.date: 09/12/2019
helpviewer_keywords:
- design
- application design [MFC], design goals
- application design [MFC], Internet applications
- Internet applications [MFC], designing applications
- Internet [MFC], vs. intranets
- applications [MFC], Internet
- server applications [MFC], vs. client applications on Internet
- client applications [MFC], vs. server applications on Internet
ms.assetid: 9b96172c-b4d4-4c69-bfb2-226ce0de6d08
ms.openlocfilehash: 89f3e5c108de1cf7b3b73a33a08e2c50b1333c92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374626"
---
# <a name="application-design-choices"></a>Überlegungen zum Anwendungsentwurf

In diesem Artikel werden einige der Entwurfsprobleme erläutert, die bei der Programmierung für das Internet zu berücksichtigen sind.

Zu den in diesem Artikel behandelten Themen gehören:

- [Intranet Versus Internet](#_core_intranet_versus_internet)

- [Client- oder Serveranwendung](#_core_client_or_server_application)

- [Die Webseite](#_core_the_web_page)

- [Browser oder Stand-Alone-Anwendung](#_core_browser_or_standalone)

- [KOM im Internet](#_core_com_on_the_internet)

- [Client Data Download Services](#_core_client_data_download_services)

Wenn Sie jetzt mit dem Schreiben des Programms beginnen möchten, finden Sie weitere Informationen unter Schreiben von [MFC-Anwendungen](../mfc/writing-mfc-applications.md).

## <a name="intranet-versus-internet"></a><a name="_core_intranet_versus_internet"></a>Intranet Versus Internet

Viele Anwendungen laufen im Internet und sind für jeden zugänglich, der über einen Browser und Internetzugang verfügt. Unternehmen implementieren auch Intranets, bei denen es sich um unternehmensweite Netzwerke handelt, die TCP/IP-Protokolle und Webbrowser verwenden. Intranets bieten eine leicht erweiterbare, zentrale Quelle für unternehmensweite Informationen. Sie können für das Upgrade von Software, für die Bereitstellung und Tabellierung von Umfragen, für den Kundensupport und für die Informationsbereitstellung verwendet werden. In der folgenden Tabelle werden die Features des Internets und der Intranets verglichen.

|Internet|Intranet|
|--------------|--------------|
|Geringe Bandbreite|Hohe Bandbreite|
|Reduzierte Sicherheit von Daten und Systemen|Kontrollierter Zugriff auf Daten und Systeme|
|Minimale Kontrolle des Inhalts|Hohe Kontrolle des Inhalts|

## <a name="client-or-server-application"></a><a name="_core_client_or_server_application"></a>Client- oder Serveranwendung

Ihre Anwendung kann auf einem Clientcomputer oder auf einem Servercomputer ausgeführt werden. Ihre Anwendung kann auch auf einem Server gespeichert und dann über das Internet heruntergeladen und auf einem Clientcomputer ausgeführt werden. MFC WinInet-Klassen werden für Clientanwendungen zum Herunterladen von Dateien verwendet. MFC- und asynchrone Monikerklassen werden zum Herunterladen von Dateien und Steuerelementeigenschaften verwendet. Klassen für ActiveX-Steuerelemente und Active-Dokumente werden für Clientanwendungen und für Anwendungen verwendet, die vom Server heruntergeladen werden, um auf einem Client ausgeführt zu werden.

## <a name="the-web-page-html-active-documents-activex-controls"></a><a name="_core_the_web_page"></a>Die Webseite: HTML, Aktive Dokumente, ActiveX-Steuerelemente

Microsoft bietet mehrere Möglichkeiten zum Bereitstellen von Inhalten auf einer Webseite. Webseiten können Standard-HTML- oder HTML-Erweiterungen, z. B. das Objekt-Tag, verwenden, um dynamische Inhalte wie ActiveX-Steuerelemente bereitzustellen.

Webbrowser zeigen in der Regel HTML-Seiten an. Aktive Dokumente können die Daten Ihrer Anwendung auch in der einfachen Point-and-Click-Schnittstelle eines COM-fähigen Browsers anzeigen. Ihr Active-Dokumentserver kann Ihr Dokument mit einem vollständigen Frame im gesamten Clientbereich mit eigenen Menüs und Symbolleisten anzeigen.

ActiveX-Steuerelemente, die Sie schreiben, können asynchron vom Server heruntergeladen und auf einer Webseite angezeigt werden. Sie können eine Skriptsprache wie VBScript verwenden, um eine clientseitige Validierung durchzuführen, bevor Sie Informationen an den Server senden.

## <a name="browser-or-stand-alone-application"></a><a name="_core_browser_or_standalone"></a>Browser oder Stand-Alone-Anwendung

Sie können ActiveX-Steuerelemente schreiben, die in eine HTML-Seite eingebettet sind, und aktive Dokumentserver, die in einem Browser angezeigt werden. Sie können HTML-Seiten schreiben, die eine Schaltfläche enthalten, um eine Anforderung zum Ausführen Ihrer ISAPI-Anwendung auf einem Webserver zu senden. Sie können eine eigenständige Anwendung schreiben, die Internetprotokolle verwendet, um Dateien herunterzuladen und die Informationen für Ihren Benutzer anzuzeigen, ohne jemals eine Browseranwendung zu verwenden.

## <a name="com-on-the-internet"></a><a name="_core_com_on_the_internet"></a>KOM im Internet

ActiveX-Steuerelemente, aktive Dokumente und asynchrone Moniker verwenden alle COM-Technologien (Component Object Model).

ActiveX-Steuerelemente stellen dynamischen Inhalt für Dokumente und Seiten auf Internetsites bereit. Mit COM können Sie ActiveX-Steuerelemente und Vollformatdokumente mithilfe von Active-Dokumenten erstellen.

Asynchrone Moniker stellen Funktionen bereit, mit denen ein Steuerelement in einer Internetumgebung gut funktionieren kann, einschließlich einer inkrementellen oder progressiven Möglichkeit zum Herunterladen von Daten. Steuerelemente müssen auch gut mit anderen Steuerelementen funktionieren, die ihre Daten auch asynchron gleichzeitig abrufen können.

## <a name="client-data-download-services"></a><a name="_core_client_data_download_services"></a>Client Data Download Services

Zwei APIs-Sätze, die beim Übertragen von Daten an Ihren Client helfen, sind WinInet und asynchrone Moniker. Wenn Sie große .gif- und .avi-Dateien und ActiveX-Steuerelemente auf Ihrer HTML-Seite haben, können Sie die Reaktionsfähigkeit für den Benutzer erhöhen, indem Sie asynchron herunterladen, entweder durch asynchrone Moniker oder WinInet asynchron.

Eine häufige Aufgabe im Internet ist die Datenübertragung. Wenn Sie active-Technologie bereits verwenden (z. B. wenn Sie über ein ActiveX-Steuerelement verfügen), können Sie asynchrone Moniker verwenden, um Daten beim Herunterladen schrittweise zu rendern. Sie können WinInet verwenden, um Daten mithilfe gängiger Internetprotokolle wie HTTP, FTP und Gopher zu übertragen. Beide Methoden bieten Protokollunabhängigkeit und eine abstrakte Ebene für die Verwendung von WinSock und TCP/IP. Sie können [WinSock](../mfc/windows-sockets-in-mfc.md) weiterhin direkt verwenden.

In der folgenden Tabelle werden verschiedene Möglichkeiten zusammengefasst, wie MFC zum Übertragen von Daten über das Internet verwendet werden kann.

|Verwenden Sie dieses Protokoll|Unter diesen Bedingungen|Verwenden dieser Klassen|
|-----------------------|----------------------------|-------------------------|
|[Internet-Download mit asynchronen Monikern](../mfc/asynchronous-monikers-on-the-internet.md)|Für asynchrone Übertragung mit COM, ActiveX-Steuerelementen und jedem Internetprotokoll.|[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md), [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md)|
|[WinInet](../mfc/win32-internet-extensions-wininet.md)|Für Internetprotokolle für HTTP, FTP und Gopher. Daten können synchron oder asynchron übertragen und in einem systemweiten Cache gespeichert werden.|[CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpFileFind](../mfc/reference/cftpfilefind-class.md), [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)und viele mehr.|
|[Winsock](../mfc/windows-sockets-in-mfc.md)|Für maximale Effizienz und Kontrolle. Erfordert das Verständnis von Sockets und TCP/IP-Protokollen.|[CSocket](../mfc/reference/csocket-class.md), [CAsyncSocket](../mfc/reference/casyncsocket-class.md)|

## <a name="see-also"></a>Siehe auch

[MFC-Internetprogrammierungsaufgaben](../mfc/mfc-internet-programming-tasks.md)<br/>
[Grundlagen der MFC-Internetprogrammierung](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32-Interneterweiterungen (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Asynchrone Moniker im Internet](../mfc/asynchronous-monikers-on-the-internet.md)
