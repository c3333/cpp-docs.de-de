---
title: Übersicht über Generics in C++/CLI
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: a1a66b6464bf952a530dbf1ea188bfd681d684d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172073"
---
# <a name="overview-of-generics-in-ccli"></a>Übersicht über Generics in C++/CLI

Generics sind parametrisierte Typen, die von der Common Language Runtime unterstützt werden. Ein parametrisierter Typ ist ein Typ, der mit einem unbekannten, bei der Verwendung des Generics angegebenen Typparameter definiert ist.

## <a name="why-generics"></a>Warum Generics?

C++ unterstützt Vorlagen, und sowohl Vorlagen als auch Generics unterstützen parametrisierte Typen zum Erstellen typisierter Sammlungsklassen. Allerdings bieten Vorlagen Parametrisierung während der Kompilierzeit. Sie können nicht auf eine Assembly verweisen, die eine Vorlagendefinition enthält, und neue Spezialisierungen der Vorlage erstellen. Nach der Kompilierung sieht eine spezialisierte Vorlage wie jede andere Klasse oder Methode aus. Im Gegensatz dazu werden Generics in MSIL als parametrisierter Typ ausgegeben, den die Runtime als parametrisierten Typ kennt; Quellcode, der auf eine Assembly verweist, die einen generischen Typ enthält, kann Spezialisierungen des generischen Typs erstellen. Weitere Informationen zum Vergleich von standardmäßigen C++-Vorlagen und Generics finden Sie unter [Generics und Vorlagen (C++/CLI)](generics-and-templates-visual-cpp.md).

## <a name="generic-functions-and-types"></a>Generische Funktionen und Typen

Klassentypen können, solange sie verwaltete Typen sind, generisch sein. Ein Beispiel hierfür könnte eine `List`-Klasse sein. Der Typ eines Objekts in der Liste wäre der Typparameter. Wenn Sie eine `List`-Klasse für viele verschiedene Typen von Objekten benötigen würden, hätten Sie, als es die Generics noch nicht gab, vielleicht eine `List` verwendet, die `System::Object` als Elementtyp akzeptiert. Aber dies würde die Verwendung jedes Objekts (einschließlich Objekte des falschen Typs) in der Liste zulassen. Eine solche Liste würde als nicht typisierte Sammlungsklasse bezeichnet. Im besten Fall könnten Sie den Typ zur Laufzeit überprüfen und eine Ausnahme auslösen. Sie hätten vielleicht auch eine Vorlage verwendet, die nach der Kompilierung in eine Assembly ihre generische Qualität verloren hätte. Consumer Ihrer Assembly könnten nicht eigene Spezialisierungen der Vorlage erstellen. Mit Generics können Sie typisierte Sammlungsklassen erstellen, z.B. `List<int>` („Int-Liste“) und `List<double>` („Double-Liste“), was einen Kompilierzeitfehler verursachen würde, wenn Sie versuchen würden, einen Typ zu platzieren, für dessen Akzeptanz in der typisierten Sammlung die Sammlung nicht ausgelegt ist. Darüber hinaus bleiben diese Typen generisch, wenn sie kompiliert werden.

Eine Beschreibung der Syntax von generischen Klassen finden Sie unter [Generische Klassen (C++/CLI)](generic-classes-cpp-cli.md). Ein neuer Namespace, <xref:System.Collections.Generic>, führt eine Reihe von parametrisierten Sammlungstypen inklusive <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> und <xref:System.Collections.Generic.LinkedList%601> ein.

Sowohl Instanz- als auch statische Memberfunktionen, Delegaten und globale Funktionen können auch generisch sein. Generische Funktionen können erforderlich sein, wenn die Parameter einer Funktion unbekannten Typs sind oder die Funktion selbst mit generischen Typen arbeiten muss. In vielen Fällen, in denen `System::Object` in der Vergangenheit vielleicht als Parameter für einen unbekannten Objekttyp verwendet wurde, könnte stattdessen ein generischer Typparameter verwendet werden, der typsichereren Code zulässt. Zur Kompilierzeit würde jeder Versuch, einen Typ zu übergeben, für den die Funktion nicht entworfen wurde, als Fehler gekennzeichnet. Mithilfe von `System::Object` als Funktionsparameter würde die unbeabsichtigte Übergabe eines Objekts, für das die Funktion nicht vorgesehen ist, nicht erkannt werden, und Sie müssten den unbekannten Objekttyp im Funktionsrumpf in einen bestimmten Typ umwandeln und die Möglichkeit einer InvalidCastException berücksichtigen. Mit einem Generic würde Code, der versucht, der Funktion ein Objekt zu übergeben, einen Typenkonflikt auslösen, sodass der Funktionsrumpf garantiert den richtigen Typ hat.

Die gleichen Vorteile gelten für Sammlungsklassen, die auf der Basis von Generics erstellt sind. In der Vergangenheit hätten Sammlungsklassen `System::Object` zum Speichern von Elementen in einer Sammlung verwendet. Das Einfügen von Objekten eines Typs, für den die Sammlung nicht vorgesehen ist, wurde nicht zur Kompilierzeit als Fehler gekennzeichnet, und oft auch sogar dann nicht, wenn die Objekte eingefügt wurden. In der Regel wird ein Objekt in einen anderen Typ umgewandelt, wenn in der Sammlung darauf zugegriffen wird. Nur wenn bei der Umwandlung ein Fehler auftritt, würde der unerwartete Typ erkannt werden. Generics lösen dieses Problem zur Kompilierzeit durch Erkennung von Code, der einen nicht mit dem Typparameter der generischen Sammlung übereinstimmenden Typ einfügt (oder implizit in diesen konvertiert).

Eine Beschreibung der Syntax finden Sie unter [Generische Funktionen (C++/CLI)](generic-functions-cpp-cli.md).

## <a name="terminology-used-with-generics"></a>Mit Generics verwendete Terminologie

### <a name="type-parameters"></a>Typparameter

Eine generische Deklaration enthält einen oder mehrere unbekannte Typen, die *Typparameter* genannt werden. Typparametern wird ein Name zugewiesen, der innerhalb des Texts der generischen Deklaration für den Typ steht. Der Typparameter wird innerhalb des Texts der generischen Deklaration als Typ verwendet. Die generische Deklaration für `List<T>` enthält den Typparameter "T".

### <a name="type-arguments"></a>Typargumente

Das *Typargument* ist der anstelle des Typparameters tatsächlich verwendete Typ, wenn das Generic für einen bestimmten Typ oder bestimmte Typen spezifiziert wird. Beispiel: **int** ist das Typargument in `List<int>`. Werttypen und Typen von Handles sind die einzigen Typen, die in einem generischen Typargument zulässig sind.

### <a name="constructed-type"></a>Konstruierter Typ

Ein aus einem generischen Typ erstellter Typ wird als *konstruierter Typ* bezeichnet. Ein nicht vollständig angegebener Typ wie z.B. `List<T>` ist ein *offen konstruierter Typ*; ein vollständig angegebener Typ wie z.B. `List<double>,` ist ein *geschlossen konstruierter Typ* oder *spezialisierter Typ*. Offen konstruierte Typen können in der Definition anderer generischer Typen oder Methoden verwendet werden und dürfen nicht vollständig angegeben werden, bis das einschließende Generic selbst angegeben ist. Im Folgenden sehen Sie ein Beispiel für die Verwendung eines offen konstruierten Typs als Basisklasse für ein Generic:

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>Einschränkung

Eine Einschränkung ist eine Einschränkung für Typen, die als Typparameter verwendet werden können. Beispielsweise könnte eine bestimmte generische Klasse nur Klassen akzeptieren, die von einer angegebenen Klasse erben oder eine angegebene Schnittstelle implementieren. Weitere Informationen finden Sie unter [Einschränkungen für generische Typparameter (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="reference-types-and-value-types"></a>Verweistypen und Werttypen

Handletypen und Werttypen können als Typargumente verwendet werden. In der generischen Definition, in der beide Typen verwendet werden können, ist die Syntax der von Verweistypen. Beispiel: Der `->`-Operator wird verwendet, um auf Member des Typs des Typparameters zuzugreifen, und zwar unabhängig davon, ob der schließlich verwendete Typ ein Verweistyp oder ein Werttyp ist. Wenn ein Werttyp als Typargument verwendet wird, generiert die Runtime Code, der die Werttypen direkt ohne Boxing verwendet.

Wenn ein Verweistyp als generisches Typargument verwendet wird, verwenden Sie die Handlesyntax. Wenn ein Werttyp als generisches Typargument verwendet wird, verwenden Sie den Namen des Typs direkt.

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>Typparameter

Typparameter in einer generischen Klasse werden wie andere Bezeichner behandelt. Da der Typ nicht bekannt ist, gibt es jedoch Einschränkungen für deren Verwendung. Sie können z.B. nicht Member und Methoden der Typparameterklasse verwenden, solange vom Typparameter nicht bekannt ist, dass er diese Member unterstützt. Also müssen Sie für den Zugriff auf einen Member über den Typparameter den Typ, der den Member enthält, der Einschränkungenliste des Typparameters hinzufügen.

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

Diese Einschränkungen gelten auch für Operatoren. Ein uneingeschränkter generischer Typparameter kann nicht die Operatoren `==` und `!=` zum Vergleichen von zwei Instanzen des Typparameters verwenden, falls der Typ diese Operatoren nicht unterstützt. Diese Überprüfungen sind für Generics erforderlich, aber nicht für Vorlagen, da Generics zur Laufzeit mit einer beliebigen Klasse spezifiziert werden können, die die Einschränkungen erfüllt, wenn es zu spät ist, um zu überprüfen, ob ungültige Member verwendet werden.

Eine Standardinstanz des Typparameters kann mithilfe des `()`-Operators erstellt werden. Beispiel:

`T t = T();`

wobei `T` ein Typparameter in einer generischen Klasse oder Methodendefinition ist; die Variable wird mit ihrem Standardwert initialisiert. Wenn `T` eine Verweisklasse ist, wird es ein NULL-Zeiger sein; wenn `T` eine Wertklasse ist, wird das Objekt mit 0 (null) initialisiert. Dies wird als *Standardinitialisierer* bezeichnet.

## <a name="see-also"></a>Weitere Informationen

[Generics](generics-cpp-component-extensions.md)
