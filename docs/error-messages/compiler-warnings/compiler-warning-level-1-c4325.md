---
title: Compilerwarnung (Stufe 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 551680bc1d24097200a1e641bc4238f883ad94dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230700"
---
# <a name="compiler-warning-level-1-c4325"></a>Compilerwarnung (Stufe 1) C4325

> Attribute für Standardabschnitt '*Abschnitt*' werden ignoriert.

## <a name="remarks"></a>Bemerkungen

Die Attribute eines Standard Abschnitts dürfen nicht geändert werden. Beispiel:

```cpp
#pragma section(".sdata", long)
```

Dadurch wird der `.sdata` Standardabschnitt überschrieben, der den- **`short`** Datentyp mit dem- **`long`** Datentyp verwendet.

Standard Abschnitte, deren Attribute Sie möglicherweise nicht ändern, sind:

- . Data

- sdata

- BSS

- SBSS

- .text

- . konstant

- . skonstanten

- . rdata

- srdata

Weitere Abschnitte können später hinzugefügt werden.

## <a name="see-also"></a>Weitere Informationen

[Sektions](../../preprocessor/section.md)
