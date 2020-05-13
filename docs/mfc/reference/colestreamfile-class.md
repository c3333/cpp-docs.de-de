---
title: COleStreamFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 202f8381361881ce3b8b62f81da5bfb81a1f952d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753760"
---
# <a name="colestreamfile-class"></a>COleStreamFile-Klasse

Stellt einen Datenstream (`IStream`) in einer Verbunddatei als Teil einer strukturierten Speicherung (OLE Structured Storage) dar.

## <a name="syntax"></a>Syntax

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|Erstellt ein `COleStreamFile`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleStreamFile::Anfügen](#attach)|Ordnet dem Objekt einen Stream zu.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Erstellt einen Stream aus dem globalen Speicher und ordnet ihn dem Objekt zu.|
|[COleStreamFile::CreateStream](#createstream)|Erstellt einen Stream und ordnet ihn dem Objekt zu.|
|[COleStreamFile::Detach](#detach)|Trennt den Stream vom Objekt.|
|[COleStreamFile::GetStream](#getstream)|Gibt den aktuellen Stream zurück.|
|[COleStreamFile::OpenStream](#openstream)|Öffnet sicher einen Stream und ordnet ihn dem Objekt zu.|

## <a name="remarks"></a>Bemerkungen

Ein `IStorage` Objekt muss vorhanden sein, bevor der Stream geöffnet oder erstellt werden kann, es sei denn, es handelt sich um einen Speicherstream.

`COleStreamFile`Objekte werden genau wie [CFile-Objekte](../../mfc/reference/cfile-class.md) bearbeitet.

Weitere Informationen zum Bearbeiten von Streams und Speicher finden Sie im Artikel [Container: Zusammengesetzte Dateien](../../mfc/containers-compound-files.md)..

Weitere Informationen finden Sie unter [IStream](/windows/win32/api/objidl/nn-objidl-istream) und [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxole.h

## <a name="colestreamfileattach"></a><a name="attach"></a>COleStreamFile::Anfügen

Ordnet dem `COleStreamFile` Objekt den mitgelieferten OLE-Stream zu.

```cpp
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parameter

*lpStream*<br/>
Zeigt auf den`IStream`OLE-Stream ( ), der dem Objekt zugeordnet werden soll. Lässt keine NULL-Werte zu.

### <a name="remarks"></a>Bemerkungen

Das Objekt darf nicht bereits einem OLE-Stream zugeordnet sein.

Weitere Informationen finden Sie unter [IStream](/windows/win32/api/objidl/nn-objidl-istream) im Windows SDK.

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStreamFile::COleStreamFile

Erstellt ein `COleStreamFile` -Objekt.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parameter

*lpStream*<br/>
Zeigen Sie mit dem Zeiger auf den OLE-Stream, der dem Objekt zugeordnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn *lpStream* NULL ist, ist das Objekt keinem OLE-Stream zugeordnet, andernfalls ist das Objekt dem bereitgestellten OLE-Stream zugeordnet.

Weitere Informationen finden Sie unter [IStream](/windows/win32/api/objidl/nn-objidl-istream) im Windows SDK.

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream

Erstellt sicher einen neuen Stream aus dem globalen, gemeinsam genutzten Speicher, bei dem ein Fehler eine normale, erwartete Bedingung ist.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*pError*<br/>
Verweist auf ein [CFileException-Objekt](../../mfc/reference/cfileexception-class.md) oder NULL, das den Abschlussstatus des Erstellungsvorgangs angibt. Geben Sie diesen Parameter an, wenn Sie mögliche Ausnahmen überwachen möchten, die durch den Versuch generiert werden, den Stream zu erstellen.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Stream erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Speicher wird vom OLE-Subsystem zugewiesen.

Weitere Informationen finden Sie unter [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) im Windows SDK.

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a>COleStreamFile::CreateStream

Erstellt sicher einen neuen Stream im bereitgestellten Speicherobjekt, bei dem ein Fehler eine normale, erwartete Bedingung ist.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*lpStorage*<br/>
Verweist auf das OLE-Speicherobjekt, das den zu erstellenden Stream enthält. Lässt keine NULL-Werte zu.

*lpszStreamName*<br/>
Name des zu erstellenden Streams. Lässt keine NULL-Werte zu.

*nOpenFlags*<br/>
Zugriffsmodus, der beim Öffnen des Streams verwendet werden soll. Exklusive Lese-/Schreib- und Erstellungsmodi werden standardmäßig verwendet. Eine vollständige Liste der verfügbaren Modi finden Sie unter [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Verweist auf ein [CFileException-Objekt](../../mfc/reference/cfileexception-class.md) oder NULL. Geben Sie diesen Parameter an, wenn Sie mögliche Ausnahmen überwachen möchten, die durch den Versuch generiert werden, den Stream zu erstellen.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Stream erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Dateiausnahme wird ausgelöst, wenn das Öffnen fehlschlägt und *pError* nicht NULL ist.

Weitere Informationen finden Sie unter [IStorage::CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) im Windows SDK.

## <a name="colestreamfiledetach"></a><a name="detach"></a>COleStreamFile::Detach

Trennt den Stream vom Objekt, ohne den Stream zu schließen.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den`IStream`Stream ( ), der dem Objekt zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Der Stream muss auf andere Weise geschlossen werden, bevor das Programm beendet wird.

Weitere Informationen finden Sie unter [IStream](/windows/win32/api/objidl/nn-objidl-istream) im Windows SDK.

## <a name="colestreamfilegetstream"></a><a name="getstream"></a>COleStreamFile::GetStream

Rufen Sie diese Funktion auf, um einen Zeiger auf den aktuellen Stream zurückzugeben.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die aktuelle Streamschnittstelle ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

## <a name="colestreamfileopenstream"></a><a name="openstream"></a>COleStreamFile::OpenStream

Öffnet einen vorhandenen Stream.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*lpStorage*<br/>
Verweist auf das OLE-Speicherobjekt, das den zu öffnenden Stream enthält. Lässt keine NULL-Werte zu.

*lpszStreamName*<br/>
Name des zu öffnenden Streams. Lässt keine NULL-Werte zu.

*nOpenFlags*<br/>
Zugriffsmodus, der beim Öffnen des Streams verwendet werden soll. Exklusive und Lese-/Schreibmodi werden standardmäßig verwendet. Die vollständige Liste der verfügbaren Modi finden Sie unter [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Verweist auf ein [CFileException-Objekt](../../mfc/reference/cfileexception-class.md) oder NULL. Geben Sie diesen Parameter an, wenn Sie mögliche Ausnahmen überwachen möchten, die durch den Versuch generiert werden, den Stream zu öffnen.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Stream erfolgreich geöffnet wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Eine Dateiausnahme wird ausgelöst, wenn das Öffnen fehlschlägt und *pError* nicht NULL ist.

Weitere Informationen finden Sie unter [IStorage::OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) im Windows SDK.

## <a name="see-also"></a>Weitere Informationen

[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
