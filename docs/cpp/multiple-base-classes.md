---
title: Mehrere Basisklassen
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: 0e663f33213a5fd57f2adbdcc53233c6af29954e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227373"
---
# <a name="multiple-base-classes"></a>Mehrere Basisklassen

Eine Klasse kann von mehr als einer Basisklasse abgeleitet werden. In einem Modell mit mehreren Vererbungen, bei dem Klassen von mehr als einer Basisklasse abgeleitet sind, werden die Basisklassen mithilfe des *Base-List-* Grammatik Elements angegeben. Beispielsweise kann die Klassendeklaration für `CollectionOfBook`, abgeleitet von `Collection` und `Book`, angegeben werden:

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

Die Reihenfolge, in der Basisklassen angegeben werden, ist nicht signifikant, außer in Fällen, in denen die Konstruktoren und Destruktoren aufgerufen werden. In diesen Fällen wirkt sich die Reihenfolge, in der Basisklassen angegeben werden, auf Folgendes aus:

- Die Reihenfolge, in der die Initialisierung durch Konstruktoren stattfindet. Wenn Ihr Code darauf basiert, dass der `Book`-Teil von `CollectionOfBook` vor dem `Collection`-Teil initialisiert wird, ist die Reihenfolge der Spezifikation signifikant. Die Initialisierung erfolgt in der Reihenfolge, in der die Klassen in der *Basisliste*angegeben werden.

- Die Reihenfolge, in der Destruktoren zur Bereinigung aufgerufen werden. Auch wenn ein bestimmter „Teil“ der Klasse vorhanden sein muss, wenn der andere Teil zerstört wird, ist die Reihenfolge relevant. Dekonstruktoren werden in umgekehrter Reihenfolge der Klassen aufgerufen, die in der *Basisliste*angegeben sind.

    > [!NOTE]
    >  Die Reihenfolge der Spezifikation der Basisklassen kann das Speicherlayout der Klasse beeinflussen. Treffen Sie keine Programmierentscheidungen, die auf der Reihenfolge der Basismember im Arbeitsspeicher basieren.

Wenn Sie die *Basisliste*angeben, können Sie nicht denselben Klassennamen mehrmals angeben. Allerdings kann eine Klasse mehrmals eine indirekte Basis für eine abgeleitete Klasse sein .

## <a name="virtual-base-classes"></a>Virtuelle Basisklassen

Da eine Klasse mehrfach als indirekte Basisklasse für eine abgeleiteten Klasse auftreten kann, stellt C++ eine Methode bereit, um die Arbeitsweise solcher Basisklassen zu optimieren. Virtuelle Basisklassen bieten eine Möglichkeit, Speicherplatz zu sparen und Mehrdeutigkeiten in Klassenhierarchien zu vermeiden, die Mehrfachvererbung verwenden.

Jedes nicht virtuelle Objekt enthält eine Kopie der Datenmember, die in der Basisklasse definiert sind. Durch diese Duplizierung wird Speicherplatz verschwendet, und Sie müssen bei jedem Zugriff angeben, welche Kopie der Basisklassenmember Sie wünschen.

Wenn eine Basisklasse als virtuelle Basisklasse angegeben ist, kann sie, ohne Verdoppelung der Datenmember, mehrmals als indirekte Basisklasse fungieren. Eine einzelne Kopie der Datenmember wird von allen Basisklassen, die diese als virtuelle Basis verwenden, gemeinsam genutzt.

Beim Deklarieren einer virtuellen Basisklasse wird das **`virtual`** Schlüsselwort in den Basis Listen der abgeleiteten Klassen angezeigt.

Betrachten Sie die Klassenhierarchie in der folgenden Abbildung, die eine simulierte Warteschlange veranschaulicht.

![Diagramm der Warteschlangensimulation](../cpp/media/vc38xp1.gif "Diagramm der Warteschlangensimulation") <br/>
Simuliertes Lunch-Line-Diagramm

In der Abbildung ist `Queue` die Basisklasse für `CashierQueue` und `LunchQueue`. Wenn jedoch beide Klassen kombiniert werden, um `LunchCashierQueue` zu bilden, tritt folgendes Problem auf: Die neue Klasse enthält zwei Unterobjekte des Typs `Queue`, eines von `CashierQueue` und das andere von `LunchQueue`. Die folgende Abbildung zeigt das konzeptuelle Speicherlayout (das tatsächliche Speicherlayout kann unter Umständen optimiert werden).

![Simuliertes Lunch&#45;Line-Objekt](../cpp/media/vc38xp2.gif "Simuliertes Lunch&#45;Line-Objekt") <br/>
Simuliertes Warteschlangenobjekt

Beachten Sie, dass es zwei `Queue`-Unterobjekte im `LunchCashierQueue`-Objekt gibt. Der folgende Code deklariert `Queue` als virtuelle Basisklasse:

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

Das- **`virtual`** Schlüsselwort stellt sicher, dass nur eine Kopie des unter Objekts `Queue` enthalten ist (siehe folgende Abbildung).

![Simuliertes Mittagessen&#45;Line-Objekt, virtuelle Basisklassen](../cpp/media/vc38xp3.gif "Simuliertes Mittagessen&#45;Line-Objekt, virtuelle Basisklassen") <br/>
Simuliertes Lunch-Line-Objekt mit virtuellen Basisklassen

Eine Klasse kann eine virtuelle Komponente und eine nicht virtuelle Komponente eines bestimmten Typs haben. Dies geschieht unter den Bedingungen, die in der folgenden Abbildung veranschaulicht werden.

![Virtuelle und nicht&#45;virtuelle Komponenten einer Klasse](../cpp/media/vc38xp4.gif "Virtuelle und nicht&#45;virtuelle Komponenten einer Klasse") <br/>
Virtuelle und nicht virtuelle Komponenten der gleichen Klasse

In der Abbildung verwenden `CashierQueue` und `LunchQueue``Queue` als virtuelle Basisklasse. Allerdings spezifiziert `TakeoutQueue``Queue` als Basisklasse und nicht als virtuelle Basisklasse. Daher verfügt `LunchTakeoutCashierQueue` über zwei Unterobjekte des Typs `Queue`: eines aus dem Vererbungspfad, der `LunchCashierQueue` einschließt, und eines aus dem Pfad, der `TakeoutQueue` einschließt. Dies wird in der folgenden Abbildung verdeutlicht.

![Virtuelle & nicht&#45;virtuelle Vererbung im Objekt Layout](../cpp/media/vc38xp5.gif "Virtuelle & nicht&#45;virtuelle Vererbung im Objekt Layout") <br/>
Objekt Layout mit virtueller und nicht virtueller Vererbung

> [!NOTE]
> Virtuelle Vererbung bietet wesentliche Vorteile im Vergleich zur nicht virtuellen Vererbung. Allerdings kann es zu Mehraufwand bei der Verarbeitung kommen.

Wenn eine abgeleitete Klasse eine virtuelle Funktion überschreibt, die sie von einer virtuellen Basisklasse erbt, und wenn ein Konstruktor oder Destruktor der abgeleiteten Basisklasse die Funktion mithilfe eines Zeigers auf die virtuelle Basisklasse aufruft, führt der Compiler möglicherweise zusätzliche ausgeblendete "vtordisp"-Felder in die Klassen mit virtuellen Basen ein. Die `/vd0` -Compileroption unterdrückt das Hinzufügen des ausgeblendeten Vtordisp-Konstruktors/destrukturverschiebungs Elements. Die- `/vd1` Compileroption, die Standardeinstellung, ermöglicht Ihnen, wo Sie erforderlich sind. Deaktivieren Sie vtordisps nur dann, wenn Sie sicher sind, dass alle Klassenkonstruktoren und -destruktoren virtuelle Funktionen virtuell aufrufen.

Die `/vd` Compileroption wirkt sich auf ein gesamtes Kompilierungs Modul aus. Verwenden `vtordisp` Sie das-Pragma, um `vtordisp` Felder auf Klassenbasis zu unterdrücken und anschließend erneut zu aktivieren:

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>Mehrdeutigkeiten bei Namen

Mehrfachvererbung bietet die Möglichkeit, dass Namen in mehr als einem Pfad geerbt werden können. Die Namen von Klassenmembern auf diesen Pfaden sind nicht unbedingt eindeutig. Diese Namenskonflikte werden als Mehrdeutigkeiten bezeichnet.

Jeder Ausdruck, der auf einen Klassenmember verweist, muss einen eindeutigen Verweis darstellen. Das folgende Beispiel zeigt, wie Mehrdeutigkeiten entstehen:

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

Bei vorangehenden Klassendeklarationen ist Code wie der folgende mehrdeutig, da unklar ist, ob `b` auf das `b` in `A` oder in `B` verweist:

```cpp
C *pc = new C;

pc->b();
```

Betrachten Sie das vorhergehende Beispiel. Da der Name `a` ein Member sowohl der Klasse `A` als auch der Klasse `B` ist, kann der Compiler nicht ermitteln, welches `a` die aufzurufende Funktion festlegt. Zugriff auf einen Member ist mehrdeutig, wenn er auf mehr als eine Funktion, ein Objekt, einen Typ oder einen Enumerator verweisen kann.

Der Compiler erkennt Mehrdeutigkeiten, indem er Tests in dieser Reihenfolge durchführt:

1. Wenn der Zugriff auf den Namen mehrdeutig ist (wie gerade beschrieben) , wird eine Fehlermeldung generiert.

1. Wenn überladene Funktionen eindeutig sind, werden sie aufgelöst.

1. Wenn der Zugriff auf den Namen gegen Memberzugangsberechtigungen verstößt, wird eine Fehlermeldung generiert. (Weitere Informationen finden Sie unter [Member-Access Control](../cpp/member-access-control-cpp.md).)

Wenn ein Ausdruck durch Vererbung eine Mehrdeutigkeit erzeugt, können Sie dies manuell korrigieren, indem Sie den betreffenden Namen mit dem Klassennamen qualifizieren. Um das vorherige Beispiel ordnungsgemäß ohne Mehrdeutigkeiten kompilieren zu können, verwenden Sie beispielsweise folgenden Code:

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
> Wenn `C` deklariert ist, können Fehler verursacht werden, wenn auf `B` im Bereich von `C` verwiesen wird. Es wird jedoch kein Fehler ausgegeben, bis ein nicht qualifizierter Verweis auf `B` tatsächlich im Bereich von `C` erfolgt.

### <a name="dominance"></a>Dominanz

Es ist möglich, mehr als einen Namen (Funktion, Objekt oder Enumerator) durch ein Vererbungsdiagramm zu erzeugen. Solche Fälle unterscheiden sich nicht eindeutig von nicht virtuellen Basisklassen. Sie unterscheiden sich auch nicht eindeutig von virtuellen Basisklassen, es sei denn, einer der Namen "dominiert" die anderen.

Ein Name dominiert einen anderen Namen, wenn er in beiden Klassen definiert ist und eine Klasse von der anderen abgeleitet ist. Der dominante Name ist der Name der abgeleiteten Klasse; dieser Name wird verwendet, wenn sich anderenfalls eine Doppeldeutigkeit ergeben hätte, wie im folgenden Beispielen veranschaulicht wird:

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>Mehrdeutige Konvertierungen

Explizite und implizite Konvertierungen von Zeigern oder Verweisen auf Klassentypen kann zu Mehrdeutigkeiten führen. Die nächste Abbildung (Mehrdeutige Konvertierung der Zeiger auf Basisklassen) zeigt Folgendes:

- Die Deklaration eines Objekts vom Typ `D`.

- Der Effekt der Anwendung des address-of-Operators ( **&** ) auf dieses Objekt. Beachten Sie, dass der address-of-Operator immer die Basisadresse des Objekts bereitstellt.

- Der Effekt der expliziten Konvertierung des Zeigers, der unter Verwendung des address-of-Operators für den Basisklassentyp `A` abgerufen wurde. Beachten Sie, dass dem Compiler mit der Koersion der Adresse des Objekts in Typ `A*` nicht immer genügend Informationen darüber bereitgestellt werden, welches Unterobjekt vom Typ `A` auszuwählen ist. In diesem Fall gibt es zwei Unterobjekte.

![Mehrdeutige Konvertierung der Zeiger auf Basisklassen](../cpp/media/vc38xt1.gif "Mehrdeutige Konvertierung der Zeiger auf Basisklassen") <br/>
Mehrdeutige Konvertierung der Zeiger auf Basisklassen

Die Konvertierung in Typ `A*` (Zeiger auf `A`) ist mehrdeutig, da nicht erkannt werden kann, welches Unterobjekt des Typs `A` das richtige ist. Sie können Mehrdeutigkeiten vermeiden, indem Sie wie folgt explizit angeben, welches Unterobjekt verwendet werden soll:

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Mehrdeutigkeiten und virtuelle Basisklassen

Wenn virtuelle Basisklassen verwendet werden, können Funktionen, Objekte, Typen und Enumeratoren über Mehrfachvererbungspfade erreicht werden. Da nur eine Instanz der Basisklasse vorhanden ist, gibt es keine Mehrdeutigkeit, wenn auf diese Namen zugegriffen wird.

Die folgende Abbildung zeigt, wie Objekte mithilfe von virtueller und nicht virtueller Vererbung zusammengestellt werden.

![Virtuelle Ableitung und nicht&#45;virtuelle Ableitung](../cpp/media/vc38xr1.gif "Virtuelle Ableitung und nicht&#45;virtuelle Ableitung") <br/>
Virtuelle und nicht virtuelle Ableitung

In der Abbildung führt der Zugriff auf beliebige Member der `A`-Klasse durch nicht virtuelle Basisklassen zu einer Mehrdeutigkeit. Der Compiler hat keine Informationen darüber, ob das `B` zugeordnete Unterobjekt oder das `C` zugeordnete Unterobjekt zu verwenden ist. Wenn jedoch `A` als virtuelle Basisklasse angegeben ist, ist klar, auf welches Unterobjekt zugegriffen wird.

## <a name="see-also"></a>Siehe auch

[Vererbung](../cpp/inheritance-cpp.md)
