---
title: CStdioFile-Klasse
ms.date: 08/29/2019
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: 80ee65aa339a38b3d8434bc4c7cb977e263f037b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366016"
---
# <a name="cstdiofile-class"></a>CStdioFile-Klasse

Stellt eine C-Laufzeitstreamdatei dar, die von der Laufzeitfunktion [fopen](../../c-runtime-library/reference/fopen-wfopen.md)geöffnet wird.

## <a name="syntax"></a>Syntax

```
class CStdioFile : public CFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStdioFile::CStdioDatei](#cstdiofile)|Erstellt ein `CStdioFile` Objekt aus einem Pfad oder Dateizeiger.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStdioFile::Öffnen](#open)|Ist überladen. Open ist für die `CStdioFile` Verwendung mit dem Standardkonstruktor (Overrides [CFile::Open](../../mfc/reference/cfile-class.md#open)) konzipiert.|
|[CStdioFile::ReadString](#readstring)|Liest eine einzelne Textzeile.|
|[CStdioFile::Suchen](#seek)|Positioniert den aktuellen Dateizeiger.|
|[CStdioFile::WriteString](#writestring)|Schreibt eine einzelne Textzeile.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Enthält einen Zeiger auf eine geöffnete Datei.|

## <a name="remarks"></a>Bemerkungen

Stream-Dateien werden gepuffert und können entweder im Textmodus (Standardmodus) oder im Binärmodus geöffnet werden.

Der Textmodus bietet eine spezielle Verarbeitung für Wagenrücklauf-Feedpaare. Wenn Sie ein Zeilenvorschub (Newline) in ein Textmodusobjekt `CStdioFile` schreiben, wird das Bytepaar (0x0D, 0x0A) an die Datei gesendet. Wenn Sie lesen, wird das Bytepaar (0x0D, 0x0A) in ein einzelnes 0x0A-Byte übersetzt.

Die [CFile-Funktionen](../../mfc/reference/cfile-class.md) [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)und `CStdioFile` [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) werden für nicht unterstützt.

Wenn Sie diese Funktionen `CStdioFile`auf einem aufrufen, erhalten Sie eine [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Weitere Informationen zur `CStdioFile`Verwendung finden Sie in den Artikeln [Dateien in MFC](../../mfc/files-in-mfc.md) und [Dateiverarbeitung](../../c-runtime-library/file-handling.md) in der *Laufzeitbibliotheksreferenz*.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdioFile::CStdioDatei

Erstellt und initialisiert ein `CStdioFile`-Objekt.

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parameter

*pOpenStream*<br/>
Gibt den Dateizeiger an, der von einem Aufruf der C-Laufzeitfunktion [fopen](../../c-runtime-library/reference/fopen-wfopen.md)zurückgegeben wird.

*lpszFileName*<br/>
Gibt eine Zeichenfolge an, die den Pfad zur gewünschten Datei ist. Der Pfad kann relativ oder absolut sein.

*nOpenFlags*<br/>
Gibt Optionen für die Dateierstellung, Dateifreigabe und Dateizugriffsmodi an. Sie können mehrere Optionen angeben, indem **|** Sie den bitweisen Operator ODER ( ) verwenden.

Eine Dateizugriffsmodusoption ist erforderlich. andere Modi sind optional. Eine Liste der Modusoptionen und anderer Flags finden Sie unter [CFile::CFile.](../../mfc/reference/cfile-class.md#cfile) In MFC Version 3.0 und höher sind Freigabeflags zulässig.

*Ptm*<br/>
Zeiger auf das CAtlTransactionManager-Objekt.

### <a name="remarks"></a>Bemerkungen

Der Standardkonstruktor fügt keine Datei `CStdioFile` an das Objekt an. Wenn Sie diesen Konstruktor verwenden, müssen Sie die `CStdioFile::Open` Methode `CStdioFile` verwenden, um eine Datei zu öffnen und an das Objekt anzufügen.

Der Einzelparameterkonstruktor fügt dem `CStdioFile` Objekt einen geöffneten Dateistream an. Zu den zulässigen Zeigerwerten gehören die vordefinierten Eingabe-/Ausgabedateizeiger *stdin*, *stdout*oder *stderr*.

Der Konstruktor mit zwei `CStdioFile` Parametern erstellt ein Objekt und öffnet die entsprechende Datei mit dem angegebenen Pfad.

Wenn Sie NULL für *pOpenStream* oder *lpszFileName*übergeben, löst der Konstruktor eine `CInvalidArgException*`aus.

Wenn die Datei nicht geöffnet oder erstellt `CFileException*`werden kann, löst der Konstruktor eine aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a>CStdioFile::m_pStream

Das `m_pStream` Datenelement ist der Zeiger auf eine geöffnete Datei, `fopen`die von der C-Laufzeitfunktion zurückgegeben wird.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Bemerkungen

Es ist NULL, wenn die Datei nie geöffnet oder geschlossen wurde.

## <a name="cstdiofileopen"></a><a name="open"></a>CStdioFile::Öffnen

Ist überladen. Open ist für die `CStdioFile` Verwendung mit dem Standardkonstruktor konzipiert.

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
Eine Zeichenfolge, die den Pfad zur gewünschten Datei ist. Der Pfad kann relativ oder absolut sein.

*nOpenFlags*<br/>
Freigabe- und Zugriffsmodus. Gibt die Aktion an, die beim Öffnen der Datei zu ergreifen ist. Sie können Optionen kombinieren, indem Sie den Operator bitwise-OR (&#124;) verwenden. Eine Zugriffsberechtigung und eine Freigabeoption sind erforderlich. die Modi modeCreate und modeNoInherit sind optional.

*pError*<br/>
Ein Zeiger auf ein vorhandenes Dateiausnahmeobjekt, das den Status eines fehlgeschlagenen Vorgangs erhält.

*Ptm*<br/>
Zeiger auf `CAtlTransactionManager` ein Objekt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

## <a name="cstdiofilereadstring"></a><a name="readstring"></a>CStdioFile::ReadString

Liest Textdaten in einen Puffer bis zu einem Limit von *nMax* `CStdioFile` -1 Zeichen aus der Datei, die dem Objekt zugeordnet ist.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parameter

*lpsz*<br/>
Gibt einen Zeiger auf einen vom Benutzer bereitgestellten Puffer an, der eine null-terminierte Textzeichenfolge empfängt.

*nMax*<br/>
Gibt die maximale Anzahl der zu lesenden Zeichen an, ohne das beendende Nullzeichen zu zählen.

*rString*<br/>
Ein Verweis `CString` auf ein Objekt, das die Zeichenfolge enthält, wenn die Funktion zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Puffer, der die Textdaten enthält. NULL, wenn das Ende der Datei erreicht wurde, ohne Daten zu lesen; oder wenn boolesch, FALSE, wenn das Ende der Datei erreicht wurde, ohne Daten zu lesen.

### <a name="remarks"></a>Bemerkungen

Das Lesen wird durch das erste Zeilenumleinenzeichen gestoppt. Wenn in diesem Fall weniger als *nMax*-1 Zeichen gelesen wurden, wird ein Zeilenumzufolge im Puffer gespeichert. In beiden Fällen wird ein Nullzeichen (''''''''''''''''''''''''''''''''''''''''''

[CFile::Read](../../mfc/reference/cfile-class.md#read) ist auch für Textmodus-Eingaben verfügbar, endet jedoch nicht auf einem Wagen-Rücklaufpaar.

> [!NOTE]
> Die `CString` Version dieser Funktion `'\n'` entfernt die, wenn vorhanden; die LPTSTR-Version nicht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a>CStdioFile::Suchen

Positioniert den Zeiger in einer zuvor geöffneten Datei neu.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parameter

*lOff*<br/>
Anzahl der Bytes, um den Zeiger zu verschieben.

*nVon*<br/>
Zeigerbewegungsmodus. Dies muss einer der folgenden Werte sein:

- `CFile::begin`: Verschieben Sie den Dateizeiger *lOff* Bytes vom Anfang der Datei vorwärts.

- `CFile::current`: Verschieben Sie den Dateizeiger *lOff* Bytes von der aktuellen Position in der Datei.

- `CFile::end`: Verschieben Sie den Dateizeiger *lOff* Bytes vom Ende der Datei. Beachten Sie, dass *lOff* negativ sein muss, um in die vorhandene Datei zu suchen. positive Werte werden über das Ende der Datei hinaus gesucht.

### <a name="return-value"></a>Rückgabewert

Wenn die angeforderte `Seek` Position legal ist, gibt der neue Byteoffset vom Anfang der Datei zurück. Andernfalls ist der Rückgabewert nicht `CFileException` definiert, und ein Objekt wird ausgelöst.

### <a name="remarks"></a>Bemerkungen

Die `Seek` Funktion ermöglicht den zufälligen Zugriff auf den Inhalt einer Datei, indem der Zeiger einen bestimmten Betrag, absolut oder relativ, bewegt. Während der Suche werden keine Daten gelesen. Wenn die angeforderte Position größer als die Größe der Datei ist, wird die Dateilänge auf diese Position erweitert, und es wird keine Ausnahme ausgelöst.

Wenn eine Datei geöffnet wird, wird der Dateizeiger am Anfang der Datei, dem Anfang der Datei, positioniert.

Diese Implementierung `Seek` von basiert auf der Run-Time `fseek`Library (CRT)-Funktion . Es gibt mehrere Einschränkungen `Seek` für die Verwendung von Streams, die im Textmodus geöffnet werden. Weitere Informationen finden Sie unter [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie `Seek` Sie den Zeiger 1000 `cfile` Bytes vom Anfang der Datei verschieben. Beachten `Seek` Sie, dass keine Daten gelesen werden, daher müssen Sie anschließend [CStdioFile::ReadString](#readstring) aufrufen, um Daten zu lesen.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a>CStdioFile::WriteString

Schreibt Daten aus einem Puffer in `CStdioFile` die dem Objekt zugeordnete Datei.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parameter

*lpsz*<br/>
Gibt einen Zeiger auf einen Puffer an, der eine null-terminierte Zeichenfolge enthält.

### <a name="remarks"></a>Bemerkungen

Das beendende Nullzeichen ( `\0`) wird nicht in die Datei geschrieben. Diese Methode schreibt Zeilenzeilenzeichen in *lpsz* in die Datei als Wagen-Rücklauf-Feedpaar.

Wenn Sie Daten schreiben möchten, die nicht null-beendet `CStdioFile::Write` sind, verwenden Sie oder [CFile::Write](../../mfc/reference/cfile-class.md#write).

Diese Methode `CInvalidArgException*` löst eine aus, wenn Sie NULL für den *Parameter lpsz* angeben.

Diese Methode `CFileException*` löst eine Antwort auf Dateisystemfehler aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Siehe auch

[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException-Klasse](../../mfc/reference/cnotsupportedexception-class.md)
