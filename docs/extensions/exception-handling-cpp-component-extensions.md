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
ms.openlocfilehash: 9f5662bb9e744b5db3b0ab25ac4230b2f67016bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182122"
---
# <a name="exception-handling--ccli-and-ccx"></a>Ausnahmebehandlung (C++/CLI und C++/CX)

Sowohl Anwendungen, die mit der Compileroption `/ZW` kompiliert wurden, als auch Anwendungen, die mit der Compileroption `/clr` kompiliert wurden, verwenden *Ausnahmen*, um unerwartete Fehler während der Programmausführung zu behandeln. In den folgenden Themen wird die Ausnahmebehandlung in C++/CX- oder C++/CLI-Anwendungen erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt

[Grundlegende Konzepte zur Verwendung verwalteter Ausnahmen](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
Beschreibt das Auslösen von Ausnahmen und das Verwenden von **try**/**catch**-Blöcken.

[Unterschiede im Ausnahmebehandlungsverhalten unter /clr](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
Erläutert die Unterschiede beim Standardverhalten der C++-Ausnahmebehandlung.

[finally](../dotnet/finally.md)<br/>
Erläutert die Verwendung des Schlüsselworts „finally“.

[Vorgehensweise: Definieren und Installieren eines globalen Ausnahmehandlers](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Veranschaulicht, wie Ausnahmefehler erfasst werden können.

[Vorgehensweise: Abfangen von Ausnahmen, die von der MSIL ausgelöst wurden, in nativem Code](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
Erläutert, wie CLR- und C++-Ausnahmen in nativem Code abgefangen werden.

[Vorgehensweise: Definieren und Installieren eines globalen Ausnahmehandlers](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
Veranschaulicht, wie alle Ausnahmefehler abgefangen werden.

## <a name="related-sections"></a>Verwandte Abschnitte

[Behandlung von Ausnahmen](../cpp/exception-handling-in-visual-cpp.md)<br/>
Beschreibt die Ausnahmebehandlung in Standard-C++.

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
