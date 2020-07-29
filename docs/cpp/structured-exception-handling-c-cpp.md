---
title: Structured Exception Handling (C/C++)
ms.date: 08/14/2018
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 01eaeaa57ee4d09452f37a7241f89e75fdca843e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231103"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

Die strukturierte Ausnahmebehandlung (SEH) ist eine Microsoft-Erweiterung von C, mit der bestimmte außergewöhnliche Code Situationen, z. b. Hardwarefehler, ordnungsgemäß behandelt werden. Obwohl Windows und Microsoft C++ SEH unterstützen, empfehlen wir die Verwendung der ISO-Standard-C++-Ausnahmebehandlung, da der Code besser portierbar und flexibler ist. Dennoch müssen Sie zum Verwalten von vorhandenem Code oder für bestimmte Arten von Programmen möglicherweise SEH verwenden.

**Microsoft-spezifisch:**

## <a name="grammar"></a>Grammatik

*Try-außer-Anweisung* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *Verbund* Anweisung **`__except`** **(** *Ausdruck* **)** *compound-statement*

*try-endlich-Anweisung* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *compound-statement* **`__finally`** *compound-statement* Verbund Anweisung (Verbund Anweisung)

## <a name="remarks"></a>Bemerkungen

Mit Seh können Sie sicherstellen, dass Ressourcen wie Speicherblöcke und Dateien ordnungsgemäß freigegeben werden, wenn die Ausführung unerwartet beendet wird. Sie können auch bestimmte Probleme – z. b. unzureichenden Arbeitsspeicher – behandeln, indem Sie präzisen strukturierten Code verwenden, der keine- **`goto`** Anweisungen oder aufwändige Tests von Rückgabecodes verwendet.

Die Anweisungen try-except und try-finally, auf die sich dieser Artikel bezieht, sind Microsoft-Erweiterungen der Programmiersprache C. Sie unterstützen SEH, indem es Anwendungen ermöglicht wird, die Steuerung eines Programms nach Ereignissen abzurufen, die andernfalls das Beenden der Ausführung zur Folge haben würden. Obwohl SEH mit C++-Quelldateien funktioniert, ist sie nicht ausdrücklich für C++ vorgesehen. Wenn Sie SEH in einem C++-Programm verwenden, das Sie mithilfe der [/EHa-oder/EHsc](../build/reference/eh-exception-handling-model.md) -Option kompilieren, werden debugtoren für lokale Objekte aufgerufen, andere Ausführungs Verhalten werden jedoch möglicherweise nicht erwartet. Eine Abbildung finden Sie im Beispiel weiter unten in diesem Artikel. In den meisten Fällen wird anstelle von SEH empfohlen, die ISO-Standard- [C++-Ausnahmebehandlung](../cpp/try-throw-and-catch-statements-cpp.md)zu verwenden, die der Microsoft C++-Compiler ebenfalls unterstützt. Mithilfe der C++-Ausnahmebehandlung können Sie eine bessere Portierbarkeit des Codes sicherstellen, und Sie können Ausnahmen jeglichen Typs behandeln.

Wenn Sie über C-Code verfügen, der Seh verwendet, können Sie ihn mit C++-Code mischen, der die C++-Ausnahmebehandlung verwendet. Weitere Informationen finden Sie unter [behandeln strukturierter Ausnahmen in C++](../cpp/exception-handling-differences.md).

Es gibt zwei SEH-Mechanismen:

- [Ausnahmehandler](../cpp/writing-an-exception-handler.md)oder- **`__except`** Blöcke, die auf die Ausnahme reagieren oder diese verwerfen können.

- Beendigungs [Handler](../cpp/writing-a-termination-handler.md)oder- **`__finally`** Blöcke, die immer aufgerufen werden, unabhängig davon, ob eine Ausnahme beendet wird oder nicht.

Diese beiden Arten von Handlern unterscheiden sich zwar, sind allerdings hinsichtlich eines als "Entladen des Stapels" bekannten Prozesses eng miteinander verknüpft. Wenn eine strukturierte Ausnahme auftritt, sucht Windows nach dem zuletzt installierten Ausnahmehandler, der derzeit aktiv ist. Beim Handler kann eine von drei Möglichkeiten auftreten:

- Fehler beim Erkennen der Ausnahme und Übergabe des Steuerelements an andere Handler

- Erkennen der Ausnahme, diese aber zurückweisen

- Erkennen und behandeln der Ausnahme

Der Ausnahmehandler, der die Ausnahme erkennt, befindet sich möglicherweise nicht in der Funktion, die bei Auftreten der Ausnahme ausgeführt wurde. In einigen Fällen ist es möglicherweise in einer Funktion wesentlich höher auf dem Stapel. Die gegenwärtig ausgeführte Funktion sowie alle weiteren Funktionen im Stapelrahmen werden beendet. Während dieses Vorgangs wird der Stapel "unverwundet", d. h., lokale nicht statische Variablen von beendeten Funktionen werden aus dem Stapel gelöscht.

Beim Entladen des Stapels ruft das Betriebssystem alle Beendigungshandler auf, die Sie für jede Funktion geschrieben haben. Mit einem Beendigungshandler können Sie Ressourcen bereinigen, die andernfalls bei einer nicht ordnungsgemäßen Beendigung geöffnet bleiben würden. Wenn Sie einen kritischen Abschnitt eingegeben haben, können Sie ihn im Beendigungs Handler beenden. Wenn das Programm beendet werden soll, können Sie weitere Ordnungsaufgaben, z. B. das Schließen und Entfernen von temporären Dateien, ausführen.

## <a name="next-steps"></a>Nächste Schritte

- [Schreiben eines Ausnahmehandlers](../cpp/writing-an-exception-handler.md)

- [Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)

- [Behandeln strukturierter Ausnahmen in C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Beispiel

Wie bereits erwähnt, werden debugtoren für lokale Objekte aufgerufen, wenn Sie SEH in einem C++-Programm verwenden und mithilfe der **/EHa** -oder **/EHsc** -Option kompilieren. Allerdings entspricht das Verhalten während der Ausführung bei zusätzlicher Verwendung von C++-Ausnahmen möglicherweise nicht Ihren Erwartungen. In diesem Beispiel werden diese Verhaltensunterschiede veranschaulicht.

```cpp
#include <stdio.h>
#include <Windows.h>
#include <exception>

class TestClass
{
public:
    ~TestClass()
    {
        printf("Destroying TestClass!\r\n");
    }
};

__declspec(noinline) void TestCPPEX()
{
#ifdef CPPEX
    printf("Throwing C++ exception\r\n");
    throw std::exception("");
#else
    printf("Triggering SEH exception\r\n");
    volatile int *pInt = 0x00000000;
    *pInt = 20;
#endif
}

__declspec(noinline) void TestExceptions()
{
    TestClass d;
    TestCPPEX();
}

int main()
{
    __try
    {
        TestExceptions();
    }
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf("Executing SEH __except block\r\n");
    }

    return 0;
}
```

Wenn Sie **/EHsc** verwenden, um diesen Code zu kompilieren, aber das lokale Test Steuerelement `CPPEX` -Makro nicht definiert ist, wird der debugtor nicht ausgeführt, `TestClass` und die Ausgabe sieht wie folgt aus:

```Output
Triggering SEH exception
Executing SEH __except block
```

Wenn Sie **/EHsc** verwenden, um den Code zu kompilieren und `CPPEX` mithilfe von definiert wird `/DCPPEX` (sodass eine C++-Ausnahme ausgelöst wird), wird der `TestClass` debugtor ausgeführt, und die Ausgabe sieht wie folgt aus:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Wenn Sie **/EHa** verwenden, um den Code zu kompilieren, wird der `TestClass` debugtor unabhängig davon ausgeführt, ob die Ausnahme mithilfe von `std::throw` oder mithilfe von SEH ausgelöst wurde, um die Ausnahme, d `CPPEX` . h. ob definiert oder nicht, zu auslösen. Die Ausgabe sieht wie folgt aus:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Weitere Informationen finden Sie unter [/EH (Ausnahmebehandlungsmodell)](../build/reference/eh-exception-handling-model.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Behandlung von Ausnahmen](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
[Behandeln von Fehlern und Ausnahmen](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Strukturierte Ausnahmebehandlung (Windows)](/windows/win32/debug/structured-exception-handling)
