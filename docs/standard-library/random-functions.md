---
title: '&lt;random&gt;-Funktionen'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425244"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt;-Funktionen

## <a name="generate_canonical"></a>generate_canonical

Gibt einen Gleitkommawert aus einer zufälligen Sequenz zurück.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Parameter

*RealType* -\
Der ganzzahlige Gleitkommatyp. Mögliche Typen finden Sie unter [\<random>](../standard-library/random.md).

*Bits* -\
Die Anzahl der zu verwendenden Bits der Zufälligkeit.

*Generator*\
Eine Zufallszahlen-Generator-Klasse.

*Gen* -\
Ein Verweis auf eine Instanz eines Zufallszahlengenerators vom Typ *Generator*.

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion ruft `operator()` von *gen* wiederholt auf und verpackt die zurückgegebenen Werte in einen Gleit Komma Wert `x` vom Typ *RealType* , bis die angegebene Anzahl von Mantisse-Bits in `x`erfasst wurde. Die angegebene Anzahl ist die kleinere von *Bits* (die nicht NULL sein darf) und die vollständige Anzahl von Mantisse-Bits in *RealType*. Beim ersten Aufruf werden die Bits mit dem geringsten Wert ausgegeben. Die Funktion gibt `x`zurück.
