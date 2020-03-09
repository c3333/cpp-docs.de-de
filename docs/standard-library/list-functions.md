---
title: '&lt;Liste&gt; Funktionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874426"
---
# <a name="ltlistgt-functions"></a>&lt;Liste&gt; Funktionen

## <a name="swap"></a>Wechsel

Tauscht die Elemente zweier Listen aus.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `list`.

*Rechte*\
Ein Objekt des Typs `list`.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion führt `left.swap(right)` aus.
