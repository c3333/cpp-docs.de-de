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
ms.openlocfilehash: 3a81e06586e6de14d57ce4c4de36dc30c73383f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212513"
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
|[CDumpContext:: CDumpContext](#cdumpcontext)|Erstellt ein `CDumpContext`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CDumpContext::D-Umschlag](#dumpashex)|Sichert das gekennzeichnete Element im Hexadezimal Format.|
|[CDumpContext:: Flush](#flush)|Leert alle Daten im Dumpkontext Puffer.|
|[CDumpContext:: gettiefe](#getdepth)|Ruft eine Ganzzahl ab, die der Tiefe des dumpbilds entspricht.|
|[CDumpContext:: Hexdump](#hexdump)|Sichert bytes, die in einem Array im Hexadezimal Format enthalten sind.|
|[CDumpContext:: settiefe](#setdepth)|Legt die Tiefe des dumpbilds fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDumpContext::-Operator&lt;&lt;](#operator_lt_lt)|Fügt Variablen und Objekte in den Dumpkontext ein.|

## <a name="remarks"></a>Bemerkungen

`CDumpContext`weist keine Basisklasse auf.

Für den größten Teil Ihres Dumpings können Sie [afxDump](diagnostic-services.md#afxdump)verwenden, ein vorab deklariertes `CDumpContext` Objekt. Das- `afxDump` Objekt ist nur in der Debugversion des Microsoft Foundation Class-Bibliothek verfügbar.

Einige der Speicher [Diagnosedienste](../../mfc/reference/diagnostic-services.md) verwenden `afxDump` für Ihre Ausgabe.

In der Windows-Umgebung wird die Ausgabe des vordefinierten `afxDump` Objekts, das dem Datenstrom konzeptionell ähnelt, `cerr` über die Windows-Funktion an den Debugger weitergeleitet `OutputDebugString` .

Die `CDumpContext` -Klasse verfügt über einen überladenen Einfügungs **<<** Operator () für `CObject` Zeiger, die die Daten des Objekts absichert. Wenn Sie ein benutzerdefiniertes dumpformat für ein abgeleitetes Objekt benötigen, überschreiben Sie [CObject::D UMP](../../mfc/reference/cobject-class.md#dump). Die meisten Microsoft Foundation-Klassen implementieren eine überschriebene `Dump` Member-Funktion.

Klassen, die nicht von abgeleitet sind `CObject` , wie z. b. `CString` , `CTime` und `CTimeSpan` , verfügen über eigene überladene `CDumpContext` einfügeoperatoren, wie häufig verwendete Strukturen wie z `CFileStatus` . b., `CPoint` und `CRect` .

Wenn Sie die [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) -oder [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) -Makro in der Implementierung der-Klasse verwenden, `CObject::Dump` wird der Name der von `CObject` abgeleiteten Klasse von gedruckt. Andernfalls wird sie gedruckt `CObject` .

Die `CDumpContext` -Klasse ist sowohl in der Debug-als auch in der Releaseversion der Bibliothek verfügbar, aber die `Dump` Member-Funktion ist nur in der Debugversion definiert. Verwenden Sie **#ifdef _DEBUG** -  /  `#endif` Anweisungen, um Ihren Diagnosecode zu Klammern, einschließlich Ihrer benutzerdefinierten Element `Dump` Funktionen.

Bevor Sie ein eigenes- `CDumpContext` Objekt erstellen, müssen Sie ein-Objekt erstellen, `CFile` das als dumpziel fungiert.

Weitere Informationen zu `CDumpContext` finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDumpContext`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext:: CDumpContext

Erstellt ein Objekt der-Klasse `CDumpContext` .

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Parameter

*pFile*<br/>
Ein Zeiger auf das- `CFile` Objekt, das das dumpziel ist.

### <a name="remarks"></a>Bemerkungen

Das `afxDump` Objekt wird automatisch erstellt.

Schreiben Sie nicht in den zugrunde liegenden, `CFile` während der Dumpkontext aktiv ist. andernfalls stören Sie die Sicherung. In der Windows-Umgebung wird die Ausgabe über die Windows-Funktion an den Debugger weitergeleitet `OutputDebugString` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::D-Umschlag

Sichert den angegebenen Typ, der als hexadezimale Zahlen formatiert ist.

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

Mit dieser Member-Funktion wird das Element des angegebenen Typs als hexadezimale Zahl gesichert. Zum Speichern eines Arrays wird [CDumpContext:: Hexdump](#hexdump)aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext:: Flush

Zwingt, dass alle in Puffern verbleibenden Daten in die Datei geschrieben werden, die an den Dumpkontext angefügt ist.

```cpp
void Flush();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext:: gettiefe

Bestimmt, ob ein tiefes oder flaches Abbild gerade verarbeitet wird.

```
int GetDepth() const;
```

### <a name="return-value"></a>Rückgabewert

Die Tiefe des Abbilds, wie von festgelegt `SetDepth` .

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [settiefe](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext:: Hexdump

Sichert ein Bytearray, das als hexadezimale Zahlen formatiert ist.

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Parameter

*lpszline*<br/>
Eine Zeichenfolge, die am Anfang einer neuen Zeile ausgegeben werden soll.

*PBY*<br/>
Ein Zeiger auf einen Puffer, der die abzurufenen Bytes enthält.

*nBytes*<br/>
Die Anzahl der abzurufenden bytes.

*nwidth*<br/>
Maximale Anzahl von Bytes, die pro Zeile (nicht die Breite der Ausgabezeile) gekippt werden.

### <a name="remarks"></a>Bemerkungen

Um einen einzelnen, bestimmten Elementtyp als hexadezimale Zahl zu sichern, nennen Sie [CDumpContext::D Umschlag](#dumpashex)-ID.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::-Operator&lt;&lt;

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

Ein `CDumpContext`-Verweis. Mithilfe des Rückgabewerts können Sie mehrere Einfügungen in einer einzelnen Zeile des Quellcodes schreiben.

### <a name="remarks"></a>Bemerkungen

Der einfügeoperator ist für `CObject` Zeiger und für die meisten primitiven Typen überladen. Ein Zeiger auf ein Zeichen führt zu einem Speicher Abbild von Zeichen folgen Inhalten. Ein Zeiger auf **`void`** führt zu einem hexadezimalen Abbild der Adresse. Ein Longlong führt zu einem Dump einer 64-Bit-Ganzzahl mit Vorzeichen. Ein ULONGLONG führt zu einem Dump einer 64-Bit-Ganzzahl ohne Vorzeichen.

Wenn Sie in der-Implementierung der-Klasse das IMPLEMENT_DYNAMIC-oder IMPLEMENT_SERIAL-Makro verwenden, druckt der einfügeoperator bis über `CObject::Dump` den Namen der von `CObject` abgeleiteten Klasse. Andernfalls wird sie gedruckt `CObject` . Wenn Sie die `Dump` Funktion der Klasse überschreiben, können Sie anstelle eines hexadezimalen dumpobjekts eine aussagekräftigere Ausgabe der Inhalte des Objekts bereitstellen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext:: settiefe

Legt die Tiefe für das Dump fest.

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Parameter

*nnewtiefe*<br/>
Der neue Tiefen Wert.

### <a name="remarks"></a>Bemerkungen

Wenn Sie einen primitiven Typ oder einen einfachen Typ `CObject` , der keine Zeiger auf andere Objekte enthält, absichern, genügt der Wert 0. Ein Wert größer als 0 gibt einen tiefen Speicher an, bei dem alle Objekte rekursiv abgehandelt werden. Beispielsweise werden bei einem Deep-Dump einer Auflistung alle Elemente der Auflistung gesichert. Sie können andere spezifische tiefen Werte in den abgeleiteten Klassen verwenden.

> [!NOTE]
> Zirkuläre Verweise werden in Deep Abbilder nicht erkannt und können zu unendlichen Schleifen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CFile-Klasse](../../mfc/reference/cfile-class.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)
