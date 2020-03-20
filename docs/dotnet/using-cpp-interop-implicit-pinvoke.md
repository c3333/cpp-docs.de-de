---
title: Verwenden von C++-Interop (implizites PInvoke)
ms.date: 11/04/2016
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
ms.openlocfilehash: d26fbefd87b3ba6d6ca7e183be78608777f383b5
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/06/2020
ms.locfileid: "79545420"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Verwenden von C++-Interop (implizites PInvoke)

Im Gegensatz zu anderen .net- C++ Sprachen verfügt Visual über Interoperabilitäts Unterstützung, mit der verwalteter und nicht verwalteter Code in derselben Anwendung und sogar in derselben Datei (mit den [verwalteten, nicht verwalteten](../preprocessor/managed-unmanaged.md) Pragmas) vorhanden sein kann. Auf diese Weise können Visual C++-Entwickler .NET-Funktionalität in vorhandene Visual C++-Anwendungen integrieren, ohne den Rest der Anwendung zu beeinträchtigen.

Sie können auch nicht verwaltete Funktionen von einer verwalteten Kompilierungen aus mithilfe von [dllexport, dllimport,](../cpp/dllexport-dllimport.md)abrufen.

Implizites PInvoke ist sinnvoll, wenn Sie das Marshalling von Funktionsparametern oder andere Details, die bei einem expliziten Aufruf von DllImportAttribute angegeben werden können, nicht festlegen müssen.

Visual C++ bietet zwei Möglichkeiten für die Interoperation von verwalteten und nicht verwalteten Funktionen:

- [Verwenden von explizitem PInvoke in C++ (DllImport-Attribut)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

Explizites PInvoke wird von .NET Framework unterstützt und ist in den meisten .NET-Sprachen verfügbar. Doch wie der Name schon sagt, ist C++-Interop Visual C++-spezifisch.

## <a name="c-interop"></a>C++ Interop

C++Interop bietet eine bessere Typsicherheit und ist in der Regel weniger mühsam zu implementieren. C++ Interop ist jedoch keine Option, wenn der nicht verwaltete Quellcode nicht verfügbar ist, oder für plattformübergreifende Projekte.

## <a name="c-com-interop"></a>C++-COM-Interop

Die von Visual C++ unterstützten Interoperabilitätsfunktionen bieten einen besonderen Vorteil gegenüber anderen .NET-Sprachen, wenn es um die Interoperation mit COM-Komponenten geht. Anstatt auf die Einschränkungen der .NET Framework [Tlbimp. exe (Typbibliothek-Import Programm)](/dotnet/framework/tools/tlbimp-exe-type-library-importer)beschränkt zu sein, z. b. eingeschränkte Unterstützung für Datentypen und die obligatorische verfügbar machung jedes Members jeder C++ com-Schnittstelle, ermöglicht Interop den Zugriff auf COM-Komponenten bei Bedarf und erfordert keine separaten Interop-Assemblys. Im Gegensatz zu C#Visual Basic und C++ kann Visual com-Objekte direkt mithilfe der üblichen com-Mechanismen (z. b. **cokreateinstance** und **QueryInterface**) verwenden. Dies ist aufgrund von C++ Interop-Features möglich, die bewirken, dass der Compiler automatisch den Übergangs Code einfügt, um von verwalteten zu nicht verwalteten Funktionen und wieder zurück zu wechseln.

Mithilfe C++ von Interop können COM-Komponenten verwendet werden, da Sie normalerweise verwendet werden, oder Sie C++ können in Klassen umschließt werden. Diese Wrapper Klassen werden als benutzerdefinierte Runtime Callable Wrapper oder CRCWs bezeichnet und haben zwei Vorteile gegenüber der Verwendung von com direkt im Anwendungscode:

- Die resultierende Klasse kann in anderen Sprachen als Visual C++verwendet werden.

- Die Details der COM-Schnittstelle können im verwalteten Client Code ausgeblendet werden. .NET-Datentypen können anstelle von systemeigenen Typen verwendet werden, und die Details des Daten Marshalling können transparent innerhalb des CRCW ausgeführt werden.

Unabhängig davon, ob com direkt oder über einen CRCW verwendet wird, müssen die anderen Argument Typen als einfache, blitfähige Typen gemarshallt werden.

## <a name="blittable-types"></a>Blitfähige Typen

Bei nicht verwalteten APIs, die einfache, systeminterne Typen verwenden (siehe [blitfähige und nicht blitfähige Typen](/dotnet/framework/interop/blittable-and-non-blittable-types)), ist keine spezielle Codierung erforderlich, da diese Datentypen die gleiche Darstellung im Arbeitsspeicher aufweisen, aber komplexere Datentypen explizites Marshalling von Daten erfordern. Ein Beispiel finden Sie unter Gewusst [wie: Aufrufen von systemeigenen DLLs aus verwaltetem Code mithilfe von PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

## <a name="example"></a>Beispiel

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>In diesem Abschnitt

- [Vorgehensweise: Marshallen von ANSI-Zeichenfolgen mit C++-Interop](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von Unicode-Zeichenfolgen mit C++-Interop](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von COM-Zeichenfolgen mit C++-Interop](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von Strukturen mit C++-Interop](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von Arrays mit C++-Interop](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von Rückrufen und Delegaten mit C++-Interop](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [Vorgehensweise: Marshallen von eingebetteten Zeigern mit C++-Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [Vorgehensweise: Zugriff auf Zeichen in einem System::String](../dotnet/how-to-access-characters-in-a-system-string.md)

- [Vorgehensweise: Umwandeln von char * String nach System::Byte Array](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [Vorgehensweise: Konvertieren von System:: String in wchar_t * oder char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Vorgehensweise: Konvertieren von System::String zu Standardzeichenfolge](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Vorgehensweise: Konvertieren einer Standardzeichenfolge nach System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Vorgehensweise: Abrufen eines Zeigers auf ein Byte-Array](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Vorgehensweise: Laden von nicht verwalteten Ressourcen in ein Byte-Array](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Vorgehensweise: Ändern der Verweisklasse in einer nativen Funktion](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Vorgehensweise: Ermitteln, ob ein Bild nativ oder CLR ist](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Vorgehensweise: Hinzufügen einer nativen DLL zum globalen Assemblycache](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Vorgehensweise: Verweis auf Werttyp in nativem Typ](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Vorgehensweise: Objektverweis in nicht verwaltetem Arbeitsspeicher](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Gewusst wie: Erkennen der/CLR-Kompilierung](../dotnet/how-to-detect-clr-compilation.md)

- [Vorgehensweise: Konvertieren zwischen System::Guid und _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Vorgehensweise: Angeben eines out-Parameters](../dotnet/how-to-specify-an-out-parameter.md)

- [Gewusst wie: Verwenden eines systemeigenen Typs in einer/CLR-Kompilierung](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Vorgehensweise: Deklarieren von Handles in nativen Typen](../dotnet/how-to-declare-handles-in-native-types.md)

- [Vorgehensweise: Kapseln einer nativen Klasse zur Verwendung in C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Informationen zur Verwendung von Delegaten in einem Interop-Szenario finden Sie unter [delegieren (C++ Komponenten Erweiterungen)](../extensions/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Siehe auch

- [Aufrufen nativer Funktionen aus verwaltetem Code](../dotnet/calling-native-functions-from-managed-code.md)
