---
title: CArchive-Klasse
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: 3cf5c3b7a79e846928b5a7ee0af12a3324e141a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424626"
---
# <a name="carchive-class"></a>CArchive-Klasse

Ermöglicht das Speichern eines komplexen Netzwerks von Objekten in einer permanenten Binär Form (normalerweise Datenträger Speicher), die beibehalten wird, nachdem diese Objekte gelöscht wurden.

## <a name="syntax"></a>Syntax

```
class CArchive
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CArchive:: CArchive](#carchive)|Erstellt ein `CArchive`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CArchive:: Abort](#abort)|Schließt ein Archiv, ohne eine Ausnahme auszulösen.|
|[CArchive:: Close](#close)|Entleert ungeschriebene Daten und trennt die Verbindung mit dem `CFile`.|
|[CArchive:: Flush](#flush)|Leert ungeschriebene Daten aus dem Archiv Puffer.|
|[CArchive:: GetFile](#getfile)|Ruft den `CFile` Objekt Zeigers für dieses Archiv ab.|
|[CArchive:: GetObjectSchema](#getobjectschema)|Wird von der `Serialize` Funktion aufgerufen, um die Version des Objekts zu ermitteln, das deserialisiert wird.|
|[CArchive:: IsBufferEmpty](#isbufferempty)|Bestimmt, ob der Puffer während eines Windows Sockets-Empfangs Prozesses geleert wurde.|
|[CArchive:: isload](#isloading)|Bestimmt, ob das Archiv geladen wird.|
|[CArchive:: isspeichernde](#isstoring)|Bestimmt, ob das Archiv speichert.|
|[CArchive:: MapObject](#mapobject)|Platziert Objekte in der Zuordnung, die nicht in die Datei serialisiert sind, aber für untergeordnete Objekte verfügbar sind, auf die verwiesen werden soll.|
|[CArchive:: Read](#read)|Liest Rohdaten bytes.|
|[CArchive:: leserclass](#readclass)|Liest einen zuvor mit `WriteClass`gespeicherten Klassen Verweis.|
|[CArchive:: Read Object](#readobject)|Ruft die `Serialize` Funktion eines Objekts zum Laden auf.|
|[CArchive:: Read String](#readstring)|Liest eine einzelne Textzeile.|
|[CArchive:: serializeclass](#serializeclass)|Liest oder schreibt den Klassen Verweis in das `CArchive` Objekt, abhängig von der Richtung des `CArchive`.|
|[CArchive:: setloadparameendnisse](#setloadparams)|Legt die Größe fest, mit der das Lade Array wächst. Muss aufgerufen werden, bevor ein Objekt geladen wird, oder bevor `MapObject` oder `ReadObject` aufgerufen wird.|
|[CArchive:: eintobjectschema](#setobjectschema)|Legt das im Archive-Objekt gespeicherte Objekt Schema fest.|
|[CArchive:: setstoreparameams](#setstoreparams)|Legt die Hash Tabellengröße und die Blockgröße der Zuordnung fest, mit der während des Serialisierungsprozesses eindeutige Objekte identifiziert werden.|
|[CArchive:: Write](#write)|Schreibt Rohdaten bytes.|
|[CArchive:: schreiteclass](#writeclass)|Schreibt einen Verweis auf die `CRuntimeClass` in den `CArchive`.|
|[CArchive:: Write Object](#writeobject)|Ruft die `Serialize` Funktion eines Objekts zum Speichern auf.|
|[CArchive:: Write String](#writestring)|Schreibt eine einzelne Textzeile.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CArchive:: Operator &lt;&lt;](#operator_lt_lt)|Speichert-Objekte und primitive Typen im Archiv.|
|[CArchive:: Operator &gt;&gt;](#operator_gt_gt)|Lädt Objekte und primitive Typen aus dem Archiv.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CArchive:: m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Hinweise

`CArchive` verfügt nicht über eine Basisklasse.

Später können Sie die Objekte aus dem permanenten Speicher laden und diese im Arbeitsspeicher wiederherstellen. Dieser Vorgang zum persistenten Ausführen von Daten wird als "Serialisierung" bezeichnet.

Sie können sich ein Archiv Objekt als Art von binärem Stream vorstellen. Wie ein Eingabe-/Ausgabestream ist ein Archiv einer Datei zugeordnet und ermöglicht das gepufferte schreiben und Lesen von Daten in den und aus dem Speicher. Ein Eingabe-/Ausgabestream verarbeitet Sequenzen von ASCII-Zeichen, ein Archiv verarbeitet jedoch binäre Objektdaten in einem effizienten, nicht redundanten Format.

Sie müssen ein [CFile](../../mfc/reference/cfile-class.md) -Objekt erstellen, bevor Sie ein `CArchive` Objekt erstellen können. Außerdem müssen Sie sicherstellen, dass der Load/Store-Status des Archivs mit dem Öffnungs Modus der Datei kompatibel ist. Sie sind auf ein aktives Archiv pro Datei beschränkt.

Wenn Sie ein `CArchive` Objekt erstellen, fügen Sie es an ein Objekt der Klasse `CFile` (oder eine abgeleitete Klasse) an, das eine geöffnete Datei darstellt. Außerdem geben Sie an, ob das Archiv zum Laden oder Speichern verwendet werden soll. Ein `CArchive`-Objekt kann nicht nur primitive Typen, sondern auch Objekte von [CObject](../../mfc/reference/cobject-class.md)-abgeleiteten Klassen verarbeiten, die für die Serialisierung entwickelt wurden. Eine serialisierbare Klasse verfügt in der Regel über eine `Serialize` Member-Funktion und verwendet in der Regel die [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) Makros, wie Unterklassen `CObject`beschrieben.

Die überladenen Extraktions-( **>>** ) und einfügeoperatoren ( **<<** ) sind praktische Archivierungs Schnittstellen, die sowohl primitive als auch `CObject`abgeleitete Klassen unterstützen.

`CArchive` unterstützt auch das Programmieren mit den MFC-Windows Sockets-Klassen [CSocket](../../mfc/reference/csocket-class.md) und [CSocketFile](../../mfc/reference/csocketfile-class.md). Die Member-Funktion von [IsBufferEmpty](#isbufferempty) unterstützt diese Verwendung.

Weitere Informationen zu `CArchive`finden Sie in den Artikeln [Serialisierung](../../mfc/serialization-in-mfc.md) und [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CArchive`

## <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="abort"></a>CArchive:: Abort

Diese Funktion wird aufgerufen, um das Archiv zu schließen, ohne eine Ausnahme auszulösen.

```
void Abort ();
```

### <a name="remarks"></a>Hinweise

Der `CArchive` Dekonstruktor ruft normalerweise `Close`auf, der alle Daten leert, die nicht im zugeordneten `CFile` Objekt gespeichert wurden. Dies kann zu Ausnahmen führen.

Wenn Sie diese Ausnahmen abfangen, empfiehlt es sich, `Abort`zu verwenden, damit das defischen des `CArchive` Objekts keine weiteren Ausnahmen verursacht. Bei der Behandlung von Ausnahmen löst `CArchive::Abort` bei Fehlern keine Ausnahme aus, da im Gegensatz zum [CArchive:: Close](#close)-`Abort` Fehler ignoriert.

Wenn Sie **New** verwendet haben, um das `CArchive` Objekt auf dem Heap zuzuordnen, müssen Sie es nach dem Schließen der Datei löschen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CArchive:: Write Class](#writeclass).

##  <a name="carchive"></a>CArchive:: CArchive

Erstellt ein `CArchive` Objekt und gibt an, ob es zum Laden oder Speichern von Objekten verwendet wird.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parameter

*pFile*<br/>
Ein Zeiger auf das `CFile` Objekt, das die ultimative Quelle oder das ultimative Ziel der persistenten Daten ist.

*nmode*<br/>
Ein Flag, das angibt, ob Objekte aus dem Archiv geladen oder dort gespeichert werden. Der *nmode* -Parameter muss einen der folgenden Werte aufweisen:

- `CArchive::load` lädt Daten aus dem Archiv. Erfordert nur `CFile` Leseberechtigung.

- `CArchive::store` speichert Daten im Archiv. Erfordert `CFile` Schreib Berechtigung.

- `CArchive::bNoFlushOnDelete` verhindert, dass das Archiv automatisch `Flush` aufgerufen wird, wenn der Archivierungs Dekonstruktor aufgerufen wird. Wenn Sie dieses Flag festlegen, sind Sie dafür verantwortlich, `Close` explizit aufzurufen, bevor der Dekonstruktor aufgerufen wird. Wenn Sie dies nicht tun, werden Ihre Daten beschädigt.

*nbuf size*<br/>
Eine ganze Zahl, die die Größe des internen Datei Puffers in Bytes angibt. Beachten Sie, dass die Standardpuffergröße 4.096 Bytes beträgt. Wenn Sie regelmäßig große Objekte archivieren, verbessern Sie die Leistung, wenn Sie eine größere Puffergröße verwenden, bei der es sich um ein Vielfaches der Datei Puffergröße handelt.

*lpbuf*<br/>
Ein optionaler Zeiger auf einen vom Benutzer bereitgestellten Puffer der Größe *nbufsize*. Wenn Sie diesen Parameter nicht angeben, ordnet das Archiv einen Puffer aus dem lokalen Heap zu und gibt ihn frei, wenn das Objekt zerstört wird. Vom Archiv wird kein vom Benutzer bereitgestellter Puffer freigegeben.

### <a name="remarks"></a>Hinweise

Sie können diese Spezifikation nicht ändern, nachdem Sie das Archiv erstellt haben.

Sie dürfen `CFile` Vorgänge nicht verwenden, um den Status der Datei zu ändern, bis Sie das Archiv geschlossen haben. Bei einem solchen Vorgang wird die Integrität des Archivs beschädigt. Sie können während der Serialisierung jederzeit auf die Position des Dateizeigers zugreifen, indem Sie das Datei Objekt des Archivs aus der [GetFile](#getfile) -Member-Funktion abrufen und dann die [CFile:: GetPosition](../../mfc/reference/cfile-class.md#getposition) -Funktion verwenden. Vor dem Abrufen der Position des Dateizeigers sollten Sie [CArchive:: Flush](#flush) aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>CArchive:: Close

Leert alle Daten, die im Puffer verbleiben, schließt das Archiv und trennt die Verbindung des Archivs mit der Datei.

```
void Close();
```

### <a name="remarks"></a>Hinweise

Es sind keine weiteren Vorgänge für das Archiv zulässig. Nachdem Sie ein Archiv geschlossen haben, können Sie ein weiteres Archiv für dieselbe Datei erstellen, oder Sie können die Datei schließen.

Mit der Member-Funktion `Close` wird sichergestellt, dass alle Daten aus dem Archiv in die Datei übertragen werden, und das Archiv ist nicht verfügbar. Zum Abschließen der Übertragung von der Datei auf das Speichermedium müssen Sie zuerst [CFile:: Close](../../mfc/reference/cfile-class.md#close) verwenden und dann das `CFile` Objekt zerstören.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für " [CArchive:: Write String](#writestring)".

##  <a name="flush"></a>CArchive:: Flush

Erzwingt, dass alle im Archiv Puffer verbleibenden Daten in die Datei geschrieben werden.

```
void Flush();
```

### <a name="remarks"></a>Hinweise

Mit der Member-Funktion `Flush` wird sichergestellt, dass alle Daten aus dem Archiv in die Datei übertragen werden. Sie müssen [CFile:: Close](../../mfc/reference/cfile-class.md#close) abrufen, um die Übertragung von der Datei auf das Speichermedium abzuschließen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>CArchive:: GetFile

Ruft den `CFile` Objekt Zeigers für dieses Archiv ab.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Rückgabewert

Ein konstanter Zeiger auf das `CFile` Objekt, das verwendet wird.

### <a name="remarks"></a>Hinweise

Sie müssen das Archiv leeren, bevor Sie `GetFile`verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>CArchive:: GetObjectSchema

Diese Funktion wird von der `Serialize`-Funktion aufgerufen, um die Version des Objekts zu ermitteln, das gerade deserialisiert wird.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Rückgabewert

Die Version des gelesenen Objekts während der Deserialisierung.

### <a name="remarks"></a>Hinweise

Das Aufrufen dieser Funktion ist nur gültig, wenn das `CArchive` Objekt geladen wird ( [CArchive:: isload](#isloading) gibt einen Wert ungleich 0 zurück). Dies sollte der erste Aufruf in der `Serialize`-Funktion sein und nur einmal aufgerufen werden. Der Rückgabewert (uint)-1 gibt an, dass die Versionsnummer unbekannt ist.

Eine von `CObject`abgeleitete Klasse kann VERSIONABLE_SCHEMA kombiniert (mit bitweises **or**) mit der Schema Version selbst (im IMPLEMENT_SERIAL-Makro) verwenden, um ein "versionierbares Objekt" zu erstellen, d. h. ein Objekt, dessen `Serialize` Member-Funktion mehrere Versionen lesen kann. Die Standard Framework-Funktionalität (ohne VERSIONABLE_SCHEMA) besteht darin, eine Ausnahme auszulösen, wenn die Version nicht übereinstimmt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>CArchive:: IsBufferEmpty

Mit dieser Member-Funktion können Sie ermitteln, ob der interne Puffer des Archiv Objekts leer ist.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Puffer des Archivs leer ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion wird bereitgestellt, um die Programmierung mit der MFC-`CSocketFile`der Windows Sockets-Klasse zu unterstützen Sie müssen Sie nicht für ein Archiv verwenden, das einem `CFile` Objekt zugeordnet ist.

Der Grund für die Verwendung von `IsBufferEmpty` mit einem Archiv, das einem `CSocketFile`-Objekt zugeordnet ist, besteht darin, dass der Puffer des Archivs möglicherweise mehr als eine Nachricht oder einen Datensatz enthält. Nachdem eine Nachricht empfangen wurde, sollten Sie `IsBufferEmpty` verwenden, um eine Schleife zu steuern, die den Empfang von Daten fortsetzt, bis der Puffer leer ist. Weitere Informationen finden Sie in der Funktion zum [empfangen](../../mfc/reference/casyncsocket-class.md#receive) von Membern der Klasse `CAsyncSocket`, in der gezeigt wird, wie `IsBufferEmpty`verwendet wird.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isloading"></a>CArchive:: isload

Bestimmt, ob das Archivdaten lädt.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn das Archiv derzeit zum Laden verwendet wird. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird von den `Serialize` Funktionen der archivierten Klassen aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>CArchive:: isspeichernde

Bestimmt, ob das Archivdaten speichert.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn das Archiv derzeit zum Speichern verwendet wird. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion wird von den `Serialize` Funktionen der archivierten Klassen aufgerufen.

Wenn der `IsStoring` Status eines Archivs ungleich 0 (null) ist, lautet sein `IsLoading` Status 0 (null) und umgekehrt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>CArchive:: MapObject

Mit dieser Member-Funktion können Sie Objekte in der Zuordnung platzieren, die nicht wirklich in die Datei serialisiert sind, aber für untergeordnete Objekte verfügbar sind, auf die verwiesen werden soll.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parameter

*POB*<br/>
Ein konstanter Zeiger auf das Objekt, das gespeichert wird.

### <a name="remarks"></a>Hinweise

Beispielsweise können Sie ein Dokument nicht serialisieren, sondern die Elemente, die Teil des Dokuments sind, serialisieren. Wenn Sie `MapObject`aufrufen, können Sie zulassen, dass diese Elemente bzw. untergeordnete Elemente auf das Dokument verweisen. Außerdem können serialisierte unter Elemente Ihren *m_pDocument* zurück-Zeiger serialisieren.

Sie können `MapObject` beim Speichern in und laden aus dem `CArchive` Objekt aufzurufen. `MapObject` fügt dem internen Datenstruktur, die während der Serialisierung und Deserialisierung vom `CArchive`-Objekt verwaltet wird, das angegebene Objekt hinzu, aber im Gegensatz zu "read [Object](#readobject) " und " [Write-Object](#writeobject)" wird Serialisieren nicht für das Objekt aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>CArchive:: m_pDocument

Standardmäßig auf NULL festgelegt ist, kann dieser Zeiger auf einen `CDocument` auf alles festgelegt werden, was der Benutzer der `CArchive` Instanz möchte.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Hinweise

Diese Zeiger werden häufig verwendet, um allen Objekten, die serialisiert werden, zusätzliche Informationen über den Serialisierungsprozess zu vermitteln. Dies wird erreicht, indem der-Zeiger mit dem Dokument (eine `CDocument`abgeleitete Klasse) initialisiert wird, das serialisiert wird, sodass Objekte im Dokument bei Bedarf auf das Dokument zugreifen können. Dieser Zeiger wird auch von `COleClientItem` Objekten während der Serialisierung verwendet.

Das Framework legt *m_pDocument* auf das Dokument fest, das serialisiert wird, wenn ein Benutzer einen Befehl zum Öffnen oder Speichern von Dateien ausgibt. Wenn Sie ein Objekt Verknüpfungs-und Einbett Ende Container Dokument (OLE) für andere Gründe als Datei öffnen oder speichern serialisieren, müssen Sie *m_pDocument*explizit festlegen. Dies wäre z. b. der Fall, wenn Sie ein Container Dokument in die Zwischenablage serialisieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>CArchive:: Operator &lt;&lt;

Speichert das Objekt oder den primitiven Typ im Archiv.

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>Rückgabewert

Eine `CArchive` Referenz, die mehrere einfügeoperatoren in einer einzelnen Zeile ermöglicht.

### <a name="remarks"></a>Hinweise

Die letzten beiden oben aufgeführten Versionen dienen speziell zum Speichern von ganzen Zahlen mit 64 Bit.

Wenn Sie das IMPLEMENT_SERIAL-Makro in der Klassen Implementierung verwendet haben, ruft der einfügeoperator, der für `CObject` überladen wird, die geschützte `WriteObject`auf. Diese Funktion ruft wiederum die `Serialize`-Funktion der-Klasse auf.

Der [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) -einfügeoperator (< <) unterstützt das Ausgeben von Diagnosen und das Speichern in einem Archiv.

### <a name="example"></a>Beispiel

Dieses Beispiel veranschaulicht die Verwendung des `CArchive` einfügeoperators < < mit dem Typ " **int** " und " **Long** ".

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Beispiel

In diesem Beispiel 2 wird die Verwendung des `CArchive` einfügeoperators < < mit dem `CStringT`-Typ veranschaulicht.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>CArchive:: Operator &gt;&gt;

Lädt das Objekt oder den primitiven Typ aus dem Archiv.

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>Rückgabewert

Eine `CArchive` Referenz, die mehrere Extraktions Operatoren in einer einzelnen Zeile ermöglicht.

### <a name="remarks"></a>Hinweise

Die letzten beiden oben aufgeführten Versionen dienen speziell zum Laden von ganzen Zahlen mit 64 Bit.

Wenn Sie das IMPLEMENT_SERIAL-Makro in der Klassen Implementierung verwendet haben, werden die Extraktions Operatoren für `CObject` überladen, um die geschützte `ReadObject`-Funktion (mit einem Lauf Zeit Klassen Zeiger ungleich null) aufzurufen. Diese Funktion ruft wiederum die `Serialize`-Funktion der-Klasse auf.

Der [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) -Extraktions Operator (> >) unterstützt das Laden aus einem Archiv.

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Verwendung des `CArchive` Extraktions Operators > > mit dem **int** -Typ veranschaulicht.

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Beispiel

In diesem Beispiel wird die Verwendung der `CArchive` Einfügungs-und Extraktions Operatoren <\< und > > mit dem `CStringT`-Typ veranschaulicht.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>CArchive:: Read

Liest eine angegebene Anzahl von Bytes aus dem Archiv.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parameter

*lpbuf*<br/>
Ein Zeiger auf einen vom Benutzer bereitgestellten Puffer, der die aus dem Archiv gelesenen Daten empfangen soll.

*nMax*<br/>
Eine ganze Zahl ohne Vorzeichen, die die Anzahl der aus dem Archiv zu lesenden Bytes angibt.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl ohne Vorzeichen, die die Anzahl der tatsächlich gelesenen Bytes enthält. Wenn der Rückgabewert kleiner als die angeforderte Anzahl ist, wurde das Ende der Datei erreicht. Für die dateiendebedingung wird keine Ausnahme ausgelöst.

### <a name="remarks"></a>Hinweise

Das Archiv interpretiert die Bytes nicht.

Sie können die `Read` Member-Funktion innerhalb ihrer `Serialize`-Funktion verwenden, um gewöhnliche Strukturen zu lesen, die in den-Objekten enthalten sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>CArchive:: leserclass

Mit dieser Member-Funktion können Sie einen Verweis auf eine Klasse lesen, die zuvor mit " [Write-Class](#writeclass)" gespeichert wurde.

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parameter

*pclassrefrequessiert*<br/>
Ein Zeiger auf die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur, die dem angeforderten Klassen Verweis entspricht. Kann NULL sein.

*pschema*<br/>
Ein Zeiger auf ein Schema der zuvor gespeicherten Lauf Zeit Klasse.

*pobtag*<br/>
Eine Zahl, die auf das eindeutige Tag eines Objekts verweist. Wird intern von der-Implementierung von "read [Object](#readobject)" verwendet. Nur für erweiterte Programmierung verfügbar. *pobtag* sollte normalerweise NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur.

### <a name="remarks"></a>Hinweise

Wenn *pclassrefrequessiert* nicht NULL ist, überprüft `ReadClass`, ob die archivierten Klassen Informationen mit Ihrer Lauf Zeit Klasse kompatibel sind. Wenn Sie nicht kompatibel ist, wird `ReadClass` eine [carchiveexception](../../mfc/reference/carchiveexception-class.md)auslösen.

Die Lauf Zeit Klasse muss [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)verwenden; Andernfalls wird `ReadClass` eine [cnotsupportedexception](../../mfc/reference/cnotsupportedexception-class.md)auslösen.

Wenn *pschema* NULL ist, kann das Schema der gespeicherten Klasse abgerufen werden, indem [CArchive:: GetObjectSchema](#getobjectschema); aufgerufen wird. Andernfalls enthält <strong>\*</strong> *pschema* das Schema der zuvor gespeicherten Lauf Zeit Klasse.

Sie können [serializeclass](#serializeclass) anstelle von `ReadClass`verwenden, das sowohl das Lesen als auch das Schreiben des Klassen Verweises behandelt.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CArchive:: Write Class](#writeclass).

##  <a name="readobject"></a>CArchive:: Read Object

Liest Objektdaten aus dem Archiv und erstellt ein Objekt des entsprechenden Typs.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parameter

*pclass*<br/>
Ein konstanter Zeiger auf die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur, die dem Objekt entspricht, das Sie lesen möchten.

### <a name="return-value"></a>Rückgabewert

Ein [CObject](../../mfc/reference/cobject-class.md) -Zeiger, der mithilfe von [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)sicher in die richtige abgeleitete Klasse umgewandelt werden muss.

### <a name="remarks"></a>Hinweise

Diese Funktion wird normalerweise vom `CArchive` Extraktions Operator ( **>>** ) aufgerufen, der für einen [CObject](../../mfc/reference/cobject-class.md) -Zeiger überladen ist. `ReadObject`wiederum die `Serialize`-Funktion der archivierten Klasse aufruft.

Wenn Sie einen *pClass* -Parameter ungleich 0 angeben, der vom [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) -Makro abgerufen wird, überprüft die Funktion die Lauf Zeit Klasse des archivierten Objekts. Dabei wird davon ausgegangen, dass Sie das IMPLEMENT_SERIAL-Makro in der Implementierung der-Klasse verwendet haben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CArchive:: Write Object](#writeobject).

##  <a name="readstring"></a>CArchive:: Read String

Mit dieser Member-Funktion können Sie Textdaten aus der Datei, die dem `CArchive` Objekt zugeordnet ist, in einen Puffer einlesen.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parameter

*RString*<br/>
Ein Verweis auf ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt, das die resultierende Zeichenfolge enthält, nachdem es aus der Datei gelesen wurde, die dem CArchive-Objekt zugeordnet ist.

*lpsz*<br/>
Gibt einen Zeiger auf einen vom Benutzer bereitgestellten Puffer an, der eine NULL-terminierte Text Zeichenfolge empfängt.

*nMax*<br/>
Gibt die maximale Anzahl der zu lesenden Zeichen an. Sollte eins kleiner als die Größe des *lpsz* -Puffers sein.

### <a name="return-value"></a>Rückgabewert

In der Version, die bool zurückgibt, true, wenn erfolgreich; Andernfalls false.

In der Version, die eine `LPTSTR`zurückgibt, ein Zeiger auf den Puffer, der die Textdaten enthält. NULL, wenn das Dateiende erreicht wurde.

### <a name="remarks"></a>Hinweise

In der-Version der Member-Funktion mit dem *nmax* -Parameter hält der Puffer bis zu einem Limit von *nmax* -1 Zeichen. Lesevorgänge werden von einem Wagen Rücklauf-Zeilenvorschub Paar beendet. Nachfolgende Zeilenumbruch Zeichen werden immer entfernt. In jedem Fall wird ein NULL-Zeichen (' \ 0 ') angefügt.

[CArchive:: Read](#read) ist auch für textmoduseingaben verfügbar, wird jedoch nicht bei einem Wagen Rücklauf/Zeilenvorschub-Paar beendet.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für " [CArchive:: Write String](#writestring)".

##  <a name="serializeclass"></a>CArchive:: serializeclass

Wenn Sie die Versionsinformationen einer Basisklasse speichern und laden möchten, wird diese Member-Funktion aufgerufen.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parameter

*pclassref*<br/>
Ein Zeiger auf ein Lauf Zeit Klassenobjekt für die Basisklasse.

### <a name="remarks"></a>Hinweise

`SerializeClass` in Abhängigkeit von der Richtung des `CArchive`den Verweis auf eine Klasse in das `CArchive` Objekt liest oder schreibt. Verwenden Sie `SerializeClass` anstelle von "read [Class](#readclass) " und " [Write-Class](#writeclass) " als bequeme Methode zum Serialisieren von Basisklassen Objekten. `SerializeClass` erfordert weniger Code und weniger Parameter.

Wie `ReadClass`überprüft `SerializeClass`, ob die archivierten Klassen Informationen mit Ihrer Lauf Zeit Klasse kompatibel sind. Wenn Sie nicht kompatibel ist, wird `SerializeClass` eine [carchiveexception](../../mfc/reference/carchiveexception-class.md)auslösen.

Die Lauf Zeit Klasse muss [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)verwenden; Andernfalls wird `SerializeClass` eine [cnotsupportedexception](../../mfc/reference/cnotsupportedexception-class.md)auslösen.

Verwenden Sie das [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) -Makro, um den Wert für den *pruntimeclass* -Parameter abzurufen. Die Basisklasse muss das [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) -Makro verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>CArchive:: setloadparameendnisse

Ruft `SetLoadParams` auf, wenn Sie eine große Anzahl von `CObject`abgeleiteten Objekten aus einem Archiv lesen möchten.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parameter

*ngrowby*<br/>
Die Mindestanzahl der zuzuordnenden Element Slots, wenn eine Größen Erhöhung erforderlich ist.

### <a name="remarks"></a>Hinweise

`CArchive` verwendet ein Load-Array zum Auflösen von Verweisen auf Objekte, die im Archiv gespeichert sind. mit `SetLoadParams` können Sie die Größe festlegen, bis zu der das Lade Array wächst.

Sie dürfen `SetLoadParams` nicht aufrufen, nachdem ein Objekt geladen wurde, oder nachdem [MapObject oder '](#mapobject) Read [Object](#readobject) ' aufgerufen wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>CArchive:: eintobjectschema

Mit dieser Member-Funktion wird das im Archive-Objekt gespeicherte Objekt Schema auf *nschema*festgelegt.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parameter

*nschema*<br/>
Gibt das Schema des Objekts an.

### <a name="remarks"></a>Hinweise

Der nächste Aufrufen von [GetObjectSchema](#getobjectschema) gibt den in *nschema*gespeicherten Wert zurück.

Verwenden von `SetObjectSchema` für die erweiterte Versionsverwaltung beispielsweise, wenn Sie erzwingen möchten, dass eine bestimmte Version in einer `Serialize` Funktion einer abgeleiteten Klasse gelesen wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>CArchive:: setstoreparameams

Verwenden Sie `SetStoreParams`, wenn Sie eine große Anzahl `CObject`abgeleiteter Objekte in einem Archiv speichern.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parameter

*nhashsize*<br/>
Die Größe der Hash Tabelle für Schnittstellen Zeiger Zuordnungen. Sollte eine Primzahl sein.

*nblocksize*<br/>
Gibt die Speicher Belegungs Granularität für die Erweiterung der Parameter an. Muss eine Potenz von 2 sein, um die bestmögliche Leistung zu erzielen.

### <a name="remarks"></a>Hinweise

mit `SetStoreParams` können Sie die Hash Tabellengröße und die Blockgröße der Zuordnung festlegen, mit der während des Serialisierungsprozesses eindeutige Objekte identifiziert werden.

Sie dürfen `SetStoreParams` nicht aufrufen, nachdem Objekte gespeichert wurden, oder nachdem [MapObject](#mapobject) oder [Write-Object](#writeobject) aufgerufen wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>CArchive:: Write

Schreibt eine angegebene Anzahl von Bytes in das Archiv.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parameter

*lpbuf*<br/>
Ein Zeiger auf einen vom Benutzer bereitgestellten Puffer, der die Daten enthält, die in das Archiv geschrieben werden sollen.

*nMax*<br/>
Eine ganze Zahl, die die Anzahl der in das Archiv zu schreibenden Bytes angibt.

### <a name="remarks"></a>Hinweise

Das Archiv formatiert die Bytes nicht.

Sie können die `Write` Member-Funktion innerhalb ihrer `Serialize`-Funktion verwenden, um gewöhnliche Strukturen zu schreiben, die in ihren-Objekten enthalten sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>CArchive:: schreiteclass

Verwenden Sie `WriteClass`, um die Versions-und Klassen Informationen einer Basisklasse während der Serialisierung der abgeleiteten Klasse zu speichern.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parameter

*pclassref*<br/>
Ein Zeiger auf die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur, die dem angeforderten Klassen Verweis entspricht.

### <a name="remarks"></a>Hinweise

`WriteClass` schreibt einen Verweis auf die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) für die Basisklasse in die `CArchive`. Verwenden Sie [CArchive:: Read Class](#readclass) zum Abrufen des Verweises.

`WriteClass` überprüft, ob die archivierten Klassen Informationen mit Ihrer Lauf Zeit Klasse kompatibel sind. Wenn Sie nicht kompatibel ist, wird `WriteClass` eine [carchiveexception](../../mfc/reference/carchiveexception-class.md)auslösen.

Die Lauf Zeit Klasse muss [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)verwenden; Andernfalls wird `WriteClass` eine [cnotsupportedexception](../../mfc/reference/cnotsupportedexception-class.md)auslösen.

Sie können [serializeclass](#serializeclass) anstelle von `WriteClass`verwenden, das sowohl das Lesen als auch das Schreiben des Klassen Verweises behandelt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>CArchive:: Write Object

Speichert die angegebene `CObject` in das Archiv.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parameter

*POB*<br/>
Ein konstanter Zeiger auf das Objekt, das gespeichert wird.

### <a name="remarks"></a>Hinweise

Diese Funktion wird normalerweise vom `CArchive` Einfügungs Operator ( **<<** ) aufgerufen, der für `CObject`überladen ist. `WriteObject`wiederum die `Serialize`-Funktion der archivierten Klasse aufruft.

Sie müssen das IMPLEMENT_SERIAL-Makro verwenden, um die Archivierung zu aktivieren. `WriteObject` schreibt den ASCII-Klassennamen in das Archiv. Dieser Klassenname wird später während des Ladevorgangs überprüft. Ein spezielles Codierungsschema verhindert unnötige Duplizierung des Klassen namens für mehrere Objekte der Klasse. Dieses Schema verhindert auch die redundante Speicherung von Objekten, die Ziele von mehr als einem Zeiger sind.

Die genaue Objekt Codierungsmethode (einschließlich des Vorhandenseins des ASCII-Klassen namens) ist ein Implementierungsdetail, das in zukünftigen Versionen der Bibliothek geändert werden kann.

> [!NOTE]
>  Beenden Sie das Erstellen, löschen und Aktualisieren aller Objekte, bevor Sie beginnen, Sie zu archivieren. Das Archiv wird beschädigt, wenn Sie die Archivierung mit Objektänderungen mischen.

### <a name="example"></a>Beispiel

Eine Definition der-Klasse `CAge`finden Sie im Beispiel für [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>CArchive:: Write String

Verwenden Sie diese Member-Funktion, um Daten aus einem Puffer in die Datei zu schreiben, die mit dem `CArchive` Objekt verknüpft ist.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parameter

*lpsz*<br/>
Gibt einen Zeiger auf einen Puffer an, der eine NULL terminierte Text Zeichenfolge enthält.

### <a name="remarks"></a>Hinweise

Das abschließende Null Zeichen (' \ 0 ') wird nicht in die Datei geschrieben. Es wird auch kein Zeilen Vorstrich automatisch geschrieben.

`WriteString` löst eine Ausnahme als Reaktion auf verschiedene Bedingungen aus, einschließlich des Datenträger-vollständigen Zustands.

`Write` ist ebenfalls verfügbar, aber anstatt bei einem NULL-Zeichen zu beenden, schreibt es die angeforderte Anzahl von Bytes in die Datei.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[CSocket-Klasse](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile-Klasse](../../mfc/reference/csocketfile-class.md)
