---
title: MixIn-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: cfa03706bc6030b337009f7228466a26e242aa6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221535"
---
# <a name="mixin-structure"></a>MixIn-Struktur

Stellt sicher, dass eine Runtime-Klasse aus Windows-Runtime-Schnittstellen (sofern vorhanden) und dann aus klassischen COM-Schnittstellen abgeleitet wird.

## <a name="syntax"></a>Syntax

```cpp
template<
    typename Derived,
    typename MixInType,
    bool hasImplements = __is_base_of(Details::ImplementsBase, MixInType)
>
struct MixIn;
```

### <a name="parameters"></a>Parameter

*Abgeleitet*<br/>
Ein Typ, der von [der-](implements-structure.md) Struktur abgeleitet wird.

*MixinType*<br/>
Ein Basistyp.

*hasimplements*<br/>
**`true`**, wenn *mixinType* von der aktuellen Implementierung des Basistyps abgeleitet ist. **`false`** andernfalls.

## <a name="remarks"></a>Bemerkungen

Wenn eine Klasse sowohl aus Windows-Runtime-als auch aus der COM-Schnittstelle der Klasse abgeleitet ist, muss die Klassen Deklarations Liste zuerst alle Windows-Runtime Schnittstellen und dann alle klassischen COM-Schnittstellen auflisten. **Mixin** stellt sicher, dass die Schnittstellen in der richtigen Reihenfolge angegeben werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`MixIn`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft:: WRL-Namespace](microsoft-wrl-namespace.md)
