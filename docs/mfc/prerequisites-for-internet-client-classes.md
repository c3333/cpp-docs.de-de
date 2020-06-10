---
title: Voraussetzungen für Internetclientklassen
ms.date: 11/04/2016
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
ms.openlocfilehash: aaf5756df69728e8ae89fb278bc0671bfc6840b7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619831"
---
# <a name="prerequisites-for-internet-client-classes"></a>Voraussetzungen für Internetclientklassen

Einige Aktionen, die von einem Internet Client durchgeführt werden (z. b. das Lesen einer Datei), haben erforderliche Aktionen (in diesem Fall das Einrichten einer Internet Verbindung). In den folgenden Tabellen sind die Voraussetzungen für einige Client Aktionen aufgeführt.

### <a name="general-internet-url-ftp-gopher-or-http"></a>Allgemeine Internet-URL (FTP, Gopher oder http)

|Aktion|Voraussetzungen|
|------------|------------------|
|Stellen Sie eine Verbindung her.|Erstellen Sie eine [cinternetzession](reference/cinternetsession-class.md) , um die Basis einer Internet Client Anwendung einzurichten.|
|Öffnen Sie eine URL.|Stellen Sie eine Verbindung her. [Cinternetzession:: OpenURL](reference/cinternetsession-class.md#openurl)aufzurufen. Die- `OpenURL` Funktion gibt ein Schreib geschütztes Ressourcen Objekt zurück.|
|Lesen von URL-Daten.|Öffnen Sie die URL. [CInternetFile:: Read](reference/cinternetfile-class.md#read)abrufen.|
|Legen Sie eine Internet Option fest.|Stellen Sie eine Verbindung her. [Cinternetzession:: SetOption](reference/cinternetsession-class.md#setoption)aufzurufen.|
|Legen Sie eine Funktion fest, die mit Statusinformationen aufgerufen werden soll.|Stellen Sie eine Verbindung her. Rufen Sie [cinternetzession:: enablestatus Callback](reference/cinternetsession-class.md#enablestatuscallback)auf. Überschreiben Sie [cinternetzession:: OnStatus Callback](reference/cinternetsession-class.md#onstatuscallback) , um Aufrufe zu verarbeiten.|

### <a name="ftp"></a>FTP

|Aktion|Voraussetzungen|
|------------|------------------|
|Stellen Sie eine FTP-Verbindung her.|Erstellen Sie eine [cinternetzession](reference/cinternetsession-class.md) als Grundlage für diese Internet Client Anwendung. Rufen Sie [cinternetzession:: GetFtpConnection](reference/cinternetsession-class.md#getftpconnection) auf, um ein [CFtpConnection](reference/cftpconnection-class.md) -Objekt zu erstellen.|
|Suchen Sie die erste Ressource.|Stellen Sie eine FTP-Verbindung her. Erstellen Sie ein [CFtpFileFind](reference/cftpfilefind-class.md) -Objekt. [CFtpFileFind:: FindFile](reference/cftpfilefind-class.md#findfile)aufzurufen.|
|Listet alle verfügbaren Ressourcen auf.|Suchen Sie die erste Datei. Ruft " [CFtpFileFind:: FindNextFile](reference/cftpfilefind-class.md#findnextfile) " auf, bis "false" zurückgegeben wird.|
|Öffnen Sie eine FTP-Datei.|Stellen Sie eine FTP-Verbindung her. Rufen Sie [CFtpConnection:: OpenFile](reference/cftpconnection-class.md#openfile) auf, um ein [CInternetFile](reference/cinternetfile-class.md) -Objekt zu erstellen und zu öffnen.|
|Eine FTP-Datei lesen.|Öffnen Sie eine FTP-Datei mit Lesezugriff. [CInternetFile:: Read](reference/cinternetfile-class.md#read)abrufen.|
|Schreiben in eine FTP-Datei.|Öffnen Sie eine FTP-Datei mit Schreibzugriff. [CInternetFile:: Write](reference/cinternetfile-class.md#write)aufruft.|
|Ändern Sie das Verzeichnis des Clients auf dem Server.|Stellen Sie eine FTP-Verbindung her. Aufrufen von [CFtpConnection:: SetCurrentDirectory](reference/cftpconnection-class.md#setcurrentdirectory).|
|Rufen Sie das aktuelle Verzeichnis des Clients auf dem Server ab.|Stellen Sie eine FTP-Verbindung her. Aufrufen von [CFtpConnection:: GetCurrentDirectory](reference/cftpconnection-class.md#getcurrentdirectory).|

### <a name="http"></a>HTTP

|Aktion|Voraussetzungen|
|------------|------------------|
|Richten Sie eine HTTP-Verbindung ein.|Erstellen Sie eine [cinternetzession](reference/cinternetsession-class.md) als Grundlage für diese Internet Client Anwendung. Rufen Sie [cinternetzession:: GetHttpConnection](reference/cinternetsession-class.md#gethttpconnection) auf, um ein [CHttpConnection](reference/chttpconnection-class.md) -Objekt zu erstellen.|
|Öffnen Sie eine HTTP-Datei.|Richten Sie eine HTTP-Verbindung ein. Rufen Sie [CHttpConnection:: openrequest](reference/chttpconnection-class.md#openrequest) auf, um ein [CHttpFile](reference/chttpfile-class.md) -Objekt zu erstellen. Nennen Sie [CHttpFile:: adressquestheaders](reference/chttpfile-class.md#addrequestheaders). [CHttpFile:: SendRequest](reference/chttpfile-class.md#sendrequest)aufzurufen.|
|Liest eine HTTP-Datei.|Öffnen Sie eine HTTP-Datei. [CInternetFile:: Read](reference/cinternetfile-class.md#read)abrufen.|
|Informationen zu einer HTTP-Anforderung erhalten.|Richten Sie eine HTTP-Verbindung ein. Rufen Sie [CHttpConnection:: openrequest](reference/chttpconnection-class.md#openrequest) auf, um ein [CHttpFile](reference/chttpfile-class.md) -Objekt zu erstellen. [CHttpFile:: QueryInfo](reference/chttpfile-class.md#queryinfo)aufzurufen.|

### <a name="gopher"></a>Gopher

|Aktion|Voraussetzungen|
|------------|------------------|
|Stellen Sie eine Gopher-Verbindung her.|Erstellen Sie eine [cinternetzession](reference/cinternetsession-class.md) als Grundlage für diese Internet Client Anwendung. Rufen Sie [cinternetzession:: GetGopherConnection](reference/cinternetsession-class.md#getgopherconnection) auf, um eine [CGopherConnection](reference/cgopherconnection-class.md)zu erstellen.|
|Suchen Sie die erste Datei im aktuellen Verzeichnis.|Stellen Sie eine Gopher-Verbindung her. Erstellen Sie ein [CGopherFileFind](reference/cgopherfilefind-class.md) -Objekt. Rufen Sie [CGopherConnection:: kreatelocator](reference/cgopherconnection-class.md#createlocator) auf, um ein [CGopherLocator](reference/cgopherlocator-class.md) -Objekt zu erstellen. Übergeben Sie den Serverlocatorpunkt an [CGopherFileFind:: FindFile](reference/cgopherfilefind-class.md#findfile). [CGopherFileFind:: GetLocator](reference/cgopherfilefind-class.md#getlocator) aufrufen, um den Serverlocatorpunkt einer Datei zu erhalten, wenn Sie Sie später benötigen.|
|Listet alle verfügbaren Dateien auf.|Suchen Sie die erste Datei. [CGopherFileFind:: FindNextFile](reference/cgopherfilefind-class.md#findnextfile) wird aufgerufen, bis false zurückgegeben wird.|
|Öffnen Sie eine Gopher-Datei.|Stellen Sie eine Gopher-Verbindung her. Erstellen Sie einen Gopher-Serverlocatorpunkt mit [CGopherConnection:: kreatelocator](reference/cgopherconnection-class.md#createlocator) , oder suchen Sie einen Serverlocatorpunkt mit [CGopherFileFind:: GetLocator](reference/cgopherfilefind-class.md#getlocator). [CGopherConnection:: OpenFile](reference/cgopherconnection-class.md#openfile)wird aufgerufen.|
|Lesen Sie eine Gopher-Datei.|Öffnen Sie eine Gopher-Datei. Verwenden Sie [CGopherFile](reference/cgopherfile-class.md).|

## <a name="see-also"></a>Siehe auch

[Win32-Interneterweiterungen (WinInet)](win32-internet-extensions-wininet.md)<br/>
[MFC-Klassen für das Erstellen von Internetclientanwendungen](mfc-classes-for-creating-internet-client-applications.md)<br/>
[Schreiben einer Internetclientanwendung mithilfe von MFC-WinInet-Klassen](writing-an-internet-client-application-using-mfc-wininet-classes.md)
