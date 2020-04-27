---
title: Klasse von "Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 7516349e4ec54d8cb90fa6ff23b0ded954aa043b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168123"
---
# <a name="catlfilemapping-class"></a>Klasse von "Klasse"

Diese Klasse stellt eine Speicher Abbild Datei dar und fügt den [Methoden von "](../../atl/reference/catlfilemappingbase-class.md)" für "" von "" die Methode "" von "" für "".

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die für den Umwandlungs Operator verwendet werden.

## <a name="members"></a>Member

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|["Chanlfilemapping:: Operator T *"](#operator_t_star)|Ermöglicht die implizite Konvertierung `CAtlFileMapping` von- `T*`Objekten in.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse fügt einen einzelnen Cast Operator hinzu, um die implizite `CAtlFileMapping` Konvertierung von `T*`Objekten in zuzulassen. Andere Member werden von der Basisklasse "" [, "](../../atl/reference/catlfilemappingbase-class.md)", "", "", ".

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[' ' ' ' ' ' ' ' ' "](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Anforderungen

**Header:** atlfile. h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>"Chanlfilemapping:: Operator T *"

Ermöglicht die implizite Konvertierung `CAtlFileMapping` von- `T*`Objekten in.

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen `T*` Zeiger auf den Anfang der Speicher Abbild Datei zurück.

### <a name="remarks"></a>Bemerkungen

Ruft ["](../../atl/reference/catlfilemappingbase-class.md#getdata) " "" "" "," ", und interpretiert den zurückgegebenen Zeiger als `T*` " ", wobei" *T* "der Typ ist, der als Vorlagen Parameter dieser Klasse verwendet wird.

## <a name="see-also"></a>Weitere Informationen:

[Klasse von "-Klasse"](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
