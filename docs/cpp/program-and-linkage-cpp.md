---
title: Übersetzungseinheiten und Verknüpfungen (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: 791ec53d4df863b218db463f2b9b9401bf6f466d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374319"
---
# <a name="translation-units-and-linkage"></a>Übersetzungseinheiten und Verknüpfungen

In einem C++-Programm kann ein *Symbol,* z. B. eine Variable oder ein Funktionsname, bemalbar innerhalb seines Gültigkeitsbereichs bemalbar deklariert werden, es kann jedoch nur einmal definiert werden. Diese Regel ist die "One Definition Rule" (ODR). Eine *Deklaration* führt einen Namen in das Programm ein (oder führt ihn erneut ein). Eine *Definition* führt einen Namen ein. Wenn der Name eine Variable darstellt, wird sie von einer Definition explizit initialisiert. Eine *Funktionsdefinition* besteht aus der Signatur plus dem Funktionstext. Eine Klassendefinition besteht aus dem Klassennamen gefolgt von einem Block, der alle Klassenmember auflistet. (Die Körper der Memberfunktionen können optional separat in einer anderen Datei definiert werden.)

Das folgende Beispiel zeigt einige Deklarationen:

```cpp
int i;
int f(int x);
class C;
```

Das folgende Beispiel zeigt einige Definitionen:

```cpp
int i{42};
int f(int x){ return x * i; }
class C {
public:
   void DoSomething();
};
```

Ein Programm besteht aus einer oder mehreren *Übersetzungseinheiten*. Eine Übersetzungseinheit besteht aus einer Implementierungsdatei und allen Kopfzeilen, die sie direkt oder indirekt enthält. Implementierungsdateien haben in der Regel die Dateierweiterung *cpp* oder *cxx*. Headerdateien haben in der Regel die Erweiterung von *h* oder *hpp*. Jede Übersetzungseinheit wird unabhängig vom Compiler kompiliert. Nach Abschluss der Kompilierung führt der Linker die kompilierten Übersetzungseinheiten zu einem einzigen *Programm*zusammen. Verstöße gegen die ODR-Regel werden in der Regel als Linkerfehler angezeigt. Linkerfehler treten auf, wenn derselbe Name zwei unterschiedliche Definitionen in verschiedenen Übersetzungseinheiten aufweist.

Im Allgemeinen ist es am besten, eine Variable über mehrere Dateien hinweg sichtbar zu machen, wenn sie in einer Headerdatei abgelegt wird. Fügen Sie dann in jeder *cpp-Datei,* die die Deklaration erfordert, eine #include-Direktive hinzu. Durch Hinzufügen von *Include-Wächtern* um den Headerinhalt stellen Sie sicher, dass die deklarierten Namen nur einmal definiert werden.

In C++20 werden [Module](modules-cpp.md) als verbesserte Alternative zu Headerdateien eingeführt.

In einigen Fällen kann es erforderlich sein, eine globale Variable oder Klasse in einer *cpp-Datei* zu deklarieren. In diesen Fällen benötigen Sie eine Möglichkeit, dem Compiler und Linker mitzuteilen, welche Art von *Verknüpfung* der Name hat. Der Verknüpfungstyp gibt an, ob der Name des Objekts nur auf eine Datei oder auf alle Dateien angewendet wird. Das Konzept der Verknüpfung gilt nur für globale Namen. Der Begriff der Verknüpfung gilt nicht für Namen, die innerhalb eines Bereichs deklariert werden. Ein Bereich wird durch eine Reihe von einschließenden geschweiften Klammern angegeben, z. B. in Funktions- oder Klassendefinitionen.

## <a name="external-vs-internal-linkage"></a>Externe vs. interne Verknüpfung

Eine *freie Funktion* ist eine Funktion, die im globalen oder Namespacebereich definiert ist. Nicht-const globale Variablen und freie Funktionen haben standardmäßig *externe Verknüpfung;* sie sind von jeder Übersetzungseinheit im Programm aus sichtbar. Daher kann kein anderes globales Objekt diesen Namen haben. Ein Symbol mit *interner Verknüpfung* oder *ohne Verknüpfung* ist nur innerhalb der Übersetzungseinheit sichtbar, in der es deklariert ist. Wenn ein Name eine interne Verknüpfung hat, kann derselbe Name in einer anderen Übersetzungseinheit vorhanden sein. Variablen, die mit Klassendefinitionen oder Funktionstexten deklariert wurden, haben keine Verknüpfung.

Sie können erzwingen, dass ein globaler Name über eine interne Verknüpfung verfügen muss, indem Sie ihn explizit als **statisch**deklarieren. Dadurch wird die Sichtbarkeit auf dieselbe Übersetzungseinheit beschränkt, in der sie deklariert ist. In diesem Zusammenhang bedeutet **statisch** etwas anderes als bei Anwendung auf lokale Variablen.

Die folgenden Objekte verfügen standardmäßig über eine interne Verknüpfung:

- const-Objekte
- constexpr-Objekte
- Typedefs
- Statische Objekte im Namespacebereich

Um einem const-Objekt eine externe Verknüpfung zu geben, deklarieren Sie es als **extern** und weisen Sie ihm einen Wert zu:

```cpp
extern const int value = 42;
```

Weitere Informationen finden Sie [unter extern.](extern-cpp.md)

## <a name="see-also"></a>Siehe auch

[Grundkonzepte](../cpp/basic-concepts-cpp.md)
