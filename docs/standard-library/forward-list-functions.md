---
title: '&lt;forward_list&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424800"
---
# <a name="ltforward_listgt-functions"></a>&lt;forward_list&gt;-Funktionen

## <a name="swap"></a>Wechsel

Tauscht die Elemente zweier Vorwärtslisten aus.

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Linker*\
Ein Objekt des Typs `forward_list`.

*Rechte*\
Ein Objekt des Typs `forward_list`.

### <a name="remarks"></a>Hinweise

Die Vorlagenfunktion führt `left.swap(right)` aus.
