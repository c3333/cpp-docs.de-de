---
title: InterfaceListHelper-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceListHelper
helpviewer_keywords:
- InterfaceListHelper structure
ms.assetid: 4297e419-c96b-45df-8a00-7568062125ba
ms.openlocfilehash: 1a7b4c19bbcdd4161e9078274f18f96a48f9e7d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213849"
---
# <a name="interfacelisthelper-structure"></a>InterfaceListHelper-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename T0,
    typename T1 = Nil,
    typename T2 = Nil,
    typename T3 = Nil,
    typename T4 = Nil,
    typename T5 = Nil,
    typename T6 = Nil,
    typename T7 = Nil,
    typename T8 = Nil,
    typename T9 = Nil
>
struct InterfaceListHelper;

template <typename T0>
struct InterfaceListHelper<T0, Nil, Nil, Nil, Nil, Nil, Nil, Nil, Nil>;
```

### <a name="parameters"></a>Parameter

*T0*<br/>
Der Vorlagen Parameter "0" ist erforderlich.

*T1*<br/>
Der Vorlagen Parameter 1, der standardmäßig nicht angegeben ist.

*T2*<br/>
Der Vorlagen Parameter 2, der standardmäßig nicht angegeben ist. Der dritte Vorlagen Parameter.

*Übte*<br/>
Der Vorlagen Parameter 3, der standardmäßig nicht angegeben ist.

*T4*<br/>
Der Vorlagen Parameter 4, der standardmäßig nicht angegeben ist.

*T5*<br/>
Der Vorlagen Parameter 5, der standardmäßig nicht angegeben ist.

*T6*<br/>
Der Vorlagen Parameter 6, der standardmäßig nicht angegeben ist.

*T7*<br/>
Der Vorlagen Parameter 7, der standardmäßig nicht angegeben ist.

*T8*<br/>
Der Vorlagen Parameter 8, der standardmäßig nicht angegeben ist.

*T9*<br/>
Der Vorlagen Parameter 9, der standardmäßig nicht angegeben ist.

## <a name="remarks"></a>Bemerkungen

Erstellt einen `InterfaceList` Typ, indem die angegebenen Vorlagen Parameter Argumente rekursiv angewendet werden.

Die Vorlage **interfakelisthelper** verwendet den Vorlagen Parameter *T0* , um den ersten Datenmember in einer `InterfaceList` Struktur zu definieren, und wendet dann rekursiv die Vorlage **interfakelisthelper** auf alle verbleibenden Vorlagen Parameter an. **Interfakelisthelper** wird beendet, wenn keine weiteren Vorlagen Parameter vorhanden sind.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`TypeT`|Ein Synonym für den interfakelist-Typ.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`InterfaceListHelper`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
