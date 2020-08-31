---
title: Compilerwarnung (Stufe 3) C4686
description: Microsoft C++-Compilerwarnung C4686.
ms.date: 08/29/2020
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: 6886ae7f413de630457b53e85b5cd75c4542ee19
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194496"
---
# <a name="compiler-warning-level-3-c4686"></a>Compilerwarnung (Stufe 3) C4686

> '*benutzerdefinierter Typ*': mögliche Änderung im Verhalten, Änderung in der UDT gibt Aufruf Konvention zurück

## <a name="remarks"></a>Bemerkungen

Eine Spezialisierung einer Klassen Vorlage wurde nicht definiert, bevor Sie in einem Rückgabetyp verwendet wurde. Alles, was die Klasse instanziiert, löst C4686; das Deklarieren einer Instanz oder das Zugreifen auf einen Member (z. b `C<int>::some_member` .) sind ebenfalls Optionen.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [standardmäßig](../../preprocessor/compiler-warnings-that-are-off-by-default.md)deaktivierte Compilerwarnungen.

## <a name="example"></a>Beispiel

Versuchen Sie stattdessen Folgendes:

```cpp
// C4686.cpp
// compile with: /W3
#pragma warning (default : 4686)
template <class T>
class C;

template <class T>
C<T> f(T);

template <class T>
class C {};

int main() {
   f(1);   // C4686
}

template <class T>
C<T> f(T) {
   return C<int>();
}
```
