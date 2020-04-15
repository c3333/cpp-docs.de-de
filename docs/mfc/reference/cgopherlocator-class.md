---
title: CGopherLocator-Klasse
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: d23ef3dad68c62e74ec64454953ca372b8c31114
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373668"
---
# <a name="cgopherlocator-class"></a>CGopherLocator-Klasse

Ruft einen Gopher-"Locator" von einem Gopher-Server ab, bestimmt den Typ des Locators und stellt den Locator [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)zur Verfügung.

> [!NOTE]
> Die `CGopherConnection`Klassen `CGopherFile` `CGopherFileFind`, `CGopherLocator` , und ihre Mitglieder wurden veraltet, weil sie nicht auf der Windows XP-Plattform funktionieren, aber sie werden weiterhin auf früheren Plattformen arbeiten.

## <a name="syntax"></a>Syntax

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Erstellt ein `CGopherLocator`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analysiert einen Gopher-Locator und bestimmt seine Attribute.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Greift direkt auf Zeichen `CGopherLocator` zu, die in einem Objekt als Zeichenfolge im C-Stil gespeichert sind.|

## <a name="remarks"></a>Bemerkungen

Eine Anwendung muss den Locator eines Gopher-Servers abrufen, bevor sie Informationen von diesem Server abrufen kann. Sobald der Locator über den Locator verfügt, muss er den Locator als undurchsichtiges Token behandeln.

Jeder Gopher-Locator verfügt über Attribute, die den Typ der gefundenen Datei oder des gefundenen Servers bestimmen. Eine Liste der Typen von Gopher-Locators finden Sie unter [GetLocatorType.](#getlocatortype)

Eine Anwendung verwendet normalerweise den Locator für Aufrufe von [CGopherFileFind::FindFile,](../../mfc/reference/cgopherfilefind-class.md#findfile) um eine bestimmte Information abzurufen.

Weitere Informationen zur `CGopherLocator` Funktionsweise mit den anderen MFC-Internetklassen finden Sie im Artikel [Internetprogrammierung mit WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopherLocator::CGopherLocator

Diese Memberfunktion wird aufgerufen, um ein `CGopherLocator` Objekt zu erstellen.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Parameter

*ref*<br/>
Ein Verweis auf `CGopherLocator` ein konstantes Objekt.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CGopherLocator` nie direkt ein Objekt. Rufen Sie stattdessen [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) auf, um `CGopherLocator` einen Zeiger auf das Objekt zu erstellen und zurückzugeben.

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopherLocator::GetLocatorType

Rufen Sie diese Memberfunktion auf, um den Locator-Typ abzurufen.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Parameter

*dwRef*<br/>
Ein Verweis auf ein DWORD, das den Locator-Typ empfängt. Siehe **Hinweise** für eine Tabelle mit Locator-Typen.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null). Wenn der Aufruf fehlschlägt, kann die Win32-Funktion [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aufgerufen werden, um die Ursache des Fehlers zu ermitteln.

### <a name="remarks"></a>Bemerkungen

Die möglichen Typen sind wie folgt:

|Wert|Bedeutung|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Eine ASCII-Textdatei.|
|GOPHER_TYPE_DIRECTORY|Ein Verzeichnis mit zusätzlichen Gopher-Elementen.|
|GOPHER_TYPE_CSO|Ein CSO-Telefonbuchserver.|
|GOPHER_TYPE_ERROR|Gibt eine Fehlerbedingung an.|
|GOPHER_TYPE_MAC_BINHEX|Eine Macintosh-Datei im BINHEX-Format.|
|GOPHER_TYPE_DOS_ARCHIVE|Eine DOS-Archivdatei.|
|GOPHER_TYPE_UNIX_UUENCODED|Eine UUENCODED-Datei.|
|GOPHER_TYPE_INDEX_SERVER|Ein Indexserver.|
|GOPHER_TYPE_TELNET|Ein Telnet-Server.|
|GOPHER_TYPE_BINARY|Eine Binärdatei.|
|GOPHER_TYPE_REDUNDANT|Ein duplizierter Server. Die darin enthaltenen Informationen sind ein Duplikat des primären Servers. Der primäre Server ist der letzte Verzeichniseintrag, der keinen GOPHER_TYPE_REDUNDANT Typ s.|
|GOPHER_TYPE_TN3270|Ein TN3270-Server.|
|GOPHER_TYPE_GIF|Eine GIF-Grafikdatei.|
|GOPHER_TYPE_IMAGE|Eine Bilddatei.|
|GOPHER_TYPE_BITMAP|Eine Bitmapdatei.|
|GOPHER_TYPE_MOVIE|Eine Filmdatei.|
|GOPHER_TYPE_SOUND|Eine Sounddatei.|
|GOPHER_TYPE_HTML|Ein HTML-Dokument.|
|GOPHER_TYPE_PDF|Eine PDF-Datei.|
|GOPHER_TYPE_CALENDAR|Eine Kalenderdatei.|
|GOPHER_TYPE_INLINE|Eine Inlinedatei.|
|GOPHER_TYPE_UNKNOWN|Der Elementtyp ist unbekannt.|
|GOPHER_TYPE_ASK|Ein Ask+-Element.|
|GOPHER_TYPE_GOPHER_PLUS|Ein Gopher+-Element.|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopherLocator::operator LPCTSTR

Dieser nützliche Umwandlungsoperator stellt eine effiziente Methode für den `CGopherLocator` Zugriff auf die null-terminierte C-Zeichenfolge bereit, die in einem Objekt enthalten ist.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeichenzeiger auf die Daten der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Es werden keine Zeichen kopiert. es wird nur ein Zeiger zurückgegeben.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind-Klasse](../../mfc/reference/cgopherfilefind-class.md)
