---
title: Carchiveexception-Klasse
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 68f64cfd7dc96da04fcc0945a6b996eab4101487
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231883"
---
# <a name="carchiveexception-class"></a>Carchiveexception-Klasse

Stellt eine serialisierungsausnahmebedingung dar.

## <a name="syntax"></a>Syntax

```
class CArchiveException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[Carchiveexception:: carchiveexception](#carchiveexception)|Erstellt ein `CArchiveException`-Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Carchiveexception:: m_cause](#m_cause)|Gibt die Ausnahme Ursache an.|
|[Carchiveexception:: m_strFileName](#m_strfilename)|Gibt den Namen der Datei für diese Ausnahme Bedingung an.|

## <a name="remarks"></a>Bemerkungen

Die- `CArchiveException` Klasse enthält einen öffentlichen Datenmember, der die Ursache der Ausnahme angibt.

`CArchiveException`-Objekte werden innerhalb von [CArchive](../../mfc/reference/carchive-class.md) -Element Funktionen erstellt und ausgelöst. Sie können auf diese Objekte innerhalb des Gültigkeits Bereichs eines **catch** -Ausdrucks zugreifen. Der Ursachen Code ist unabhängig vom Betriebssystem. Weitere Informationen zur Ausnahme Verarbeitung finden Sie unter [Ausnahmebehandlung (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>Carchiveexception:: carchiveexception

Erstellt ein- `CArchiveException` Objekt und speichert den Wert der *Ursache* im-Objekt.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parameter

*zufügen*<br/>
Eine enumerierte Typvariable, die den Grund für die Ausnahme angibt. Eine Liste der Enumeratoren finden Sie unter [m_cause](#m_cause) -Datenmember.

*lpszarchivename*<br/>
Verweist auf eine Zeichenfolge, die den Namen des Objekts enthält, `CArchive` das die Ausnahme verursacht hat.

### <a name="remarks"></a>Bemerkungen

Sie können ein `CArchiveException` -Objekt auf dem Heap erstellen und es selbst auslösen oder die globale Funktion [afxthrowarchiveexception](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) für Sie behandeln lassen.

Verwenden Sie diesen Konstruktor nicht direkt. Verwenden Sie stattdessen die globale Funktion `AfxThrowArchiveException` .

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>Carchiveexception:: m_cause

Gibt die Ursache der Ausnahme an.

```
int m_cause;
```

### <a name="remarks"></a>Bemerkungen

Dieser Datenmember ist eine öffentliche Variable vom Typ **`int`** . Die Werte werden durch einen `CArchiveException` enumerierten Typ definiert. Die Enumeratoren und ihre Bedeutungen lauten wie folgt:

- `CArchiveException::none`Es ist kein Fehler aufgetreten.

- `CArchiveException::genericException`Nicht spezifizierter Fehler.

- `CArchiveException::readOnly`Es wurde versucht, in ein Archiv zu schreiben, das zum Laden geöffnet wurde

- `CArchiveException::endOfFile`Das Dateiende wurde beim Lesen eines Objekts erreicht.

- `CArchiveException::writeOnly`Es wurde versucht, ein Archiv zu lesen, das zum Speichern geöffnet wurde.

- `CArchiveException::badIndex`Ungültiges Dateiformat.

- `CArchiveException::badClass`Es wurde versucht, ein Objekt in ein Objekt des falschen Typs zu lesen.

- `CArchiveException::badSchema`Es wurde versucht, ein Objekt mit einer anderen Version der Klasse zu lesen.

    > [!NOTE]
    >  Diese `CArchiveException`-Ursachenenumeratoren unterscheiden sich von den `CFileException`-Ursachenenumeratoren.

    > [!NOTE]
    > `CArchiveException::generic` ist veraltet. Verwenden Sie stattdessen `genericException`. Wenn **generisch** in einer Anwendung verwendet und mit/CLR erstellt wird, sind Syntax Fehler vorhanden, die nicht leicht entschlüsselt werden können.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>Carchiveexception:: m_strFileName

Gibt den Namen der Datei für diese Ausnahme Bedingung an.

```
CString m_strFileName;
```

## <a name="see-also"></a>Weitere Informationen

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CArchive-Klasse](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Ausnahme Verarbeitung](../../mfc/reference/exception-processing.md)
