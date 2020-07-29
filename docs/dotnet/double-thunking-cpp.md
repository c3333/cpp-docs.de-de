---
title: Doppeltes Thunking (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: 6b2d3b4415b81dc5a9b7d0e36c154d9ee74b98ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221483"
---
# <a name="double-thunking-c"></a>Doppeltes Thunking (C++)

Double Thunking bezieht sich auf den Leistungsverlust, der auftreten kann, wenn ein Funktionsaufruf in einem verwalteten Kontext eine Visual C++ verwaltete Funktion aufruft und die Programmausführung den systemeigenen Einstiegspunkt der Funktion aufruft, um die verwaltete Funktion aufzurufen. In diesem Thema wird erläutert, wo Double Thunking auftritt und wie Sie es vermeiden können, um die Leistung zu verbessern.

## <a name="remarks"></a>Bemerkungen

Standardmäßig bewirkt die Definition einer verwalteten Funktion beim Kompilieren mit **/CLR**, dass der Compiler einen verwalteten Einstiegspunkt und einen systemeigenen Einstiegspunkt generiert. Dadurch kann die verwaltete Funktion von nativen und verwalteten Aufruf Sites aufgerufen werden. Wenn jedoch ein nativer Einstiegspunkt vorhanden ist, kann dies der Einstiegspunkt für alle Aufrufe der Funktion sein. Wenn eine aufrufende Funktion verwaltet wird, ruft der Native Einstiegspunkt den verwalteten Einstiegspunkt auf. Tatsächlich sind zwei Aufrufe erforderlich, um die Funktion aufzurufen (daher Double Thunking). Virtuelle Funktionen werden z. b. immer über einen systemeigenen Einstiegspunkt aufgerufen.

Eine Lösung besteht darin, den Compiler anzuweisen, keinen systemeigenen Einstiegspunkt für eine verwaltete Funktion zu generieren, dass die Funktion nur von einem verwalteten Kontext aus aufgerufen wird, indem Sie die [__clrcall](../cpp/clrcall.md) Aufruf Konvention verwendet.

Ebenso gilt: Wenn Sie ([dllexport, dllimport](../cpp/dllexport-dllimport.md)) eine verwaltete Funktion exportieren, wird ein nativer Einstiegspunkt generiert, und jede Funktion, die diese Funktion importiert und aufruft, wird über den systemeigenen Einstiegspunkt aufgerufen. Verwenden Sie keine native Export/Import-Semantik, um in diesem Fall doppelte Thunking zu vermeiden. verweisen Sie einfach auf die Metadaten über `#using` (siehe [#using Direktive](../preprocessor/hash-using-directive-cpp.md)).

Der Compiler wurde aktualisiert, um unnötige doppelte Thunking zu verringern. Beispielsweise wird jede Funktion mit einem verwalteten Typ in der Signatur (einschließlich Rückgabetyp) implizit als markiert `__clrcall` .

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Im folgenden Beispiel wird das Double-Thunking veranschaulicht. Bei der systemeigenen Kompilierung (ohne **/CLR**) generiert der-Aufrufe der virtuellen Funktion in `main` einen `T` -Kopierkonstruktor und einen-aufrufervorgang. Ähnliches Verhalten wird erzielt, wenn die virtuelle Funktion mit **/CLR** und deklariert wird `__clrcall` . Wenn Sie jedoch nur mit **/CLR**kompiliert werden, generiert der-Funktions aufrutor einen-aufrufkonstruktor, aber es gibt einen weiteren-aufrufkonstruktor aufgrund des vom systemeigenen zu verwaltenden Thunk.

### <a name="code"></a>Code

```cpp
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Beispielausgabe

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Das vorherige Beispiel hat das vorhanden sein von Double-Thunking veranschaulicht. Dieses Beispiel zeigt seine Auswirkung. Die **`for`** -Schleife ruft die virtuelle Funktion auf, und das Programm meldet die Ausführungszeit. Die langsamste Zeit wird gemeldet, wenn das Programm mit **/CLR**kompiliert wird. Die schnellsten Zeiten werden bei der Kompilierung ohne **/CLR** gemeldet, oder wenn die virtuelle Funktion mit deklariert wird `__clrcall` .

### <a name="code"></a>Code

```cpp
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>Beispielausgabe

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>Weitere Informationen

[Gemischte (Native und verwaltete) Assemblys](../dotnet/mixed-native-and-managed-assemblies.md)
