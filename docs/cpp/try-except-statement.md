---
title: try-except-Anweisung
description: Der Microsoft C++-Verweis auf die Anweisungen für die __try und __except strukturierte Ausnahmebehandlung.
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
ms.openlocfilehash: 6d0ed9cfa290ab83693ee248da5bebae6f91de57
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87185696"
---
# <a name="try-except-statement"></a>try-except-Anweisung

Die **try-with-** Anweisung ist eine Microsoft-Erweiterung, die die strukturierte Ausnahmebehandlung in den Programmiersprachen C und C++ unterstützt. Diese Extension ist **Microsoft-spezifisch**.

## <a name="syntax"></a>Syntax

> **\_\_versu**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;geschützter Code \
> }\
> ** \_ \_ außer** ( *Ausdruck* ) \
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;ausnahmehandlercode \
> }

## <a name="remarks"></a>Bemerkungen

Die **Try-außer-** Anweisung ist eine Microsoft-Erweiterung der Programmiersprachen C und C++. Dadurch können Zielanwendungen steuern, wann Ereignisse auftreten, die normalerweise die Programmausführung beenden. Solche Ereignisse werden als *strukturierte Ausnahmen*oder kurz *Ausnahmen* bezeichnet. Der Mechanismus, der diese Ausnahmen behandelt, wird als *strukturierte Ausnahmebehandlung* (SEH) bezeichnet.

Weitere Informationen finden Sie in der [try-schließlich-Anweisung](../cpp/try-finally-statement.md).

Ausnahmen können entweder Hardware-oder Software basiert sein. Die strukturierte Ausnahmebehandlung ist hilfreich, auch wenn Anwendungen von Hardware-oder Software Ausnahmen nicht vollständig wieder hergestellt werden können. SEH ermöglicht es, Fehlerinformationen anzuzeigen und den internen Zustand der Anwendung abzufangen, um die Diagnose des Problems zu erleichtern. Dies ist besonders nützlich bei zeitweiligen Problemen, die nicht leicht zu reproduzieren sind.

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit Win32 für C- und C++-Quelldateien. Es ist jedoch nicht speziell für C++ konzipiert. Sie können sicherstellen, dass der Code portabler ist, indem Sie die C++-Ausnahmebehandlung verwenden. Die C++-Ausnahmebehandlung ist auch flexibler, da sie Ausnahmen eines beliebigen Typs behandeln kann. Für C++-Programme empfehlen wir die Verwendung der nativen C++-Ausnahmebehandlung: [try-, catch-und Throw](../cpp/try-throw-and-catch-statements-cpp.md) -Anweisungen.

Die Verbund Anweisung nach der **__try** -Klausel ist der *Text* oder der *geschützte* Abschnitt. Der **`__except`** Ausdruck wird auch als *Filter* Ausdruck bezeichnet. Der Wert bestimmt, wie die Ausnahme behandelt wird. Die Verbund Anweisung nach der- **`__except`** Klausel ist der Ausnahmehandler. Der Handler gibt die Aktionen an, die ausgeführt werden sollen, wenn während der Ausführung des Text Abschnitts eine Ausnahme ausgelöst wird. Die Ausführung erfolgt folgendermaßen:

1. Der geschützte Bereich wird ausgeführt.

1. Wenn während der Ausführung des geschützten Abschnitts keine Ausnahme auftritt, wird die Ausführung bei der Anweisung nach der-Klausel fortgesetzt **`__except`** .

1. Wenn während der Ausführung des geschützten Abschnitts oder in einer Routine, die der geschützte Abschnitt aufruft, eine Ausnahme auftritt, **`__except`** wird der Ausdruck ausgewertet. Es gibt drei mögliche Werte:

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) Die Ausnahme wurde verworfen. Fortsetzen der Ausführung an der Stelle, an der die Ausnahme aufgetreten ist.

   - `EXCEPTION_CONTINUE_SEARCH`(0) Ausnahme wird nicht erkannt. Fahren Sie fort, im Stapel nach einem Handler zu suchen, zuerst nach enthaltenen **try-except**-Anweisungen, dann nach Handlern mit der nächst höheren Priorität.

   - `EXCEPTION_EXECUTE_HANDLER`(1) Ausnahme wurde erkannt. Übertragen Sie die Steuerung an den Ausnahmehandler, indem Sie die **`__except`** Verbund Anweisung ausführen und anschließend die Ausführung nach dem Block fortsetzen **`__except`** .

Der **`__except`** Ausdruck wird als C-Ausdruck ausgewertet. Es ist auf einen einzelnen Wert, den bedingten Ausdrucks Operator oder den Komma Operator beschränkt. Wenn eine erweiterte Verarbeitung erforderlich ist, kann der Ausdruck eine Routine aufrufen, die einen der drei Werte zurückgibt, die oben aufgelistet sind.

Jede Anwendung kann einen eigenen Ausnahmehandler haben.

Es ist nicht zulässig, zu einer **__try** -Anweisung zu springen, aber gültig, um von einer zu springen. Der Ausnahmehandler wird nicht aufgerufen, wenn ein Prozess in der Mitte der Ausführung einer **Try-außer-** Anweisung beendet wird.

Aus Kompatibilitätsgründen mit früheren Versionen sind **_try**, **_except**und **_leave** Synonyme für **__try**, **`__except`** und, **`__leave`** es sei denn, die Compileroption [/Za \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

### <a name="the-__leave-keyword"></a>Das __leave-Schlüsselwort

Das **`__leave`** Schlüsselwort ist nur innerhalb des geschützten Abschnitts einer **Try-außer-** Anweisung gültig, und seine Auswirkung besteht darin, zum Ende des geschützten Abschnitts zu springen. Die Ausführung wird mit der ersten Anweisung nach dem Ausnahmehandler fortgesetzt.

Eine **`goto`** -Anweisung kann auch aus dem abgesicherten Abschnitt herausspringen, und die Leistung wird nicht beeinträchtigt, wie dies in einer **try-after-** Anweisung der Fall ist. Das liegt daran, dass die Stapel Entwicklung nicht erfolgt. Es wird jedoch empfohlen, **`__leave`** anstelle einer-Anweisung das-Schlüsselwort zu verwenden **`goto`** . Der Grund hierfür ist, dass Sie weniger wahrscheinlich einen Programmierfehler machen, wenn der geschützte Abschnitt groß oder komplex ist.

### <a name="structured-exception-handling-intrinsic-functions"></a>Intrinsische Funktionen der strukturierten Ausnahmebehandlung

Die strukturierte Ausnahmebehandlung bietet zwei intrinsische Funktionen, die für die Verwendung mit der **Try-außer-** Anweisung verfügbar sind: [GetExceptionCode](/windows/win32/Debug/getexceptioncode) und [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`Gibt den Code (eine 32-Bit-Ganzzahl) der Ausnahme zurück.

Die `GetExceptionInformation` intrinsische Funktion gibt einen Zeiger auf eine [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) -Struktur zurück, die zusätzliche Informationen über die Ausnahme enthält. Mit diesem Zeiger können Sie auf den Computerzustand zugreifen, der zum Zeitpunkt einer Hardwareausnahme vorhanden war. Die Struktur sieht wie folgt aus:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Die Zeiger Typen `PEXCEPTION_RECORD` und `PCONTEXT` werden in der Includedatei definiert \<winnt.h> , und `_EXCEPTION_RECORD` und `_CONTEXT` werden in der Includedatei definiert.\<excpt.h>

Sie können `GetExceptionCode` innerhalb des Ausnahme Handlers verwenden. Sie können jedoch `GetExceptionInformation` nur innerhalb des Ausnahme Filter Ausdrucks verwenden. Die Informationen, auf die Sie verweist, werden im Allgemeinen auf dem Stapel angezeigt und sind nicht mehr verfügbar, wenn die Steuerung an den Ausnahmehandler übertragen wird.

Die intrinsische Funktion " [abnormalbeendigung](/windows/win32/Debug/abnormaltermination) " ist innerhalb eines Beendigungs Handlers verfügbar. Gibt 0 zurück, wenn der Text der **Try-End-** Anweisung sequenziell beendet wird. In allen anderen Fällen wird 1 zurückgegeben.

\<excpt.h>definiert einige alternative Namen für diese systeminternen Funktionen:

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
[Schlüsselwörter](../cpp/keywords-cpp.md)
