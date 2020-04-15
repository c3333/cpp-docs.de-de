---
title: CFile-Klasse
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: 4ba37d481db73fb0556659ede267b3474c3f32f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373917"
---
# <a name="cfile-class"></a>CFile-Klasse

Die Basisklasse für Microsoft Foundation Class-Dateiklassen.

## <a name="syntax"></a>Syntax

```
class CFile : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFile::CFile](#cfile)|Erstellt ein `CFile` Objekt aus einem Pfad oder Dateihandle.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFile::Abbruch](#abort)|Schließt eine Datei, die alle Warnungen und Fehler ignoriert.|
|[CFile::Schließen](#close)|Schließt eine Datei und löscht das Objekt.|
|[CFile::Duplicate](#duplicate)|Erstellt ein doppeltes Objekt basierend auf dieser Datei.|
|[CFile::Flush](#flush)|Löscht alle noch zu schreibenden Daten.|
|[CFile::GetFileName](#getfilename)|Ruft den Dateinamen der ausgewählten Datei ab.|
|[CFile::GetFilePath](#getfilepath)|Ruft den vollständigen Dateipfad der ausgewählten Datei ab.|
|[CFile::GetFileTitle](#getfiletitle)|Ruft den Titel der ausgewählten Datei ab.|
|[CFile::GetLength](#getlength)|Ruft die Länge der Datei ab.|
|[CFile::GetPosition](#getposition)|Ruft den aktuellen Dateizeiger ab.|
|[CFile::GetStatus](#getstatus)|Ruft den Status der geöffneten Datei oder in der statischen Version ab, ruft den Status der angegebenen Datei (statische, virtuelle Funktion) ab.|
|[CFile::LockRange](#lockrange)|Sperrt einen Bereich von Bytes in einer Datei.|
|[CFile::Öffnen](#open)|Öffnet sicher eine Datei mit einer Fehlertestoption.|
|[CFile::Lesen](#read)|Liest (ungepufferte) Daten aus einer Datei an der aktuellen Dateiposition.|
|[CFile::Entfernen](#remove)|Löscht die angegebene Datei (statische Funktion).|
|[CFile::Umbenennen](#rename)|Benennt die angegebene Datei um (statische Funktion).|
|[CFile::Suchen](#seek)|Positioniert den aktuellen Dateizeiger.|
|[CFile::SeekToBegin](#seektobegin)|Positioniert den aktuellen Dateizeiger am Anfang der Datei.|
|[CFile::SeekToEnd](#seektoend)|Positioniert den aktuellen Dateizeiger am Ende der Datei.|
|[CFile::SetFilePath](#setfilepath)|Legt den vollständigen Dateipfad der ausgewählten Datei fest.|
|[CFile::SetLength](#setlength)|Ändert die Länge der Datei.|
|[CFile::SetStatus](#setstatus)|Legt den Status der angegebenen Datei fest (statische, virtuelle Funktion).|
|[CFile::UnlockRange](#unlockrange)|Entsperrt einen Bereich von Bytes in einer Datei.|
|[CFile::Schreiben](#write)|Schreibt (ungepufferte) Daten in einer Datei in die aktuelle Dateiposition.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFile::operator HANDLE](#operator_handle)|Ein Handle `CFile` für ein Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Bestimmt, `CFile` ob das Objekt über ein gültiges Handle verfügt.|
|[CFile::m_hFile](#m_hfile)|Enthält in der Regel das Betriebssystemdateihandle.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Zeiger auf das `CAtlTransactionManager`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Es bietet direkt ungepufferte, binäre Datenträgereingabe/-ausgabedienste und unterstützt indirekt Textdateien und Speicherdateien über seine abgeleiteten Klassen. `CFile`arbeitet in Verbindung `CArchive` mit der Klasse, um die Serialisierung von Microsoft Foundation Class-Objekten zu unterstützen.

Die hierarchische Beziehung zwischen dieser Klasse und ihren abgeleiteten Klassen ermöglicht es `CFile` Dem Programm, alle Dateiobjekte über die polymorphe Schnittstelle zu bearbeiten. Eine Speicherdatei verhält sich beispielsweise wie eine Datenträgerdatei.

Verwenden `CFile` Sie und seine abgeleiteten Klassen für allgemeine Datenträger-E/A. Verwenden `ofstream` Sie `iostream` oder andere Microsoft-Klassen für formatierten Text, der an eine Datenträgerdatei gesendet wird.

Normalerweise wird eine Datenträgerdatei `CFile` beim Bau automatisch geöffnet und bei der Zerstörung geschlossen. Statische Memberfunktionen ermöglichen es Ihnen, den Status einer Datei abzuhören, ohne die Datei zu öffnen.

Weitere Informationen zur `CFile`Verwendung finden Sie in den Artikeln [Dateien in MFC](../../mfc/files-in-mfc.md) und [Dateiverarbeitung](../../c-runtime-library/file-handling.md) in der *Laufzeitbibliotheksreferenz*.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cfileabort"></a><a name="abort"></a>CFile::Abbruch

Schließt die diesem Objekt zugeordnete Datei und macht die Datei zum Lesen oder Schreiben nicht verfügbar.

```
virtual void Abort();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Datei vor dem Zerstören des Objekts nicht geschlossen haben, schließt der Destruktor sie für Sie.

Bei der Behandlung `CFile::Abort` von `CFile::Close` Ausnahmen unterscheidet sich von zwei wichtigen Möglichkeiten. Erstens löst `Abort` die Funktion keine Ausnahme bei Fehlern aus, `Abort`da Fehler von ignoriert werden. Zweitens, `Abort` wird nicht **ASSERT,** wenn die Datei nicht geöffnet wurde, oder zuvor geschlossen wurde.

Wenn Sie **das** Objekt `CFile` neu verwendet haben, um das Objekt auf dem Heap zuzuweisen, müssen Sie es nach dem Schließen der Datei löschen. `Abort`setzt `m_hFile` `CFile::hFileNull`auf .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a>CFile::CFile

Erstellt und initialisiert ein `CFile`-Objekt.

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parameter

*hDatei*<br/>
Handle einer Datei zum Anhängen an das `CFile`-Objekt.

*lpszFileName*<br/>
Relativer oder vollständiger Pfad einer Datei zum Anhängen an das `CFile`-Objekt.

*nOpenFlags*<br/>
Bitweise Kombination (OR) der Dateizugriffsoptionen für die angegebene Datei. Mögliche Optionen finden Sie im Abschnitt "Hinweise".

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="remarks"></a>Bemerkungen

In den folgenden fünf Tabellen sind die möglichen Optionen für den Parameter *nOpenFlags* aufgeführt.

Wählen Sie eine der folgenden Dateizugriffsmodus-Optionen. Der standardmäßige Dateizugriffsmodus ist `CFile::modeRead`, wobei es sich um einen schreibgeschützten Modus handelt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CFile::modeRead`|Fordert nur Lesezugriff an.|
|`CFile::modeWrite`|Fordert nur Schreibzugriff an.|
|`CFile::modeReadWrite`|Fordert Lese- und Schreibzugriff an.|

Wählen Sie eine der folgenden Zeichenmodus-Optionen.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CFile::typeBinary`|Legt den Binärmodus fest (nur in abgeleiteten Klassen verwendet).|
|`CFile::typeText`|Legt den Textmodus mit spezieller Verarbeitung für Wagenrücklauf-Feedpaare fest (nur in abgeleiteten Klassen).|
|`CFile::typeUnicode`|Legt den Unicode-Modus fest (nur in abgeleiteten Klassen verwendet). Text wird im Unicode-Format in die Datei geschrieben, wenn die Anwendung in einer Unicode-Konfiguration erstellt wurde. Es wird keine BOM in die Datei geschrieben.|

Wählen Sie eine der folgenden Dateifreigabemodus-Optionen. Der standardmäßige Dateifreigabemodus ist `CFile::shareExclusive`, wobei es sich um einen exklusiven Modus handelt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CFile::shareDenyNone`|Keine Freigabebeschränkungen.|
|`CFile::shareDenyRead`|Verweigert allen anderen Lesezugriff.|
|`CFile::shareDenyWrite`|Verweigert allen anderen Schreibzugriff.|
|`CFile::shareExclusive`|Verweigert allen anderen Lese- und Schreibzugriff.|

Wählen Sie die erste oder beide Dateierstellungsmodus-Optionen. Der standardmäßige Dateierstellungsmodus ist `CFile::modeNoTruncate`, wobei es sich um "offen vorhanden" handelt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CFile::modeCreate`|Erstellt eine neue Datei, wenn keine Datei vorhanden ist. Wenn die Datei bereits vorhanden ist, wird sie überschrieben und zunächst auf Null festgelegt.|
|`CFile::modeNoTruncate`|Erstellt eine neue Datei, wenn keine Datei vorhanden ist; Andernfalls wird die Datei, wenn sie bereits `CFile` vorhanden ist, an das Objekt angefügt.|

Wählen Sie die folgenden Datei-Cache-Optionen wie beschrieben. Standardmäßig verwendet das System ein allgemeines Zwischenspeicherungsschema, das nicht als Option verfügbar ist.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CFile::osNoBuffer`|Das System verwendet keinen Zwischencache für die Datei. Diese Option bricht die beiden folgenden Optionen ab.|
|`CFile::osRandomAccess`|Der Datei-Cache wird für wahlfreien Zugriff optimiert. Verwenden Sie nicht sowohl diese Option als auch die Option für den sequenziellen Scan.|
|`CFile::osSequentialScan`|Der Datei-Cache wird für sequenziellen Zugriff optimiert. Verwenden Sie nicht sowohl diese Option als auch die Option für den zufälligen Zugriff.|
|`CFile::osWriteThrough`|Schreibvorgänge werden ohne Verzögerung durchgeführt.|

Wählen Sie die folgende Sicherheitsoption, um zu verhindern, dass der Dateihandle übergeben wird. Standardmäßig können alle neuen untergeordneten Prozesse den Dateihandle verwenden.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CFile::modeNoInherit`|Verhindert, dass untergeordnete Prozesse den Dateihandle verwenden.|

Der Standardkonstruktor initialisiert Member, fügt aber keine `CFile` Datei an das Objekt an. Nachdem Sie diesen Konstruktor verwendet haben, verwenden Sie die [CFile::Open-Methode,](#open) um eine Datei zu öffnen und an das `CFile` Objekt anzufügen.

Der Konstruktor mit einem Parameter initialisiert Member und hängt eine vorhandene Datei an das `CFile`-Objekt an.

Der Konstruktor mit zwei Parametern initialisiert Member und versucht, die angegebene Datei zu öffnen. Wenn der Konstruktor die angegebene Datei erfolgreich öffnet, wird die Datei an das `CFile`-Objekt angehängt; anderenfalls löst der Konstruktor einen Zeiger auf ein `CInvalidArgException`-Objekt aus. Weitere Informationen zum Behandeln von Ausnahmen finden Sie unter [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

Wenn `CFile` ein Objekt eine angegebene Datei erfolgreich öffnet, `CFile` wird diese Datei automatisch geschlossen, wenn das Objekt zerstört wird. Andernfalls müssen Sie die Datei explizit schließen, nachdem `CFile` sie nicht mehr an das Objekt angefügt wurde.

### <a name="example"></a>Beispiel

Der folgende Code veranschaulicht die Verwendung einer `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a>CFile::Schließen

Schließt die diesem Objekt zugeordnete Datei und macht die Datei zum Lesen oder Schreiben nicht verfügbar.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie die Datei vor dem Zerstören des Objekts nicht geschlossen haben, schließt der Destruktor sie für Sie.

Wenn Sie **das** Objekt `CFile` neu verwendet haben, um das Objekt auf dem Heap zuzuweisen, müssen Sie es nach dem Schließen der Datei löschen. `Close`setzt `m_hFile` `CFile::hFileNull`auf .

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFile::CFile](#cfile).

## <a name="cfileduplicate"></a><a name="duplicate"></a>CFile::Duplicate

Erstellt ein `CFile` doppeltes Objekt für eine bestimmte Datei.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CFile` ein doppeltes Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion entspricht der C-Laufzeitfunktion `_dup`.

## <a name="cfileflush"></a><a name="flush"></a>CFile::Flush

Erzwingt, dass alle im Dateipuffer verbleibenden Daten in die Datei geschrieben werden.

```
virtual void Flush();
```

### <a name="remarks"></a>Bemerkungen

Die Verwendung `Flush` von garantiert keine `CArchive` Spülung von Puffern. Wenn Sie ein Archiv verwenden, rufen Sie [zuerst CArchive::Flush](../../mfc/reference/carchive-class.md#flush) auf.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFile::SetFilePath](#setfilepath).

## <a name="cfilegetfilename"></a><a name="getfilename"></a>CFile::GetFileName

Rufen Sie diese Memberfunktion auf, um den Namen einer angegebenen Datei abzurufen.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Name der Datei.

### <a name="remarks"></a>Bemerkungen

Wenn Sie beispielsweise `GetFileName` anrufen, um eine Nachricht an `c:\windows\write\myfile.wri`den Benutzer `myfile.wri`über die Datei zu generieren, wird der Dateiname , zurückgegeben.

Um den gesamten Pfad der Datei, einschließlich des Namens, zurückzugeben, rufen Sie [GetFilePath](#getfilepath)auf. Um den Titel der `myfile`Datei ( zurückzugeben, rufen Sie [GetFileTitle](#getfiletitle)auf.

### <a name="example"></a>Beispiel

Dieses Codefragment öffnet das SYSTEM. INI-Datei in Ihrem WINDOWS-Verzeichnis. Wenn gefunden, wird das Beispiel den Namen, den Pfad und den Titel ausdrucken, wie unter Ausgabe gezeigt:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a>CFile::GetFilePath

Rufen Sie diese Memberfunktion auf, um den vollständigen Pfad einer angegebenen Datei abzurufen.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Rückgabewert

Der vollständige Pfad der angegebenen Datei.

### <a name="remarks"></a>Bemerkungen

Wenn Sie beispielsweise `GetFilePath` aufrufen, um eine Nachricht an `c:\windows\write\myfile.wri`den Benutzer `c:\windows\write\myfile.wri`über die Datei zu generieren, wird der Dateipfad zurückgegeben.

Um nur den Namen der`myfile.wri`Datei ( zurückzugeben, rufen Sie [GetFileName](#getfilename)auf. Um den Titel der`myfile`Datei ( zurückzugeben, rufen Sie [GetFileTitle](#getfiletitle)auf.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetFileName](#getfilename).

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a>CFile::GetFileTitle

Rufen Sie diese Memberfunktion auf, um den Dateititel (den Anzeigenamen) für die Datei abzurufen.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Rückgabewert

Der Titel der zugrunde liegenden Datei.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) auf, um den Titel der Datei abzurufen. Bei Erfolg gibt die Methode die Zeichenfolge zurück, die das System verwenden würde, um dem Benutzer den Dateinamen anzuzeigen. Andernfalls ruft die Methode [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) auf, um den Dateinamen (einschließlich der Dateierweiterung) der zugrunde liegenden Datei abzurufen. Das bedeutet, dass die Dateierweiterung nicht immer in der zurückgegebenen Dateititelzeichenfolge enthalten ist. Weitere Informationen finden Sie unter [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) und [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) im Windows SDK.

Um den gesamten Pfad der Datei, einschließlich des Namens, zurückzugeben, rufen Sie [GetFilePath](#getfilepath)auf. Um nur den Namen der Datei zurückzugeben, rufen Sie [GetFileName](#getfilename)auf.

### <a name="example"></a>Beispiel

Siehe Beispiel für [GetFileName](#getfilename).

## <a name="cfilegetlength"></a><a name="getlength"></a>CFile::GetLength

Ruft die aktuelle logische Länge der Datei in Bytes ab.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Rückgabewert

Die Länge der Datei.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a>CFile::GetPosition

Ruft den aktuellen Wert des Dateizeigers ab, der `Seek`in späteren Aufrufen von verwendet werden kann.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Der Dateizeiger.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a>CFile::GetStatus

Diese Methode ruft Statusinformationen ab, die sich auf eine bestimmte `CFile` Objektinstanz oder einen bestimmten Dateipfad beziehen.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*rStatus*<br/>
Ein Verweis auf eine `CFileStatus` vom Benutzer bereitgestellte Struktur, die die Statusinformationen empfängt. Die `CFileStatus` Struktur hat die folgenden Felder:

- `CTime m_ctime`Das Datum und die Uhrzeit, zu der die Datei erstellt wurde.

- `CTime m_mtime`Datum und Uhrzeit der letzten Änderung der Datei.

- `CTime m_atime`Das Datum und die Uhrzeit, zu der die Datei zuletzt zum Lesen aufgerufen wurde.

- `ULONGLONG m_size`Die logische Größe der Datei in Bytes, wie vom Befehl DIR gemeldet.

- `BYTE m_attribute`Das Attributbyte der Datei.

- `char m_szFullName[_MAX_PATH]`Der absolute Dateiname im Windows-Zeichensatz.

*lpszFileName*<br/>
Eine Zeichenfolge im Windows-Zeichensatz, die den Pfad zur gewünschten Datei ist. Der Pfad kann relativ oder absolut sein oder einen Netzwerkpfadnamen enthalten.

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Statusinformationen für die angegebene Datei erfolgreich abgerufen wurden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die nicht statische `GetStatus` Version von ruft Statusinformationen der geöffneten Datei ab, die dem angegebenen `CFile` Objekt zugeordnet ist.  Die statische `GetStatus` Version von ruft den Dateistatus von einem bestimmten Dateipfad ab, ohne die Datei tatsächlich zu öffnen. Diese Version ist nützlich, um die Existenz- und Zugriffsrechte einer Datei zu testen.

Der `m_attribute` Member `CFileStatus` der Struktur bezieht sich auf den Dateiattributsatz. Die `CFile` Klasse stellt den Attributenumerationstyp bereit, sodass Dateiattribute symbolisch angegeben werden können: **Attribute**

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

## <a name="cfilehfilenull"></a><a name="hfilenull"></a>CFile::hFileNull

Bestimmt das Vorhandensein eines gültigen `CFile` Dateihandles für das Objekt.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Bemerkungen

Diese Konstante wird verwendet, `CFile` um zu bestimmen, ob das Objekt über ein gültiges Dateihandle verfügt.

Das folgende Beispiel veranschaulicht diesen Vorgang:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a>CFile::LockRange

Sperrt einen Bytebereich in einer geöffneten Datei und löst eine Ausnahme aus, wenn die Datei bereits gesperrt ist.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parameter

*dwPos*<br/>
Der Byte-Offset des Anfangs des zu sperrenden Bytebereichs.

*dwCount*<br/>
Die Anzahl der zu sperrenden Bytes im Bereich.

### <a name="remarks"></a>Bemerkungen

Das Sperren von Bytes in einer Datei verhindert den Zugriff auf diese Bytes durch andere Prozesse. Sie können mehr als einen Bereich einer Datei sperren, aber es sind keine überlappenden Bereiche zulässig.

Wenn Sie die Region `UnlockRange` mit der Memberfunktion entsperren, muss der Bytebereich genau dem Bereich entsprechen, der zuvor gesperrt war. Die `LockRange` Funktion führt keine angrenzenden Bereiche zusammen. Wenn zwei gesperrte Bereiche nebeneinander liegen, müssen Sie jede Region separat entsperren.

> [!NOTE]
> Diese Funktion ist für die `CMemFile`-derived-Klasse nicht verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a>CFile::m_hFile

Enthält das Betriebssystemdateihandle für eine geöffnete Datei.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Bemerkungen

`m_hFile`ist eine öffentliche Variable vom Typ UINT. Es `CFile::hFileNull`enthält , eine betriebssystemunabhängige leere Dateianzeige, wenn das Handle nicht zugewiesen wurde.

Die `m_hFile` Verwendung von wird nicht empfohlen, da die Bedeutung des Members von der abgeleiteten Klasse abhängt. `m_hFile`wird ein öffentliches Mitglied für die Unterstützung der nichtpolymorphen Verwendung der Klasse gemacht.

## <a name="cfilem_ptm"></a><a name="m_ptm"></a>CFile::m_pTM

Zeiger auf `CAtlTransactionManager` ein Objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cfileopen"></a><a name="open"></a>CFile::Öffnen

Ist überladen. `Open`ist für die Verwendung `CFile` mit dem Standardkonstruktor konzipiert.

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*lpszFileName*<br/>
Eine Zeichenfolge, die den Pfad zur gewünschten Datei enthält. Der Pfad kann relativ, absolut oder ein Netzwerkname (UNC) sein.

*nOpenFlags*<br/>
Ein UINT, das den Freigabe- und Zugriffsmodus der Datei definiert. Sie gibt die Aktion an, die beim Öffnen der Datei zu ergreifen ist. Sie können Optionen kombinieren, indem Sie den Operator bitwise-OR ( **&#124;** ) verwenden. Eine Zugriffsberechtigung und eine Freigabeoption sind erforderlich. und `modeCreate` `modeNoInherit` Modi sind optional. Eine [CFile](#cfile) Liste der Modusoptionen finden Sie im CFile-Konstruktor.

*pError*<br/>
Ein Zeiger auf ein vorhandenes Dateiausnahmeobjekt, das den Status eines fehlgeschlagenen Vorgangs erhält.

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Open erfolgreich war; andernfalls 0. Der *parameter pError* ist nur dann aussagekräftig, wenn 0 zurückgegeben wird.

### <a name="remarks"></a>Bemerkungen

Die `Open` beiden Funktionen sind "sichere" Methoden zum Öffnen einer Datei, bei der ein Fehler eine normale, erwartete Bedingung ist.

Während `CFile` der Konstruktor eine Ausnahme in `Open` einer Fehlerbedingung auslöst, gibt FALSE für Fehlerbedingungen zurück. `Open`kann jedoch ein [CFileException-Objekt](../../mfc/reference/cfileexception-class.md) initialisieren, um den Fehler zu beschreiben. Wenn Sie den *Parameter pError* nicht angeben oder wenn Sie `Open` NULL für *pError* `CFileException`übergeben, gibt FALSE zurück und löst keine aus. Wenn Sie einen Zeiger an `CFileException`einen `Open` vorhandenen übergeben und auf einen Fehler stößt, füllt die Funktion ihn mit Informationen aus, die diesen Fehler beschreiben. `Open`löst in beiden Fällen keine Ausnahme aus.

In der folgenden Tabelle `Open`werden die möglichen Ergebnisse von beschrieben.

|`pError`|Fehler aufgetreten|Rückgabewert|CFileException-Inhalt|
|--------------|------------------------|------------------|----------------------------|
|NULL|Nein|TRUE|–|
|ptr zu`CFileException`|Nein|TRUE|unverändert|
|NULL|Ja|FALSE|–|
|ptr zu`CFileException`|Ja|FALSE|Initialisiert, um Fehler zu beschreiben|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a>CFile::operator HANDLE

Verwenden Sie diesen Operator, `CFile` um ein Handle an ein Objekt an Funktionen `HANDLE`wie [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) und [GetFileTime](/windows/win32/api/fileapi/nf-fileapi-getfiletime) zu übergeben, die eine erwarten.

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a>CFile::Lesen

Liest Daten aus der dem `CFile` Objekt zugeordneten Datei in einen Puffer.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Zeiger auf den vom Benutzer bereitgestellten Puffer, der die aus der Datei gelesenen Daten empfangen soll.

*nCount*<br/>
Die maximale Anzahl von Bytes, die aus der Datei gelesen werden sollen. Bei Textmodusdateien werden Wagen-Rücklauf-Feedpaare als einzelne Zeichen gezählt.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der in den Puffer übertrageben Bytes. Für `CFile` alle Klassen kann der Rückgabewert kleiner als *nCount* sein, wenn das Ende der Datei erreicht wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Ein weiteres Beispiel finden Sie unter [CFile::Open](#open).

## <a name="cfileremove"></a><a name="remove"></a>CFile::Entfernen

Diese statische Funktion löscht die durch den Pfad angegebene Datei.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*lpszFileName*<br/>
Eine Zeichenfolge, die den Pfad zur gewünschten Datei ist. Der Pfad kann relativ oder absolut sein und einen Netzwerknamen enthalten.

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="remarks"></a>Bemerkungen

`Remove`wird kein Verzeichnis entfernt.

Die `Remove` Memberfunktion löst eine Ausnahme aus, wenn die verbundene Datei geöffnet ist oder die Datei nicht entfernt werden kann. Diese Funktion entspricht dem DEL-Befehl.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a>CFile::Umbenennen

Diese statische Funktion benennt die angegebene Datei um.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*lpszOldName*<br/>
Der alte Pfad.

*lpszNewName*<br/>
Der neue Pfad.

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="remarks"></a>Bemerkungen

Verzeichnisse können nicht umbenannt werden. Diese Funktion entspricht dem REN-Befehl.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a>CFile::Suchen

Positioniert den Dateizeiger in einer geöffneten Datei neu.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parameter

*lOff*<br/>
Anzahl der Bytes, um den Dateizeiger zu verschieben. Positive Werte verschieben den Dateizeiger in Richtung des Endes der Datei. negative Werte verschieben den Dateizeiger zum Anfang der Datei.

*nVon*<br/>
Position, von der gesucht werden kann. Weitere Informationen zu möglichen Werten finden Sie im Abschnitt "Bemerkungen".

### <a name="return-value"></a>Rückgabewert

Die Position des Dateizeigers, wenn die Methode erfolgreich war; Andernfalls ist der Rückgabewert nicht definiert, `CFileException` und ein Zeiger auf eine Ausnahme wird ausgelöst.

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle sind mögliche Werte für den Parameter *nFrom* aufgeführt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`CFile::begin`|Suchen Sie vom Anfang der Datei.|
|`CFile::current`|Suchen Sie vom aktuellen Speicherort des Dateizeigers.|
|`CFile::end`|Suchen Sie vom Ende der Datei.|

Wenn eine Datei geöffnet wird, wird der Dateizeiger bei 0, dem Anfang der Datei, positioniert.

Sie können den Dateizeiger auf eine Position außerhalb des Endes einer Datei festlegen. Wenn Sie dies tun, wird die Größe der Datei erst erhöht, wenn Sie in die Datei schreiben.

Der Ausnahmehandler für diese Methode muss das Ausnahmeobjekt löschen, nachdem die Ausnahme verarbeitet wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a>CFile::SeekToBegin

Legt den Wert des Dateizeigers auf den Anfang der Datei fest.

```
void SeekToBegin();
```

### <a name="remarks"></a>Bemerkungen

`SeekToBegin()` entspricht `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a>CFile::SeekToEnd

Legt den Wert des Dateizeigers auf das logische Ende der Datei fest.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Rückgabewert

Die Länge der Datei in Byte.

### <a name="remarks"></a>Bemerkungen

`SeekToEnd()` entspricht `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a>CFile::SetFilePath

Rufen Sie diese Funktion auf, um den Pfad der Datei anzugeben. Wenn z. B. der Pfad einer Datei nicht verfügbar ist, `SetFilePath` wenn ein [CFile-Objekt](../../mfc/reference/cfile-class.md) erstellt wird, rufen Sie die Bereitstellung auf.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parameter

*lpszNewName*<br/>
Zeiger auf eine Zeichenfolge, die den neuen Pfad angibt.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> `SetFilePath`öffnet die Datei nicht und erstellt die Datei nicht; Es ordnet `CFile` das Objekt einfach einem Pfadnamen zu, der dann verwendet werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a>CFile::SetLength

Rufen Sie diese Funktion auf, um die Länge der Datei zu ändern.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parameter

*dwNewLen*<br/>
Gewünschte Länge der Datei in Bytes. Dieser Wert kann größer oder kleiner als die aktuelle Länge der Datei sein. Die Datei wird erweitert oder abgeschnitten.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Mit `CMemFile`kann diese Funktion `CMemoryException` ein Objekt auslösen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a>CFile::SetStatus

Legt den Status der Datei fest, die diesem Dateispeicherort zugeordnet ist.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parameter

*lpszFileName*<br/>
Eine Zeichenfolge, die den Pfad zur gewünschten Datei ist. Der Pfad kann relativ oder absolut sein und einen Netzwerknamen enthalten.

*Status*<br/>
Der Puffer, der die neuen Statusinformationen enthält. Rufen `GetStatus` Sie die Memberfunktion `CFileStatus` auf, um die Struktur mit aktuellen Werten vorzufüllen, und nehmen Sie dann bei Bedarf Änderungen vor. Wenn ein Wert 0 ist, wird das entsprechende Statuselement nicht aktualisiert. Eine Beschreibung der `CFileStatus` Struktur finden Sie in der [GetStatus-Memberfunktion.](#getstatus)

*Ptm*<br/>
Zeiger auf CAtlTransactionManager-Objekt

### <a name="remarks"></a>Bemerkungen

Um die Uhrzeit `m_mtime` festzulegen, ändern Sie das *Statusfeld*.

Wenn Sie einen `SetStatus` Aufruf tätigen, um nur die Attribute der `m_mtime` Datei zu ändern, und das Element der Dateistatusstruktur ungleich Null ist, können auch die Attribute betroffen sein (das Ändern des Zeitstempels kann Nebenwirkungen auf die Attribute haben). Wenn Sie nur die Attribute der Datei ändern `m_mtime` möchten, legen Sie zuerst das Element der `SetStatus`Dateistatusstruktur auf Null fest, und rufen Sie dann an .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a>CFile::UnlockRange

Entsperrt einen Bereich von Bytes in einer geöffneten Datei.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parameter

*dwPos*<br/>
Der Byte-Offset des Anfangs des Freischaltbereichs des Bytebereichs.

*dwCount*<br/>
Die Anzahl der Bytes im Zuentsperren.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden [LockRange](#lockrange) Sie in der Beschreibung der LockRange-Memberfunktion.

> [!NOTE]
> Diese Funktion ist für `CMemFile`die -derived-Klasse nicht verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a>CFile::Schreiben

Schreibt Daten aus einem Puffer in `CFile` die dem Objekt zugeordnete Datei.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Zeiger auf den vom Benutzer bereitgestellten Puffer, der die Daten enthält, die in die Datei geschrieben werden sollen.

*nCount*<br/>
Die Anzahl der Bytes, die aus dem Puffer übertragen werden sollen. Bei Textmodusdateien werden Wagen-Rücklauf-Feedpaare als einzelne Zeichen gezählt.

### <a name="remarks"></a>Bemerkungen

`Write`löst eine Ausnahme als Reaktion auf mehrere Bedingungen aus, einschließlich der Bedingung für den Datenträger voll.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Siehe auch die Beispiele für [CFile::CFile](#cfile) und [CFile::Open](#open).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile-Klasse](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile-Klasse](../../mfc/reference/cmemfile-class.md)
