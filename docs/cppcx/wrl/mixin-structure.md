---
title: MixIn-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::MixIn
helpviewer_keywords:
- MixIn structure
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
ms.openlocfilehash: b302d6e08e401a24b465508d5ddabcae8b16bd8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213693"
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

*Gewonnen*<br/>
Ein Typ, der von [der-](implements-structure.md) Struktur abgeleitet wird.

*MixinType*<br/>
Ein Basistyp.

*hasimplements*<br/>
**true** , wenn *mixinType* von der aktuellen Implementierung des Basistyps abgeleitet ist. andernfalls **false** .

## <a name="remarks"></a>Bemerkungen

Wenn eine Klasse sowohl aus Windows-Runtime-als auch aus der COM-Schnittstelle der Klasse abgeleitet ist, muss die Klassen Deklarations Liste zuerst alle Windows-Runtime Schnittstellen und dann alle klassischen COM-Schnittstellen auflisten. **Mixin** stellt sicher, dass die Schnittstellen in der richtigen Reihenfolge angegeben werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`MixIn`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
