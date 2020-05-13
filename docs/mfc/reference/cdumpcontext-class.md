---
title: CDumpContext-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: e89bbc5f263dc9303140e43914619090109b8315
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753211"
---
# <a name="cdumpcontext-class"></a>CDumpContext-Klasse

Unterstützt die Darstellung gestreamter Diagnoseausgaben als Klartext.

## <a name="syntax"></a>Syntax

```
class CDumpContext
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|Erstellt ein `CDumpContext`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Dumpt das angegebene Element im hexadezimalen Format.|
|[CDumpContext::Flush](#flush)|Löscht alle Daten im Dumpkontextpuffer.|
|[CDumpContext::GetDepth](#getdepth)|Ruft eine ganze Zahl ab, die der Tiefe des Dumps entspricht.|
|[CDumpContext::HexDump](#hexdump)|Dumpt Bytes aus, die in einem Array im hexadezimalen Format enthalten sind.|
|[CDumpContext::SetDepth](#setdepth)|Legt die Tiefe des Dumps fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|Fügt Variablen und Objekte in den Dumpkontext ein.|

## <a name="remarks"></a>Bemerkungen

`CDumpContext`hat keine Basisklasse.

Sie können [afxDump](diagnostic-services.md#afxdump), `CDumpContext` ein vordeklariertes Objekt, für den größten Teil Ihres Dumpings verwenden. Das `afxDump` Objekt ist nur in der Debugversion der Microsoft Foundation-Klassenbibliothek verfügbar.

Mehrere [Speicherdiagnosedienste](../../mfc/reference/diagnostic-services.md) verwenden `afxDump` für ihre Ausgabe.

Unter der Windows-Umgebung wird die `afxDump` Ausgabe des vordefinierten `cerr` Objekts, konzeptionell ähnlich dem Stream, über die Windows-Funktion `OutputDebugString`an den Debugger weitergeleitet.

Die `CDumpContext` Klasse verfügt über **<<** einen überladenen Einfügeoperator ( ) für `CObject` Zeiger, der die Daten des Objekts abgibt. Wenn Sie ein benutzerdefiniertes Dumpformat für ein abgeleitetes Objekt benötigen, überschreiben Sie [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Die meisten Microsoft Foundation-Klassen implementieren eine überschriebene `Dump` Memberfunktion.

Klassen, die nicht `CObject`von `CString`abgeleitet `CTime`sind, z. B. `CTimeSpan`, und , verfügen über eigene überladene `CDumpContext` Einfügeoperatoren, wie häufig verwendete Strukturen wie , `CFileStatus` `CPoint`und `CRect`.

Wenn Sie die [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) oder [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) Makros in `CObject::Dump` der Implementierung Ihrer `CObject`Klasse verwenden, wird der Name der -derived-Klasse gedruckt. Andernfalls wird gedruckt. `CObject`

Die `CDumpContext` Klasse ist sowohl mit der Debug- als `Dump` auch mit der Release-Version der Bibliothek verfügbar, die Memberfunktion ist jedoch nur in der Debug-Version definiert. Verwenden Sie **#ifdef _DEBUG**  /  `#endif` Anweisungen, um `Dump` den Diagnosecode, einschließlich der benutzerdefinierten Memberfunktionen, in Klammern zu setzen.

Bevor Sie ein `CDumpContext` eigenes Objekt erstellen, müssen Sie ein `CFile` Objekt erstellen, das als Dumpziel dient.

Weitere Informationen `CDumpContext`zu finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDumpContext`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afx.h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext::CDumpContext

Erstellt ein Objekt `CDumpContext`der Klasse .

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parameter

*pFile*<br/>
Ein Zeiger auf `CFile` das Objekt, das das Dumpziel ist.

### <a name="remarks"></a>Bemerkungen

Das `afxDump` Objekt wird automatisch erstellt.

Schreiben Sie nicht `CFile` in den Basiswert, während der Dumpkontext aktiv ist. Andernfalls stören Sie die Dump. Unter der Windows-Umgebung wird die Ausgabe über die `OutputDebugString`Windows-Funktion an den Debugger weitergeleitet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::DumpAsHex

Dumpt den angegebenen Typ aus, der als hexadezimale Zahlen formatiert ist.

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein `CDumpContext`-Objekt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um das Element des angegebenen Typs als hexadezimale Zahl abzuladen. Um ein Array zu dumpen, rufen Sie [CDumpContext::HexDump](#hexdump)auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext::Flush

Erzwingt, dass alle in Puffern verbleibenden Daten in die Datei geschrieben werden, die an den Dumpkontext angefügt ist.

```cpp
void Flush();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext::GetDepth

Bestimmt, ob ein tiefes oder flaches Dump in Bearbeitung ist.

```
int GetDepth() const;
```

### <a name="return-value"></a>Rückgabewert

Die Tiefe des Dumps, wie durch `SetDepth`festgelegt.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [SetDepth](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext::HexDump

Dumpt ein Array von Bytes aus, die als hexadezimale Zahlen formatiert sind.

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parameter

*lpszLine*<br/>
Eine Zeichenfolge, die am Anfang einer neuen Zeile ausgegeben wird.

*pby*<br/>
Ein Zeiger auf einen Puffer, der die abzuladenden Bytes enthält.

*nBytes*<br/>
Die Anzahl der abzuladenden Bytes.

*nWidth*<br/>
Maximale Anzahl der pro Zeile gedumpten Bytes (nicht die Breite der Ausgabezeile).

### <a name="remarks"></a>Bemerkungen

Um einen einzelnen, bestimmten Elementtyp als hexadezimale Nummer zu verwerfen, rufen Sie [CDumpContext::DumpAsHex](#dumpashex)auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;

Gibt die angegebenen Daten an den Dumpkontext aus.

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>Rückgabewert

Ein `CDumpContext`-Verweis. Mithilfe des Rückgabewerts können Sie mehrere Einfügungen in eine einzelne Zeile des Quellcodes schreiben.

### <a name="remarks"></a>Bemerkungen

Der Einfügeoperator ist `CObject` für Zeiger sowie für die meisten primitiven Typen überlastet. Ein Zeiger auf das Zeichen führt zu einem Dump von Zeichenfolgeninhalten. ein Zeiger auf **void** führt nur zu einem hexadezimalen Dump der Adresse. Ein LONGLONG führt zu einem Dump einer 64-Bit-signierten Ganzzahl; Ein ULONGLONG führt zu einem Dump einer 64-Bit-Ganzzahl ohne Vorzeichen.

Wenn Sie das IMPLEMENT_DYNAMIC oder IMPLEMENT_SERIAL-Makro in der Implementierung Ihrer `CObject::Dump`Klasse verwenden, wird `CObject`der Einfügeoperator durch den Namen der -derived-Klasse gedruckt. Andernfalls wird gedruckt. `CObject` Wenn Sie die `Dump` Funktion der Klasse überschreiben, können Sie eine aussagekräftigere Ausgabe des Objektinhalts anstelle eines hexadezimalen Dumps bereitstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext::SetDepth

Legt die Tiefe für das Dump fest.

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parameter

*nNewDepth*<br/>
Der neue Tiefenwert.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einen primitiven `CObject` Typ oder einen einfachen Typ, der keine Zeiger auf andere Objekte enthält, absetzen, ist ein Wert von 0 ausreichend. Ein Wert größer als 0 gibt ein tiefes Dump an, bei dem alle Objekte rekursiv gedumpt werden. Beispielsweise werden durch ein tiefes Dump einer Auflistung alle Elemente der Auflistung abgeladen. Sie können andere spezifische Tiefenwerte in den abgeleiteten Klassen verwenden.

> [!NOTE]
> Zirkuläre Referenzen werden in tiefen Dumps nicht erkannt und können zu Endlosschleifen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)
