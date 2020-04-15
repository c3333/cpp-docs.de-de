---
title: CDefaultHashTraits-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 43932092621d44cfc8b07270df92e2765665f23f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327088"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits-Klasse

Diese Klasse stellt eine statische Funktion zum Berechnen von Hashwerten bereit.

## <a name="syntax"></a>Syntax

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die in der Auflistung gespeichert werden sollen.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Statisch) Rufen Sie diese Funktion auf, um einen Hashwert für ein bestimmtes Element zu berechnen.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse enthält eine einzelne statische Funktion, die einen Hashwert für ein bestimmtes Element zurückgibt. Diese Klasse wird von der [CDefaultElementTraits-Klasse](../../atl/reference/cdefaultelementtraits-class.md)verwendet.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits::Hash

Rufen Sie diese Funktion auf, um einen Hashwert für ein bestimmtes Element zu berechnen.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Parameter

*Element*<br/>
Das Element.

### <a name="return-value"></a>Rückgabewert

Gibt den Hashwert zurück.

### <a name="remarks"></a>Bemerkungen

Der Standard-Hashalgorithmus ist sehr einfach: Der Rückgabewert ist die Elementnummer. Überschreiben Sie diese Funktion, wenn ein komplizierterer Algorithmus erforderlich ist.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
