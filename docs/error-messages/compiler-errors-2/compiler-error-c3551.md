---
title: Compilerfehler C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 1555817de6e50ea27a021718c8b094efeaebacde
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230843"
---
# <a name="compiler-error-c3551"></a>Compilerfehler C3551

"spät angegebener Rückgabetyp erwertet"

Wenn Sie das- **`auto`** Schlüsselwort als Platzhalter für den Rückgabetyp einer Funktion verwenden, müssen Sie einen spät angegebenen Rückgabetyp angeben. Im folgenden Beispiel ist der spät angegebene Rückgabetyp der Funktion `myFunction` ein Zeiger auf ein Array aus vier Elementen vom Typ **`int`** .

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Siehe auch

[auto](../../cpp/auto-cpp.md)
