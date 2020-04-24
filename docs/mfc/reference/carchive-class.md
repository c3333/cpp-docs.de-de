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
ms.openlocfilehash: ef8b6ec9060e8c15dd45f8203dadd2a2aca9e168
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753120"
---
# <a name="carchive-class"></a>CArchive-Klasse

Ermöglicht das Speichern eines komplexen Netzwerks von Objekten in einer permanenten binären Form (in der Regel Datenträgerspeicher), die nach dem Löschen dieser Objekte beibehalten wird.

## <a name="syntax"></a>Syntax

```
class CArchive
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Erstellt ein `CArchive` -Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArchive::Abbruch](#abort)|Schließt ein Archiv, ohne eine Ausnahme auszulösen.|
|[CArchive::Schließen](#close)|Löscht ungeschriebene Daten und `CFile`trennt die Verbindung zur .|
|[CArchive::Flush](#flush)|Löscht ungeschriebene Daten aus dem Archivpuffer.|
|[CArchive::GetFile](#getfile)|Ruft `CFile` den Objektzeiger für dieses Archiv ab.|
|[CArchive::GetObjectSchema](#getobjectschema)|Wird von `Serialize` der Funktion aufgerufen, um die Version des Objekts zu bestimmen, das deserialisiert wird.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Bestimmt, ob der Puffer während eines Windows Sockets-Empfangsprozesses geleert wurde.|
|[CArchive::IsLoading](#isloading)|Bestimmt, ob das Archiv geladen wird.|
|[CArchive::IsStoring](#isstoring)|Bestimmt, ob das Archiv gespeichert wird.|
|[CArchive::MapObject](#mapobject)|Platziert Objekte in der Karte, die nicht in die Datei serialisiert sind, aber für Unterobjekte verfügbar sind, auf die verwiesen werden kann.|
|[CArchive::Lesen](#read)|Liest unformatierte Bytes.|
|[CArchive::ReadClass](#readclass)|Liest einen Klassenverweis, `WriteClass`der zuvor mit gespeichert wurde.|
|[CArchive::ReadObject](#readobject)|Ruft die Funktion `Serialize` eines Objekts zum Laden auf.|
|[CArchive::ReadString](#readstring)|Liest eine einzelne Textzeile.|
|[CArchive::SerializeClass](#serializeclass)|Liest oder schreibt den `CArchive` Klassenverweis auf das `CArchive`Objekt in Abhängigkeit von der Richtung der .|
|[CArchive::SetLoadParams](#setloadparams)|Legt die Größe fest, auf die das Lastarray anwächst. Muss aufgerufen werden, bevor ein `MapObject` `ReadObject` Objekt geladen oder vor oder aufgerufen wird.|
|[CArchive::SetObjectSchema](#setobjectschema)|Legt das im Archivobjekt gespeicherte Objektschema fest.|
|[CArchive::SetStoreParams](#setstoreparams)|Legt die Größe der Hashtabelle und die Blockgröße der Karte fest, die zum Identifizieren eindeutiger Objekte während des Serialisierungsprozesses verwendet wird.|
|[CArchive::Schreiben](#write)|Schreibt unformatierte Bytes.|
|[CArchive::WriteClass](#writeclass)|Schreibt einen Verweis `CRuntimeClass` auf `CArchive`die .|
|[CArchive::WriteObject](#writeobject)|Ruft die Funktion `Serialize` eines Objekts zum Speichern auf.|
|[CArchive::WriteString](#writestring)|Schreibt eine einzelne Textzeile.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|Speichert Objekte und primitive Typen im Archiv.|
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|Lädt Objekte und primitive Typen aus dem Archiv.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Bemerkungen

`CArchive`hat keine Basisklasse.

Später können Sie die Objekte aus dem persistenten Speicher laden und sie im Speicher neu konstituieren. Dieser Prozess der Beständigung von Daten wird als "Serialisierung" bezeichnet.

Sie können sich ein Archivobjekt als eine Art binären Stream vorstellen. Wie ein Eingabe-/Ausgabestrom ist ein Archiv einer Datei zugeordnet und ermöglicht das gepufferte Schreiben und Lesen von Daten in und aus dem Speicher. Ein Eingabe-/Ausgabestream verarbeitet Sequenzen von ASCII-Zeichen, ein Archiv verarbeitet binäre Objektdaten jedoch in einem effizienten, nicht redundanten Format.

Sie müssen ein [CFile-Objekt](../../mfc/reference/cfile-class.md) erstellen, bevor Sie ein `CArchive` Objekt erstellen können. Darüber hinaus müssen Sie sicherstellen, dass der Lade-/Speicherstatus des Archivs mit dem geöffneten Modus der Datei kompatibel ist. Sie sind auf ein aktives Archiv pro Datei beschränkt.

Wenn Sie `CArchive` ein Objekt erstellen, fügen Sie `CFile` es an ein Objekt der Klasse (oder eine abgeleitete Klasse) an, das eine geöffnete Datei darstellt. Sie geben auch an, ob das Archiv zum Laden oder Speichern verwendet wird. Ein `CArchive` Objekt kann nicht nur primitive Typen verarbeiten, sondern auch Objekte von [CObject-abgeleiteten](../../mfc/reference/cobject-class.md)Klassen, die für die Serialisierung entwickelt wurden. Eine serialisierbare Klasse `Serialize` verfügt in der Regel über eine Memberfunktion und `CObject`verwendet in der Regel die [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) Makros, wie unter class beschrieben.

Die überladenen **>>** Extraktions- **<<**( ) und Insertionsoperatoren ( `CObject`) sind praktische Archivprogrammierschnittstellen, die sowohl primitive Typen als auch -abgeleitete Klassen unterstützen.

`CArchive`unterstützt auch die Programmierung mit den MFC Windows Sockets-Klassen [CSocket](../../mfc/reference/csocket-class.md) und [CSocketFile](../../mfc/reference/csocketfile-class.md). Die [IsBufferEmpty-Memberfunktion](#isbufferempty) unterstützt diese Verwendung.

Weitere Informationen `CArchive`zu finden Sie in den Artikeln [Serialisierung](../../mfc/serialization-in-mfc.md) und [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CArchive`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afx.h

## <a name="carchiveabort"></a><a name="abort"></a>CArchive::Abbruch

Rufen Sie diese Funktion auf, um das Archiv zu schließen, ohne eine Ausnahme auszulösen.

```cpp
void Abort ();
```

### <a name="remarks"></a>Bemerkungen

Der `CArchive` Destruktor `Close`ruft normalerweise auf, wodurch alle Daten, `CFile` die nicht im zugeordneten Objekt gespeichert wurden, gelöscht werden. Dies kann Zufällen verursachen.

Beim Abfangen dieser Ausnahmen ist es `Abort`eine gute Idee, `CArchive` zu verwenden, damit das Zerstören des Objekts keine weiteren Ausnahmen verursacht. Wenn Sie Ausnahmen `CArchive::Abort` behandeln, wird keine Ausnahme für Fehler ausgelöst, `Abort` da im Gegensatz zu [CArchive::Close](#close)Fehler ignoriert werden.

Wenn Sie **das** Objekt `CArchive` neu verwendet haben, um das Objekt auf dem Heap zuzuweisen, müssen Sie es nach dem Schließen der Datei löschen.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CArchive::WriteClass](#writeclass).

## <a name="carchivecarchive"></a><a name="carchive"></a>CArchive::CArchive

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
Ein Zeiger auf `CFile` das Objekt, das die endgültige Quelle oder das Ziel der persistenten Daten ist.

*nMode*<br/>
Ein Flag, das angibt, ob Objekte aus dem Archiv geladen oder in das Archiv gespeichert werden sollen. Der *nMode-Parameter* muss einen der folgenden Werte aufweisen:

- `CArchive::load`Lädt Daten aus dem Archiv. Erfordert `CFile` nur Leseberechtigung.

- `CArchive::store`Speichert Daten im Archiv. Erfordert `CFile` Schreibberechtigung.

- `CArchive::bNoFlushOnDelete`Verhindert, dass das `Flush` Archiv automatisch aufgerufen wird, wenn der Archivdestruktor aufgerufen wird. Wenn Sie dieses Flag festlegen, sind `Close` Sie dafür verantwortlich, explizit aufzurufen, bevor der Destruktor aufgerufen wird. Andernfalls werden Ihre Daten beschädigt.

*nBufSize*<br/>
Eine ganze Zahl, die die Größe des internen Dateipuffers in Bytes angibt. Beachten Sie, dass die Standardpuffergröße 4.096 Byte beträgt. Wenn Sie große Objekte routinemäßig archivieren, verbessern Sie die Leistung, wenn Sie eine größere Puffergröße verwenden, die ein Vielfaches der Dateipuffergröße ist.

*lpBuf*<br/>
Ein optionaler Zeiger auf einen vom Benutzer bereitgestellten Puffer der Größe *nBufSize*. Wenn Sie diesen Parameter nicht angeben, weist das Archiv einen Puffer aus dem lokalen Heap zu und gibt ihn frei, wenn das Objekt zerstört wird. Das Archiv gibt keinen vom Benutzer bereitgestellten Puffer frei.

### <a name="remarks"></a>Bemerkungen

Sie können diese Spezifikation nicht ändern, nachdem Sie das Archiv erstellt haben.

Sie dürfen `CFile` Vorgänge nicht verwenden, um den Status der Datei zu ändern, bis Sie das Archiv geschlossen haben. Ein solcher Vorgang schadet der Integrität des Archivs. Sie können während der Serialisierung jederzeit auf die Position des Dateizeigers zugreifen, indem Sie das Dateiobjekt des Archivs von der [GetFile-Memberfunktion](#getfile) abrufen und dann die Funktion [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) verwenden. Sie sollten [CArchive::Flush](#flush) aufrufen, bevor Sie die Position des Dateizeigers abrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>CArchive::Schließen

Löscht alle im Puffer verbleibenden Daten, schließt das Archiv und trennt das Archiv von der Datei.

```cpp
void Close();
```

### <a name="remarks"></a>Bemerkungen

Weitere Operationen im Archiv sind nicht zulässig. Nachdem Sie ein Archiv geschlossen haben, können Sie ein weiteres Archiv für dieselbe Datei erstellen oder die Datei schließen.

Die Memberfunktion `Close` stellt sicher, dass alle Daten aus dem Archiv in die Datei übertragen werden, und macht das Archiv nicht verfügbar. Um die Übertragung von der Datei auf das Speichermedium abzuschließen, müssen Sie `CFile` zuerst [CFile::Close](../../mfc/reference/cfile-class.md#close) verwenden und dann das Objekt zerstören.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CArchive::WriteString](#writestring).

## <a name="carchiveflush"></a><a name="flush"></a>CArchive::Flush

Erzwingt, dass alle im Archivpuffer verbleibenden Daten in die Datei geschrieben werden.

```cpp
void Flush();
```

### <a name="remarks"></a>Bemerkungen

Die Memberfunktion `Flush` stellt sicher, dass alle Daten aus dem Archiv in die Datei übertragen werden. Sie müssen [CFile::Close](../../mfc/reference/cfile-class.md#close) aufrufen, um die Übertragung von der Datei auf das Speichermedium abzuschließen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>CArchive::GetFile

Ruft `CFile` den Objektzeiger für dieses Archiv ab.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Rückgabewert

Ein konstanter Zeiger `CFile` auf das verwendete Objekt.

### <a name="remarks"></a>Bemerkungen

Sie müssen das Archiv `GetFile`vor der Verwendung von löschen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive::GetObjectSchema

Rufen Sie diese `Serialize` Funktion von der Funktion auf, um die Version des Objekts zu bestimmen, das derzeit deserialisiert wird.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Rückgabewert

Während der Deserialisierung wird die Version des zu lesenden Objekts gelesen.

### <a name="remarks"></a>Bemerkungen

Das Aufrufen dieser Funktion `CArchive` ist nur gültig, wenn das Objekt geladen wird ( [CArchive::IsLoading](#isloading) gibt einen Wert ungleich Null zurück). Es sollte der erste `Serialize` Aufruf in der Funktion sein und nur einmal aufgerufen werden. Ein Rückgabewert von ( UINT)-1 gibt an, dass die Versionsnummer unbekannt ist.

Eine `CObject`-abgeleitete Klasse kann VERSIONABLE_SCHEMA kombiniert (mit bitweisem **ODER**) mit der Schemaversion selbst (im IMPLEMENT_SERIAL Makro) verwenden, um ein "versionierbares Objekt" zu erstellen, d. h. ein Objekt, dessen `Serialize` Memberfunktion mehrere Versionen lesen kann. Die Standardframeworkfunktionalität (ohne VERSIONABLE_SCHEMA) besteht darin, eine Ausnahme auszulösen, wenn die Version nicht übereinstimmen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive::IsBufferEmpty

Rufen Sie diese Memberfunktion auf, um zu bestimmen, ob der interne Puffer des Archivobjekts leer ist.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Puffer des Archivs leer ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird zur Unterstützung der Programmierung mit `CSocketFile`der MFC Windows Sockets-Klasse bereitgestellt. Sie müssen es nicht für ein Archiv `CFile` verwenden, das einem Objekt zugeordnet ist.

Der Grund `IsBufferEmpty` für die Verwendung `CSocketFile` mit einem Archiv, das einem Objekt zugeordnet ist, ist, dass der Puffer des Archivs möglicherweise mehr als eine Nachricht oder einen Datensatz enthält. Nach dem Empfang einer `IsBufferEmpty` Nachricht sollten Sie eine Schleife steuern, die weiterhin Daten empfängt, bis der Puffer leer ist. Weitere Informationen finden Sie in der [Funktion Empfangen](../../mfc/reference/casyncsocket-class.md#receive) von Membern der Klasse `CAsyncSocket`, die zeigt, wie `IsBufferEmpty`.

Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="carchiveisloading"></a><a name="isloading"></a>CArchive::IsLoading

Bestimmt, ob das Archiv Daten lädt.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Archiv derzeit zum Laden verwendet wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird `Serialize` von den Funktionen der archivierten Klassen aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>CArchive::IsStoring

Bestimmt, ob das Archiv Daten speichert.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Archiv derzeit zum Speichern verwendet wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion wird `Serialize` von den Funktionen der archivierten Klassen aufgerufen.

Wenn `IsStoring` der Status eines Archivs ungleich Null ist, ist sein `IsLoading` Status 0 und umgekehrt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>CArchive::MapObject

Rufen Sie diese Memberfunktion auf, um Objekte in der Zuordnung zu platzieren, die nicht wirklich in die Datei serialisiert sind, aber für Unterobjekte verfügbar sind, auf die verwiesen werden kann.

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parameter

*Pob*<br/>
Ein konstanter Zeiger auf das zu speichernde Objekt.

### <a name="remarks"></a>Bemerkungen

Sie können z. B. ein Dokument nicht serialisieren, aber Sie würden die Elemente serialisieren, die Teil des Dokuments sind. Durch `MapObject`Aufrufen von erlauben Sie diesen Elementen oder Unterobjekten, auf das Dokument zu verweisen. Serialisierte Unterelemente können auch ihren *m_pDocument* Hintergrundzeiger serialisieren.

Sie können `MapObject` aufrufen, wenn Sie `CArchive` das Objekt speichern und laden. `MapObject`fügt das angegebene Objekt den internen `CArchive` Datenstrukturen hinzu, die vom Objekt während der Serialisierung und Deserialisierung verwaltet werden, aber im Gegensatz zu [ReadObject](#readobject) und [WriteObject](#writeobject)wird die Serialisierung für das Objekt nicht aufgeschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>CArchive::m_pDocument

Standardmäßig auf NULL festgelegt, kann `CDocument` dieser Zeiger auf einen auf `CArchive` alles festgelegt werden, was der Benutzer der Instanz möchte.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Bemerkungen

Eine häufige Verwendung dieses Zeigers besteht darin, allen Zustellobjekten zusätzliche Informationen über den Serialisierungsprozess zu übermitteln. Dies wird erreicht, indem der Zeiger `CDocument`mit dem Dokument (einer -abgeleiteten Klasse) initialisiert wird, das serialisiert wird, so dass Objekte innerhalb des Dokuments bei Bedarf auf das Dokument zugreifen können. Dieser Zeiger wird auch `COleClientItem` von Objekten während der Serialisierung verwendet.

Das Framework legt *m_pDocument* für das Dokument fest, das serialisiert wird, wenn ein Benutzer einen Befehl "Datei öffnen" oder "Speichern" ausgibt. Wenn Sie ein OLE-Containerdokument (Object Linking and Embedding) aus anderen Gründen als Datei öffnen oder Speichern serialisieren, müssen Sie *explizit m_pDocument*festlegen. Dies würden Sie z. B. beim Serialisieren eines Containerdokuments in die Zwischenablage tun.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;

Speichert das angegebene Objekt oder den primitiven Typ im Archiv.

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

Eine `CArchive` Referenz, die mehrere Einfügeoperatoren in einer einzelnen Zeile aktiviert.

### <a name="remarks"></a>Bemerkungen

Die letzten beiden oben genannten Versionen sind speziell für die Speicherung von 64-Bit-Ganzzahlen.

Wenn Sie das IMPLEMENT_SERIAL-Makro in Ihrer Klassenimplementierung verwendet `CObject` haben, `WriteObject`wird der Einfügeoperator für den geschützten . Diese Funktion ruft wiederum `Serialize` die Funktion der Klasse auf.

Der [CStringT-Einfügeoperator](../../atl-mfc-shared/reference/cstringt-class.md) (<<) unterstützt Diagnose-Dumping und Speicherung in einem Archiv.

### <a name="example"></a>Beispiel

In diesem Beispiel wird `CArchive` die Verwendung des Einfügeoperators << mit den Typen **int** und **long** veranschaulicht.

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Beispiel

In diesem Beispiel 2 `CArchive` wird die Verwendung `CStringT` des Einfügeoperators << mit dem Typ veranschaulicht.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;

Lädt das angegebene Objekt oder den primitiven Typ aus dem Archiv.

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

Eine `CArchive` Referenz, die mehrere Extraktionsoperatoren auf einer einzigen Leitung aktiviert.

### <a name="remarks"></a>Bemerkungen

Die letzten beiden oben genannten Versionen sind speziell zum Laden von 64-Bit-Ganzzahlen vorgesehen.

Wenn Sie das IMPLEMENT_SERIAL-Makro in Ihrer Klassenimplementierung verwendet `CObject` haben, `ReadObject` sind die Extraktionsoperatoren für den Aufruf der geschützten Funktion überlastet (mit einem Run-Time-Pointer ungleich Null). Diese Funktion ruft wiederum `Serialize` die Funktion der Klasse auf.

Der [CStringT-Extraktionsoperator](../../atl-mfc-shared/reference/cstringt-class.md) (>>) unterstützt das Laden aus einem Archiv.

### <a name="example"></a>Beispiel

In diesem Beispiel wird `CArchive` die Verwendung des Extraktionsoperators >> mit dem **Typ int** veranschaulicht.

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Beispiel

In diesem Beispiel wird `CArchive` die Verwendung \< der Einfüge- und Extraktionsoperatoren <und >> mit dem `CStringT` Typ veranschaulicht.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>CArchive::Lesen

Liest eine angegebene Anzahl von Bytes aus dem Archiv.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Zeiger auf einen vom Benutzer bereitgestellten Puffer, der die aus dem Archiv gelesenen Daten empfangen soll.

*nMax*<br/>
Eine ganzzahlige Datei ohne Vorzeichen, die die Anzahl der Bytes angibt, die aus dem Archiv gelesen werden sollen.

### <a name="return-value"></a>Rückgabewert

Eine ganzzahlige Datei ohne Vorzeichen, die die Anzahl der tatsächlich gelesenen Bytes enthält. Wenn der Rückgabewert kleiner als die angeforderte Anzahl ist, wurde das Ende der Datei erreicht. Für die End-of-File-Bedingung wird keine Ausnahme ausgelöst.

### <a name="remarks"></a>Bemerkungen

Das Archiv interpretiert die Bytes nicht.

Sie können `Read` die Memberfunktion `Serialize` in Ihrer Funktion verwenden, um gewöhnliche Strukturen zu lesen, die in Ihren Objekten enthalten sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>CArchive::ReadClass

Rufen Sie diese Memberfunktion auf, um einen Verweis auf eine Zuvor mit [WriteClass](#writeclass)gespeicherte Klasse zu lesen.

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parameter

*pClassRefRequested*<br/>
Ein Zeiger auf die [CRuntimeClass-Struktur,](../../mfc/reference/cruntimeclass-structure.md) die dem angeforderten Klassenverweis entspricht. Kann den Wert NULL haben.

*pSchema*<br/>
Ein Zeiger auf ein Schema der zuvor gespeicherten Laufzeitklasse.

*pObTag*<br/>
Eine Zahl, die auf das eindeutige Tag eines Objekts verweist. Wird intern von der Implementierung von [ReadObject](#readobject)verwendet. Nur für erweiterte Programmierung verfügbar gemacht; *pObTag* sollte normalerweise NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die [CRuntimeClass-Struktur.](../../mfc/reference/cruntimeclass-structure.md)

### <a name="remarks"></a>Bemerkungen

Wenn *pClassRefRequested* nicht `ReadClass` NULL ist, wird überprüft, ob die archivierten Klasseninformationen mit Ihrer Laufzeitklasse kompatibel sind. Wenn es nicht `ReadClass` kompatibel ist, wird eine [CArchiveException](../../mfc/reference/carchiveexception-class.md)ausgelöst.

Ihre Laufzeitklasse muss [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)verwenden. Andernfalls `ReadClass` wird eine [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)ausgelöst.

Wenn *pSchema* NULL ist, kann das Schema der gespeicherten Klasse durch Aufrufen von [CArchive::GetObjectSchema](#getobjectschema)abgerufen werden. <strong>\*</strong>Andernfalls enthält *pSchema* das Schema der zuvor gespeicherten Laufzeitklasse.

Sie können [SerializeClass](#serializeclass) `ReadClass`anstelle von verwenden, das sowohl das Lesen als auch das Schreiben des Klassenverweises verarbeitet.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CArchive::WriteClass](#writeclass).

## <a name="carchivereadobject"></a><a name="readobject"></a>CArchive::ReadObject

Liest Objektdaten aus dem Archiv und erstellt ein Objekt des entsprechenden Typs.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parameter

*pKlasse*<br/>
Ein konstanter Zeiger auf die [CRuntimeClass-Struktur,](../../mfc/reference/cruntimeclass-structure.md) der dem zu lesenden Objekt entspricht.

### <a name="return-value"></a>Rückgabewert

Ein [CObject-Zeiger,](../../mfc/reference/cobject-class.md) der mithilfe von [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)sicher in die richtige abgeleitete Klasse umgecastet werden muss.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise `CArchive` vom **>>** Fürser ( ) -Operator aufgerufen, der für einen [CObject-Zeiger](../../mfc/reference/cobject-class.md) überladen ist. `ReadObject`ruft wiederum die `Serialize` Funktion der archivierten Klasse auf.

Wenn Sie einen *pClass-Parameter* ungleich Null angeben, der vom [RUNTIME_CLASS-Makro](../../mfc/reference/run-time-object-model-services.md#runtime_class) abgerufen wird, überprüft die Funktion die Laufzeitklasse des archivierten Objekts. Dies setzt voraus, dass Sie das IMPLEMENT_SERIAL Makros bei der Implementierung der Klasse verwendet haben.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CArchive::WriteObject](#writeobject).

## <a name="carchivereadstring"></a><a name="readstring"></a>CArchive::ReadString

Rufen Sie diese Memberfunktion auf, um Textdaten `CArchive` aus der dem Objekt verknüpften Datei in einen Puffer zu lesen.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parameter

*rString*<br/>
Ein Verweis auf eine [CString,](../../atl-mfc-shared/reference/cstringt-class.md) die die resultierende Zeichenfolge enthält, nachdem sie aus der dem CArchive-Objekt zugeordneten Datei gelesen wurde.

*lpsz*<br/>
Gibt einen Zeiger auf einen vom Benutzer bereitgestellten Puffer an, der eine null-terminierte Textzeichenfolge empfängt.

*nMax*<br/>
Gibt die maximale Anzahl der zu lesenden Zeichen an. Sollte eine kleiner als die Größe des *lpsz-Puffers* sein.

### <a name="return-value"></a>Rückgabewert

In der Version, die BOOL zurückgibt, TRUE, wenn erfolgreich; FALSE sonst.

In der Version, `LPTSTR`die einen zurückgibt, ein Zeiger auf den Puffer, der die Textdaten enthält; NULL, wenn das Ende der Datei erreicht wurde.

### <a name="remarks"></a>Bemerkungen

In der Version der Memberfunktion mit dem Parameter *nMax* hält der Puffer bis zu einer Grenze von *nMax* - 1 Zeichen. Das Lesen wird durch ein Wagen-Rücklaufpaar angehalten. Nachgestellte Zeilenumreine werden immer entfernt. In beiden Fällen wird ein Nullzeichen (''''''''''''''''''''''''''''''''''''''''''

[CArchive::Read](#read) ist auch für Textmodus-Eingaben verfügbar, endet jedoch nicht bei einem Wagen-Rücklaufpaar.

### <a name="example"></a>Beispiel

  Siehe beispiel für [CArchive::WriteString](#writestring).

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>CArchive::SerializeClass

Rufen Sie diese Memberfunktion auf, wenn Sie die Versionsinformationen einer Basisklasse speichern und laden möchten.

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parameter

*pClassRef*<br/>
Ein Zeiger auf ein Laufzeitklassenobjekt für die Basisklasse.

### <a name="remarks"></a>Bemerkungen

`SerializeClass`liest oder schreibt den Verweis `CArchive` auf eine Klasse auf `CArchive`das Objekt, abhängig von der Richtung des . Verwenden `SerializeClass` Sie anstelle von [ReadClass](#readclass) und [WriteClass](#writeclass) als bequeme Möglichkeit zum Serialisieren von Basisklassenobjekten; `SerializeClass` erfordert weniger Code und weniger Parameter.

Wie `ReadClass` `SerializeClass` überprüft , ob die archivierten Klasseninformationen mit Ihrer Laufzeitklasse kompatibel sind. Wenn es nicht `SerializeClass` kompatibel ist, wird eine [CArchiveException](../../mfc/reference/carchiveexception-class.md)ausgelöst.

Ihre Laufzeitklasse muss [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)verwenden. Andernfalls `SerializeClass` wird eine [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)ausgelöst.

Verwenden [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) Sie das RUNTIME_CLASS-Makro, um den Wert für den Parameter *pRuntimeClass* abzurufen. Die Basisklasse muss das [IMPLEMENT_SERIAL-Makro](../../mfc/reference/run-time-object-model-services.md#implement_serial) verwendet haben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>CArchive::SetLoadParams

Rufen `SetLoadParams` Sie auf, wenn Sie `CObject`eine große Anzahl von -abgeleiteten Objekten aus einem Archiv lesen möchten.

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parameter

*nGrowBy*<br/>
Die minimale Anzahl von Elementsteckplätzen, die zugewiesen werden sollen, wenn eine Größenerhöhung erforderlich ist.

### <a name="remarks"></a>Bemerkungen

`CArchive`verwendet ein Ladearray, um Verweise auf im Archiv gespeicherte Objekte aufzulösen. `SetLoadParams`können Sie die Größe festlegen, auf die das Lastarray anwächst.

Sie dürfen `SetLoadParams` nicht aufrufen, nachdem ein Objekt geladen wurde oder nachdem [MapObject](#mapobject) oder [ReadObject](#readobject) aufgerufen wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive::SetObjectSchema

Rufen Sie diese Memberfunktion auf, um das im Archivobjekt gespeicherte Objektschema auf *nSchema*festzulegen.

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parameter

*nSchema*<br/>
Gibt das Schema des Objekts an.

### <a name="remarks"></a>Bemerkungen

Beim nächsten Aufruf von [GetObjectSchema](#getobjectschema) wird der in *nSchema*gespeicherte Wert zurückgegeben.

Verwendung `SetObjectSchema` für erweiterte Versionierung; Z. B. wenn Sie erzwingen möchten, dass `Serialize` eine bestimmte Version in einer Funktion einer abgeleiteten Klasse gelesen wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive::SetStoreParams

Verwenden `SetStoreParams` Sie diese Verwendung, wenn Sie eine große Anzahl von `CObject`-abgeleiteten Objekten in einem Archiv speichern.

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parameter

*nHashSize*<br/>
Die Größe der Hashtabelle für Schnittstellenzeigerzuordnungen. Sollte eine Primzahl sein.

*nBlockSize*<br/>
Gibt die Speicherzuweisungsgranularität zum Erweitern der Parameter an. Sollte eine Leistung von 2 für die beste Leistung sein.

### <a name="remarks"></a>Bemerkungen

`SetStoreParams`ermöglicht es Ihnen, die Hashtabellengröße und die Blockgröße der Karte festzulegen, die zum Identifizieren eindeutiger Objekte während des Serialisierungsprozesses verwendet wird.

Sie dürfen `SetStoreParams` nicht aufrufen, nachdem Objekte gespeichert wurden oder nachdem [MapObject](#mapobject) oder [WriteObject](#writeobject) aufgerufen wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>CArchive::Schreiben

Schreibt eine angegebene Anzahl von Bytes in das Archiv.

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parameter

*lpBuf*<br/>
Ein Zeiger auf einen vom Benutzer bereitgestellten Puffer, der die Daten enthält, die in das Archiv geschrieben werden sollen.

*nMax*<br/>
Eine ganze Zahl, die die Anzahl der Bytes angibt, die in das Archiv geschrieben werden sollen.

### <a name="remarks"></a>Bemerkungen

Das Archiv formatiert die Bytes nicht.

Sie können `Write` die Memberfunktion `Serialize` in Ihrer Funktion verwenden, um gewöhnliche Strukturen zu schreiben, die in Ihren Objekten enthalten sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>CArchive::WriteClass

Verwenden `WriteClass` Sie diese Möglichkeit, um die Versions- und Klasseninformationen einer Basisklasse während der Serialisierung der abgeleiteten Klasse zu speichern.

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parameter

*pClassRef*<br/>
Ein Zeiger auf die [CRuntimeClass-Struktur,](../../mfc/reference/cruntimeclass-structure.md) die dem angeforderten Klassenverweis entspricht.

### <a name="remarks"></a>Bemerkungen

`WriteClass`schreibt einen Verweis auf die [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) `CArchive`für die Basisklasse in die . Verwenden Sie [CArchive::ReadClass,](#readclass) um den Verweis abzurufen.

`WriteClass`überprüft, ob die archivierten Klasseninformationen mit Ihrer Laufzeitklasse kompatibel sind. Wenn es nicht `WriteClass` kompatibel ist, wird eine [CArchiveException](../../mfc/reference/carchiveexception-class.md)ausgelöst.

Ihre Laufzeitklasse muss [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) und [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)verwenden. Andernfalls `WriteClass` wird eine [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)ausgelöst.

Sie können [SerializeClass](#serializeclass) `WriteClass`anstelle von verwenden, das sowohl das Lesen als auch das Schreiben des Klassenverweises verarbeitet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>CArchive::WriteObject

Speichert die `CObject` angegebenen Dateien im Archiv.

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parameter

*Pob*<br/>
Ein konstanter Zeiger auf das zu speichernde Objekt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise `CArchive` vom **<<** Operator insertion `CObject`( ) aufgerufen, der für überladen ist. `WriteObject`ruft wiederum die `Serialize` Funktion der archivierten Klasse auf.

Sie müssen das IMPLEMENT_SERIAL-Makro verwenden, um die Archivierung zu aktivieren. `WriteObject`schreibt den ASCII-Klassennamen in das Archiv. Dieser Klassenname wird später während des Ladevorgangs überprüft. Ein spezielles Codierungsschema verhindert unnötige Duplizierungen des Klassennamens für mehrere Objekte der Klasse. Dieses Schema verhindert auch die redundante Speicherung von Objekten, die Ziele von mehr als einem Zeiger sind.

Die genaue Objektcodierungsmethode (einschließlich des Vorhandenseins des ASCII-Klassennamens) ist ein Implementierungsdetail und kann sich in zukünftigen Versionen der Bibliothek ändern.

> [!NOTE]
> Beenden Sie das Erstellen, Löschen und Aktualisieren aller Objekte, bevor Sie mit der Archivierung beginnen. Ihr Archiv wird beschädigt, wenn Sie die Archivierung mit der Objektänderung mischen.

### <a name="example"></a>Beispiel

Eine Definition der `CAge`Klasse finden Sie im Beispiel für [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>CArchive::WriteString

Verwenden Sie diese Memberfunktion, um Daten aus `CArchive` einem Puffer in die dem Objekt zugeordnete Datei zu schreiben.

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parameter

*lpsz*<br/>
Gibt einen Zeiger auf einen Puffer an, der eine null-terminierte Textzeichenfolge enthält.

### <a name="remarks"></a>Bemerkungen

Das beendende Nullzeichen ('''''' wird nicht in die Datei geschrieben; auch wird eine Neuezeile nicht automatisch geschrieben.

`WriteString`löst eine Ausnahme als Reaktion auf mehrere Bedingungen aus, einschließlich der Bedingung für den Datenträger voll.

`Write`ist ebenfalls verfügbar, aber anstatt ein Nullzeichen zu beenden, schreibt es die angeforderte Anzahl von Bytes in die Datei.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[CSocket-Klasse](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile-Klasse](../../mfc/reference/csocketfile-class.md)
