---
title: CBookmark-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
ms.openlocfilehash: 4013e40c364593676ebb099804304ffb2adb42c1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838476"
---
# <a name="cbookmark-class"></a>CBookmark-Klasse

Enthält einen Lesezeichen Wert im Puffer.

## <a name="syntax"></a>Syntax

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Parameter

*nSize*<br/>
Die Größe des Lesezeichen Puffers in Bytes. Wenn *nSize* gleich 0 (null) ist, wird der Lesezeichen Puffer dynamisch zur Laufzeit erstellt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[CBookmark](#cbookmark)|Der Konstruktor|
|[GetBuffer](#getbuffer)|Ruft den Zeiger auf den Puffer ab.|
|[GetSize](#getsize)|Ruft die Größe des Puffers in Bytes ab.|
|[SetBookmark](#setbookmark)|Legt den Lesezeichen Wert fest.|

### <a name="operators"></a>Operatoren

| Name | Beschreibung |
|-|-|
|[Operator =](#operator)|Weist einer `CBookmark` anderen Klasse eine Klasse zu.|

## <a name="remarks"></a>Bemerkungen

`CBookmark<0>` ist eine Vorlagen Spezialisierung von `CBookmark` . der Puffer wird zur Laufzeit dynamisch erstellt.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a> CBookmark:: CBookmark

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Parameter

*nSize*<br/>
in Größe des Lesezeichen Puffers in Bytes.

### <a name="remarks"></a>Bemerkungen

Mit der ersten Funktion wird der Puffer auf NULL festgelegt, und die Puffergröße wird auf 0 festgelegt. Mit der zweiten Funktion wird die Puffergröße auf *nSize*festgelegt, und der Puffer wird auf ein Bytearray mit *nSize* -Bytes festgelegt.

> [!NOTE]
> Diese Funktion ist nur in verfügbar `CBookmark<0>` .

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a> CBookmark:: GetBuffer

Ruft den Zeiger auf den Lesezeichen Puffer ab.

### <a name="syntax"></a>Syntax

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Lesezeichen Puffer.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a> CBookmark:: GetSize

Ruft die Größe des Lesezeichen Puffers ab.

### <a name="syntax"></a>Syntax

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Größe des Puffers in Byte.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a> CBookmark:: SetBookmark

Kopiert den von *pbuffer* referenzierten Lesezeichen Wert in den `CBookmark` Puffer und legt die Puffergröße auf *nSize*fest.

### <a name="syntax"></a>Syntax

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Parameter

*nSize*<br/>
in Die Größe des Lesezeichen Puffers.

*pBuffer*<br/>
in Ein Zeiger auf das Bytearray, das den Lesezeichen Wert enthält.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nur in verfügbar `CBookmark<0>` .

## <a name="cbookmarkoperator-"></a><a name="operator"></a> CBookmark:: Operator =

Weist ein- `CBookmark` Objekt einem anderen zu.

### <a name="syntax"></a>Syntax

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator wird nur in benötigt `CBookmark<0>` .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
