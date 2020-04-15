---
title: Aufrufen systemeigener Funktionen aus verwaltetem Code
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: 0cdd5db4fae8d9167fa9ab1aeb6a4e8cbfe76ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372508"
---
# <a name="calling-native-functions-from-managed-code"></a>Aufrufen systemeigener Funktionen aus verwaltetem Code

Die Common Language Runtime stellt Platform Invocation Services, oder PInvoke, zur Verfügung, wodurch verwalteter Code Funktionen in C-Format in systemeigenen DLLs (Dynamic Link Libraries) aufrufen kann. Hierbei wird das gleiche Datenmarshalling verwendet wie für die COM-Interoperabilität mit der Laufzeit und für den IJW ("It Just Works")-Mechanismus.

Weitere Informationen finden Sie unter

- [Verwenden von explizitem PInvoke in C++ (DllImport-Attribut)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

In den Beispielen dieses Abschnitts wird veranschaulicht, wie `PInvoke` verwendet werden kann. `PInvoke` kann angepasstes Datenmarshalling vereinfachen, da Sie die Marshallinginformationen deklarativ in Attributen bereitstellen, anstatt prozeduralen Marshallingcode zu schreiben.

> [!NOTE]
> Die Marshallingbibliothek bietet eine alternative Möglichkeit, Daten auf optimierte Weise zwischen nativen und verwalteten Umgebungen zu marshallen. Weitere Informationen zur Marshallingbibliothek finden Sie unter [Übersicht über Das Marshalling in C++.](../dotnet/overview-of-marshaling-in-cpp.md) Die Marshallingbibliothek kann nur für Daten verwendet werden, nicht für Funktionen.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke und das DllImport-Attribut

Im folgenden Beispiel wird die Verwendung von `PInvoke` in einem Visual C++-Programm veranschaulicht. Die systemeigene Funktion puts ist in msvcrt.dll definiert. Das DllImport-Attribut wird für die Deklaration von puts verwendet.

```cpp
// platform_invocation_services.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", CharSet=CharSet::Ansi)]
extern "C" int puts(String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

Das folgende Beispiel gleicht dem vorherigen Beispiel, verwendet jedoch IJW.

```cpp
// platform_invocation_services_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <stdio.h>

int main() {
   String ^ pStr = "Hello World!";
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();
   puts(pChars);

   Marshal::FreeHGlobal((IntPtr)pChars);
}
```

### <a name="advantages-of-ijw"></a>Vorteile von IJW

- Es brauchen keine `DLLImport`-Attributdeklarationen für die nicht verwalteten APIs geschrieben zu werden, die das Programm verwendet. Schließen Sie einfach die Headerdatei ein, und stellen Sie eine Verknüpfung mit der Importbibliothek her.

- Der IJW-Mechanismus ist etwas schneller (die IJW-Stubs müssen beispielsweise nicht die Notwendigkeit zum Fixieren oder Kopieren von Datenelementen prüfen, da dies explizit durch den Entwickler geschieht).

- Leistungsaspekte werden eindeutig dargestellt. In diesem Fall wird die Tatsache dargestellt, dass Sie eine Unicode-Zeichenfolge in eine ANSI-Zeichenfolge übersetzen und eine zugehörige Speicherbelegung und -freigabe erfolgt. In diesem Fall würde ein Entwickler, der den Code mit IJW schreibt, erkennen, dass das Aufrufen von `_putws` und die Verwendung von `PtrToStringChars` das Leistungsverhalten verbessern.

- Wenn Sie viele nicht verwaltete APIs mit denselben Daten aufrufen, ist es wesentlich effizienter, die Daten einmal zu marshallen und die gemarshallte Kopie zu übergeben, als die Daten jedes Mal neu zu marshallen.

### <a name="disadvantages-of-ijw"></a>Nachteile von IJW

- Marshalling muss explizit in Code statt durch Attribute (die oft entsprechende Standards haben) angegeben werden.

- Der Marshallingcode ist inline, wodurch er stärker in den Fluss der Anwendungslogik eindringt.

- Da die expliziten Marshalling-APIs `IntPtr`-Typen für 32-Bit- zu 64-Bit-Portierbarkeit zurückgeben, müssen Sie besondere `ToPointer`-Aufrufe verwenden.

Die spezifische durch C++ verfügbare Methode ist die effizientere explizite Methode, allerdings um den Preis erhöhter Komplexität.

Wenn in der Anwendung hauptsächlich nicht verwaltete Datentypen verwendet oder mehr nicht verwaltete APIs als .NET Framework-APIs aufgerufen werden, sollten Sie die IJW-Funktion verwenden. Bei gelegentlichen Aufrufen von nicht verwalteten APIs in einer überwiegend verwalteten Anwendung fällt die Wahl subtiler aus.

## <a name="pinvoke-with-windows-apis"></a>PInvoke mit Windows-APIs

PInvoke eignet sich für aufrufende Funktionen in Windows.

In diesem Beispiel arbeitet ein Visual C++-Programm mit der MessageBox-Funktion zusammen, die Teil der Win32-API ist.

```cpp
// platform_invocation_services_4.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
typedef void* HWND;
[DllImport("user32", CharSet=CharSet::Ansi)]
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);

int main() {
   String ^ pText = "Hello World! ";
   String ^ pCaption = "PInvoke Test";
   MessageBox(0, pText, pCaption, 0);
}
```

Bei der Ausgabe handelt es sich um ein Meldungsfeld mit dem Titel PInvoke Test, das den Text Hello World! enthält.

Die Marshallinginformationen werden von PInvoke auch verwendet, um Funktionen in der DLL zu suchen. Tatsächlich gibt es in user32.dll keine MessageBox-Funktion, aber mit CharSet=CharSet::Ansi kann PInvoke die ANSI-Version, MessageBoxA, an Stelle der Unicode-Version, MessageBoxW, verwenden. Grundsätzlich sollten Sie Unicode-Versionen nicht verwalteter APIs verwenden, weil dabei die aufwändige Übersetzung des systemeigenen Unicode-Formats des .NET Framework-Zeichenfolgenobjekts in ANSI entfällt.

## <a name="when-not-to-use-pinvoke"></a>Wann PInvoke nicht zu verwenden ist

Die Verwendung von PInvoke ist nicht für alle DLL-Funktionen im C-Format geeignet. Angenommen, es gibt eine Funktion MakeSpecial in mylib.dll, die folgendermaßen deklariert ist.

`char * MakeSpecial(char * pszString);`

Zur Verwendung von PInvoke in einer Visual C++-Anwendung würde der Code in etwa folgendermaßen aussehen:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

Die Schwierigkeit dabei ist, dass wir den Speicher für die nicht verwaltete Zeichenfolge, die von MakeSpecial zurückgegeben wird, nicht löschen können. Andere über PInvoke aufgerufene Funktionen geben einen Zeiger auf einen internen Puffer zurück, der nicht durch den Benutzer freigegeben werden muss. In diesem Fall ist es naheliegend, das IJW-Feature zu verwenden.

## <a name="limitations-of-pinvoke"></a>Beschränkungen von PInvoke

Sie dürfen nicht den gleichen exakten Zeiger von einer systemeigenen Funktion zurückgeben lassen, den Sie als Parameter verwendet haben. Gibt eine native Funktion den Zeiger zurück, der mit PInvoke für sie gemarshallt wurde, kann dies Speicherschäden und Ausnahmen zur Folge haben.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

Im folgenden Beispiel wird dieses Problem veranschaulicht, und obwohl das Programm scheinbar eine korrekte Ausgabe liefert, kommt diese aus einem freigegebenen Speicherbereich.

```cpp
// platform_invocation_services_5.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
#include <limits.h>

ref struct MyPInvokeWrap {
public:
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]
   static String^ CharLower([In, Out] String ^);
};

int main() {
   String ^ strout = "AabCc";
   Console::WriteLine(strout);
   strout = MyPInvokeWrap::CharLower(strout);
   Console::WriteLine(strout);
}
```

## <a name="marshaling-arguments"></a>Marshalling von Argumenten

Zwischen verwalteten Typen und nativen primitiven C++-Typen der gleichen Form ist bei Verwendung von `PInvoke` kein Marshalling erforderlich. Zum Beispiel ist zwischen Int32 und int oder zwischen Double und double kein Marshalling erforderlich.

Aber Sie müssen Typen marshallen, die nicht das gleiche Formular aufweisen. Dazu gehören Zeichen-, Zeichenfolgen- und Strukturtypen. In der folgenden Tabelle werden die vom Marshaller für verschiedene Typen verwendeten Zuordnungen angezeigt:

|wtypes.h|Visual C++|Visual C++ mit /clr|Common Language Runtime|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|Leere\*|Leere\*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|SHORT|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|INT|INT|Int32|
|UINT|unsigned int|unsigned int|UInt32|
|LONG|long|long|Int32|
|BOOL|long|bool|Boolean|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPSTR|Char\*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const char\*|String ^|String|
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|const wchar_t\*|String ^|String|
|GLEITKOMMAZAHL|float|float|Single|
|Double|double|double|Double|

Wenn die Adresse an eine nicht verwaltete Funktion übergeben wird, fixiert der Marshaller automatisch den auf dem Laufzeitheap belegten Speicherplatz. Das Fixieren verhindert, dass der Garbage Collector den belegten Speicherblock während der Komprimierung verschiebt.

Im weiter oben gezeigten Beispiel gibt der CharSet-Parameter von DllImport an, wie verwaltete Zeichenfolgen gemarshallt werden sollen; in diesem Fall sollen sie für die native Seite zu ANSI-Zeichenfolgen gemarshallt werden.

Sie können Marshallinginformationen für einzelne Argumente einer nativen Funktion mit dem MarshalAs-Attribut angeben. Es gibt mehrere Möglichkeiten zum \* Marshallen eines String-Arguments: BStr, ANSIBStr, TBStr, LPStr, LPWStr und LPTStr. Der Standard ist LPStr.

In diesem Beispiel wird die Zeichenfolge als Doppelbyte-Unicode-Zeichenfolge, LPWStr, gemarshallt. Die Ausgabe ist der erste Buchstabe von Hello World! da das zweite Byte der gemarshallten Zeichenfolge null ist und dies als End-of-String-Marker interpretiert.

```cpp
// platform_invocation_services_3.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", EntryPoint="puts")]
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

Das MarshalAs-Attribut befindet sich im System::Runtime::InteropServices-Namespace. Das Attribut kann mit anderen Datentypen, z. B. Arrays, verwendet werden.

Wie bereits in diesem Thema erwähnt, bietet die Marshallingbibliothek eine neue, optimierte Methode, Daten zwischen nativen und verwalteten Umgebungen zu marshallen. Weitere Informationen finden Sie unter [Übersicht über das Marshalling in C++](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Überlegungen zur Leistung

Der Aufwand von PInvoke umfasst zwischen 10 und 30 x86-Anweisungen pro Aufruf. Über diesen festen Aufwand hinaus verursacht das Marshalling zusätzlichen Aufwand. Zwischen blitfähigen Typen, die in verwaltetem und nicht verwaltetem Code gleich sind, entsteht kein Aufwand durch das Marshalling. Z. B. kostet es keinen Aufwand, zwischen int und Int32 zu übersetzen.

Es verbessert die Leistung, mit möglichst wenigen PInvoke-Aufrufen so viele Daten wie möglich zu marshallen, statt mehr Aufrufe zu verwenden, die jeweils wenige Daten marshallen.

## <a name="see-also"></a>Siehe auch

[Interoperabilität von nativem Code und .NET](../dotnet/native-and-dotnet-interoperability.md)
