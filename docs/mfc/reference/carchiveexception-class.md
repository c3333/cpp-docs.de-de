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
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855302"
---
# <a name="carchiveexception-class"></a>Carchiveexception-Klasse

Stellt eine serialisierungsausnahmebedingung dar.

## <a name="syntax"></a>Syntax

```
class CArchiveException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Carchiveexception:: carchiveexception](#carchiveexception)|Erstellt ein `CArchiveException`-Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[Carchiveexception:: m_cause](#m_cause)|Gibt die Ausnahme Ursache an.|
|[Carchiveexception:: m_strFileName](#m_strfilename)|Gibt den Namen der Datei für diese Ausnahme Bedingung an.|

## <a name="remarks"></a>Hinweise

Die `CArchiveException`-Klasse enthält einen öffentlichen Datenmember, der die Ursache der Ausnahme angibt.

`CArchiveException` Objekte werden innerhalb von [CArchive](../../mfc/reference/carchive-class.md) -Element Funktionen erstellt und ausgelöst. Sie können auf diese Objekte innerhalb des Gültigkeits Bereichs eines **catch** -Ausdrucks zugreifen. Der Ursachen Code ist unabhängig vom Betriebssystem. Weitere Informationen zur Ausnahme Verarbeitung finden Sie unter [Ausnahmebehandlung (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="carchiveexception"></a>Carchiveexception:: carchiveexception

Erstellt ein `CArchiveException`-Objekt, wobei der Wert der *Ursache* im-Objekt gespeichert wird.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parameter

*cause*<br/>
Eine enumerierte Typvariable, die den Grund für die Ausnahme angibt. Eine Liste der Enumeratoren finden Sie unter [m_cause](#m_cause) -Datenmember.

*lpszarchivename*<br/>
Verweist auf eine Zeichenfolge, die den Namen des `CArchive` Objekts enthält, das die Ausnahme verursacht hat.

### <a name="remarks"></a>Hinweise

Sie können ein `CArchiveException` Objekt auf dem Heap erstellen und es selbst auslösen oder die globale Funktion [afxthrowarchiveexception](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) für Sie behandeln lassen.

Verwenden Sie diesen Konstruktor nicht direkt. nennen Sie stattdessen die globale Funktion `AfxThrowArchiveException`.

##  <a name="m_cause"></a>Carchiveexception:: m_cause

Gibt die Ursache der Ausnahme an.

```
int m_cause;
```

### <a name="remarks"></a>Hinweise

Dieser Datenmember ist eine öffentliche Variable vom Typ **int**. Die Werte werden durch einen `CArchiveException` enumerierten Typ definiert. Die Enumeratoren und ihre Bedeutungen lauten wie folgt:

- `CArchiveException::none` ist kein Fehler aufgetreten.

- nicht spezifizierter Fehler `CArchiveException::genericException`.

- `CArchiveException::readOnly` versuchte, in ein Archiv zu schreiben, das zum Laden geöffnet wurde.

- `CArchiveException::endOfFile` das Dateiende beim Lesen eines Objekts erreicht hat.

- `CArchiveException::writeOnly` hat versucht, aus einem Archiv zu lesen, das zum Speichern geöffnet wurde.

- `CArchiveException::badIndex` Ungültiges Dateiformat.

- `CArchiveException::badClass` hat versucht, ein Objekt in ein Objekt des falschen Typs zu lesen.

- `CArchiveException::badSchema` hat versucht, ein Objekt mit einer anderen Version der Klasse zu lesen.

    > [!NOTE]
    >  Diese `CArchiveException`-Ursachenenumeratoren unterscheiden sich von den `CFileException`-Ursachenenumeratoren.

    > [!NOTE]
    > `CArchiveException::generic` ist veraltet. Verwenden Sie stattdessen `genericException`. Wenn **generisch** in einer Anwendung verwendet und mit/CLR erstellt wird, sind Syntax Fehler vorhanden, die nicht leicht entschlüsselt werden können.

##  <a name="m_strfilename"></a>Carchiveexception:: m_strFileName

Gibt den Namen der Datei für diese Ausnahme Bedingung an.

```
CString m_strFileName;
```

## <a name="see-also"></a>Siehe auch

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CArchive-Klasse](../../mfc/reference/carchive-class.md)<br/>
[Afxthrowarchiveexception](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[Ausnahmeverarbeitung](../../mfc/reference/exception-processing.md)
