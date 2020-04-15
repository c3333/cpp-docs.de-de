---
title: CFileException-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: 2d1025ca33d5641982ba52f1ac539db85df3bfd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373894"
---
# <a name="cfileexception-class"></a>CFileException-Klasse

Stellt eine dateibezogene Ausnahmebedingung dar.

## <a name="syntax"></a>Syntax

```
class CFileException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Erstellt ein `CFileException`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Gibt Code zurück, der einer Laufzeitfehlernummer entspricht.|
|[CFileException::GetErrorMessage](#geterrormessage)|Ruft die Nachricht ab, die eine Ausnahme beschreibt.|
|[CFileException::OsErrorToException](#oserrortoexception)|Gibt einen Ursachencode zurück, der einem Betriebssystemfehlercode entspricht.|
|[CFileException::ThrowErrno](#throwerrno)|Löst eine Dateiausnahme basierend auf einer Laufzeitfehlernummer aus.|
|[CFileException::ThrowOsError](#throwoserror)|Löst eine Dateiausnahme basierend auf einer Betriebssystemfehlernummer aus.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Enthält portablen Code, der der Ausnahmeursache entspricht.|
|[CFileException::m_lOsError](#m_loserror)|Enthält die zugehörige Fehlernummer des Betriebssystems.|
|[CFileException::m_strFileName](#m_strfilename)|Enthält den Namen der Datei für diese Ausnahme.|

## <a name="remarks"></a>Bemerkungen

Die `CFileException` Klasse enthält öffentliche Datenmember, die den portablen Ursachencode und die betriebssystemspezifische Fehlernummer enthalten. Die Klasse bietet auch statische Memberfunktionen zum Auslösen von Dateiausnahmen und zum Zurückgeben von Ursachencodes für Betriebssystemfehler und C-Laufzeitfehler.

`CFileException`Objekte werden in `CFile` Memberfunktionen und in Memberfunktionen abgeleiteter Klassen erstellt und ausgelöst. Sie können im Rahmen eines **CATCH-Ausdrucks** auf diese Objekte zugreifen. Verwenden Sie für die Portabilität nur den Ursachencode, um den Grund für eine Ausnahme zu erhalten. Weitere Informationen zu Ausnahmen finden Sie im Artikel [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>CFileException::CFileException

Erstellt ein `CFileException` Objekt, das den Ursachencode und den Betriebssystemcode im Objekt speichert.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parameter

*Ursache*<br/>
Eine aufgezählte Typvariable, die den Grund für die Ausnahme angibt. Eine Liste der möglichen Werte finden Sie unter [CFileException::m_cause.](#m_cause)

*lOsError*<br/>
Ein betriebssystemspezifischer Grund für die Ausnahme, sofern verfügbar. Der Parameter *lOsError* stellt mehr Informationen bereit als *Ursache.*

*lpszArchiveName*<br/>
Zeigt auf eine Zeichenfolge, `CFile` die den Namen des Objekts enthält, das die Ausnahme verursacht.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Konstruktor nicht direkt, sondern rufen Sie die globale Funktion [AfxThrowFileException](exception-processing.md#afxthrowfileexception)auf.

> [!NOTE]
> Die Variable *lOsError* `CFile` gilt `CStdioFile` nur für und für Objekte. Die `CMemFile` Klasse behandelt diesen Fehlercode nicht.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException::ErrnoToException

Konvertiert einen bestimmten Laufzeitbibliotheksfehlerwert `CFileException` in einen aufgezählten Fehlerwert.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parameter

*nErrno*<br/>
Ein ganzzahliger Fehlercode, wie in der Laufzeit-Includedatei ERRNO definiert. H.

### <a name="return-value"></a>Rückgabewert

Aufgezählter Wert, der einem angegebenen Laufzeitbibliotheksfehlerwert entspricht.

### <a name="remarks"></a>Bemerkungen

Eine Liste der möglichen aufgezählten Werte finden Sie unter [CFileException::m_cause.](#m_cause)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException::GetErrorMessage

Ruft Text ab, der eine Ausnahme beschreibt.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parameter

*lpszError*<br/>
[in, out] Zeiger auf einen Puffer, der eine Fehlermeldung empfängt.

*nMaxError*<br/>
[in] Die maximale Anzahl von Zeichen, die der angegebene Puffer enthalten kann. Dazu gehört auch das beendende Nullzeichen.

*pnHelpContext*<br/>
[in, out] Zeiger auf eine nicht signierte ganzzahlige Datei, die die Hilfekontext-ID empfängt. Wenn `NULL`, wird keine ID zurückgegeben.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn der angegebene Puffer zu klein ist, wird die Fehlermeldung abgeschnitten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CFileException::GetErrorMessage` verwendet.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException::m_cause

Enthält Werte, die von einem `CFileException`-Enumerationstyp definiert wurden.

```
int m_cause;
```

### <a name="remarks"></a>Bemerkungen

Dieser Datenmember ist eine öffentliche Variable vom Typ **int**. Die Zähler und ihre Bedeutung enumgieren wie folgt:

- `CFileException::none`0: Es ist kein Fehler aufgetreten.

- `CFileException::genericException`1: Ein nicht angegebener Fehler ist aufgetreten.

- `CFileException::fileNotFound`2: Die Datei konnte nicht gefunden werden.

- `CFileException::badPath`3: Der pfadweise ganze oder ein Teil ist ungültig.

- `CFileException::tooManyOpenFiles`4: Die zulässige Anzahl geöffneter Dateien wurde überschritten.

- `CFileException::accessDenied`5: Auf die Datei konnte nicht zugegriffen werden.

- `CFileException::invalidFile`6: Es wurde versucht, ein ungültiges Dateihandle zu verwenden.

- `CFileException::removeCurrentDir`7: Das aktuelle Arbeitsverzeichnis kann nicht entfernt werden.

- `CFileException::directoryFull`8: Es gibt keine verzeichnisen Einträge mehr.

- `CFileException::badSeek`9: Beim Versuch, den Dateizeiger festzulegen, ist ein Fehler aufgetreten.

- `CFileException::hardIO`10: Es ist ein Hardwarefehler aufgetreten.

- `CFileException::sharingViolation`11: AKTIE. EXE wurde nicht geladen, oder eine freigegebene Region wurde gesperrt.

- `CFileException::lockViolation`12: Es gab einen Versuch, einen Bereich zu sperren, der bereits gesperrt war.

- `CFileException::diskFull`14: Die Festplatte ist voll.

- `CFileException::endOfFile`15: Das Ende der Datei wurde erreicht.

    > [!NOTE]
    >  Diese `CFileException`-Ursachenenumeratoren unterscheiden sich von den `CArchiveException`-Ursachenenumeratoren.

    > [!NOTE]
    > `CArchiveException::generic` ist veraltet. Verwenden Sie stattdessen `genericException`. Wenn **generic** in einer Anwendung verwendet und mit /clr erstellt wird, sind die resultierenden Syntaxfehler nicht leicht zu entschlüsseln.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException::m_lOsError

Enthält den Betriebssystemfehlercode für diese Ausnahme.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der Fehlercodes finden Sie in Ihrem technischen Handbuch für Ihr Betriebssystem. Dieser Datenmember ist eine öffentliche Variable vom Typ LONG.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException::m_strFileName

Enthält den Namen der Datei für diese Ausnahmebedingung.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException::OsErrorToException

Gibt einen Enumerator zurück, der einem bestimmten *lOsError-Wert* entspricht. Wenn der Fehlercode unbekannt ist, `CFileException::generic`gibt die Funktion zurück.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parameter

*lOsError*<br/>
Ein betriebssystemspezifischer Fehlercode.

### <a name="return-value"></a>Rückgabewert

Aufgezählter Wert, der einem angegebenen Betriebssystemfehlerwert entspricht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>CFileException::ThrowErrno

Erstellt ein `CFileException` Objekt, das einem bestimmten *nErrno-Wert* entspricht, und löst dann die Ausnahme aus.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parameter

*nErrno*<br/>
Ein ganzzahliger Fehlercode, wie in der Laufzeit-Includedatei ERRNO definiert. H.

*lpszFileName*<br/>
Ein Zeiger auf die Zeichenfolge, die den Namen der Datei enthält, die die Ausnahme verursacht hat, sofern verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException::ThrowOsError

Löst `CFileException` einen entsprechenden wert für *einen angegebenen lOsError* aus. Wenn der Fehlercode unbekannt ist, löst die `CFileException::generic`Funktion eine Ausnahme aus, die als codiert ist.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parameter

*lOsError*<br/>
Ein betriebssystemspezifischer Fehlercode.

*lpszFileName*<br/>
Ein Zeiger auf die Zeichenfolge, die den Namen der Datei enthält, die die Ausnahme verursacht hat, sofern verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Siehe auch

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Ausnahmeverarbeitung](../../mfc/reference/exception-processing.md)
