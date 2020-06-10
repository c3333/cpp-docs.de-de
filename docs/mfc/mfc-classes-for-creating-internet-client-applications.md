---
title: MFC-Klassen für das Erstellen von Internetclientanwendungen
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, WinInet classes
- WinInet classes [MFC], classes
- classes [MFC], MFC
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
ms.openlocfilehash: d65a2e8b373f26fe928e4c3e7c0193aec4edf2d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618035"
---
# <a name="mfc-classes-for-creating-internet-client-applications"></a>MFC-Klassen für das Erstellen von Internetclientanwendungen

MFC stellt die folgenden Klassen und globalen Funktionen zum Schreiben von Internet Client Anwendungen bereit. Einzug gibt an, dass eine Klasse von der übergeordneten Klasse abgeleitet ist. `CGopherFile`und `CHttpFile` `CInternetFile` können z. b. von abgeleitet werden. Diese Klassen und globalen Funktionen werden in AFXINET deklariert. H, außer `CFileFind` , das in AFX deklariert wird. Micha.

## <a name="classes"></a>Klassen

- [CInternetSession](reference/cinternetsession-class.md)

- [CInternetConnection](reference/cinternetconnection-class.md)

  - [CFtpConnection](reference/cftpconnection-class.md)

  - [CGopherConnection](reference/cgopherconnection-class.md)

  - [CHttpConnection](reference/chttpconnection-class.md)

- [CInternetFile](reference/cinternetfile-class.md)

  - [CGopherFile](reference/cgopherfile-class.md)

  - [CHttpFile](reference/chttpfile-class.md)

- [CFileFind](reference/cfilefind-class.md)

  - [CFtpFileFind](reference/cftpfilefind-class.md)

  - [CGopherFileFind](reference/cgopherfilefind-class.md)

- [CGopherLocator](reference/cgopherlocator-class.md)

- [CInternetException](reference/cinternetexception-class.md)

## <a name="global-functions"></a>Globale Funktionen

- [AfxParseURL](reference/internet-url-parsing-globals.md#afxparseurl)

- [AfxGetInternetHandleType](reference/internet-url-parsing-globals.md#afxgetinternethandletype)

- [AfxThrowInternetException](reference/internet-url-parsing-globals.md#afxthrowinternetexception)

## <a name="see-also"></a>Siehe auch

[Win32-Interneterweiterungen (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Voraussetzungen für Internetclientklassen](prerequisites-for-internet-client-classes.md)<br/>
[Schreiben einer Internetclientanwendung mithilfe von MFC-WinInet-Klassen](writing-an-internet-client-application-using-mfc-wininet-classes.md)
