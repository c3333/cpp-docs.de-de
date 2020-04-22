---
title: CStrBufT-Klasse
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 71d7b6f7d53e9613b1ac26013d73c1dbd1ef0aab
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746929"
---
# <a name="cstrbuft-class"></a>CStrBufT-Klasse

Diese Klasse bietet eine `GetBuffer` automatische `ReleaseBuffer` Ressourcenbereinigung `CStringT` für ein vorhandenes Objekt und ruft es auf.

## <a name="syntax"></a>Syntax

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parameter

*TCharType*<br/>
Der Zeichentyp `CStrBufT` der Klasse. Dabei kann es sich um eine der folgenden Methoden handeln:

- **char** (für ANSI-Zeichenketten)

- **wchar_t** (für Unicode-Zeichenfolgen)

- TCHAR (für ANSI- und Unicode-Zeichenfolgen)

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|PCXSTR|Ein Zeiger auf eine konstante Zeichenfolge.|
|PXSTR|Ein Zeiger auf eine Zeichenfolge.|
|`StringType`|Der Zeichenfolgentyp, dessen Puffer durch Spezialisierungen dieser Klassenvorlage bearbeitet werden soll.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|Der Konstruktor für das Zeichenfolgenpufferobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|Legt die Zeichenpufferlänge des zugeordneten Zeichenfolgenobjekts fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Ruft einen **const-Zeiger** auf den Zeichenpuffer des zugeordneten Zeichenfolgenobjekts ab.|
|[CStrBufT::operator PXSTR](#operator_pxstr)|Ruft einen Zeiger auf den Zeichenpuffer des zugeordneten Zeichenfolgenobjekts ab.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|Bestimmen Sie automatisch die neue Länge der Zeichenfolge bei der Freigabe.|
|[CStrBufT::SET_LENGTH](#set_length)|Festlegen der Länge des Zeichenfolgenobjekts zur GetBuffer-Zeit|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wird als Wrapperklasse zum Ersetzen von Aufrufen von [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) `ReleaseBuffer`und [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)oder [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) und verwendet.

In erster Linie als `CStrBufT` Hilfsklasse konzipiert, bietet eine bequeme Möglichkeit für einen Entwickler, mit dem `ReleaseBuffer`Zeichenpuffer eines Zeichenfolgenobjekts zu arbeiten, ohne sich Gedanken darüber zu machen, wie oder wann er aufruft. Dies ist möglich, da das Wrapperobjekt bei einer Ausnahme oder mehreren beendenden Codepfaden natürlich aus dem Gültigkeitsbereich verschwindet. dadurch, dass der Destruktor die Zeichenfolgenressource freigibt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsimpstr.h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>CStrBufT::AUTO_LENGTH

Bestimmen Sie automatisch die neue Länge der Zeichenfolge bei der Freigabe.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Bemerkungen

Bestimmen Sie automatisch die neue Länge der Zeichenfolge bei der Freigabe. Die Zeichenfolge muss null-beendet sein.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>CStrBufT::CStrBufT

Erstellt ein Pufferobjekt.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Das dem Puffer zugeordnete Zeichenfolgenobjekt. In der Regel verwendet der Entwickler die `CStrBuf` vordefinierten typdefs von `CStrBufA` (TCHAR-Variante),**(char-Variante)** und `CStrBufW` (**wchar_t** Variante).

*nMinLength*<br/>
Die Mindestlänge des Zeichenpuffers.

*dwFlags*<br/>
Bestimmt, ob die Zeichenfolgenlänge automatisch bestimmt wird. Dabei kann es sich um eine der folgenden Methoden handeln:

- AUTO_LENGTH String-Länge wird automatisch bestimmt, wenn [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) aufgerufen wird. Die Zeichenfolge muss null-beendet sein. Standardwert.

- SET_LENGTH String-Länge wird festgelegt, wenn [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Erstellt einen Zeichenfolgenpuffer für das zugeordnete Zeichenfolgenobjekt. Während der Konstruktion wird [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) oder [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) aufgerufen.

Beachten Sie, dass der Kopierkonstruktor **privat**ist.

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>CStrBufT::operator PCXSTR

Greift direkt auf Zeichen zu, die im zugeordneten Zeichenfolgenobjekt als Zeichenfolge im C-Stil gespeichert sind.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeichenzeiger auf die Daten der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um einen Zeiger auf den Zeichenpuffer eines Zeichenfolgenobjekts zurückzugeben. Der Inhalt des Zeichenfolgenobjekts kann mit diesem Zeiger nicht geändert werden.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>CStrBufT::operator PXSTR

Greift direkt auf Zeichen zu, die im zugeordneten Zeichenfolgenobjekt als Zeichenfolge im C-Stil gespeichert sind.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeichenzeiger auf die Daten der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um einen Zeiger auf den Zeichenpuffer eines Zeichenfolgenobjekts zurückzugeben. Der Entwickler kann den Inhalt des Zeichenfolgenobjekts mit diesem Zeiger ändern.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>CStrBufT::PCXSTR

Ein Zeiger auf eine konstante Zeichenfolge.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>CStrBufT::PXSTR

Ein Zeiger auf eine Zeichenfolge.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>CStrBufT::SET_LENGTH

Legen Sie die Länge `GetBuffer` des Zeichenfolgenobjekts zum Zeitpunkt fest.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie die Länge des Zeichenfolgenobjekts zur GetBuffer-Zeit fest.

Legt fest, ob [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) und [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) aufgerufen werden, wenn das Zeichenfolgenpufferobjekt erstellt wird.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>CStrBufT::SetLength

Legt die Länge des Zeichenpuffers fest.

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>Parameter

*nLänge*<br/>
Die neue Länge des Zeichenpuffers des Zeichenfolgenobjekts.

> [!NOTE]
> Muss kleiner oder gleich der im Konstruktor von `CStrBufT`angegebenen minimalen Pufferlänge sein.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die Länge der Zeichenfolge festzulegen, die durch das Pufferobjekt dargestellt wird.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>CStrBufT::StringType

Der Zeichenfolgentyp, dessen Puffer durch Spezialisierungen dieser Klassenvorlage bearbeitet werden soll.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Bemerkungen

`TCharType`ist der Zeichentyp, der zum Spezialisieren der Klassenvorlage verwendet wird.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[FREIGEGEBENe ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
