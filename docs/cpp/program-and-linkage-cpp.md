---
title: Übersetzungseinheiten und Verknüpfungen (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: 5a166efc7ae926f6b028c35007b0972d0a652d6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227191"
---
# <a name="translation-units-and-linkage"></a>Übersetzungseinheiten und Verknüpfungen

In einem C++-Programm kann ein *Symbol*(z. b. ein Variablen-oder Funktionsname) beliebig oft innerhalb des Gültigkeits Bereichs deklariert werden, es kann jedoch nur einmal definiert werden. Diese Regel ist die "One Definition Rule" (ODR). Eine- *Deklaration* führt einen Namen in das Programm ein (oder führt ihn erneut ein). Eine *Definition* führt einen Namen ein. Wenn der Name eine Variable darstellt, wird er von einer Definition explizit initialisiert. Eine *Funktionsdefinition* besteht aus der Signatur und dem Funktions Rumpf. Eine Klassendefinition besteht aus dem Klassennamen, gefolgt von einem-Block, der alle Klassenmember auflistet. (Die Textkörper der Element Funktionen können optional separat in einer anderen Datei definiert werden.)

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

Ein Programm besteht aus einer oder mehreren *Übersetzungseinheiten*. Eine Übersetzungseinheit besteht aus einer Implementierungs Datei und allen Headern, die Sie direkt oder indirekt enthält. Implementierungs Dateien verfügen in der Regel über die Dateierweiterung *cpp* oder *cxx*. Header Dateien haben in der Regel eine Erweiterung von *h* oder *HPP*. Jede Übersetzungseinheit wird vom Compiler unabhängig kompiliert. Nach Abschluss der Kompilierung führt der Linker die kompilierten Übersetzungseinheiten in einem einzigen *Programm*zusammen. Verstöße gegen die ODR-Regel werden in der Regel als Linker-Fehler angezeigt. Linker-Fehler treten auf, wenn derselbe Name über zwei unterschiedliche Definitionen in verschiedenen Übersetzungseinheiten verfügt.

Im Allgemeinen ist die beste Möglichkeit, eine Variable in mehreren Dateien sichtbar zu machen, darin, Sie in eine Header Datei einzufügen. Fügen Sie dann in jeder *cpp* -Datei, die die Deklaration erfordert, eine #include-Anweisung hinzu. Durch Hinzufügen von *include-Wächter* um den Header Inhalt müssen Sie sicherstellen, dass die deklarierenden Namen nur einmal definiert werden.

In c++ 20 werden [Module](modules-cpp.md) als verbesserte Alternative zu Header Dateien eingeführt.

In einigen Fällen kann es erforderlich sein, eine globale Variable oder Klasse in einer *cpp* -Datei zu deklarieren. In diesen Fällen benötigen Sie eine Möglichkeit, um dem Compiler und dem Linker mitzuteilen, welche Art von *Verknüpfung* der Name aufweist. Der Typ der Verknüpfung gibt an, ob der Name des Objekts nur für eine Datei oder für alle Dateien gilt. Das Konzept der Verknüpfung gilt nur für globale Namen. Das Konzept der Verknüpfung gilt nicht für Namen, die in einem Bereich deklariert werden. Ein Bereich wird durch eine Reihe von einschließenden geschweiften Klammern angegeben, z. b. in Funktions-oder Klassendefinitionen.

## <a name="external-vs-internal-linkage"></a>Externe und interne Verknüpfung

Eine *Free-Funktion* ist eine Funktion, die im globalen oder im Namespace-Gültigkeitsbereich definiert ist. Nicht konstante globale Variablen und freie Funktionen haben standardmäßig eine *externe Verknüpfung*. Sie sind in allen Übersetzungseinheiten des Programms sichtbar. Daher kann kein anderes globales Objekt den Namen haben. Ein Symbol mit *interner Verknüpfung* oder *ohne Verknüpfung* ist nur innerhalb der Übersetzungseinheit sichtbar, in der es deklariert ist. Wenn ein Name eine interne Verknüpfung aufweist, kann derselbe Name in einer anderen Übersetzungseinheit vorhanden sein. Innerhalb von Klassendefinitionen oder Funktions Texten deklarierte Variablen haben keine Verknüpfung.

Sie können erzwingen, dass ein globaler Name eine interne Verknüpfung hat, indem Sie ihn explizit als deklarieren **`static`** . Dadurch wird die Sichtbarkeit auf dieselbe Übersetzungseinheit beschränkt, in der Sie deklariert ist. In diesem Kontext **`static`** bedeutet etwas anderes als bei Anwendung auf lokale Variablen.

Die folgenden Objekte haben standardmäßig eine interne Verknüpfung:

- Konstante Objekte
- constexpr-Objekte
- Typedefs
- statische Objekte im Namespace-Gültigkeitsbereich

Um einem konstanten Objekt eine externe Verknüpfung zu verleihen, deklarieren Sie es als, **`extern`** und weisen Sie ihm einen Wert zu:

```cpp
extern const int value = 42;
```

Weitere Informationen finden Sie unter [extern](extern-cpp.md) .

## <a name="see-also"></a>Siehe auch

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)
