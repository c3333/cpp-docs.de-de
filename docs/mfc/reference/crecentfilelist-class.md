---
title: CRecentFileList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: a2102c6a39c14c548828e57ad1c49de6a5bc03dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370898"
---
# <a name="crecentfilelist-class"></a>CRecentFileList-Klasse

Unterstützt die Verwendung der zuletzt verwendeten Dateiliste (MRU).

## <a name="syntax"></a>Syntax

```
class CRecentFileList
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|Erstellt ein `CRecentFileList`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecentFileList::Hinzufügen](#add)|Fügt der MRU-Dateiliste eine Datei hinzu.|
|[CRecentFileList::GetDisplayName](#getdisplayname)|Stellt einen Anzeigenamen für die Menüanzeige eines MRU-Dateinamens bereit.|
|[CRecentFileList::GetSize](#getsize)|Ruft die Anzahl der Dateien in der MRU-Dateiliste ab.|
|[CRecentFileList::ReadList](#readlist)|Liest die MRU-Dateiliste aus der Registrierung oder . INI-Datei.|
|[CRecentFileList::Entfernen](#remove)|Entfernt eine Datei aus der MRU-Dateiliste.|
|[CRecentFileList::UpdateMenu](#updatemenu)|Aktualisiert die Menüanzeige der MRU-Dateiliste.|
|[CRecentFileList::WriteList](#writelist)|Schreibt die MRU-Dateiliste aus der Registrierung oder . INI-Datei.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRecentFileList::operator \[\]](#operator_at)|Gibt `CString` ein Objekt an einer bestimmten Position zurück.|

## <a name="remarks"></a>Bemerkungen

Dateien können der MRU-Dateiliste hinzugefügt oder aus ihr gelöscht werden, die Dateiliste kann aus der Registrierung oder einer gelesen oder in die Registrierung geschrieben werden. INI-Datei, und das Menü mit der MRU-Dateiliste kann aktualisiert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CRecentFileList`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxadv.h

## <a name="crecentfilelistadd"></a><a name="add"></a>CRecentFileList::Hinzufügen

Fügt der zuletzt verwendeten Dateiliste (MRU) eine Datei hinzu.

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>Parameter

*lpszPathName*<br/>
Gibt den Pfadnamen an, der der Liste hinzugefügt werden soll.

*lpszAppID*<br/>
Gibt die Anwendungsbenutzermodell-ID für die Anwendung an.

*pItem*<br/>
Gibt einen Zeiger auf Shell-Element an, der der Liste hinzugefügt werden soll.

*Plink*<br/>
Gibt einen Zeiger auf Shell Link an, der der Liste hinzugefügt werden soll.

*Pidl*<br/>
Gibt die IDLIST für das Shellelement an, das dem Ordner "letzte Dokumente" hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Der Dateiname wird oben in der MRU-Liste hinzugefügt. Wenn der Dateiname bereits in der MRU-Liste vorhanden ist, wird er nach oben verschoben.

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>CRecentFileList::CRecentFileList

Erstellt ein `CRecentFileList`-Objekt.

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>Parameter

*nStart*<br/>
Offset für die Nummerierung in der Menüanzeige der MRU-Dateiliste (zuletzt verwendet).

*lpszSection*<br/>
Verweist auf den Namen des Abschnitts der Registrierung oder der . INI-Datei, in der die MRU-Dateiliste gelesen und/oder geschrieben wird.

*lpszEntryFormat*<br/>
Verweist auf eine Formatzeichenfolge, die für die Namen der in der Registrierung gespeicherten Einträge oder der . INI-Datei.

*nGröße*<br/>
Maximale Anzahl von Dateien in der MRU-Dateiliste.

*nMaxDispLen*<br/>
Maximale Länge in Zeichen, verfügbar für die Menüanzeige eines Dateinamens in der MRU-Dateiliste.

### <a name="remarks"></a>Bemerkungen

Die Formatzeichenfolge, auf die *lpszEntryFormat* zeigt, sollte "%d" enthalten, die zum Ersetzen des Indexjedes MRU-Elements verwendet wird. Wenn die Formatzeichenfolge z. B. `"file%d"` lautet, werden die Einträge den Namen , `file0` `file1`, usw. genannt.

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>CRecentFileList::GetDisplayName

Ruft einen Anzeigenamen für eine Datei in der MRU-Dateiliste ab, der in der Menüanzeige der MRU-Liste verwendet werden kann.

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>Parameter

*strName*<br/>
Vollständiger Pfad der Datei, deren Name in der Menüliste der MRU-Dateien angezeigt werden soll.

*nIndex*<br/>
Nullbasierter Index der Datei in der MRU-Dateiliste.

*lpszCurDir*<br/>
Zeichenfolge, die das aktuelle Verzeichnis enthält.

*nCurDir*<br/>
Länge der aktuellen Verzeichniszeichenfolge.

*bAtLeastName*<br/>
Wenn ungleich Null, gibt an, dass der Basisname der Datei zurückgegeben werden soll, auch wenn er `CRecentFileList` die maximale Anzeigelänge überschreitet (als *nMaxDispLen-Parameter* an den Konstruktor übergeben).

### <a name="return-value"></a>Rückgabewert

**FALSE,** wenn in der zuletzt verwendeten Dateiliste (MRU) kein Dateiname am angegebenen Index vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Wenn sich die Datei im aktuellen Verzeichnis befindet, verlässt die Funktion das Verzeichnis von der Anzeige. Wenn der Dateiname zu lang ist, werden das Verzeichnis und die Erweiterung entfernt. Wenn der Dateiname immer noch zu lang ist, wird der Anzeigename auf eine leere Zeichenfolge festgelegt, es sei *denn, bAtLeastName* ist ungleich Null.

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a>CRecentFileList::GetSize

Ruft die Anzahl der Dateien in der MRU-Dateiliste ab.

```
int GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Dateien in der aktuell zuletzt verwendeten Dateiliste (MRU).

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a>CRecentFileList::operator [ ]

Der operator überladene Subskripte (`[]`) gibt eine einzelne `CString` Datei zurück, die vom nullbasierten Index in *nIndex*angegeben wurde.

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Nullbasierter Index `CString` von a `CString`in einer Reihe von s.

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a>CRecentFileList::ReadList

Liest die zuletzt verwendete Dateiliste (MRU) aus der Registrierung oder der . INI-Datei.

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a>CRecentFileList::Entfernen

Entfernt eine Datei aus der MRU-Dateiliste.

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Nullbasierter Index der Datei, die aus der zuletzt verwendeten (MRU)-Dateiliste entfernt werden soll.

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a>CRecentFileList::UpdateMenu

Aktualisiert die Menüanzeige der MRU-Dateiliste.

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>Parameter

*pCmdUI*<br/>
Ein Zeiger auf das [CCmdUI-Objekt](../../mfc/reference/ccmdui-class.md) für das zuletzt verwendete Dateilistenmenü (MRU).

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a>CRecentFileList::WriteList

Schreibt die zuletzt verwendete Dateiliste (MRU) in die Registrierung oder die . INI-Datei.

```
virtual void WriteList();
```

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
