---
title: Ausnahmebehandlung (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
ms.openlocfilehash: 23d65bb8056672d12e3d40f9fcab1e58bab65a3d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219702"
---
# <a name="exception-handling--ccli-and-ccx"></a>Ausnahmebehandlung (C++/CLI und C++/CX)

Sowohl Anwendungen, die mit der Compileroption `/ZW` kompiliert wurden, als auch Anwendungen, die mit der Compileroption `/clr` kompiliert wurden, verwenden *Ausnahmen*, um unerwartete Fehler während der Programmausführung zu behandeln. In den folgenden Themen wird die Ausnahmebehandlung in C++/CX- oder C++/CLI-Anwendungen erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt

[Grundlegende Konzepte bei der Verwendung von verwalteten Ausnahmen](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Beschreibt das Auslösen von Ausnahmen und die Verwendung von- **`try`** / **`catch`** Blöcken.

[Unterschiede im Ausnahme Behandlungs Verhalten unter/CLR](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Erläutert die Unterschiede beim Standardverhalten der C++-Ausnahmebehandlung.

[finally](../dotnet/finally.md)<br/>
Erläutert die Verwendung des Schlüsselworts „finally“.

[Gewusst wie: definieren und Installieren eines globalen Ausnahme Handlers](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Veranschaulicht, wie Ausnahmefehler erfasst werden können.

[Gewusst wie: Abfangen von Ausnahmen in System eigenem Code, der von MSIL ausgelöst wird](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Erläutert, wie CLR- und C++-Ausnahmen in nativem Code abgefangen werden.

[Gewusst wie: definieren und Installieren eines globalen Ausnahme Handlers](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Veranschaulicht, wie alle Ausnahmefehler abgefangen werden.

## <a name="related-sections"></a>Verwandte Abschnitte

[Behandlung von Ausnahmen](../cpp/exception-handling-in-visual-cpp.md)<br/>
Beschreibt die Ausnahmebehandlung in Standard-C++.

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
