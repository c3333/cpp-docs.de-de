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
ms.openlocfilehash: 5a8fb7bf07ec631869075c5977dcec468143ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366290"
---
# <a name="mfc-internet-programming-basics"></a>Grundlagen der MFC-Internetprogrammierung

Microsoft stellt viele APIs für die Programmierung von Client- und Serveranwendungen bereit. Viele neue Anwendungen werden für das Internet geschrieben, und wenn sich Technologien, Browserfunktionen und Sicherheitsoptionen ändern, werden neue Anwendungstypen geschrieben. Browser werden auf Clientcomputern ausgeführt, bieten Zugriff auf das World Wide Web und zeigen HTML-Seiten an, die Text, Grafiken, ActiveX-Steuerelemente und Dokumente enthalten. Server stellen FTP-, HTTP- und Gopherdienste bereit und führen Servererweiterungsanwendungen mithilfe von CGI aus. Ihre benutzerdefinierte Anwendung kann Informationen abrufen und Daten im Internet bereitstellen.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen finden Sie unter [ActiveX-Steuerelemente](activex-controls.md).

![Client- und Serveranwendungen](../mfc/media/vc38bq1.gif "Client- und Serveranwendungen")

MFC stellt Klassen bereit, die die Internetprogrammierung unterstützen. Sie können [COleControl](../mfc/reference/colecontrol-class.md) und [CDocObjectServer](../mfc/reference/cdocobjectserver-class.md) und verwandte MFC-Klassen verwenden, um ActiveX-Steuerelemente und Active-Dokumente zu schreiben. Sie können MFC-Klassen wie [CInternetSession](../mfc/reference/cinternetsession-class.md), [CFtpConnection](../mfc/reference/cftpconnection-class.md)und [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) verwenden, um Dateien und Informationen mithilfe von Internetprotokollen wie FTP, HTTP und Gopher abzurufen.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Internetbezogene MFC-Klassen](../mfc/internet-related-mfc-classes.md)

- [Themenliste für Internetinformationen](../mfc/internet-information-by-topic.md)

- [Internetinformation – nach Aufgaben geordnet](../mfc/internet-information-by-task.md)

- [Active Technology für das Internet](../mfc/active-technology-on-the-internet.md)

- [WinInet-Grundlagen](../mfc/wininet-basics.md)

- [Grundlagen zu HTML](../mfc/html-basics.md)

## <a name="related-sections"></a>Verwandte Abschnitte

- [ActiveX-Steuerelemente für das Internet](../mfc/activex-controls-on-the-internet.md)

- [Asynchrone Moniker im Internet](../mfc/asynchronous-monikers-on-the-internet.md)

- [Win32-Interneterweiterungen (WinInet)](../mfc/win32-internet-extensions-wininet.md)

- [MFC-Internetprogrammierungsaufgaben](../mfc/mfc-internet-programming-tasks.md)

- [Überlegungen zum Anwendungsentwurf](../mfc/application-design-choices.md)

- [Schreiben von MFC-Anwendungen](../mfc/writing-mfc-applications.md)

- [Testen von Internetanwendungen](../mfc/testing-internet-applications.md)

- [Internetsicherheit](../mfc/internet-security-cpp.md)

- [ATL-Unterstützung für DHTML-Steuerelemente](../atl/atl-support-for-dhtml-controls.md)

## <a name="web-sites-for-more-information"></a><a name="_core_web_sites_for_more_information"></a>Websites für weitere Informationen

Weitere Informationen zur Microsoft-Internettechnologie finden Sie auf der [Microsoft Developer Network (MSDN)-Website.](https://go.microsoft.com/fwlink/p/?linkid=56322) (Links können sich ohne vorherige Ankündigung ändern.)

Diese Website für Entwickler enthält Informationen zur Verwendung von Microsoft-Entwicklungstools und -technologien sowie aktuelle Berichte zu aktuellen und bevorstehenden Konferenzen. Auf dieser Seite können Sie zu vielen verwandten Entwicklerwebsites wechseln, einschließlich .NET und XML Developer Centers. Sie können auch Beta-SDKs und Samples herunterladen.

Das [World Wide Web Consortium (W3C)](https://go.microsoft.com/fwlink/p/?linkid=37125) veröffentlicht Spezifikationen für HTML, HTTP, CGI und andere World Wide Web-Technologien.

## <a name="more-internet-help"></a><a name="_core_more_internet_help"></a>Mehr Internet-Hilfe

Der Ole-Abschnitt des Windows SDK enthält zusätzliche Informationen zur OLE-Programmierung. Diese Informationen enthalten Details zur Verwendung der Win32 WinInet-Funktionen direkt und nicht über die MFC-Klassen. Es enthält auch Übersichtsinformationen über Internettechnologien.
