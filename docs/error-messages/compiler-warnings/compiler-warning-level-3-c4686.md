---
title: Compilerwarnung (Stufe 3) C4686
ms.date: 08/27/2018
f1_keywords:
- C4686
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
ms.openlocfilehash: a8eae1ddeb875d267b82c67e989cb41e8c9b2afb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185450"
---
# <a name="compiler-warning-level-3-c4686"></a>Compilerwarnung (Stufe 3) C4686

> '*benutzerdefinierter Typ*': mögliche Änderung im Verhalten, Änderung in der UDT gibt Aufruf Konvention zurück

## <a name="remarks"></a>Bemerkungen

Eine Spezialisierung einer Klassen Vorlage wurde nicht definiert, bevor Sie in einem Rückgabetyp verwendet wurde. Alle Elemente, die die Klasse instanziiert, lösen C4686; das Deklarieren einer Instanz oder das Zugreifen auf einen Member (C\<int >:: Anything) sind ebenfalls Optionen.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

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
