---
title: '&lt;Liste&gt; Funktionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425604"
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

### <a name="remarks"></a>Hinweise

Die Vorlagenfunktion führt `left.swap(right)` aus.
