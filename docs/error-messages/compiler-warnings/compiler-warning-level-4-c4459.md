---
title: Compilerwarnung (Stufe 4) C4459
ms.date: 11/04/2016
f1_keywords:
- C4459
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
ms.openlocfilehash: d6d0a802f9f628145fbc5910aca805a5b01b94d2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214372"
---
# <a name="compiler-warning-level-4-c4459"></a>Compilerwarnung (Stufe 4) C4459

> Deklaration von "*Identifier*" blendet globale Deklaration aus

Durch die Deklaration des *Bezeichners* im lokalen Gültigkeitsbereich wird die Deklaration des identikalibenannten *Bezeichners* im globalen Gültigkeitsbereich ausgeblendet. Diese Warnung informiert Sie darüber, dass Verweise auf *Bezeichner* in diesem Bereich in die lokal deklarierte Version aufgelöst werden, nicht in der globalen Version, die möglicherweise ihre Absicht ist. Im Allgemeinen empfiehlt es sich, die Verwendung globaler Variablen als eine gute Engineering-Übung zu minimieren. Um die Belastung des globalen Namespaces zu minimieren, empfehlen wir die Verwendung eines benannten Namespace für globale Variablen.

Diese Warnung war neu in Visual Studio 2015 in der Microsoft C++-Compilerversion 18,00. Verwenden Sie die [/WV: 18](../../build/reference/compiler-option-warning-level.md) -Compileroption, um Warnungen von dieser Version des Compilers oder später während der Migration Ihres Codes zu unterdrücken.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4459 generiert:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

Eine Möglichkeit, dieses Problem zu beheben, besteht darin, einen Namespace für Ihre globalen Variablen zu erstellen, aber keine- **`using`** Direktive zu verwenden, um diesen Namespace in den Gültigkeitsbereich zu bringen, sodass alle Verweise die eindeutigen qualifizierten Namen verwenden müssen:

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
