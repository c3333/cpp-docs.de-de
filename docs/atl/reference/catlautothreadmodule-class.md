---
title: Klasse von "-Klasse"
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModule
- atlbase/ATL::CAtlAutoThreadModule
helpviewer_keywords:
- CAtlAutoThreadModule class
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
ms.openlocfilehash: f4bd1071380bf3e31c69c593c5db81112fdf21de
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168305"
---
# <a name="catlautothreadmodule-class"></a>Klasse von "-Klasse"

Diese Klasse implementiert einen com-Server mit einem Thread im Pool.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
class CAtlAutoThreadModule : public CAtlAutoThreadModuleT<CAtlAutoThreadModule>
```

## <a name="remarks"></a>Bemerkungen

`CAtlAutoThreadModule`wird von " [catlaudethreadmodulet](../../atl/reference/catlautothreadmodulet-class.md) " abgeleitet und implementiert einen Thread im Pool für den com-Server mit einem Thread Pool. `CAtlAutoThreadModule`verwendet [ccomapartment](../../atl/reference/ccomapartment-class.md) zum Verwalten eines Apartment für jeden Thread im Modul.

Sie müssen das [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) -Makro in der Klassendefinition Ihres Objekts verwenden, um [ccomclassfactoryautothread](../../atl/reference/ccomclassfactoryautothread-class.md) als Klassenfactory anzugeben. Sie sollten dann eine einzelne Instanz einer von `CAtlAutoThreadModuleT` abgeleiteten Klasse hinzufügen, `CAtlAutoThreadModule`z. b.. Beispiel:

`CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`

> [!NOTE]
> Diese Klasse ersetzt die veraltete [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) -Klasse.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IAtlAutoThreadModule`

[""](../../atl/reference/catlautothreadmodulet-class.md)

`CAtlAutoThreadModule`

## <a name="requirements"></a>Anforderungen

**Header:** atlbase. h

## <a name="see-also"></a>Weitere Informationen:

[Klasse von "-Klasse"](../../atl/reference/catlautothreadmodulet-class.md)<br/>
[Iatlaudethreadmodule-Klasse](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)
