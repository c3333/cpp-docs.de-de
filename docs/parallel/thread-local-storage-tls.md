---
title: Threadlokaler Speicher (TLS)
ms.date: 08/09/2019
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
ms.openlocfilehash: f677d7382a9747df63023bd83b104a6bb3b74c1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222653"
---
# <a name="thread-local-storage-tls"></a>Threadlokaler Speicher (TLS)

Durch den lokalen Threadspeicher (Thread Local Storage, TLS) kann jeder Thread in einem bestimmten Multithreadprozess Speicherplätze für threadspezifische Daten zuordnen. Dynamisch gebundene (Laufzeit-) Thread spezifische Daten werden über die TLS-API ([TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)) unterstützt. Win32 und der Microsoft C++-Compiler unterstützen jetzt zusätzlich zur vorhandenen API-Implementierung statisch gebundene Daten (Lade Zeit) pro Thread.

## <a name="compiler-implementation-for-tls"></a><a name="_core_compiler_implementation_for_tls"></a>Compilerimplementierung für TLS

**C++ 11:**  Der **`thread_local`** Speicherklassenspezifizierer ist die empfohlene Methode zum Angeben von lokalem Thread Speicher für Objekte und Klassenmember. Weitere Informationen finden Sie unter [Speicher Klassen (C++)](../cpp/storage-classes-cpp.md).

MSVC bietet auch ein Microsoft-spezifisches Attribut, [Thread](../cpp/thread.md), als erweiterten Speicherklassenmodifizierer. Verwenden Sie das- **`__declspec`** Schlüsselwort zum Deklarieren einer **`thread`** Variablen. Mit folgendem Code wird z. B. eine Ganzzahl-TLS-Variable deklariert und mit einem Wert initialisiert:

```C
__declspec( thread ) int tls_i = 1;
```

## <a name="rules-and-limitations"></a>Regeln und Einschränkungen

Die folgenden Richtlinien müssen bei der Deklaration von statisch gebundenen lokalen Threadobjekten und -variablen beachtet werden: Diese Richtlinien gelten sowohl für [Thread](../cpp/thread.md) -als auch für [thread_local](../cpp/storage-classes-cpp.md):

- Das **`thread`** -Attribut kann nur auf Klassen-und Datendeklarationen und-Definitionen angewendet werden. Sie kann nicht für Funktions Deklarationen oder-Definitionen verwendet werden. Beispielsweise verursacht der folgende Code einen Compilerfehler:

    ```C
    __declspec( thread )void func();     // This will generate an error.
    ```

- Der- **`thread`** Modifizierer kann nur für Datenelemente mit dem Wertebereich angegeben werden **`static`** . Dazu zählen globale Datenobjekte (sowohl **`static`** als auch **`extern`** ), lokale statische Objekte sowie statische Datenmember von C++-Klassen. Automatische Datenobjekte können nicht mit dem- **`thread`** Attribut deklariert werden. Im folgenden Code werden Compilerfehler generiert:

    ```C
    void func1()
    {
        __declspec( thread )int tls_i;            // This will generate an error.
    }

    int func2(__declspec( thread )int tls_i )     // This will generate an error.
    {
        return tls_i;
    }
    ```

- Die Deklarationen und die Definition eines lokalen Thread Objekts müssen das- **`thread`** Attribut angeben. Durch folgenden Code wird z. B. ein Fehler verursacht:

    ```C
    #define Thread  __declspec( thread )
    extern int tls_i;        // This will generate an error, since the
    int __declspec( thread )tls_i;        // declaration and definition differ.
    ```

- Das- **`thread`** Attribut kann nicht als Typmodifizierer verwendet werden. Beispielsweise verursacht der folgende Code einen Compilerfehler:

    ```C
    char __declspec( thread ) *ch;        // Error
    ```

- Da die Deklaration von C++-Objekten, die das- **`thread`** Attribut verwenden, zulässig ist, sind die folgenden beiden Beispiele semantisch äquivalent:

    ```cpp
    __declspec( thread ) class B
    {
    // Code
    } BObject;  // OK--BObject is declared thread local.

    class B
    {
    // Code
    };
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.
    ```

- Die Adresse eines Thread lokalen Objekts wird nicht als konstant angesehen, und jeder Ausdruck mit einer solchen Adresse wird nicht als konstanter Ausdruck angesehen. In Standard-C ist der Effekt, dass die Verwendung der Adresse einer Thread lokalen Variablen als Initialisierer für ein Objekt oder einen Zeiger nicht zulässig ist. Folgender Code wird z. B. vom C-Compiler mit einem Fehlerflag versehen:

    ```C
    __declspec( thread ) int tls_i;
    int *p = &tls_i;       //This will generate an error in C.
    ```

   Diese Einschränkung gilt nicht für C++. Da C++ die dynamische Initialisierung aller Objekte gestattet, kann ein Objekt mit einem Ausdruck initialisiert werden, der die Adresse einer threadlokalen Variablen verwendet. Dies erfolgt genau wie bei der Erstellung von Thread lokalen Objekten. Beispielsweise generiert der zuvor gezeigte Code keinen Fehler, wenn er als C++-Quelldatei kompiliert wird. Die Adresse einer Thread lokalen Variablen ist nur gültig, solange der Thread, in dem die Adresse erstellt wurde, noch vorhanden ist.

- Standard C ermöglicht die Initialisierung eines Objekts oder einer Variablen mit einem Ausdruck, der einen Verweis auf sich selbst beinhaltet, jedoch nur für Objekte, die nicht statisch sind. Obwohl C++ im Allgemeinen eine solche dynamische Initialisierung von Objekten mit einem Ausdruck zulässt, der einen Verweis auf sich selbst beinhaltet, ist diese Art der Initialisierung mit Thread lokalen Objekten nicht zulässig. Beispiel:

    ```C
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++
    int j = j;                               // OK in C++, error in C
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++
    ```

   Ein **`sizeof`** -Ausdruck, der das Objekt enthält, das initialisiert wird, stellt keinen Verweis auf sich selbst dar und ist sowohl in C als auch in C++ aktiviert.

   C++ lässt eine solche dynamische Initialisierung von Thread Daten aufgrund möglicher zukünftiger Verbesserungen an der lokalen Thread Speicherfunktion nicht zu.

- Unter Windows-Betriebssystemen vor Windows Vista sind `__declspec( thread )` einige Einschränkungen zu beachten. Wenn eine DLL Daten oder Objekte als deklariert `__declspec( thread )` , kann dies zu einem Schutz Fehler führen, wenn Sie dynamisch geladen werden. Nachdem die DLL mit [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)geladen wurde, verursacht Sie einen Systemfehler, wenn der Code auf die `__declspec( thread )` Daten verweist. Da der globale Variablenspeicher für einen Thread zur Laufzeit reserviert wird, basiert die Größe dieses Speichers auf der Berechnung der Anforderungen der jeweiligen Anwendung sowie der Anforderungen aller DLLs, die statisch gebunden sind. Wenn Sie verwenden `LoadLibrary` , können Sie diesen Bereich nicht erweitern, um die mit deklarierten Thread lokalen Variablen zuzulassen `__declspec( thread )` . Verwenden Sie die TLS-APIs, wie z. b. [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc), in der dll, um TLS zuzuweisen, wenn die dll möglicherweise mit geladen wird `LoadLibrary` .

## <a name="see-also"></a>Weitere Informationen

[Multithreading bei C und Win32](multithreading-with-c-and-win32.md)
