---
title: CSimpleStringT-Klasse
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: dce33289699b9e7b7484d1feb6335476f93dee9b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317685"
---
# <a name="csimplestringt-class"></a>CSimpleStringT-Klasse

Diese Klasse `CSimpleStringT` stellt ein Objekt dar.

## <a name="syntax"></a>Syntax

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parameter

*BaseType*<br/>
Der Zeichentyp der Zeichenfolgenklasse. Dabei kann es sich um eine der folgenden Methoden handeln:

- **char** (für ANSI-Zeichenfolgen).

- **wchar_t** (für Unicode-Zeichenfolgen).

- TCHAR (für ANSI- und Unicode-Zeichenfolgen).

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Ein Zeiger auf eine konstante Zeichenfolge.|
|[CSimpleStringT::PXSTR](#pxstr)|Ein Zeiger auf eine Zeichenfolge.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Erstellt `CSimpleStringT` Objekte auf verschiedene Weise.|
|[CSimpleStringT::'csimplestringt](#dtor)|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleStringT::Anfügen](#append)|Fügt ein `CSimpleStringT` Objekt an `CSimpleStringT` ein vorhandenes Objekt an.|
|[CSimpleStringT::AppendChar](#appendchar)|Fügt ein Zeichen an `CSimpleStringT` ein vorhandenes Objekt an.|
|[CSimpleStringT::CopyChars](#copychars)|Kopiert ein Zeichen oder Zeichen in eine andere Zeichenfolge.|
|[CSimpleStringT::CopyCharsÜberlappend](#copycharsoverlapped)|Kopiert ein Zeichen oder Zeichen in eine andere Zeichenfolge, in der sich die Puffer überlappen.|
|[CSimpleStringT::Leer](#empty)|Erzwingt, dass eine Zeichenfolge eine Länge von Null hat.|
|[CSimpleStringT::FreeExtra](#freeextra)|Gibt zusätzlichen Speicher frei, der zuvor vom Zeichenfolgenobjekt zugewiesen wurde.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Ruft die zugewiesene `CSimpleStringT` Länge eines Objekts ab.|
|[CSimpleStringT::Getat](#getat)|Gibt das Zeichen an einer bestimmten Position zurück.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Gibt einen Zeiger auf die `CSimpleStringT`Zeichen in einer zurück.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Gibt einen Zeiger auf die `CSimpleStringT`Zeichen in einem zurück, der auf die angegebene Länge abgeschnitten wird.|
|[CSimpleStringT::GetLength](#getlength)|Gibt die Anzahl der `CSimpleStringT` Zeichen in einem Objekt zurück.|
|[CSimpleStringT::GetManager](#getmanager)|Ruft den Speicher-Manager `CSimpleStringT` des Objekts ab.|
|[CSimpleStringT::GetString](#getstring)|Ruft die Zeichenfolge ab|
|[CsimpleStringt::IsEmpty](#isempty)|Testet, `CSimpleStringT` ob ein Objekt keine Zeichen enthält.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Deaktiviert die Verweiszählung und schützt die Zeichenfolge im Puffer.|
|[CSimpleStringT::Pzuteilung](#preallocate)|Weist eine bestimmte Speichermenge für den Zeichenpuffer zu.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Gibt die Steuerung des `GetBuffer`Puffers frei, der von zurückgegeben wird.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Gibt die Steuerung des `GetBuffer`Puffers frei, der von zurückgegeben wird.|
|[CSimpleStringT::Setat](#setat)|Legt ein Zeichen an einer bestimmten Position fest.|
|[CSimpleStringT::SetManager](#setmanager)|Legt den Speicher-Manager eines `CSimpleStringT` Objekts fest.|
|[CSimpleStringT::SetString](#setstring)|Legt die Zeichenfolge `CSimpleStringT` eines Objekts fest.|
|[CSimpleStringT::StringLength](#stringlength)|Gibt die Anzahl der Zeichen in der angegebenen Zeichenfolge zurück.|
|[CSimpleStringT::Truncate](#truncate)|Kürt die Zeichenfolge auf eine angegebene Länge.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Aktiviert die Referenzzählung und gibt die Zeichenfolge im Puffer frei.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Greift direkt auf Zeichen `CSimpleStringT` zu, die in einem Objekt als Zeichenfolge im C-Stil gespeichert sind.|
|[CSimpleStringT::operator\[\]](#operator_at)|Gibt das Zeichen an einer bestimmten `GetAt`Position zurück – Operatorerersetzung für .|
|[CSimpleStringT::operator +=](#operator_add_eq)|Verkettet eine neue Zeichenfolge am Ende einer vorhandenen Zeichenfolge.|
|[CSimpleStringT::operator =](#operator_eq)|Weist einem `CSimpleStringT` Objekt einen neuen Wert zu.|

### <a name="remarks"></a>Bemerkungen

`CSimpleStringT`ist die Basisklasse für die verschiedenen Zeichenfolgenklassen, die von Visual C++ unterstützt werden. Es bietet minimale Unterstützung für die Speicherverwaltung des Zeichenfolgenobjekts und grundlegende Puffermanipulation. Weitere erweiterte Zeichenfolgenobjekte finden Sie unter [CStringT-Klasse](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpstr.h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT::Anfügen

Fügt ein `CSimpleStringT` Objekt an `CSimpleStringT` ein vorhandenes Objekt an.

### <a name="syntax"></a>Syntax

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parameter

*strSrc*<br/>
Das `CSimpleStringT` anzuhängende Objekt.

*pszSrc*<br/>
Ein Zeiger auf eine Zeichenfolge, die die anzuhängenden Zeichen enthält.

*nLänge*<br/>
Die Anzahl der anzufügenden Zeichen.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode `CSimpleStringT` auf, `CSimpleStringT` um ein vorhandenes Objekt an ein anderes Objekt anzuhängen.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::AppendChar

Fügt ein Zeichen an `CSimpleStringT` ein vorhandenes Objekt an.

### <a name="syntax"></a>Syntax

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parameter

*Ch*<br/>
Das anzuhängende Zeichen

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um das `CSimpleStringT` angegebene Zeichen an das Ende eines vorhandenen Objekts anzuhängen.

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars

Kopiert ein Zeichen oder `CSimpleStringT` Zeichen in ein Objekt.

### <a name="syntax"></a>Syntax

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parameter

*pchDest*<br/>
Ein Zeiger auf eine Zeichenfolge.

*pchSrc*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu kopierenden Zeichen enthält.

*nChars*<br/>
Die Anzahl der zu kopierenden *pchSrc-Zeichen.*

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um Zeichen aus *pchSrc* in die *pchDest-Zeichenfolge* zu kopieren.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsÜberlappend

Kopiert ein Zeichen oder `CSimpleStringT` Zeichen in ein Objekt.

### <a name="syntax"></a>Syntax

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parameter

*pchDest*<br/>
Ein Zeiger auf eine Zeichenfolge.

*pchSrc*<br/>
Ein Zeiger auf eine Zeichenfolge, die die zu kopierenden Zeichen enthält.

*nChars*<br/>
Die Anzahl der zu kopierenden *pchSrc-Zeichen.*

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um Zeichen aus *pchSrc* in die *pchDest-Zeichenfolge* zu kopieren. Im `CopyChars` `CopyCharsOverlapped` Gegensatz zu bietet eine sichere Methode zum Kopieren aus Zeichenpuffern, die möglicherweise überlappen.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [CSimpleStringT::CopyChars](#copychars), `CSimpleStringT::SetString` oder den Quellcode für (befindet sich in atlsimpstr.h).

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>CSimpleStringT::CSimpleStringT

Erstellt ein `CSimpleStringT`-Objekt.

### <a name="syntax"></a>Syntax

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parameter

*strSrc*<br/>
Ein `CSimpleStringT` vorhandenes Objekt, `CSimpleStringT` das in dieses Objekt kopiert werden soll.

*pchSrc*<br/>
Ein Zeiger auf ein Array von Zeichen der Länge *nLength*, nicht null beendet.

*pszSrc*<br/>
Eine null-terminierte Zeichenfolge, die `CSimpleStringT` in dieses Objekt kopiert werden soll.

*nLänge*<br/>
Eine Anzahl der Zeichen `pch`in .

*pStringMgr*<br/>
Ein Zeiger auf den Speicher-Manager des `CSimpleStringT` Objekts. Weitere Informationen `IAtlStringMgr` zu und `CSimpleStringT`Speicherverwaltung für finden Sie unter [Speicherverwaltung und CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Bemerkungen

Erstellt ein neues `CSimpleStringT`-Objekt. Da die Konstruktoren die Eingabedaten in neuen zugewiesenen Speicher kopieren, können Speicherausnahmen auftreten.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CSimpleStringT::CSimpleStringT` die Verwendung von atL **typedef** `CSimpleString`veranschaulicht. `CSimpleString`ist eine häufig verwendete Spezialisierung `CSimpleStringT`der Klassenvorlage .

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

## <a name="csimplestringtempty"></a><a name="empty"></a>CSimpleStringT::Leer

Macht `CSimpleStringT` dieses Objekt zu einer leeren Zeichenfolge und gibt ggf. Speicher frei.

### <a name="syntax"></a>Syntax

```
void Empty() throw();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Strings: CString Exception Cleanup](../cstring-exception-cleanup.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra

Gibt zusätzlichen Speicher frei, der zuvor von der Zeichenfolge reserviert, aber nicht mehr benötigt wurde.

### <a name="syntax"></a>Syntax

```
void FreeExtra();
```

### <a name="remarks"></a>Bemerkungen

Dadurch sollte der vom Zeichenfolgenobjekt verbrauchte Speicheraufwand reduziert werden. Die Methode ordnet den Puffer auf die exakte Länge um, die von [GetLength](#getlength)zurückgegeben wird.

### <a name="example"></a>Beispiel

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>Bemerkungen

Die Ausgabe aus diesem Beispiel ist wie folgt:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Ruft die zugewiesene `CSimpleStringT` Länge eines Objekts ab.

### <a name="syntax"></a>Syntax

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen, die für dieses Objekt reserviert sind.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um `CSimpleStringT` die Anzahl der Zeichen zu bestimmen, die für dieses Objekt zugewiesen wurden. Ein Beispiel für das Aufrufen dieser Funktion finden Sie unter [FreeExtra.](#freeextra)

## <a name="csimplestringtgetat"></a><a name="getat"></a>CSimpleStringT::Getat

Gibt ein Zeichen `CSimpleStringT` aus einem Objekt zurück.

### <a name="syntax"></a>Syntax

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierter Index des Zeichens im `CSimpleStringT` Objekt. Der *iChar-Parameter* muss größer oder gleich 0 und kleiner als der von [GetLength](#getlength)zurückgegebene Wert sein. Andernfalls `GetAt` wird eine Ausnahme generiert.

### <a name="return-value"></a>Rückgabewert

Eine, `XCHAR` die das Zeichen an der angegebenen Position in der Zeichenfolge enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um das von *iChar*angegebene Zeichen zurückzugeben. Der überladene Subscript -**[]**) `GetAt`Operator ist ein praktischer Alias für . Der NULL-Terminator ist adressierbar, ohne `GetAt`eine Ausnahme mithilfe von zu generieren. Es wird jedoch nicht `GetLength`von gezählt, und der zurückgegebene Wert ist 0.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CSimpleStringT::GetAt`veranschaulicht, wie verwendet wird.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT::GetBuffer

Gibt einen Zeiger auf den internen `CSimpleStringT` Zeichenpuffer für das Objekt zurück.

### <a name="syntax"></a>Syntax

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parameter

*nMinBufferLength*<br/>
Die minimale Anzahl von Zeichen, die der Zeichenpuffer enthalten kann. Dieser Wert enthält keinen Speicherplatz für einen Nullabschluss.

Wenn *nMinBufferLength* größer als die Länge `GetBuffer` des aktuellen Puffers ist, zerstört der aktuelle Puffer, ersetzt ihn durch einen Puffer der angeforderten Größe und setzt die Anzahl der Objektverweise auf Null zurück. Wenn Sie zuvor [LockBuffer](#lockbuffer) für diesen Puffer aufgerufen haben, gehen Sie von der Puffersperre aus.

### <a name="return-value"></a>Rückgabewert

Ein `PXSTR` Zeiger auf den (null-terminierten) Zeichenpuffer des Objekts.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, `CSimpleStringT` um den Pufferinhalt des Objekts zurückzugeben. Die `PXSTR` zurückgegebene ist keine Konstante und `CSimpleStringT` ermöglicht daher eine direkte Änderung der Inhalte.

Wenn Sie den zurückgegebenen `GetBuffer` Zeiger verwenden, um den Zeichenfolgeninhalt zu `CSimpleStringT` ändern, müssen Sie [ReleaseBuffer](#releasebuffer) aufrufen, bevor Sie andere Membermethoden verwenden.

Die von `GetBuffer` ihr zurückgegebene Adresse ist `ReleaseBuffer` nach `CSimpleStringT` dem Aufruf `CSimpleStringT` möglicherweise ungültig, da zusätzliche Vorgänge dazu führen können, dass der Puffer umverteilt wird. Der Puffer wird nicht umverteilt, wenn Sie `CSimpleStringT`die Länge der nicht ändern.

Der Pufferspeicher wird automatisch `CSimpleStringT` freigegeben, wenn das Objekt zerstört wird.

Wenn Sie die Zeichenfolgenlänge selbst nachverfolgen, sollten Sie das beendende Nullzeichen nicht anhängen. Sie müssen jedoch die letzte Zeichenfolgenlänge angeben, wenn Sie den Puffer mit `ReleaseBuffer`freigeben. Wenn Sie ein beendendes NULL-Zeichen anhängen, sollten Sie -1 (Standard) für die Länge übergeben. `ReleaseBuffer`bestimmt dann die Pufferlänge.

Wenn nicht genügend Arbeitsspeicher `GetBuffer` vorhanden ist, um die Anforderung zu erfüllen, löst diese Methode eine CMemoryException* aus.

### <a name="example"></a>Beispiel

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Gibt einen Zeiger auf den internen `CSimpleStringT` Zeichenpuffer für das Objekt zurück, der bei Bedarf abgeschnitten oder vergrößert wird, um genau der in *nLength*angegebenen Länge zu entsprechen.

### <a name="syntax"></a>Syntax

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parameter

*nLänge*<br/>
Die genaue Größe `CSimpleStringT` des Zeichenpuffers in Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein `PXSTR` Zeiger auf den (null-terminierten) Zeichenpuffer des Objekts.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um eine `CSimpleStringT` angegebene Länge des internen Puffers des Objekts abzurufen. Der `PXSTR` zurückgegebene Zeiger ist nicht **const** `CSimpleStringT` und ermöglicht somit eine direkte Änderung des Inhalts.

Wenn Sie den von [GetBufferSetLength](#getbuffersetlength) zurückgegebenen Zeiger verwenden, um den Zeichenfolgeninhalt zu ändern, rufen Sie den `ReleaseBuffer` internen Status auf, `CsimpleStringT` bevor Sie andere `CSimpleStringT` Methoden verwenden.

Die von `GetBufferSetLength` ihr zurückgegebene Adresse ist `ReleaseBuffer` nach `CSimpleStringT` dem Aufruf `CSimpleStringT` möglicherweise ungültig, da zusätzliche Vorgänge dazu führen können, dass der Puffer umverteilt wird. Der Puffer wird nicht neu zugewiesen, wenn `CSimpleStringT`Sie die Länge der nicht ändern.

Der Pufferspeicher wird automatisch `CSimpleStringT` freigegeben, wenn das Objekt zerstört wird.

Wenn Sie die Zeichenfolgenlänge selbst nachverfolgen, fügen Sie das beendende Nullzeichen nicht an. Sie müssen die letzte Zeichenfolgenlänge angeben, `ReleaseBuffer`wenn Sie den Puffer mithilfe von freigeben. Wenn Sie `ReleaseBuffer`beim Aufrufen ein beendendes NULL-Zeichen anhängen, übergeben Sie `ReleaseBuffer`-1 `ReleaseBuffer` (Standardeinstellung) für die Länge an , und führen sie auf dem Puffer aus, `strlen` um seine Länge zu bestimmen.

Weitere Informationen zur Referenzzählung finden Sie in den folgenden Artikeln:

- [Verwalten der Objektlebensdauer durch Referenzzählung](/windows/win32/com/managing-object-lifetimes-through-reference-counting) im Windows SDK.

- [Implementieren der Referenzzählung](/windows/win32/com/implementing-reference-counting) im Windows SDK.

- Regeln für die [Verwaltung von Referenzanzahlen](/windows/win32/com/rules-for-managing-reference-counts) im Windows SDK.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::GetBufferSetLength`.

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT::GetLength

Gibt die Anzahl der `CSimpleStringT` Zeichen im Objekt zurück.

### <a name="syntax"></a>Syntax

```
int GetLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Eine Anzahl der Zeichen in der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Zeichen im Objekt zurückzugeben. Die Anzahl enthält keinen Null-Terminator.

Zählt bei Multibyte-Zeichensätzen `GetLength` (MBCS) jedes 8-Bit-Zeichen; Das heißt, ein Lead- und Trailbyte in einem Multibyte-Zeichen werden als zwei Bytes gezählt. Ein Beispiel für das Aufrufen dieser Funktion finden Sie unter [FreeExtra.](#freeextra)

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT::GetManager

Ruft den Speicher-Manager `CSimpleStringT` des Objekts ab.

### <a name="syntax"></a>Syntax

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicher-Manager für das `CSimpleStringT` Objekt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, `CSimpleStringT` um den vom Objekt verwendeten Speicher-Manager abzurufen. Weitere Informationen zu Speicher-Managern und Zeichenfolgenobjekten finden Sie unter [Speicherverwaltung und CStringT](../memory-management-with-cstringt.md).

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT::GetString

Ruft die Zeichenfolge ab.

### <a name="syntax"></a>Syntax

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine null-terminierte Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, `CSimpleStringT` um die dem Objekt zugeordnete Zeichenfolge abzurufen.

> [!NOTE]
> Der `PCXSTR` zurückgegebene Zeiger ist **const** und `CSimpleStringT` lässt keine direkte Änderung von Inhalten zu.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>CsimpleStringt::IsEmpty

Testet `CSimpleStringT` ein Objekt für den leeren Zustand.

### <a name="syntax"></a>Syntax

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE `CSimpleStringT` zurück, wenn das Objekt eine Länge von 0 hat. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um zu bestimmen, ob das Objekt eine leere Zeichenfolge enthält.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>CSimpleStringT::LockBuffer

Deaktiviert die Verweiszählung und schützt die Zeichenfolge im Puffer.

### <a name="syntax"></a>Syntax

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CSimpleStringT` ein Objekt oder eine null-terminierte Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den Puffer des `CSimpleStringT` Objekts zu sperren. Durch `LockBuffer`Aufrufen erstellen Sie eine Kopie der Zeichenfolge mit einer -1 für die Referenzanzahl. Wenn der Referenzanzahlwert -1 ist, wird die Zeichenfolge im Puffer als "gesperrt" betrachtet. In einem gesperrten Zustand ist die Zeichenfolge auf zwei Arten geschützt:

- Keine andere Zeichenfolge kann einen Verweis auf die Daten in der gesperrten Zeichenfolge abrufen, auch wenn diese Zeichenfolge der gesperrten Zeichenfolge zugewiesen ist.

- Die gesperrte Zeichenfolge verweist nie auf eine andere Zeichenfolge, auch wenn diese andere Zeichenfolge in die gesperrte Zeichenfolge kopiert wird.

Indem Sie die Zeichenfolge im Puffer sperren, stellen Sie sicher, dass der exklusive Halt der Zeichenfolge für den Puffer intakt bleibt.

Nachdem Sie mit `LockBuffer`abgeschlossen haben, rufen Sie [UnlockBuffer](#unlockbuffer) auf, um die Referenzanzahl auf 1 zurückzusetzen.

> [!NOTE]
> Wenn Sie [GetBuffer](#getbuffer) für einen gesperrten `GetBuffer` `nMinBufferLength` Puffer aufrufen und den Parameter auf größer als die Länge des aktuellen Puffers festlegen, gehen die Puffersperre verloren. Ein solcher `GetBuffer` Aufruf, um den aktuellen Puffer zu zerstören, ersetzt ihn durch einen Puffer der angeforderten Größe und setzt die Verweisanzahl auf Null zurück.

Weitere Informationen zur Referenzzählung finden Sie in den folgenden Artikeln:

- [Verwalten von Objektlebensdauern durch Referenzzählung](/windows/win32/com/managing-object-lifetimes-through-reference-counting) im Windows SDK

- [Implementieren der Referenzzählung](/windows/win32/com/implementing-reference-counting) im Windows SDK

- Regeln für die [Verwaltung von Referenzanzahlen](/windows/win32/com/rules-for-managing-reference-counts) im Windows SDK

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]

Rufen Sie diese Funktion auf, um auf ein einzelnes Zeichen des Zeichenarrays zuzugreifen.

### <a name="syntax"></a>Syntax

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierter Index eines Zeichens in der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Der Operator überladene Subskripte (**[]**) gibt ein einzelnes Zeichen zurück, das durch den nullbasierten Index in *iChar*angegeben wird. Dieser Operator ist ein [GetAt](#getat) bequemer Ersatz für die GetAt-Memberfunktion.

> [!NOTE]
> Sie können den Operator subscript (**[]**) verwenden, `CSimpleStringT`um den Wert eines Zeichens in einem `CSimpleStringT`abzubekommen, aber Sie können es nicht verwenden, um den Wert eines Zeichens in einem zu ändern.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]

Rufen Sie diese Funktion auf, um auf ein einzelnes Zeichen des Zeichenarrays zuzugreifen.

### <a name="syntax"></a>Syntax

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierter Index eines Zeichens in der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Der Operator überladene Subskripte (**[]**) gibt ein einzelnes Zeichen zurück, das durch den nullbasierten Index in *iChar*angegeben wird. Dieser Operator ist ein [GetAt](#getat) bequemer Ersatz für die GetAt-Memberfunktion.

> [!NOTE]
> Sie können den Operator subscript (**[]**) verwenden, `CSimpleStringT`um den Wert eines Zeichens in einem `CSimpleStringT`abzubekommen, aber Sie können es nicht verwenden, um den Wert eines Zeichens in einem zu ändern.

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT::operator +=

Verknüpft eine neue Zeichenfolge oder ein neues Zeichen mit dem Ende einer vorhandenen Zeichenfolge.

### <a name="syntax"></a>Syntax

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge.

*strSrc*<br/>
Ein Zeiger auf `CSimpleStringT` ein vorhandenes Objekt.

*Ch*<br/>
Das Zeichen, das angefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Der Operator `CSimpleStringT` akzeptiert ein anderes Objekt oder ein Zeichen. Beachten Sie, dass Speicherausnahmen auftreten können, wenn Sie diesen Verkettungsoperator `CSimpleStringT` verwenden, da möglicherweise neuer Speicher für Zeichen zugewiesen wird, die diesem Objekt hinzugefügt wurden.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT::operator =

Weist einem `CSimpleStringT` Objekt einen neuen Wert zu.

### <a name="syntax"></a>Syntax

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge.

*strSrc*<br/>
Ein Zeiger auf `CSimpleStringT` ein vorhandenes Objekt.

### <a name="remarks"></a>Bemerkungen

Wenn die Zielzeichenfolge (die linke Seite) bereits groß genug ist, um die neuen Daten zu speichern, wird keine neue Speicherzuweisung durchgeführt. Beachten Sie, dass Speicherausnahmen auftreten können, wenn Sie den Zuweisungsoperator verwenden, da häufig neuer Speicher für das resultierende `CSimpleStringT` Objekt reserviert wird.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator =`.

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT::operator PCXSTR

Greift direkt auf Zeichen `CSimpleStringT` zu, die in einem Objekt als Zeichenfolge im C-Stil gespeichert sind.

### <a name="syntax"></a>Syntax

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeichenzeiger auf die Daten der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Es werden keine Zeichen kopiert. es wird nur ein Zeiger zurückgegeben. Seien Sie vorsichtig mit diesem Operator. Wenn Sie `CString` ein Objekt ändern, nachdem Sie den Zeichenzeiger erhalten haben, können Sie eine Neuzuweisung des Speichers verursachen, die den Zeiger ungültig macht.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator PCXSTR`.

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::PCXSTR

Ein Zeiger auf eine konstante Zeichenfolge.

### <a name="syntax"></a>Syntax

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::Pzuteilung

Ordnet dem `CSimpleStringT` Objekt eine bestimmte Menge an Bytes zu.

### <a name="syntax"></a>Syntax

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parameter

*nLänge*<br/>
Die genaue Größe `CSimpleStringT` des Zeichenpuffers in Zeichen.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, `CSimpleStringT` um dem Objekt eine bestimmte Puffergröße zuzuweisen.

`CSimpleStringT`generiert eine STATUS_NO_MEMORY Ausnahme, wenn sie keinen Speicherplatz für den Zeichenpuffer zuweisen kann. Standardmäßig wird die Speicherzuweisung von WIN32-API-Funktionen `HeapAlloc` oder `HeapReAlloc`von ausgeführt.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT::PXSTR

Ein Zeiger auf eine Zeichenfolge.

### <a name="syntax"></a>Syntax

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Gibt die Steuerung des von [GetBuffer](#getbuffer)zugewiesenen Puffers frei.

### <a name="syntax"></a>Syntax

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parameter

*nNewLength*<br/>
Die neue Länge der Zeichenfolge in Zeichen, ohne einen Null-Terminator zu zählen. Wenn die Zeichenfolge null beendet ist, legt `CSimpleStringT` der Standardwert -1 die Größe auf die aktuelle Länge der Zeichenfolge fest.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den Puffer des Zeichenfolgenobjekts neu zuzuweisen oder freizugeben. Wenn Sie wissen, dass die Zeichenfolge im Puffer null beendet ist, können Sie das Argument *nNewLength* weglassen. Wenn Ihre Zeichenfolge nicht null beendet ist, verwenden Sie *nNewLength,* um ihre Länge anzugeben. Die von [GetBuffer zurückgegebene](#getbuffer) Adresse ist `ReleaseBuffer` nach `CSimpleStringT` dem Aufruf oder einem anderen Vorgang ungültig.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::ReleaseBuffer`.

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Gibt die Steuerung des von [GetBuffer](#getbuffer)zugewiesenen Puffers frei.

### <a name="syntax"></a>Syntax

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parameter

*nNewLength*<br/>
Die Länge der freizugebenden Zeichenfolge

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist funktional ähnlich wie [ReleaseBuffer,](#releasebuffer) mit der Ausnahme, dass eine gültige Länge für das Zeichenfolgenobjekt übergeben werden muss.

## <a name="csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT::Setat

Legt ein einzelnes `CSimpleStringT` Zeichen aus einem Objekt fest.

### <a name="syntax"></a>Syntax

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierter Index des Zeichens im `CSimpleStringT` Objekt. Der *iChar-Parameter* muss größer oder gleich 0 und kleiner als der von [GetLength](#getlength)zurückgegebene Wert sein.

*Ch*<br/>
Der neue Charakter.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um das Zeichen in *iChar*zu überschreiben. Diese Methode vergrößert die Zeichenfolge nicht, wenn *iChar* die Grenzen der vorhandenen Zeichenfolge überschreitet.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT::SetManager

Gibt den Speicher-Manager `CSimpleStringT` des Objekts an.

### <a name="syntax"></a>Syntax

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parameter

*pStringMgr*<br/>
Ein Zeiger auf den neuen Speicher-Manager.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um `CSimpleStringT` einen neuen Speicher-Manager anzugeben, der vom Objekt verwendet wird. Weitere Informationen zu Speicher-Managern und Zeichenfolgenobjekten finden Sie unter [Speicherverwaltung und CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT::SetString

Legt die Zeichenfolge `CSimpleStringT` eines Objekts fest.

### <a name="syntax"></a>Syntax

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge.

*nLänge*<br/>
Eine Anzahl der Zeichen in *pszSrc*.

### <a name="remarks"></a>Bemerkungen

Kopieren Sie eine `CSimpleStringT` Zeichenfolge in das Objekt. `SetString`überschreibt die älteren Zeichenfolgendaten im Puffer.

Beide Versionen `SetString` von überprüfen, ob *pszSrc* ein Nullzeiger ist, und, falls dies der Fall ist, werfen sie einen E_INVALIDARG Fehler aus.

Die Ein-Parameter-Version von `SetString` erwartet, dass *pszSrc* auf eine null-terminierte Zeichenfolge verweist.

Die Zwei-Parameter-Version von `SetString` erwartet auch, dass *pszSrc* eine null-terminierte Zeichenfolge ist. Es verwendet *nLength* als Zeichenfolgenlänge, es sei denn, es wird zuerst ein Null-Terminator.

Die Zwei-Parameter-Version von `SetString` überprüft auch, ob *pszSrc* `CSimpleStringT`auf eine Position im aktuellen Puffer in zeigt. Verwendet in diesem `SetString` speziellen Fall eine Speicherkopiefunktion, die die Zeichenfolgendaten nicht überschreibt, wenn sie die Zeichenfolgendaten zurück in den Puffer kopiert.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>CSimpleStringT::StringLength

Gibt die Anzahl der Zeichen in der angegebenen Zeichenfolge zurück.

### <a name="syntax"></a>Syntax

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parameter

*Psz*<br/>
Ein Zeiger auf eine null-terminierte Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen in *psz*; nicht zählen einen Null-Terminator.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Zeichen in der Zeichenfolge abzurufen, auf die *psz*zeigt.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT::Truncate

Kürt die Zeichenfolge auf die neue Länge.

### <a name="syntax"></a>Syntax

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parameter

*nNewLength*<br/>
Die neue Länge der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um den Inhalt der Zeichenfolge auf die neue Länge zu abschneiden.

> [!NOTE]
> Dies wirkt sich nicht auf die zugewiesene Länge des Puffers aus. Informationen zum Verringern oder Erhöhen des aktuellen Puffers finden Sie unter [FreeExtra](#freeextra) und [Preallocate](#preallocate).

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Truncate`.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

Entsperrt den `CSimpleStringT` Puffer des Objekts.

### <a name="syntax"></a>Syntax

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Referenzanzahl der Zeichenfolge auf 1 zurückzusetzen.

Der `CSimpleStringT` Destruktor `UnlockBuffer` ruft automatisch auf, um sicherzustellen, dass der Puffer nicht gesperrt wird, wenn der Destruktor aufgerufen wird. Ein Beispiel für diese Methode finden Sie unter [LockBuffer](#lockbuffer).

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT::'csimplestringt

Zerstört ein `CSimpleStringT` -Objekt.

### <a name="syntax"></a>Syntax

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese `CSimpleStringT` Methode auf, um das Objekt zu zerstören.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
