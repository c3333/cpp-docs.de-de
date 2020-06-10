---
title: CFileException-Klasse
ms.date: 06/09/2020
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
ms.openlocfilehash: f58ba02862e9c0f0c0c0d24797be939276ca8035
ms.sourcegitcommit: 8167c67d76de58a7c2df3b4dcbf3d53e3b151b77
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2020
ms.locfileid: "84664338"
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
|[CFileException:: CFileException](#cfileexception)|Erstellt ein `CFileException`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CFileException:: errnodeexception](#errnotoexception)|Gibt den Code zurück, der einer Lauf Zeit Fehlernummer entspricht.|
|[CFileException:: getErrorMessage](#geterrormessage)|Ruft die Meldung ab, in der eine Ausnahme beschrieben wird.|
|[CFileException:: oserrordeexception](#oserrortoexception)|Gibt einen Ursachen Code zurück, der dem Fehlercode des Betriebssystems entspricht.|
|[CFileException:: throwerrno](#throwerrno)|Löst eine Datei Ausnahme basierend auf einer Lauf Zeit Fehlernummer aus.|
|[CFileException:: throwoserror](#throwoserror)|Löst eine Datei Ausnahme basierend auf einer Betriebssystem-Fehlernummer aus.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFileException:: m_cause](#m_cause)|Enthält portablen Code, der der Ausnahme Ursache entspricht.|
|[CFileException:: m_lOsError](#m_loserror)|Enthält die zugehörige Betriebssystem-Fehlernummer.|
|[CFileException:: m_strFileName](#m_strfilename)|Enthält den Namen der Datei für diese Ausnahme.|

## <a name="remarks"></a>Bemerkungen

Die `CFileException` -Klasse enthält öffentliche Datenmember, die den portablen Ursachen Code und die betriebssystemspezifische Fehlernummer enthalten. Die-Klasse stellt auch statische Member-Funktionen zum Auslösen von Datei Ausnahmen und zum Zurückgeben von Ursachen Codes für Betriebssystem Fehler und C-Laufzeitfehler bereit.

`CFileException`-Objekte werden in Element `CFile` Funktionen und in Element Funktionen abgeleiteter Klassen erstellt und ausgelöst. Sie können auf diese Objekte innerhalb des Gültigkeits Bereichs eines **catch** -Ausdrucks zugreifen. Verwenden Sie für die Portabilität nur den Ursachen Code, um den Grund für eine Ausnahme zu erhalten. Weitere Informationen zu Ausnahmen finden Sie im Artikel [Ausnahmebehandlung (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>CFileException:: CFileException

Erstellt ein `CFileException` -Objekt, das den Ursachen Code und den Betriebssystem Code im-Objekt speichert.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parameter

*zufügen*<br/>
Eine enumerierte Typvariable, die den Grund für die Ausnahme angibt. Eine Liste der möglichen Werte finden Sie unter [CFileException:: m_cause](#m_cause) .

*loserror*<br/>
Ein Betriebssystem spezifischer Grund für die Ausnahme, falls verfügbar. Der *loserror* -Parameter bietet mehr Informationen als *Ursache* .

*lpszarchivename*<br/>
Verweist auf eine Zeichenfolge, die den Namen des Objekts enthält, `CFile` das die Ausnahme verursacht hat.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Konstruktor nicht direkt, sondern nennen Sie stattdessen die globale Funktion [afxthrowfileexception](exception-processing.md#afxthrowfileexception).

> [!NOTE]
> Die Variable *loserror* gilt nur für `CFile` -und- `CStdioFile` Objekte. `CMemFile`Dieser Fehlercode wird von der-Klasse nicht behandelt.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException:: errnodeexception

Konvertiert einen angegebenen Lauf Zeit Bibliotheks-Fehlerwert in einen `CFileException` enumerationsfehlerwert.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parameter

*nrno*<br/>
Ein ganzzahliger Fehlercode, wie er in der Lauf Zeit Datei "errno" definiert ist. Micha.

### <a name="return-value"></a>Rückgabewert

Enumerationswert, der einem angegebenen Lauf Zeit Bibliotheks-Fehlerwert entspricht.

### <a name="remarks"></a>Bemerkungen

Eine Liste der möglichen Enumerationswerte finden Sie unter [CFileException:: m_cause](#m_cause) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException:: getErrorMessage

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
in Die maximale Anzahl von Zeichen, die im angegebenen Puffer enthalten sein können. Dies schließt das abschließende Null-Zeichen ein.

*pnHelpContext*<br/>
[in, out] Zeiger auf eine Ganzzahl ohne Vorzeichen, die die Hilfe Kontext-ID empfängt. Wenn `NULL` , wird keine ID zurückgegeben.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich war. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Wenn der angegebene Puffer zu klein ist, wird die Fehlermeldung abgeschnitten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CFileException::GetErrorMessage` verwendet.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException:: m_cause

Enthält Werte, die von einem `CFileException`-Enumerationstyp definiert wurden.

```
int m_cause;
```

### <a name="remarks"></a>Bemerkungen

Dieser Datenmember ist eine öffentliche Variable vom Typ **int**. Die Enumeratoren und ihre Bedeutungen lauten wie folgt:

| Fehler | Wert und Bedeutung |
|--|--|
| `CFileException::none` | 0: kein Fehler aufgetreten. |
| `CFileException::genericException` | 1: ein nicht angegebener Fehler ist aufgetreten. |
| `CFileException::fileNotFound` | 2: die Datei konnte nicht gefunden werden. |
| `CFileException::badPath` | 3: der vollständig oder ein Teil des Pfads ist ungültig. |
| `CFileException::tooManyOpenFiles` | 4: die zulässige Anzahl geöffneter Dateien wurde überschritten. |
| `CFileException::accessDenied` | 5: auf die Datei konnte nicht zugegriffen werden. |
| `CFileException::invalidFile` | 6: Es wurde versucht, ein ungültiges Datei Handle zu verwenden. |
| `CFileException::removeCurrentDir` | 7: das aktuelle Arbeitsverzeichnis kann nicht entfernt werden. |
| `CFileException::directoryFull` | 8: Es sind keine weiteren Verzeichniseinträge vorhanden. |
| `CFileException::badSeek` | 9: beim Versuch, den Dateizeiger festzulegen, ist ein Fehler aufgetreten. |
| `CFileException::hardIO` | 10: Hardwarefehler. |
| `CFileException::sharingViolation` | 11: SHARE.EXE wurde nicht geladen, oder ein frei gegebener Bereich wurde gesperrt. |
| `CFileException::lockViolation` | 12: Es wurde versucht, einen Bereich zu sperren, der bereits gesperrt war. |
| `CFileException::diskFull` | 13: der Datenträger ist voll. |
| `CFileException::endOfFile` | 14: das Dateiende wurde erreicht. |

    > [!NOTE]
    >  These `CFileException` cause enumerators are distinct from the `CArchiveException` cause enumerators.

    > [!NOTE]
    > `CArchiveException::generic` is deprecated. Use `genericException` instead. If **generic** is used in an application and built with /clr, the resulting syntax errors are not easy to decipher.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException:: m_lOsError

Enthält den Fehlercode des Betriebssystems für diese Ausnahme.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Bemerkungen

Eine Liste der Fehlercodes finden Sie in der technischen Anleitung Ihres Betriebssystems. Dieser Datenmember ist eine öffentliche Variable vom Typ Long.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException:: m_strFileName

Enthält den Namen der Datei für diese Ausnahme Bedingung.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException:: oserrordeexception

Gibt einen Enumerator zurück, der einem angegebenen *loserror* -Wert entspricht. Wenn der Fehlercode unbekannt ist, gibt die Funktion zurück `CFileException::generic` .

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parameter

*loserror*<br/>
Ein Betriebssystem spezifischer Fehlercode.

### <a name="return-value"></a>Rückgabewert

Enumerationswert, der einem angegebenen Betriebssystem-Fehlerwert entspricht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>CFileException:: throwerrno

Erstellt ein- `CFileException` Objekt, das einem angegebenen *nerrno* -Wert entspricht, und löst dann die Ausnahme aus.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parameter

*nrno*<br/>
Ein ganzzahliger Fehlercode, wie er in der Lauf Zeit Datei "errno" definiert ist. Micha.

*lpszfilename*<br/>
Ein Zeiger auf die Zeichenfolge, die den Namen der Datei enthält, die die Ausnahme verursacht hat, sofern verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException:: throwoserror

Löst eine aus `CFileException` , die einem angegebenen *loserror* -Wert entspricht. Wenn der Fehlercode unbekannt ist, löst die Funktion eine Ausnahme aus, die als codiert ist `CFileException::generic` .

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parameter

*loserror*<br/>
Ein Betriebssystem spezifischer Fehlercode.

*lpszfilename*<br/>
Ein Zeiger auf die Zeichenfolge, die den Namen der Datei enthält, die die Ausnahme verursacht hat, sofern verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Ausnahmeverarbeitung](../../mfc/reference/exception-processing.md)
