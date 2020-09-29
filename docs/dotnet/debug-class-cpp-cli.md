---
title: Debug-Klasse (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Trace class, Visual C++
- .NET Framework [C++], Debug class
- Debug class
ms.assetid: 076bd528-1b6f-4e8a-a372-eb5849cf969a
ms.openlocfilehash: 47e1b949cb6e998508a3bd362b1c74961cf4cc23
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414151"
---
# <a name="debug-class-ccli"></a>Debug-Klasse (C++/CLI)

Wenn Sie <xref:System.Diagnostics.Debug> in einer Visual C++ Anwendung verwenden, ändert sich das Verhalten nicht zwischen einem Debug-und einem Releasebuild.

## <a name="remarks"></a>Bemerkungen

Das Verhalten für <xref:System.Diagnostics.Trace> ist identisch mit dem Verhalten der Debug-Klasse, hängt jedoch von der definierten Symbol Ablauf Verfolgung ab. Dies bedeutet, dass Sie `#ifdef` alle Ablauf Verfolgungs bezogenen Codes benötigen, um das Debugverhalten in einem Releasebuild zu verhindern.

## <a name="example-always-executes-output-statements"></a>Beispiel: führt immer Ausgabe Anweisungen aus

### <a name="description"></a>BESCHREIBUNG

Im folgenden Beispiel werden immer die OUTPUT-Anweisungen ausgeführt, unabhängig davon, ob Sie mit **/DDEBUG** oder **/DTrace**kompilieren.

### <a name="code"></a>Code

```cpp
// mcpp_debug_class.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
   Trace::Unindent();

   Debug::WriteLine("test");
}
```

### <a name="output"></a>Ausgabe

```Output
    Entering Main
Hello World.
    Exiting Main
test
```

## <a name="example-use-ifdef-and-endif-directives"></a>Beispiel: Verwenden von #ifdef und #endif Direktiven

### <a name="description"></a>BESCHREIBUNG

Um das erwartete Verhalten (d. h. keine "Test Ausgabe" für einen Releasebuild gedruckt) zu erhalten, müssen Sie die `#ifdef` -Direktive und die- `#endif` Direktive verwenden. Das vorherige Codebeispiel wurde unten geändert, um diese Lösung zu veranschaulichen:

### <a name="code"></a>Code

```cpp
// mcpp_debug_class2.cpp
// compile with: /clr
#using <system.dll>
using namespace System::Diagnostics;
using namespace System;

int main() {
   Trace::Listeners->Add( gcnew TextWriterTraceListener( Console::Out ) );
   Trace::AutoFlush = true;
   Trace::Indent();

#ifdef TRACE   // checks for a debug build
   Trace::WriteLine( "Entering Main" );
   Console::WriteLine( "Hello World." );
   Trace::WriteLine( "Exiting Main" );
#endif
   Trace::Unindent();

#ifdef DEBUG   // checks for a debug build
   Debug::WriteLine("test");
#endif   //ends the conditional block
}
```

## <a name="see-also"></a>Siehe auch

[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
