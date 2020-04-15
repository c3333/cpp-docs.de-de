---
title: CComAutoCriticalSection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 8cbf08082fd24ef2cf0e8794e2944a799baec084
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321094"
---
# <a name="ccomautocriticalsection-class"></a>CComAutoCriticalSection-Klasse

`CComAutoCriticalSection`bietet Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnittsobjekts.

## <a name="syntax"></a>Syntax

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComAutoCriticalSection::CComAutoCriticalSection](#ccomautocriticalsection)|Der Konstruktor.|
|[CComAutoCriticalSection::'CComAutoCriticalSection](#dtor)|Der Destruktor.|

## <a name="remarks"></a>Bemerkungen

`CComAutoCriticalSection`ist der Klasse [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)ähnlich, außer `CComAutoCriticalSection` das kritische Abschnittsobjekt im Konstruktor automatisch zu initialisieren.

In der `CComAutoCriticalSection` Regel `typedef` verwenden Sie über den Namen [AutoCriticalSection](ccommultithreadmodel-class.md#autocriticalsection). Dieser Name `CComAutoCriticalSection` verweist auf die Verwendung von [CComMultiThreadModel.](../../atl/reference/ccommultithreadmodel-class.md)

Die `Init` `Term` und Methoden von [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) sind bei Verwendung dieser Klasse nicht verfügbar.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcore.h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a>CComAutoCriticalSection::CComAutoCriticalSection

Der Konstruktor.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Bemerkungen

Ruft die Win32-Funktion [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)auf, die das Objekt des kritischen Abschnitts initialisiert.

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a>CComAutoCriticalSection::'CComAutoCriticalSection

Der Destruktor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Destruktor ruft [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)auf, wodurch alle Systemressourcen freigegeben werden, die vom kritischen Abschnittsobjekt verwendet werden.

## <a name="see-also"></a>Siehe auch

[CComFakeCriticalSection-Klasse](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[CComCriticalSection-Klasse](../../atl/reference/ccomcriticalsection-class.md)
