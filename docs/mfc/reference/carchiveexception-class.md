---
title: CArchiveException-Klasse
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
ms.openlocfilehash: ad2a9d8c5b4466a04b5a88fcce7679911bf1b81a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377012"
---
# <a name="carchiveexception-class"></a>CArchiveException-Klasse

Stellt eine Serialisierungsausnahmebedingung dar

## <a name="syntax"></a>Syntax

```
class CArchiveException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|Erstellt ein `CArchiveException`-Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArchiveException::m_cause](#m_cause)|Gibt die Ausnahmeursache an.|
|[CArchiveException::m_strFileName](#m_strfilename)|Gibt den Namen der Datei für diese Ausnahmebedingung an.|

## <a name="remarks"></a>Bemerkungen

Die `CArchiveException` Klasse enthält einen öffentlichen Datenmember, der die Ursache der Ausnahme angibt.

`CArchiveException`Objekte werden innerhalb von [CArchive-Memberfunktionen](../../mfc/reference/carchive-class.md) erstellt und verworfen. Sie können im Rahmen eines **CATCH-Ausdrucks** auf diese Objekte zugreifen. Der Ursachencode ist unabhängig vom Betriebssystem. Weitere Informationen zur Ausnahmeverarbeitung finden Sie unter [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>CArchiveException::CArchiveException

Erstellt ein `CArchiveException` Objekt und speichert den Wert der *Ursache* im Objekt.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parameter

*Ursache*<br/>
Eine aufgezählte Typvariable, die den Grund für die Ausnahme angibt. Eine Liste der Enumeratoren [m_cause](#m_cause) finden Sie im m_cause-Datenmember.

*lpszArchiveName*<br/>
Zeigt auf eine Zeichenfolge, `CArchive` die den Namen des Objekts enthält, das die Ausnahme verursacht.

### <a name="remarks"></a>Bemerkungen

Sie können `CArchiveException` ein Objekt auf dem Heap erstellen und es selbst ableben oder die globale Funktion [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) für Sie behandeln lassen.

Verwenden Sie diesen Konstruktor nicht direkt. Rufen Sie stattdessen `AfxThrowArchiveException`die globale Funktion auf.

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>CArchiveException::m_cause

Gibt die Ursache der Ausnahme an.

```
int m_cause;
```

### <a name="remarks"></a>Bemerkungen

Dieser Datenmember ist eine öffentliche Variable vom Typ **int**. Seine Werte werden `CArchiveException` durch einen aufgezählten Typ definiert. Die Enumeratoren und ihre Bedeutungen lauten wie folgt:

- `CArchiveException::none`Es ist kein Fehler aufgetreten.

- `CArchiveException::genericException`Nicht angegebener Fehler.

- `CArchiveException::readOnly`Es wurde versucht, in ein zum Laden geöffnetes Archiv zu schreiben.

- `CArchiveException::endOfFile`Beendet das Ende der Datei beim Lesen eines Objekts.

- `CArchiveException::writeOnly`Es wurde versucht, aus einem archivierenden Archiv zu lesen.

- `CArchiveException::badIndex`Ungültiges Dateiformat.

- `CArchiveException::badClass`Es wurde versucht, ein Objekt in ein Objekt des falschen Typs zu lesen.

- `CArchiveException::badSchema`Es wurde versucht, ein Objekt mit einer anderen Version der Klasse zu lesen.

    > [!NOTE]
    >  Diese `CArchiveException`-Ursachenenumeratoren unterscheiden sich von den `CFileException`-Ursachenenumeratoren.

    > [!NOTE]
    > `CArchiveException::generic` ist veraltet. Verwenden Sie stattdessen `genericException`. Wenn **generic** in einer Anwendung verwendet und mit /clr erstellt wird, gibt es Syntaxfehler, die nicht leicht zu entschlüsseln sind.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>CArchiveException::m_strFileName

Gibt den Namen der Datei für diese Ausnahmebedingung an.

```
CString m_strFileName;
```

## <a name="see-also"></a>Siehe auch

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CArchive-Klasse](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Ausnahmeverarbeitung](../../mfc/reference/exception-processing.md)
