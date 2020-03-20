---
title: 'Gewusst wie: Marshallen von Zeichenfolgen mit PInvoke'
ms.custom: get-started-article
ms.date: 09/09/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: e89177261aa32d34ea392030078d4088ea61e2a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545222"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Gewusst wie: Marshallen von Zeichenfolgen mit PInvoke

In diesem Thema wird erläutert, wie Native Funktionen, die Zeichen folgen im C-Stil akzeptieren, mithilfe des CLR-Zeichen folgen Typs System:: String aufgerufen werden können, indem .NET Framework Platt Form Aufruf Unterstützung Visual C++ Programmierern wird empfohlen, die C++ Interop-Features (sofern möglich) zu verwenden, da P/aufrufen wenig Kompilierzeit-Fehlerberichterstattung bietet, nicht typsicher ist und die Implementierung mühsam sein kann. Wenn die nicht verwaltete API als DLL verpackt ist und der Quellcode nicht verfügbar ist, ist P/aufrufen die einzige Option, aber andernfalls wird die [Verwendung C++ von Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)angezeigt.

Verwaltete und nicht verwaltete Zeichen folgen werden im Arbeitsspeicher unterschiedlich angeordnet. Daher erfordert das Übergeben von Zeichen folgen von verwalteten an nicht verwaltete Funktionen das <xref:System.Runtime.InteropServices.MarshalAsAttribute>-Attribut, um den Compiler anzuweisen, die erforderlichen Konvertierungs Mechanismen zum ordnungsgemäßen und sicheren Marshalling der Zeichen folgen Daten einzufügen.

Wie bei Funktionen, die nur systeminterne Datentypen verwenden, wird <xref:System.Runtime.InteropServices.DllImportAttribute> verwendet, um verwaltete Einstiegspunkte in die nativen Funktionen zu deklarieren, aber zum Übergeben von Zeichen folgen, anstatt diese Einstiegspunkte als Zeichen folgen im C-Format zu definieren, kann stattdessen ein Handle für den <xref:System.String> Typ verwendet werden. Dadurch wird der Compiler aufgefordert, Code einzufügen, der die erforderliche Konvertierung ausführt. Für jedes Funktions Argument in einer nicht verwalteten Funktion, die eine Zeichenfolge annimmt, sollte das <xref:System.Runtime.InteropServices.MarshalAsAttribute> Attribut verwendet werden, um anzugeben, dass das Zeichen folgen Objekt als Zeichenfolge im C-Format an die native Funktion gemarshallt werden soll.

Der Mars Haller umschließt den Aufrufen der nicht verwalteten Funktion in einer ausgeblendeten Wrapper Routine, die die verwaltete Zeichenfolge anheftet und in eine lokal zugewiesene Zeichenfolge im nicht verwalteten Kontext kopiert, der dann an die nicht verwaltete Funktion übergeben wird. Wenn die nicht verwaltete Funktion zurückgibt, löscht der Wrapper entweder die Ressource, oder wenn Sie sich auf dem Stapel befunden hat, wird Sie freigegeben, wenn der Wrapper den Gültigkeitsbereich verlässt. Die nicht verwaltete Funktion ist für diesen Arbeitsspeicher nicht verantwortlich. Der nicht verwaltete Code erstellt und löscht nur den Arbeitsspeicher im Heap, der durch seine eigene CRT eingerichtet ist. es gibt also nie ein Problem mit dem Mars Haller für, das eine andere CRT-Version verwendet.

Wenn Ihre nicht verwaltete Funktion eine Zeichenfolge zurückgibt, entweder als Rückgabewert oder out-Parameter, kopiert der Mars Haller Sie in eine neue verwaltete Zeichenfolge und gibt dann den Arbeitsspeicher frei. Weitere Informationen finden Sie unter [standardmäßiges Marshallingverhalten](/dotnet/framework/interop/default-marshaling-behavior) und Mars Hallen von [Daten mit Platt Form Aufruf](/dotnet/framework/interop/marshaling-data-with-platform-invoke).

## <a name="example"></a>Beispiel

Der folgende Code besteht aus einem nicht verwalteten und einem verwalteten Modul. Das nicht verwaltete Modul ist eine DLL, die eine Funktion namens "TakesAString" definiert, die eine ANSI-Zeichenfolge im C-Format in Form von "char *" akzeptiert. Das verwaltete Modul ist eine Befehlszeilen Anwendung, die die TakesAString-Funktion importiert, Sie aber als eine verwaltete System. String anstelle eines Char-\*definiert. Das <xref:System.Runtime.InteropServices.MarshalAsAttribute>-Attribut wird verwendet, um anzugeben, wie die verwaltete Zeichenfolge gemarshallt werden soll, wenn TakesAString aufgerufen wird.

```cpp
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```cpp
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

Dieses Verfahren bewirkt, dass eine Kopie der Zeichenfolge auf dem nicht verwalteten Heap erstellt wird, sodass Änderungen, die von der systemeigenen Funktion an der Zeichenfolge vorgenommen werden, nicht in der verwalteten Kopie der Zeichenfolge widergespiegelt werden.

Beachten Sie, dass kein Teil der DLL für den verwalteten Code über die herkömmliche #include-Direktive verfügbar gemacht wird. Tatsächlich wird nur zur Laufzeit auf die dll zugegriffen, sodass Probleme mit Funktionen, die mit `DllImport` importiert werden, zum Zeitpunkt der Kompilierung nicht erkannt werden.

## <a name="see-also"></a>Siehe auch

[Verwenden von explizitem PInvoke in C++ (DllImport-Attribut)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
