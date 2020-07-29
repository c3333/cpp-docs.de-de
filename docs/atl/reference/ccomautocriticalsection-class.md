---
title: Ccomautocriticalsection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection
- ATLCORE/ATL::CComAutoCriticalSection::CComAutoCriticalSection
helpviewer_keywords:
- CComAutoCriticalSection class
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
ms.openlocfilehash: 26b43fa4adc40993a44318c67be990c781b5cdf6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226632"
---
# <a name="ccomautocriticalsection-class"></a>Ccomautocriticalsection-Klasse

`CComAutoCriticalSection`stellt Methoden zum Abrufen und Freigeben des Besitzes eines kritischen Abschnitts Objekts bereit.

## <a name="syntax"></a>Syntax

```
class CComAutoCriticalSection : public CComCriticalSection
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Ccomautocriticalsection:: ccomautocriticalsection](#ccomautocriticalsection)|Der Konstruktor.|
|[Ccomautocriticalsection:: ~ ccomautocriticalsection](#dtor)|Der Destruktor.|

## <a name="remarks"></a>Bemerkungen

`CComAutoCriticalSection`ähnelt der Klasse [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md), mit der Ausnahme, dass `CComAutoCriticalSection` das kritische Abschnitts Objekt im Konstruktor automatisch initialisiert wird.

Normalerweise verwenden Sie `CComAutoCriticalSection` den **`typedef`** Namen [autocriticalsection](ccommultithreadmodel-class.md#autocriticalsection). Dieser Name verweist auf den Fall `CComAutoCriticalSection` , dass [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) verwendet wird.

Die `Init` -Methode und die- `Term` Methode aus [ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md) sind nicht verfügbar, wenn diese Klasse verwendet wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Ccomcriticalsection](../../atl/reference/ccomcriticalsection-class.md)

`CComAutoCriticalSection`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlcore. h

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="ccomautocriticalsection"></a>Ccomautocriticalsection:: ccomautocriticalsection

Der Konstruktor.

```
CComAutoCriticalSection();
```

### <a name="remarks"></a>Bemerkungen

Ruft die Win32-Funktion [InitializeCriticalSection](/windows/win32/api/synchapi/nf-synchapi-initializecriticalsection)auf, die das kritische Abschnitts Objekt initialisiert.

## <a name="ccomautocriticalsectionccomautocriticalsection"></a><a name="dtor"></a>Ccomautocriticalsection:: ~ ccomautocriticalsection

Der Destruktor.

```
~CComAutoCriticalSection() throw();
```

### <a name="remarks"></a>Bemerkungen

Der Dekonstruktor Ruft den [DeleteCriticalSection](/windows/win32/api/synchapi/nf-synchapi-deletecriticalsection)auf, der alle vom kritischen Abschnitts Objekt verwendeten Systemressourcen freigibt.

## <a name="see-also"></a>Siehe auch

[Ccomfakecriticalsection-Klasse](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Ccomcriticalsection-Klasse](../../atl/reference/ccomcriticalsection-class.md)
