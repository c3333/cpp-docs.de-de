---
title: try-except-Anweisung
ms.date: 10/09/2018
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: 7d3a92aa8c6d1f77a1795eabde0ae1e575bb5770
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444128"
---
# <a name="try-except-statement"></a>try-except-Anweisung

**Microsoft-spezifisch**

Die **Try-außer-** Anweisung ist eine Microsoft-Erweiterung für C C++ und Sprachen, die die strukturierte Ausnahmebehandlung unterstützen.

## <a name="syntax"></a>Syntax

> **\_\_versuchen**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//überwachten Code<br/>
> }<br/>
> **\_\_außer** ( *Ausdruck* )<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;//Ausnahmehandler-Code<br/>
> }

## <a name="remarks"></a>Bemerkungen

Die **try-with-** Anweisung ist eine Microsoft-Erweiterung für die C++ C-und die-Sprache, mit der Zielanwendungen steuern können, wann Ereignisse auftreten, die die Programmausführung normalerweise beenden. Diese Ereignisse werden als *Ausnahmen*bezeichnet, und der Mechanismus, der Ausnahmen behandelt, wird als *strukturierte Ausnahmebehandlung* (SEH) bezeichnet.

Weitere Informationen finden Sie in der [try-schließlich-Anweisung](../cpp/try-finally-statement.md).

Ausnahmen können entweder hardwarebasiert oder softwarebasiert sein. Auch wenn Anwendungen nicht von Hardware- oder Softwareausnahmen vollständig wiederhergestellt werden können, kann die strukturierte Ausnahmebehandlung das Anzeigen von Fehlerinformationen ermöglichen und den internen Zustand der Anwendung abfangen, um das Problem zu diagnostizieren. Dies ist besonders hilfreich bei zeitweilig auftretenden Problemen, die nicht leicht reproduziert werden können.

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit Win32 für C- und C++-Quelldateien. Sie ist jedoch nicht speziell für C++ entwickelt. Sie können sicherstellen, dass der Code portabler ist, indem Sie die C++-Ausnahmebehandlung verwenden. Die C++-Ausnahmebehandlung ist auch flexibler, da sie Ausnahmen eines beliebigen Typs behandeln kann. Bei C++ Programmen empfiehlt es sich, den Mechanismus für die C++ Ausnahmebehandlung zu verwenden ([try-, catch-und Throw](../cpp/try-throw-and-catch-statements-cpp.md) -Anweisungen).

Die Verbund Anweisung nach der **__try** -Klausel ist der Text oder der geschützte Abschnitt. Die Verbund Anweisung nach der **__except** -Klausel ist der Ausnahmehandler. Der Handler gibt eine Reihe von Aktionen an, die abgerufen werden, wenn eine Ausnahme während der Ausführung des Texts des geschützten Bereichs ausgelöst wird. Die Ausführung erfolgt folgendermaßen:

1. Der geschützte Bereich wird ausgeführt.

1. Wenn während der Ausführung des geschützten Abschnitts keine Ausnahme auftritt, wird die Ausführung bei der Anweisung nach der **__except** -Klausel fortgesetzt.

1. Wenn während der Ausführung des geschützten Abschnitts oder in einer Routine, die der geschützte Abschnitt aufruft, eine Ausnahme auftritt, wird der **__except** *Ausdruck* (bezeichnet als *Filter* Ausdruck) ausgewertet, und der Wert bestimmt, wie die Ausnahme behandelt wird. Es gibt drei mögliche Werte:

   - Die Ausnahme EXCEPTION_CONTINUE_EXECUTION (-1) wurde verworfen. Fortsetzen der Ausführung an der Stelle, an der die Ausnahme aufgetreten ist.

   - EXCEPTION_CONTINUE_SEARCH (0) Ausnahme wurde nicht erkannt. Fahren Sie fort, im Stapel nach einem Handler zu suchen, zuerst nach enthaltenen **try-except**-Anweisungen, dann nach Handlern mit der nächst höheren Priorität.

   - EXCEPTION_EXECUTE_HANDLER (1) Ausnahme wurde erkannt. Übertragen Sie die Steuerung an den Ausnahmehandler, indem Sie die **__except** Verbund Anweisung ausführen und dann die Ausführung nach dem Block **__except** fortsetzen.

Da der **__except** Ausdruck als C-Ausdruck ausgewertet wird, ist er auf einen einzelnen Wert, den bedingten Ausdrucks Operator oder den Komma-Operator beschränkt. Wenn eine erweiterte Verarbeitung erforderlich ist, kann der Ausdruck eine Routine aufrufen, die einen der drei Werte zurückgibt, die oben aufgelistet sind.

Jede Anwendung kann einen eigenen Ausnahmehandler haben.

Es ist nicht zulässig, zu einer **__try** -Anweisung zu springen, aber gültig, um von einer Anweisung zu springen. Der Ausnahmehandler wird nicht aufgerufen, wenn ein Prozess in der Mitte der Ausführung einer **Try-außer-** Anweisung beendet wird.

Aus Kompatibilitätsgründen mit früheren Versionen sind **_try**, **_except**und **_leave** Synonyme für **__try**, **__except**und **__leave** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

### <a name="the-__leave-keyword"></a>Das __leave-Schlüsselwort

Das **__leave** -Schlüsselwort ist nur innerhalb des geschützten Abschnitts einer **Try-außer-** Anweisung gültig, und seine Auswirkung besteht darin, bis zum Ende des geschützten Abschnitts zu springen. Die Ausführung wird mit der ersten Anweisung nach dem Ausnahmehandler fortgesetzt.

Eine **goto** -Anweisung kann auch aus dem abgesicherten Abschnitt herausspringen, und die Leistung wird nicht beeinträchtigt, da dies in einer **try-schließlich-** Anweisung der Fall ist, da keine Stapel Auflösung stattfindet. Es empfiehlt sich jedoch, anstelle einer **goto** -Anweisung das **__leave** Schlüsselwort zu verwenden, da es weniger wahrscheinlich ist, einen Programmierfehler zu erstellen, wenn der geschützte Abschnitt groß oder komplex ist.

### <a name="structured-exception-handling-intrinsic-functions"></a>Intrinsische Funktionen der strukturierten Ausnahmebehandlung

Die strukturierte Ausnahmebehandlung bietet zwei intrinsische Funktionen, die für die Verwendung mit der **Try-außer-** Anweisung verfügbar sind: `GetExceptionCode` und `GetExceptionInformation`.

`GetExceptionCode` gibt den Code (eine 32-Bit-Ganzzahl) der Ausnahme zurück.

Die intrinsische Funktion `GetExceptionInformation` gibt einen Zeiger auf eine-Struktur zurück, die zusätzliche Informationen über die Ausnahme enthält. Mit diesem Zeiger können Sie auf den Computerzustand zugreifen, der zum Zeitpunkt einer Hardwareausnahme vorhanden war. Die Struktur sieht wie folgt aus:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Die Zeiger Typen `PEXCEPTION_RECORD` und `PCONTEXT` werden in der Includedatei \<Winnt. h > definiert, und `_EXCEPTION_RECORD` und `_CONTEXT` werden in der Includedatei \<excpt. h definiert >

Sie können `GetExceptionCode` innerhalb des Ausnahme Handlers verwenden. Allerdings können Sie `GetExceptionInformation` nur innerhalb des Ausnahme Filter Ausdrucks verwenden. Die Information, auf die verwiesen wird, befindet sich im Allgemeinen auf dem Stapel und ist nicht mehr verfügbar, wenn die Steuerung an den Ausnahmehandler übertragen wird.

Die intrinsische Funktion `AbnormalTermination` ist innerhalb eines Beendigungs Handlers verfügbar. Gibt 0 zurück, wenn der Text der **Try-End-** Anweisung sequenziell beendet wird. In allen anderen Fällen wird 1 zurückgegeben.

excpt. h definiert einige alternative Namen für diese systeminternen Funktionen:

`GetExceptionCode` entspricht `_exception_code`

`GetExceptionInformation` entspricht `_exception_info`

`AbnormalTermination` entspricht `_abnormal_termination`

## <a name="example"></a>Beispiel

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>Output

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Ausnahme Handlers](../cpp/writing-an-exception-handler.md)<br/>
[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
