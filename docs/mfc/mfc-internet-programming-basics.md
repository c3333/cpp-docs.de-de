---
title: Grundlagen der MFC-Internetprogrammierung
ms.date: 11/19/2018
helpviewer_keywords:
- ISAPI extensions, programming with ISAPI
- Internet applications [MFC]
- ISAPI
- ActiveX controls [MFC], Internet
- programming [MFC], Internet
- Web applications [MFC], MFC classes
- ISAPI filters [MFC], programming with ISAPI
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], writing
- Internet applications [MFC], Active technology
- Active technology [MFC]
- Internet content [MFC]
- WinInet classes [MFC]
ms.assetid: 6df2dfd0-6e3f-4587-9d01-2a32f00f8a6f
ms.openlocfilehash: c9825cdcb5cb0963a4e0d3acdeb36dfee54b70fc
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86405025"
---
# <a name="mfc-internet-programming-basics"></a>Grundlagen der MFC-Internetprogrammierung

Microsoft stellt viele APIs zum Programmieren von Client-und Server Anwendungen bereit. Viele neue Anwendungen werden für das Internet geschrieben, und als Technologien, Browserfunktionen und Änderungen an Sicherheitsoptionen werden neue Anwendungs Typen geschrieben. Browser können auf Client Computern ausgeführt werden und bieten Zugriff auf die World Wide Web und die Anzeige von HTML-Seiten, die Text, Grafiken, ActiveX-Steuerelemente und Dokumente enthalten. Server stellen FTP-, http-und Gopher-Dienste bereit und führen Server Erweiterungs Anwendungen mithilfe von CGI aus. Ihre benutzerdefinierte Anwendung kann Informationen abrufen und Daten im Internet bereitstellen.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen finden Sie unter [ActiveX](activex-controls.md)-Steuerelemente.

![Client-und Server Anwendungen](../mfc/media/vc38bq1.gif "Client- und Serveranwendungen")

MFC stellt Klassen bereit, die die Internet Programmierung unterstützen. Sie können [COleControl](reference/colecontrol-class.md) und [CDocObjectServer](reference/cdocobjectserver-class.md) und verwandte MFC-Klassen verwenden, um ActiveX-Steuerelemente und aktive Dokumente zu schreiben. Sie können MFC-Klassen wie [cinternetzession](reference/cinternetsession-class.md), [CFtpConnection](reference/cftpconnection-class.md)und [CAsyncMonikerFile](reference/casyncmonikerfile-class.md) verwenden, um Dateien und Informationen mithilfe von Internet Protokollen wie FTP, http und Gopher abzurufen.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Internetbezogene MFC-Klassen](internet-related-mfc-classes.md)

- [Themenliste für Internetinformationen](internet-information-by-topic.md)

- [Internetinformation – nach Aufgaben geordnet](internet-information-by-task.md)

- [Active Technology für das Internet](active-technology-on-the-internet.md)

- [WinInet-Grundlagen](wininet-basics.md)

- [Grundlagen zu HTML](html-basics.md)

## <a name="related-sections"></a>Verwandte Abschnitte

- [ActiveX-Steuerelemente für das Internet](activex-controls-on-the-internet.md)

- [Asynchrone Moniker im Internet](asynchronous-monikers-on-the-internet.md)

- [Win32-Interneterweiterungen (WinInet)](win32-internet-extensions-wininet.md)

- [MFC-Internetprogrammierungsaufgaben](mfc-internet-programming-tasks.md)

- [Überlegungen zum Anwendungsentwurf](application-design-choices.md)

- [Schreiben von MFC-Anwendungen](writing-mfc-applications.md)

- [Testen von Internetanwendungen](testing-internet-applications.md)

- [Internetsicherheit](internet-security-cpp.md)

- [ATL-Unterstützung für DHTML-Steuerelemente](../atl/atl-support-for-dhtml-controls.md)

## <a name="websites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Websites Weitere Informationen

Weitere Informationen zur Microsoft-Internet Technologie finden Sie unter [Microsoft-Dokumentation](https://docs.microsoft.com/).

Der [World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) veröffentlicht Spezifikationen für HTML-, http-, CGI-und andere World Wide Web-Technologien.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Weitere Internet Hilfe

Der OLE-Abschnitt der Windows SDK enthält zusätzliche Informationen zur OLE-Programmierung. Diese Informationen enthalten Details zur direkten Verwendung der Win32-WinInet-Funktionen und nicht über die MFC-Klassen. Sie enthält auch Übersichts Informationen zu Internet Technologien.
