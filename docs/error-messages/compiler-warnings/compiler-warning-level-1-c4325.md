---
title: Compilerwarnung (Stufe 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: e0a13761b0657d054065358994638779817dad6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163023"
---
# <a name="compiler-warning-level-1-c4325"></a>Compilerwarnung (Stufe 1) C4325

> Attribute für Standardabschnitt '*Abschnitt*' werden ignoriert.

## <a name="remarks"></a>Bemerkungen

Die Attribute eines Standard Abschnitts dürfen nicht geändert werden. Beispiel:

```cpp
#pragma section(".sdata", long)
```

Dadurch wird der `.sdata` Standardabschnitt überschrieben, der den **Short** -Datentyp mit dem **Long** -Datentyp verwendet.

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

[section](../../preprocessor/section.md)
