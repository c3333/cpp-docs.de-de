---
title: WinInet-Grundlagen
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: b989e5c3df63ee7b5129d01468a0f869772ed286
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367320"
---
# <a name="wininet-basics"></a>WinInet-Grundlagen

Sie können WinInet verwenden, um FTP-Unterstützung zum Herunterladen und Hochladen von Dateien aus Ihrer Anwendung hinzuzufügen. Sie können [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) überschreiben und den *Parameter dwContext* verwenden, um Benutzern beim Suchen und Herunterladen von Dateien Fortschrittsinformationen bereitzustellen.

Dieser Artikel enthält folgende Themen:

- [Erstellen eines sehr einfachen Browsers](#_core_create_a_very_simple_browser)

- [Herunterladen einer Webseite](#_core_download_a_web_page)

- [FTP eine Datei](#_core_ftp_a_file)

- [Abrufen eines Gopher-Verzeichnisses](#_core_retrieve_a_gopher_directory)

- [Statusinformationen beim Übertragen von Dateien anzeigen](#_core_display_progress_information_while_transferring_files)

Die folgenden Codeauszüge veranschaulichen, wie Sie einen einfachen Browser erstellen, eine Webseite herunterladen, eine Datei FTP erstellen und nach einer Gopherdatei suchen. Sie sind nicht als vollständige Beispiele gedacht und enthalten nicht alle Ausnahmebehandlungen.

Weitere Informationen zu WinInet finden Sie unter [Win32 Internet Extensions (WinInet)](../mfc/win32-internet-extensions-wininet.md).

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a>Erstellen eines sehr einfachen Browsers

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a>Herunterladen einer Webseite

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a>FTP eine Datei

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a>Abrufen eines Gopher-Verzeichnisses

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>OnStatusCallback verwenden

Wenn Sie die WinInet-Klassen verwenden, können Sie das [OnStatusCallback-Member](../mfc/reference/cinternetsession-class.md#onstatuscallback) des [CInternetSession-Objekts](../mfc/reference/cinternetsession-class.md) Ihrer Anwendung verwenden, um Statusinformationen abzurufen. Wenn Sie Ihr `CInternetSession` eigenes Objekt `OnStatusCallback`ableiten, überschreiben und Statusrückrufe `OnStatusCallback` aktivieren, ruft MFC Ihre Funktion mit Fortschrittsinformationen über alle Aktivitäten in dieser Internetsitzung auf.

Da eine einzelne Sitzung möglicherweise mehrere Verbindungen unterstützt (die während ihrer `OnStatusCallback` Lebensdauer viele verschiedene Vorgänge ausführen können), ist ein Mechanismus erforderlich, um jede Statusänderung mit einer bestimmten Verbindung oder Transaktion zu identifizieren. Dieser Mechanismus wird durch den Kontext-ID-Parameter bereitgestellt, der vielen Memberfunktionen in den WinInet-Supportklassen gegeben wird. Dieser Parameter ist immer vom Typ **DWORD** und wird immer *dwContext*genannt.

Der einem bestimmten Internetobjekt zugewiesene Kontext wird nur verwendet, `OnStatusCallback` um `CInternetSession` die Aktivität zu identifizieren, die das Objekt im Element des Objekts verursacht. Der Aufruf, mehrere Parameter zu `OnStatusCallback` empfangen; Diese Parameter arbeiten zusammen, um Ihrer Anwendung mitzuteilen, welche Fortschritte für welche Transaktion und Verbindung erzielt wurden.

Wenn Sie `CInternetSession` ein Objekt erstellen, können Sie dem Konstruktor einen *dwContext-Parameter* angeben. `CInternetSession`selbst verwendet nicht die Kontext-ID; Stattdessen übergibt es die Kontext-ID an alle **von InternetConnection**abgeleiteten Objekte, die nicht explizit eine eigene Kontext-ID abrufen. Diese `CInternetConnection` Objekte übergeben wiederum die Kontext-ID an `CInternetFile` Objekte, die sie erstellen, wenn Sie nicht explizit eine andere Kontext-ID angeben. Wenn Sie hingegen eine eigene Kontext-ID angeben, werden das Objekt und alle Arbeiten dieser Kontext-ID zugeordnet. Sie können die Kontext-IDs verwenden, um zu ermitteln, welche Statusinformationen Ihnen in Ihrer `OnStatusCallback` Funktion gegeben werden.

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a>Statusinformationen beim Übertragen von Dateien anzeigen

Wenn Sie beispielsweise eine Anwendung schreiben, die eine Verbindung mit einem FTP-Server herstellt, um eine Datei zu `CInternetSession` lesen, `CInternetConnection` und auch eine `CFtpSession` Verbindung zu einem `CHttpSession`HTTP-Server herstellt, um eine Webseite zu erhalten, haben Sie ein Objekt, zwei Objekte (eines wäre ein und das andere wäre ein ) und zwei `CInternetFile` Objekte (eines für jede Verbindung). Wenn Sie Standardwerte für die *dwContext-Parameter* verwendet haben, `OnStatusCallback` können Sie nicht zwischen den Aufrufen, die den Fortschritt für die FTP-Verbindung anzeigen, und den Aufrufen, die den Fortschritt für die HTTP-Verbindung anzeigen, unterscheiden. Wenn Sie eine *dwContext-ID* angeben, die `OnStatusCallback`Sie später in testen können, wissen Sie, welcher Vorgang den Rückruf generiert hat.

## <a name="see-also"></a>Siehe auch

[Grundlagen der MFC-Internetprogrammierung](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32-Interneterweiterungen (WinInet)](../mfc/win32-internet-extensions-wininet.md)
