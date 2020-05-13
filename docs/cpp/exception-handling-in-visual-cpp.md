---
title: Ausnahmebehandlung in MSVC
description: C++-Sprachreferenzausnahmeübersicht für Diehand.
ms.date: 04/15/2020
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 0d60f49c6f1412925c19aaf497352940411b5d92
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396276"
---
# <a name="exception-handling-in-msvc"></a>Ausnahmebehandlung in MSVC

Eine Ausnahme ist ein Fehlerzustand, möglicherweise außerhalb der Steuerung des Programms, der verhindert, dass das Programm entlang des regulären Ausführungspfads fortgesetzt wird. Bestimmte Vorgänge, einschließlich Objekterstellung, Dateieingabe/-ausgabe und Funktionsaufrufe aus anderen Modulen, sind potenzielle Quellen von Ausnahmen, selbst wenn das Programm ordnungsgemäß ausgeführt wird. Stabiler Code antizipiert und behandelt Ausnahmen. Um Logikfehler zu erkennen, verwenden Sie Assertionen anstelle von Ausnahmen (siehe [Verwenden von Assertionen](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Arten von Ausnahmen

Der Microsoft C++-Compiler (MSVC) unterstützt drei Arten der Ausnahmebehandlung:

- [C++-Ausnahmebehandlung](errors-and-exception-handling-modern-cpp.md)

   Für die meisten C++-Programme sollten Sie die C++-Ausnahmebehandlung verwenden. Es ist typsicher und stellt sicher, dass Objektdestruktoren während des Stapelauflösens aufgerufen werden.

- [Strukturierte Behandlung von Ausnahmen](structured-exception-handling-c-cpp.md)

   Windows stellt einen eigenen Ausnahmemechanismus bereit, der als Structured Exception Handling (SEH) bezeichnet wird. Es wird nicht für C++- oder MFC-Programmierung empfohlen. Verwenden Sie SEH nur in MFC-fremden C-Programmen.

- [MFC-Ausnahmen](../mfc/exception-handling-in-mfc.md)

   Seit Version 3.0 verwendet MFC C++-Ausnahmen. Es unterstützt weiterhin seine älteren Ausnahmebehandlungsmakros, die C++-Ausnahmen in der Form ähneln. Informationen zum Mischen von MFC-Makros und C++-Ausnahmen finden Sie unter [Ausnahmen: Verwenden von MFC-Makros und C++-Ausnahmen](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Verwenden [/EH](../build/reference/eh-exception-handling-model.md) Sie eine /EH-Compileroption, um das Ausnahmebehandlungsmodell anzugeben, das in einem C++-Projekt verwendet werden soll. Die Standard-C++-Ausnahmebehandlung (**/EHsc**) ist die Standardeinstellung in neuen C++-Projekten in Visual Studio.

Es wird nicht empfohlen, die Mechanismen zur Ausnahmebehandlung zu mischen. Verwenden Sie z. B. keine C++-Ausnahmen mit strukturierter Ausnahmebehandlung. Wenn Sie die C++-Ausnahmebehandlung verwenden, wird Ihr Code ausschließlich portabler, und Sie können Ausnahmen eines beliebigen Typs behandeln. Weitere Informationen zu den Nachteilen der strukturierten Ausnahmebehandlung finden Sie unter [Structured Exception Handling](structured-exception-handling-c-cpp.md).

## <a name="in-this-section"></a>In diesem Abschnitt

- [Moderne C++-Best Practices für Ausnahmen und Fehlerbehandlung](errors-and-exception-handling-modern-cpp.md)

- [Wie man für Ausnahmesicherheit designt](how-to-design-for-exception-safety.md)

- [Verbinden von Code, der Ausnahmen zulässt, mit Code ohne Ausnahmen](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Die try-, catch- und throw-Anweisungen](try-throw-and-catch-statements-cpp.md)

- [Auswerten von Catch-Blöcken](how-catch-blocks-are-evaluated-cpp.md)

- [Ausnahmen und Stapelabwickeln](exceptions-and-stack-unwinding-in-cpp.md)

- [Ausnahmespezifikationen](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Nicht behandelte C++-Ausnahmen](unhandled-cpp-exceptions.md)

- [Kombination von C (strukturiert)- und C++-Ausnahmen](mixing-c-structured-and-cpp-exceptions.md)

- [Behandeln strukturierter Ausnahmen in C++](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Weitere Informationen

[C++-Sprachreferenz](cpp-language-reference.md)</br>
[GCC-Ausnahmebehandlung bei x64-Systemen](../build/exception-handling-x64.md)</br>
[Ausnahmebehandlung (C++/CLI und C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
