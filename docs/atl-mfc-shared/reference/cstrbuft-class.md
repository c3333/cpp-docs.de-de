---
title: Cstrinbuft-Klasse
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
ms.openlocfilehash: 4d9d0b403e572d6fdea65355702467c89587cc3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219078"
---
# <a name="cstrbuft-class"></a>Cstrinbuft-Klasse

Diese Klasse ermöglicht die automatische Ressourcen Bereinigung für `GetBuffer` -und- `ReleaseBuffer` Aufrufe für ein vorhandenes- `CStringT` Objekt.

## <a name="syntax"></a>Syntax

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>Parameter

*Tchartype*<br/>
Der Zeichentyp der `CStrBufT` Klasse. Dabei kann es sich um eine der folgenden Methoden handeln:

- **`char`**(für ANSI-Zeichen folgen)

- **`wchar_t`**(für Unicode-Zeichen folgen)

- Tchar (für ANSI-und Unicode-Zeichen folgen)

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|PCXSTR|Ein Zeiger auf eine Konstantenzeichenfolge.|
|Pxstr|Ein Zeiger auf eine Zeichenfolge.|
|`StringType`|Der Zeichen folgertyp, dessen Puffer durch Spezialisierungs Informationen dieser Klassen Vorlage manipuliert werden soll.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cstrinbuft:: cstrinbuft](#cstrbuft)|Der Konstruktor für das Zeichen folgen Puffer Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[Cstrinbuft:: SetLength](#setlength)|Legt die Länge des Zeichen Puffers des zugeordneten Zeichen folgen Objekts fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cstrinbuft:: Operator PCXSTR](#operator_pcxstr)|Ruft einen **`const`** Zeiger auf den Zeichen Puffer des zugeordneten Zeichen folgen Objekts ab.|
|[Cstrinbuft:: Operator pxstr](#operator_pxstr)|Ruft einen Zeiger auf den Zeichen Puffer des zugeordneten Zeichen folgen Objekts ab.|

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Cstrinbuft:: AUTO_LENGTH](#auto_length)|Die neue Länge der Zeichenfolge wird bei der Freigabe automatisch festgelegt.|
|[Cstrinbuft:: SET_LENGTH](#set_length)|Festlegen der Länge des Zeichen folgen Objekts zur GetBuffer-Zeit|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wird als Wrapper Klasse zum Ersetzen von Aufrufen von [GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) und [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)oder [getbuffersetlength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) und verwendet `ReleaseBuffer` .

Ist hauptsächlich als `CStrBufT` Hilfsklasse konzipiert und stellt einem Entwickler eine bequeme Möglichkeit zur Verfügung, mit dem Zeichen Puffer eines String-Objekts zu arbeiten, ohne sich Gedanken darüber machen zu müssen, wie oder wann aufgerufen werden soll `ReleaseBuffer` . Dies ist möglich, da das Wrapper Objekt im Falle einer Ausnahme oder mehrerer beendigender Codepfade den Gültigkeitsbereich verlässt. bewirkt, dass der Dekonstruktor die Zeichen folgen Ressource freigibt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlsimpstr. h

## <a name="cstrbuftauto_length"></a><a name="auto_length"></a>Cstrinbuft:: AUTO_LENGTH

Die neue Länge der Zeichenfolge wird bei der Freigabe automatisch festgelegt.

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Bemerkungen

Die neue Länge der Zeichenfolge wird bei der Freigabe automatisch festgelegt. Die Zeichenfolge muss auf Null enden.

## <a name="cstrbuftcstrbuft"></a><a name="cstrbuft"></a>Cstrinbuft:: cstrinbuft

Erstellt ein Puffer Objekt.

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>Parameter

*str*<br/>
Das Zeichen folgen Objekt, das dem Puffer zugeordnet ist. In der Regel verwendet der Entwickler die vordefinierten Typedefs von `CStrBuf` (TCHAR Variant), `CStrBufA` ( **`char`** Variant) und `CStrBufW` ( **`wchar_t`** Variant).

*nminlength*<br/>
Die minimale Länge des Zeichen Puffers.

*dwFlags*<br/>
Bestimmt, ob die Zeichen folgen Länge automatisch bestimmt wird. Dabei kann es sich um eine der folgenden Methoden handeln:

- AUTO_LENGTH Zeichen folgen Länge wird automatisch festgelegt, wenn [CSimpleStringT:: Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) aufgerufen wird. Die Zeichenfolge muss auf Null enden. Standardwert.

- SET_LENGTH Zeichen folgen Länge wird festgelegt, wenn [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Erstellt einen Zeichen folgen Puffer für das zugeordnete String-Objekt. Während der Konstruktion wird [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) oder [CSimpleStringT:: getbuffersetlength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) aufgerufen.

Beachten Sie, dass der Kopierkonstruktor ist **`private`** .

## <a name="cstrbuftoperator-pcxstr"></a><a name="operator_pcxstr"></a>Cstrinbuft:: Operator PCXSTR

Greift direkt auf Zeichen zu, die im zugeordneten String-Objekt als Zeichenfolge im C-Format gespeichert sind.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeichen Zeiger auf die Daten der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, um einen Zeiger auf den Zeichen Puffer eines Zeichen folgen Objekts zurückzugeben. Der Inhalt des String-Objekts kann mit diesem Zeiger nicht geändert werden.

## <a name="cstrbuftoperator-pxstr"></a><a name="operator_pxstr"></a>Cstrinbuft:: Operator pxstr

Greift direkt auf Zeichen zu, die im zugeordneten String-Objekt als Zeichenfolge im C-Format gespeichert sind.

```
operator PXSTR() throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeichen Zeiger auf die Daten der Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, um einen Zeiger auf den Zeichen Puffer eines Zeichen folgen Objekts zurückzugeben. Der Entwickler kann den Inhalt des Zeichen folgen Objekts mit diesem Zeiger ändern.

## <a name="cstrbuftpcxstr"></a><a name="pcxstr"></a>Cstrinbuft::P cxstr

Ein Zeiger auf eine Konstantenzeichenfolge.

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

## <a name="cstrbuftpxstr"></a><a name="pxstr"></a>Cstrinbuft::P xstr

Ein Zeiger auf eine Zeichenfolge.

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

## <a name="cstrbuftset_length"></a><a name="set_length"></a>Cstrinbuft:: SET_LENGTH

Legen Sie die Länge des Zeichen folgen Objekts zum `GetBuffer` Zeitpunkt fest.

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie die Länge des Zeichen folgen Objekts zur GetBuffer-Zeit fest.

Bestimmt, ob [CSimpleStringT:: GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) und [CSimpleStringT:: getbuffersetlength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) aufgerufen werden, wenn das Zeichen folgen Puffer Objekt erstellt wird.

## <a name="cstrbuftsetlength"></a><a name="setlength"></a>Cstrinbuft:: SetLength

Legt die Länge des Zeichen Puffers fest.

```cpp
void SetLength(int nLength);
```

### <a name="parameters"></a>Parameter

*nlength*<br/>
Die neue Länge des Zeichen Puffers des Zeichen folgen Objekts.

> [!NOTE]
> Muss kleiner oder gleich der minimalen Pufferlänge sein, die im Konstruktor von angegeben ist `CStrBufT` .

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion wird die Länge der Zeichenfolge festgelegt, die durch das Buffer-Objekt dargestellt wird.

## <a name="cstrbuftstringtype"></a><a name="stringtype"></a>Cstrinbuft:: StringType

Der Zeichen folgertyp, dessen Puffer durch Spezialisierungs Informationen dieser Klassen Vorlage manipuliert werden soll.

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Bemerkungen

`TCharType`der Zeichentyp, der verwendet wird, um die Klassen Vorlage zu spezialisieren.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Gemeinsam genutzte ATL/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
