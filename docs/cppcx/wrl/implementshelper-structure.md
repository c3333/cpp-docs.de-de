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
ms.openlocfilehash: d7908670b67df7dbf7b2b74e98f8b59cf30f8e96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184942"
---
# <a name="implementshelper-structure"></a>ImplementsHelper-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parameter

*Runtimeclassflagst*<br/>
Ein Feld von Flags, das einen oder mehrere [runtimeclasstype](runtimeclasstype-enumeration.md) -Enumeratoren angibt.

*Ilst*<br/>
Eine Liste der Schnittstellen-IDs.

*Isdelegatedeclass*<br/>
Geben Sie **`true`** an, ob die aktuelle Instanz von `Implements` eine Basisklasse der ersten Schnittstellen-ID in *ilst*ist, und andernfalls **`false`** .

## <a name="remarks"></a>Bemerkungen

Hilft [bei der Implementierung der implementierten](implements-structure.md) -Struktur.

Diese Vorlage durchläuft eine Liste mit Schnittstellen und fügt sie als Basisklassen und als erforderliche Informationen zum Aktivieren von hinzu `QueryInterface` .

## <a name="members"></a>Member

### <a name="protected-methods"></a>Geschützte Methoden

Name                                                    | BESCHREIBUNG
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Implemenshelper:: CanCastTo](#cancastto)               | Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.
[Implemenshelper:: castto Unknown](#casttounknown)       | Ruft einen Zeiger auf die zugrunde liegende- `IUnknown` Schnittstelle für die aktuelle- `Implements` Struktur ab.
[Implemenshelper:: fillarraywithiid](#fillarraywithiid) | Fügt die vom aktuellen nullte-Vorlagen Parameter angegebene Schnittstellen-ID in das angegebene Array Element ein.
[Implemenshelper:: iidcount](#iidcount)                 | Enthält die Anzahl der implementierten Schnittstellen-IDs im aktuellen- `Implements` Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ImplementsHelper`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>Implemenshelper:: CanCastTo

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

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

*PPV*<br/>
Wenn dieser Vorgang erfolgreich ist, ein Zeiger auf die durch *riid* oder *IID*angegebene Schnittstelle.

*IID*<br/>
Verweis auf eine Schnittstellen-ID.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>Implemenshelper:: castto Unknown

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die zugrunde liegende- `IUnknown` Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Ruft einen Zeiger auf die zugrunde liegende- `IUnknown` Schnittstelle für die aktuelle- `Implements` Struktur ab.

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>Implemenshelper:: fillarraywithiid

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Ein NULL basierter Index, der das Start Array Element für diesen Vorgang angibt. Wenn dieser Vorgang abgeschlossen ist, wird der *Index* um 1 erhöht.

*IIDs*<br/>
Ein Array vom Typ IIDs.

### <a name="remarks"></a>Bemerkungen

Fügt die vom aktuellen nullte-Vorlagen Parameter angegebene Schnittstellen-ID in das angegebene Array Element ein.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>Implemenshelper:: iidcount

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Bemerkungen

Enthält die Anzahl der implementierten Schnittstellen-IDs im aktuellen- `Implements` Objekt.
