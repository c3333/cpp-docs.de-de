---
title: Compilerfehler C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: ca0eab35f6e60d81a324156905619ceb7ace8830
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508287"
---
# <a name="compiler-error-c3172"></a>Compilerfehler C3172

"module_name": in einem Projekt können keine unterschiedlichen idl_module Attribute angegeben werden.

[idl_module](../../windows/attributes/idl-module.md) Attribute mit demselben Namen, aber unterschiedlichen- `dllname` oder- `version` Parametern, wurden in zwei Dateien einer Kompilierung gefunden. `idl_module`Pro Kompilierung kann nur ein eindeutiges Attribut angegeben werden.

Identische `idl_module` Attribute können in mehr als einer Quell Code Datei angegeben werden.

Beispielsweise, wenn die folgenden `idl_module` Attribute gefunden wurden:

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

und anschließend

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

der Compiler generiert C3172 (Beachten Sie die verschiedenen Versions Werte).
