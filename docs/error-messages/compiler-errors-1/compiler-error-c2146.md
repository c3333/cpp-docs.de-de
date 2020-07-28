---
title: Compilerfehler C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: c1a790902af92d72eb73be7fc2321762ab01fd8c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214762"
---
# <a name="compiler-error-c2146"></a>Compilerfehler C2146

Syntax Fehler: Fehlendes "Token" vor Bezeichner "Bezeichner"

Der Compiler hat `token` Stattdessen erwartet und gefunden `identifier` .  Mögliche Ursachen:

1. Rechtschreibfehler oder Groß-/Kleinschreibung

1. Fehlender Typspezifizierer in der Deklaration des Bezeichners.

Dieser Fehler kann durch einen typografischen Fehler verursacht werden. Fehler [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) in der Regel liegt dieser Fehler vor.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2146 generiert.

```cpp
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>Beispiel

Dieser Fehler kann auch infolge einer compilerübereinstimmungs-Arbeit generiert werden, die für Visual Studio .NET 2003: Fehlendes **`typename`** Schlüsselwort abgeschlossen wurde.

Das folgende Beispiel wird in Visual Studio .NET 2002 kompiliert, schlägt jedoch in Visual Studio .NET 2003 fehl:

```cpp
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>Beispiel

Diese Fehlermeldung wird auch aufgrund von compilerübereinstimmungs-Aufgaben angezeigt, die für Visual Studio .NET 2003 ausgeführt wurden: explizite Spezialisierungen finden keine Vorlagen Parameter mehr aus der primären Vorlage.

Die Verwendung von `T` aus der primären Vorlage ist in der expliziten Spezialisierung nicht zulässig. Damit Code in Visual Studio .NET 2003 und Visual Studio .net gültig ist, ersetzen Sie alle Instanzen des Vorlagen Parameters in der Spezialisierung durch den explizit spezialisierten Typ.

Das folgende Beispiel wird in Visual Studio .NET kompiliert, schlägt jedoch in Visual Studio .NET 2003 fehl:

```cpp
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```
