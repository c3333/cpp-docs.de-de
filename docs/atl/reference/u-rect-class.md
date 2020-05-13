---
title: _U_RECT Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::_U_RECT
- _U_RECT
- ATL._U_RECT
helpviewer_keywords:
- U_RECT class
- _U_RECT class
ms.assetid: 5f880a2d-09cf-4327-bf32-a3519c4dcd63
ms.openlocfilehash: 8a4d5b2a770b3f0ecfe10be0fbad22a702aa0531
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325810"
---
# <a name="_u_rect-class"></a>_U_RECT Klasse

Mit dieser Argumentadapterklasse können Zeiger `RECT` oder Verweise an eine Funktion übergeben werden, die in Bezug auf Zeiger implementiert ist.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class _U_RECT
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[_U_RECT::_U_RECT](#_u_rect___u_rect)|Der Konstruktor.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[_U_RECT::m_lpRect](#_u_rect__m_lprect)|Zeiger auf `RECT`eine .|

## <a name="remarks"></a>Bemerkungen

Die Klasse definiert zwei Konstruktorüberladungen: eine akzeptiert ein **RECT-&-Argument** und die andere ein `LPRECT` Argument. Der erste Konstruktor speichert die Adresse des Referenzarguments im einzelnen Datenmember der Klasse, [m_lpRect](#_u_rect__m_lprect). Das Argument zum Zeigerkonstruktor wird direkt ohne Konvertierung gespeichert.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="_u_rectm_lprect"></a><a name="_u_rect__m_lprect"></a>_U_RECT::m_lpRect

Die Klasse hält den Wert, der an einen `LPRECT` ihrer Konstruktoren übergeben wird, als öffentliches Datenmember.

```
LPRECT m_lpRect;
```

## <a name="_u_rect_u_rect"></a><a name="_u_rect___u_rect"></a>_U_RECT::_U_RECT

Die Adresse des Referenzarguments wird im einzelnen Datenmember der [Klasse, m_lpRect](#_u_rect__m_lprect)gespeichert.

```
_U_RECT(RECT& rc);
_U_RECT(LPRECT lpRect);
```

### <a name="parameters"></a>Parameter

*Rc*<br/>
Ein `RECT`-Verweis.

*lpRect*<br/>
Ein `RECT` Zeiger.

### <a name="remarks"></a>Bemerkungen

Das Argument zum Zeigerkonstruktor wird direkt ohne Konvertierung gespeichert.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
