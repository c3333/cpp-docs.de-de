---
title: Compilerfehler C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 14f0cedc5448005a29d74f05ae3e68e74eb5cf1c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508306"
---
# <a name="compiler-error-c3171"></a>Compilerfehler C3171

"Module": Es können keine verschiedenen Modul Attribute in einem Projekt angegeben werden.

[Modul](../../windows/attributes/module-cpp.md) Attribute mit unterschiedlichen Parameterlisten wurden in zwei Dateien einer Kompilierung gefunden. `module`Pro Kompilierung kann nur ein eindeutiges Attribut angegeben werden.

Identische `module` Attribute können in mehr als einer Quell Code Datei angegeben werden.

Beispielsweise, wenn die folgenden `module` Attribute gefunden wurden:

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

und anschließend

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

der Compiler generiert C3171 (Beachten Sie die verschiedenen Versions Werte).
