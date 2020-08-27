---
title: Structured Exception Handling (C/C++)
description: Eine Übersicht über die strukturierte Ausnahmebehandlung in Microsoft C/C++.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 142e89bc82adbe7938e8825029908e814df6055c
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898625"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

Die strukturierte Ausnahmebehandlung (SEH) ist eine Microsoft-Erweiterung von C, mit der bestimmte außergewöhnliche Code Situationen, z. b. Hardwarefehler, ordnungsgemäß behandelt werden. Obwohl Windows und Microsoft C++ SEH unterstützen, empfehlen wir die Verwendung der ISO-Standard-C++-Ausnahmebehandlung. Dadurch wird Ihr Code portabler und flexibler. Um vorhandenen Code oder bestimmte Arten von Programmen beizubehalten, müssen Sie jedoch möglicherweise SEH verwenden.

**Microsoft-spezifisch:**

## <a name="grammar"></a>Grammatik

> *`try-except-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__except`** **`(`** *`expression`* **`)`** *`compound-statement`*
>
> *`try-finally-statement`* :<br/>
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

## <a name="remarks"></a>Hinweise

Mit Seh können Sie sicherstellen, dass Ressourcen, z. b. Speicherblöcke und Dateien, ordnungsgemäß freigegeben werden, wenn die Ausführung unerwartet beendet wird. Sie können auch bestimmte Probleme – z. b. unzureichenden Arbeitsspeicher – behandeln, indem Sie präzisen strukturierten Code verwenden, der keine- **`goto`** Anweisungen oder aufwändige Tests von Rückgabecodes verwendet.

Die `try-except` -und- `try-finally` Anweisungen, auf die in diesem Artikel verwiesen wird, sind Microsoft-Erweiterungen der Programmiersprache C. Sie unterstützen SEH, indem es Anwendungen ermöglicht wird, die Steuerung eines Programms nach Ereignissen abzurufen, die andernfalls das Beenden der Ausführung zur Folge haben würden. Obwohl SEH mit C++-Quelldateien funktioniert, ist sie nicht ausdrücklich für C++ vorgesehen. Wenn Sie SEH in einem C++-Programm verwenden, das Sie mit der-Option [ `/EHa` oder `/EHsc` ](../build/reference/eh-exception-handling-model.md) der-Option kompilieren, werden debugtoren für lokale Objekte aufgerufen, andere Ausführungs Verhalten sind jedoch möglicherweise nicht das, was Sie erwarten. Eine Abbildung finden Sie im Beispiel weiter unten in diesem Artikel. In den meisten Fällen wird anstelle von SEH empfohlen, die ISO-Standard- [C++-Ausnahmebehandlung](../cpp/try-throw-and-catch-statements-cpp.md)zu verwenden, die der Microsoft C++-Compiler ebenfalls unterstützt. Mithilfe der C++-Ausnahmebehandlung können Sie eine bessere Portierbarkeit des Codes sicherstellen, und Sie können Ausnahmen jeglichen Typs behandeln.

Wenn Sie über C-Code verfügen, der Seh verwendet, können Sie ihn mit C++-Code mischen, der die C++-Ausnahmebehandlung verwendet. Weitere Informationen finden Sie unter [behandeln strukturierter Ausnahmen in C++](../cpp/exception-handling-differences.md).

Es gibt zwei SEH-Mechanismen:

- [Ausnahmehandler](../cpp/writing-an-exception-handler.md)oder- **`__except`** Blöcke, die auf die Ausnahme reagieren oder diese verwerfen können.

- Beendigungs [Handler](../cpp/writing-a-termination-handler.md)oder- **`__finally`** Blöcke, die immer aufgerufen werden, unabhängig davon, ob eine Ausnahme beendet wird oder nicht.

Diese beiden Arten von Handlern sind unterschiedlich, sind aber eng über einen Prozess verknüpft, *der als entwickeln des Stapels*bezeichnet wird. Wenn eine strukturierte Ausnahme auftritt, sucht Windows nach dem zuletzt installierten Ausnahmehandler, der derzeit aktiv ist. Beim Handler kann eine von drei Möglichkeiten auftreten:

- Fehler beim Erkennen der Ausnahme und Übergabe des Steuerelements an andere Handler

- Erkennen der Ausnahme, diese aber zurückweisen

- Erkennen und behandeln der Ausnahme

Der Ausnahmehandler, der die Ausnahme erkennt, befindet sich möglicherweise nicht in der Funktion, die bei Auftreten der Ausnahme ausgeführt wurde. Sie kann sich in einer Funktion viel höher auf dem Stapel befinden. Die gegenwärtig ausgeführte Funktion sowie alle weiteren Funktionen im Stapelrahmen werden beendet. Während dieses Vorgangs wird der Stapel *entwickelt*. Das heißt, lokale nicht statische Variablen von beendeten Funktionen werden aus dem Stapel gelöscht.

Beim Entladen des Stapels ruft das Betriebssystem alle Beendigungshandler auf, die Sie für jede Funktion geschrieben haben. Mithilfe eines Beendigungs Handlers bereinigen Sie Ressourcen, die andernfalls aufgrund einer nicht ordnungsgemäßen Beendigung geöffnet bleiben würden. Wenn Sie einen kritischen Abschnitt eingegeben haben, können Sie ihn im Beendigungs Handler beenden. Wenn das Programm heruntergefahren wird, können Sie andere Aufgaben für die Verwaltung durchführen, z. b. das Schließen und Entfernen von temporären Dateien.

## <a name="next-steps"></a>Nächste Schritte

- [Schreiben eines Ausnahmehandlers](../cpp/writing-an-exception-handler.md)

- [Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)

- [Behandeln strukturierter Ausnahmen in C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Beispiel

Wie bereits erwähnt, werden debugtoren für lokale Objekte aufgerufen, wenn Sie SEH in einem C++-Programm verwenden und mit der- **`/EHa`** Option oder der- **`/EHsc`** Option kompilieren. Das Verhalten während der Ausführung ist jedoch möglicherweise nicht das, was Sie erwarten, wenn Sie auch C++-Ausnahmen verwenden. In diesem Beispiel werden diese Verhaltensunterschiede veranschaulicht.

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

Wenn Sie verwenden **`/EHsc`** , um diesen Code zu kompilieren, aber das lokale Test Steuerelement-Makro `CPPEX` nicht definiert ist, wird der `TestClass` Dekonstruktor nicht ausgeführt. Die Ausgabe sieht wie folgt aus:

```Output
Triggering SEH exception
Executing SEH __except block
```

Wenn Sie verwenden, **`/EHsc`** um den Code zu kompilieren und `CPPEX` mithilfe von definiert wird `/DCPPEX` (sodass eine C++-Ausnahme ausgelöst wird), wird der debugtor ausgeführt `TestClass` , und die Ausgabe sieht wie folgt aus:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Wenn Sie verwenden, **`/EHa`** um den Code zu kompilieren, `TestClass` führt der debugtor aus, ob die Ausnahme mithilfe von `std::throw` oder mithilfe von SEH ausgelöst wurde, um die Ausnahme aufzurufenden. Das heißt, ob `CPPEX` definiert ist oder nicht. Die Ausgabe sieht wie folgt aus:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Weitere Informationen finden Sie unter [ `/EH` (Ausnahme Behandlungsmodell)](../build/reference/eh-exception-handling-model.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Ausnahmebehandlung](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[`<exception>`](../standard-library/exception.md)<br/>
[Fehler-und Ausnahmebehandlung](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Strukturierte Ausnahmebehandlung (Windows)](/windows/win32/debug/structured-exception-handling)
