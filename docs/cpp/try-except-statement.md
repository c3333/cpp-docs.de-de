---
title: try-except-Anweisung
description: Der Microsoft C++-Verweis auf die __try und __except strukturierten Ausnahmebehandlungsanweisungen.
ms.date: 04/03/2020
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
ms.openlocfilehash: 132edf7cc9819637fafa3947686972d311924b99
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366240"
---
# <a name="try-except-statement"></a>try-except-Anweisung

Die **try-except-Anweisung** ist eine Microsoft-Erweiterung, die strukturierte Ausnahmebehandlungen in den Sprachen C und C++ unterstützt. Diese Erweiterung ist **Microsoft-spezifisch**.

## <a name="syntax"></a>Syntax

> **\_\_Versuchen**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;geschützter Code<br/>
> }<br/>
> außer ( *Ausdruck* ) ** \_ \_**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;Ausnahmehandlercode<br/>
> }

## <a name="remarks"></a>Bemerkungen

Die **try-except-Anweisung** ist eine Microsoft-Erweiterung der C- und C++-Sprachen. Es ermöglicht Zielanwendungen, Die Kontrolle zu erlangen, wenn Ereignisse auftreten, die normalerweise die Programmausführung beenden. Solche Ereignisse werden als *strukturierte Ausnahmen*oder kurz *Ausnahmen* bezeichnet. Der Mechanismus, der sich mit diesen Ausnahmen befasst, wird als *Structured Exception Handling* (SEH) bezeichnet.

Weitere Informationen finden Sie in der [try-finally-Anweisung](../cpp/try-finally-statement.md).

Ausnahmen können entweder hardwarebasiert oder softwarebasiert sein. Strukturierte Ausnahmebehandlung ist nützlich, auch wenn Anwendungen von Hardware- oder Softwareausnahmen nicht vollständig wiederhergestellt werden können. SEH ermöglicht es, Fehlerinformationen anzuzeigen und den internen Status der Anwendung abzufangen, um das Problem zu diagnostizieren. Es ist besonders nützlich für intermittierende Probleme, die nicht einfach zu reproduzieren sind.

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit Win32 für C- und C++-Quelldateien. Es ist jedoch nicht speziell für C++ konzipiert. Sie können sicherstellen, dass der Code portabler ist, indem Sie die C++-Ausnahmebehandlung verwenden. Die C++-Ausnahmebehandlung ist auch flexibler, da sie Ausnahmen eines beliebigen Typs behandeln kann. Für C++-Programme wird empfohlen, systemeigene C++-Ausnahmebehandlungen zu verwenden: [Try-, catch- und](../cpp/try-throw-and-catch-statements-cpp.md) throw-Anweisungen.

Die zusammengesetzte Anweisung nach der **__try-Klausel** ist der *Körper-* oder *Bewachtabschnitt.* Der **__except** Ausdruck wird auch als *Filterausdruck* bezeichnet. Sein Wert bestimmt, wie die Ausnahme behandelt wird. Die zusammengesetzte Anweisung nach der **__except-Klausel** ist der Ausnahmehandler. Der Handler gibt die Aktionen an, die ausgeführt werden sollen, wenn während der Ausführung des Bodyabschnitts eine Ausnahme ausgelöst wird. Die Ausführung erfolgt folgendermaßen:

1. Der geschützte Bereich wird ausgeführt.

1. Wenn während der Ausführung des bewachten Abschnitts keine Ausnahme auftritt, wird die Ausführung in der Anweisung nach der **__except-Klausel** fortgesetzt.

1. Wenn während der Ausführung des bewachten Abschnitts oder in einer Routine, die der bewachte Abschnitt aufruft, eine Ausnahme auftritt, wird der **__except-Ausdruck** ausgewertet. Es gibt drei mögliche Werte:

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) Die Ausnahme wird abgelehnt. Fortsetzen der Ausführung an der Stelle, an der die Ausnahme aufgetreten ist.

   - `EXCEPTION_CONTINUE_SEARCH`(0) Die Ausnahme wird nicht erkannt. Fahren Sie fort, im Stapel nach einem Handler zu suchen, zuerst nach enthaltenen **try-except**-Anweisungen, dann nach Handlern mit der nächst höheren Priorität.

   - `EXCEPTION_EXECUTE_HANDLER`(1) Die Ausnahme wird anerkannt. Übertragen Sie die Steuerung an den Ausnahmehandler, indem Sie die **__except** zusammengesetzte Anweisung ausführen, und fahren Sie dann nach dem **__except-Block** fort.

Der **__except** Ausdruck wird als C-Ausdruck ausgewertet. Sie ist auf einen einzelnen Wert, den Operator für bedingten Ausdruck oder den Kommaoperator beschränkt. Wenn eine erweiterte Verarbeitung erforderlich ist, kann der Ausdruck eine Routine aufrufen, die einen der drei Werte zurückgibt, die oben aufgelistet sind.

Jede Anwendung kann einen eigenen Ausnahmehandler haben.

Es ist nicht gültig, in eine **__try-Anweisung** zu springen, aber es ist gültig, aus einer zu springen. Der Ausnahmehandler wird nicht aufgerufen, wenn ein Prozess mitten in der Ausführung einer **try-except-Anweisung** beendet wird.

Aus Kompatibilitätmit früheren Versionen sind **_try**, **_except**und **_leave** Synonyme für **__try**, **__except**und **__leave,** es sei denn, die Compileroption [ \(/Za Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) wird angegeben.

### <a name="the-__leave-keyword"></a>Das __leave-Schlüsselwort

Das schlüsselwortlose schlüsselwortbesuchende **Schlüsselwort __leave** ist nur innerhalb des bewachten Abschnitts einer **try-except-Anweisung** gültig, und seine Wirkung besteht darin, bis zum Ende des bewachten Abschnitts zu springen. Die Ausführung wird mit der ersten Anweisung nach dem Ausnahmehandler fortgesetzt.

Eine **goto-Anweisung** kann auch aus dem bewachten Abschnitt springen, und sie beeinträchtigt die Leistung nicht, wie sie es in einer **try-finally-Anweisung** tut. Das liegt daran, dass das Stapelaufwickeln nicht auftritt. Es wird jedoch empfohlen, das **Schlüsselwort __leave** anstelle einer **goto-Anweisung** zu verwenden. Der Grund dafür ist, dass Sie weniger wahrscheinlich einen Programmierfehler machen, wenn der bewachte Abschnitt groß oder komplex ist.

### <a name="structured-exception-handling-intrinsic-functions"></a>Intrinsische Funktionen der strukturierten Ausnahmebehandlung

Die strukturierte Ausnahmebehandlung stellt zwei systeminterne Funktionen bereit, die mit der **try-except-Anweisung** verwendet werden können: [GetExceptionCode](/windows/win32/Debug/getexceptioncode) und [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`gibt den Code (eine 32-Bit-Ganzzahl) der Ausnahme zurück.

Die systeminterne Funktion `GetExceptionInformation` gibt einen Zeiger auf eine [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) Struktur zurück, die zusätzliche Informationen über die Ausnahme enthält. Mit diesem Zeiger können Sie auf den Computerzustand zugreifen, der zum Zeitpunkt einer Hardwareausnahme vorhanden war. Die Struktur sieht wie folgt aus:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Die Zeigertypen `PEXCEPTION_RECORD` `PCONTEXT` und sind in \<der Includedatei winnt.h> definiert und `_EXCEPTION_RECORD` `_CONTEXT` in der Includedatei \<excpt.h>

Sie können `GetExceptionCode` innerhalb des Ausnahmehandlers verwendet werden. Sie können jedoch `GetExceptionInformation` nur innerhalb des Ausnahmefilterausdrucks verwendet werden. Die Informationen, auf die es verweist, befinden sich im Allgemeinen auf dem Stapel und sind nicht mehr verfügbar, wenn das Steuerelement an den Ausnahmehandler übertragen wird.

Die intrinsische Funktion [AbnormalTermination](/windows/win32/Debug/abnormaltermination) ist innerhalb eines Beendigungshandlers verfügbar. Es gibt 0 zurück, wenn der Text der **try-finally-Anweisung** sequenziell beendet wird. In allen anderen Fällen wird 1 zurückgegeben.

\<excpt.h> definiert einige alternative Namen für diese systeminternen:

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

## <a name="see-also"></a>Siehe auch

[Schreiben eines Ausnahmehandlers](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
