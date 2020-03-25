---
title: Compilerwarnung (Stufe 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 601b99eec4625e9b598ece4cbb74d0039ad04bf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161788"
---
# <a name="compiler-warning-level-2-c4412"></a>Compilerwarnung (Stufe 2) C4412

> '*Function*': die Funktions Signatur enthält den Typ '*Type*'; C++ Objekte sind unsicher, um zwischen reinem und gemischtem oder nativem Code zu übergeben.

## <a name="remarks"></a>Bemerkungen

Die **/clr: pure** -Compileroption ist in Visual Studio 2015 veraltet und wird in Visual Studio 2017 nicht unterstützt. Wenn Sie über Code verfügen, der rein sein muss, empfiehlt es sich, ihn in C#zu portieren.

Der Compiler hat eine potenziell unsichere Situation festgestellt, die zu einem Laufzeitfehler führen könnte: ein-Rückruf wird von einer **/clr: pure** -Kompilierungen zu einer Funktion ausgelöst, die über dllimport importiert wurde, und die Funktions Signatur enthält einen unsicheren Typ. Ein Typ ist unsicher, wenn er eine Element Funktion oder einen Datenmember enthält, der ein unsicherer Typ oder eine Dereferenzierung zu einem unsicheren Typ ist.

Dies ist aufgrund der Unterschiede in den Standard Aufruf Konventionen zwischen reinem und nativem Code (oder gemischt Native und verwaltete) unsicher. Wenn Sie eine Funktion (über `dllimport`) in eine **/clr: pure** -Kompilierungen importieren, stellen Sie sicher, dass die Deklarationen der einzelnen Typen in der Signatur mit denen in der Kompilierungen identisch sind, die die Funktion exportiert (besonders vorsichtig bei den Unterschieden bei impliziten Aufruf Konventionen).

Eine virtuelle Member-Funktion ist besonders anfällig für unerwartete Ergebnisse.  Allerdings sollte auch eine nicht virtuelle Funktion getestet werden, um sicherzustellen, dass Sie die richtigen Ergebnisse erhalten. Wenn Sie sicher sind, dass Sie die richtigen Ergebnisse erhalten, können Sie diese Warnung ignorieren.

C4412 ist standardmäßig deaktiviert. Weitere Informationen finden Sie [unter standardmäßig](../../preprocessor/compiler-warnings-that-are-off-by-default.md) deaktivierte Compilerwarnungen und [dllexport, dllimport](../../cpp/dllexport-dllimport.md) .

Entfernen Sie alle Funktionen aus dem Typ, um diese Warnung zu beheben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4412 generiert.

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

## <a name="example"></a>Beispiel

Das folgende Beispiel ist eine Header Datei, die zwei Typen deklariert. Der `Unsafe` Typ ist unsicher, weil er über eine Member-Funktion verfügt.

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

## <a name="example"></a>Beispiel

In diesem Beispiel werden Funktionen mit den Typen exportiert, die in der Header Datei definiert sind.

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

## <a name="example"></a>Beispiel

Die Standard Aufruf Konvention in einer **/clr: pure** -Kompilierung unterscheidet sich von einer nativen Kompilierung.  Wenn C4412. h eingeschlossen ist, `Test` standardmäßig `__clrcall`. Wenn Sie dieses Programm kompilieren und ausführen ( **/c**nicht verwenden), löst das Programm eine Ausnahme aus.

Im folgenden Beispiel wird C4412 generiert.

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```
