---
title: RuntimeClassBaseT-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 06a9f73e00d541b0e5bcbe20c57befe4a67c5132
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375719"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parameter

*RuntimeClassTypeT*<br/>
Ein Feld mit Flags, das einen oder mehrere [RuntimeClassType-Enumeratoren](runtimeclasstype-enumeration.md) angibt.

## <a name="remarks"></a>Bemerkungen

Stellt Hilfsmethoden `QueryInterface` für Vorgänge und das Abrufen von Schnittstellen-IDs bereit.

## <a name="members"></a>Member

### <a name="protected-methods"></a>Geschützte Methoden

Name                                                         | BESCHREIBUNG
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.
[RuntimeClassBaseT::GetImplementedIIDS](#getimplementediids) | Ruft ein Array von Schnittstellen-IDs ab, die von einem angegebenen Typ implementiert werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`RuntimeClassBaseT`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a>RuntimeClassBaseT::AsIID

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ein Typ, der die durch den Parameter *riid*angegebene Schnittstellen-ID implementiert.

*implements*<br/>
Eine Variable des Typs, die durch den Vorlagenparameter *T*angegeben wird.

*riid*<br/>
Die abzurufende Schnittstellen-ID.

*ppvObject*<br/>
Wenn dieser Vorgang erfolgreich ist, wird ein Zeiger auf die Schnittstelle angezeigt, die durch den Parameter *riid*angegeben wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a>RuntimeClassBaseT::GetImplementedIIDS

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des *Implements-Parameters.*

*implements*<br/>
Zeiger auf den typ, der durch parameter *T*angegeben wird.

*iidCount*<br/>
Die maximale Anzahl der abzurufenden Schnittstellen-IDs.

*iids*<br/>
Wenn dieser Vorgang erfolgreich abgeschlossen wird, wird ein Array der Schnittstellen-IDs, die vom Typ *T*implementiert sind.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Ruft ein Array von Schnittstellen-IDs ab, die von einem angegebenen Typ implementiert werden.
