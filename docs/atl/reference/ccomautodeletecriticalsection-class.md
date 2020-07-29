---
title: Ccomautodeletecriticalsection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
ms.openlocfilehash: f44dbff7d353cb09142ac742b526d3541e9b2265
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224330"
---
# <a name="ccomautodeletecriticalsection-class"></a>Ccomautodeletecriticalsection-Klasse

Diese Klasse stellt Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts Objekts bereit.

## <a name="syntax"></a>Syntax

```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```

## <a name="remarks"></a>Bemerkungen

`CComAutoDeleteCriticalSection`wird von der [ccomsafedeletecriticalsection](../../atl/reference/ccomsafedeletecriticalsection-class.md)-Klasse abgeleitet. `CComAutoDeleteCriticalSection`Überschreibt jedoch den [Begriff](ccomsafedeletecriticalsection-class.md#term) Methode für den **`private`** Zugriff auf, wodurch die interne Speicher Bereinigung nur dann erfolgt, wenn Instanzen dieser Klasse den Gültigkeitsbereich verlassen oder explizit aus dem Arbeitsspeicher gelöscht werden.

Mit dieser Klasse werden keine zusätzlichen Methoden über die Basisklasse eingeführt. Weitere Informationen zu kritischen Abschnitts Hilfsklassen finden Sie unter [ccomsafedeletecriticalsection](../../atl/reference/ccomsafedeletecriticalsection-class.md) und [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md)

[Ccomsafedeletecriticalsection](../../atl/reference/ccomsafedeletecriticalsection-class.md)

`CComAutoDeleteCriticalSection`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcore. h

## <a name="see-also"></a>Siehe auch

[Ccomsafedeletecriticalsection-Klasse](../../atl/reference/ccomsafedeletecriticalsection-class.md)<br/>
[Ccomcriticalsection-Klasse](../../atl/reference/ccomcriticalsection-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
