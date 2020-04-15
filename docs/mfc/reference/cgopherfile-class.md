---
title: CGopherFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: e157a4509fe30b814a1834690a675906ac82afe7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373697"
---
# <a name="cgopherfile-class"></a>CGopherFile-Klasse

Stellt die Funktionalität bereit, um Dateien auf einem Gopherserver zu suchen und zu lesen.

> [!NOTE]
> Die `CGopherConnection`Klassen `CGopherFile` `CGopherFileFind`, `CGopherLocator` , und ihre Mitglieder wurden veraltet, weil sie nicht auf der Windows XP-Plattform funktionieren, aber sie werden weiterhin auf früheren Plattformen arbeiten.

## <a name="syntax"></a>Syntax

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherFile::CGopherDatei](#cgopherfile)|Erstellt ein `CGopherFile`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Der gopher-Dienst erlaubt es Benutzern nicht, Daten in eine Gopher-Datei zu schreiben, da dieser Dienst hauptsächlich als menügesteuerte Schnittstelle zum Suchen von Informationen fungiert. Die `CGopherFile` `Write`Memberfunktionen `WriteString`, `Flush` und sind `CGopherFile`nicht für implementiert. Wenn Sie diese `CGopherFile` Funktionen für ein Objekt aufrufen, wird eine [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)zurückgegeben.

Weitere Informationen zur `CGopherFile` Funktionsweise mit den anderen MFC-Internetklassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopherFile::CGopherDatei

Diese Memberfunktion wird aufgerufen, um ein `CGopherFile` Objekt zu erstellen.

```
CGopherFile(
    HINTERNET hFile,
    CGopherLocator& refLocator,
    CGopherConnection* pConnection);

CGopherFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrLocator,
    DWORD dwLocLen,
    DWORD_PTR dwContext);
```

### <a name="parameters"></a>Parameter

*hDatei*<br/>
Ein Handle für eine HINTERNET-Datei.

*refLocator*<br/>
Ein Verweis auf ein [CGopherLocator-Objekt.](../../mfc/reference/cgopherlocator-class.md)

*pConnection*<br/>
Ein Zeiger auf ein [CGopherConnection-Objekt.](../../mfc/reference/cgopherconnection-class.md)

*hSession*<br/>
Ein Handle für die aktuelle Internetsitzung.

*pstrLocator*<br/>
Ein Zeiger auf eine Zeichenfolge, die zum Suchen des Gopher-Servers verwendet wird. Weitere Informationen zu Gopher-Locators finden Sie unter [Gopher-Sitzungen.](cgopherlocator-class.md)

*dwLocLen*<br/>
Ein DWORD, das die Anzahl der Bytes in *pstrLocator*enthält.

*dwContext*<br/>
Ein Zeiger auf den Kontextbezeichner der zu öffnenden Datei.

### <a name="remarks"></a>Bemerkungen

Sie benötigen `CGopherFile` ein Objekt, um während einer Gopher-Internetsitzung aus einer Datei zu lesen.

Sie erstellen `CGopherFile` nie direkt ein Objekt. Rufen Sie stattdessen [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) auf, um eine Datei auf einem Gopher-Server zu öffnen.

## <a name="see-also"></a>Siehe auch

[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile-Klasse](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator-Klasse](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind-Klasse](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection-Klasse](../../mfc/reference/cgopherconnection-class.md)
