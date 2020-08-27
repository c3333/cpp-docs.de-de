---
title: Cloud- und Webprogrammierung in Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.topic: overview
ms.openlocfilehash: 675502e9ae50c9e69ad4555502000d128d5d4cbe
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898667"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Cloud- und Webprogrammierung in Visual C++

In C++ haben Sie mehrere Optionen, um eine Verbindung mit dem Web und der Cloud herzustellen.

## <a name="microsoft-azure-sdks-and-rest-services"></a>Microsoft Azure SDKs und REST-Dienste

- [Microsoft Azure Storage-Clientbibliothek für C++](https://azure.github.io/azure-storage-cpp/)

  Die Azure Storage-Clientbibliothek für C++ stellt eine umfassende API zum Arbeiten mit Azure Storage bereit, die u. a. die folgenden Möglichkeiten bietet:

  - Erstellen, Lesen, Löschen und Auflisten von Blob-Containern, Tabellen und Warteschlangen
  - Erstellen, Lesen, Löschen, Auflisten und Kopieren von Blobs sowie Lesen und Schreiben von Blob-Bereichen
  - Einfügen, Löschen, Zusammenführen und Abfragen von Entitäten in einer Azure-Tabelle
  - Einreihen von Nachrichten in eine und Entfernen von Nachrichten aus einer Azure-Warteschlange
  - Verzögertes Auflisten von Containern, Blobs, Tabellen und Warteschlangen und verzögertes Abfragen von Entitäten

- Mit den ANSI C99 [Azure IoT Hub SDKs](/azure/iot-hub/iot-hub-devguide-sdks) für das Internet der Dinge wird für IoT-Anwendungen die Ausführung auf dem Gerät oder auf dem Back-End ermöglicht.

- [OneDrive and SharePoint in Microsoft Graph](https://dev.onedrive.com/README.htm) (OneDrive und SharePoint in Microsoft Graph)

  Die onedrive-API bietet eine Reihe von http-Diensten, mit denen Sie Ihre Anwendung mit Dateien und Ordnern in Microsoft 365 und SharePoint Server 2016 verbinden können.

## <a name="windows-and-cross-platform-networking-apis"></a>Windows- und plattformübergreifende Netzwerk-APIs

- [C++ REST SDK (Codename „Casablanca“)](https://github.com/Microsoft/cpprestsdk)

  Stellt eine moderne, plattformübergreifende, asynchrone API zum Interagieren mit REST-Diensten bereit.

  - Ausführen von REST-Aufrufen an einen beliebigen HTTP-Server mit integrierter Unterstützung für JSON-Dokumentanalysierung und -serialisierung
  - Unterstützt OAuth-1 und 2, einschließlich eines lokalen Umleitungslisteners
  - Herstellen von WebSockets-Verbindungen mit Remotediensten
  - Eine vollständig asynchrone Aufgaben-API auf Basis von PPL, einschließlich eines integrierten Threadpools

  Unterstützt Windows Desktop (7+), Windows Server (2012+), Universelle Windows-Plattform, Linux, OSX, Android und iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Eine Windows-Runtime-HTTP-Clientklasse, die in der .NET Framework-Klasse des gleichen Namens im System.Web-Namespace modelliert ist. `HttpClient` unterstützt vollständig den asynchronen Upload und Download über HTTP und Pipelinefilter, die das Einfügen von benutzerdefinierten HTTP-Handlern in die Pipeline ermöglichen. Das Windows SDK umfasst Beispielfilter für gemessene Netzwerke, OAuth-Authentifizierung und mehr. Für Apps, die nur für die Universelle Windows-Plattform vorgesehen sind, empfiehlt es sich, die `Windows::Web:HttpClient`-Klasse zu verwenden.

- [IXMLHTTPRequest2-Schnittstelle](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Stellt eine systemeigene COM-Schnittstelle bereit, die Sie in Windows-Runtime-Apps oder Windows-Desktop-Apps verwenden können, um über HTTP eine Verbindung mit dem Internet herzustellen und GET-, PUT- und andere HTTP-Befehle auszugeben. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Herstellen einer Verbindung mithilfe von Aufgaben und XML-HTTP-Anforderungen](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/win32/WinInet/portal)

  Eine Windows-API, die Sie in Windows-Desktop-Apps verwenden können, um eine Verbindung mit dem Internet herzustellen.

## <a name="see-also"></a>Weitere Informationen

[C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Microsoft Azure C und C++ Developer Center](https://azure.microsoft.com/develop/cpp/) <br/>
[Netzwerke und Webdienste (UWP)](/windows/uwp/networking/)
