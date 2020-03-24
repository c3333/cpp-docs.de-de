---
title: Synchronisieren (C++ com-Attribut)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: a0f4702de4cfde8586cc573f9ff5a6195984d207
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214512"
---
# <a name="synchronize"></a>synchronize

Synchronisiert den Zugriff auf die Ziel Methode.

## <a name="syntax"></a>Syntax

```cpp
[synchronize]
```

## <a name="remarks"></a>Bemerkungen

Das Attribut " **Synchronisieren** C++ " implementiert die Unterstützung für die Synchronisierung der Ziel Methode eines Objekts. Durch die Synchronisierung können mehrere Objekte eine gemeinsame Ressource (z. b. eine Methode einer Klasse) verwenden, indem Sie den Zugriff auf die Ziel Methode steuern.

Der von diesem Attribut eingefügte Code Ruft die richtige `Lock` Methode (bestimmt durch das Threading Modell) am Anfang der Ziel Methode auf. Wenn die Methode beendet wird, wird `Unlock` automatisch aufgerufen. Weitere Informationen zu diesen Funktionen finden Sie unter [CComAutoThreadModule:: Lock](../../atl/reference/ccomautothreadmodule-class.md#lock) .

Dieses Attribut erfordert, dass die Attribute [coclass](coclass.md), [progid](progid.md), oder [vi_progid](vi-progid.md) (oder ein anderes Attribut, das eines der genannten impliziert) auch auf demselben Element angewendet werden. Wenn ein einzelnes Attribut verwendet wird, werden die anderen beiden automatisch angewendet. Wenn `progid` z. b. angewendet wird, werden `vi_progid` und `coclass` ebenfalls angewendet.

## <a name="example"></a>Beispiel

Der folgende Code stellt die Synchronisierung für die `UpdateBalance`-Methode des `CMyClass`-Objekts bereit.

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

### <a name="attribute-context"></a>Attributkontext

|||
|-|-|
|**Betrifft**|Class-Methode, Methode|
|**Wiederholbar**|Nein|
|**Erforderliche Attribute**|Eine oder mehrere der folgenden: `coclass`, `progid`oder `vi_progid`.|
|**Ungültige Attribute**|Keine|

Weitere Informationen zu den Attributkontexten finden Sie unter [Attributkontexte](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Weitere Informationen

[COM-Attribute](com-attributes.md)
