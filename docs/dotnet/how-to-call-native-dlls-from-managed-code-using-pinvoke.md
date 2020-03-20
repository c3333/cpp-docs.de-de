---
title: 'Gewusst wie: Aufrufen von systemeigenen DLLs in verwaltetem Code mithilfe von PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: 1eb5d5669c49dd49a411c275f8845dbbab989df3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545090"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Gewusst wie: Aufrufen von systemeigenen DLLs in verwaltetem Code mithilfe von PInvoke

Funktionen, die in nicht verwalteten DLLs implementiert werden, können mit dem Platt Form Aufruf (P/aufrufen) von verwaltetem Code aufgerufen werden. Wenn der Quellcode für die dll nicht verfügbar ist, ist P/aufrufen die einzige Option für die Interoperabilität. Im Gegensatz zu anderen .NET-Sprachen stellt C++ Visual jedoch eine Alternative zu P/aufrufen bereit. Weitere Informationen finden Sie unter [using C++ Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird die Win32-Funktion [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) verwendet, um die aktuelle Auflösung des Bildschirms in Pixel abzurufen.

Für Funktionen, die nur systeminterne Typen als Argumente und Rückgabewerte verwenden, ist keine zusätzliche Arbeit erforderlich. Für andere Datentypen, wie z. b. Funktionszeiger, Arrays und Strukturen, sind zusätzliche Attribute erforderlich, um ein ordnungsgemäßes Daten Marshalling sicherzustellen.

Obwohl dies nicht erforderlich ist, empfiehlt es sich, P/aufrufen-Deklarationen statische Member einer Value-Klasse zu erstellen, sodass Sie im globalen Namespace nicht vorhanden sind, wie in diesem Beispiel gezeigt.

```cpp
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>Siehe auch

[Verwenden von explizitem PInvoke in C++ (DllImport-Attribut)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
