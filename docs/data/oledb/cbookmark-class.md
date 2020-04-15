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
ms.openlocfilehash: d3d82ea09b7ed2c1cbaf325906b4f9b480e1eb4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359335"
---
# <a name="cbookmark-class"></a>CBookmark-Klasse

Hält einen Lesezeichenwert in seinem Puffer.

## <a name="syntax"></a>Syntax

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Parameter

*nGröße*<br/>
Die Größe des Lesezeichenpuffers in Bytes. Wenn *nSize* Null ist, wird der Lesezeichenpuffer zur Laufzeit dynamisch erstellt.

## <a name="requirements"></a>Anforderungen

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CBookmark](#cbookmark)|Der Konstruktor|
|[GetBuffer](#getbuffer)|Ruft den Zeiger auf den Puffer ab.|
|[GetSize](#getsize)|Ruft die Größe des Puffers in Bytes ab.|
|[SetBookmark](#setbookmark)|Legt den Lesezeichenwert fest.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#operator)|Weist eine `CBookmark` Klasse einer anderen klasse zu.|

## <a name="remarks"></a>Bemerkungen

`CBookmark<0>`ist eine Vorlagenspezialisierung `CBookmark`von ; sein Puffer wird zur Laufzeit dynamisch erstellt.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a>CBookmark::CBookmark

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Parameter

*nGröße*<br/>
[in] Größe des Lesezeichenpuffers in Bytes.

### <a name="remarks"></a>Bemerkungen

Die erste Funktion legt den Puffer auf NULL und die Puffergröße auf 0 fest. Die zweite Funktion legt die Puffergröße auf *nSize*fest und der Puffer auf ein Bytearray von *nSize* Bytes.

> [!NOTE]
> Diese Funktion ist `CBookmark<0>`nur in verfügbar.

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a>CBookmark::GetBuffer

Ruft den Zeiger auf den Lesezeichenpuffer ab.

### <a name="syntax"></a>Syntax

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Lesezeichenpuffer.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a>CBookmark::GetSize

Ruft die Größe des Lesezeichenpuffers ab.

### <a name="syntax"></a>Syntax

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Größe des Puffers in Byte.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a>CBookmark::SetBookmark

Kopiert den Lesezeichenwert, auf den `CBookmark` *pBuffer verweist,* in den Puffer und legt die Puffergröße auf *nSize*fest.

### <a name="syntax"></a>Syntax

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Parameter

*nGröße*<br/>
[in] Die Größe des Lesezeichenpuffers.

*pBuffer*<br/>
[in] Ein Zeiger auf das Bytearray, das den Lesezeichenwert enthält.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist `CBookmark<0>`nur in verfügbar.

## <a name="cbookmarkoperator-"></a><a name="operator"></a>CBookmark::operator =

Weist ein `CBookmark` Objekt einem anderen objekt zu.

### <a name="syntax"></a>Syntax

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator wird `CBookmark<0>`nur in benötigt.

## <a name="see-also"></a>Siehe auch

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Ole DB Consumer Templates Referenz](../../data/oledb/ole-db-consumer-templates-reference.md)
