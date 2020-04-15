---
title: ImplementsHelper-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: e33842f574df5617fb40c5b3f6bb8324d5ba7c1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371399"
---
# <a name="implementshelper-structure"></a>ImplementsHelper-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parameter

*RuntimeClassFlagsT*<br/>
Ein Feld mit Flags, das einen oder mehrere [RuntimeClassType-Enumeratoren](runtimeclasstype-enumeration.md) angibt.

*ILst*<br/>
Eine Liste der Schnittstellen-IDs.

*IsDelegateToClass*<br/>
Geben Sie **true an,** wenn die aktuelle Instanz von `Implements` eine Basisklasse der ersten Schnittstellen-ID in *ILst*ist. andernfalls **false**.

## <a name="remarks"></a>Bemerkungen

Hilft bei der Implementierung der [Implements-Struktur.](implements-structure.md)

Diese Vorlage durchläuft eine Liste von Schnittstellen und fügt sie als `QueryInterface`Basisklassen sowie als Informationen hinzu, die zum Aktivieren erforderlich sind.

## <a name="members"></a>Member

### <a name="protected-methods"></a>Geschützte Methoden

Name                                                    | BESCHREIBUNG
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Ruft einen Zeiger auf `IUnknown` die zugrunde `Implements` liegende Schnittstelle für die aktuelle Struktur ab.
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | Fügt die durch den aktuellen Vorlagenparameter Null in das angegebene Arrayelement angegebene Schnittstellen-ID ein.
[ImplementsHelper::IidCount](#iidcount)                 | Enthält die Anzahl der implementierten Schnittstellen-IDs im aktuellen `Implements` Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ImplementsHelper`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper::CanCastTo

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Verweis auf eine Schnittstellen-ID.

*Ppv*<br/>
Wenn dieser Vorgang erfolgreich ist, wird ein Zeiger auf die schnittstelle angezeigt, die von *riid* oder *iid*angegeben wird.

*Iid*<br/>
Verweis auf eine Schnittstellen-ID.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf die `IUnknown` zugrunde liegende Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Ruft einen Zeiger auf `IUnknown` die zugrunde `Implements` liegende Schnittstelle für die aktuelle Struktur ab.

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Ein nullbasierter Index, der das Startarrayelement für diesen Vorgang angibt. Wenn dieser Vorgang abgeschlossen ist, wird der *Index* um 1 erhöht.

*iids*<br/>
Ein Array vom Typ IIDs.

### <a name="remarks"></a>Bemerkungen

Fügt die durch den aktuellen Vorlagenparameter Null in das angegebene Arrayelement angegebene Schnittstellen-ID ein.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper::IidCount

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Bemerkungen

Enthält die Anzahl der implementierten Schnittstellen-IDs im aktuellen `Implements` Objekt.
