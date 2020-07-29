---
title: Thread
ms.date: 05/07/2019
f1_keywords:
- thread_cpp
helpviewer_keywords:
- thread local storage (TLS)
- thread __declspec keyword
- TLS (thread local storage), compiler implementation
- __declspec keyword [C++], thread
ms.assetid: 667f2a77-6d1f-4b41-bee8-05e67324fab8
ms.openlocfilehash: 13e6d45642c08a97c06d7099b83e632501267310
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225812"
---
# <a name="thread"></a>Thread

**Microsoft-spezifisch**

Der **`thread`** Erweiterte Speicherklassenmodifizierer wird verwendet, um eine Thread lokale Variable zu deklarieren. Verwenden Sie für das Portable Äquivalent in c++ 11 und höher den [thread_local](../cpp/storage-classes-cpp.md#thread_local) Speicherklassenspezifizierer für portablen Code. Unter Windows **`thread_local`** wird mit implementiert **`__declspec(thread)`** .

## <a name="syntax"></a>Syntax

**`__declspec(thread)`***Deklarator*

## <a name="remarks"></a>Bemerkungen

Threadlokaler Speicher (TLS) ist der Mechanismus, mit dem jeder Thread in einem Multithreadprozess den Speicher für threadspezifische Daten zuordnet. In den standardmäßigen Multithreadprogrammen werden Daten auf allen Threads eines angegebenen Prozesses freigegeben, während der threadlokale Speicher der Mechanismus zum Zuordnen der threadspezifischen Daten ist. Eine umfassende Erörterung der Threads finden Sie unter [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Deklarationen von lokalen Thread Variablen müssen die [Erweiterte Attribut Syntax](../cpp/declspec.md) und das- **`__declspec`** Schlüsselwort mit dem- **`thread`** Schlüsselwort verwenden. Mit folgendem Code wird z. B. eine Ganzzahl-TLS-Variable deklariert und mit einem Wert initialisiert:

```cpp
__declspec( thread ) int tls_i = 1;
```

Wenn Sie lokale Thread Variablen in dynamisch geladenen Bibliotheken verwenden, müssen Sie die Faktoren kennen, die bewirken können, dass eine Thread lokale Variable nicht ordnungsgemäß initialisiert wird:

1. Wenn die Variable mit einem Funktionsaufruf initialisiert wird (einschließlich Konstruktoren), wird diese Funktion nur für den Thread aufgerufen, der bewirkt hat, dass die binäre/dll in den Prozess geladen wurde, und für die Threads, die nach dem Laden der Binär-/dll-Datei gestartet wurden. Die Initialisierungs Funktionen werden nicht für andere Threads aufgerufen, die bereits beim Laden der DLL ausgeführt wurden. Die dynamische Initialisierung erfolgt im DllMain-Befehl für DLL_THREAD_ATTACH, aber die DLL erhält diese Nachricht nicht, wenn sich die dll nicht im Prozess befindet, wenn der Thread gestartet wird.

1. Lokale Thread Variablen, die statisch mit Konstanten Werten initialisiert werden, werden in der Regel ordnungsgemäß für alle Threads initialisiert. Ab Dezember 2017 gibt es jedoch ein bekanntes Konformitäts Problem im Microsoft C++-Compiler, bei dem **`constexpr`** Variablen anstelle der statischen Initialisierung dynamisch empfangen werden.

   Hinweis: diese beiden Probleme werden bei zukünftigen Updates des Compilers voraussichtlich behoben.

Außerdem müssen Sie diese Richtlinien beachten, wenn Sie Thread lokale Objekte und Variablen deklarieren:

- Sie können das **`thread`** -Attribut nur auf Klassen-und Datendeklarationen und-Definitionen anwenden; **`thread`** kann nicht für Funktions Deklarationen oder-Definitionen verwendet werden.

- Sie können das- **`thread`** Attribut nur für Datenelemente mit statischer Speicherdauer angeben. Hierzu zählen globale Datenobjekte (sowohl **`static`** als auch **`extern`** ), lokale statische Objekte sowie statische Datenmember von Klassen. Sie können automatische Datenobjekte nicht mit dem-Attribut deklarieren **`thread`** .

- Sie müssen das **`thread`** -Attribut für die Deklaration und die Definition eines lokalen Thread Objekts verwenden, unabhängig davon, ob die Deklaration und Definition in der gleichen Datei oder in separaten Dateien auftreten.

- Sie können das- **`thread`** Attribut nicht als Typmodifizierer verwenden.

- Da die Deklaration von Objekten, die das- **`thread`** Attribut verwenden, zulässig ist, sind diese beiden Beispiele semantisch äquivalent:

    ```cpp
    // declspec_thread_2.cpp
    // compile with: /LD
    __declspec( thread ) class B {
    public:
       int data;
    } BObject;   // BObject declared thread local.

    class B2 {
    public:
       int data;
    };
    __declspec( thread ) B2 BObject2;   // BObject2 declared thread local.
    ```

- Standard C ermöglicht die Initialisierung eines Objekts oder einer Variablen mit einem Ausdruck, der einen Verweis auf sich selbst beinhaltet, aber nur für nicht statische Objekte. Obwohl C++ normalerweise eine solche dynamische Initialisierung eines Objekts mit einem Ausdruck zulässt, der einen Verweis auf sich selbst beinhaltet, ist dieser Initialisierungstyp für lokale Thread Objekte nicht zulässig. Beispiel:

   ```cpp
   // declspec_thread_3.cpp
   // compile with: /LD
   #define Thread __declspec( thread )
   int j = j;   // Okay in C++; C error
   Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
   ```

   Ein **`sizeof`** -Ausdruck, der das Objekt enthält, das initialisiert wird, stellt keinen Verweis auf sich selbst dar und ist in C und C++ zulässig.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Thread lokaler Speicher (TLS)](../parallel/thread-local-storage-tls.md)
