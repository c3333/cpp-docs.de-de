---
title: Compilerfehler C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: a68c3f06daf977bda4700a293803859d4aa96771
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216205"
---
# <a name="compiler-error-c2482"></a>Compilerfehler C2482

>"*Bezeichner*": die dynamische Initialisierung von "Thread"-Daten ist in verwaltetem oder WinRT-Code nicht zulässig.

## <a name="remarks"></a>Bemerkungen

In verwaltetem oder WinRT-Code können Variablen, die mit dem [__declspec (Thread)](../../cpp/thread.md) -speicherklassenmodifiziererattribut oder dem [thread_local](../../cpp/storage-classes-cpp.md#thread_local) Speicherklassenspezifizierer deklariert wurden, nicht mit einem Ausdruck initialisiert werden, der zur Laufzeit ausgewertet werden muss. Zum Initialisieren von- `__declspec(thread)` oder- **`thread_local`** Daten in diesen Laufzeitumgebungen ist ein statischer Ausdruck erforderlich.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2482 im verwalteten (**/CLR**) und in WinRT-Code (**/ZW**) generiert:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Um dieses Problem zu beheben, initialisieren Sie den lokalen Thread Speicher mithilfe eines Konstanten-,- **`constexpr`** oder statischen Ausdrucks. Führen Sie eine beliebige Thread spezifische Initialisierung separat aus.
