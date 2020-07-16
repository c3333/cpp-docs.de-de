---
title: Typsystem (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: f4a6ea32681ad033b5db9451682c764f0a6d8959
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404625"
---
# <a name="type-system-ccx"></a>Typsystem (C++/CX)

Mithilfe der Windows-Runtime-Architektur können Sie C++/CX, Visual Basic, Visual c# und JavaScript verwenden, um apps und Komponenten zu schreiben, die direkt auf die Windows-API zugreifen und mit anderen Windows-Runtime-apps und-Komponenten zusammenarbeiten. Universelle Windows-Plattform in C++ geschriebenen apps werden in nativen Code kompiliert, der direkt in der CPU ausgeführt wird. Universelle Windows-Plattform apps, die in c# geschrieben sind, oder Visual Basic in Microsoft Intermediate Language (MSIL) kompiliert und im Common Language Runtime (CLR) ausgeführt werden. Universelle Windows-Plattform in JavaScript geschriebenen apps werden in einer Laufzeitumgebung ausgeführt. Die Windows-Runtime Betriebssystemkomponenten selbst sind in C++ geschrieben und werden als System eigener Code ausgeführt. Alle diese Komponenten und universelle Windows-Plattform-apps kommunizieren direkt über die Windows-Runtime Application Binary Interface (ABI).

Um die Unterstützung für die Windows-Runtime in einer modernen C++-Sprache zu aktivieren, hat Microsoft das C++-/CX. C++/CX bietet integrierte Basis Typen und Implementierungen von grundlegenden Windows-Runtime Typen, mit denen C++-apps und-Komponenten über die ABI mit in anderen Sprachen geschriebenen apps kommunizieren können. Sie können beliebige Windows-Runtime Typen nutzen oder Klassen, Strukturen, Schnittstellen und andere benutzerdefinierte Typen erstellen, die von anderen universelle Windows-Plattform-apps und-Komponenten verwendet werden können. eine universelle Windows-Plattform-APP, die in C++ geschrieben ist/CX kann auch reguläre C++-Klassen und-Strukturen verwenden, solange Sie keine öffentliche Barrierefreiheit haben.

Eine ausführliche Diskussion der C++/CX-Sprachprojektion und ihrer Funktionsweise finden Sie in folgenden Blogbeiträgen:

- [C++/CX Teil 0 von \[ n \] : eine Einführung](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)

- [C++/CX Teil 1 von \[ n \] : einfache Klasse](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)

- [C++/CX Teil 2 von \[ n \] : Typen mit hüten](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)

- [C++/CX Teil 3 von \[ n \] : in Bearbeitung](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)

- [C++/CX Teil 4 von \[ n \] : statische Element Funktionen](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)

## <a name="windows-metadata-winmd-files"></a>Windows-Metadatendateien (.winmd)

Wenn Sie eine universelle Windows-Plattform-App kompilieren, die in C++ geschrieben ist, generiert der Compiler die ausführbare Datei im systemeigenen Computercode und generiert außerdem eine separate Windows-Metadatendatei (. winmd), die Beschreibungen der öffentlichen Windows-Runtime Typen enthält, einschließlich Klassen, Strukturen, Enumerationen, Schnittstellen, parametrisierte Schnittstellen und Delegaten. Das Format der Metadaten ähnelt dem Format, das in den .NET Framework-Assemblys verwendet wird.  In einer C++-Komponente enthält die WinMD-Datei nur Metadaten. Der ausführbare Code befindet sich in einer separaten Datei. Dies ist der Fall für die Windows-Runtime Komponenten, die in Windows enthalten sind. Der WinMD-Dateiname muss übereinstimmen oder ein Präfix des Stammnamenspace im Quellcode sein. (Für die .NET Framework-Sprachen sind in einer WinMD-Datei wie in einer .NET Framework-Assembly sowohl Code als auch Metadaten enthalten.)

Die Metadaten in der WinMD-Datei stellen die veröffentlichte Oberfläche des Codes dar. Veröffentlichte Typen sind für andere universelle Windows-Plattformen sichtbar, unabhängig davon, in welcher Sprache diese anderen apps geschrieben sind. Daher können die Metadaten oder der veröffentlichte Code nur Typen enthalten, die vom Windows-Runtime Type System angegeben werden. C++-spezifische Sprachkonstrukte wie reguläre Klassen, Arrays, Vorlagen oder STL-Container können nicht in Metadaten veröffentlicht werden, da eine JavaScript- oder C#-Clientapp sie nicht verwenden kann.

Ob ein Typ oder eine Methode in den Metadaten sichtbar ist, hängt davon ab, welche Zugriffsmodifizierer auf diesen Typ oder diese Methode angewendet werden. Um sichtbar zu sein, muss ein Typ sowohl in einem Namespace als auch als öffentlich deklariert werden. Eine nicht öffentliche Verweisklasse ist als interner Hilfsprogrammtyp im Code zugelassen, wird jedoch nicht in den Metadaten angezeigt. Es sind jedoch auch in einer öffentlichen Verweisklasse nicht unbedingt alle Member sichtbar. In der folgenden Tabelle wird die Beziehung zwischen C++-zugriffsspezifiziererbezeichgern in einer öffentlichen Verweis Klasse und Windows-Runtime Sichtbarkeit von Metadaten aufgelistet

|||
|-|-|
|**In Metadaten veröffentlicht**|**Nicht in Metadaten veröffentlicht**|
|öffentlich|private|
|protected|internal|
|public protected|private protected|

Mit dem **Objektkatalog** können Sie den Inhalt von WinMD-Dateien anzeigen. Die Windows-Runtime Komponenten, die in Windows enthalten sind, befinden sich in der Datei Windows. winmd. Die default. winmd-Datei enthält die grundlegenden Typen, die in C++/CX verwendet werden, und Platform. winmd enthält zusätzliche Typen aus dem Platform-Namespace. Standardmäßig sind diese drei winmd-Dateien in jedem C++-Projekt für universelle Windows-Plattform-Apps enthalten.

> [!TIP]
> Die im [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) vorhandenen Typen sind in der WinMD-Datei nicht sichtbar, da sie nicht öffentlich sind. Es sind private C++-spezifische Implementierungen der Schnittstellen, die in `Windows::Foundation::Collections`definiert sind. Eine Windows-Runtime-APP, die in JavaScript oder c# geschrieben ist, weiß nicht, was eine [Platform:: Collections:: Vector-Klasse](../cppcx/platform-collections-vector-class.md) ist, aber Sie kann einen Nutzen `Windows::Foundation::Collections::IVector` . Die `Platform::Collections` -Typen werden in der Datei collection.h definiert.

## <a name="windows-runtime-type-system-in-ccx"></a>Windows-Runtime Type System in C++/CX

In den folgenden Abschnitten werden die wichtigsten Features des Windows-Runtime Typsystems beschrieben und die Unterstützung in C++/CX.

### <a name="namespaces"></a>Namespaces

Alle Windows-Runtime Typen müssen innerhalb eines Namespace deklariert werden. die Windows-API selbst ist nach Namespaces organisiert. Eine WinMD-Datei muss denselben Namen wie der Stammnamespace haben. Zum Beispiel kann eine Klasse namens A.B.C.MyClass nur instanziiert werden, wenn sie in einer Metadatendatei definiert ist, die A.winmd oder A.B.winmd oder A.B.C.winmd heißt. Der Name der DLL muss nicht mit dem Namen der WINMD-Datei übereinstimmen.

Die Windows-API selbst wurde überarbeitet und präsentiert sich nun als gut gestaltete Klassenbibliothek, die nach Namespaces organisiert ist.  Alle Windows-Runtime Komponenten werden in den Windows. *-Namespaces deklariert.

Weitere Informationen finden Sie unter [Namespaces und Typsichtbarkeit](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Grundlegende Typen

Die Windows-Runtime definiert die folgenden grundlegenden Typen: UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, Boolean und String. C++/CX unterstützt die grundlegenden numerischen Typen im Standard Namespace wie UInt16, UInt32, UInt64, Int16, Int32, Int64, float32, float64 und char16. Boolean und String werden auch im Plattformnamespace definiert.

C++/CX definiert auch Uint8 `unsigned char` . Dies entspricht, das im Windows-Runtime nicht unterstützt wird und in öffentlichen APIs nicht verwendet werden kann.

Ein elementarer Typ kann auf NULL festlegbar gemacht werden, indem er in einer [Platform::IBox Interface](../cppcx/platform-ibox-interface.md) -Schnittstelle umgebrochen wird. Weitere Informationen finden Sie unter [Wertklassen und Strukturen](../cppcx/value-classes-and-structs-c-cx.md)definiert sind.

Weitere Informationen über grundlegende Typen finden Sie unter [Grundlegende Typen](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>Zeichenfolgen

Eine Windows-Runtime Zeichenfolge ist eine unveränderliche Sequenz von 16-Bit-Unicode-Zeichen. Eine Windows-Runtime Zeichenfolge wird als projiziert `Platform::String^` . Diese Klasse stellt Methoden zum Erstellen und Bearbeiten von Zeichenfolgen zur Verfügung und ermöglicht, Zeichenfolgen in und aus `wchar_t`zu konvertieren.

Weitere Informationen finden Sie unter [Zeichenfolgen](../cppcx/strings-c-cx.md)definiert sind.

### <a name="arrays"></a>Arrays

Der Windows-Runtime unterstützt eindimensionale Arrays eines beliebigen Typs. Arrays von Arrays werden nicht unterstützt.  In C++/CX werden Windows-Runtime Arrays als [Platform:: Array-Klasse](../cppcx/platform-array-class.md)projiziert.

Weitere Informationen finden Sie unter [Array und beschreiteonlyarray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Referenzklassen und Strukturen

Eine Windows-Runtime Klasse wird in C++/CX als Verweis Klasse oder Verweis Struktur projiziert, da Sie als Verweis kopiert werden. Die Speicherverwaltung für Verweisklassen und Referenzstrukturen erfolgt mittels der Verweiszählung transparent. Wenn der letzte Verweis auf ein Objekt außerhalb des gültigen Bereichs ist, wird das Objekt vernichtet. Eine Verweisklasse oder Referenzstruktur

- kann als Member Konstruktoren, Methoden, Eigenschaften und Ereignisse enthalten. Diese Member können einen öffentlichen, privaten, geschützten oder internen Zugriff aufweisen.

- kann private geschachtelte Enumerations-, Struktur- oder Klassendefinitionen enthalten.

- kann direkt von einer Basisklasse erben und eine beliebige Anzahl von Schnittstellen implementieren. Alle Verweisklassen sind implizit konvertierbar in die [Platform::Object Class](../cppcx/platform-object-class.md) und können ihre virtuellen Methoden wie [Object::ToString](../cppcx/platform-object-class.md#tostring)überschreiben.

Eine Verweisklasse, die über einen öffentlichen Konstruktor verfügt, muss als versiegelt deklariert werden, um eine weitere Ableitung zu verhindern.

Weitere Informationen finden Sie unter [Referenzklassen und Strukturen](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>Wertklassen und Strukturen

Eine Wertklasse oder Wertstruktur stellt eine grundlegende Datenstruktur dar und enthält nur Felder, die Wertklassen, Wertstrukturen oder vom Typ `Platform::String^`sein können.  Wertstrukturen und Wertklassen werden nach Wert kopiert.

Eine Wertstruktur kann auf NULL festlegbar gemacht werden, indem sie in einer IBox-Schnittstelle umgebrochen wird.

Weitere Informationen finden Sie unter [Wertklassen und Strukturen](../cppcx/value-classes-and-structs-c-cx.md)definiert sind.

### <a name="partial-classes"></a>Teilklassen

Mit der Funktion der Teilklassen kann eine Klasse für mehrere Dateien definiert werden. Sie wird hauptsächlich dazu verwendet, um es Codegenerierungstools wie dem XAML-Editor ermöglichen, eine Datei zu ändern, ohne dass die Datei, die Sie bearbeiten, angefasst werden muss.

Weitere Informationen finden Sie unter [Teilklassen](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Eigenschaften

Eine Eigenschaft ist ein öffentliches Datenmember beliebiger Windows-Runtime Typs und wird als Get/Set-Methoden paar implementiert. Clientcode interpretiert eine Eigenschaft beim Zugriff als öffentliches Feld. Eine Eigenschaft, die keinen benutzerdefinierten GET- oder SET-Code erfordert, wird als *trivial-Eigenschaft* bezeichnet und kann ohne explizite GET- oder SET-Methoden deklariert werden.

Weitere Informationen finden Sie unter [Eigenschaften](../cppcx/properties-c-cx.md)definiert sind.

### <a name="windows-runtime-collections-in-ccx"></a>Windows-Runtime Auflistungen in C++/CX

Der Windows-Runtime definiert einen Satz von Schnittstellen für Auflistungs Typen, die von jeder Sprache auf eigene Weise implementiert werden. C++/CX stellt Implementierungen in der [Platform:: Collections:: Vector-Klasse](../cppcx/platform-collections-vector-class.md), [Platform:: Collections:: Map-Klasse](../cppcx/platform-collections-map-class.md)und anderen verwandten, konkreten Auflistungs Typen bereit, die mit ihren STL-Entsprechungen (Standard Template Library) kompatibel sind.

Weitere Informationen finden Sie unter [Collections](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Vorlagenverweisklassen

Private und interne Verweisklassen können vorlagenbasiert und spezialisiert sein.

Weitere Informationen finden Sie unter [Vorlagenverweisklassen](../cppcx/template-ref-classes-c-cx.md)definiert sind.

### <a name="interfaces"></a>Schnittstellen

Eine Windows-Runtime-Schnittstelle definiert einen Satz von öffentlichen Eigenschaften, Methoden und Ereignissen, die eine Verweis Klasse oder Verweis Struktur implementieren muss, wenn Sie von der-Schnittstelle erbt.

Weitere Informationen finden Sie unter [Schnittstellen](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Enumerationen

Eine Enumerationsklasse in Windows-Runtime ähnelt einer Bereichs bezogenen Enumeration in C++. Der zugrunde liegende Typ ist int32, es sei denn, das Attribut [Flags] kommt zur Anwendung. Dann ist der zugrunde liegende Typ uint32.

Weitere Informationen finden Sie unter [Enumerationen](../cppcx/enums-c-cx.md)definiert sind.

### <a name="delegates"></a>Delegaten

Ein Delegat in der Windows-Runtime ist analog zu einem Std:: Function-Objekt in C++. Es ist eine spezielle Verweisklasse, mit deren Hilfe vom Client bereitgestellte Funktionen aufgerufen werden, die kompatible Signaturen enthalten.  Delegaten werden am häufigsten in der Windows-Runtime als Typ eines Ereignisses verwendet.

Weitere Informationen finden Sie unter [Delegaten](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Ausnahmen

In C++/CX können Sie benutzerdefinierte Ausnahmetypen, [std::exception](../standard-library/exception-class.md) -Typen und [Platform::Exception](../cppcx/platform-exception-class.md) -Typen abfangen.

Weitere Informationen finden Sie unter [Ausnahmen](../cppcx/exceptions-c-cx.md)definiert sind.

### <a name="events"></a>Events

Ein Ereignis ist ein öffentlicher Member in einer Verweisklasse oder einer Referenzstruktur mit einem Delegattyp als Typ. Ein Ereignis kann nur durch die besitzende Klasse aufgerufen, d. h. ausgelöst werden. Clientcode kann jedoch eigene Funktionen bereitstellen, die als Ereignishandler bezeichnet werden. Diese Ereignishandler werden aufgerufen, wenn die besitzende Klasse das Ereignis auslöst.

Weitere Informationen finden Sie unter [Ereignisse](../cppcx/events-c-cx.md).

### <a name="casting"></a>Umwandlung

C++/CX unterstützt die Standard-C++-Umwandlungsoperatoren [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)und [reinterpret_cast](../cpp/reinterpret-cast-operator.md)sowie den Operator **safe_cast** , der C++/CX-spezifisch ist.

Weitere Informationen finden Sie unter [Umwandlung](../cppcx/casting-c-cx.md)definiert sind.

### <a name="boxing"></a>Boxing

Eine geschachtelte Variable ist ein Werttyp, der in einem Referenztyp in Situationen umschlossen wird, in denen eine Verweissemantik erforderlich ist.

Weitere Informationen finden Sie unter [Boxing](../cppcx/boxing-c-cx.md)definiert sind.

### <a name="attributes"></a>Attributes

Ein Attribut ist ein Metadatenwert, der auf beliebige Windows-Runtime Typen oder Typmember angewendet und zur Laufzeit überprüft werden kann. Der-Windows-Runtime definiert einen Satz allgemeiner Attribute im- `Windows::Foundation::Metadata` Namespace. Benutzerdefinierte Attribute in öffentlichen Schnittstellen werden von Windows-Runtime in dieser Version nicht unterstützt.

## <a name="api-deprecation"></a>API-Veraltung

Beschreibt, wie öffentliche APIs als veraltet markiert werden, indem das Attribut verwendet wird, das von den Windows-Runtime Systemtypen verwendet wird.

Weitere Informationen finden Sie unter [Veraltete Typen und](../cppcx/deprecating-types-and-members-c-cx.md)Member.

## <a name="see-also"></a>Weitere Informationen

[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)
