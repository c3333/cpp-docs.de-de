---
title: '&lt;forward_list&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 78b1eaa44ed464de67d8ec45fab3241179bb94b9
ms.sourcegitcommit: 19016630f9d35f365e9ba249e0f3617515d7ca33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92274567"
---
# <a name="ltforward_listgt-functions"></a>&lt;forward_list&gt;-Funktionen

## <a name="swap"></a><a name="swap"></a> Wechsel

Tauscht die Elemente zweier Vorwärtslisten aus.

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*linken*\
Ein Objekt vom Typ `forward_list`.

*Richting*\
Ein Objekt vom Typ `forward_list`.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenfunktion führt `left.swap(right)` aus.
