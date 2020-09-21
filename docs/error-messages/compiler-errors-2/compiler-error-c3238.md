---
title: Compilerfehler C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: 1f238a3be27023c755544438166aae1b2b2967d3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90741982"
---
# <a name="compiler-error-c3238"></a>Compilerfehler C3238

"Typ": Ein Typ mit diesem Namen wurde bereits an die Assembly "Assembly" weitergeleitet.

In einer Clientanwendung wurde ein Typ definiert, der über Syntax zur Typweiterleitung auch in einer referenzierten Assembly definiert ist. Es ist nicht zulässig, beide Typen im Gültigkeitsbereich der Anwendung zu definieren.

Weitere Informationen finden Sie unter [Typweiterleitung (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md) .

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird eine Assembly erstellt, die einen Typ enthält, der von einer anderen Assembly weitergeleitet wurde.

```cpp
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

Im folgende Beispiel wird eine Assembly erstellt, die die Typdefinition enthält, aber nicht nur Typweiterleitungssyntax enthält.

```cpp
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

Im folgenden Beispiel wird C3238 generiert:

```cpp
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```
