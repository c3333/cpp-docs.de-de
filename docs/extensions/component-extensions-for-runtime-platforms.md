---
title: Komponentenerweiterungen für .NET und UWP
ms.date: 10/12/2018
ms.topic: overview
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: 887fa14153e728735937604d531782a9ae7535bb
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509710"
---
# <a name="component-extensions-for-net-and-uwp"></a>Komponentenerweiterungen für .NET und UWP

Der C++-Standard ermöglicht es Compileranbietern, nicht standardmäßige Erweiterungen für die Sprache bereitzustellen. Microsoft stellt Erweiterungen bereit, um Sie dabei zu unterstützen, nativen C++-Code mit Code zu verknüpfen, der im .NET Framework oder auf der universellen Windows-Plattform (UWP) ausgeführt wird. Die .NET-Erweiterungen heißen C++/CLI und erzeugen Code, der in der Common Language Runtime – der von .NET verwalteten Ausführungsumgebung – ausgeführt werden kann. Die UWP-Erweiterungen heißen C++/CX und erzeugen nativen Maschinencode.

> [!NOTE]
> Für neue Anwendungen empfehlen wir die Verwendung von C++/WinRT anstelle von C++/CX. C++/WinRT ist eine neue, standardmäßige C++17-Sprachprojektion für Windows-Runtime-APIs. Wir unterstützen C++/CX und WRL weiterhin, empfehlen jedoch dringend die Verwendung von C++/WinRT für neue Anwendungen. Weitere Informationen finden Sie unter [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Zwei Laufzeiten, ein Satz von Erweiterungen

C++/CLI erweitert den ISO/ANSI-C++-Standard und wird unter dem ECMA-C++/CLI-Standard definiert. Weitere Informationen Sie unter [.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Die C++/CX-Erweiterungen sind eine Teilmenge von C++/CLI. Die Erweiterungssyntax ist zwar in den meisten Fällen gleich, welcher Code generiert wird, richtet sich aber danach, ob Sie die Compileroption `/ZW` für UWP oder die Option `/clr` für .NET angeben. Diese Schalter werden automatisch festgelegt, wenn Sie Visual Studio zur Erstellung eines Projekt verwenden.

## <a name="data-type-keywords"></a>Datentyp-Schlüsselworte

Die Spracherweiterungen schließen *Aggregatschlüsselwörter* ein, die aus zwei durch Leerraum getrennte Token bestehen. Die Token haben möglicherweise eine bestimmte Bedeutung, wenn sie einzeln verwendet werden, und eine andere Bedeutung, wenn sie zusammen verwendet werden. Beispielsweise ist das Wort "ref" ein normaler Bezeichner und das Wort "class" ein Schlüsselwort, das eine systemeigene Klasse deklariert. Wenn diese Wörter jedoch zu **ref class** kombiniert werden, deklariert das resultierende Aggregatschlüsselwort eine Entität, die als *Laufzeitklasse* bezeichnet wird.

Die Erweiterungen enthalten auch *kontextbezogene* Schlüsselwörter. Ein Schlüsselwort wird abhängig von der Art der Anweisung, in der es enthalten ist, und seiner Platzierung in dieser Anweisung als kontextbezogen behandelt. Beispielsweise kann das Token "property" ein Bezeichner sein oder es kann eine spezielle Art eines öffentlichen Klassenmembers deklarieren.

In der folgenden Tabelle sind Schlüsselwörter in der C++-Spracherweiterung aufgeführt.

|Schlüsselwort|Kontextbezogen|Zweck|Verweis|
|-------------|-----------------------|-------------|---------------|
|**ref class**<br /><br /> **ref struct**|Nein|Deklariert eine Klasse.|[Klassen und Strukturen](classes-and-structs-cpp-component-extensions.md)|
|**value class**<br /><br /> **value struct**|Nein|Deklariert eine Wertklasse.|[Klassen und Strukturen](classes-and-structs-cpp-component-extensions.md)|
|**Schnittstellenklasse**<br /><br /> **interface struct**|Nein|Deklariert eine Schnittstelle.|[Schnittstellenklasse](interface-class-cpp-component-extensions.md)|
|**enum class**<br /><br /> **enum struct**|Nein|Deklariert eine Enumeration.|[enum class](enum-class-cpp-component-extensions.md)|
|**`property`**|Ja|Deklariert eine Eigenschaft.|[property](property-cpp-component-extensions.md)|
|**delegate**|Ja|Deklariert einen Delegaten.|[Delegat (C++/CLI und C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|Ja|Deklariert ein Ereignis.|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Überschreibungsspezifizierer

Sie können die folgenden Schlüsselwörter verwenden, um das Überschreibungsverhalten für Ableitung zu qualifizieren. Obwohl das **`new`** Schlüsselwort keine Erweiterung von C++ ist, wird es hier aufgeführt, da es in einem zusätzlichen Kontext verwendet werden kann. Einige Bezeichner sind auch für die systemeigene Programmierung gültig. Weitere Informationen finden Sie unter Vorgehens [Weise: Deklarieren von Überschreibungsspezifizierer in nativen Kompilierungen (C++/CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Schlüsselwort|Kontextbezogen|Zweck|Verweis|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Ja|Gibt an, dass Funktionen oder Klassen abstrakt sind.|[abstract](abstract-cpp-component-extensions.md)|
|**`new`**|Nein|Gibt an, dass eine Funktion keine Überschreibung einer Basisklassenversion ist.|[new (neuer Slot in vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Ja|Gibt an, dass eine Methode eine Überschreibung einer Basisklassenversion sein muss.|[override](override-cpp-component-extensions.md)|
|**sealed**|Ja|Verhindert, dass Klassen als Basisklassen verwendet werden.|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Schlüsselwörter für Generics

Die folgenden Schlüsselwörter wurden hinzugefügt, um generische Typen zu unterstützen. Weitere Informationen finden Sie unter [Generics](generics-cpp-component-extensions.md).

|Schlüsselwort|Kontextbezogen|Zweck|
|-------------|-----------------------|-------------|
|**allgemeinen**|Nein|Definiert einen generischen Typ.|
|**where**|Ja|Gibt die Einschränkungen an, die für einen generischen Typparameter angewendet werden.|

## <a name="miscellaneous-keywords"></a>Sonstige Schlüsselwörter

Die folgenden Schlüsselwörter wurden den C++-Erweiterungen hinzugefügt.

|Schlüsselwort|Kontextbezogen|Zweck|Verweis|
|-------------|-----------------------|-------------|---------------|
|**finally**|Ja|Gibt das Standardausnahmebehandlungsverhalten an.|[Ausnahmebehandlung](exception-handling-cpp-component-extensions.md)|
|**for each, in**|Nein|Listet die Elemente einer Auflistung auf.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Nein|Ordnet Typen auf dem Heap der Garbage Collection zu. Verwenden Sie anstelle von **`new`** und **`delete`** .|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**ref new**|Ja|Weist einen Windows-Runtime-Typ zu. Verwenden Sie anstelle von **`new`** und **`delete`** .|[ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Ja|Gibt an, dass ein Member nur in der Deklaration oder in einem statischen Konstruktor initialisiert werden kann.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literal**|Ja|Erstellt eine literale Variable.|[literal](literal-cpp-component-extensions.md)|
|**`nullptr`**|Nein|Gibt an, dass ein Handle oder ein Zeiger nicht auf ein Objekt zeigt.|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Vorlagenkonstrukte

Die folgenden Sprachkonstrukte werden nicht als Schlüsselwörter, sondern als Vorlagen implementiert. Wenn Sie die `/ZW`-Compileroption angeben, werden sie im `lang`-Namespace definiert. Wenn Sie die `/clr`-Compileroption angeben, werden sie im `cli`-Namespace definiert.

|Schlüsselwort|Zweck|Verweis|
|-------------|-------------|---------------|
|**array**|Deklariert einen Array.|[Arrays](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(Nur CLR:) Zeigt auf Daten in einem Referenztyp.|[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(Nur CLR:) Zeigt auf CLR-Referenztypen, um das Garbage Collection-System vorübergehend zu unterdrücken.|[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|Bestimmt die optimale Umwandlungsmethode für einen Laufzeittyp und führt diese aus.|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**`typeid`**|(Nur CLR:) Ruft ein <xref:System.Type?displayProperty=fullName>-Objekt ab, das den angegebenen Typ oder das angegebene Objekt beschreibt.|[TypeId](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Deklaratoren

Die folgenden Typdeklaratoren weisen die Laufzeit an, die Lebensdauer und das Löschen von zugeordneten Objekten automatisch zu verwalten.

|Operator|Zweck|Verweis|
|--------------|-------------|---------------|
|`^`|Deklariert ein Handle zu einem Objekt, d.h. einen Zeiger auf ein Windows-Runtime- oder CLR-Objekt, der automatisch gelöscht wird, wenn er nicht mehr verwendet werden kann.|[Handle für Objekt Operator (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Deklariert einen Nachverfolgungsverweis, d.h. einen Verweis auf ein Windows-Runtime- oder CLR-Objekt, der automatisch gelöscht wird, wenn er nicht mehr verwendet werden kann.|[Nach Verfolgungs Verweis Operator](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Zusätzliche Konstrukte und verwandte Themen

In diesem Abschnitt werden weitere Programmierungskonstrukte sowie Themen aufgeführt, die die CLR betreffen.

|Thema|Beschreibung|
|-----------|-----------------|
|[__identifier (C++/CLI)](identifier-cpp-cli.md)|(Windows-Runtime und CLR) Ermöglicht die Verwendung von Schlüsselwörtern als Bezeichner.|
|[Variable Argumentlisten (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows-Runtime und CLR) Ermöglicht es einer Funktion, eine variable Anzahl von Argumenten zu akzeptieren.|
|[.NET Framework Entsprechungen zu C++ Native-Typen (C++/CLI)](../dotnet/managed-types-cpp-cli.md#dotnet)|Listet die CLR-Typen auf, die anstelle von ganzzahligen C++-Typen verwendet werden.|
|[AppDomain](../cpp/appdomain.md) **`__declspec`** Modifizierer|**`__declspec`** Ein Modifizierer, der vorschreibt, dass statische und globale Variablen pro AppDomain vorhanden sind.|
|[C-stilartige Umwandlungen mit /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)|Beschreibt, wie Umwandlungen im C-Stil interpretiert werden.|
|[__clrcall](../cpp/clrcall.md)-Aufrufkonvention|Gibt die CLR-kompatible Aufrufkonvention an.|
|`__cplusplus_cli`|[Vordefinierte Makros](../preprocessor/predefined-macros.md)|
|[Benutzerdefinierte Attribute](user-defined-attributes-cpp-component-extensions.md)|Beschreibt, wie eigene CLR-Attribute definiert werden.|
|[Ausnahmebehandlung](exception-handling-cpp-component-extensions.md)|Stellt eine Übersicht über die Ausnahmebehandlung bereit.|
|[Explizite über schreibungen](explicit-overrides-cpp-component-extensions.md)|Zeigt, wie Memberfunktionen beliebige Member überschreiben können.|
|[Friend-Assemblys (C++)](../dotnet/friend-assemblies-cpp.md)|Erläutert, wie eine Clientassembly auf alle Typen in einer Assemblykomponente zugreifen kann.|
|[Boxing](boxing-cpp-component-extensions.md)|Veranschaulicht die Bedingungen, unter denen Werttypen geschachtelt werden.|
|[Compilerunterstützung für Typmerkmale](compiler-support-for-type-traits-cpp-component-extensions.md)|Erläutert, wie Eigenschaften von Typen zur Kompilierzeit erkannt werden.|
|[verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md) Pragmas|Veranschaulicht, wie verwaltete und nicht verwaltete Funktionen in demselben Modul zusammen verwendet werden können.|
|[Prozess](../cpp/process.md) **`__declspec`** Modifizierer|**`__declspec`** Ein Modifizierer, der vorschreibt, dass statische und globale Variablen pro Prozess vorhanden sind.|
|[Reflexion (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Zeigt die CLR-Version von Informationen zum Laufzeittyp.|
|[String](string-cpp-component-extensions.md)|Erläutert die Compilerkonvertierung von Zeichenfolgenliteralen zu <xref:System.String>.|
|[Typweiterleitung (C++/CLI)](type-forwarding-cpp-cli.md)|Ermöglicht das Verschieben eines Typs aus einer bereits bereitgestellten Assembly in eine andere Assembly, sodass Clientcode nicht neu kompiliert werden muss.|
|[Benutzerdefinierte Attribute](user-defined-attributes-cpp-component-extensions.md)|Veranschaulicht benutzerdefinierte Attribute.|
|[#using-Direktive](../preprocessor/hash-using-directive-cpp.md)|Importiert externe Assemblys.|
|[XML-Dokumentation](../build/reference/xml-documentation-visual-cpp.md)|Erläutert die XML-basierte Codedokumentation mit [/doc (Verarbeiten von Dokumentationskommentaren) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md).|

## <a name="see-also"></a>Weitere Informationen

[.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Native und .NET-Interoperabilität](../dotnet/native-and-dotnet-interoperability.md)
