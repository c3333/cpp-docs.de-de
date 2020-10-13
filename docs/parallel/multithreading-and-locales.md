---
title: Multithreading und Gebietsschemas
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], multithreading
- multithreading [C++], locales
- threading [C++], locales
- per-thread locale
ms.assetid: d6fb159a-eaca-4130-a51a-f95d62f71485
ms.openlocfilehash: 82b410c592e5b68737514dda5a864c7bd15f6dc3
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008594"
---
# <a name="multithreading-and-locales"></a>Multithreading und Gebietsschemas

Sowohl die C-Lauf Zeit Bibliothek als auch die C++-Standard Bibliothek unterstützen das Ändern des Gebiets Schemas Ihres Programms. In diesem Thema werden Probleme erläutert, die bei der Verwendung der Gebiets Schema Funktionalität beider Bibliotheken in einer Multithreadanwendung auftreten.

## <a name="remarks"></a>Bemerkungen

Mit der C-Lauf Zeit Bibliothek können Sie Multithreadanwendungen mithilfe der `_beginthread` -Funktion und der- `_beginthreadex` Funktion erstellen. In diesem Thema werden nur Multithreadanwendungen behandelt, die mit diesen Funktionen erstellt wurden. Weitere Informationen finden Sie unter [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md).

Verwenden Sie die [setlocale](../preprocessor/setlocale.md) -Funktion, um das Gebiets Schema mithilfe der C-Lauf Zeit Bibliothek zu ändern. In früheren Versionen von Visual C++ hat diese Funktion immer das Gebiets Schema in der gesamten Anwendung geändert. Es gibt jetzt Unterstützung für das Festlegen des Gebiets Schemas auf Thread Basis. Dies erfolgt mithilfe der [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) -Funktion. Um anzugeben, dass [setlocale](../preprocessor/setlocale.md) nur das Gebiets Schema im aktuellen Thread ändern soll, müssen Sie `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` in diesem Thread aufrufen. Umgekehrt bewirkt das Aufrufen von, `_configthreadlocale(_DISABLE_PER_THREAD_LOCALE)` dass dieser Thread das globale Gebiets Schema verwendet, und jeder Aufruf von [setlocale](../preprocessor/setlocale.md) in diesem Thread ändert das Gebiets Schema in allen Threads, die das Thread spezifische Gebiets Schema nicht explizit aktiviert haben.

Verwenden Sie die [Locale-Klasse](../standard-library/locale-class.md), um das Gebiets Schema mithilfe der C++-Lauf Zeit Bibliothek zu ändern. Indem Sie die [locale:: Global](../standard-library/locale-class.md#global) -Methode aufrufen, ändern Sie das Gebiets Schema in jedem Thread, der das Thread spezifische Gebiets Schema nicht explizit aktiviert hat. Um das Gebiets Schema in einem einzelnen Thread oder Teil einer Anwendung zu ändern, erstellen Sie einfach eine Instanz eines- `locale` Objekts in diesem Thread oder Teil des Codes.

> [!NOTE]
> Durch den Aufruf von [locale:: Global](../standard-library/locale-class.md#global) wird das Gebiets Schema für die C++-Standard Bibliothek und die C-Lauf Zeit Bibliothek geändert. Beim Aufrufen von [setlocale](../preprocessor/setlocale.md) wird jedoch nur das Gebiets Schema für die C-Lauf Zeit Bibliothek geändert. die C++-Standard Bibliothek ist nicht betroffen.

In den folgenden Beispielen wird gezeigt, wie die [setlocale](../preprocessor/setlocale.md) -Funktion, die [Locale-Klasse](../standard-library/locale-class.md)und die [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) -Funktion verwendet werden, um das Gebiets Schema einer Anwendung in verschiedenen Szenarien zu ändern.

## <a name="example-change-locale-with-per-thread-locale-enabled"></a>Beispiel: Ändern des Gebiets Schemas mit aktiviertem Thread spezifischen Gebiets Schema

In diesem Beispiel erzeugt der Haupt Thread zwei untergeordnete Threads. Der erste Thread, Thread A, aktiviert das Thread spezifische Gebiets Schema durch Aufrufen von `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Der zweite Thread, Thread B und der Haupt Thread, aktivieren das Thread spezifische Gebiets Schema nicht. Thread A fährt dann mit der Verwendung der [setlocale](../preprocessor/setlocale.md) -Funktion der C-Lauf Zeit Bibliothek fort, das Gebiets Schema zu ändern.

Da Thread a das Thread spezifische Gebiets Schema aktiviert hat, beginnt nur die C-Lauf Zeit Bibliotheksfunktionen in Thread A mit dem Gebiets Schema "Französisch". Die c-Lauf Zeit Bibliotheksfunktionen in Thread B und im Haupt Thread verwenden weiterhin das Gebiets Schema "c". Da [setlocale](../preprocessor/setlocale.md) sich auch nicht auf das Gebiets Schema der C++-Standardbibliothek auswirkt, verwenden alle C++-Standard Bibliotheksobjekte weiterhin das Gebiets Schema "C".

```cpp
// multithread_locale_1.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "C"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "C"
```

## <a name="example-change-global-locale-with-per-thread-locale-enabled"></a>Beispiel: Ändern des globalen Gebiets Schemas mit aktiviertem Thread spezifischen Gebiets Schema

In diesem Beispiel erzeugt der Haupt Thread zwei untergeordnete Threads. Der erste Thread, Thread A, aktiviert das Thread spezifische Gebiets Schema durch Aufrufen von `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Der zweite Thread, Thread B und der Haupt Thread, aktivieren das Thread spezifische Gebiets Schema nicht. Thread A ändert dann das Gebiets Schema mithilfe der [locale:: Global](../standard-library/locale-class.md#global) -Methode der C++-Standard Bibliothek.

Da Thread a das Thread spezifische Gebiets Schema aktiviert hat, beginnt nur die C-Lauf Zeit Bibliotheksfunktionen in Thread A mit dem Gebiets Schema "Französisch". Die c-Lauf Zeit Bibliotheksfunktionen in Thread B und im Haupt Thread verwenden weiterhin das Gebiets Schema "c". Da jedoch die [locale:: Global](../standard-library/locale-class.md#global) -Methode das Gebiets Schema "Global" ändert, beginnen alle C++-Standard Bibliotheksobjekte in allen Threads mit dem Gebiets Schema "Französisch".

```cpp
// multithread_locale_2.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "French_France.1252"
[Thread A] locale::global is set to "French_France.1252"

[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "C"
[Thread B] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "C"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="example-change-locale-without-per-thread-locale-enabled"></a>Beispiel: Ändern des Gebiets Schemas ohne Thread bezogenes Gebiets Schema

In diesem Beispiel erzeugt der Haupt Thread zwei untergeordnete Threads. Der erste Thread, Thread A, aktiviert das Thread spezifische Gebiets Schema durch Aufrufen von `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Der zweite Thread, Thread B und der Haupt Thread, aktivieren das Thread spezifische Gebiets Schema nicht. Thread B ändert dann das Gebiets Schema mithilfe der [setlocale](../preprocessor/setlocale.md) -Funktion der C-Lauf Zeit Bibliothek.

Da für Thread b das Thread spezifische Gebiets Schema nicht aktiviert ist, wird die C-Lauf Zeit Bibliotheksfunktion in Thread B und im Haupt Thread mit dem Gebiets Schema "Französisch" gestartet. Die Funktionen der c-Lauf Zeit Bibliothek in Thread a verwenden weiterhin das Gebiets Schema "c", da Thread a das Thread spezifische Gebiets Schema aktiviert hat. Da [setlocale](../preprocessor/setlocale.md) sich auch nicht auf das Gebiets Schema der C++-Standardbibliothek auswirkt, verwenden alle C++-Standard Bibliotheksobjekte weiterhin das Gebiets Schema "C".

```cpp
// multithread_locale_3.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    setlocale(LC_ALL, "french");
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "C"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "C"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "C"
```

## <a name="example-change-global-locale-without-per-thread-locale-enabled"></a>Beispiel: Ändern des globalen Gebiets Schemas ohne Thread bezogenes Gebiets Schema

In diesem Beispiel erzeugt der Haupt Thread zwei untergeordnete Threads. Der erste Thread, Thread A, aktiviert das Thread spezifische Gebiets Schema durch Aufrufen von `_configthreadlocale(_ENABLE_PER_THREAD_LOCALE)` . Der zweite Thread, Thread B und der Haupt Thread, aktivieren das Thread spezifische Gebiets Schema nicht. Thread B ändert dann das Gebiets Schema mithilfe der [locale:: Global](../standard-library/locale-class.md#global) -Methode der C++-Standard Bibliothek.

Da für Thread b das Thread spezifische Gebiets Schema nicht aktiviert ist, wird die C-Lauf Zeit Bibliotheksfunktion in Thread B und im Haupt Thread mit dem Gebiets Schema "Französisch" gestartet. Die Funktionen der c-Lauf Zeit Bibliothek in Thread a verwenden weiterhin das Gebiets Schema "c", da Thread a das Thread spezifische Gebiets Schema aktiviert hat. Da jedoch die [locale:: Global](../standard-library/locale-class.md#global) -Methode das Gebiets Schema "Global" ändert, beginnen alle C++-Standard Bibliotheksobjekte in allen Threads mit dem Gebiets Schema "Französisch".

```cpp
// multithread_locale_4.cpp
// compile with: /EHsc /MD
#include <clocale>
#include <cstdio>
#include <locale>
#include <process.h>
#include <windows.h>

#define NUM_THREADS 2
using namespace std;

unsigned __stdcall RunThreadA(void *params);
unsigned __stdcall RunThreadB(void *params);

BOOL localeSet = FALSE;
BOOL configThreadLocaleCalled = FALSE;
HANDLE printMutex = CreateMutex(NULL, FALSE, NULL);

int main()
{
    HANDLE threads[NUM_THREADS];

    unsigned aID;
    threads[0] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadA, NULL, 0, &aID);

    unsigned bID;
    threads[1] = (HANDLE)_beginthreadex(
        NULL, 0, RunThreadB, NULL, 0, &bID);

    WaitForMultipleObjects(2, threads, TRUE, INFINITE);

    printf_s("[Thread main] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread main] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread main] locale::global is set to \"%s\"\n",
        locale().name().c_str());

    CloseHandle(threads[0]);
    CloseHandle(threads[1]);
    CloseHandle(printMutex);

    return 0;
}

unsigned __stdcall RunThreadA(void *params)
{
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);
    configThreadLocaleCalled = TRUE;
    while (!localeSet)
        Sleep(100);

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread A] Per-thread locale is enabled.\n");
    printf_s("[Thread A] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread A] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}

unsigned __stdcall RunThreadB(void *params)
{
    while (!configThreadLocaleCalled)
        Sleep(100);
    locale::global(locale("french"));
    localeSet = TRUE;

    WaitForSingleObject(printMutex, INFINITE);
    printf_s("[Thread B] Per-thread locale is NOT enabled.\n");
    printf_s("[Thread B] CRT locale is set to \"%s\"\n",
        setlocale(LC_ALL, NULL));
    printf_s("[Thread B] locale::global is set to \"%s\"\n\n",
        locale().name().c_str());
    ReleaseMutex(printMutex);

    return 1;
}
```

```Output
[Thread B] Per-thread locale is NOT enabled.
[Thread B] CRT locale is set to "French_France.1252"
[Thread B] locale::global is set to "French_France.1252"

[Thread A] Per-thread locale is enabled.
[Thread A] CRT locale is set to "C"
[Thread A] locale::global is set to "French_France.1252"

[Thread main] Per-thread locale is NOT enabled.
[Thread main] CRT locale is set to "French_France.1252"
[Thread main] locale::global is set to "French_France.1252"
```

## <a name="see-also"></a>Siehe auch

[Multithreading-Unterstützung für älteren Code (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)<br/>
[_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)<br/>
[setlocale](../preprocessor/setlocale.md)<br/>
[Internationalisierung](../c-runtime-library/internationalization.md)<br/>
[Gebietsschema](../c-runtime-library/locale.md)<br/>
[\<clocale>](../standard-library/clocale.md)<br/>
[\<locale>](../standard-library/locale.md)<br/>
[Locale-Klasse](../standard-library/locale-class.md)
